ssh-key-service
================

Per user ssh-agent service that doesn't need systemd.

# Installation
1. Clone this repo
2. Install the file **ssh-key-service** to your home with
```
install -m=770 -o=$USER:$USER ssh-key-service "$HOME/.ssh-key-service"
```

## Basic Setup
1. After installing add the service to your *~/.xinitrc* or to your DE startup
2. Append something like this to your *~/.bashrc* or *~/.zshrc* (or whatever, depending on your shell):

```bash
if [[ -f $HOME/.cache/ssh-agent-session ]]; then
    source "$HOME/.cache/ssh-agent-session"
fi
```

You are done :)

## Advanced Setup
If you want to load keys from other path then "$HOME/.ssh", just edit the array **SSH_KEYS_DIRS** and add to it as many path as you like E.G. :

```bash
SSH_KEYS_DIRS=("/path/to/keys1" "/path/to/keys2")
```

Note that the script will **not** look for keys recursively, so if you have keys in a subpath they won't be loaded.

Also be care that the script check the integry for each file in the directory you specify, so if you put a big directory it *may* slow your startup time.
