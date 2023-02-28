
## Datos personales
|Nombre| Carnet|
|--|--|
|Wilfred Stewart Perez Solorzano|201408419|
<center>
<br/>

# Actividad 3
</center>

Modificación del dockerfile en la carpeta de frontend con la siguiente información


```
## BUILD
# docker build -t mifrontend:0.1.0-nginx-alpine -f nginx.Dockerfile .
## RUN
# docker run -d -p 3000:80 mifrontend:0.1.0-nginx-alpine
FROM node:18.14.0-buster-slim as compilacion

LABEL developer="jesus guzman" \
      email="susguzman@gmail.com"

## Linea a agregar
## Agregar la variable de entorno
ENV REACT_APP_BACKEND_BASE_URL=http://localhost:3800

# Copy app
COPY . /opt/app

WORKDIR /opt/app

# Npm install
RUN npm install

RUN npm run build

# Fase 2
FROM nginx:1.22.1-alpine as runner

COPY --from=compilacion /opt/app/build /usr/share/nginx/html
```