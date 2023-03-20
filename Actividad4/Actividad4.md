# Actividad 4
## Crear un systemd unit
---
### Wilfred Stewart Perez Solorzano
### 201408419
---

## Pasos de instalacion

1. Se crea un script en el cual se programara la funcionalidad del servicio. Lo guardaremos como saludo.sh

```
#!/bin/bash
echo "Bienvenido usuario, La fecha del dia de hoy es: $(date)"
```
Para que el script tenga presmisos ejecutamos lo siguiente
```
chmod +x saludo
```

2. Se crea un archivo de systemd unit en la carpeta /etc/systemd/system/, nombrandolo 

```
sudo nano /etc/systemd/system/actividad4.service
```

3. Para crear el servicio lo modificamos con los siguiente comandos guardando los cambios.

```
[Unit] 
Description=Imprimir Saludo  

[Service]
Type=simple 
ExecStart=/home/linux/Escritorio/saludo.sh 

[Install] 
WantedBy=multi-user.target  
```

4. Para actualizar los servicios e incluir el servicio creado utilizaremos lo siguiente:
```
sudo systemctl daemon-reload  
```

5. Para iniciar el servicio utilizaremos el siguiente comando
```
sudo systemctl start actividad4.service
```

NOTA: Para validar que el servicio se esta ejecutando ejecutar el siguiente comando

```
sudo systemctl status actividad4.service  
```