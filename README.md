# Setup Inicial do Linux Mint

##### Versão utilizada: 19.2 - Tina | 03/10/2019

### 1. Atualizar pacotes
- Utilizar o *Update Manager* e adicionar mirror's *(Ex. UFPR e C3SL)*
- Atualizar pacotes pelo Update Manager ou rodar seguinte comando
    `sudo apt update && sudo apt upgrade -y`

### 2. Instalar Git
- Adicionar PPA `sudo add-apt-repository ppa:git-core/ppa`
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
```
Caso já não esteja configurado no arquivo `~/.profile`, adicione
`export PATH=$HOME/.local/bin:$PATH` ao arquivo `~/.bashrc`

### 4. Instalar PHP e MySQL

### 5. Estilização e outras cutomizações
- Pacote de ícones [McMojave Circle](https://www.cinnamon-look.org/p/1305429/)
- Tema *Adapta-Nokto*
- Adicionar `redshift -O 4000` aos *Startup Applications*

### 6. Limpeza geral
Remoção de pacotes que não foram instalados completamente
`sudo apt-get autoclean`
Remoção do apt-cache
`sudo apt-get clean`
Remoção de dependências indesejadas
`sudo apt-get autoremove`
