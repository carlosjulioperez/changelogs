Voy a ser **directo y brutal**, como pediste.

Gran parte de tu lista es **ruido de Twitter, newsletters y artículos sueltos** que **no te van a dar empleabilidad real**. DevOps/MLOps se aprende **con terminal, repos, clusters y pipelines corriendo**.
Todo lo que sea:

* tweets
* newsletters
* “100 days of X”
* artículos de opinión
* PDFs de roadmap

➡️ **no te da skill productivo.** Lo elimino.

Tu objetivo correcto es:

> **Backend Dev → DevOps → AI Infra / MLOps**
> construyendo **pipelines reales en producción**

Eso requiere **solo 8 bloques reales**:

1. Linux + Networking
2. Git + Automation
3. Containers (Docker)
4. CI/CD
5. Kubernetes
6. Cloud (AWS o GCP)
7. Infrastructure as Code
8. Observability + SRE
9. MLOps layer (después)

Todo lo demás es **decoración**.

---

# Roadmap brutal DevOps → AI Infra (16 semanas)

Si trabajas **3-5h diarias**, en **4 meses** puedes estar listo para roles junior DevOps / Platform.

---

# W1–W2 — Linux REAL (no teoría)

Si no dominas Linux, estás muerto en DevOps.

![Image](https://haseebmajid.dev/posts/2023-05-08-my-development-workflow-with-linux/images/fun.png)

![Image](https://media2.dev.to/dynamic/image/width%3D1280%2Cheight%3D720%2Cfit%3Dcover%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Ffox5hguxv5n9mzs0dyib.png)

![Image](https://www.linuxfoundation.org/hs-fs/hubfs/Imported_Blog_Media/standard-unix-filesystem-hierarchy-1.png?height=1001\&name=standard-unix-filesystem-hierarchy-1.png\&width=1817)

![Image](https://miro.medium.com/0%2AbFnHaO8eYpW3dSuz)

### Aprende solo esto

* filesystem
* processes
* ssh
* permissions
* logs
* networking tools
* bash scripting

### Recursos (hands-on)

**Linux Journey**

[https://linuxjourney.com/](https://linuxjourney.com/)

**Missing Semester MIT**

[https://missing.csail.mit.edu/](https://missing.csail.mit.edu/)

**Bash scripting**

[https://www.shellscript.sh/](https://www.shellscript.sh/)

### Proyecto obligatorio

Crear repo:

```
linux-devops-toolkit
```

scripts:

```
backup.sh
log-parser.sh
deploy.sh
health-check.sh
```

Si no escribes scripts → **no eres DevOps**.

---

# W3 — Networking para DevOps

La mayoría de devs fallan aquí.

Aprende:

```
DNS
TCP/IP
HTTP
Ports
Load balancing
NAT
Reverse proxy
```

### Recurso bueno

Cloudflare learning

[https://www.cloudflare.com/learning/network-layer/what-is-the-network-layer/](https://www.cloudflare.com/learning/network-layer/what-is-the-network-layer/)

### Proyecto

Configurar:

```
nginx reverse proxy
2 apps backend
load balancing
```

---

# W4 — Git avanzado

No Git básico.

Necesitas:

```
rebase
cherry-pick
bisect
hooks
gitflow
```

### Recurso

[https://learngitbranching.js.org/](https://learngitbranching.js.org/)

### Proyecto

Crear pipeline repo:

```
microservices-demo
```

con:

```
3 servicios
gitflow
PR pipeline
```

---

# W5–W6 — Docker (core DevOps)

![Image](https://media2.dev.to/dynamic/image/width%3D800%2Cheight%3D%2Cfit%3Dscale-down%2Cgravity%3Dauto%2Cformat%3Dauto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2F7298dbklbkky66pmpu4d.png)

![Image](https://miro.medium.com/1%2A1YxpABThWxBlytz2LRTIKA.jpeg)

![Image](https://miro.medium.com/1%2AuuZ-h5EH76LOtJ614z-qDA.png)

![Image](https://learn.microsoft.com/en-us/dotnet/architecture/microservices/docker-application-development-process/media/docker-app-development-workflow/life-cycle-containerized-apps-docker-cli.png)

### Aprende

```
Dockerfile
multi-stage builds
docker compose
volumes
networks
image optimization
```

### Mejor recurso práctico

Docker official tutorial

[https://docs.docker.com/get-started/](https://docs.docker.com/get-started/)

### Proyecto obligatorio

Containerizar:

```
backend API
redis
postgres
nginx
```

con

```
docker-compose
```

---

# W7–W8 — CI/CD real

Aquí empieza el valor real.

![Image](https://razorops.com/images/blog/stages-of-ci-cd-pipeline.jpg)

![Image](https://i.sstatic.net/fkLD3.png)

![Image](https://cdn.sanity.io/images/z7wg6mcy/production-2025/5f7de2ca91f3176ece8f67bc969d54c8a7dd79d3-4312x3140.png)

![Image](https://www.xenonstack.com/hubfs/xenonstack-jenkins-dashboard-visualization-services.png)

### Aprende

```
pipelines
artifacts
build automation
testing automation
deployment automation
```

### Herramienta recomendada

NO Jenkins primero.

Empieza con:

**GitHub Actions**

[https://docs.github.com/actions](https://docs.github.com/actions)

### Proyecto

Pipeline:

```
push → test → build docker → push image → deploy
```

---

# W9–W10 — Kubernetes (core skill)

![Image](https://kubernetes.io/images/docs/kubernetes-cluster-architecture.svg)

![Image](https://devopscube.com/content/images/2025/03/kubernetes-pod-1.png)

![Image](https://matthewpalmer.net/kubernetes-app-developer/articles/deployment-yaml-diagram.gif)

![Image](https://matthewpalmer.net/kubernetes-app-developer/articles/service-annotated.png)

### Aprende SOLO esto

```
pods
deployments
services
configmaps
secrets
ingress
autoscaling
```

### Curso práctico bueno

Kubernetes Basics

[https://kubernetes.io/docs/tutorials/kubernetes-basics/](https://kubernetes.io/docs/tutorials/kubernetes-basics/)

### Cluster local

Instala:

```
kind
```

[https://kind.sigs.k8s.io/](https://kind.sigs.k8s.io/)

### Proyecto

Deploy microservices stack:

```
API
worker
redis
postgres
nginx ingress
```

---

# W11–W12 — Cloud (elige UNO)

NO aprendas 3 clouds.

### Mejor ROI

```
AWS
```

Aprende solo:

```
EC2
ECR
EKS
S3
IAM
VPC
Load Balancer
```

### Recurso brutal (hands-on)

[https://cloudresumechallenge.dev/](https://cloudresumechallenge.dev/)

### Proyecto

Deploy:

```
k8s cluster
CI/CD pipeline
container registry
```

---

# W13 — Terraform

![Image](https://cms.cloudoptimo.com/uploads/terraform_eaa800441c.png)

![Image](https://miro.medium.com/v2/resize%3Afit%3A1400/1%2AMTdEQWZ-Wpr5iRPWWvJX0g.jpeg)

![Image](https://d2908q01vomqb2.cloudfront.net/77de68daecd823babbb58edb1c8e14d7106e83bb/2023/10/06/ServiceCatalog-TerraformCloud-RE.png)

![Image](https://assets.numericaideas.com/2023/09/Terraform-Introduction-min.png)

### Aprende

```
providers
resources
modules
state
variables
```

### Recurso oficial

[https://developer.hashicorp.com/terraform/tutorials](https://developer.hashicorp.com/terraform/tutorials)

### Proyecto

Provisionar:

```
VPC
EKS
registry
network
```

con Terraform.

---

# W14 — Observability

![Image](https://devopscube.com/content/images/size/w1200/2025/03/prometheus-grafan-dashboard-1.png)

![Image](https://raw.githubusercontent.com/instrumentisto/grafana-dashboard-kubernetes-prometheus/master/screens/total.png)

![Image](https://signoz.io/img/guides/2024/07/how-does-prometheus-work-Untitled.webp)

![Image](https://prometheus.io/assets/docs/architecture.svg)

### Stack estándar

```
Prometheus
Grafana
Loki
```

### Tutorial

[https://prometheus.io/docs/prometheus/latest/getting_started/](https://prometheus.io/docs/prometheus/latest/getting_started/)

### Proyecto

Monitorear:

```
cluster
API latency
CPU
memory
errors
```

---

# W15 — SRE skills

Aprende:

```
SLI
SLO
incident response
runbooks
alerting
```

### Libro obligatorio

Google SRE

[https://sre.google/books/](https://sre.google/books/)

Lee solo:

```
SLI/SLO
Monitoring
Incident response
```

---

# W16 — Introducción a MLOps / AI infra

Cuando ya sabes DevOps.

![Image](https://ml-ops.org/img/mlops-phasen.jpg)

![Image](https://cdn-uploads.huggingface.co/production/uploads/6262fb8e6f289e10ee04f83b/vUc6IgSbrxn5T9jaR5_Ov.png)

![Image](https://miro.medium.com/max/1400/1%2AWNn0RhcPt_UCDhwRUnNj4A.gif)

![Image](https://dev-kit.io/uploads/mlflow_tracking_chart_cdccca1f2c.webp)

### Stack actual

```
MLflow
Kubeflow
Airflow
Feature stores
GPU scheduling
```

### Tutorial

MLflow

[https://mlflow.org/docs/latest/index.html](https://mlflow.org/docs/latest/index.html)

### Proyecto

Pipeline:

```
train model
track experiment
build docker
deploy inference API
monitor model
```

---

# Proyectos que te dan trabajo

Debes terminar con **3 repos públicos fuertes**.

### 1️⃣ DevOps pipeline

```
microservices
docker
CI/CD
k8s
monitoring
```

---

### 2️⃣ Infra as Code

```
terraform
aws
eks
network
```

---

### 3️⃣ MLOps pipeline

```
mlflow
model deployment
k8s inference
monitoring
```

---

# Stack final (sin humo)

```
Linux
Bash
Git
Docker
Kubernetes
GitHub Actions
AWS
Terraform
Prometheus
Grafana
MLflow
```

Nada más.

---

# Cosas que eliminé sin piedad

De tu lista:

❌ newsletters
❌ tweets
❌ "100 days of cloud"
❌ artículos motivacionales
❌ roadmaps PDF

Eso **no genera skill productivo**.

---

# Brutal realidad del mercado

DevOps juniors que **sí reciben ofertas** tienen:

```
Docker
Kubernetes
CI/CD
Terraform
AWS
```

* repos con **pipelines reales**.

Si no tienes **infra corriendo**, **nadie te contrata**.

---

Si quieres, también puedo darte:

**1️⃣ El roadmap REAL para pasar de DevOps → AI Infrastructure Engineer (el perfil mejor pagado de 2026)**
**2️⃣ Los 12 proyectos open-source que más contratan DevOps hoy**
**3️⃣ Cómo montar un homelab DevOps completo por $0** (clusters, CI/CD, monitoring, ML pipelines).
