# Laboratorio N6
# mmap
### SOI - FCEFyN - UNC - 2021


## Objetivo

Con el desarrollo del siguiente Trabajo Práctico (TP), se busca:
- Utilizar archivos binarios.
- Utilizar mecanismos de mapeo de memoria.

## Duración
Con el material dado en clase, este laboratorio está diseñado para resolverse entre 6 y 8 horas.


## Introducción
Este trabajo práctico consta en la elaboración de un programa en lenguaje C sobre _GNU/Linux_. El trabajo se divide en soluciones incrementales.

## Actividades
#### 1. Acceder datos
En  la carpeta _rawdata_ se encuentra el archivo binario llamado _datos_. El archivo contiene información obtenida por el radar meteorológio RMA1 instalado en Ciudad Universitaria (UNC).  Nuestro programa debe mapear el archivo en memoria ram y castearlo al tipo de dato de acuerdo a la siguiente estructura.

| Nombre      | tipo    |  bytes      | Descripción |  
| ----------- | ----------- | ----------- | ----------- |
| version      | unsigned int | 2 | versión del dato n1 |
| drxVersion   | unsigned int | 2 | version del DRX que generó el dato n1 |
| RESERVADO   |  | 4 |  |
| initCW   | double | 8 | inicio de la ventana de recepción, en segundos |
| azimuth   | float | 4 | apuntamiento acimut en grados |
| elevation   | float | 4 | apuntamiento elevación en grados |
| idVolumen   | unsigned int  | 2 | identificador de volumen |
| idBarrido   | unsigned int  | 2 | identificador de barrido |
| idCnjunto  | unsigned int  | 2 | identificador de conjunto |
| idGrupo  | unsigned int  | 2 | identificador de grupo |
| idPulso   | unsigned int  | 2 | identificador de pulso |
| iniBarrido   | bool | 1 | bandera del primer pulso de barrido |
| finBarrido   | bool  | 1 | bandera del último pulso de barrido |
| finGrupo   | bool  | 1 |  bandera del último pulso del grupo |
| inhibido   | bool  | 1 | bandera de transmisión inhibida |
| validSamples  | unsigned int  | 2 | cantidad de muestras complejas válidas |
| nroAdquisicion  | unsigned int  | 2 | contador de adquisiciones |
| RESERVADO   |  | 2 |  |
| nroSecuencia   | unsigned int | 4 | número de secuencia |
| readTime_high   | unsigned int | 8 | campo alto de la marca de tiempo |
| readTime_low   | unsigned int | 8 | campo bajo de la marca de tiempo |
| RESERVADO   |  | 64 |  |


La estructura representa el header de un pulso de radar, con los metadatos que describen al mismo. 


#### 2. Pipe
_myshell_ provee la funcionalidad de un pipe a través del operador **|** (pipe). El mismo conecta la salida estándar del proceso (stdout) lazando por el comando de la izquierda del pipe con la entrada estándar del proceso (stdin) que se genera con el comando a la derecha del pipe.

Ejemplos:
```
$ last <username> | wc -l
$ ps aux | grep firefox
$ grep bash /etc/passwd | cut -d “:” -f 1 | sort -r
```

##### Responder:
¿Dónde se encuentran los pipes en el filesystem, qué atributos tienen?


#### 3. I/O redirection 
Se debe soportar redirección de entrada/salida en _stdin_ y/o _stdout_. 

Por ejemplo:
```
program arg1 ar2 < inputfile > outputfile
```

Ejecuta la el programa _program_ con los arguments _arg1_, _arg2_. _stdin_ es reemplazado por _inputfile_ y _stdout_ por _outputfile_.
La redirección debe funcionar para el comando interno _echo_.


## Criterio de desarrollo
Dado que este laboratorio propone agregar funcionalidades a un proyecto existente, deben utilizar correctamente el workflow de desarrllo. Es decir:
- Se debe realizar un fork al proyecto original (laboratorio 4)
- Se implementan las nuevas funcionalidades
- Se realiza un Pull Request en un nuevo branch en el repositorio del laboratorio 4.


## Criterios de Corrección
- Se debe compilar el código con los flags de compilación: -Wall -Pedantic -Werror 
- Dividir el código en módulos de manera juiciosa.
- Estilo de código.
- El código no debe contener errores, ni warnings.
- El código no debe contener errores de cppcheck.
- _myshell_ no debe crear procesos zombies.

## Qué se debe Entregar
- Informe del desarrollo del proyecto (markdown).
- Código (funcionando bajo las especificaciones dadas y bajo cualquier caso de test de parámetros de entrada).
- Makefile
- Todo en el GitHub


### Links
- [1] https://www.toptal.com/git/git-workflows-for-pros-a-good-git-guide
- [2] https://www.dataschool.io/how-to-contribute-on-github/
