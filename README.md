

Plugin manager:  https://github.com/junegunn/vim-plug/wiki/tutorial

- Install all the vim packages
```
yum install vim-minimal vim-common vim-enhanced vim-filesystem
```

# Download plugin manager and install

- Download plugin manager into Vim (~/.vim/autoload)
```
curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
```
-  or copy it 
```
cp plug.vim ~/.vim/autoload/
```

- Edit ~/.vimrc
```
color desert
autocmd FileType yaml setlocal et ts=2 ai sw=2 nu sts=0

" Specify a directory for plugins
" - Avoid using standard Vim directory names like 'plugin'
call plug#begin('~/.vim/plugged')
" Make sure you use single quotes
Plug 'Yggdroot/indentLine'
" Initialize plugin system
call plug#end()
```

- After adding the above to the top of your Vim configuration file, reload it `:source ~/.vimrc` or restart Vim. 
- Now run `:PlugInstall` to install the plugins.

- Update the .vimrc file with all the plugins from the vimrc file
```
cp ./vimrc ~/.vimrc
```
- Rerun `:Pluginstall`

## **Updating plugins**

Run :PlugUpdate to update the plugins. After the update is finished, you can review the changes by pressing D in the window. Or you can do it later by running :PlugDiff.

## **Reviewing the changes**

Updated plugins may have new bugs and no longer work correctly. With :PlugDiff command you can review the changes from the last :PlugUpdate and roll each plugin back to the previous state before the update by pressing X on each paragraph.

## **Removing plugins**

1. Delete or comment out Plug commands for the plugins you want to remove.
2. Reload vimrc (:source ~/.vimrc) or restart Vim
3. Run :PlugClean. It will detect and remove undeclared plugins.

**Errors**
RHEL8 uses vi minimal which doesn't support plugins
Either use vim and relink the /usr/bin/vi command
mv /usr/bin/vi /usr/bin/vi.old
ln -s /usr/bin/vim /usr/bin/vi
