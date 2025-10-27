## File Editing in Linux (103.8): 
Compare the editing modes in vi with another text editor you're familiar with.
- I use to use `nano` then I realized `vim` is better than `nano`, why I switched? vim has more features. My favorite editing feature is switching between files. The instructions below is a built-in functionality in vim.
    1. First open at least two files or more, in command mode `:e /file/path` x3
    1. To switch between files/buffers, list all avaliable files/buffers by `:ls` in command mode.
    1. To select a specific file/buffer, `:b [NUM]` in command mode.

What are the advantages or disadvantages of vi's insert, command, and visual modes for a Linux user?
**Disadvantages, only for new users**
- When I first started using vim, I had trouble exiting vim. That's when in `insert mode`.

**Advantages**
- Sometimes I forget to use `sudo` when editing root files. That means I can't save my buffer and I will lose my new data. `:w`, `:w!` won't work but using `:w! /home/USER/Documents/tempfile.txt` works temporary. I only use this when saving nonsensitive information btw.

## Regular Expressions for File Searching (103.7): 
### What challenges have you faced or anticipated when working with regular expressions?
The only challenge I faced was looking for URLs within html pages. Trying to find urls that had, ...
- File extensions: `.html`, `.json`, & `.png`
- URL protocols: `https` & `http`, trying to avoid `http` because it's spooky. Always use `https` because It's secure!
- SRC URLs, URLs that are internal not external.

All of that had there own special regular expression.

### Share an example of a basic regular expression pattern and how it can be used to extract meaningful data from a file.
I use to do web scraping for fun, for example. grabbing all urls to download them all with wget instead of clicking the url one by one.

`index.html`
```html
<!DOCTYPE html>
<html>
<body>

<h2>Absolute URLs</h2>
<p><a href="https://www.w3.org/" target="_blank">W3C</a></p>
<p><a href="https://www.google.com/" target="_blank">Google</a></p>

<h2>Relative URLs</h2>
<p><a href="html_images.asp">HTML Images</a></p>
<p><a href="/css/default.asp">CSS Tutorial</a></p>

</body>
</html>
```
`grep --only-matching 'href="[^"]*"' local-file.html` **Output**
- `--only-matching`, This will only display it's attribute and value insted of the full html tag that it came from.
- `'href="[^"]*"'` - the url
    - `[]`, Matches any single character inside the brackets.
    - `^"`, Matches any character except a double quote.
    - `*`, Any number of characters that are not double quotes.
```
href="https://www.w3.org/"
href="https://www.google.com/"
href="html_images.asp"
href="/css/default.asp"
```

The code above is for local files only but if you don't want to use local files you can insted use, `curl --silent http://example.com | grep --only-matching 'href="[^"]*"'`
- `--silent` This will git rid of the extra information for example, when piping output, this extra information will follow along without `--silent`.
    ```
    % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                    Dload  Upload   Total   Spent    Left  Speed
    100 65559  100 65559    0     0   228k      0 --:--:-- --:--:-- --:--:--  228k
    ```