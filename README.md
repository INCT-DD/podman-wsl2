# podman-wsl2

## AVISO

**O WSL2 está disponível apenas para versões do Windows 10 Pro/Enterprise/Workstations iguais ou superiores à 2004, Compilação 19041. Para checar a versão/compilação do Windows você está executando, rode o comando `winver` no terminal de sua preferência.**

**Além disso, é preciso que as funções de virtualização de hardware estejam habilitadas na BIOS de seu dispositivo**

## Como habilitar o WSL e instalar o WSL2

Para habilitar o WSL em um sistema Windows que cumpra os requisitos apresentados no aviso anterior, inicie um terminal do Powershell como administrador e execute os seguintes comandos, na ordem em que são apresentados abaixo:

```powershell
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux -NoRestart
Enable-WindowsOptionalFeature -Online -FeatureName VirtualMachinePlatform
```

Ao final, o Windows solicitará que o seu sistema seja reiniciado. Caso isto não aconteça, reinicie o seu dispositivo manualmente e efetue login como de costume. Inicie um novo terminal do Powershell como administrador e execute os seguintes comandos, na ordem em que são apresentados abaixo:

```powershell
wget https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi -o wsl_update_x64.msi
msiexec /i ./wsl_update_x64.msi
```

Isso iniciará um prompt de instalação. Prossiga com a instalação como de costume e então retorne ao terminal e execute:

```powershell
wsl --set-default-version 2
```

Isso irá configurar o WSL2 como a versão padrão do WSL a ser utilizada em seu sistema. Uma vez que esta etapa da configuração tenha sido finalizada, instale sua versão favorita do Linux utilizando a Microsoft Store.

## Como instalar o podman no WSL2

Como estas etapas podem mudar de acordo com a liberação de novas versões do podman, recomendamos que siga as etapas referentes à distribuição de sua escolha apresentadas no site oficial da ferramenta: https://podman.io/getting-started/installation

## Como configurar o podman no WSL2

Neste repositório você encontrará uma versão do arquivo `containers.conf` configurada para rodar dentro do WSL2. Tome alguns minutos do seu tempo para checar as opções *não comentadas* para entender as modificações feitas à configuração padrão. Uma vez que esteja confortável de que as tenha revisado, copie o arquivo `containers.conf` fornecido neste repositório para os diretórios `$HOME/.config/containers/` e `/etc/containers/`. É possível que o gerenciador de pacotes de sua distribuição tenha criado versões padrão destes arquivos, as quais recomendamos que sejam substituídas pela deste repositório.

## Como utilizar o podman no WSL2

O podman possui uma interface CLI compatível com o Docker. Para mais informações sobre como utilizar a ferramenta para gerenciar e executar seus containers, por favor cheque a documentação oficial em: http://docs.podman.io/en/latest/
