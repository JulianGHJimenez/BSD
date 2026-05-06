# Contenido de couchDB

Enlace a la presentacion: https://docs.google.com/presentation/d/10UvX3cDDllSOJUPvPShSK1FEMAMVYhuV/edit?usp=sharing&ouid=108933785635092925997&rtpof=true&sd=true

Enlace a Apache couchDB(guia de instalacion): https://docs.couchdb.org/en/stable/install/unix.html

Enlace a Fauxton: http://127.0.0.1:5984/_utils

## Instalacion:

sudo apt update && sudo apt install -y curl apt-transport-https gnupg
curl https://couchdb.apache.org/repo/keys.asc | gpg --dearmor | sudo tee /usr/share/keyrings/couchdb-archive-keyring.gpg >/dev/null 2>&1
source /etc/os-release
echo "deb [signed-by=/usr/share/keyrings/couchdb-archive-keyring.gpg] https://apache.jfrog.io/artifactory/couchdb-deb/ ${VERSION_CODENAME} main" \
    | sudo tee /etc/apt/sources.list.d/couchdb.list >/dev/null
    
sudo apt update
sudo apt install -y couchdb

Modelo a instalar: Standalone o clustered → elige Standalone

sudo apt-get --no-install-recommends -y install \
    build-essential pkg-config erlang \
    libicu-dev libmozjs185-dev

- Prueba a hacer un curl -u <tu_user:tu_contra> http://127.0.0.1:5984/ y si te dice {welcome ...} entonces ya funciona correctamente.
- En caso de que no arranque prueba a usar:

sudo systemctl start couchdb
sudo systemctl enable couchdb

## Consultas basicas:
curl -u <admin:paswword> -X GET http://localhost:5984/tiendaonline/_all_docs?include_docs=true
 
- El "_all_docs" permite ver todo el contenido de la base de datos
- El "?" permite concatenar la condicion de busqueda
- El "include_docs=true" permite poner la condicion de poder ver toda la documentacion integrada en la base de datos, como id, nombres, categorias y mas...

Lo siento pero no tendras mas acceso a esta base de datos aparte de esto, a menos que importes la base de datos.

## Importar
Te preguntaras como importarla, verdad? pues la solucion te la dejo más abajo.

1. Descarga los .json que estan en el repo.
2. En la terminal colocaras la siguien linea en la ubicacion del archivo descargado, primero hazlo con la tiendaonline y despues con el _user.
 
curl -X POST http://<tu_usuario:tu_contra>@localhost:5984/tiendaonline/_bulk_docs \
-H "Content-Type: application/json" \
-d @<nombre_del_json>

3. Ya deberias de poder ver tu base de datos en tu fauxton o aplicando un curl.
4. Si hay conflicto a la hora de importar la base de datos se debe a los _rev, prueba a eliminarlos.
