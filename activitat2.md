# Instalar Owncloud en Ubuntu 20.04 LTS.

Per instalar el apache2 fem la comanda 

![alt text](Selecció_001.png)

Desactivem el llistat de directoris del servidor:

![alt text](Selecció_002.png)

# Instalar MariaDB:

Instal·lem MariaDB

![alt text](Selecció_003.png)

I configurem la instal·lació:

![alt text](Selecció_004.png)

Aquí hem de modificar el seguent:

![alt text](Selecció_005.png)

Finalment reiniciem el servidor MariaDB.

![alt text](Selecció_006.png)

Crear la base de dades d'owncloud:

Entrem a MariaDB:

![alt text](Selecció_007.png)

Creem la base de dades:

![alt text](Selecció_008.png)

Creem un usuari anomenat ownclouduser amb una contrasenya que podria ser Admin1234.

![alt text](Selecció_009.png)

Us donem accés a l'usuari a la base de dades creada:

![alt text](Selecció_010.png)

Apliquem els canvis i sortim:

FLUSH PRIVILEGES;
EXIT;

# Instal·lar PHP i els seus mòduls necessaris:

![alt text](Selecció_010.png)

Actualitzem els paquets amb el repositori afegit:

![alt text](Selecció_011.png)

Instal·lem PHP i els mòduls necessaris:

![alt text](Selecció_012.png)

Hem de tenir en compte els requisits d'Owncloud abans d'instal·lar els mòduls.

![alt text](Selecció_013.png)

Després de la instal·lació editem el fitxer php.ini i canviarem alguns valors:

![alt text](Selecció_014.png)

Els valors que hem de canviar són els següents:

file_uploads = On allow_url_fopen = On memory_limit = 256M upload_max_filesize = 100M display_errors = Off date.timezone = Europe/Madrid

# Instal·lem Owncloud:

Descarreguem la darrera versió del programa i descomprimim els fitxers, a més movem els fitxers d'Owncloud a "/var/www/html/owncloud".

![alt text](Selecció_015.png)

Canviem propietari i permisos dels directoris d'owncloud. www-data perquè els pugui fer servir Apache, 755 perquè els pugui executar i llegir qualsevol usuari de Linux:

![alt text](Selecció_016.png)

![alt text](Selecció_017.png)

![alt text](Selecció_018.png)

![alt text](Selecció_019.png)

![alt text](Selecció_020.png)

# Configurar Apache:

Configurarem Apache:

![alt text](Selecció_021.png)

Hem de deixar un fitxer com el següent, però canviant el ServerName i el ServerAlias pels noms i àlies del nostre propi domini.

![alt text](Selecció_022.png)

Habilitem owncloud i el mòdul rewrite:

![alt text](Selecció_023.png)

![alt text](Selecció_024.png)

Reiniciem Apache:

A partir d'aquest moment podem accedir a owncloud des del navegador per això hem d'introduir la nostra IP seguida de "/owncloud" al mateix, per exemple si la nostra IP és 172.31.84.197 posarem al navegador 172.31.84.197/owncloud i podrem accedir al servei.

Ja al navegador creem un compte d'administració i posem les dades de MariaDB que hem configurat anteriorment.

# Que es apache

La funcionalitat principal daquest servei web és servir als usuaris tots els fitxers necessaris per visualitzar el web. Les sol·licituds dels usuaris es fan normalment mitjançant un navegador (Chrome, Firefox, Safari, etc.).

Per exemple, quan un usuari escriu al seu navegador dinahosting.com, aquesta petició arribarà al nostre servidor Apache que mitjançant el protocol HTTP aquest s'encarregarà de facilitar-vos els textos, imatges, estils, etc. que conformen la portada de la nostra web de manera segura.

Apache té una estructura basada en mòduls, que permet activar i desactivar funcionalitats addicionals, per exemple, mòduls de seguretat com mod_security, mòduls de memòria cau com Varnish, o de personalització de capçaleres com mod_headers. També permet ajustar els paràmetres de PHP del teu hosting de manera personalitzada mitjançant el fitxer .htaccess.

## Què fa la comanda a2ensite?
Enjaga el owncloud

## I la comando a2dissite?
Apaga el owncloud

## Què significa la línia de /etc/hosts
Aqui configurem els nostres dominis que voldrem entrar a la nostra pagina de owncloud.
