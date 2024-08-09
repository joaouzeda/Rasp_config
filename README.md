<h1 align="center"> Mosquitto Config </h1>


<h22 align="center"> Fixando o Ip </h2>

O primeiro passo é verificar o ip que Raspverry esta utilizado

```
    ~ netstat -nr
```

Apos isso editar o arquivo dhcpcd, para isso utilizar o comando

```
    ~ sudo nano/etc/dhc.conf
```
E no topo do aquivo digiar as linhas

```
interface wlan0
    ~ static ip_adress = {seu futuro ip}/{mascara de rede}
    ~ static routers = {ip do roteador}
    ~ static domain_name_server = {ip do roteador} 8.8.8.8 8.8.4.4  
```

Após isso salvar o arquivo cliando " Ctrl + x " e depois " S "; e reniciar a Raspberry

```
    ~ reboot
```

<h22 align="center"> Instalando o Mosquitto </h2>

Para instalar verificamos 

```
    ~ sudo apt-get update
    ~ sudo apt-get upgrade
```

```
    ~ sudo apt-get install mosquitto -y
    ~ sudo apt-get install mosquitto-client -y
```


```

```

```

```

```

```

```

```

```

```

```

```