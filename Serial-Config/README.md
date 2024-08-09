<h1 align="center"> Serial Config </h1>

A raspberry possui duas portas de comuniação uart, sendo uma ttyAMA0 (equivalente a COM1) e a miniuart chamada ttyS0.

É possivel conferir as portas serial rodando o comando abaixo

```
    $  ls -1 /dev
```


<h2 align="center"> Habilitando a comunicação serial </h2>

Para inicar a configuração do uart é primeiro preciso habilitar os pinos do serial para isso utiliza-se o comando

```
    $ sudo nano /boot/config.txt
```

E neste arquivo adicionar essa linha, abaixo, no final do arquivo;

```
    enalbe_uart = 1 
```

Após isso salve o arquivo cliando " Ctrl + x " e depois " S "

<h2 align="center"> Desabilitando o console </h2>

Por padrão a Raspberry utiliza a comunicação serial para o console e para utilizar o uart é necessario desativar o console 

```
    $ sudo systemctl stop serial-getty@ttyS0.service
    $ sudo systemctl disable serial-getty@ttyS0.service
```

É também necessario remover o console do cmdline.txt 

```
    $ sudo nano /boot/cmdline.txt
```

Dentro do arquivo terá algo parecido com

```
    dwc_otg.lpm_enable=0 console=serial0,115200 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes root wait 
```

Agora é so apagar a parte do console=serial,115200 salvar o arquivo e sair.