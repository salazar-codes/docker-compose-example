# Usa una imagen base con JRE 17 de Alpine
FROM eclipse-temurin:17-alpine

# Crea un nuevo grupo de usuarios
RUN addgroup devopsc
# Agrega un usuario al nuevo grupo 
RUN adduser -D -G devopsc admin

# Crea un nuevo mount point a tmp
VOLUME /tmp

# Copiamos el jar a la imagen
ARG JAR_FILE
# Establecemos una variable de entorno para la contraseña de la BD
ARG DB_PASSWORD

# Establece la variable de entorno DB_PASSWORD con el valor del argumento
ENV DB_PASSWORD=$DB_PASSWORD

# Copia el archivo JAR
COPY ${JAR_FILE} /tmp/app.jar

# Change ownership of the /app directory to the "admin" user
RUN chown -R admin:devopsc /tmp

# Cambia al usuario admin
USER admin

# Comando por defecto al ejecutar el contenedor
ENTRYPOINT ["java","-jar","/tmp/app.jar"]

