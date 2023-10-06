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
