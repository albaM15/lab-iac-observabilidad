# INtrucciones para validar 

## Levantar contenedores

```
docker compose up -d --build
```

![Levantando contenedores](imagenes/docker-up.png)

## Servicios principales

| Servicio | URL | Qué deberías ver |
| --- | --- | --- |
| Frontend | http://localhost:8080 | Página "Hello World" con dos botones |
| Backend | http://localhost:3001/metrics | Texto de métricas en formato Prometheus |
| Grafana | http://localhost:3000 | Login (usuario `admin`, clave `admin`) |
| Prometheus | http://localhost:9090 | Interfaz de Prometheus |

## Ver contenedores en ejecución

```
docker compose ps
```

![Estado de los contenedores](imagenes/docker-ps.png)

## Detener los contenedores (conservando los dashboards)

```
docker compose down
```

![Deteniendo contenedores](imagenes/docker-down.png)

## Detener los contenedores (borrando todo)

```
docker compose down -v
```
