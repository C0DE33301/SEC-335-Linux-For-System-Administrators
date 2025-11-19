### Boot Manager Installation (102.2)

**How do you configure it for a custom boot setup?**  
Back when I had Windows, I wanted to learn Linux. I created a boot menu specifically for Windows 10, just to keep Windows and have Linux.

*   Get the UUID of the EFI partition, `sudo blkid /dev/EFI_PARTITION`
*   Write this block of code at the end of the file, `nano /etc/grub.d/40_custom`. Add the UUID of the EFI partition to `UUID`.
    
    ```
    menuentry "Windows 10" {
      search --fs-uuid --no-floppy --set=root UUID
      chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
    }
    ```
    
*   Update grub, `grub_mkconfig -o /boot/grub/grub.cfg` or `sudo update-grub`

### File Management (103.3, 103.8)

**How do you efficiently perform basic file management tasks like moving, copying, renaming, and deleting files using the command line?**

I use the normal tools, ...

*   `cp`, To copy files
    *   `-v`, This option is best used when copying large amounts of files. To make a guess at where the coping progress is at.
    *   `-r`, `-R`, `--recursive`, When coping a directory, without this option. The `cp` command will throw an error. For example, `cp: -r not specified; omitting directory 'testing'`. Use this option to avoid this.
*   `mv`, To move files
    *   `-v`, This option is best used when moving large amounts of files. To make a guess at where the moving process is at.
*   `mv`, This is also use to rename files.
*   `rm`, To delete files
    *   `-r`, `-R`, `--recursive`, When trying to delete a directory, without this option. The command will throw an error message explaining that the chosen directory is a directory. for example, `rm: cannot remove 'Week-01': Is a directory`. Make sure to use this option for deleting directories with files and subdirectories.
    *   `-v`, `--verbose`, This option is best used when deleting large amounts of files. To make a guess at where the delting progress is at.