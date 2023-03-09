
# _Instalação e configuração do Docker_

## 2.1 Instalação do Docker

### Os seguintes comandos serão dados dentro do terminal que o Cockpit nos oferece.

-----

Primeiro vamos instalar as dependências necessárias para o Docker:
```
sudo apt-get install -y apt-transport-https ca-certificates curl gnupg-agent software-properties-common
```

Em seguida adicionamos a chave GPG oficial do Docker:
```
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
```

Agora vem o repositório do Docker:
```
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
```

Após estes comandos o Docker está pronto para ser instalado. Mas antes devemos atualizar novamente o SO:
```
sudo apt update
```

Por fim vamos instalar o Docker:
```
sudo apt-get install docker-ce docker-ce-cli containerd.io
```

------

## 2.2 Configurações do Docker

Primeiro vamos ativar o serviço do Docker:
```
sudo systemctl start docker
```

Habilitamos o serviço para ser iniciado automáticamente:
```
sudo systemctl enable docker
```

Agora vamos adicionar o nosso usuário ao grupo do docker, para que não seja necessário usar o comando SUDO toda vez que for executar um comando Docker:
```
sudo usermod -aG docker nome_de_usuario
```
```
sudo usermod -aG docker ${USER}
```

Execute ambos os comandos, altere apenas o primeiro comando no campo nome_de_usuario substituindo-o pelo nome de usuário que você está utilizando. Após isto faça log-out da sessão e inicie novamente. Você pode testar com o comando:
```
id  -nG
```
Com este comando irá aparecer os grupos a qual seu usuário faz parte,  se lá estiver o grupo do Docker é sinal de que funcionou.
