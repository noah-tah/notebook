# Thursday February 12, 2026
Updated arch last night to install steam and we woke up to 1381,935 errors.

![[Pasted image 20260212101330.png]]

Boy that is a terribly optimized photo

# Break things in chunks, but create backups first

- Change or remove one thing at a time
	- With every change, run `hyprctl reload`
	- if it breaks, you know what broke bloke
- Make backups
`cp -r ~/.local/share/omarchy/default/hypr ~/.local/share/omarchy/default/hypr.backup`

