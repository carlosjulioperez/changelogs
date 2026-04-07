# Design Engineer Roadmap — 16 Semanas
**Prerrequisito:** Completar el roadmap AI Engineer de 16 semanas.  
**Objetivo de empleabilidad:** Design Engineer con stack React/Next.js en producción, capaz de buildear MVPs AI completos con UI de calidad y portfolio que cubra JDs de AI product/infra.

---

## Contexto de mercado

El rol **Design Engineer** cierra el gap entre Figma y código de producción. No es frontend genérico ni UX puro.

JD canónica (MrBeast, Tailwind Labs, startups AI 2026):
- Build polished, production-ready UI using React, Next.js, Tailwind
- Implement motion y micro-interactions con Framer Motion
- Mantener design systems con shadcn/ui como primitivo base
- Traducir Figma a código con estados y flows completos
- Iterar con UI real en lugar de static hand-offs

**Stack target al finalizar:** TypeScript · React 19 · Next.js 15 · Tailwind v4 · shadcn/ui · Framer Motion · Figma · v0.dev · Vercel

---

## Fase 1 — Fundamentos (Semanas 1–4)
*Objetivo: salir de cero frontend. Al terminar puedes construir layouts funcionales con React y Tailwind.*

### Semana 1 — HTML/CSS/Flexbox/Grid + Tailwind v4

**Qué aprender:**
- Box model, Flexbox, CSS Grid desde cero
- Tailwind v4: utility-first, responsive prefixes, dark mode
- Variables CSS y cómo Tailwind las expone

