# Setup Inicial do Linux Mint

##### Versão utilizada: 19.2 - Tina | 03/10/2019

### 1. Atualizar pacotes
- Utilizar o *Update Manager* e adicionar mirror's *(Ex. UFPR e C3SL)*
- Atualizar pacotes pelo Update Manager ou rodar seguinte comando
    `sudo apt update && sudo apt upgrade -y`
- `sudo apt install build-essential`

### 2. Instalar Git
- Adicionar PPA `sudo add-apt-repository ppa:git-core/ppa`
- `sudo apt update`
- Instalar com `sudo apt install git`
- Configurar com
`git config --global user.name "_NOME_"`
`git config --global user.email "_EMAIL_"`

### 3. Instalar Node.js e npm
Instalação na pasta .local da home

**Lembrar de substituir o link da linha 5 pela [versão mais recente](https://nodejs.org/en/download/)**
```
cd ~
mkdir -p .local/bin
mkdir -p .local/node
cd .local/node
curl -O https://nodejs.org/dist/v10.16.3/node-v10.16.3-linux-x64.tar.xz
tar -xzf node-v10.16.3-linux-x64.tar.gz
ln -s node-v10.16.3-linux-x64 latest
cd ../bin
ln -s ../node/latest/bin/node
ln -s ../node/latest/bin/npm
export NPM_CONFIG_PREFIX=~/.local/node/latest
npm config set prefix '~/.local/node/latest'
```
Caso já não esteja configurado no arquivo `~/.profile`, adicione

`export PATH=$HOME/.local/bin:$PATH` ao arquivo `~/.bashrc`

### 4. Instalar PHP e MySQL
- Adicionar PPA do PHP `sudo add-apt-repository ppa:ondrej/php`
- `sudo apt update`
--------
- Instalar o Apache2 `sudo apt install apache2`
- Verificar com `sudo systemctl status apache2`
- `sudo a2enmod rewrite`
- `sudo systemctl restart apache2`
--------
- Instalar o MySQL com `sudo apt install mysql-server`
```
sudo mysql -u root
SELECT User,Host FROM mysql.user;
DROP USER 'root'@'localhost';
CREATE USER 'root'@'localhost' IDENTIFIED BY '';
GRANT ALL PRIVILEGES ON *.* TO 'root'@'localhost' WITH GRANT OPTION;
FLUSH PRIVILEGES;
```
--------
- Instalar o PHP com `sudo apt install php7.3`
```
sudo apt install php7.3-cli libapache2-mod-php7.3 php7.3-mysql php7.3-curl php-memcached php7.3-dev php7.3-pgsql php7.3-sqlite3 php7.3-mbstring php7.3-gd php7.3-json php7.3-xml php7.3-zip php7.3-bcmath php7.3-soap php7.3-intl php7.3-readline
```
--------
- Instalar o Composer
```
cd ~/.local/bin/
wget https://getcomposer.org/download/1.9.0/composer.phar -O composer
sudo chmod 755 composer
```

### 5. Estilização e outras cutomizações
- Pacote de ícones [***McMojave Circle***](https://www.cinnamon-look.org/p/1305429/)
- Tema *Adapta-Nokto*
- Adicionar `redshift -O 4000` aos *Startup Applications*
- Pacotes para o Atom
    - File Icons
    - Tree View Auto Resize
    - Highlight Selected
    - Language Vue

### 6. Limpeza geral
Remoção de pacotes que não foram instalados completamente

`sudo apt-get autoclean`

Remoção do apt-cache

`sudo apt-get clean`

Remoção de dependências indesejadas

`sudo apt-get autoremove`
