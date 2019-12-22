# Ejercicios del tema "Contenedores y cómo usarlos"

## Ejercicio 2: Tomar algún programa simple, “Hola mundo” impreso desde el intérprete de línea de órdenes, y comparar el tamaño de las imágenes de diferentes sistemas operativos base, Fedora, CentOS y Alpine, por ejemplo.

### Alpine

Dockerfile de alpine:

```dockerfile
    # Escoger la base
    FROM python:alpine

    # Establecer el directorio de trabajo
    WORKDIR /home/nonrootuser/cc-ejercicios

    # Copiar exclusivamente los ficheros necesarios
    COPY hello.py ./

    # Crear un usuario sin permisos de root
    RUN adduser -D nonrootuser

    # Indicar el usuario a usar al ejecutar la imagen.
    USER nonrootuser

    # Ejecutar script
    CMD python hello.py
```

Ejecutar desde el directorio 'docker':

```bash
    docker build -t alpine-hello -f fedora/Dockerfile .
```

### CentOS

CentOS tiene python2 instalado por defecto.  

Dockerfile de centos:

```dockerfile
    # Escoger la base
    FROM centos:centos7

    # Establecer el directorio de trabajo
    WORKDIR /home/nonrootuser/cc-ejercicios

    # Copiar exclusivamente los ficheros necesarios
    COPY hello.py ./

    # Crear un usuario sin permisos de root
    RUN useradd -m nonrootuser

    # Indicar el usuario a usar al ejecutar la imagen.
    USER nonrootuser

    # Ejecutar script
    CMD python hello.py
```

Ejecutar desde el directorio 'docker':

```bash
    docker build -t centos-hello -f centos/Dockerfile .
```

### Fedora

Fedora tiene python3 instalado por defecto:  

Dockerfile de fedora:

```dockerfile
    # Escoger la base
    FROM fedora:latest

    # Establecer el directorio de trabajo
    WORKDIR /home/nonrootuser/cc-ejercicios

    # Copiar exclusivamente los ficheros necesarios
    COPY hello.py ./

    # Crear un usuario sin permisos de root
    RUN useradd -m nonrootuser

    # Indicar el usuario a usar al ejecutar la imagen.
    USER nonrootuser

    # Ejecutar script
    CMD python3 hello.py
```

Ejecutar desde el directorio 'docker':

```bash
    docker build -t fedora-hello -f fedora/Dockerfile .
```

### Resultados

```bash
    REPOSITORY          TAG                 IMAGE ID            CREATED              SIZE
    fedora-hello        latest              43108e08f015        8 seconds ago        194MB
    centos-hello        latest              d7b8c4d32220        51 seconds ago       203MB
    alpine-hello        latest              3d184f9f6946        About a minute ago   111MB
```

Se puede observar que el que tiene menor tamaño es el que utiliza alpine.