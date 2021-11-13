# Mecanismos de autenticación remota
Un mecanismo de autenticación define reglas sobre información de seguridad, como si una credencial es reenviable a otro proceso de Java™ y el formato de cómo se almacena la información de seguridad en credenciales y señales. Puede seleccionar y configurar un mecanismo de autenticación utilizando la consola administrativa.
La autenticación es una manera de controlar el acceso cuando los usuarios intentan acceder a un sistema remoto. La autenticación se puede configurar en el nivel del sistema y en el nivel de red. Después de que un usuario haya obtenido acceso a un sistema remoto, la autorización es una manera de limitar las operaciones que el usuario puede realizar. En la siguiente tabla, se muestran los servicios que proporcionan autenticación y autorización.

## Autenticación por token de sesión
En la autenticación por token de sesión, conocida normalmente como autenticación por sesión, se genera un token asociado internamente a un usuario. Este token suele tener además una caducidad establecida.

![image](https://user-images.githubusercontent.com/50505172/140596686-b210d5b6-3a88-47d9-8a5b-c8c75a208c45.png)
## Autenticación por token de aplicación
La sesión es una forma de proveer de un estado al protocolo HTTP. Asociado al identificador de sesión, es posible guardar temporalmente información adicional del usuario al que está enlazado. Hay veces en las que no es necesario guardar un estado de la interacción con la aplicación y simplemente se desean realizar acciones. Además, para obtener un token de sesión es necesario autenticarse previamente, lo que en el caso de aplicaciones automatizadas supondría por un lado guardar credenciales y por otro tener que gestionar los procesos de autenticación que sean necesarios.
Es por ello que muchas plataformas permiten la generación de un token de acceso que deberá guardarse de forma segura y que permitirá acceder a los recursos del usuario al que esté asociado, como si de una sesión se tratase del mismo. Algunas aplicaciones restringen los permisos del token de acceso generado en el momento de la creación del mismo. Aunque se pueden implementar caducidades, un token de acceso de aplicación generalmente no caduca y es siempre el mismo. (No confundir con el token de autorización de acceso a recursos generado por un proveedor de OAuth, que es distinto cada vez que se genera o renueva). Al igual que el token de sesión, si este token sufriera de una filtración el atacante que dispusiera de este podría realizar las acciones que le brinde el token.
Aunque no tiene por qué, este token suele mandarse en la cabecera Authorization. Un caso de uso sería el de por ejemplo, Linode, que permite la generación de tokens de aplicación para hacer uso de su API y desplegar máquinas en la nube.

En este escenario, una medida de seguridad interesante a adoptar sería la de restringir el uso del token de aplicación generado, a una dirección IP siempre que se pueda.

Idealmente el reto inicial debe proveer de 3 elementos para probar la identidad del usuario.

1. Algo que el usuario sabe
2. Algo que el usuario posee
3. Algo que el usuario es

Estos tres elementos pueden traducirse de la siguiente forma:

1. Contraseña o información secreta que únicamente el usuario conoce
2. Dispositivo de seguridad, certificado digital, código sms, etc.
3. Elementos biométricos
