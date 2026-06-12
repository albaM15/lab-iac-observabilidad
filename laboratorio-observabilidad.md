# Laboratorio de Observabilidad — Grafana, Prometheus y Loki

---

### Levantar contenedores

```
docker compose up -d --build
```

### Detener los contenedores (conservando los  dashboards)

```
docker compose down 
```

### Detener los contenedores (borrando todo)

```
docker compose down -v
```

## Breve explicación de cada componente del stack

El stack combina herramientas especializadas para observar el sistema desde dos ángulos: métricas y logs. Prometheus recolecta y almacena los números del sistema, usando node-exporter y cAdvisor como fuentes de datos del host y los contenedores respectivamente. Alloy captura los logs de cada contenedor en tiempo real y los envía a Loki, que los almacena y permite consultarlos. Grafana es la capa de visualización que conecta todo, dibuja los dashboards y dispara alarmas cuando algo supera un umbral. Las aplicaciones backend y frontend  son el objeto de observación: exponen métricas y emiten logs en formato JSON que el resto del stack recoge y procesa.

---

## Preguntas a responder

### 1. ¿Por qué necesitamos Loki además de Prometheus si ya tenemos `/metrics`?

Porque son dos cosas distintas: Prometheus recolecta **métricas**, que dicen cuándo y cuánto, pero no por qué; en cambio, Loki recolecta **logs**, que son los que dicen qué pasó.

### 2. ¿Qué ventaja aporta que las fuentes de datos de Grafana estén aprovisionadas como código y no creadas a mano?

- Se evitan errores humanos
- Se reduce el tiempo de configuración
- Cuando alguien quiera levantar el stack (los contenedores), ya tendrá la configuracion correcta. 

### 3. El panel "CPU contenedor" y el panel "CPU host" pueden mostrar valores muy distintos. ¿Por qué? ¿Cuál usarías para alertar sobre una aplicación concreta?

El panel "CPU contenedor" mide únicamente el CPU que consume el proceso `lab-backend` dentro de su contenedor. El panel "CPU host" mide el consumo total de la máquina física, incluyendo todos los contenedores y el sistema operativo. Para alertar sobre una aplicación concreta se usaría el panel de CPU contenedor, ya que es específico del servicio que se quiere monitorear.

### 4. ¿Qué diferencia hay entre el *evaluation interval* y el *pending period* de una alarma?

- **Evaluation interval:** cada cuánto tiempo Grafana revisa si la condición de la alarma se cumple.
- **Pending period:** cuánto tiempo debe cumplirse la condición de forma continua antes de pasar a Firing. Evita falsas alarmas por picos momentáneos.

