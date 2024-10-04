# P2-Montando-Volumes-en-Apache

Comproba que a tes a imaxe httpd

**Para comprobar se temos a imaxe httpd xa descargada utilizaremos o seguinte comando:**
```
docker images
```
**Unha cousa importante é que se nos costa atopar esta imaxe podemos apoiarnos con grep e o nome da imaxe xa que filtrara entre todas as imaxes sendo moito máis doado atopar a imaxe que queremos. Se non temos esta imaxe utilizaremos o seguinte comando para descargala:**
```
docker pull httpd
```


Crea un contenedor de nome 'asir_httpd'.

**Antes de empezar creando o contenedor deberemos de crear un novo directorio co mesmo HTML para todos os contenedores que e o solicitado máis adiante, para esto utilizaremos o seguinte comando para crear o directorio**
```
mkdir -p /home/ivan/htdocs
```
**Unha vez creado o directorio faremos un echo co queramos que teña o noso HTML co seguinte comando:**
```
echo "<h1>Benvido ao servidor Apache</h1>" > /home/ivan/htdocs/index.html
```
**Unha vez feito isto imos a crear o noso contenedor co comando:**
```
docker run -d --name asir_httpd
```


Mapea o porto 80 do contenedor có 8080 da túa máquina. Utiliza bind mount para que o directorio do apache2 'htdocs' estea montado nun directorio da túa elección.  Utiliza -v "$PWD"/htdocs:/usr/local/apache2/htdocs/

**Para mapear e comprobar que o porto esta dispoñibel e engadir o contenedor utilizaremos o seguinte comando:**
```
docker run -d --name asir_httpd -p 8080:80 -v /home/ivan/htdocs:/usr/local/apache2/htdocs/ httpd
```
**Con esto montamos o noso servidor apache co contenedor co porto indicado**

Mostra unha páxina html aloxada no apache2 dende o teu navegador.

**Para mostrar esta paxina abriremos un navegador web e visitaremos a nosa paxina que estara xestionada polo noso contenedor: http://localhost:8080 . Este e o enlance que utilzaremos para comprobar o noso servidor apache**

Crea un contenedor 'asir_web1' que use este mesmo directorio para 'htdocs' e o puerto 8000

**Para este paso utilizaremos a base do mesmo comando que no punto 3 e non debería de haber ningun problema xa que estamos utilizando otro porto diferente ao anterior e non debería de pisarse e ao compartir o mesmo directorio "htdcos" tendra o mismo HTML o comando é**
```
docker run -d --name asir_web1 -p 8000:80 -v /home/ivan/htdocs:/usr/local/apache2/htdocs/ httpd
```
**Isto deberia ser suficiente para que funcione a paxina**

Crea outro contenedor 'asir_web2' có el mesmo directorio e otro puerto, como o 8090.

**Faremos o mesmo que no paso anterior pero cambiando o porto**
```
docker run -d --name asir_web2 -p 8090:80 -v /home/ivan/htdcos:/usr/local/apache2/htdocs/ httpd
```

Comproba que los dous servidores mostran a mesma páxina

**Por último para comprobar que os dous servidores mostran a mesma paxina web buscaremos no noso navegador web os comandos:**

```
http://localhost:8000/
http://localhost:8090/
```

