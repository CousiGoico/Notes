# Planes de precios en GitHub

## Contenido

- [Planes personales](#planes-personales)
  - [Free (personal)](#free-personal)
  - [Pro](#pro)
- [Planes empresa](#planes-empresa)
  - [Free (empresa)](#free-empresa)
  - [Team](#team)
  - [Enterprise](#enterprise)
- [Precio por usuario](#precio-por-usuario)
  - [Dos modelos de facturación para licencias GitHub Enterprise](#dos-modelos-de-facturación-para-licencias-github-enterprise)
- [Referencias](#referencias)

## Planes personales

### Free (personal)

Carácteristicas de este plan:

- Apoyo comunitario de GitHub.
- Alertas de dependabot.
- Normas de protección de despliegue para repositorios públicos.
- Aplicación de autenticación de dos factores.
- 500 MB de almacenamiento de paquetes GitHub.
- 120 horas/mes de GitHub Codespaces.
- 15 GB/mes de almacenamiento de GitHub Codespaces.
- GitHub actions:
  - 2.000 minutos/mes
  - Normas de protección de deslpiegue para repositorios públicos.
- Páginas de GitHub en repositorios públicos.

### Pro

Precio: $4.

Carácteristicas añadidas al plan Free:

- Soporte de GitHub por correo electrónico.
- 3000 minutos/mes GitHub Actions.
- 2 GB de almacenamiento de paquetes GitHub.
- 180 horas/mes GitHub Codespaces.
- 20 GB de almacenameintos de GitHub Codespaces.
- Herramientas avanzadas e ideas en repositorios privados:
  - Revisores de solictudes de extracción requeridos.
  - Múltiples revisores de solicitures de extracción.
  - Ramas protegidas.
  - Propietarios de códigos.
  - Referencias autovinculadas.
  - Páginas de GitHub.
  - Wikis.
  - Gráficos de información de repositorio: Pulse, contribuyentes, tráfico, commits, frecuencia de código, red y bifurcaciones (forks).

> [!NOTE]
> Para publicar un sitio de GitHub Pages de forma privada, debe tener una cuenta de organización. Además, su organización debe usar GitHub Enterprise Cloud.
>
> [!NOTE]
> Ciertas ideas de frecuencia de código, confirmación y contribuidor solo están disponibles para repositorios que tienen menos de 10,000 confirmaciones.

## Planes empresa

### Free (empresa)

Carácteristicas añadidas al plan Free:

- Apoyo comunitario de GitHub.
- Controles de acceso de equipo para administrar grupos.
- 2.000 minutos/mes para GitHub Actions.

### Team

Carácteristicas añadidas al plan Free (empresa):

- Soporte de GitHub por correo electrónico.
- 3.000 minutos/mes para GitHub Accions.
- 2 GB de almacenamiento de paquetes GitHub.
- Opción de compra de productos GitHub Advanced Security:
  - Código de seguridad de GitHub.
  - Protección secretos GitHub.
- Herramientas avanzadas e idas en repositorios privados:
  - Revisores de solicitudes de extracción requeridos.
  - Múltiples revisores de solicitudes de extracción.
  - Solicitudes de extracción de borradores.
  - Revisores de solicitudes de extracción de equipo.
  - Ramas protegidas.
  - Propietarios de códigos.
  - Recordatorios programados.
  - Páginas de GitHub.
  - Wikis.
  - Gráficos de información de repositorio: Pulse, contribuyentes, tráfico, commits, frecuencia de código, red y bifurcaciones (forks).
  - La opción de habilitar o deshabilitar espacios de Codespaces para los repositorios privados de la organización, y pueden pagar por el uso de miembros y colaboradores.

> [!NOTE]
> Para publicar un sitio de GitHub Pages de forma privada, debe tener una cuenta de organización. Además, su organización debe usar GitHub Enterprise Cloud.
>
> [!NOTE]
> Ciertas ideas de frecuencia de código, confirmación y contribuidor solo están disponibles para repositorios que tienen menos de 10,000 confirmaciones.

GitHub factura por equipo de GitHub por usuario. En cuanto a los jobs que se ejecutan en los GitHub Actions son gartuitos para repositorios publicos y autohospedados, y los repositorios privados tienen un cantidad de minutos gratuitos dependiendo de la cuenta.

### Enterprise

Incluye dos implementaciones: GitHub Enterprise Cloud y GItHub Enterprise Server.

[Más información](https://docs.github.com/es/enterprise-cloud@latest/admin/overview/about-github-for-enterprises)

Carácteristicas añadidas al plan Team:

- Soporte Empresarial de GitHub.
- Controles adicionales de seguridad, cumplimiento e implementación.
- Auteicación con inicio de sesión único SAML.
- Acceso al aprovisionameinto con SAML o SCIM.
- Reglas de protección de implmentación con acciones de GitHub para repositorios privados o internos.
- GitHub Conectar.
- Características adicionales como repositorios internos y regalas de repositorio.

GitHub Enterprise Cloud incluye específicamente:

- 50.000 minutos/mes de GitHub actions. (Los minutos incluidos se pueden usar solo con corredores alojados en GitHub estándar)
- 50 GB de almacenamiento de paquetes GitHub.
- Un acuerdo de nivel de servicio para un tiempo de actividad mensual del 99.99%.
- La opción de administrar centramente la política y la facturación para múltiples organizaciones de GitHub con una cuenta empresarial.
- La opción de aprovisionar y administrar las cuentas de usuario para sus desarrolladores, mediante el uso de Usuarios Administrados Empresariales.
- Las características adicionales, como la transmisión de registros de auditoría y la lista de permisos de IP.
- La opción de alojar los datos de su empresa en una región específica, en un subdominio único.

## Precio por usuario

La base de su factura es el número de cuentas de usuario que utilizan su organización o empresa. GitHub determina cuántas licencias está consumiendo en función de la cantidad de usuarios únicos en sus implementaciones. Para garantizar que el mismo usuario no consuma más de una licencia para múltiples implementaciones empresariales, puede sincronizar el uso de la licencia entre los entornos de GitHub Enterprise Server y GitHub Enterprise Cloud.

Además de mostrar las licencias facturables de GitHub Enterprise, su factura puede incluir otros cargos, como GitHub Advanced Security.

### Dos Modelos de facturación para licencias GitHub Enterprise

Con la facturación basada en el uso, usted paga por la cantidad de licencias que usa cada mes.

Si actualmente paga sus licencias de GitHub Enterprise por factura con un volumen, suscripción o acuerdo prepago, continuará facturándose de esta manera hasta que expire su acuerdo. En la renovación, tiene la opción de cambiar al modelo de facturación medido.

#### Personas que consumen una licencia

> [!NOTE]
> Si su empresa utiliza cuentas de usuario administradas, el rol de colaborador externo se llama "colaborador repositorio.".

#### Cuentas que consumen una licencia en GitHub Enteprise Cloud

GitHub factura por cada una de las siguientes cuentas en GitHub Enterprise Cloud:

- Propietarios de empresas que son miembros o propoietarios de al menos una organización en la empresa.
- Miembros de la organización, incluidos los propietarios.
- Colaboradores externos en repositorios privados o internos propiedad de su organización, excluyendo bifurcaciones.
- Usuarios inactivos que son miembros o propietarios de al menos una organización en la empresa.

Si su empresa no utiliza Usuarios Administrados Empresariales, también se le facturará por cada una de las siguientes cuentas:

- Cualquier persona con una invitación pendiente para convertirse en propietario o miembro de una organización.
- Cualquier persona con una invitación pendiente para convertirse en un colaborador externo en repositorios privados o internos propiedad de su organización, excluyendo las bifurcaciones.

> [!NOTE]
> - GitHub cuenta a cada miembro o colaborador externo una vez para fines de facturación, incluso si la cuenta de usuario tiene membresía en múltiples organizaciones en una empresa o acceso a múltiples repositorios propiedad de su organización.
> - Si un invitado no acepta la invitación dentro de los siete días, la invitación pendiente caduca automáticamente. Si una solicitud SCIM de su proveedor de identidad (IdP) genera la invitación, la invitación no caducará.
> - Invitar a un colaborador externo a un repositorio utilizando su dirección de correo electrónico utiliza temporalmente una licencia disponible, incluso si ya tienen acceso a otros repositorios. Después de que acepten la invitación, la licencia será liberada nuevamente. Sin embargo, invitarlos a usar su nombre de usuario no usa temporalmente una licencia.

GitHub no factura ninguna de las siguientes cuentas:

- Cuentas de usuario administradas que están suspendidas.
- Propietarios de empresas que no son miembros o propietarios de al menos una organización en la empresa, excepto el usuario que creó la empresa.
- Gerentes de facturación empresarial.
- Gerentes de facturación para organizaciones individuales.
- Cualquier persona con una invitación pendiente para convertirse en un gerente de facturación.
- Cualquier persona con una invitación pendiente para convertirse en un colaborador externo en un repositorio público propiedad de su organización.
- Colaboradores invitados que no son miembros de la organización o colaboradores del repositorio.
- Usuarios de suscripciones de Visual Studio con GitHub Enterprise cuyas cuentas en GitHub no están vinculadas, y que no cumplen con ninguno de los otros criterios de precios por usuario.
- Usuarios que han sido aprovisionados con una cuenta de usuario administrada, pero no son miembros de ninguna organización en la empresa.
- El scim-admin configuración de usuario, cuando SCIM está habilitado en su dispositivo GitHub Enterprise Server.

## Referencias

[GitHub docs](https://docs.github.com/es/get-started/learning-about-github/githubs-plans)

[GitHub plans](https://github.com/settings/billing/plans)