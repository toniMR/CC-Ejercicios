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