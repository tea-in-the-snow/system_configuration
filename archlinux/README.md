# Some instructions

## The hook

The hook is meant to update the `pkglist.txt`(/etc/pkglist.txt) after a pacman command, it should be placed in the directory `/usr/share/libalpm/hooks/`

## Using "pkglist.txt" to quickly set up a system

The command to install packages through `pkglist.txt`:

```terminal
pacman -S --needed - < pkglist.txt
```

To rule out yay packages:

```terminal
pacman -S --needed $(comm -12 <(pacman -Slq | sort) <(sort pkglist.txt))
```

To remove those packages not in `pkglist.txt`:

```terminal
pacman -Rsu $(comm -23 <(pacman -Qq | sort) <(sort pkglist.txt))
```
