parseTV3
========

Petit script que permet descarregar-se la programació dels diferents canals de Televisió de Catalunya en format XMLTV, el format estàndard reconegut per qualsevol media center mínimament decent, com ara TVHeadend, MythTV, MediaPortal o semblants.

Ús del programa
---------------

La invocació és molt senzilla, basta executar:

parseTV3.py .

Es generarà al directori actual un fitxer XMLTV per a cada canal i dia. Si no s'indica una altra cosa amb el paràmetre -d, es descarreguen 3 dies de programació a partir de la data actual. 

Per defecte es descarrega la informació de TV3 Cat, 33 i Canal Super 3. Es poden afegir/eliminar canals modificant la variable de configuració CANALS que es troba al principi del fitxer. Els identificadors són els que apareixen al final de la URL de la web de TV3 quan consultam la programació. Per exemple, si consultam la programació de TV3 HD pel 3 d'abril, la URL és http://www.tv3.cat/programacio/20140403/3hd, de manera que l'identificador seria "3hd".

Si això de generar tants fitxers diferents no va bé, potser perquè el programa a on els volem emprar només n'admet un, es poden juntar tots els fitxers en un mitjançant la utilitat tv_cat que ve de sèrie amb el pack d'utilitats xmltv-utils. És tan fàcil com fer: 

tv_cat -o sortida.xmltv *.xmltv

En algun moment modificaré el programa perquè només generi un fitxer gran, però de moment s'ha de fer així.

Instal·lació i dependències
---------------------------

En principi no fa falta cap configuració especial per executar parseTV3. Basta tenir un intèrpret de Python instal·lat, i ja hauria de funcionar. Les úniques coses que no formen part de les llibreries estàndard de Python són les llibreries BeautifulSoup i el parser lxml. Si pel que sigui no estan instal·lades al sistema (són bastant comunes i és probable que ja hi siguin), s'han d'instal·lar. Generalment basta amb fer pip install XXX i s'instal·la automàgicament.

Tot i que el programa hauria de ser multiplataforma, totes les proves les he fet a sistemes Linux, concretament a Ubuntu, de manera que no sé si a Windows o altres sistemes operatius funcionarà tot bé. He intentat fer les coses de forma estàndard i independent del sistema operatiu, però podria ser que aparegués algun problema amb les rutes dels fitxers, o amb els encodings del text. Si els accents no surten bé, o directament falla en algun moment perquè no pot convertir entre encodings, és que passa alguna cosa així. Deixau-me un comentari al github i potser ho miraré.

Comentari legal
---------------

Per acabar, no tenc molt clara la legalitat d'extreure i manipular aquest tipus d'informació des de la web de TVC. De totes formes, i tenint en compte que es tracta de canals públics i no hi ha interés lucratiu (només vull tenir informació de la programació al meu media center) no veig per què hauria d'haver-hi cap problema. En qualsevol cas, recoman que es faci un ús responsable de l'eina i, per exemple, no es consulti la programació massa sovint (amb una vegada al dia hi ha més que suficient). No cal dir que no em faig responsable de cap ús negatiu/fraudulent/dolent en general que es faci d'aquest programa, així com tampoc de cap dany que aquest pugui causar. La idea és que funcioni bé, i jo sóc el primer interessat en què sigui així (el faig servir a diari), però no puc donar cap tipus de garantia.
