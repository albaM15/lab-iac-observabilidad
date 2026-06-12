# INtrucciones para validar

## Levantar contenedores

```
docker compose up -d --build
```

![Levantando contenedores](imagenes/docker-up.png)

## Servicios principales

| Servicio   | URL                           |
| ---------- | ----------------------------- |
| Frontend   | http://localhost:8080         |
| Backend    | http://localhost:3001/metrics |
| Grafana    | http://localhost:3000         |
| Prometheus | http://localhost:9090         |

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

![Deteniendo contenedores y borrando volúmenes](imagenes/docker-down-v.png)
