# Manual de usuario [Backoffice]

[[<] Go back home](../README.md)

El Backoffice de ClassConnect es la plataforma web exclusiva para administradores, donde podrán controlar, mantener y supervisar el funcionamiento de la aplicación.

## Inicio de Sesión como Administrador

Para acceder al Backoffice, es necesario:

 - Haber sido registrado previamente como administrador por otro administrador.

 - Ingresar con las credenciales otorgadas por este administrador.

⚠️ Los administradores pueden permanecer logueados por una hora. Luego de este período, deberán volver a ingresar sus credenciales para continuar utilizando la plataforma.

![profile/img/Backoffice_Login.png](https://github.com/ClassConnect-org/.github/blob/eeed27954d7299a854554c800eb5303b75257072/profile/img/Backoffice_Login.png)

Una vez dentro, los administradores podrán navegar por el menú lateral para acceder a las distintas funcionalidades del sistema.

## Gestión de Reglas de la Aplicación

Los administradores tienen la responsabilidad de crear, modificar o eliminar reglas que rigen el comportamiento y uso de la aplicación.

![profile/img/Backoffice_RulesDeatils.png](https://github.com/ClassConnect-org/.github/blob/7f2cac35a4c36684cf3744bdafba2be809aae054/profile/img/Backoffice_RulesDetails.png)

⚠️ Cualquier cambio en las reglas debe realizarse con máxima precaución, ya que puede impactar directamente en la experiencia de todos los usuarios.

![profile/img/Backoffice_CreateNewRule.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_CreateNewRule.png)

Una vez efectuados los cambios, todos los usuarios registrados recibirán un email con los detalles actualizados de las reglas modificadas, creadas o eliminadas.

![profile/img/Backoffice_NewRuleEmail.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_NewRuleEmail.png)

## Moderación de Usuarios

Dentro de la sección Users, se lleva a cabo la gestión de usuarios registrados en la aplicación. Esta sección permite:

 - Bloquear usuarios hasta una fecha determinada. Mientras estén bloqueados, no podrán acceder a la app.

 - Eliminar usuarios, eliminando su cuenta de forma permanente.

![profile/img/Backoffice_UsersManagment.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_UsersManagment.png)

## Logs de la aplicación

Los administradores tienen acceso a registros internos de actividad, organizados en dos categorías principales:

### Logs de Auditoría

Encargado de registrar todos los cambios hechos en las reglas y normativas de la aplicación. Cada entrada incluye:

 - Acción realizada (crear, editar, eliminar)

 - Administrador que efectuó el cambio

 - Detalles del cambio aplicado

![profile/img/Backoffice_AuditLogs.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_AuditLogs.png)

![profile/img/Backoffice_AuditLogs_details.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_AuditLogs_details.png)

### Logs de Notificaciones

Encargado de registrar los envios de notificaciones de la aplicación. Cada registro incluye:

 - Estados de envío: `sent`, `not sent - no permission` y `error`.

 - Tipo de Notificación: `email` o `push`.
 
 - Detalles del contenido enviado y los destinatarios.

![profile/img/Backoffice_NotificationsLogs.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_NotificationsLogs.png)

## Chat AI

Cuando una respuesta del chatbot Navi recibe una valoración (positiva o negativa), los administradores deben revisarla para:

 - Evaluar si la respuesta podría haberse expresado de forma más clara

 - Determinar si requiere ser ajustada mediante procesos de fine tuning

En caso de uso malicioso o abusivo del sistema, el administrador podrá ver los detalles del usuario que realizó la consulta para tomar las medidas necesarias.

![profile/img/Backoffice_ChatAINavi.png](https://github.com/ClassConnect-org/.github/blob/779343edd78700c563133e87c7e2e262edb98f93/profile/img/Backoffice_ChatAINavi.png)

## Manejo de Administradores

Finalmente los administradores podran acceder a la tabla de administradores donde podran buscar la existencia de un administrador segun su email y crear nuevos administradores. Esta es la unica forma de convertirse en administrador y lograr acceso al backoffice.

![profile/img/Backoffice_CreateAdmin.png](https://github.com/ClassConnect-org/.github/blob/283176c690e738c9321322abb5d9850ed8f38239/profile/img/Backoffice_CreateAdmin.png)

🚫 Esta es la única forma de convertirse en administrador y acceder a la plataforma de gestión. El administrador tiene la responsabilidad de notificar al nuevo administrador sus credenciales.

