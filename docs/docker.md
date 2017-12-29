# Instalação do Docker
O primeiro passo é a instalação do Docker. Existem várias opções de instalação de acordo com o Sistema Operacional utilizado. Deve-se instalar a versão Community Edition por ser gratuita. O seguinte link possui instruções (em inglês) de como proceder:

[https://docs.docker.com/engine/installation/](https://docs.docker.com/engine/installation/)

Os seguintes links possuem explicações em português:

* Ubuntu: [https://www.digitalocean.com/community/tutorials/como-instalar-e-usar-o-docker-no-ubuntu-16-04-pt](https://www.digitalocean.com/community/tutorials/como-instalar-e-usar-o-docker-no-ubuntu-16-04-pt)
* Windows: [https://talkitbr.com/2016/10/20/usando-docker-no-windows-10/](https://talkitbr.com/2016/10/20/usando-docker-no-windows-10/)
* Mac OS: [https://gabrielfelipesoares.wordpress.com/2016/01/28/rodando-docker-mac-os-x/](https://gabrielfelipesoares.wordpress.com/2016/01/28/rodando-docker-mac-os-x/)

## Passos extras para Linux

Após a instalação, você deverá conseguir rodar o comando `docker`, mas precisará utilizar um usuário root (`sudo` no Ubuntu). Para que isso não seja mais necessário, você deve adicionar seu usuário no grupo `docker`. Assim, ele terá permissão para invocar o Docker diretamente.

Como root, execute o comando: `sudo usermod -aG docker $(whoami)`
