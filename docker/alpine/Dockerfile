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