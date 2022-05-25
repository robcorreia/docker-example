# docker-example
# Docker

Comandos do docker

- docker version
- docker run -it (nome da imagem), exemplo node
- exit para sair da imagem, no caso do node, 2x control+c
- docker ps lista todos os containers ativos
- docker ps -a mostra todos containers do computador
- docker run -d (nome da imagem) para rodar em background e nao ocupar a aba do terminal
- docker stop + id da imagem rodando para o container que esta rodando em background
- docker run -p (porta) exporta uma porta no navegador e o nome da imagem exemplo (docker run -d -p 80:80 nginx)
- docker start + id/name para reiniciar o container (continuar algum trbalho por exemplo)
- docker run -d -p 80:80 —name (+ nome que voce quer do container) e o nome da imagem para renomear um container, exemplo docker run -d -p 80:80 —name nginx-docker nginx
- docker logs (nome do container) mostra tudo que foi feito
- docker rm (nomedocontainer) para remover uma imagem
- tag -f para forçar o comando
- docker image ls (listas todas images do computador)
- docker system prune (remove tudo que nao esta sendo utilizado)
- 
    
    

## criação de uma nova imagem

imagens são baseadas em arquivos

nome Dockerfile como padrão

- FROM (nome da imagem)
- WORKDIR diretorio onde voce quer salvar ( da pra acessar usando .)
- COPY arquivo que deve ser copiado passando o caminho (exemplo . ou o caminho do WORKDIR)
- RUN comando para rodar na imagem
- COPY .  . (copia tudo que tem aqui para o WORKDIR
- EXPORE (mais a porta) para o docker exportar a porta no numero certo
- CMD (comando para rodar a aplicacao)

### exemplo de Dockerfile para uma app simples de Node

```jsx
FROM node

WORKDIR /urs/src/app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD ["node", "index.js"]
```

## Buildar uma imagem criada

docker build . (. para o diretorio atual)

docker image ls para listar a imagem criada

copiar id 

rocker run - p 3000:3000 (expor a porta que eu quero rodar a imagem) -d + id da imagem

exemplo: docker run -p 3000:3000 -d e9006f5518bd

depois basta visualizar o que foi feito, exemplo acessar o browser localhost:3000

para atualizar a imagem, é necessario buildar novamente apos atualização de arquivos da app

docker run -d -p 3000:3000 --name node-docker d290742f50f9

### nomear a imagem dando uma tag para ela

docker build -t nomedaimagem . (. é o diretorio)

### remover imagens

docker rmi nomedaimagem se precisar usa um -f para forçar o comando