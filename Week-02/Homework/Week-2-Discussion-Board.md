### Package Management (102.1, 102.4, 102.5)
**How do these package management tools differ, and what are the advantages or disadvantages of each system?**
- The advantages of `apt`, `yum`, and `dnf` commands are that they all download the needed dependencies of the package, and the disadvantage of the `rpm` is downloading the dependencies of the main package first, then the main package after that.

**Can you share a scenario where you had to troubleshoot a package management issue?**
- I never had a package issue, but I use Arch Linux, and I try my best to avoid the AUR repository because it's community-based. Meaning anyone can upload malware into the AUR repo. For example, recently someone actually uploaded three Remote Access Tojan (RAT) packages, `librewolf-fix-bin`, `firefox-patch-bin`, & `zen-browser-patched-bin` that I know of. I think the word `patch` within the package release is very odd & suspicious to me because they are usually numbered longer. The real package names are `librewolf-bin`, `firefox-bin`, & `zen-browser-bin`. My main point is that when using the AUR repository, for example, be careful when downloading packages. You might end up downloading malware, and for those who downloaded malware from the AUR repository, remove it.

### Process Management (103.5, 103.6)
**How do you create, monitor, and terminate processes in Linux?**
- I use `htop` over `top` because it's more organized by color. I'm not really a fan of viewing my notes in black and white, like the `ps` command, how it's displayed. For example, system-wide CPU usage blue means low priority.

**Discuss the use of commands like ps, top, kill, and how you modify process priorities with nice and renice.**
- Use the `ps aux` command to view all non-live running commands, or just use `top` to view live running commands. Or even better, the `htop` command with color!
- Try to find non-important commands and remember the PID. When using the `kill` command, it **terminates** the command, not forcefully **kills** the command; remember, they are different.
- and lastly the `nice` & `renice` commands. I rarely use them, but they are used to lower the priority of commands when needed.

**Can you provide an example of when adjusting process priorities was necessary?**
- I rarely adjust priorities; tasks sometimes use too much CPU. The Linux user can lower or prioritize specific tasks when needed, for example, `nice -1 wget https://wordpress.org/latest.zip` by setting the priority to a higher number to get more CPU time.