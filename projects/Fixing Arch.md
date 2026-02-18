# Thursday February 12, 2026
Updated arch last night to install steam and we woke up to 1381,935 errors.

![[Pasted image 20260212101330.png]]

Boy that is a terribly optimized photo

# Break things in chunks, but create backups first

- Change or remove one thing at a time
	- With every change, run `hyprctl reload`
	- if it breaks, you know what broke bloke
- Make backups
```bash
cp -r ~/.local/share/omarchy/default/hypr ~/.local/share/omarchy/defaul/t/hypr.backup
```
- Basically making a copy of the folder int a .backup file
	- How does it work? not sure yet
- When something breaks, check the errors:

```bash
journalctl -xe | grep hypr
journalctl -u uwsm_hyprland.desktop -f # Listen to active logs
timedatectl status # check the hardware time
journalctl -u uwsm_hyprland.desktop -f # follows user session
hyprctl errors
```

```

```


# The Ultimatum

- Rip out everything that is not absolutely essential to fix the errors, and we will reclaim our arch setup by creating our own config and ripping out omarchy
- for now fix the syntax errors
