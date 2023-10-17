# Un SCP que te deja saltar un "puente" para ingresar a la máquina que quieras

Suponiendo que tengas un sistema Host-Puente-Máquina_Remota y quieras copiar archivos desde o hacia uno de los dos extremos, agrega este alias a tu archivo ´.bashrc´.

´alias sscp1="scp -oProxyJump=bridge"´

De preferencia agregalo al final para que en caso de que rompas algo, tengas bien claro dónde metiste el error

Ten en cuenta que el ´ProxyJump´ lleva el nombre que diste en tu archivo config del puente. En mi caso, el "puente" lo tengo con el nombre de _bridge_.

Para enviar documentos: $ sscp [tu archivo local] ubmi02:/path/de/destino
Para recibir documentos: $ sscp ubmi02:/path/to/file .

Es un ´cp´ pero a distancia, así que si quieres copiar carpetas agrega el ´-r´.

# Una config para tus clientes frecuentes SSH

´Host ubmi02
    HostName 10.10.180.37
    User rolivares
    Port 1234´

Donde:

- Host = Nombre del cliente al que te quieres conectar
- HostName = Dirección IP
- User = Tu usuario en ese cliente remoto
- Port = En caso de requerirlo, el número de puerto a utilizar
