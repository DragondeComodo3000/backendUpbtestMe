# Backend de productos

API Express con PostgreSQL para listar y crear productos. El servicio publicado en Render puede ser consumido por el frontend, pero para ejecutar una copia de este backend se necesita una conexión propia a PostgreSQL.

## Ejecutar localmente

1. Instala las dependencias con `npm install`.
2. Copia `.env.example` a `.env` y completa `DATABASE_URL` con las credenciales de **tu propia base de datos**.
3. Ejecuta `npm run db:init` para crear la tabla `productos`.
4. Ejecuta `npm run dev` y visita `http://localhost:3000/api/productos`.

Ejemplo para una base de datos PostgreSQL local:

```dotenv
PORT=3000
DATABASE_URL=postgresql://usuario:contrasena@localhost:5432/nombre_bd
DB_SSL=false
```

`PORT=3000` corresponde al servidor HTTP de Express. El `5432` de `DATABASE_URL` corresponde a PostgreSQL. Son servicios distintos y sus puertos no tienen que coincidir.

Si usas una base de datos externa en Render, coloca **tu propia URL externa** en `DATABASE_URL` y configura `DB_SSL` según lo requiera esa conexión. En el servicio web de Render, estas variables se configuran en **Environment**; Render proporciona el puerto HTTP mediante `PORT`.

El archivo `.env` está excluido de Git. `.env.example` solo contiene valores de muestra: copiarlo sin reemplazar `USUARIO`, `PASSWORD`, `HOST` y `NOMBRE_BD` no conectará a ninguna base de datos. No publiques credenciales ni cadenas de conexión reales en el repositorio.

`GET /api/health` comprueba que Express responde. `GET /api/productos` también comprueba que puede consultar PostgreSQL.
