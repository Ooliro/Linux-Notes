# Conexiones ssh

Computadora de Carlos: ssh rolivares@10.10.180.37

Computadora Blanca: ssh rolivares@10.10.180.36

Computadora Puente: ssh -p 6112 rolivares@132.248.16.17





chmod 755 [nombre a modificar]

---------------------

# byobu

- Para salir de byobu, presiona F6

- Para nueva terimnal, presiona 2

- Navegar F3 y F4

- Para terminar byobu, mata todos los procesos y exit a todo

-----------------

# Kill process

Para matar forzozamente un proceso, entra a htop, filtra (F4) buscando el comando que está saturando el equipo, anota el numero de proceso y corre 

`kill -9 202020`

Obvio cambia el numero del proceso

---------------------
Copiar de una ubicación de red con alias a mi carpeta deseada
scp ubmi01:/UBMInas/databases/rolivares_cpa/raul_gtf/importan3/metazoa_gtf.txt /home/raulrosas/Documentos/IFC/lab/scripts_temp/
