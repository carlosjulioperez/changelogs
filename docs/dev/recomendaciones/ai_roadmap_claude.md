Aquí el roadmap definitivo. Recursos verificados y activos al día de hoy.

## STACK OBJETIVO (coherente con JDs reales)

```
Python → FastAPI → LLM APIs → Embeddings → RAG → Vector DB
→ LangGraph (Agents) → Evaluation (RAGAS) → Observability (Langfuse)
→ Docker → Kubernetes → Ollama/vLLM → GPU inference → MLOps
```

---

## ROADMAP — 16 SEMANAS

### FASE 1 — Python AI-Ready + APIs (W1–W2)

**W1**
**[FCC] Learn Python and Build Autonomous Agents** (6h)
https://www.freecodecamp.org/news/learn-python-and-build-autonomous-agents/
Cubre Python moderno, NumPy, Pandas, FastAPI, LLM APIs, HuggingFace. Punto de entrada correcto dado tu background Java/Kotlin.

**W2**
**[FCC] How to Build Advanced AI Agents** (50min — denso)
https://www.freecodecamp.org/news/how-to-build-advanced-ai-agents/

Complemento inmediato: estructura de agentes, tool calling, agentic loops con código real.

---

### FASE 2 — RAG Core + Vector DB (W3–W5)

**W3**
**[FCC] Vector Search and RAG Tutorial** (1h11)
https://www.freecodecamp.org/news/vector-search-and-rag-tutorial-using-llms-with-your-data/

Embeddings, búsqueda semántica, integración con LLMs. Base técnica de todo lo que sigue.

**W4**
**[FCC] Mastering RAG from Scratch** (2h30)
https://www.freecodecamp.org/news/mastering-rag-from-scratch/

Chunking, retrieval strategies, reranking, evaluación básica. El más completo del stack RAG en FCC.

**W5**
**[GitHub] RAG from Scratch — LangChain**
https://github.com/langchain-ai/rag-from-scratch
18 notebooks progresivos. Query transformation, multi-vector, RAPTOR. Ejecutar todos los notebooks.

---

### FASE 3 — LangGraph + Agents (W6–W7)

**W6**
**[FCC] Learn LangGraph and Build Conversational AI** (3h)
https://www.freecodecamp.org/news/learn-langgraph-and-build-conversational-ai-with-python/

Grafos de estado, 5 agentes desde cero, RAG integrado con LangGraph.

**W7**
**[FCC] Learn RAG and MCP Fundamentals** (1h39)
https://www.freecodecamp.org/news/learn-rag-and-mcp-fundamentals/

RAG + MCP side-by-side. MCP aquí ya tiene sentido porque se introduce como patrón de tool use, no como framework aislado.

---

### FASE 4 — Local Models + GPU Inference (W8–W9)

**W8**
**[FCC] Local AI Development with Ollama** (3h)
https://www.freecodecamp.org/news/local-ai-development-with-ollama-course/

Ollama, modelos locales, Streamlit UI, integración con RAG pipelines.

**W9**
**[GitHub] mlabonne/llm-course — Sección "LLM Engineer"** (LLM APIs, quantization, deployment)
https://github.com/mlabonne/llm-course
Usar exclusivamente la sección del LLM Engineer (no la parte de researcher). Colab notebooks ejecutables. Cubre vLLM, GGUF, inferencia local optimizada.

**Recurso adicional — vLLM Docs (hands-on)**
https://docs.vllm.ai/en/latest/getting_started/quickstart.html
Desplegar un modelo con vLLM en local/Docker. Esto aparece explícitamente en JDs de AI Infra.

---

### FASE 5 — Production RAG System (W10–W13)

**Este bloque es el núcleo de tu portfolio.**

**[GitHub] jamwithai/production-agentic-rag-course** (7 semanas de material, tú lo comprimes en 4)
https://github.com/jamwithai/production-agentic-rag-course

Stack que cubre: Docker + FastAPI + PostgreSQL + OpenSearch + Airflow + Ollama + LangGraph + Langfuse + Redis.
- W10 → Week 1–2 del repo: infraestructura + pipeline de datos
- W11 → Week 3–4: hybrid search + embeddings reales
- W12 → Week 5–6: RAG completo + observabilidad con Langfuse
- W13 → Week 7: Agentic RAG con LangGraph. **Este es tu proyecto de portfolio #1.**

---

### FASE 6 — Evaluation + MLOps (W14–W16)

**W14**
**[GitHub] RAGAS — Evaluación de RAG**
https://github.com/explodinggradients/ragas
Evaluar el sistema construido en Fase 5 con RAGAS. Faithfulness, answer relevancy, context precision. Integrar métricas al pipeline.

**W15–W16**
**[DataTalks.Club] MLOps Zoomcamp** (módulos selectivos)
https://github.com/DataTalksClub/mlops-zoomcamp

Usar solo: Módulo 1 (MLflow experiment tracking), Módulo 4 (deployment), Módulo 5 (monitoring con Evidently). Ignorar los módulos de batch scoring que no aplican a tu stack.

**Complemento Kubernetes — recurso oficial**
https://kubernetes.io/docs/tutorials/kubernetes-basics/
Los 6 módulos interactivos del tutorial oficial. Suficiente para lo que aparece en JDs de AI Infra a nivel entry/mid.

---

## RECURSOS FALTANTES AGREGADOS (alto ROI, verificados)

**LLM Zoomcamp — DataTalks.Club**
https://github.com/DataTalksClub/llm-zoomcamp
10 semanas de material sobre RAG, búsqueda elástica, agentes, evaluación. Usar en paralelo como referencia durante Fases 2–4.

**Langfuse Docs + Quickstart**
https://langfuse.com/docs/get-started
Observabilidad de producción. Trazas, scores, datasets de evaluación. Aparece en el repo de jamwithai y en JDs reales de AI Infra.

**FastAPI Official Tutorial** (si necesitas refuerzo)
https://fastapi.tiangolo.com/tutorial/
No es un curso, es la documentación. Directamente ejecutable. Tu background Java/Spring hace que esto sea trivial.

---

## PROYECTOS DE PORTFOLIO (lo que contrata la industria)

**Proyecto 1 (W13):** Production Agentic RAG — el sistema completo del repo de jamwithai desplegado con Docker Compose, con Langfuse activo y métricas de RAGAS documentadas.

**Proyecto 2 (W16):** Tomar el sistema anterior y agregar: endpoint vLLM con modelo local como alternativa al API externo, pipeline de evaluación continua con RAGAS, y deployment en Kubernetes (minikube local cuenta).

Estos dos proyectos responden a más del 80% de los requerimientos técnicos en JDs de AI Engineer y AI Infrastructure Engineer de empresas que pagan bien.