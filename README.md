# BTCPayServer-Video
Lista de comandos:
## Generar par de llaves SSH
  `$ ssh-keygen -b 4096` 
  
  ## Copiar llave pública
  
  ` $ cat ~/.ssh/id_rsa.pub `
  
## Acceso a VPS por terminal
  ` $ ssh root@LA_IP_DE_TU_VPS `

## Actualizar el Servidor
  `sudo apt-get update`     
  
  `sudo apt-get upgrade`
  
## Añadir seguridad:
  ```
##Denegar todos los puertos no permitidos explícitament##

sudo ufw default deny incoming
sudo ufw default allow outgoing

##Permitir acceso SSH##

sudo ufw allow ssh

##Permitir HTTP para verificacion LetsEncrypt##

sudo ufw allow http

##Permitir HTTPS para the BTCPay Server UI##

sudo ufw allow https

##Activar UFW##

sudo ufw enable
```

## Preparación inicial

```
# Loguearse como root
sudo su 

# Crear carpeta para BTCPay

mkdir BTCPayServer

cd BTCPayServer

#Clonar el repositorio##

git clone https://github.com/btcpayserver/btcpayserver-docker

cd btcpayserver-docker
```

## Preparar BTCPay Server para Monero
```
# Antes de instalar, metemos estos parametros uno a uno
# Aquí va tu sub-dominio

export BTCPAY_HOST="btcpay.EXAMPLE.com"

# Activar el soporte para Monero

export BTCPAYGEN_CRYPTO1="xmr"

# Soporte Tor

export BTCPAYGEN_ADDITIONAL_FRAGMENTS="opt-add-tor"

# Activar HTTPS reverse proxy + SSL certs via Nginx and LetsEncrypt

export BTCPAYGEN_REVERSEPROXY="nginx"

# Permitir administrar por UI

export BTCPAY_ENABLE_SSH=true
```

## Instalar BTCPay Server
. ./btcpay-setup.sh -i

