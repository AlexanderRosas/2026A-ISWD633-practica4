# COMPLETAR  
Antes de esta práctica, veía a los contenedores como cajas que simplemente "corrían" software. No era consciente de que, en un entorno real de producción, un contenedor mal configurado puede consumir toda la RAM del servidor y tumbar otros servicios.

Principales aprendizajes:

  Control de Recursos: Aprendí a poner límites de CPU y memoria (--memory y --cpus). Esto es clave para la estabilidad del sistema y para evitar costos innecesarios en la nube.

  Automatización con Dockerfile: Entendí que el Dockerfile es el "receta" de la infraestructura. El concepto de capas y caché es fundamental: si ordenas bien las instrucciones, las imágenes se construyen mucho más rápido.

  Monitoreo de Salud: Configurar HEALTHCHECK me enseñó que no basta con que un contenedor esté "Up"; hay que verificar que el servicio interno (como Apache o MySQL) realmente esté respondiendo.

Problemas solucionados:
  Al principio, al probar los límites de memoria, puse un valor demasiado bajo (menos de 6m) y Docker me dio un error de validación. También tuve problemas con el caché del Dockerfile porque no entendía por qué no se actualizaban mis cambios en el HTML, hasta que comprendí que cualquier cambio en un archivo copiado invalida las capas siguientes en la construcción.

Comandos adicionales:

docker stats: Lo usé para ver en tiempo real si el contenedor respetaba el límite de memoria asignado.

docker inspect --format='{{.State.Health.Status}}': Para verificar si el Healthcheck estaba pasando de "starting" a "healthy".
