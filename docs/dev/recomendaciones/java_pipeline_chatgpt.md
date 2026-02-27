Perfecto. Vamos a construir un **proyecto realista, enterprise-ready y 100% portfolio**, usando herramientas que sí pide la industria y con planes gratuitos.

Stack que usaremos:

* Backend: **Spring Boot**
* Control de versiones: **GitHub**
* CI/CD: **GitHub Actions**
* Contenedores: **Docker**
* Registro de imágenes: **GitHub Container Registry**
* Cloud (Free Tier real): **Render**
* Infraestructura como código: **Terraform**
* Seguridad: **OWASP Dependency-Check**
* Calidad: **SonarCloud**

Objetivo final:
Tener un pipeline completo:

```
Push → Test → Static Analysis → Security Scan → Build Docker → Push Image → Deploy automático a Cloud
```

Todo listo para mostrar en CV y entrevistas.

---

# 🔥 Estructura Final del Proyecto

```
springboot-cicd-enterprise/
│
├── src/
├── Dockerfile
├── docker-compose.yml
├── pom.xml
├── .github/workflows/ci-cd.yml
├── terraform/
│   └── main.tf
├── README.md
└── README-PIPELINE.md
```

---

# 🧩 PARTE 1 — Crear la aplicación Spring Boot

## Paso 1 — Crear proyecto en Spring Initializr

