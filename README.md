# 🚀 CI Spring Boot con GitHub Actions

## 📌 Descripción del proyecto
Este repositorio contiene un proyecto **Spring Boot** configurado con un **proceso de Integración Continua (CI)** utilizando **GitHub Actions**, cuyo objetivo es automatizar la compilación, ejecución de pruebas y construcción de una imagen Docker en cada cambio realizado sobre la rama principal (`main`).

El proyecto fue desarrollado como práctica para **reforzar los conocimientos adquiridos en CI/CD**, aplicando herramientas utilizadas en entornos reales de desarrollo de software.

---

## 🎯 Objetivo
Implementar un proceso de **CI (Continuous Integration)** que permita:

- Compilar el proyecto automáticamente.
- Ejecutar pruebas unitarias e integración.
- Construir una imagen Docker lista para despliegue.
- Ejecutarse de forma automática en cada `push` a la rama `main`.

---

## 🛠️ Tecnologías utilizadas
- **Java 17**
- **Spring Boot**
- **Maven**
- **GitHub Actions**
- **Docker**
- **H2 Database**

---

## ⚙️ Proceso de Integración Continua (CI)
El pipeline de CI está definido en el archivo:


.github/workflows/ci.yml


Este workflow se ejecuta **automáticamente en cada push a la rama `main`** y realiza los siguientes pasos:

1. Checkout del código fuente desde el repositorio.
2. Configuración del entorno **Java 17**.
3. Asignación de permisos de ejecución a **Maven Wrapper (`mvnw`)**.
4. Compilación del proyecto y ejecución de pruebas mediante **Maven**.
5. Construcción de una imagen **Docker** lista para despliegue.

---

## 🧪 Build y pruebas
El pipeline ejecuta el siguiente comando:

```bash
./mvnw clean verify


Este comando:

Compila el proyecto.

Ejecuta pruebas unitarias e integración.

Genera el archivo .jar de la aplicación.

🐳 Docker

El proyecto incluye un archivo Dockerfile en la raíz del repositorio, el cual permite construir una imagen Docker de la aplicación Spring Boot.

Dockerfile
FROM eclipse-temurin:17-jdk-alpine

WORKDIR /app

COPY target/*.jar app.jar

EXPOSE 8080

ENTRYPOINT ["java", "-jar", "app.jar"]


Durante el pipeline se ejecuta:

docker build -t myapp:latest .


Esto genera una imagen Docker lista para ser utilizada en un entorno de despliegue.

✅ Resultado

El proceso de CI se ejecuta correctamente en cada push a main.

El pipeline finaliza exitosamente (estado verde en GitHub Actions).

El proyecto cumple con todos los requisitos planteados en la consigna.

📎 Conclusión

La implementación de este pipeline permitió aplicar de manera práctica los conceptos de Integración Continua, automatizando tareas clave del ciclo de desarrollo y asegurando que el código sea compilado, probado y empaquetado correctamente en cada cambio.

Este flujo de trabajo representa una base sólida para futuras implementaciones de Continuous Deployment (CD).
