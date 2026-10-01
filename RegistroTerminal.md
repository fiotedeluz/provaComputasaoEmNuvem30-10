RA: a7850c44436a53c25468

gleidson Alves

 ##registro da prova

por questões de segurança e praticidade estou usando o user root e foi criada uma pasta temporaria contendo apenas o conteudo da prova

foi criada uma pasta e criado um arquivo html, seguimos então por criar um conteiner nginx/alpine chamado estoque para onde foi enviado o arquivo html

foi executado o comando docker ps e curl para verificar o funcionamento dos conteiners e entao o e chamalo confirmando o conteudo enviado para dentro do conteiner Estoque

agora segue o registro do meu terminal pessoal onde foi executada a prova pratica

##Terminal
root@uwubura:/temp# mkdir prova
root@uwubura:/temp# cd prova
root@uwubura:/temp/prova# vim index.html
root@uwubura:/temp/prova# root@ubuntu:~/prova$ docker run -d --name estoque -p 8085:80 nginx:alpine
-bash: root@ubuntu:~/prova$: Arquivo ou diretório inexistente
root@uwubura:/temp/prova# docker run -d --name estoque -p 8085:80 nginx:alpine
Unable to find image 'nginx:alpine' locally
alpine: Pulling from library/nginx
0deea27e58d9: Download complete 
e2de96513ba9: Pull complete 
6c53d0b2a666: Pull complete 
e72112c14215: Pull complete 
d9aae54b5831: Pull complete 
9a9a644fdd6a: Pull complete 
e76228b47809: Pull complete 
64c8194480fe: Pull complete 
745dfb2690dd: Pull complete 
d54d3939625e: Download complete 
Digest: sha256:df221db836e1754089190208cee7eeda94f233197056426eda74a43ab1abeac2
Status: Downloaded newer image for nginx:alpine
ff4b3526d0fe6ef89936e754a289848166db5ec5c8e59c708c886531b4a22d45
root@uwubura:/temp/prova# 
docker cp index.html estoque:/usr/share/nginx/html/index.html
docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                                     NAMES
ff4b3526d0fe   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8085->80/tcp, [::]:8085->80/tcp   estoque
root@uwubura:/temp/prova# 
root@uwubura:/temp/prova# curl http://localhost:8085
<!DOCKTYPE>
<HTML LANG="pt-BR">
<head>

	<meta charset="UTF-8">
	<title>Estoque </title>

</head>

<body>

	<h1>Estoque Disponivel </h1>

</body>

</html>


root@uwubura:/temp/prova# 

##verificação do conteiner
docker ps
CONTAINER ID   IMAGE          COMMAND                  CREATED              STATUS              PORTS                                     NAMES
ff4b3526d0fe   nginx:alpine   "/docker-entrypoint.…"   About a minute ago   Up About a minute   0.0.0.0:8085->80/tcp, [::]:8085->80/tcp   estoque
root@uwubura:/temp/prova# 

##teste da pagina
root@uwubura:/temp/prova# curl http://localhost:8085
<!DOCKTYPE>
<HTML LANG="pt-BR">
<head>

	<meta charset="UTF-8">
	<title>Estoque </title>

</head>

<body>

	<h1>Estoque Disponivel </h1>

</body>

</html>


root@uwubura:/temp/prova# 

##explicação
a diferença entre imagem e conteiner e para que serviu o mapeamento das portas 8085:80
a imagem é um modelo permitindo a criação de um conteiner, o conteiner Estoque e uma imagem ja executada e preenchida com os dados passados

