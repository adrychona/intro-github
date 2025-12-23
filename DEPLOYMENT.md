# Guía de despliegue

Este repositorio incluye un workflow de ejemplo para desplegar a un servidor remoto usando SSH y `rsync`:

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

¿Quieres que configure una variante para Docker Hub, GitHub Pages o un proveedor en concreto?
