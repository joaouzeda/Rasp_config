<h1 align="center"> Mosquitto Config </h1>


<h2 align="center"> Fixando o Ip </h2>

O primeiro passo é verificar o ip que Raspverry esta utilizado

```
    $  netstat -nr
```

Apos isso editar o arquivo dhcpcd, para isso utilizar o comando

```
    $  sudo nano/etc/dhc.conf
```
E no topo do aquivo digiar as linhas

```
    interface {wlan0 para wifi e eth0 para ethernet}
    static ip_adress = {seu futuro ip}/{mascara de rede}
    static routers = {ip do roteador}
    static domain_name_server = {ip do roteador} 8.8.8.8 8.8.4.4  
```

Após isso salve o arquivo cliando " Ctrl + x " e depois " S "; e reniciar a Raspberry

```
    $  reboot
```

<h2 align="center"> Instalando o Mosquitto </h2>

Para toda instalação primeiro verificar a se existe algum pacote novo e/ou atualização

```
    $  sudo apt-get update
    $  sudo apt-get upgrade
```

Apos a atualização podemos instalar o mosquitto e o mosquitto-client 


```
    $  sudo apt-get install mosquitto -y
    $  sudo apt-get install mosquitto-client -y
```

<h2 align="center"> Criando o arquivo de configuracao </h2>

Agora tem que criar o arquivo de configuração    

```
    $  sudo nano /etc/mosquitto/mosquitto.conf 

```

Dentro desse arquivo, localize e apague a seguinte linha 

```
    include_dir /etc/mosquitt/conf.d
```

e inclua 

```
    allow_anonymous false 
    password_file /etc/mosquitto/passwd
    listener 1883
```
Após isso salve o arquivo cliando " Ctrl + x " e depois " S ".

Com isso bloqueamos o acesso de usuarios anonimos, ou seja requer login e senha para broker, e indicamos o arquivo da senha e a porta do broker.

E em sequencia criamos o arquivo de senha com o seguinte comando
```
    $  sudo mosquitto_passwd -c /etc/mosquitto/pwfile {nome do usuario}
```
Com isso ira aparecer para digitar e comfirmara senha escolhida para o perfil.

É possivel verificar a senha utilizando o comando 
```
  $  cat /etc/mosquitto/pwfile
```
Após isso o broker ja esta instalado e configurado, faltando apenas reiniciar a raspberry e inicar o mosquitto

```
    $  reboot
    ...
    $  mosquitto
```