# CEBEA Transporte y Servicios

Sitio estático servido con Nginx en Docker. No requiere instalar Node.js ni
compilar la página.

## Prueba local sin Docker

Requisito: Python 3. Desde esta carpeta, ejecuta:

```powershell
py -m http.server 8000
```

Abre [http://localhost:8000/CEBEA%20Transporte%20y%20Servicios.html](http://localhost:8000/CEBEA%20Transporte%20y%20Servicios.html).
Detén el servidor con `Ctrl+C`.

## Prueba local con Docker

Requisitos: Docker Engine y Docker Compose.

Desde esta carpeta, ejecuta:

```powershell
docker compose up --build
```

Abre [http://localhost:8080](http://localhost:8080). Para detenerlo, pulsa
`Ctrl+C` y luego ejecuta:

```powershell
docker compose down
```

El puerto local predeterminado es `8080`. Si está ocupado, puedes elegir otro:

```powershell
$env:APP_PORT = "8081"
docker compose up --build
```

En ese caso, abre `http://localhost:8081`.

## Despliegue en el servidor

Copia esta carpeta completa al servidor y, desde ella, ejecuta:

```sh
docker compose up -d --build
```

El sitio quedará disponible en el puerto `8080` del servidor. Para usar otro
puerto, configura la variable `APP_PORT` antes de iniciar Compose. Asegúrate de
que el puerto esté permitido en el firewall o enlázalo a tu proxy inverso.

Para actualizar la página, reemplaza `CEBEA Transporte y Servicios.html` y
vuelve a ejecutar `docker compose up -d --build`.

## Notas

- El formulario de cotización abre WhatsApp; no guarda envíos en el servidor.
- La página usa Google Fonts cuando hay conexión a Internet y fuentes locales
  como alternativa.
