# Guía de despliegue

Este repositorioo incluye un workflow de ejemplo para desplegar a un servidor remoto usando SSH y `rsync`:

- Archivo del workflow: .github/workflows/deploy.yml

Secrets requeridos (configurar en Settings → Secrets and variables → Actions):

- `SSH_PRIVATE_KEY`: clave privada SSH (sin passphrase o con passphrase gestionada por el runner). Debe corresponder a la clave pública autorizada en el servidor.
- `SSH_HOST`: host o IP del servidor remoto (ej. example.com)
- `SSH_USER`: usuario SSH en el servidor remoto (ej. ubuntu)
- `TARGET_DIR`: ruta en el servidor donde se subirán los archivos (ej. /var/www/my-site)

Notas de uso:

- El workflow detecta proyectos Node/Python de forma sencilla y ejecuta pasos básicos de build si encuentra `package.json` o `requirements.txt`/`pyproject.toml`.
- Asegúrate de que el servidor remoto tenga permisos y suficiente espacio para recibir los archivos.
- Puedes adaptar el workflow a Docker Hub, GitHub Pages, AWS, etc., cambiando la sección de deploy.

Integración con Jira/Atlassian

Este workflow ahora crea un `GitHub Deployment` y marca su estado como `success`. Si instalas la integración oficial
de Atlassian ↔️ GitHub (por ejemplo, la app "Atlassian for GitHub"), Jira Cloud puede detectar estos despliegues y
mostrarlos en la pestaña "Deployments" cuando haya asociaciones con commits o issues.

Pasos recomendados:

- Instala la integración Atlassian ↔ GitHub desde el marketplace o desde la configuración de tu proyecto/organización.
- Asegúrate de que tus commits incluyan claves de Jira (p. ej. `PROJ-123`) o que tus cambios estén vinculados mediante la app.
- Opcional: en lugar de la integración, puedes usar la API de Deployments de Jira para reportar despliegues directamente (ver notas anteriores).

¿Quieres que añada la configuración para desplegar y publicar una imagen Docker en Docker Hub, o un paso para reportar también a la API de Jira?
