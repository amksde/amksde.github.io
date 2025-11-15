---
title: IdeaVimRC
draft: false
date: "2025-11-20T00:00:00+05:30"
lastmod: "2025-11-20T00:00:00+05:30"
---

```
"" -- Suggested options --
" Show a few lines of context around the cursor. Note that this makes the
" text scroll if you mouse-click near the start or end of the window.
set scrolloff=5

" Do incremental searching.
set incsearch
set nu rnu

"ignore case while searching"
set ic

" set the new escape key"
inoremap jk <ESC>
nnoremap <C-d> <C-d>zz
nnoremap <C-u> <C-u>zz
" Don't use Ex mode, use Q for formatting.
map Q gq

" --- Enable IdeaVim plugins https://jb.gg/ideavim-plugins

" Highlight copied text
Plug 'machakann/vim-highlightedyank'
" Commentary plugin
Plug 'tpope/vim-commentary'

"" -- Map IDE actions to IdeaVim -- https://jb.gg/abva4t
"" Map \r to the Reformat Code action
"map \r <Action>(ReformatCode)

"" Map <leader>d to start debug
"map <leader>d <Action>(Debug)

"" Map \b to toggle the breakpoint on the current line
"map \b <Action>(ToggleLineBreakpoint)
```