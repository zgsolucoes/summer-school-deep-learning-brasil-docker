# Execução da Imagem
Com o Docker instalado, resta executá-lo com uma das imagens disponibilizadas. Foram disponibilizadas duas imagens: uma com suporte a GPU e outra sem. Você deve utilizar a imagem com suporte a GPU apenas se seu computador possuir GPU e seu Sistema Operacional for o Linux. Caso tiver uma GPU e não estiver utilizando Linux, recomenda-se instalá-lo em sua máquina para utilizá-la (ela faz diferença no treinamento de redes neurais profundas).

Algo importante de se entender, antes de prosseguir, é que é necessário mapear uma pasta de seu computador como um "volume" do Docker. Isso significa que essa pasta será compartilhada entre seu Sistema Operacional e o Docker. Assim, a aplicação executada no Docker poderá ler e escrever nessa pasta. Caso esse mapeamento não fosse feito, seria complicado acessar os arquivos gerados no Docker e eles poderiam ser perdidos. Logo, prepare uma pasta (de preferência vazia) e guarde seu caminho, pois ele será passado no comando de inicialização do Docker. A partir de agora, referenciaremos essa pasta como `<workspace>`. Logo, quando encontrar isso no comando, você deverá substituir pelo caminho de sua pasta.

O nome da imagem disponibilizada é: `zgsolucoes/tensorflow-notebook`. Essa imagem está disponível no registro público do Docker (https://hub.docker.com/r/zgsolucoes/tensorflow-notebook). Os comandos disponibilizados a seguir realizam download dessa imagem na primeira vez em que forem executados.

## Comando para iniciar Jupyter Lab

Ao executar um dos comandos abaixo, um link na forma `http://localhost:8888/?token=4b2113a4256f5678b965bb190f590725962a2342e3b5031b` aparecerá em seu terminal. Copie e cole no navegador para abrir o Jupyter Lab.

### Sem GPU

#### Linux e MAC OS

```bash
docker run -it -p 8888:8888 -v <workspace>:/home/jovyan/work --user root -e NB_UID=$(id -u) -e NB_GID=$(id -g) zgsolucoes/tensorflow-notebook:latest start.sh jupyter lab
```

#### Windows

```bash
docker run -it -p 8888:8888 -v <workspace>:/home/jovyan/work zgsolucoes/tensorflow-notebook:latest start.sh jupyter lab
```

### Com GPU (apenas Linux)

Será necessário instalar o `nvidia-docker`, que está disponível apenas para Linux. Siga a instruções da [Documentação Oficial](https://github.com/nvidia/nvidia-docker/wiki/Installation-%28version-2.0%29). Depois de instalar e testar que seu hardware e drivers são compatíveis como explicado nas instruções, execute o comando a seguir para rodar a imagem.

```bash
nvidia-docker run -it -p 8888:8888 -v <workspace>:/home/jovyan/work --user root -e NB_UID=$(id -u) -e NB_GID=$(id -g) zgsolucoes/tensorflow-notebook:latest-gpu start.sh jupyter lab
```

### Observações

Os comandos anteriores executarão o Jupyter Lab, que está em Beta no momento. Caso prefira executar o clássico Jupyter no lugar, remova o final `lab` do comando.