**Recursos:**
- [The Odin Project — Foundations](https://www.theodinproject.com/paths/foundations) — HTML/CSS interactivo, gratis, sin registro
- [Tailwind CSS Docs — Core Concepts](https://tailwindcss.com/docs/utility-first) — oficial, gratis
- [Kevin Powell YouTube](https://www.youtube.com/@KevinPowell) — CSS más sólido que cualquier curso de pago

**Entregable:**  
Clonar visualmente la landing de un producto real (ej: Vercel.com) usando solo HTML + Tailwind. Sin JS. Deploy en Vercel.

---

### Semana 2 — JavaScript/TypeScript esencial para React

**Qué aprender:**
- ES6+: destructuring, spread, optional chaining, async/await, Promises
- TypeScript: tipos básicos, interfaces, generics simples, type narrowing
- DOM no es necesario profundizar — React lo abstrae

**Recursos:**
- [JavaScript.info](https://javascript.info/) — El mejor recurso gratis de JS. Secciones relevantes: Part 1 (The JavaScript language) completa
- [TypeScript Handbook](https://www.typescriptlang.org/docs/handbook/intro.html) — oficial, gratis. Leer hasta "Generics"
- [Matt Pocock — Total TypeScript Tutorials](https://www.totaltypescript.com/tutorials) — gratis, ejercicios interactivos en browser

**Entregable:**  
Script TypeScript que consuma tu propia FastAPI de RAG (del roadmap AI) y formatee los resultados. Ejecutado con `tsx`.

---

### Semana 3 — React 19 Core

**Qué aprender:**
- JSX, componentes funcionales, props, state con `useState`
- `useEffect`, `useRef`, `useContext`
- React 19: Server Components vs Client Components (conceptual)
- Component composition patterns

**Recursos:**
- [React Docs — Learn React](https://react.dev/learn) — oficial y reescrito en 2024, es el mejor punto de entrada
- [Jack Herrington YouTube](https://www.youtube.com/@jherr) — React 19 y patrones modernos
- [roadmap.sh/react](https://roadmap.sh/react) — usa como índice de lo que tienes que saber, no como recurso de aprendizaje

**Entregable:**  
Chat UI funcional en React que consuma tu LLM API (del roadmap AI). Debe manejar streaming, estados de carga, historial de mensajes. Sin estilo por ahora.

---

### Semana 4 — Next.js 15 App Router + Vercel Deploy

**Qué aprender:**
- App Router: file-based routing, layouts, loading/error states
- Server Components, Client Components, cuando usar cada uno
- API Routes en Next.js como proxy hacia tus backends FastAPI
- Deploy en Vercel desde GitHub

**Recursos:**
- [nextjs.org/learn — App Router Course](https://nextjs.org/learn) — oficial, gratis, construyes un dashboard completo
- [nextjs.org/learn/react-foundations](https://nextjs.org/learn/react-foundations) — si necesitas reforzar React antes

**Entregable:**  
Migrar el chat UI de la semana 3 a Next.js App Router. API Route como proxy a FastAPI. Deploy en Vercel con dominio `.vercel.app`. README con arquitectura.

---

## Fase 2 — Design Engineer Stack (Semanas 5–10)
*Objetivo: producir UI de calidad profesional con design systems, animaciones y un workflow Figma→código.*

### Semana 5 — Figma para Design Engineers

**Qué aprender:**
- Auto Layout, Constraints, Variants, Components
- Design tokens, variables (color, spacing, radius)
- Dev Mode: cómo leer Figma como ingeniero y extraer specs
- NO aprender UX research, IA, flujos de usuario — eso no es el objetivo aquí

**Recursos:**
- [Figma Design for Beginners 2025](https://help.figma.com/hc/en-us/articles/30848209492887) — oficial, gratis, 2025
- [Figma Free Crash Course Community File](https://www.figma.com/community/file/1512771800400751467) — gratis en Figma Community
- [Untitled UI — Free Figma UI Kit](https://www.untitledui.com/) — referencia de design system real, gratis

**Entregable:**  
Diseñar en Figma el dashboard principal de tu proyecto AI (RAG UI o agente UI). Usar Auto Layout 5.0 y variables de color/spacing. Exportar design tokens.

---

### Semana 6 — shadcn/ui + Design Systems en código

**Qué aprender:**
- shadcn/ui: filosofía copy-paste, no dependencia de librería
- Configurar shadcn en Next.js, tema, dark mode con CSS variables
- Construir components compuestos (DataTable, Combobox, Command Palette)
- Cuándo usar shadcn vs construir desde cero

**Recursos:**
- [shadcn/ui Docs](https://ui.shadcn.com/docs) — oficial, gratis
- [shadcn/ui Components](https://ui.shadcn.com/components) — referencia completa
- [Theo (t3.gg) YouTube](https://www.youtube.com/@t3dotgg) — patrones reales con shadcn y Next.js

**Entregable:**  
Reimplementar el chat UI del roadmap AI con shadcn/ui. Añadir: Command Palette para cambiar de conversación, DataTable para historial, dark mode toggle. Mismo deploy en Vercel.

---

### Semana 7 — Framer Motion + Micro-interactions

**Qué aprender:**
- `motion.div`, variants, orchestration
- `AnimatePresence` para enter/exit
- `useInView`, `whileInView` para scroll animations
- `useSpring`, `useTransform` para física
- Cuándo NO animar (performance, accesibilidad)

**Recursos:**
- [Framer Motion Docs](https://www.framer.com/motion/) — oficial, gratis
- [Motion Primitives](https://motion-primitives.com/) — componentes copy-paste con Framer Motion + Tailwind, gratis
- [Aceternity UI](https://ui.aceternity.com/) — referencia de animaciones de hero section, gratis

**Entregable:**  
Añadir al chat UI: transición suave al cargar mensajes, animación de streaming token por token, micro-interaction en el send button, page transition al navegar entre conversaciones.

---

### Semana 8 — Figma → v0.dev → Producción (Vibe Design workflow)

**Qué aprender:**
- v0.dev: generar componentes desde descripción o screenshot de Figma
- Iterar con v0 en el browser, exportar a tu Next.js project
- Google Stitch (si tienes acceso beta): text-to-UI de alta fidelidad
- Workflow: diseño en Figma → vibe en v0 → refinamiento en código → deploy

**Recursos:**
- [v0.dev](https://v0.dev/) — gratis (plan free con límites razonables)
- [v0 Docs](https://v0.dev/docs) — oficial
- [Google Stitch](https://stitch.withgoogle.com/) — solicitar acceso, anunciado 19 marzo 2026

**Entregable:**  
Usar v0.dev para generar el dashboard del proyecto AI a partir del diseño de Figma de la semana 5. Integrar los componentes generados en tu Next.js. Documentar qué tuvo que ser refactorizado a mano y por qué.

---

### Semana 9 — Responsive Design + Accesibilidad (a11y)

**Qué aprender:**
- Tailwind breakpoints, container queries
- Responsive con Next.js Image, font optimization
- WCAG 2.1 AA: contraste, focus management, ARIA
- Radix UI primitivos (base de shadcn) y por qué son accesibles por defecto
- Core Web Vitals: LCP, CLS, INP — cómo diagnosticar con Vercel Analytics

**Recursos:**
- [Tailwind Docs — Responsive Design](https://tailwindcss.com/docs/responsive-design) — gratis
- [web.dev — Accessibility](https://web.dev/accessibility/) — Google, gratis
- [Vercel Analytics](https://vercel.com/docs/analytics) — free en plan hobby

**Entregable:**  
Auditar el proyecto AI UI con Lighthouse y axe-core. Alcanzar 90+ en performance, 90+ en accessibility. Documentar los 3 problemas más críticos encontrados y cómo los resolviste.

---

### Semana 10 — Data Visualization para AI dashboards

**Qué aprender:**
- Recharts con shadcn: gráficas para métricas de modelos
- Tanstack Table v8: tablas con sort, filter, pagination
- Visualizar: latencia de LLM, tokens/sec, retrieval scores de RAG, traces de agentes
- Streaming updates con Server-Sent Events en Next.js

**Recursos:**
- [Recharts Docs](https://recharts.org/en-US) — gratis
- [shadcn Charts](https://ui.shadcn.com/charts) — integración Recharts + shadcn, gratis
- [Tanstack Table Docs](https://tanstack.com/table/latest) — gratis

**Entregable:**  
Dashboard de observabilidad para tu agente AI: gráfica de latencia por llamada, tabla de traces con filter por status, visualización de retrieval scores. Conectado a tu backend de Langfuse (del roadmap AI).

---

## Fase 3 — Producción y Portfolio (Semanas 11–16)
*Objetivo: buildear MVPs completos y un portfolio que cubra JDs reales.*

### Semana 11 — State Management + Forms en producción

**Qué aprender:**
- Zustand para estado global ligero (reemplaza Redux en proyectos modernos)
- React Hook Form + Zod para validación type-safe
- Server Actions de Next.js 15: mutations sin API routes explícitas
- Optimistic updates con `useOptimistic`

**Recursos:**
- [Zustand Docs](https://zustand.docs.pmnd.rs/) — gratis
- [React Hook Form Docs](https://react-hook-form.com/) — gratis
- [Next.js — Server Actions Docs](https://nextjs.org/docs/app/building-your-application/data-fetching/server-actions-and-mutations) — gratis

**Entregable:**  
Añadir al proyecto AI: formulario de configuración de agente (modelo, temperatura, system prompt, herramientas activas) con validación Zod, persistencia via Server Action, feedback optimista en UI.

---

### Semana 12 — Auth + Multi-tenancy

**Qué aprender:**
- NextAuth v5 (Auth.js): OAuth con GitHub/Google, JWT sessions
- Middleware de Next.js para proteger rutas
- Supabase como backend de datos si no tienes DB (optional)

**Recursos:**
- [Auth.js Docs](https://authjs.dev/) — gratis
- [Supabase Docs](https://supabase.com/docs) — free tier generoso

**Entregable:**  
Añadir autenticación al proyecto AI. Login con GitHub. Rutas protegidas. Historial de conversaciones asociado al usuario. Deploy completo en Vercel.

---

### Semana 13 — MVP 1: AI SaaS landing page + onboarding

**Qué aprender:**
- Anatomía de una landing page de SaaS moderna
- Copywriting para AI products
- Onboarding flow: de signup a primera acción en < 3 pasos

**Recursos:**
- [Leerling de referencias reales](https://www.saaslandingpage.com/) — galería de landing pages reales, gratis
- [Tailark](https://tailark.com/) — bloques de marketing con shadcn, gratis

**Entregable:**  
Landing page completa para uno de tus proyectos AI: hero section con animación, feature grid, pricing, FAQ. Onboarding en 3 pasos con progress indicator. Deploy en Vercel con dominio personalizado opcional.

---

### Semana 14 — MVP 2: Admin dashboard completo

**Qué aprender:**
- Sidebar navigation con collapse (shadcn Sidebar component)
- Breadcrumbs, command palette global
- Role-based UI (show/hide según permisos)

**Recursos:**
- [shadcn Sidebar Docs](https://ui.shadcn.com/docs/components/sidebar) — gratis

**Entregable:**  
Dashboard completo de administración para tu plataforma AI: sidebar colapsable, command palette (Cmd+K), métricas en tiempo real (SSE), tabla de usuarios/conversaciones, settings. Todo con TypeScript estricto.

---

### Semana 15 — Performance + DX profesional

**Qué aprender:**
- Bundle analysis con `@next/bundle-analyzer`
- Dynamic imports y code splitting
- Image optimization pipeline
- Storybook 8 para component documentation
- Chromatic para visual regression testing

**Recursos:**
- [Next.js Docs — Optimizing](https://nextjs.org/docs/app/building-your-application/optimizing) — gratis
- [Storybook Docs](https://storybook.js.org/docs) — gratis

**Entregable:**  
Componentes críticos del proyecto AI documentados en Storybook con stories para todos los estados. Bundle size < 250KB (gzip) en first load JS. Score Lighthouse > 90 en todas las categorías.

---

### Semana 16 — Portfolio final + preparación JD

**Qué aprender:**
- Portfolio site como producto, no como CV
- Case studies: problema → decisión de diseño → implementación → métricas
- Preparar para JD screening de Design Engineer

**Entregable:**  
Portfolio site desplegado en Vercel con:

1. **AI Chat Platform** — RAG + agente + UI completa (semanas 3–12)
2. **MLOps Dashboard** — observabilidad + métricas en tiempo real (semana 10)
3. **AI SaaS landing + onboarding** (semana 13)
4. **Component library** documentada en Storybook (semana 15)

Cada proyecto con: live demo, GitHub repo, case study de 200 palabras, stack badges.

---

## Stack de herramientas AI para acelerar el workflow

Estas herramientas son parte del flujo Vibe Design — no son muletas, son el workflow estándar de Design Engineers en 2026:

| Herramienta | Uso | Costo |
|---|---|---|
| [v0.dev](https://v0.dev) | Generar componentes desde descripción/screenshot | Free tier |
| [Google Stitch](https://stitch.withgoogle.com) | Text-to-UI de alta fidelidad | Beta gratuita |
| [Cursor](https://cursor.sh) | IDE con AI inline para refinar componentes | Free tier |
| [Vercel](https://vercel.com) | Deploy + Analytics + Edge Functions | Free hobby |
| [Figma](https://figma.com) | Design + Dev Mode + Prototipado | Free tier |

---

## Mapa de dependencias entre roadmaps

```
Roadmap AI Engineer (16 semanas)
  └─ FastAPI backends ──────────────────┐
  └─ LLM APIs / RAG / Agentes ──────────┤
  └─ Langfuse observability ────────────┤
                                         ▼
                              Design Engineer (este roadmap)
                                 └─ Construye la UI encima de todo eso
                                 └─ Portfolio integrado, no aislado
```

El resultado no son dos portfolios separados. Es uno solo: un AI product completo con backend AI-grade y frontend de producción.

---

## Recursos permanentes de referencia

- [roadmap.sh/frontend](https://roadmap.sh/frontend) — índice de skill coverage
- [web.dev](https://web.dev/) — performance y web standards
- [Untitled UI Blog](https://www.untitledui.com/blog) — recursos de diseño UI curados
- [Tailwind CSS Docs](https://tailwindcss.com/docs) — referencia permanente
- [shadcn/ui](https://ui.shadcn.com/) — referencia permanente
- [Framer Motion Docs](https://www.framer.com/motion/) — referencia permanente
