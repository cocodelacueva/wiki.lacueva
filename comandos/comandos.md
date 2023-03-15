# COMANDOS


## VSCODE

Para agregar code a la terminal hay que:
Open the Command Palette (Cmd+Shift+P) and type 'shell command' to find the Shell Command: Install 'code' command in PATH command.

Para copiar las extensiones que tenemos hay que poner en terminal:
MAC:
code --list-extensions | xargs -L 1 echo code --install-extension
WINDOWS:
code --list-extensions | % { "code --install-extension $_" }

Y luego copiar el output que nos genera y podemos instalar uno por uno.
Por ejemplo:
code --install-extension aaron-bond.better-comments

Para sincronizar con Github instalar esta extensión:
https://marketplace.visualstudio.com/items?itemName=Shan.code-settings-sync

## GIT

* git reflog (te muestra donde estuvo el head y que hizo por mas que modificaciones se hicieron)
* git reset —soft  hash (cambia el head a donde lo apuntas y sin perder los cambios de los archivos y los deja en stage para que comitees)
* git reset —mixed hash (cambia el head a donde lo apuntas y sin perder los cambios de los archivos pero queda en el workdirectory para agregarlos)
* git reset —hard hash (cambia el head y perdes todo, si hiciste commit, podes volver a recuperar con git reflog)
* git stash (guarda lo que no esta en stage en algún lugar para poder guardarlo después, se puede hacer varias veces y se va haciendo una lista)
* git stash list
* git stash pop (agrega el ultimo del stash y lo borra del stage)
* git stash apply hash (agrega el indicado pero no lo borra de la lista de stash)



---


## DOCKER


### CONSTRUYE LA IMAGEN:
docker build -t nombre_repo .
(El punto es porque estas parado dentro del directorio)


### CONSTRUYE EL CONTENEDOR
docker run -t -i -p 8011:80 nombre_repo
docker run -t -d -i --name=nombre_repo -p 8020:3000 chatbot
docker run --rm -t -e MYSQL_ALLOW_EMPTY_PASSWORD=true mysql:5.7


### ENTRAR EN EL CONTENEDOR Y VER LA TERMINAL
docker exec -i -t 7e80656e001b /bin/bash


### BORRAR TODO
docker system prune --volumes
docker run -d -p 8004:80 170287751818.dkr.ecr.sa-east-1.amazonaws.com/portinos.blog

## En Mac con M1
a veces hay que incluir esto: platform: linux/x86_64 en docker compose

---


## AWS:

### Aww cli
aws s3 ls
aws s3 ls s3://nombrebucket

COPIAR DESDE LOCAL A BUCKET
aws copy archivo.ext s3://nombrebucket

COPIAR DESDE BUCKET A LOCAL
aws s3 cp s3://BUCKETNAME/PATH/TO/FOLDER LocalFolderName —recursive

SINCRONIZAR BUCKET CON CARPETA LOCAL
aws s3 sync s3://<source_bucket> <local_destination>
https://docs.aws.amazon.com/cli/latest/reference/s3/sync.html

### ECR
-LOGIN:
aws ecr get-login --region sa-east-1 --no-include-email
$(aws ecr get-login --no-include-email --region us-east-1)

---

## PHP

php -S localhost:8000
php -S 192.168.0.55:1111 -t public/
Al darle un ip se puede acceder desde el celular

---

## SSH:
-para conectarse
ssh portinosdev@192.168.5.199
(usuario@puertoOhost)

---

## BASH

Comprimir archivo en terminal:
tar -zcvf nombre-archivo.tar.gz nombre-directorio
(-z: Comprimir archivos usando gzip
-c: Crear un nuevo archivo
-v: Verbose, es decir, mostrar el proceso durante la creación del archivo
-f: nombre de archivo)
Descomprimir un archivo
tar -xvzf miarcho.tar.gz
(-x: extrae el contenido del archivo comprimido
-v: Verbose, es decir, mostrar el proceso durante la creación del archivo
-f: nombre de archivo)

### SCP
COPIAR SERVIDOR POR SSH
scp -r marman123@elkhead.dreamhost.com:/home/marman123/mathaus.com.ar .
(el punto final es el directorio de destino)

### BASH PROFILE
alias composer="php /usr/local/bin/composer" export PATH="/Users/coco/.composer/vendor/bin:$PATH" export PATH="/Users/coco/dart-sass:$PATH" export PATH="/Users/coco/Library/Python/3.7/bin:$PATH"


---

## 3D threejs: gltf-pipeline

Compresión cld
gltf-pipeline -i city.gltf -o city.glb --draco.compressionLevel=10

--- 

## MONGO DOCKER

docker run --name some-mongo -d mongo
docker run -d -p 27017:27017 mongo

## Redis para docker

* Documentacion: https://hub.docker.com/_/redis/
* Descargar e iniciar container de redis: docker run -d -p 6379:6379 redis
* Entran en el contenedor: docker exec -it idcontenedor bash
* Entrar en redis cli: redis-cli
* Setear un pw, porque sino no funciona: config set requirepass 123
* Colocar la misma pw en el .env

## MySQL

* docker run -e MYSQL_ROOT_PASSWORD=secret -d -p 3306:3306 mysql:5.7
* connect in terminal:
```bash
mysql -u=USERNAME -p DATABASENAME 
```
-u: username
-p: password (**no space between -p and the password text**)
-h: host
last one is name of the database that you wanted to connect.

mysql -u=dbuser -p db 

## Actualizar wordpress en Base de datos

UPDATE wp_options SET option_value = replace(option_value, 'https://agencia.portinos.com/', 'http://localhost:8001/') WHERE option_name = 'home' OR option_name = 'siteurl';
UPDATE wp_posts SET post_content = replace(post_content, 'https://agencia.portinos.com/', 'http://localhost:8001/');
UPDATE wp_links SET link_url = replace(link_url, 'https://agencia.portinos.com/','http://localhost:8001/');
UPDATE wp_postmeta SET meta_value = replace(meta_value, 'https://agencia.portinos.com/','http://localhost:8001/');
UPDATE wp_posts SET guid = replace(guid, 'https://agencia.portinos.com/','http://localhost:8001/')
