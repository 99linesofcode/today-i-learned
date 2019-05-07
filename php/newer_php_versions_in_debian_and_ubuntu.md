# Install newer versions of PHP that those available in default package repository

Debian Developer Ondřej Surý maintains a separate package archive where he packages (amongst other things) PHP packages. Simply add the archive for PHP to your own list of repositories like so:

**Ubuntu**

```zsh
sudo add-apt-repository ppa:ondrej/php &&
sudo apt-get update
```

**Debian**

```zsh
sudo apt-get -y install lsb-release apt-transport-https ca-certificates &&
sudo wget -O /etc/apt/trusted.gpg.d/php.gpg https://packages.sury.org/php/apt.gpg &&
echo "deb https://packages.sury.org/php/ $(lsb_release -sc) main" | sudo tee /etc/apt/sources.list.d/php7.3.list &&
sudo apt-get update
```

Now that you have added the new package repository for PHP, in this case 7.3, you can install it through aptitude as you normally would:

```zsh
sudo apt-get install php7.3
```

The package repository that you added also contains packages for commonly used PHP extensions and can be installed in similar fashion. The command below installs commonly used, recommended, packages:

```zsh
sudo apt-get install php7.3-bcmath php7.3-bz2 php7.3-curl php7.3-gd php7.3-intl php7.3-json php7.3-mbstring php7.3-readline php7.3-xml php7.3-zip
```

## Troubleshooting

### Locale issues

You may find that installing the package fails due to locale issues caused by the package developers surname. Make sure to set your locale to `UTF-8` as described here: https://github.com/oerdnj/deb.sury.org/issues/56. I would recommend adding the following lines to your shell profile:

```zsh
locale-gen en_US.UTF-8
export LC_ALL=en_US.UTF-8
export LANG=en_US.UTF-8
```
