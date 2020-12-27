# My-vim-movidas

## With spaceVim, in ~/.Spacevim:

### Edit bundle/neomake/autoload/neomake/makers/ft/php.vim
Change neomake#makers#ft#php#psalm() to this:
  function! neomake#makers#ft#php#psalm() abort
      let maker = {
         \ 'exe': './vendor/bin/psalm', <--- This is the important part
         \ 'args': [
            \ '--output-format=pylint',
            \ '--diff'
         \ ],
         \ 'errorformat': '%A%f:%l:%\s[%t%n]%\s%m',
         \ }
      return maker
  endfunction

### Edit vendor/vimeo/psalm/src/Psalm/Progress/LongProgress.php and comment every $this->write() line that 
you don't want to see in the error output.

### Edit ~/.SpaceVim/config/neovim.vim and add:

  let g:neomake_php_enabled_makers = ['php', 'psalm']
