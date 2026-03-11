Ahora tengo suficiente contexto. Aquí va el análisis brutal y el roadmap definitivo:

---

## Análisis de los artículos W1

**[Learn Python and Build Autonomous Agents (FCC)](https://www.freecodecamp.org/news/learn-python-and-build-autonomous-agents/)**
Curso de 6 horas en YouTube que cubre Python desde cero hasta agentes AI: Python esencial, NumPy/Pandas/SQL, APIs con FastAPI, y finalmente integración con LLMs (ChatGPT, Gemini, HuggingFace) más herramientas de agentes.

**Veredicto para ti como Backend**: Módulos 1 y 2 son **skip total** — ya sabes programar. Módulos 3 (FastAPI) y 4 (LLMs + Agents) son los únicos que importan. Sáltate ~3h de las 6h.

**[How to Build Your Own MCP Server with Python (FCC)](https://www.freecodecamp.org/news/how-to-build-your-own-mcp-server-with-python/)**
Tutorial hands-on que usa FastMCP para construir un MCP server real: tools, SSE, deploy a cloud. No vende nada — código en GitHub incluido y gratuito.

**Veredicto**: **Oro puro**. MCP es el estándar que está ganando. Aprenderlo ahora te diferencia.

---

## El roadmap definitivo — sin humo

### Lo que elimino y por qué

**BASURA / RUIDO (eliminar sin piedad):**
- Todos los artículos de Twitter sobre "$500/hour skills in 2027" — puro clickbait de cuentas de growth hacking
- "Chinos reconstruyen OpenClaw" — irrelevante
- "Generar ingresos", "Construye su SaaS", "Automates LinkedIn" — no son skills, son distracciones
- Videos de generar dinero con AI — no te contratan por saber hacer eso
- Ruta ChatGPT, Ruta Gemini, Ruta Grok — son el **mismo contenido triplicado**. Unificar en una sola ruta
- `code-an-llm-from-scratch` (6h) — teoría pura, cero ROI empleable. Las empresas no te pagan por saber construir un transformer
- `build-12-data-science-apps-with-streamlit` — Streamlit es UI toy, no infraestructura
- Cursos Udemy genéricos de LangChain — LangChain está perdiendo terreno vs LangGraph/direct SDK. Solo el de LLM Engineering (202K estudiantes, $65) si tienes presupuesto
- Claude 101 / AI Fluency Framework de Anthropic — marketing disfrazado de educación
- `cs-video-courses` repo de CS general — no es AI, es desvío masivo de tiempo
- "High-Paying Career Paths 2026", "Wall Street traders ML" — ruido motivacional

**LO QUE MANTENGO:** Solo recursos con código real, proyectos desplegables, y skills que aparecen en JDs de AI Engineer / AI Infra Engineer.

---

## ROADMAP DEFINITIVO

> **Premisa**: Ya eres Backend. Python no te asusta. Tienes ~3-4h/día disponibles. Meta: empleable en 8-10 semanas.

---

### W1 — Fundamentos AI + FastAPI + LLM APIs
**Objetivo**: Hacer llamadas reales a LLMs, construir tu primera API que expone un modelo.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [FCC: Learn Python & Build Autonomous Agents](https://youtu.be/UsfpzxZNsPo) — **solo módulos 3 y 4** | ~3h | FastAPI + LLM integration desde cero |
| [Anthropic API Quickstart](https://docs.anthropic.com/en/api/getting-started) | 1h | Aprende la API que más pagan en producción |
| [OpenAI API Quickstart](https://platform.openai.com/docs/quickstart) | 1h | El estándar de la industria |
| [FCC: Development with LLMs](https://www.freecodecamp.org/news/development-with-large-language-models/) | 2h | Patrones reales de integración |

**Proyecto W1**: FastAPI endpoint que recibe un query, llama a Claude/GPT, devuelve respuesta estructurada. Deploy local con Docker.

---

### W2 — RAG completo (el skill más demandado en JDs)
**Objetivo**: Construir un RAG pipeline production-ready de punta a punta.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [FCC: Mastering RAG from Scratch](https://www.freecodecamp.org/news/mastering-rag-from-scratch/) | 2h30 | Fundamentos sólidos sin fluff |
| [FCC: Vector Search and RAG Tutorial](https://www.freecodecamp.org/news/vector-search-and-rag-tutorial-using-llms-with-your-data/) | 1h11 | Embeddings + Vector DB hands-on |
| [LangChain RAG from Scratch](https://github.com/langchain-ai/rag-from-scratch) | 3h | 18 notebooks progresivos, el repo más citado en entrevistas |
| [CognitiveClass: Mastering RAG](https://cognitiveclass.ai/learn/mastering-rag-build-smart-data-driven-application) | 3h55 | 7 guided projects con certificado |

**Proyecto W2**: RAG chatbot sobre documentación técnica. FastAPI backend + ChromaDB/Qdrant + embeddings de OpenAI. Dockerizado.

---

### W3 — Agentes, MCP y Workflows
**Objetivo**: Entender agentes reales (no el hype), MCP como estándar emergente.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [FCC: How to Build Advanced AI Agents](https://www.freecodecamp.org/news/how-to-build-advanced-ai-agents/) | 50min | Patrones de agentes sin frameworks innecesarios |
| [FCC: Build MCP Server with Python](https://www.freecodecamp.org/news/how-to-build-your-own-mcp-server-with-python/) | 2h | MCP es el protocolo que está ganando en producción |
| [FCC: MCP Essentials + FastMCP](https://www.freecodecamp.org/news/learn-mcp-essentials-and-how-to-create-secure-agent-interfaces-with-fastmcp/) | 2h | FastMCP = menos boilerplate, más producción |
| [Microsoft MCP for Beginners (ES)](https://github.com/microsoft/mcp-for-beginners/blob/main/translations/es/README.md) | 3h | Curso oficial con ejemplos reales |
| [FCC: LangGraph](https://www.freecodecamp.org/news/learn-langgraph-and-build-conversational-ai-with-python/) | 3h | LangGraph > LangChain para agentes stateful en 2025+ |

**Proyecto W3**: Agente con tools (web search + DB query + code execution). Expuesto via MCP server. LangGraph para el workflow.

---

### W4 — Agentic RAG (combina todo)
**Objetivo**: El tier de skill que separa juniors de seniors en JDs.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [Agentic RAG for Dummies](https://github.com/GiovanniPasq/agentic-rag-for-dummies) | 4h | Repo hands-on, progresivo, bien mantenido |
| [Production Agentic RAG Course](https://github.com/jamwithai/production-agentic-rag-course) | 6h | El repo más completo de RAG en producción de la lista |
| [CognitiveClass: Agentic AI Hands-On](https://cognitiveclass.ai/learn/agentic-ai-hands-on) | 11h | 7 guided projects, certificado IBM |
| [LlamaIndex docs + tutorials](https://github.com/run-llama/llama_index) | 3h | Alternativa a LangChain, muy usada en producción enterprise |

**Proyecto W4**: Agentic RAG con routing inteligente (decide cuándo hacer RAG vs responder directo vs usar tool). Eval básica con RAGAS.

---

### W5 — Evaluación + Observability (el skill que nadie aprende y todos necesitan)
**Objetivo**: Demostrar que puedes medir y debuggear sistemas AI en producción.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [RAGAS documentation + examples](https://docs.ragas.io/en/stable/) | 3h | Estándar de facto para eval de RAG |
| [Langfuse quickstart](https://langfuse.com/docs/get-started) | 2h | Observability open-source, aparece en JDs |
| [Weights & Biases LLM monitoring](https://wandb.ai/site/llm) | 2h | El estándar en ML teams |
| [Arize Phoenix](https://github.com/Arize-ai/phoenix) | 2h | Open-source, tracing + eval, muy demandado |

**Proyecto W5**: Agrega eval + tracing a tu proyecto de W4. Dashboard con métricas reales (faithfulness, relevance, latency).

---

### W6 — Local Models + Ollama + GPU Inference
**Objetivo**: Saber deployar modelos sin depender de APIs de terceros (crítico para enterprise).

| Recurso | Tiempo | Por qué |
|---|---|---|
| [FCC: Local AI Development with Ollama](https://www.freecodecamp.org/news/local-ai-development-with-ollama-course/) | 3h | Covers Ollama + Streamlit + local inference completo |
| [FCC: How to Use DeepSeek R1](https://www.freecodecamp.org/news/how-to-use-deepseek-r1/) | 1h30 | Modelo open-source más relevante ahora mismo |
| [Hugging Face: Inference Endpoints docs](https://huggingface.co/docs/inference-endpoints/index) | 2h | Cómo deployar modelos a escala |
| [vLLM quickstart](https://docs.vllm.ai/en/latest/getting_started/quickstart.html) | 2h | El servidor de inferencia GPU más usado en producción |

**Proyecto W6**: Llama 3 / Mistral corriendo con Ollama localmente. Mismo RAG pipeline de W2 pero con modelo local. Benchmark latency vs API.

---

### W7 — Docker + Deployment production-grade
**Objetivo**: Como Backend ya sabes Docker. Aquí aplicas eso a sistemas AI con sus particularidades.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [FCC: RAG and MCP Fundamentals](https://www.freecodecamp.org/news/learn-rag-and-mcp-fundamentals/) | 1h39 | Integra todo en un pipeline deployable |
| [FastAPI deployment guide](https://fastapi.tiangolo.com/deployment/) | 2h | Ya conoces el framework, ahora producción |
| [Docker AI workloads — GPU containers](https://docs.docker.com/guides/use-case/gpu-llm/) | 2h | Específico para LLMs con GPU |
| [Modal.com quickstart](https://modal.com/docs/guide) | 2h | Deploy de inferencia GPU serverless, muy demandado en startups |

**Proyecto W7**: Dockerizar tu stack completo (RAG API + Vector DB + LLM). docker-compose funcional. Deploy en Railway/Render.

---

### W8 — Kubernetes + AI Infra (el tier de $180k-$300k)
**Objetivo**: El salto de AI Engineer a AI Infrastructure Engineer.

| Recurso | Tiempo | Por qué |
|---|---|---|
| [Harvard ML Systems Book](https://mlsysbook.ai/book/) | ongoing | La biblia de ML Systems, gratuita, referenciada en entrevistas de big tech |
| [Kubernetes for ML — KubeFlow basics](https://www.kubeflow.org/docs/started/introduction/) | 4h | Orquestación de ML workloads |
| [AI Engineering Field Guide](https://github.com/alexeygrigorev/ai-engineering-field-guide) | 3h | Repo de referencia con patrones de producción |
| [AI Engineering Hub](https://github.com/patchy631/ai-engineering-hub) | ongoing | Colección de notebooks de infra AI |
| [Google ADK Fundamentals](https://www.skills.google/paths/3473) | 3h | Google te certifica gratis. Aparece bien en CV |

**Proyecto W8**: Pipeline completo en Kubernetes local (minikube). FastAPI + Vector DB + modelo inference en pods separados. HPA configurado.

---

### W9-W10 — Portfolio + Evaluación final

**El portfolio que te contrata (3 proyectos, no 10):**

1. **Production RAG API** — FastAPI + ChromaDB/Qdrant + Claude/GPT + Docker + eval con RAGAS + tracing con Langfuse. README con architecture diagram.
2. **Agentic MCP System** — Agente con 3-5 tools real (no demos), expuesto via MCP server, LangGraph workflow, observable.
3. **Local Inference Stack** — vLLM o Ollama serviendo un modelo open-source, benchmarked, dockerizado, con API compatible OpenAI.

**Recursos de apoyo continuo (no cursos, referencias):**
- [roadmap.sh/ai-engineer](https://roadmap.sh/ai-engineer) — para verificar gaps
- [github.com/mlabonne/llm-course](https://github.com/mlabonne/llm-course) — para deep-dives puntuales
- [CognitiveClass: Fundamentals of AI Agents](https://cognitiveclass.ai/learn/fundamentals-of-ai-agents) — si necesitas llenar gaps de conceptos

---

## Veredicto brutal sobre el resto de la lista

| Recurso | Veredicto |
|---|---|
| FCC 65h GenAI Bootcamp | Demasiado amplio, bajo ROI por hora invertida. Los recursos específicos del roadmap > esto |
| Udemy LLM Engineering (202K, 33h) | **El único Udemy que vale** si tienes $65 y quieres estructura. Omitir el resto |
| Cognitive Class GPT-5 course | El nombre es marketing. El contenido es genérico |
| Andrew Ng tweet sobre bootcamps | Clickbait. Ni lo abras |
| "Libros" tweet | Sin contexto, sin links, sin valor |
| FCC Build RAG with JavaScript | Tú eres Backend Python ahora. JavaScript para AI = callejón sin salida |
| Anthropic Claude 101 / skilljar | Marketing puro. Los docs oficiales valen más |

---

## Stack final coherente que dominas en 10 semanas

```
Python → FastAPI → LLM APIs (Anthropic/OpenAI) →
Embeddings → ChromaDB/Qdrant → RAG → Agentic RAG →
LangGraph → MCP → RAGAS/Langfuse → Ollama/vLLM →
Docker → Kubernetes básico → GPU inference
```

Ese stack exacto aparece en JDs de AI Engineer en Anthropic, Cohere, startups bien financiadas, y enterprises con equipos AI internos. No es teoría — es lo que los hiring managers buscan cuando filtran CVs en 2026.