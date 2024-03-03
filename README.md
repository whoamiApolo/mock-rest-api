## Disciplina Microsserviços - Simulação de REST APIs

### Pasta raíz de todos os códigos: app1

```bash
# verificar se o cUrl está disponível
curl --version

# verificar se o docker foi devidamente instalado
docker

# descompactar arquivo app1.zip
unzip app1.zip

# acessar pasta app1
cd app1

# criar a imagem do container
docker build -t jsonserver .

# executar o container
# -d    Roda o container em background e exibe o ID do container
# –rm	Remove o container quando ele é encerrado
# -it   Inicia o modo interativo, acessa o terminal docker container via linha de comando
docker run -d --rm -it --name jsonserver-container -p 8080:8080 jsonserver

# acessar JSON-server via navegador
http://localhost:8080/

# testar chamada GET via linha de comando LINUX/MacOS
# utilize 127.0.0.1, caso localhost ou 0.0.0.0 não funcione
curl -X GET http://0.0.0.0:8080/filmes
curl http://0.0.0.0:8080/filmes

#ou Windows (cmd)
curl http://localhost:8080/filmes 
curl -X GET http://localhost:8080/filmes

# carregar mais dados através do arquivo data.json
# Na pasta app1, verificar se o arquivo carros.json está disponível (LINUX/MacOS)
ls -l data.json

# ou Windows (cmd)
dir data.json

# copiar o arquivo data.json para o container na pasta temp com o nome base.json 
docker cp data.json jsonserver-container:tmp/base.json

# listar o container ativo e anotar o container ID
docker ps

# reiniciar o container, adicionando o container ID
docker restart `ID_DO_CONTAINER`

# ou reiniciar via nome do container
docker restart jsonserver-container

# POST - Testar chamada via linha de comando LINUX/MacOS
curl -i -H "Accept: application/json" -H "Content-type: application/json" -X POST http://localhost:8080/carros -d '{"id":"9","marca":"audi","modelo":"q7"}'

# ou Windows (cmd)
curl -i -H "Accept: application/json" -H "Content-type: application/json" -X POST http://localhost:8080/carros -d '{\"id\":\"9\",\"marca\":\"audi\",\"modelo\":\"q7\"}'

# PUT - Testar chamada via linha de comando LINUX/MacOS
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X PUT http://localhost:8080/carros/9 -d '{"id":"9","marca":"bmw","modelo":"x1"}'

# ou Windows (cmd)
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X PUT http://localhost:8080/carros/9 -d '{\"id\":\"9\",\"marca\":\"bmw\",\"modelo\":\"x1\"}'

# PATCH - Testar chamada via linha de comando LINUX/MacOS
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X PATCH http://localhost:8080/carros/9 -d '{"id":"9","modelo":"x2"}'

# ou Windows (cmd)
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X PATCH http://localhost:8080/carros/9 -d '{\"id\":\"9\",\"marca\":\"bmw\",\"modelo\":\"x2\"}'

# DELETE - Testar chamada via linha de comando LINUX/MacOS
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X DELETE http://localhost:8080/carros/9

# ou Windows (cmd)
curl -i -H "Accept: application/json" -H "Content-Type: application/json" -X DELETE http://localhost:8080/carros/9
