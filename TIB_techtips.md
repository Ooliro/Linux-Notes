# EBM 2022
### Datos de acceso al servidor de bioinformática

IP del servidor: 132.248.220.16  
Puerto SSH: 2424  
Nombre de usuario: guest09  
Contraseña: P$j9PVHLqQ

Comando:
`$ ssh -X guest09@132.248.220.16 -p 2424`

Y luego la contraseña esa:
`P$j9PVHLqQ`

Si quieres cargar un archivo desde tu maquina local a una remota, se hace mas o menos asi:
`scp phyml_tutorial_data.tgz guest09@132.248.220.16:/home/guest09/sesion6_ML`

Si quieres descargar algo desde un repositorio github usas
`wget https://github.com/vinuesa/TIB-filoinfo`

### Datos de acceso a "Cursos del NNB-UNAM"

Usuario: raulolivaresrosas@gmail.com
Contraseña: mN#1z1/T

## Notas Importantes

[Guías de comandos de Linux](https://en.wikipedia.org/wiki/List_of_Unix_commands)

head -1 linux_basic_commands.tab | sed 's/\t/\n/g' | cat -n > wawa.txt
Toma el encabezado, acomodalo cambiando el tab por enter, y enumeralo… podría ser útil.

cat assembly_summary.txt | cut -f1,2 | head -3
Cortas los campos 1 y 2 (columnas) para que solo veas esas columnas cortadas!

cat assembly_summary.txt | grep Acinetobacter | grep Complete | cut -f8 |sort | uniq -c | sort -nrk1 | less
Busca una especie, busca solo genomas completos, corta el campo 8 que es el nombre del organismo, ordenalos, busca claves únicas y cuentalas, nordenalas de mayor a menos y paginalo.

grep '^>' recA.faa | cut -d' ' -f2,3 | sort | uniq -c | sort -nrk1 | awk 'BEGIN{OFS="\t";print "genus\species\tn_seq"}{print $2,$3,$1}'
Acomoda tu salida en con AWK para que se más fácil de guardar como tabla, da formato.

cat standard_blast_fields.tsv 16S_problema_blastN_maln1_m6.tab | column -t | head
No conocía esa madre de column. Puede ser útil!

seaview - Paquete multiplataforma para filogenética

pangenoma - Genoma núcleo compartida por todos los [] + el genoma dispensable, squishy, compartidos parcialmente y genes especificos de la especie.

Para el dominio de CS puede que haya aa núcelo. Si las dos proteínas son homologas podría haber forma de probarlo, no solo para que nos diga que lo son, sino dónde podrían serlo y así pulir aún más nuestras secuencias semilla con los dominios catalíticos de CS y HS. [BBH's, BDBH's, Get_homologues, COG's, y OrthoMCL si crees que puede ayudar]

Get_Homologues fue creado por el Dr. Pablo Vinuesa, y se corre en un servidor por el tiempo y recursos que puede consumir. Recomienda su instalación por Docker, ya que evita problemas de permisos y requerimientos mínimos del SO. Además, analiza genomas, proteomas, secuencias COMPLETAS de las especies que le des, no a nivel de dominio, pero aún así podría ser útil si resultara que los dominios de CS aparecen en el análisis pangenómico como core o shells.




![225d9ea614f6741300cb3c61351e1d78.png](225d9ea614f6741300cb3c61351e1d78.png)




## Apuntes
gedit - Es literlamente una forma de abrir tu editor de textos para editar algun archivo que selecciones. Un entorno gráfico de edición de textos

grep - si usas el gorrito ^ al inicio de tu búsqueda será más rápido ya que el incluir el gorrito le dice "busca solo al inicio de la línea"

Secuencias homologas - Sinónimas o No Sinónimas, dependiendo de si codifican para el mismo aminoácido o no. En codones, la modifiación en la posición 2 siempre resulta en mutaciones no sinónimas. Si dos proteínas o genes se parecen mucho a lo largo de toda su longitud asumimos que se trata de proteínas o genes homólogos, es decir, descendientes de un mismo ancestro común (cenancestro).

¿Usamos una secuencia de proteínas adecuada para un alineamiento global? Ya que nuestra secuencia problema (tesis) comparte homologia solo en el dominio de QS y HS, ¿sería mejor utilizar alineamientos locales?

Para lineamientos locales tenemos valores útiles como el valor de expectancia de Karlin-Altschul que describe la probabilidad de que los alineamientos hallan ocurrido al azar. Entre menor sea el valor, mejor.

¿Cómo descartamos el uso de alineamientos locales? ¿Porqué utilizamos alineamientos globales?

Los bloques altamente conservados son generalmente elementos estructurales como alfa helices y pliegues beta, que evolucionan más lentamente que los loops o bucles que los conectan.

Entre mejor sea tu alineamiento, mejor y más eficiente será tu modelo. Ten cuidad de tener bien curado el alineamiento inicial, si no le has dado el tiempo de ser probado, pulido y limpiado lo mejor posible de ruido, mejor será tu modelo y por consiguiente tu escaneo con el mismo.

El grado de confianza que tengamos en una filogenia particular realmente depende de la que tengamos en el modelo subyacente. Por lo tanto, siempre que usemos un método basado en un modelo explícito de evolución (NJ, ML, By) es necesario usar rigurosas pruebas estadísticas para seleccionar el modelo y el valor de sus parámetros que mejor se ajusten a la matriz de datos a analizar

Para inferir filogenias con Phyml primero vamos con un arbol NJ para tener un árbol base. 

¿De qué me serviría utilizar Get_homologues o Get_Phylomarkers? Mis secuencias son proteicas, altamente divergentes y ni si quiera se trata de establecer una filogenia entre especies parecidas. Ambos programas leen secuencias enteras de nt y aa, en busca del mejor árbol que represente eventos de especiación. Yo, en este punto, no necesito eso.
Yo estoy buscando un modelo oculto de markov que pueda encontrar CS y HS, y con lo que he aprendido en el taller eso implica que si desde mis alineamientos no estoy bien, el modelo es pobre. No contiene información suficientemente pulida como para tomar enserio sus resultados, pero una vez pueda tener un HMM y una lectura más pulida, podría encontrar especies donde el dominio de interés pueda ser compartido entre esas especies. Usaría el par de programas antes mencionados? No lo se, si son especies con poca divergencia tal vez valdría la pena probarlos, ya que dentro de los clusters core y shell podría hallarse mi dominio proteico de interés.