Ve a:
[https://start.spring.io](https://start.spring.io)

Configura:

* Project: Maven
* Language: Java
* Spring Boot: última estable
* Group: com.portfolio
* Artifact: cicd
* Java: 17
* Dependencies:

  * Spring Web
  * Spring Data JPA
  * H2
  * Spring Boot Actuator
  * Lombok
  * Spring Security

Descarga y descomprime.

---

## Paso 2 — Crear API sencilla (Enterprise Style)

### Controller

```java
package com.portfolio.cicd.controller;

import org.springframework.web.bind.annotation.*;

@RestController
@RequestMapping("/api/v1/hello")
public class HelloController {

    @GetMapping
    public String hello() {
        return "CI/CD Pipeline Working!";
    }
}
```

---

## Paso 3 — Agregar Health Check (para deploy real)

En `application.properties`:

```properties
management.endpoints.web.exposure.include=health,info
management.endpoint.health.show-details=always
```

Esto es importante para Render.

---

## Paso 4 — Tests

```java
@SpringBootTest
class CicdApplicationTests {

    @Test
    void contextLoads() {
    }
}
```

---

# 🐳 PARTE 2 — Dockerización

## Dockerfile

```dockerfile
FROM eclipse-temurin:17-jdk-alpine
WORKDIR /app
COPY target/cicd-0.0.1-SNAPSHOT.jar app.jar
ENTRYPOINT ["java","-jar","app.jar"]
```

---

## Construcción local

```bash
./mvnw clean package
docker build -t cicd-app .
docker run -p 8080:8080 cicd-app
```

Probar:

```
http://localhost:8080/api/v1/hello
```

---

# 🚀 PARTE 3 — Subir a GitHub

1. Crear repositorio en GitHub
2. Subir código:

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/TU_USUARIO/springboot-cicd-enterprise.git
git push -u origin main
```

---

# ⚙️ PARTE 4 — CI/CD con GitHub Actions

Crear archivo:

```
.github/workflows/ci-cd.yml
```

---

## Pipeline completo Enterprise-Ready

```yaml
name: CI-CD Pipeline

on:
  push:
    branches: [ "main" ]

jobs:

  build-test:
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Set up JDK 17
        uses: actions/setup-java@v3
        with:
          distribution: 'temurin'
          java-version: '17'

      - name: Build and Test
        run: mvn clean verify

      - name: OWASP Dependency Check
        run: mvn org.owasp:dependency-check-maven:check

  docker-build:
    needs: build-test
    runs-on: ubuntu-latest

    steps:
      - uses: actions/checkout@v3

      - name: Login to GitHub Container Registry
        run: echo "${{ secrets.GITHUB_TOKEN }}" | docker login ghcr.io -u ${{ github.actor }} --password-stdin

      - name: Build Docker image
        run: |
          docker build -t ghcr.io/${{ github.repository }}/cicd-app:latest .

      - name: Push Docker image
        run: |
          docker push ghcr.io/${{ github.repository }}/cicd-app:latest
```

---

# ☁️ PARTE 5 — Deploy automático en Render (Gratis)

1. Crear cuenta en Render
2. New → Web Service
3. Conectar repo GitHub
4. Configuración:

* Environment: Docker
* Auto Deploy: Yes
* Health Check Path:

```
/actuator/health
```

Ahora cada push → despliegue automático.

---

# 🏗 PARTE 6 — Infraestructura como Código (Terraform)

Crear carpeta:

```
terraform/main.tf
```

```hcl
terraform {
  required_providers {
    render = {
      source = "render-oss/render"
    }
  }
}

provider "render" {
  api_key = var.render_api_key
}
```

(Para portafolio esto es suficiente como demostración)

---

# 🔎 PARTE 7 — Calidad con SonarCloud

1. Crear cuenta en SonarCloud
2. Vincular GitHub
3. Agregar secret en GitHub:

```
SONAR_TOKEN
```

Agregar step en pipeline:

```yaml
- name: SonarCloud Scan
  run: mvn sonar:sonar \
    -Dsonar.projectKey=TU_PROJECT_KEY \
    -Dsonar.organization=TU_ORG \
    -Dsonar.host.url=https://sonarcloud.io \
    -Dsonar.login=${{ secrets.SONAR_TOKEN }}
```

---

# 📄 README.md (PORTFOLIO-READY)

```
# Spring Boot Enterprise CI/CD Pipeline

Production-ready CI/CD pipeline built with:

- Spring Boot
- GitHub Actions
- Docker
- GitHub Container Registry
- OWASP Security Scan
- SonarCloud Code Quality
- Terraform Infrastructure as Code
- Render Cloud Deployment

## Architecture

Developer → GitHub → CI Pipeline → Docker Build → Security Scan → Deploy to Cloud

## Features

- Automated Testing
- Security Dependency Scan
- Static Code Analysis
- Containerized Deployment
- Infrastructure as Code
- Health Checks
- Production Ready

## Live Demo

https://your-app.onrender.com/api/v1/hello
```

---

# 📘 README-PIPELINE.md

Explica:

* Etapas del pipeline
* Seguridad integrada
* Estrategia de branching
* Buenas prácticas enterprise

---

# 🎯 Qué Logras para tu CV

Podrás decir:

✔ Diseñé pipeline CI/CD enterprise-ready
✔ Integré análisis estático y escaneo de vulnerabilidades
✔ Implementé despliegue automático en cloud
✔ Contenerización con Docker
✔ Infraestructura como código
✔ Seguridad shift-left

---

# 🏆 Cómo Presentarlo a Reclutadores

En tu CV:

> Designed and implemented an enterprise-grade CI/CD pipeline using Spring Boot, GitHub Actions, Docker, SonarCloud and automated cloud deployment on Render.

En LinkedIn:
Video corto mostrando:

* Push
* Pipeline ejecutándose
* Deploy automático

---

# 🚀 Si quieres subir esto a nivel Senior DevOps:

Podemos agregar:

* Kubernetes (k3s)
* Blue/Green deployment
* Canary
* Trivy image scan
* ArgoCD
* AWS Free Tier versión real enterprise

---

Si quieres, ahora podemos:

1. Convertirlo en versión AWS real enterprise
2. Hacerlo multi-environment (dev/stage/prod)
3. Agregar Kubernetes
4. Prepararlo específicamente para entrevistas FAANG/Big Tech

Tú dime tu objetivo profesional y lo afinamos para que sea un proyecto que impresione reclutadores.
