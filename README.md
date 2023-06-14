# Imagens Docker

Nesse projeto estão as imagens docker do DockerHub do Abner e os compose.yaml exemplo para ajudar no desenvolvimento de aplicações

## Requerimentos

Docker
Docker Compose (este normalmente ja vem junto com o instalador do docker)

## Utlizando com o docker compose

Entre na pasta da imagem que gostaria de usar

Exemplo
```
$ cd apache-php
```

Clone o docker compose example para dentro da pasta raiz do seu projeto
```
$ cp docker-compose.yaml.example docker-compose.yaml
```

Altere as portas externas caso necessário dentro do arquivo docker-compose.yaml, caso as portas não estejam em uso basta pular essa etapa
```
    # como esta no original
    ports:
        - '80:80' 

    # a porta que você deve alterar apenas se necessário é o primeiro 80, por exemplo
    ports:
        - '8000:80' # Onde a primeira é a porta da sua maquina e a segunda é a porta do container
```

Execute o comando para subir os containers
```
$ docker compose up -d
```