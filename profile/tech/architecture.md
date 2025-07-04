# Arquitectura & Infraestructura

[[<] Go back home](../README.md)

## Arquitectura general del proyecto

Para este proyecto se tomo la decision de confeccionar una aquitectura por microservicios con multiples repositorios, de manera tal que se independizo cada unidad logica diferente en su propio repositorio y su propio servicio.

De esta manera, cada servicio puede tener el *stack* tecnologico que se desee sin comprometer las dependencias de los demas micro-servicios. Ademas se tuvo en cuenta la atomicidad de los mismos y se utilizo la arquitectura interna de *package by layer*, lo que garantizo una mayor facilidad de mantenimiento y de introduccion de nuevas *features*.

El equipo fue capaz de dividir eficientemente la carga de trabajo entre los integrates inicialmente uno por cada micro-servicio y uno para la aplicacion movil, y luego a medida que se terminaron las historias de usuario de cada servicio, hubo cooperacion para la integracion de cada parte, o para *troubleshooting* en algunos casos de error complejos.

Dicho esto, a continuacion se puede ver una representacion grafica de la arquitectura empleada:

![arquitectura final](../img/arquitectura_final.png)

## Bases de datos

Las bases de datos utilizadas por cada microservicio son aisladas y son las denotadas a continuacion:

| Microservicio     | Base de datos |
|-------------------|---------------|
| Users             | PostgreSQL    |
| Courses           | PostgreSQL    |
| AI                | PostgreSQL    |
| Forum             | MongoDB       |
| Administration    | MongoDB       |
| Notifications     | MongoDB       |

Los *hostings* de bases de datos utilizados para cada tipo fueron:

| Base de datos     | Host |
|-------------------|---------------|
| PostgreSQL        |   Supabase    |
| MongoDB           | MongoAtlas    |

Adicionalmente los servicios de Users y Courses utilizan los **buckets** para almacenamiento multimedia proporcionados en el mismo plan gratis de *supabase*.

## Infraestructura empleada

A nivel de infraestructura, se llevo a cabo una investigacion sobre cada uno de los *cloud-providers* que tienen convenio con el pack estudiantil provisto por github, y sobre los proveedores que no tienen convenio, pero que si tienen un *free-tier*. Los criterios del equipo para la seleccion del proveedor, era principalmente que cuente con un motor de *kubernentes* en el free-tier, esto hizo que la busqueda sea mas complicada ya que no es comun en este tipo de proveedores de *cloud-computing* ofrecer ese tipo de servicios bajo ese tier, por lo que tambien se buscaron proveedores con *hosting* para servicios individuales (lo malo de esto es que cada micro-servicio estaria en un host diferente y no en la misma red interna).

En principio se intento abrir una cuenta con Microsoft-Azure por medio de dicho pack estudiantil, sin embargo se desistio por las dificultades impuestas por la plataforma a la hora de hacerlo. Tambien se tuvo en cuenta otros prooverdores IaaS como DigitalOcean, AWS (no cuenta con motor de k8s en free-tier, pero sin embargo fue una opcion considerada), y otros proveedores PaaS como Heroku y Render.

Finalmente se descubrio el proovedor de infraestructura como servicio Linode, y es el que se eligio, debido a que este cuenta con motor de k8s en el free-tier (a dia de entregado este trabajo) y credito por $100usd, para el que es necesario vincular un medio de pago de credito. Esta plataforma permitio obtener infraestructura con las siguientes caracteristicas:

K8s cluster con:
- 2 Nodos - shared CPU
- Memoria: 4GB ram c/u
- Costo: $33usd/mes
- Validez: 60 dias

La validez de 60 dias significo que, se tuvo que hacer una migracion de todos los servicios deployeados a un nuevo cluster antes de la expiracion del mismo. Este tema se aborda en el [analisis postmortem](../misc/postmortem.md).

En este cluster se desplego (por medio de CI/CD pipelines) todo el servidor con sus diferentes micro-servicios (capaces de comunicarse internamente en una red privada) y a su vez un servidor web con nginx encargado del frontend backoffice. Tambien se desplegaron utilidades como:

- Api gateway (kong): Encargada de exponer todos los servidores por una interfaz unificada y encaminar las *requests* entrantes al servicio correspondiente. Adicionalmente permite la configuracion de plugins para mejorar la seguridad y/o agregar requests con informacion de mas de un micro-servicio.
- Datadog (DD) agents: Se desplego un daemonset de DD agent (uno por nodo), capaz de obtener metricas e informacion a nivel infraestructura (e.g. metricas de uso de cpu, memoria, banda ancha, etc) de los nodos, asi como tambien un DD cluster agent que se encarga de recolectar informacion a nivel cluster (e.g. pods, metadata, estado, etc).
