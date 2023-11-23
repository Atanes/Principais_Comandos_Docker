# Principais_Comandos_Docker
Listagem dos principais comandos do Docker

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


