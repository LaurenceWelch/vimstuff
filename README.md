# vimstuff

# what are these?
These tidbits can be tossed into your .vimrc file to add some additional functionality.

# basic config
The first line maps jk (k is pressed after j, not at the same time) to ESC. This makes leaving insert mode easier.
The next line maps `'` as the leader key. The leader key can be used to create something akin to a macro (Vim also has macros). If you for example wanted to insert the word hello before a sentence, you could do the following.
```vim
:map <leader>a Ihellojk
``` 
Pressing the leader key and then `a` would be like typing `I` (go to the start of the line and enter insert mode), `hello` (type in hello), and `jk` (exit insert mode with our custom remapping).
The next lines revolve around changing the tab button to 4 spaces instead of 8. In addition, the `<>` keys can be used to shift a line by 4.

# comments
The commentFunction script brings in single line and block level commenting. The line `:filetype on` causes vim to populate the filetype variable with the type of file being edited. For example it might be a javascript file or a python file. As you can imagine, the autocmd command causes vim, upon opening, to run the SetCommentChar function which, depending on the filetype, sets the comment variable accordingly. The next lines map c, u, C, and U to different types of comments; uppercase being block level and lowercase being single line. The basic idea behind the Comment function is, look for a blank line above the current line and below the current line, comment out everything between those two lines. Logic has to be added in situations where the file starts or ends before a blank line is discovered.

# run
The runFunction file allows you to `<leader>r` to run your code without leaving vim. To mitigate bad things from happening, the run function won't work until you call AllowRun. If you for example are editing a file called `helloworld.py`, you can do the following:
```vim
:call AllowRun('python3 helloworld.py')
```
The `w` command hanging out all by itself in the RunSomething function writes the current file, saving you from having to `:w` everytime.
