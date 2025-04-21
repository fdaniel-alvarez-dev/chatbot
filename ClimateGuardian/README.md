ClimateGuardian
Descripción General

ClimateGuardian es una plataforma digital desarrollada por NGO-ModernEdge diseñada para monitorear, analizar y reportar datos climáticos, facilitando la gestión de proyectos ambientales y la coordinación entre organizaciones sin fines de lucro dedicadas a la protección del medio ambiente.
Características Principales

    Monitoreo Ambiental: Seguimiento de indicadores climáticos en tiempo real

    Gestión de Proyectos: Herramientas para planificar y ejecutar iniciativas ambientales

    Análisis de Datos: Visualizaciones y reportes sobre impacto ambiental

    Colaboración: Espacios para coordinación entre múltiples ONGs

    Portal de Transparencia: Información pública sobre proyectos e impacto

Guía de Despliegue
1. Requisitos Previos

    Servidor con sistema operativo Linux (Ubuntu 20.04 LTS recomendado)

    Docker y Docker Compose instalados

    Mínimo 4GB RAM, 2 CPUs

    Dominio configurado con registros DNS apuntando al servidor

    Certificado SSL (recomendado Let's Encrypt)

2. Configuración del Entorno

    Clonar el repositorio:

    git clone https://github.com/ngo-modernedge/platform.git

    Crear archivo

    .env

    con variables de entorno necesarias

    Configurar credenciales de base de datos y servicios externos

    Establecer URL del sitio y parámetros de correo electrónico

3. Instalación

    Ejecutar

    docker-compose build

    para construir las imágenes

    Iniciar servicios con

    docker-compose up -d

    Ejecutar migraciones de base de datos:

    docker-compose exec app python manage.py migrate

    Crear superusuario:

    docker-compose exec app python manage.py createsuperuser

4. Configuración de Seguridad

    Configurar firewall (permitir puertos 80, 443)

    Instalar y configurar Let's Encrypt para HTTPS

    Configurar cabeceras de seguridad en el servidor web

    Implementar política de contraseñas seguras

5. Mantenimiento

    Configurar copias de seguridad automáticas

    Establecer monitoreo del sistema

    Procedimiento de actualización:

    git pull && docker-compose down && docker-compose build && docker-compose up -d

    Rotación de logs y gestión de almacenamiento

Contribuciones

Si deseas contribuir al proyecto ClimateGuardian, por favor consulta nuestras guías de contribución en la documentación oficial.
Soporte

Para soporte técnico, contacta a nuestro equipo en support@ngo-modernedge.org o abre un issue en el repositorio de GitHub.
Licencia

ClimateGuardian está disponible bajo la licencia MIT. Ver el archivo LICENSE para más detalles.
