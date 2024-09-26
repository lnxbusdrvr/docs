# Right way to modify SpaceVim vimrc

## Use init.toml not vimrc

Use ~/.SpaceVim.d/init.toml
for custom settings, not ~/.Spacevim/vimrc

Example of custom vimrc in 
name = "better-defaults" and extra_settings = '''.

~/.SpaceVim.d/init.toml:
```toml
# init.toml
[options]
  # Disable error bells
  visualbell = true

[[layers]]
  name = "better-defaults"
  extra_settings = '''
    " Set tab width to 2 spaces
    set tabstop=2
    set shiftwidth=2
    set expandtab
    
    " Disable error bell
    set noeb vb t_vb=
    
    " Set encoding to ISO-8859-1 (Latin-1)
    set encoding=latin1
    set fileencoding=latin1
  '''

```
