# ci-cd-hackaton-juanfuentes
Categoría Básica (Si, este readme fue hecho en los 5 minutos de IA)

# CI/CD Hackaton - Juan Fuentes

## 🏆 Categoría de Participación
**Categoría Básica**

## 📋 Descripción del Proyecto
Este proyecto demuestra la automatización del ciclo de vida de una aplicación web simple usando GitHub Actions para CI/CD y desplegándola en AWS S3. El objetivo es implementar buenas prácticas de seguridad y DevOps.

### 🚀 Tecnologías Utilizadas
- **Frontend:** HTML básico
- **CI/CD:** GitHub Actions
- **Cloud:** AWS S3 (Static Website Hosting)
- **Control de Versiones:** Git/GitHub

## 🏗️ Arquitectura del Proyecto

```
├── .github/
│   └── workflows/
│       └── deploy.yml          # Pipeline de CI/CD
├── src/
│   ├── index.html             # Página principal
│   └── error.html             # Página de error
└── README.md                  # Documentación
```

## 🔧 Configuración del Pipeline CI/CD

### Pipeline Stages:
1. **Checkout:** Descarga del código fuente
2. **Build:** Preparación de archivos para despliegue
3. **Configure AWS:** Configuración de credenciales
4. **Verify Connection:** Verificación de conectividad con AWS
5. **Deploy:** Subida de archivos a S3 con Content-Type correcto
6. **Cache Headers:** Configuración de headers HTTP

### Triggers:
- Push a ramas `main` o `master`
- Pull requests a ramas `main` o `master`
- Ejecución manual (`workflow_dispatch`)

## ☁️ Despliegue en AWS

### Servicio: AWS S3 Static Website Hosting
- **Bucket:** `juanfuentes3bucket`
- **Región:** us-east-2 (Ohio)
- **URL:** http://juanfuentes3bucket.s3-website.us-east-2.amazonaws.com

### Configuración S3:
- Static website hosting habilitado
- Index document: `index.html`
- Error document: `error.html`
- Acceso público configurado
- Bucket policy para lectura pública

## 🔐 Buenas Prácticas de Seguridad Implementadas

### 1. ✅ GitHub Secrets para Credenciales
Todas las credenciales sensibles están almacenadas como secrets:
- `AWSACESSKEY_ID`: Access Key ID de AWS
- `AWSSECRETACESS_KEY`: Secret Access Key de AWS
- `AWS_REGION`: Región de AWS
- `S3BUCKETNAME`: Nombre del bucket S3

### 2. ✅ Principio de Menor Privilegio
- Usuario IAM con permisos mínimos necesarios solo para S3
- Bucket policy restrictiva solo para operaciones de lectura pública

### 3. ✅ Separación de Ambientes
- Configuración específica por ambiente usando secrets
- Pipeline que verifica conectividad antes del despliegue

### 4. ✅ Versionado y Trazabilidad
- Control de versiones con Git
- Logs detallados en cada step del pipeline
- Información de despliegue al finalizar

## 🚀 Instrucciones de Despliegue

### Prerrequisitos:
1. Cuenta de AWS con permisos para S3
2. Usuario IAM configurado
3. Bucket S3 creado y configurado para static hosting

### Pasos para Desplegar:

1. **Clonar el repositorio:**
   ```bash
   git clone https://github.com/juanfuentes-code/ci-cd-hackaton-juanfuentes.git
   cd ci-cd-hackaton-juanfuentes
   ```

2. **Configurar GitHub Secrets:**
   - Ir a Settings → Secrets and variables → Actions
   - Agregar los secrets mencionados arriba

3. **Realizar cambios y push:**
   ```bash
   git add .
   git commit -m "Deploy changes"
   git push origin main
   ```

4. **Verificar despliegue:**
   - Revisar Actions tab en GitHub
   - Acceder a la URL del sitio web

## 📁 Estructura de Archivos

### `src/index.html`
```html
<h1>Hola :D</h1>
```

### `.github/workflows/deploy.yml`
Pipeline completo de CI/CD con:
- Configuración de AWS
- Deploy con Content-Type correcto
- Configuración de cache headers
- Verificaciones de seguridad

## 🔍 Monitoreo y Logs

- **GitHub Actions:** Logs detallados de cada ejecución
- **AWS CloudTrail:** Seguimiento de acciones en AWS (opcional)
- **S3 Access Logs:** Logs de acceso al sitio web (opcional)

## 🎯 Resultados Esperados

- ✅ Sitio web accesible públicamente
- ✅ Despliegue automatizado en cada push
- ✅ Credenciales seguras usando GitHub Secrets
- ✅ Pipeline robusto con verificaciones

## 🏆 Logros del Hackaton

Este proyecto demuestra:
- Implementación exitosa de CI/CD con GitHub Actions
- Despliegue en cloud (AWS S3)
- Aplicación de múltiples buenas prácticas de seguridad
- Documentación clara y completa
- Trabajo en categoría "Tecnología no dominada"

---

**Desarrollado por:** Juan Fuentes  
**Fecha:** Julio 2025  
**Hackaton:** CI/CD Automation Challenge
