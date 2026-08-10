Responde brevemente en inglés a cada pregunta para un entrevistador generado por AI para un rol de Fullstack developer:

### 1. TTL Cache Eviction Strategy

- 1. If you implement a TTL cache, how do you handle actual eviction of expired items to prevent memory leaks over time?

I combine two strategies to manage memory efficiently:

* **Lazy (Passive) Eviction:** Check item expiration upon access and remove it if expired.
* **Active Eviction:** Run a background scheduled task (or a probabilistic sample, like Redis does) that periodically sweeps through keys to remove expired, unaccessed items and prevent memory leaks.

### 2. PostgreSQL Materialized Views

- 2. What are materialized views in PostgreSQL, and when would you use them over standard views for read-heavy workloads?

* **What they are:** Unlike standard views (which execute the underlying query on every request), materialized views persist the query results to disk as an actual table.
* **When to use:** In read-heavy, latency-sensitive workloads with expensive aggregations where real-time accuracy isn't strictly required. You can refresh them periodically (e.g., via background job or `REFRESH MATERIALIZED VIEW CONCURRENTLY`) to keep data reasonably fresh without blocking reads.


### 3. React Functional Lifecycle & Memoization

- 3. Explain the React lifecycle for functional components and hooks. How do you use useMemo and useCallback to prevent unnecessary re-renders?

* **Lifecycle:** Functional components don't have explicit lifecycle methods like class components; instead, `useEffect` handles side effects, mirroring mounting, updating, and unmounting based on its dependency array.
* **`useMemo`:** Caches the **result of a calculation** so expensive computations aren't re-run unless dependencies change.
* **`useCallback`:** Caches a **function instance** between renders to prevent breaking reference equality on child props, stopping child components wrapped in `React.memo` from unnecessarily re-rendering.

### 4. Spring Boot Clean Architecture

- 4. How do you structure a Spring Boot app for clean architecture, keeping core business logic separate from infrastructure and framework?

To decouple core domain logic from the framework and infrastructure:

* **Domain Layer:** Core entities and pure business logic at the center, free from Spring annotations or database dependencies.
* **Application/Use Case Layer:** Defines inbound/outbound ports (interfaces) for actions and repository operations.
* **Adapter/Infrastructure Layer:** Implements outbound ports (e.g., Spring Data JPA repositories, external HTTP clients) and inbound adapters (e.g., `@RestController` entry points). Dependency injection handles binding without the core knowing about Spring details.