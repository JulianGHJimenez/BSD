##Contenido de couchDB

Enlace a la presentacion: https://docs.google.com/presentation/d/10UvX3cDDllSOJUPvPShSK1FEMAMVYhuV/edit?usp=sharing&ouid=108933785635092925997&rtpof=true&sd=true

Enlace a Apache couchDB(guia de instalacion): https://docs.couchdb.org/en/stable/install/unix.html

Enlace a Fauxton: http://127.0.0.1:5984/_utils

##Consultas basicas:

#Permite hacer una consulta simple:
curl -u <admin:paswword> -X GET http://localhost:5984/tiendaonline/_all_docs?include_docs=true
 
- El "_all_docs" permite ver todo el contenido de la base de datos
- El "?" permite concatenar la condicion de busqueda
- El "include_docs='true'" permite poner la condicion de poder ver toda la documentacion integrada en la base de datos, como id, nombres, categorias y mas...

Lo siento pero no tendras mas acceso a esta base de datos aparte de esto, a menos que te descarges los backup.json que son la base de datos en si y lo importes a la tuya propia.


