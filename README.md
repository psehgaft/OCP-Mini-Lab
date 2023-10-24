# OCP-Mini-Lab

Adicional a las urls para acceso a Internet considerar las siguientes por favor, (por completud coloco las anteriores):

https://maven.repository.redhat.com/ga
https://maven.repository.redhat.com/earlyaccess/all
https://repository.jboss.org/nexus/content/groups/public
https://github.com/
https://developers.redhat.com/
https://access.redhat.com/

Para la descarga en redhat developers se requiere de una cuenta. Es posible utilizar una cuenta del portal de customer(https://access.redhat.com/) o también registrar un nuevo correo(este ultimo es preferente para los desarrolladores).

En lo que respecta al browser puede ser Google o Firefox, en particular Firefox permite guardar todas las ligas consultadas y migrar fácilmente a otro ambiente de desarrollo. Esta recomendación es responsabilidad de cada desarrollador.

NOTA: Las acciones señaladas a continuación se deben ejecutar preferentemente por los desarrolladores. Se ejecutan previo para garantizar el correcto funcionamiento y poder prever cualquier incidente durante el proceso.

Adicional a la instalación de paquetería se requieren las siguientes configuraciones:

Por default Maven apunta al repositorio central de maven, este repo no es oficial de redhat. Es necesario cambiar esta configuración a los repositorios oficiales de redhat. Acorde la documentación oficial add-red-hat-repositories-to-maven adjunto el archivo settings.xml, hacer backup del archivo /etc/maven/settings.xml y sustituir.

Con esta configuración podemos realizar el tunning del IDE CodeReady Studio. Editar el archivo ~/codereadystudio/studio/codereadystudio.ini y incrementar las siguientes variables de java:
-Xms1024m
-Xmx2048m

Una vez editadas las propiedades iniciar el IDE CodeReadyStudio y realizar la siguiente actividad:

- Dar click en "File", luego hacer hover sobre "New" y seleccionar "Maven Project" del menu desplegado. Dar click en "Next" y en la barra de búsqueda "Filter" escribir "fabric". Se deben mostrar los arquetipos de los grupos "io.fabric8" y "io.fabric8.archetypes", si así ocurre la configuración de setting.xml de maven ha sido exitosa y correcta. Finalmente seleccionar el arquetipo de camel-amq (camel-amq-archetype) y dar click en next. Llenar los campos groupid (ex. com.redhat), artifactid (ex. helloWorld) y en la versión 0.0.1 (importante quitar el snapshot), dar click en "Finish". Se tarda un poco en generar el proyecto. Verificar que se construye el proyecto sin errores, en caso de algún error incrementar la memoria y reiniciar el IDE.

Para la instalación de Minishift seguir la siguiente guía oficial:  https://docs.okd.io/latest/minishift/getting-started/index.html. Se recomienda esta instalación solamente para maquinas con 12gb o mas de memoria RAM. Para determinar si la memoria es suficiente, abrir la paquetería instalada y ejecutar el comando minishift start.
Como resumen se propone el siguiente roadmap:

    https://docs.okd.io/latest/minishift/getting-started/setting-up-virtualization-environment.html#kvm-driver-fedora
    Descargar el tar para linux: Download the archive for your operating system from the Minishift Releases page and extract its contents.
    Descomprimir el tar sobre el directorio "~" , (es /home/user/):Copy the contents of the directory to your preferred location.
    Add the minishift binary to your PATH environment variable.
        añadir al archivo .bashrc las siguientes lineas al final:
            export MINISHIFT_BIN=/home/darkdragonel/minishift-1.34.1-linux-amd64
            PATH="$MINISHIFT_BIN:$PATH"
            export PATH
        Después ejecutar el archivo bashrc con "sh" para cargar la nueva variable.
        Una vez con esto, el comando "minishift start" creara un cluster local como se indica en la guia oficial.
