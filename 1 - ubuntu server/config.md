# _Configuração do Ubuntu Server e instalação do Cockpit_

###  Neste projeto está sendo utilizada uma VM (VirtualBox) com a iso do Ubuntu Server na sua versão 22.04.2 LTS.

----

## 1.1 Configuração do Ubuntu
Não é necessária nenhuma configuração específica durante o processo de instalação. Portanto, proceda com a instalação normalmente.

Com o servidor instalado, rode o comando de atualização:
``` 
sudo apt update 
```

----

## 1.2 Instalação do Cockpit
Pronto, com o servidor atualizado podemos partir paraa a instalação do Cockpit que também é bem simples:
``` 
sudo apt install cockpit
```

Logo em seguida inicie os serviços do cockpit e habilite o serviço para que seja iniciado automaticamente durante o boot da máquina:
``` 
sudo systemctl start cockpit
```
``` 
sudo systemctl enable cockpit 
```

------

## 1.3 Configuração da VM
Com o serviço em execução, é essencial configurar adequadamente a máquina virtual para permitir o redirecionamento de portas. Essa configuração é necessária para que o servidor hospedado na máquina virtual possa ser acessado a partir da máquina real.

<div>
<img src="..\redirecionamentoporta.png"/>  
<img src="..\configportcockpit.png">
</div>

Note que foi criado uma nova regra com base nas minhas configurações. No entanto, se o endereço IP da sua máquina virtual for diferente, certifique-se de inseri-lo no campo "IP do convidado". É importante mencionar que a porta padrão do cockpit é a 9090 e não é necessário alterá-la. Quanto ao endereço IP do hospedeiro, esse deve ser definido como o endereço de loopback da sua máquina real, portanto, não é necessária nenhuma alteração nesse sentido.

Com essa configuração pronta podemos acessar o navegador de nossa máquina real e digitar o ip http://127.0.0.1:9090 e se tudo ocorreu bem irá ser aberto o painel de login do Cockpit. Faça login com o usuário e senha do seu servidor e pronto. Agora podemos partir para a instalação do Docker.
