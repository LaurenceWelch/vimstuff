```vim
:filetype on

autocmd VimEnter * call SetCommentChar()

let commentCharacter="#"

map <leader>c :call Comment(1)<CR>
map <leader>u :call Comment(2)<CR>
map <leader>C :call Comment(3)<CR>
map <leader>U :call Comment(4)<CR>

function SetCommentChar()
    let t = &filetype
    if t == 'python'
        let g:commentCharacter = '#'
    elseif t == 'javascript'
        let g:commentCharacter = '//'
    endif
endfunction

function CommentLine(n, opt)
    let l = getline(a:n)
    if a:opt == 1 | call setline(a:n, g:commentCharacter.l)
    else
        let length = len(g:commentCharacter)
        call setline(a:n, l[length:])
    endif
endfunction

function Comment(opt)
    if getline('.') == '' | return | endif
    let c = line('.')
    if a:opt == 1 || a:opt == 2
        call CommentLine(c, a:opt)
    else
        let a = search('^$', 'bn')
        let b = search('^$', 'n')
        if a > c | let a = 0 | endif
        if b < c | let b = line('$') + 1 | endif
        for i in range(a + 1, b - 1)
            call CommentLine(i, a:opt - 2)
        endfor
    endif
endfunction
```
