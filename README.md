# Principais_Comandos_Docker

## Comandos básicos
Para utilizarmos o Docker é preciso conhecer alguns comandos e entender de forma clara e objetiva como funcionam e para que servem, nesse repositório vamos ver alguns desses comendos junto com alguns exemplos de utilização para facilitar seu entendimento e aplicação. 🤔

## Executando um container
Um container só pode ser iniciado a partir de uma imagem e por isso temos alguns comandos do Docker que podemos usar para listar, pegar e atualizar essas imagens.  
Para listar as imagens que você tem na máquina é só executar o comando abaixo:

`docker image list`  
Uma lista com as imagens presentes na sua máquina é apresentada na tela indicando que elas foram criadas e ou baixadas do Docker host em algum momento.  
Caso deseje atualizar alguma dessas imagens você pode utilizar o comando:  

`docker image pull node`  
Nesse caso estou solicitando ao Docker que atualize a imagem do node que tenho na minha máquina com as ultima versão existente no Docker hub. Para atualizar qualquer outra imagem é só mudar o nome da imagem que deseja atualizar no final do comando.

Se desejar inspecionar a imagem que acabou de atualizar, basta usar o comando:  

`docker image inspect node`  
A diretiva **inspect** nesse comando é responsável por informar todos os dados referentes à imagem.

Agora com a imagem atualizada e inspecionada, podemos iniciar o container com o comando:  

`docker container run -it --rm --name node_test node bash`  
Vamos tentar entender melhor cada parte desse comando e como ele funciona efetivamente.  

Estrutura base: `docker container run <parâmetros> <imagem> <CMD> <argumentos>`  
Os parâmetros mais utilizados na execução do container são:

| Parâmetro |	Aplicação / Utilização                                                    |
|-----------|---------------------------------------------------------------------------|
| -d        | Execução do container em background                                       |
| -i        | Modo interativo. Mantém o STDIN aberto mesmo sem console anexado          |
| -t        | Aloca uma pseudo TTY                                                      |
| --rm      | Automaticamente remove o container após finalização (Não funciona com -d) |
| --name	  | Dar um nome para o container                                              |
| -v	      | Mapeamento de volume                                                      |
| -p	      | Mapeamento de porta                                                       |
| -m	      | Limitar o uso de memória RAM                                              |
| -c	      | Balancear o uso de CPU                                                    |

Sendo assim quando olhamos para o comando anterior `docker container run -it --rm --name node_test node bash` vamos entender que um container com o nome **node_test** será iniciado e terá como base de craição a imagem **node** e o **bash** será executado no container ao final da sua construção e execução.  

Caso o **CMD** não seja especificado no comando `docker container run`, é utilizado o valor padrão definido no Dockerfile da imagem utilizada. No nosso caso é node e seu comando padrão executa o node, ou seja, se não fosse especificado o bash, no final do comando de exemplo acima, ao invés de um shell bash do GNU/Linux, seria exibido um shell do node.  

## Listagem dos principais comandos do Docker

docker ps  
docker ps -a  
docker ps -a -q  
  - Lista todos os IDs dos contaners ativos no computador

docker run hello-world   
docker run -it ubuntu bash  
docker start stoic_dirac  
docker stop 3c80eaaf7cd5  
docker run -it --rm ubuntu bash  
docker run -p 8080:80 nginx  
docker run -d -p 8080:80 nginx  
docker rm 2b6c164a8428  
  - Remove o container com o ID especificado no comando

docker rm crazy_khorana -f  
  - Remove o container com o nome especificado no comando

docker rm $(docker ps -a -q) -f  
  - Remove todos os containers ativos pelos seus ids

docker run -d --name nginx -p 8080:80 nginx  
docker run --rm -d --name nginx --network host nginx  
  - Conecta o host do docker com a máquina, dessa forma após o comando você consegue acessar a aplicação direto pelo localhost;
  - Esse comando não funciona no MAC OS.

docker exec nginx ls  
docker exec -it nginx bash  
docker run -d --name nginx -p 8080:80 -v ~/my-project/:/usr/share/nginx/html nginx  
docker run -d --name nginx -p 8080:80 --mount type=bind,source=/my-project/,target=/usr/share/nginx/html nginx  
docker run -d --name nginx -p 8080:80 --mount type=bind,source="$(pwd)"/my-project/,target=/usr/share/nginx/html nginx  
docker volume create meuvolume  
docker run --name nginx -d --mount type=volume,source=meuvolume,target=/app nginx  
docker inspect meuvolume  
docker volume ls  
docker volume prune  

docker images 
docker rmi imagem:tag  

Com arquivo Dockerfile no mesmo diretório onde estamos rodando os comandos  
docker build -t teste_go . 

**Para WSL2 usar docker compose no lugar de docker-compose**  
docker compose up  
docker compose up -d --build  
docker compose down

docker logs db  

Sequencia de comandos para limpar Docker local:  
 - sudo docker rm -f $(docker ps -a -q) 
 - sudo docker rmi -f $(docker images -q)
 - sudo docker system prune -af
 - sudo docker volume prune -f


