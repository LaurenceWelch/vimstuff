```vim
let allowRun = -1

map <leader>r :call RunSomething()<CR>

function AllowRun(s)
    echo 'running enabled'
    echo 'command: '.a:s
    echo '<leader>r to run'
    let g:allowRun = 1
    let g:runCommand = a:s
endfunction

function RunSomething()
    if g:allowRun != 1 | echo 'call AllowRun([str]) to enable' | return | endif
    w
    execute '!'.g:runCommand
endfunction
```
