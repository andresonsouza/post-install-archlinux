# Pós-instalação do Arch Linux

## Brave Browser

```BASH
git clone https://aur.archlinux.org/brave-bin.git
cd brave-bin
makepkg -si
```

## Wine-staging

```BASH
sudo pacman -Sy
sudo pacman -S wine-staging winetricks
sudo pacman -S giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo libxcomposite lib32-libxcomposite libxinerama lib32-libxinerama ncurses lib32-ncurses opencl-icd-loader lib32-opencl-icd-loader libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader cups samba dosbox
```

## ASDF

```BASH
git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.7.6
echo -e '\n. $HOME/.asdf/asdf.sh' >> ~/.bashrc
echo -e '\n. $HOME/.asdf/completions/asdf.bash' >> ~/.bashrc
```

## Principais Linguagens

### Clojure

```BASH
asdf plugin-add clojure https://github.com/vic/asdf-clojure.git
asdf list-all clojure
asdf install clojure 1.10.1 #update_version
asdf global clojure 1.10.1 #update_version
```

### kotlin

```BASH
asdf plugin-add kotlin https://github.com/missingcharacter/asdf-kotlin.git
asdf list-all kotlin
asdf install kotlin 1.3.61 #update_version
asdf global kotlin 1.3.61 #update_version
```

### Elixir

```BASH
asdf plugin-add elixir https://github.com/asdf-vm/asdf-elixir.git
asdf list-all elixir
asdf install elixir 1.9.4 #update_version
asdf global elixir 1.9.4 #update_version
```

### Erlang

```BASH
asdf plugin-add erlang https://github.com/asdf-vm/asdf-erlang.git
asdf list-all erlang
asdf install erlang 22.1.8 #update_version
asdf global erlang 22.1.8 #update_version
```

### Golang

```BASH
asdf plugin-add golang https://github.com/kennyp/asdf-golang.git
asdf list-all golang
asdf install golang 1.13.5 #update_version
asdf global golang 1.13.5 #update_version
```

### Ruby

```BASH
asdf plugin-add ruby https://github.com/asdf-vm/asdf-ruby.git
asdf list-all ruby
asdf install ruby 2.6.5 #update_version
asdf global ruby 2.6.3 #update_version
```

### Rust

```BASH
asdf plugin-add rust https://github.com/code-lever/asdf-rust.git
asdf list-all rust
asdf install rust 1.39.0 #update_version
asdf global rust 1.39.0 #update_version
```

### Crystal

```BASH
asdf plugin-add crystal https://github.com/marciogm/asdf-crystal.git
asdf list-all crystal
asdf install crystall 0.32.0 #update_version
asdf global crystal 0.32.0 #update_version
```

### NodeJs

```BASH
asdf plugin-add nodejs https://github.com/asdf-vm/asdf-nodejs.git
bash ~/.asdf/plugins/nodejs/bin/import-release-team-keyring
asdf list-all nodejs
asdf install nodejs 10.18.0 #update_version
asdf global nodejs 10.18.0 #update_version
npm i -g npm
```

## Angular

```BASH
npm install -g @angular/cli
```

## Typescript

```BASH
npm install -g typescript
```
## TypeStrong

```BASH
npm install -g ts-node
```

## Instalação do PHP

```BASH
sudo pacman -Syu &&
sudo pacman -S php &&
php -v
```

## Install PHP Extensions
```BASH
sudo pacman -Syu &&
sudo pacman -S php-apache php-cgi php-fpm php-gd  php-embed php-intl php-imap  php-redis php-snmp &&
pacman -Qi php-fpm
```

## Instalação Laravel
```BASH
sudo pacman -Syu &&
sudo pacman -S php apache php-apache mariadb composer &&
composer global require "laravel/installer" &&
echo 'export PATH="$HOME/.config/composer/vendor/bin:$PATH"' >> .bashrc &&
echo 'export PATH="$HOME/.config/composer/vendor/bin:$PATH"' >> .zshrc
```

## Biblioteca pra gerar projetos React

```BASH
npm i -g create-react-app
```

## Surge - Static web publishing for Front-End Developers - <https://surge.sh/>

```BASH
npm install -g surge
```

## Visual Studio Code

```BASH
sudo pacman -Sy visual-studio-code-bin
```

## MongoDB

```BASH
yay -Sy mongodb-bin
systemctl enable --now mongodb
```

## Postgresql

```BASH
sudo pacman -Sy postgresql
sudo -u postgres -i
initdb --locale $LANG -E UTF8 -D '/var/lib/postgres/data'
exit
```

### Não faça isso em máquinas de produção

```BASH
sudo sed -i.bak 's/ident/trust/' /var/lib/postgres/data/pg_hba.conf
sudo systemctl start postgresql
sudo systemctl enable postgresql

sudo -u postgres -i
createuser --interactive # create with your username and superuser role
createdb youruser
exit
sudo systemctl restart postgresql
```

## Docker

```BASH
sudo pacman -Sy docker
sudo usermod -aG docker $USER
sudo systemctl start docker
sudo systemctl enable docker
```

```BASH
base=https://github.com/docker/machine/releases/download/v0.16.0 &&
curl -L $base/docker-machine-$(uname -s)-$(uname -m) >/tmp/docker-machine &&
sudo mv /tmp/docker-machine /usr/local/bin/docker-machine &&
chmod +x /usr/local/bin/docker-machine
```

## Docker Compose - <https://github.com/docker/compose/releases>

```BASH
sudo -i
curl -L https://github.com/docker/compose/releases/download/1.25.1-rc1/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

## Docker Machine - <https://github.com/docker/machine/releases>

```BASH
curl -L https://github.com/docker/machine/releases/download/v0.16.2/docker-machine-`uname -s`-`uname -m` >/tmp/docker-machine &&
chmod +x /tmp/docker-machine && sudo cp /tmp/docker-machine /usr/local/bin/docker-machine
```

## Redis, Memcached

```BASH
sudo pacman -Sy redis memcached
sudo systemctl start redis
sudo systemctl enable redis
sudo systemctl start memcached
sudo systemctl enable memcached
```

## ZSH

```BASH
sudo pacman -Sy zsh
sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
echo zplugin light zdharma/fast-syntax-highlighting >> ~/.zshrc
```
