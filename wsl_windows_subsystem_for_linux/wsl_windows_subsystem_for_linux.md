# Windows Subsystem for Linux

The developers at Microsoft explained it best [Windows Subsystem for Linux overview](https://blogs.msdn.microsoft.com/wsl/2016/04/22/windows-subsystem-for-linux-overview/).

## Turn on WSL under Windows 10
Though WSL is available to all Windows 10 users, it must still be turned on manually. In order to do this:

Navigate to `Control Panel` > `Programs and Features` > `Turn Windows features on or off`. Now, enable `Windows Subsystem for Linux`. Windows will require you to restart your computer.

Now that you have WSL enabled, you can download one of the officially supported Linux containers from the `Microsoft Store`. I would recommend using [Debian](https://www.microsoft.com/en-us/p/debian/9msvkqc78pk6?activetab=pivot:overviewtab) or [Ubuntu](https://www.microsoft.com/en-us/p/ubuntu/9nblggh4msv6?activetab=pivot:overviewtab).

## Enable Linux metadata under WSL
Since [build 17063](https://docs.microsoft.com/en-us/windows/wsl/release-notes#build-17063) the WSL filesystem plugin DrvFS can be configured at boot to, amongst other things, store Linux metadata. This resolves some of the file permission issues that people may have experienced in the past when working with files from the host machine (win10) as well as inside the WSL container. Below is a blog post article explaining the various configuration options:

https://devblogs.microsoft.com/commandline/automatically-configuring-wsl/

Feel free to copy my [wsl.conf](https://github.com/99linesofcode/dotfiles) to `/etc/wsl.conf` into your Linux distro of choice.

## Symlink $HOME to C:/Users/You
As I find myself developing on multiple platforms across different containerization and virtualization methods I strive to keep all of my `dotfiles/` in one place if possible.

In order to achieve this, I've simply created a symbolic link pointing from the `home/` directory under Debian to my `home/` directory on the host machine:

`ln -s ~/home /mnt/c/Users/Jordy`

## Troubleshooting

### SSH Agent Forwarding causes system halt BSOD #3916
When attempting to use SSH agent Forwarding you might run into a system halt error which causes a BSOD and your system to reboot. This is a known issue and supposedly resolved in one of the most recent 1809 fall updates: https://github.com/Microsoft/WSL/issues/3916

Also be sure to check out https://github.com/Microsoft/WSL/issues/3183 should the problem persist and consider downgrading the `openssh-agent` package as is recommended there.
