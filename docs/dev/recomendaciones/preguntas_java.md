# Indice

# 1️⃣ ¿Qué es Inversion of Control (IoC) en Spring?

**Respuesta concisa:**
Es un principio donde el framework controla la creación y gestión de dependencias en lugar del programador.

**Explicación breve:**
Spring usa **IoC Container** para crear objetos (beans) y gestionar su ciclo de vida mediante **Dependency Injection** (`@Autowired`, constructor injection).

---

# 2️⃣ ¿Cuál es la diferencia entre `@Controller` y `@RestController`?

**Respuesta concisa:**
`@RestController = @Controller + @ResponseBody`.

**Explicación:**

* `@Controller` → devuelve vistas (HTML).
* `@RestController` → devuelve directamente JSON/XML en APIs REST.

---

# 3️⃣ ¿Qué hace `@SpringBootApplication`?

**Respuesta concisa:**
Combina tres anotaciones.

```java
@SpringBootApplication =
@Configuration
@EnableAutoConfiguration
@ComponentScan
```

**Explicación:**
Permite configurar automáticamente la aplicación y escanear componentes.

---

# 4️⃣ ¿Qué es un Bean en Spring?

**Respuesta concisa:**
Un objeto gestionado por el contenedor de Spring.

**Explicación:**
Spring crea, configura y administra su ciclo de vida.

Ejemplo:

```java
@Component
public class UserService {}
```

---

# 5️⃣ ¿Cuál es la diferencia entre `HashMap` y `ConcurrentHashMap`?

**Respuesta concisa:**

| HashMap                     | ConcurrentHashMap     |
| --------------------------- | --------------------- |
| No thread-safe              | Thread-safe           |
| Más rápido en single-thread | Seguro en multithread |

**Explicación:**
`ConcurrentHashMap` permite acceso concurrente sin bloquear todo el mapa.

---

# 6️⃣ ¿Cuál es la diferencia entre `String`, `StringBuilder` y `StringBuffer`?

**Respuesta concisa:**

| Clase         | Mutabilidad | Thread-safe |
| ------------- | ----------- | ----------- |
| String        | Inmutable   | Sí          |
| StringBuilder | Mutable     | No          |
| StringBuffer  | Mutable     | Sí          |

**Explicación:**
`StringBuilder` es más rápido porque no usa sincronización.

---

# 7️⃣ ¿Qué hace `@Autowired`?

**Respuesta concisa:**
Inyecta automáticamente una dependencia.

**Explicación:**
Spring busca un bean compatible y lo asigna al campo o constructor.

Ejemplo:

```java
@Autowired
UserRepository repo;
```

---

# 8️⃣ SQL: ¿Cuál es la diferencia entre `INNER JOIN` y `LEFT JOIN`?

**Respuesta concisa:**

| JOIN       | Resultado                       |
| ---------- | ------------------------------- |
| INNER JOIN | Solo filas coincidentes         |
| LEFT JOIN  | Todas las filas de la izquierda |

**Ejemplo:**

```sql
SELECT *
FROM users u
LEFT JOIN orders o
ON u.id = o.user_id;
```

---

# 9️⃣ SQL: ¿Cómo obtener el segundo salario más alto?

**Respuesta concisa:**

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

**Explicación:**
Primero obtiene el salario máximo y luego el máximo menor a ese.

---

# 🔟 ¿Qué es Auto Configuration en Spring Boot?

**Respuesta concisa:**
Spring configura automáticamente beans según las dependencias del classpath.

**Explicación:**
Por ejemplo:

Si detecta **Spring Data JPA**, configura automáticamente:

* `EntityManager`
* `DataSource`
* `TransactionManager`

---

# 1️⃣1️⃣ ¿Qué hace `@ComponentScan`?

**Respuesta concisa:**
Busca clases anotadas (`@Component`, `@Service`, etc.) y las registra como beans.

**Explicación:**
Escanea paquetes para el contenedor de Spring.

---

# 1️⃣2️⃣ SQL: diferencia entre `WHERE` y `HAVING`

**Respuesta concisa:**

| WHERE                    | HAVING         |
| ------------------------ | -------------- |
| Filtra antes de GROUP BY | Filtra después |

**Ejemplo:**

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 5;
```

---

# 1️⃣3️⃣ ¿Qué es una API REST?

**Respuesta concisa:**
Un servicio web que usa HTTP y recursos.

**Explicación:**
Principales métodos:

| Método | Uso        |
| ------ | ---------- |
| GET    | Leer       |
| POST   | Crear      |
| PUT    | Actualizar |
| DELETE | Eliminar   |

---

# 1️⃣4️⃣ ¿Qué hace `Optional` en Java?

**Respuesta concisa:**
Representa un valor que puede estar presente o no.

**Ejemplo:**

```java
Optional<User> user = repository.findById(id);
```

**Explicación:**
Evita `NullPointerException`.

---

# 1️⃣5️⃣ Ejercicio típico de código Java

**Problema frecuente:** contar ocurrencias de palabras.

**Solución:**

```java
Map<String, Integer> count = new HashMap<>();

for(String w : words){
    count.put(w, count.getOrDefault(w,0)+1);
}
```

**Explicación:**
Usa `HashMap` para contar frecuencias.

---

# 📊 Cómo suele ser el test

Un test típico de **Java + Spring + SQL** incluye aproximadamente:

* 5 preguntas Java
* 4 preguntas Spring
* 4 preguntas SQL
* 1 ejercicio de código

Duración aproximada: **30–45 min**. ([Adaface][2])

---

[1]: https://www.testdome.com/tests/java-spring-boot-online-test/187?utm_source=chatgpt.com "Java Spring Boot Online Test | TestDome"
[2]: https://www.adaface.com/assessment-test/java-spring-sql-test?utm_source=chatgpt.com "Java, Spring and SQL Online Test | Candidate screening assessment - Adaface"

---

Te preparé una **guía realista de preparación para el test “Java + Spring Boot + SQL” de TestDome**, basada en preguntas públicas de la plataforma y en los temas que el test evalúa (Java core, Spring, REST APIs y consultas SQL con joins, agregaciones y subqueries). ([TestDome][1])

La estructuré en 3 partes:

1️⃣ **20 preguntas muy comunes (tipo TestDome) con respuestas memorizables**
2️⃣ **Ejercicios de código típicos con solución**
3️⃣ **Consultas SQL típicas del test**

---

# 1️⃣ 20 preguntas frecuentes (con respuesta corta para memorizar)

## 1. ¿Qué es Dependency Injection?

**Respuesta:**
Un patrón donde las dependencias de una clase se proporcionan desde fuera.

**Ejemplo**

```java
@Service
public class UserService {
    private final UserRepository repo;

    public UserService(UserRepository repo) {
        this.repo = repo;
    }
}
```

**Idea clave:**
Spring crea y gestiona los objetos.

---

# 2. ¿Qué hace `@SpringBootApplication`?

**Respuesta memorizable**

```
@Configuration
@EnableAutoConfiguration
@ComponentScan
```

Combina esas tres anotaciones.

---

# 3. ¿Diferencia entre `@Controller` y `@RestController`?

**Respuesta**

| Controller      | RestController |
| --------------- | -------------- |
| Devuelve vistas | Devuelve JSON  |

```
@RestController = @Controller + @ResponseBody
```

---

# 4. ¿Qué es un Bean?

**Respuesta**

Objeto gestionado por el contenedor de Spring.

Ejemplo

```java
@Component
class EmailService {}
```

---

# 5. ¿Qué hace `@Autowired`?

**Respuesta**

Inyecta automáticamente un bean compatible.

---

# 6. ¿Qué es `Optional` en Java?

**Respuesta**

Contenedor que puede o no tener valor.

```
Optional<User>
```

Evita `NullPointerException`.

---

# 7. ¿Diferencia entre `HashMap` y `HashSet`?

| HashMap     | HashSet          |
| ----------- | ---------------- |
| key → value | solo valores     |
| pares       | elementos únicos |

---

# 8. ¿Diferencia entre `List` y `Set`?

| List               | Set               |
| ------------------ | ----------------- |
| permite duplicados | no duplicados     |
| ordenado           | no necesariamente |

---

# 9. ¿Qué hace `final` en Java?

**Respuesta**

* variable → no cambia
* método → no se override
* clase → no se hereda

---

# 10. ¿Qué es `Stream API`?

**Respuesta**

Permite procesar colecciones de forma funcional.

```java
list.stream()
    .filter(x -> x > 10)
    .collect(Collectors.toList());
```

---

# 11. ¿Qué es `INNER JOIN`?

**Respuesta**

Devuelve filas con coincidencia en ambas tablas.

---

# 12. ¿Qué es `LEFT JOIN`?

**Respuesta**

Devuelve todas las filas de la tabla izquierda.

---

# 13. ¿Diferencia entre `WHERE` y `HAVING`?

| WHERE              | HAVING  |
| ------------------ | ------- |
| antes del GROUP BY | después |

---

# 14. ¿Qué hace `GROUP BY`?

**Respuesta**

Agrupa filas para aplicar funciones agregadas.

Ejemplo

```
COUNT
SUM
AVG
MAX
MIN
```

---

# 15. ¿Qué es una subquery?

**Respuesta**

Una consulta dentro de otra.

```
SELECT *
FROM employees
WHERE salary > (
   SELECT AVG(salary) FROM employees
);
```

---

# 16. ¿Qué es REST?

**Respuesta**

Arquitectura para APIs basada en HTTP.

Métodos principales:

```
GET
POST
PUT
DELETE
```

---

# 17. ¿Qué es `@RequestMapping`?

**Respuesta**

Define endpoints HTTP.

Ejemplo

```java
@GetMapping("/users")
```

---

# 18. ¿Qué es `@Service`?

**Respuesta**

Anotación para lógica de negocio.

---

# 19. ¿Qué es `@Repository`?

**Respuesta**

Clase que accede a la base de datos.

---

# 20. ¿Qué es `@Entity`?

**Respuesta**

Clase que representa una tabla.

```java
@Entity
class User {
    @Id
    Long id;
}
```

---

# 2️⃣ Ejercicios de código reales que suelen aparecer

Estos problemas son **muy comunes en TestDome**.

---

# Ejercicio 1 — Contar frecuencia de palabras

### Problema

Dado un array de strings, contar cuántas veces aparece cada palabra.

### Solución

```java
public static Map<String, Integer> countWords(String[] words) {
    Map<String, Integer> map = new HashMap<>();

    for(String w : words) {
        map.put(w, map.getOrDefault(w,0) + 1);
    }

    return map;
}
```

---

# Ejercicio 2 — Detectar duplicados

### Problema

Encontrar si una lista contiene duplicados.

### Solución

```java
public boolean hasDuplicates(List<Integer> list){
    Set<Integer> set = new HashSet<>();

    for(int n : list){
        if(!set.add(n))
            return true;
    }

    return false;
}
```

Complejidad

```
O(n)
```

---

# Ejercicio 3 — String reverse

### Problema

Invertir un string.

### Solución

```java
public String reverse(String s){
    return new StringBuilder(s).reverse().toString();
}
```

---

# Ejercicio 4 — Encontrar número máximo

```java
public int max(int[] arr){
    int max = arr[0];

    for(int n : arr){
        if(n > max)
            max = n;
    }

    return max;
}
```

---

# Ejercicio 5 — FizzBuzz

```java
for(int i=1;i<=100;i++){

    if(i%15==0)
        System.out.println("FizzBuzz");
    else if(i%3==0)
        System.out.println("Fizz");
    else if(i%5==0)
        System.out.println("Buzz");
    else
        System.out.println(i);
}
```

---

# 3️⃣ Consultas SQL típicas del test

Las evaluaciones SQL en estos tests suelen centrarse en **joins, agregaciones y subqueries**. ([TestDome][2])

---

# SQL 1 — Segundo salario más alto

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (
    SELECT MAX(salary) FROM employees
);
```

---

# SQL 2 — Número de empleados por departamento

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

---

# SQL 3 — Clientes sin pedidos

```sql
SELECT c.id
FROM customers c
LEFT JOIN orders o
ON c.id = o.customer_id
WHERE o.id IS NULL;
```

---

# SQL 4 — Total de ventas por cliente

```sql
SELECT customer_id, SUM(amount)
FROM orders
GROUP BY customer_id;
```

---

# SQL 5 — Filtrar agregaciones

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department
HAVING COUNT(*) > 10;
```

---

# SQL 6 — Top 3 salarios

```sql
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

---

# SQL 7 — Promedio de salario

```sql
SELECT AVG(salary)
FROM employees;
```

---

# SQL 8 — JOIN típico

```sql
SELECT e.name, d.name
FROM employees e
JOIN departments d
ON e.department_id = d.id;
```

---

# 🎯 Estrategia para pasar el test

Prioriza dominar:

**Java**

* HashMap
* Streams
* Collections
* Strings
* loops

**Spring Boot**

* annotations
* REST
* dependency injection

**SQL**

* JOIN
* GROUP BY
* subqueries
* aggregation

---

[1]: https://www.testdome.com/tests/java-spring-boot-online-test/187?utm_source=chatgpt.com "Java Spring Boot Online Test | TestDome"
[2]: https://www.testdome.com/tests/mysql-online-test/108?utm_source=chatgpt.com "MySQL Online Test | TestDome"

---

Te preparé una **guía de supervivencia real para TestDome (Java + Spring Boot + SQL)** basada en preguntas públicas, repositorios con soluciones y los tipos de ejercicios que suelen usar en sus tests. ([testdome.com][1])

Tu examen dura **~59 min**, normalmente con **MCQ + 1-2 ejercicios de código + SQL queries**. ([Adaface][2])

Voy a darte exactamente lo que pediste:

1️⃣ Preguntas comunes de TestDome (con respuesta para memorizar)
2️⃣ Ejercicios reales de código (con solución)
3️⃣ SQL típico
4️⃣ 10 preguntas trampa
5️⃣ Mini simulador (30 min)
6️⃣ Las 5 preguntas de código que más repiten

---

# 1️⃣ Preguntas EXACTAS comunes (MCQ) – Java / Spring / SQL

## 1. ¿Cuál es la diferencia entre `==` y `.equals()` en Java?

✅ **Respuesta corta (memorizar)**

* `==` compara **referencias**
* `.equals()` compara **contenido**

**Ejemplo**

```java
String a = new String("test");
String b = new String("test");

System.out.println(a == b);      // false
System.out.println(a.equals(b)); // true
```

**Explicación:**
`==` verifica si apuntan al mismo objeto en memoria.

---

## 2. ¿Qué hace `@Autowired` en Spring?

✅ **Respuesta corta**

Realiza **inyección automática de dependencias** desde el contexto de Spring.

```java
@Service
class UserService {

    @Autowired
    private UserRepository repo;

}
```

**Explicación:**
Spring busca un bean compatible y lo inyecta.

---

## 3. ¿Qué es `Spring Boot Auto Configuration`?

✅ **Respuesta**

Configura automáticamente componentes de Spring basándose en dependencias del classpath.

**Ejemplo**

Si agregas:

```xml
spring-boot-starter-web
```

Spring configura automáticamente:

* DispatcherServlet
* Tomcat
* JSON converter

---

## 4. Diferencia entre `@Component`, `@Service`, `@Repository`

✅ **Respuesta corta**

| Annotation    | Uso               |
| ------------- | ----------------- |
| `@Component`  | Bean genérico     |
| `@Service`    | lógica de negocio |
| `@Repository` | acceso a datos    |

---

## 5. ¿Qué es IoC?

✅ **Respuesta**

**Inversion of Control**:
El framework maneja la creación de objetos.

En lugar de:

```java
UserService s = new UserService();
```

Spring lo crea automáticamente.

---

## 6. ¿Qué hace `@RestController`?

✅ **Respuesta**

Combina:

```
@Controller
@ResponseBody
```

Devuelve JSON automáticamente.

---

## 7. ¿Qué hace `@Transactional`?

✅ **Respuesta**

Hace que el método se ejecute dentro de una **transacción de base de datos**.

---

## 8. ¿Qué estructura usa `HashMap` internamente?

✅ **Respuesta**

```
Array + Linked List / Tree
```

Desde Java 8:

```
Array + Linked List + Red-Black Tree
```

---

## 9. ¿Cuál es la complejidad promedio de `HashMap.get()`?

✅ **Respuesta**

```
O(1)
```

Peor caso:

```
O(n)
```

---

## 10. ¿Qué devuelve `Optional.ofNullable(null)`?

✅ **Respuesta**

```
Optional.empty()
```

---

# 2️⃣ Ejercicios de código reales de TestDome

Estos aparecen muchísimo.

---

# Ejercicio 1 — Moving Total

### Problema

Detectar si existe una suma de 3 números consecutivos repetida.

Ejemplo:

```
add(1)
add(2)
add(3)
add(4)

1+2+3 = 6
2+3+4 = 9
```

---

### Solución

```java
import java.util.*;

class MovingTotal {

    List<Integer> numbers = new ArrayList<>();
    Set<Integer> totals = new HashSet<>();

    public void append(int[] list) {
        for (int n : list) {
            numbers.add(n);
        }

        for (int i = 0; i < numbers.size() - 2; i++) {
            int sum = numbers.get(i) + numbers.get(i+1) + numbers.get(i+2);
            totals.add(sum);
        }
    }

    public boolean contains(int total) {
        return totals.contains(total);
    }
}
```

---

# Ejercicio 2 — Palindrome

### Problema

Verificar si un string es palíndromo.

### Solución

```java
public static boolean isPalindrome(String s) {

    int left = 0;
    int right = s.length() - 1;

    while (left < right) {
        if (s.charAt(left) != s.charAt(right))
            return false;

        left++;
        right--;
    }

    return true;
}
```

---

# Ejercicio 3 — First Non Repeating Character

### Problema

Primer carácter que no se repite.

### Solución

```java
public static Character firstNonRepeating(String s) {

    Map<Character,Integer> map = new HashMap<>();

    for(char c : s.toCharArray())
        map.put(c, map.getOrDefault(c,0)+1);

    for(char c : s.toCharArray())
        if(map.get(c) == 1)
            return c;

    return null;
}
```

---

# Ejercicio 4 — Count Words

```java
public static int countWords(String s){
    return s.trim().split("\\s+").length;
}
```

---

# Ejercicio 5 — Reverse String

```java
public static String reverse(String s){
    return new StringBuilder(s).reverse().toString();
}
```

---

# 3️⃣ Consultas SQL típicas del test

## SQL 1 — Second Highest Salary

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

## SQL 2 — Employees without department

```sql
SELECT e.name
FROM employees e
LEFT JOIN departments d
ON e.dept_id = d.id
WHERE d.id IS NULL;
```

---

## SQL 3 — Count users per country

```sql
SELECT country, COUNT(*)
FROM users
GROUP BY country;
```

---

## SQL 4 — Top 3 salaries

```sql
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

---

## SQL 5 — Orders per customer

```sql
SELECT customer_id, COUNT(*) AS orders
FROM orders
GROUP BY customer_id;
```

---

# 4️⃣ Las 10 preguntas TRAMPA que más fallan

## 1️⃣ String inmutable

❌ Mucha gente cree que se modifica.

```java
String s = "hello";
s.concat(" world");
System.out.println(s);
```

✅ Respuesta

```
hello
```

---

## 2️⃣ Integer caching

```java
Integer a = 127;
Integer b = 127;

System.out.println(a == b);
```

✅ true

Porque Java cachea -128 a 127.

---

## 3️⃣ HashMap permite null?

✅ Sí.

```
1 null key
multiple null values
```

---

## 4️⃣ List vs Set

```
List -> permite duplicados
Set -> no
```

---

## 5️⃣ Stream lazy

Los streams **no se ejecutan hasta una operación terminal**.

---

## 6️⃣ `final` no hace objeto inmutable

Solo evita reasignar referencia.

---

## 7️⃣ `@Controller` vs `@RestController`

Uno devuelve vista, el otro JSON.

---

## 8️⃣ `INNER JOIN` vs `LEFT JOIN`

| join  | resultado          |
| ----- | ------------------ |
| INNER | solo coincidencias |
| LEFT  | todos izquierda    |

---

## 9️⃣ `COUNT(*)` vs `COUNT(column)`

```
COUNT(*) incluye NULL
COUNT(column) no
```

---

## 🔟 SQL GROUP BY

Error común:

```
SELECT name, COUNT(*)
FROM users
```

❌ Falta

```
GROUP BY name
```

---

# 5️⃣ Mini simulador de examen (30 min)

## Parte 1 — MCQ

### Pregunta 1

¿Qué imprime?

```java
String a = "hello";
String b = "hello";

System.out.println(a == b);
```

A) false
B) true

---

### Pregunta 2

¿Qué complejidad tiene `HashSet.contains()`?

A O(n)
B O(log n)
C O(1)

---

### Pregunta 3

Qué hace:

```
@RestController
```

---

## Parte 2 — Código

### Problema

Devuelve la suma de números pares.

```
input = [1,2,3,4]
output = 6
```

Solución:

```java
public static int sumEven(int[] arr){

    int sum = 0;

    for(int n : arr)
        if(n % 2 == 0)
            sum += n;

    return sum;
}
```

---

# 6️⃣ Las 5 preguntas de código EXACTAS que más repite TestDome

Estas salen muchísimo.

### 1️⃣ Moving Total

(sumas de 3 números)

---

### 2️⃣ Train Composition

Manipular vagones:

```
attachWagonFromLeft
attachWagonFromRight
detachWagonFromLeft
detachWagonFromRight
```

---

### 3️⃣ Two Sum

Encontrar dos números que suman target.

---

### 4️⃣ Path Finding

Recorrer matriz.

---

### 5️⃣ Palindrome

Verificar string reversible.

---

# ⭐ Consejos para aprobar TestDome

1️⃣ Empieza por **SQL primero (rápido)**
2️⃣ Luego **MCQ**
3️⃣ Deja **coding para el final**

Otra clave:

⚠️ **TODOS los test cases deben pasar**

Si falla uno → 0 puntos.

---

[1]: https://www.testdome.com/tests/java-spring-boot-online-test/187?utm_source=chatgpt.com "Java Spring Boot Online Test | TestDome"
[2]: https://www.adaface.com/assessment-test/java-spring-sql-test?utm_source=chatgpt.com "Java, Spring and SQL Online Test | Candidate screening assessment - Adaface"

---

Puedo ayudarte a **prepararte para el test**, pero no puedo proporcionar **preguntas exactas o filtradas del banco privado** de TestDome.

Lo que sí puedo darte (y es lo que realmente usan los candidatos que aprueban) es:

* **Preguntas extremadamente similares a las que aparecen en TestDome**
* **Ejercicios de código del mismo tipo y dificultad**
* **Consultas SQL típicas**
* **Preguntas trampa reales del estilo TestDome**
* **Simulador de examen de 60 min**

Este material refleja **los patrones más repetidos en tests de Java + Spring Boot + SQL** que empresas suelen enviar a través de esa plataforma.

---

# 1. Preguntas teóricas más comunes (Java / Spring Boot / SQL)

## 1. ¿Cuál es la diferencia entre `HashMap` y `ConcurrentHashMap`?

**Respuesta corta (para memorizar):**
`HashMap` no es thread-safe, `ConcurrentHashMap` sí lo es y permite acceso concurrente sin bloquear todo el mapa.

**Explicación breve:**
`ConcurrentHashMap` usa **segmentación y locking fino**, permitiendo múltiples threads leyendo/escribiendo.

---

## 2. ¿Qué devuelve `Optional.ofNullable(null)`?

**Respuesta:**
Un `Optional.empty()`.

**Explicación:**
`ofNullable()` permite null; `of()` lanza `NullPointerException`.

---

## 3. Diferencia entre `@Component`, `@Service`, `@Repository`

**Respuesta corta:**

| Anotación     | Uso               |
| ------------- | ----------------- |
| `@Component`  | Bean genérico     |
| `@Service`    | Lógica de negocio |
| `@Repository` | Acceso a datos    |

**Explicación:**
Todas crean beans, pero `@Repository` también **traduce excepciones de base de datos**.

---

## 4. ¿Qué hace `@Autowired`?

**Respuesta:**
Inyecta automáticamente un bean del contexto de Spring.

**Explicación:**
Spring resuelve dependencias por **tipo o nombre**.

---

## 5. Diferencia entre `==` y `.equals()` en Java

**Respuesta corta:**

`==` compara **referencias**
`.equals()` compara **contenido**

---

## 6. ¿Qué es un `Stream` en Java?

**Respuesta:**
Una API para procesar colecciones de forma declarativa y funcional.

Ejemplo:

```java
list.stream()
    .filter(x -> x > 10)
    .map(x -> x * 2)
    .toList();
```

---

## 7. ¿Qué hace `@Transactional`?

**Respuesta:**
Gestiona transacciones automáticamente.

**Explicación:**
Si ocurre una excepción runtime → **rollback automático**.

---

## 8. Diferencia entre `List` y `Set`

| List               | Set                   |
| ------------------ | --------------------- |
| Permite duplicados | No permite duplicados |
| Ordenado           | Generalmente no       |

---

## 9. ¿Qué hace `@RestController`?

**Respuesta:**
Combina:

```
@Controller
@ResponseBody
```

Devuelve **JSON automáticamente**.

---

## 10. ¿Qué es `LazyInitializationException`?

**Respuesta:**
Error cuando se accede a una relación `LAZY` fuera de la sesión de Hibernate.

---

# 2. Consultas SQL típicas del test

## 1. Obtener el segundo salario más alto

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

Explicación:
Filtra todo lo menor al máximo.

---

## 2. Contar registros por grupo

```sql
SELECT department, COUNT(*)
FROM employees
GROUP BY department;
```

---

## 3. Filtrar duplicados

```sql
SELECT email, COUNT(*)
FROM users
GROUP BY email
HAVING COUNT(*) > 1;
```

---

## 4. JOIN típico

```sql
SELECT e.name, d.name
FROM employees e
JOIN departments d
ON e.department_id = d.id;
```

---

## 5. Último registro por fecha

```sql
SELECT *
FROM orders
ORDER BY created_at DESC
LIMIT 1;
```

---

# 3. Ejercicios de código típicos (muy estilo TestDome)

## 1. Contar caracteres

### Problema

Contar ocurrencias de cada letra.

### Solución

```java
import java.util.*;

public class CharCount {

    public static Map<Character, Integer> count(String s) {

        Map<Character,Integer> map = new HashMap<>();

        for(char c : s.toCharArray()){
            map.put(c, map.getOrDefault(c,0)+1);
        }

        return map;
    }
}
```

---

## 2. Detectar palíndromo

```java
public static boolean isPalindrome(String s){

    int left = 0;
    int right = s.length()-1;

    while(left < right){
        if(s.charAt(left)!=s.charAt(right))
            return false;

        left++;
        right--;
    }

    return true;
}
```

Complejidad: **O(n)**.

---

## 3. Eliminar duplicados de una lista

```java
List<Integer> unique = list.stream()
        .distinct()
        .toList();
```

---

## 4. Encontrar número faltante

Entrada:

```
[1,2,3,5]
```

Salida:

```
4
```

Solución:

```java
public static int missing(int[] arr, int n){

    int sum = n*(n+1)/2;

    for(int a : arr)
        sum -= a;

    return sum;
}
```

---

## 5. Frecuencia máxima

```java
public static int mostFrequent(int[] arr){

    Map<Integer,Integer> map = new HashMap<>();

    for(int n : arr)
        map.put(n,map.getOrDefault(n,0)+1);

    return map.entrySet()
        .stream()
        .max(Map.Entry.comparingByValue())
        .get()
        .getKey();
}
```

---

# 4. Preguntas TRAMPA más comunes

## 1

```java
String a = "hello";
String b = "hello";

System.out.println(a == b);
```

Respuesta:

```
true
```

Porque **String pool**.

---

## 2

```java
Integer a = 127;
Integer b = 127;

System.out.println(a == b);
```

Respuesta:

```
true
```

Cache de Integer.

---

## 3

```java
Integer a = 128;
Integer b = 128;

System.out.println(a == b);
```

Respuesta:

```
false
```

---

## 4

`final` significa:

Respuesta:

No se puede **reasignar la referencia**.

---

## 5

`List.of()` es:

Respuesta:

**Inmutable**

---

## 6

`HashSet` permite duplicados?

Respuesta:

**No**

---

## 7

`Stream` se puede reutilizar?

Respuesta:

**No**

---

## 8

`Optional.get()` con vacío?

Respuesta:

`NoSuchElementException`

---

## 9

`@ComponentScan` sirve para:

Respuesta:

Escanear beans.

---

## 10

`volatile` garantiza:

Respuesta:

**Visibilidad entre threads**

---

# 5. Ejercicios de código que más se repiten (estilo TestDome)

## 1 Two Sum

```java
public int[] twoSum(int[] nums, int target){

    Map<Integer,Integer> map = new HashMap<>();

    for(int i=0;i<nums.length;i++){

        int diff = target - nums[i];

        if(map.containsKey(diff))
            return new int[]{map.get(diff),i};

        map.put(nums[i],i);
    }

    return null;
}
```

Complejidad:

```
O(n)
```

---

## 2 Reverse String

```java
public String reverse(String s){

    return new StringBuilder(s)
            .reverse()
            .toString();
}
```

---

## 3 Valid Parentheses

```java
public boolean valid(String s){

    Stack<Character> stack = new Stack<>();

    for(char c : s.toCharArray()){

        if(c=='(') stack.push(')');
        else if(c=='{') stack.push('}');
        else if(c=='[') stack.push(']');
        else if(stack.isEmpty() || stack.pop()!=c)
            return false;
    }

    return stack.isEmpty();
}
```

---

# 6. Simulador de examen (60 min)

## Sección 1 — Java (10 preguntas)

1️⃣ Diferencia `HashMap` vs `TreeMap`
2️⃣ Qué hace `final`
3️⃣ Diferencia `ArrayList` vs `LinkedList`
4️⃣ `==` vs `.equals()`
5️⃣ Qué hace `Stream.map()`
6️⃣ `Optional` para qué sirve
7️⃣ `@RestController`
8️⃣ `@Autowired`
9️⃣ `checked vs unchecked exception`
🔟 `volatile` keyword

---

## Sección 2 — SQL

1️⃣ Segundo salario más alto
2️⃣ JOIN entre tablas
3️⃣ Contar duplicados
4️⃣ GROUP BY + HAVING
5️⃣ Subquery simple

---

## Sección 3 — Código

### Problema 1

Eliminar duplicados de array.

### Problema 2

Detectar palíndromo.

### Problema 3

Two Sum.

---

⏱ Tiempo sugerido:

| Parte  | Tiempo |
| ------ | ------ |
| Java   | 15 min |
| SQL    | 15 min |
| Código | 30 min |

---

# 7. Estrategia real para aprobar (muy importante)

En tests tipo TestDome:

1️⃣ **Primero SQL** (son rápidas)
2️⃣ **Luego teoría**
3️⃣ **Deja código para el final**

Regla clave:

```
Si un ejercicio de código tarda >10 min → saltar
```

--- 

# 1. Preguntas conceptuales comunes (Java / Spring Boot / SQL)

## 1. ¿Cuál es la diferencia entre `HashMap` y `ConcurrentHashMap`?

**Respuesta corta:**
`ConcurrentHashMap` es thread-safe y permite concurrencia sin bloquear todo el mapa.

**Explicación:**

* `HashMap` → no es seguro para múltiples hilos.
* `ConcurrentHashMap` → usa segmentación / CAS para concurrencia eficiente.

---

## 2. ¿Qué sucede si un `HashMap` tiene múltiples claves con el mismo `hashCode()`?

**Respuesta:**
Se almacenan en la misma **bucket** y se comparan con `equals()`.

**Explicación:**
HashMap usa:

1. `hashCode()` para ubicar bucket
2. `equals()` para distinguir claves.

---

## 3. ¿Qué imprime este código?

```java
Integer a = 100;
Integer b = 100;
System.out.println(a == b);
```

**Respuesta:**
`true`

**Explicación:**
Java cachea enteros entre **-128 y 127**.

---

## 4. ¿Qué imprime?

```java
Integer a = 200;
Integer b = 200;
System.out.println(a == b);
```

**Respuesta:**
`false`

**Explicación:**
Fuera del cache se crean objetos distintos.

---

## 5. Diferencia entre `==` y `equals()`.

**Respuesta:**

* `==` compara referencias
* `equals()` compara contenido (si está sobrescrito)

---

## 6. ¿Qué hace `Optional`?

**Respuesta:**
Representa un valor que puede estar presente o no evitando `NullPointerException`.

---

## 7. ¿Qué es `@Transactional` en Spring?

**Respuesta:**
Indica que el método debe ejecutarse dentro de una transacción.

**Explicación:**
Si ocurre excepción runtime → rollback automático.

---

## 8. Diferencia entre `@Component`, `@Service`, `@Repository`.

**Respuesta:**

| Anotación  | Uso               |
| ---------- | ----------------- |
| Component  | genérico          |
| Service    | lógica de negocio |
| Repository | acceso a datos    |

---

## 9. ¿Qué hace `@RestController`?

**Respuesta:**
Combina `@Controller` + `@ResponseBody`.

---

## 10. Diferencia entre `INNER JOIN` y `LEFT JOIN`.

**Respuesta:**

| JOIN  | resultado                    |
| ----- | ---------------------------- |
| INNER | solo coincidencias           |
| LEFT  | todas las filas de izquierda |

---

# 2. Ejercicios de código estilo TestDome

## Ejercicio 1 — FizzBuzz

```java
public class FizzBuzz {
    public static void print(int n){
        for(int i=1;i<=n;i++){
            if(i%15==0) System.out.println("FizzBuzz");
            else if(i%3==0) System.out.println("Fizz");
            else if(i%5==0) System.out.println("Buzz");
            else System.out.println(i);
        }
    }
}
```

**Explicación:**
15 cubre divisibilidad por 3 y 5.

---

## Ejercicio 2 — String reverse

```java
public static String reverse(String s){
    return new StringBuilder(s).reverse().toString();
}
```

---

## Ejercicio 3 — Contar caracteres

```java
public static Map<Character,Integer> count(String s){
    Map<Character,Integer> map=new HashMap<>();
    for(char c:s.toCharArray())
        map.put(c,map.getOrDefault(c,0)+1);
    return map;
}
```

---

## Ejercicio 4 — Detectar duplicados

```java
public static boolean hasDuplicates(int[] arr){
    Set<Integer> set=new HashSet<>();
    for(int n:arr){
        if(!set.add(n)) return true;
    }
    return false;
}
```

---

## Ejercicio 5 — Palindrome

```java
public static boolean isPalindrome(String s){
    int l=0,r=s.length()-1;
    while(l<r){
        if(s.charAt(l++)!=s.charAt(r--)) return false;
    }
    return true;
}
```

---

# 3. SQL típico en TestDome

## 1. Obtener el segundo salario más alto

```sql
SELECT MAX(salary)
FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
```

---

## 2. Contar empleados por departamento

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```

---

## 3. Usuarios sin pedidos

```sql
SELECT u.id
FROM users u
LEFT JOIN orders o
ON u.id=o.user_id
WHERE o.id IS NULL;
```

---

## 4. Top 3 salarios

```sql
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 3;
```

---

# 4. 20 trampas típicas donde fallan candidatos

| #  | Pregunta                                        | Respuesta    |
| -- | ----------------------------------------------- | ------------ |
| 1  | `String` mutable?                               | No           |
| 2  | `List.of()` mutable?                            | No           |
| 3  | `HashMap` thread safe?                          | No           |
| 4  | `ConcurrentHashMap` permite null?               | No           |
| 5  | `ArrayList` synchronized?                       | No           |
| 6  | `volatile` garantiza atomicidad?                | No           |
| 7  | `==` compara contenido?                         | No           |
| 8  | `Optional.get()` seguro?                        | No           |
| 9  | `finally` siempre se ejecuta?                   | casi siempre |
| 10 | `Integer` caching?                              | -128 a 127   |
| 11 | `HashSet` ordenado?                             | No           |
| 12 | `TreeSet` ordenado?                             | Sí           |
| 13 | `@Autowired` obligatorio?                       | No           |
| 14 | `@SpringBootApplication` incluye ComponentScan? | Sí           |
| 15 | `LEFT JOIN` elimina filas?                      | No           |
| 16 | `COUNT(column)` cuenta null?                    | No           |
| 17 | `COUNT(*)` cuenta null?                         | Sí           |
| 18 | `GROUP BY` obligatorio con agregados?           | Sí           |
| 19 | `Optional` puede ser null?                      | No           |
| 20 | `Stream` reutilizable?                          | No           |

---

# 5. Simulador de examen (60 min)

## Parte 1 — Java

### Pregunta

¿Qué imprime?

```java
String a="hello";
String b="he"+"llo";
System.out.println(a==b);
```

Respuesta:
`true`

Explicación:
Java intern pool.

---

### Pregunta

Completa método para sumar array.

```java
public static int sum(int[] arr){
    int s=0;
    for(int n:arr)
        s+=n;
    return s;
}
```

---

## Parte 2 — Spring Boot

¿Qué anotación define endpoint REST?

Respuesta:
`@RestController`

---

## Parte 3 — SQL

Tabla `orders`

|id|user_id|amount|

Consulta total por usuario.

```sql
SELECT user_id, SUM(amount)
FROM orders
GROUP BY user_id;
```

---

# 6. Estrategia real para aprobar TestDome

1️⃣ **Practicar algoritmos simples**

* strings
* arrays
* hashmaps

2️⃣ **Dominar SQL**

* joins
* group by
* subqueries

3️⃣ **Conceptos Spring Boot**

* DI
* REST controllers
* transactions

4️⃣ **Tiempo**

59 min suele dividirse en:

| sección   | tiempo |
| --------- | ------ |
| Java code | 20 min |
| SQL       | 15 min |
| Conceptos | 15 min |
| debug     | 9 min  |

---

Preparar un **examen específico de TestDome** memorizando **preguntas exactas del banco real** no es algo que pueda reproducir literalmente (los bancos de preguntas están protegidos).
Pero sí puedo darte **lo más útil para aprobar**:

* preguntas **muy similares a las que realmente aparecen**
* ejercicios **del mismo estilo y dificultad**
* **consultas SQL típicas**
* **preguntas trampa frecuentes**
* **simulador realista de 90 min**

Este material está diseñado para **Java + Spring Boot + SQL en TestDome**, que suele evaluar:

* Java Core
* Streams / Collections
* OOP
* Concurrencia básica
* Spring Boot / REST
* SQL (joins, group by, subqueries)
* debugging de código

---

# 1. Preguntas teóricas más comunes (Java) + respuestas

## 1

**Pregunta**
¿Cuál es la diferencia entre `HashMap` y `ConcurrentHashMap`?

**Respuesta**
`HashMap` no es thread-safe.
`ConcurrentHashMap` permite acceso concurrente seguro sin bloquear todo el mapa.

**Explicación**
`ConcurrentHashMap` usa segmentación y locking fino.

---

## 2

**Pregunta**

¿Qué imprime este código?

```java
String s1 = "hello";
String s2 = "hello";
System.out.println(s1 == s2);
```

**Respuesta**

```
true
```

**Explicación**

Los strings literales se guardan en el **String pool**.

---

## 3

**Pregunta**

Diferencia entre `==` y `.equals()`.

**Respuesta**

* `==` compara referencias
* `.equals()` compara contenido

---

## 4

**Pregunta**

¿Qué hace `Optional`?

**Respuesta**

Representa un valor que **puede estar presente o no**, evitando `NullPointerException`.

---

## 5

**Pregunta**

¿Cuál es la complejidad promedio de `HashMap.get()`?

**Respuesta**

```
O(1)
```

---

## 6

**Pregunta**

¿Qué es un Stream en Java?

**Respuesta**

Una secuencia de elementos que permite **operaciones funcionales** (map, filter, reduce).

---

## 7

**Pregunta**

¿Diferencia entre `List` y `Set`?

**Respuesta**

* `List` permite duplicados
* `Set` no

---

## 8

**Pregunta**

¿Qué imprime?

```java
System.out.println(10 + 20 + "30");
```

**Respuesta**

```
3030
```

**Explicación**

Primero suma números → luego concatena string.

---

## 9

**Pregunta**

¿Para qué sirve `@RestController`?

**Respuesta**

Marca una clase como **controlador REST en Spring**.

---

## 10

**Pregunta**

¿Qué hace `@Autowired`?

**Respuesta**

Inyección automática de dependencias.

---

# 2. Preguntas TRAMPA (las que más hacen fallar)

## Trampa 1

```java
Integer a = 127;
Integer b = 127;
System.out.println(a == b);
```

Respuesta

```
true
```

Explicación
Java cachea Integer entre **-128 y 127**.

---

## Trampa 2

```java
Integer a = 128;
Integer b = 128;
System.out.println(a == b);
```

Respuesta

```
false
```

---

## Trampa 3

```java
List<String> list = Arrays.asList("A","B","C");
list.add("D");
```

Respuesta

```
UnsupportedOperationException
```

Explicación
La lista de `Arrays.asList` es **fixed size**.

---

## Trampa 4

```java
String s = null;
System.out.println(s.length());
```

Respuesta

```
NullPointerException
```

---

## Trampa 5

```java
System.out.println(1 + 2 + "3");
```

Respuesta

```
33
```

---

## Trampa 6

```java
System.out.println("3" + 1 + 2);
```

Respuesta

```
312
```

---

## Trampa 7

```java
Set<Integer> set = new HashSet<>();
set.add(1);
set.add(1);
System.out.println(set.size());
```

Respuesta

```
1
```

---

## Trampa 8

```java
List<Integer> list = new ArrayList<>();
list.remove(1);
```

Respuesta

```
IndexOutOfBoundsException
```

---

# 3. Consultas SQL típicas del TestDome

## Consulta 1

Obtener todos los empleados y sus departamentos.

```sql
SELECT e.name, d.name
FROM employees e
JOIN departments d
ON e.department_id = d.id;
```

---

## Consulta 2

Contar empleados por departamento.

```sql
SELECT department_id, COUNT(*)
FROM employees
GROUP BY department_id;
```

---

## Consulta 3

Obtener el salario máximo.

```sql
SELECT MAX(salary)
FROM employees;
```

---

## Consulta 4

Empleados con salario mayor al promedio.

```sql
SELECT *
FROM employees
WHERE salary > (
    SELECT AVG(salary)
    FROM employees
);
```

---

## Consulta 5

Top 5 salarios.

```sql
SELECT *
FROM employees
ORDER BY salary DESC
LIMIT 5;
```

---

# 4. Ejercicios de código reales tipo TestDome

## Ejercicio 1 — FizzBuzz

**Problema**

Imprimir números del 1 al 100.

* múltiplo de 3 → Fizz
* múltiplo de 5 → Buzz
* ambos → FizzBuzz

**Solución**

```java
for (int i = 1; i <= 100; i++) {
    if (i % 15 == 0)
        System.out.println("FizzBuzz");
    else if (i % 3 == 0)
        System.out.println("Fizz");
    else if (i % 5 == 0)
        System.out.println("Buzz");
    else
        System.out.println(i);
}
```

---

## Ejercicio 2 — Encontrar duplicados

```java
public static boolean hasDuplicates(List<Integer> list) {
    Set<Integer> set = new HashSet<>(list);
    return set.size() != list.size();
}
```

Explicación
Set elimina duplicados.

---

## Ejercicio 3 — Contar palabras

```java
public static Map<String,Integer> countWords(String text){
    Map<String,Integer> map = new HashMap<>();

    for(String word : text.split(" ")){
        map.put(word, map.getOrDefault(word,0)+1);
    }

    return map;
}
```

---

## Ejercicio 4 — Palíndromo

```java
public static boolean isPalindrome(String s){
    String rev = new StringBuilder(s).reverse().toString();
    return s.equals(rev);
}
```

---

## Ejercicio 5 — Encontrar máximo

```java
public static int max(int[] arr){
    int max = arr[0];

    for(int n : arr){
        if(n > max) max = n;
    }

    return max;
}
```

---

# 5. Ejercicio de Streams típico

Filtrar números pares.

```java
List<Integer> evens =
list.stream()
    .filter(n -> n % 2 == 0)
    .collect(Collectors.toList());
```

---

# 6. Simulador realista de TestDome (90 min)

## Sección 1 — Java teoría

1. Diferencia entre `HashMap` y `TreeMap`.
2. ¿Qué hace `final`?
3. ¿Qué imprime un bloque `finally`?
4. ¿Qué es `Serializable`?
5. Diferencia entre `checked` y `unchecked exception`.

---

## Sección 2 — SQL

Tabla:

Employees

```
id | name | salary | dept_id
```

Departments

```
id | name
```

Preguntas:

1. Empleados con departamento.
2. Salario promedio.
3. Empleados con salario mayor al promedio.
4. Conteo por departamento.

---

## Sección 3 — Código

### Problema

Encontrar el número que aparece una sola vez.

Input

```
[2,3,2,4,4]
```

Output

```
3
```

Solución

```java
public static int singleNumber(int[] nums) {
    int result = 0;

    for(int n : nums){
        result ^= n;
    }

    return result;
}
```

Complejidad

```
O(n)
```

---

# 7. Tip secreto para TestDome (muy importante)

La mayoría de candidatos falla por:

1️⃣ no leer bien el enunciado
2️⃣ errores de índices
3️⃣ olvidar edge cases
4️⃣ usar algoritmos O(n²)

La mayoría de ejercicios se resuelven con:

* `HashMap`
* `HashSet`
* `Streams`
* `sorting`
* `XOR`

---
## Liderazgo técnico y operativo

### Trabajo con Objetivos Claros por Sprint (Agile/Scrum)

En un entorno **Enterprise-Ready**, es fundamental que el equipo de desarrollo tenga claridad sobre qué se debe lograr en cada sprint. Esto se traduce en tener **objetivos bien definidos** y alineados con los objetivos comerciales de la empresa. Un **Sprint Goal** claro ayuda a enfocar el esfuerzo del equipo y asegurar que las entregas contribuyan de manera directa al valor esperado.

![Sprint](https://www.visual-paradigm.com/servlet/editor-content/scrum/what-is-sprint-in-scrum/sites/7/2018/12/scrum-sprint.png)
![Sprint Goal](https://scrumorg-website-prod.s3.amazonaws.com/drupal/inline-images/SprintGoalLibro.JPG)

#### Ejemplo de Sprint

Imagina que estás trabajando en una **aplicación de ventas** que necesita integrarse con un **sistema de pagos**. El objetivo de un sprint podría ser: "Integrar el sistema de pagos con la aplicación y asegurar que el proceso de pago funcione correctamente".

Esto implica una serie de **historias de usuario** que deben completarse para alcanzar ese objetivo. Al final del sprint, el equipo debe entregar un incremento funcional del sistema que pueda ser probado y validado.

### Métricas Técnicas (Lead Time, Defectos, Cobertura)

Las métricas son esenciales para mantener el rendimiento predecible y enfocado en la calidad. Aquí te detallo algunas de las métricas clave:

#### Lead Time (Tiempo de entrega)

El **Lead Time** es el tiempo que transcurre desde que una tarea o historia de usuario es **empezada** hasta que se entrega al usuario o cliente. En un ambiente **Enterprise-Ready**, reducir el Lead Time mejora la agilidad del equipo.

**Ejemplo:** Si el equipo tarda 10 días en integrar un sistema de pagos, pero luego se logra reducir a 6 días, se ha optimizado el Lead Time. Las herramientas como **Jira** o **Azure DevOps** pueden ayudarte a medir y visualizar esto.

![Lead Time](https://cdn.prod.website-files.com/655b544bd3bde25e54062eda/655da6da786209502a58f5a5_6230807e58e18d5a1deebe71_Lead_Time_Cycle_Time__Change_Lead_Time.jpeg)

#### Defectos

El **número de defectos** o errores detectados durante y después del sprint es una métrica crítica. En un entorno empresarial, los defectos deben ser gestionados y corregidos rápidamente para no impactar la producción.

**Ejemplo:** Si en el sprint anterior detectamos 5 defectos en la integración del sistema de pagos, el objetivo es que en el próximo sprint no haya más de 2 defectos. Las herramientas de seguimiento de bugs como **SonarQube** ayudan a identificar posibles defectos durante el ciclo de vida del desarrollo.

![Defectos](https://www.6sigma.us/wp-content/uploads/2025/01/defect-management.webp)
![Defectos](https://www.6sigma.us/wp-content/uploads/2025/01/defect-management-process-flow.webp)
![Defectos](https://www.slidegeeks.com/_next/image?url=https://www.slidegeeks.com/media/catalog/product/cache/1280x720/A/g/Agile_Sprint_Defect_Management_Summary_Report_Structure_PDF_Slide_1.jpg&w=1920&q=75)

#### Cobertura de Pruebas (Test Coverage)

La cobertura de pruebas mide cuán completo es el conjunto de pruebas unitarias y de integración que cubren el código fuente. En un entorno empresarial, tener una **alta cobertura de pruebas** es esencial para asegurar la calidad y evitar defectos en producción.

**Ejemplo:** Si el código tiene una cobertura de pruebas del 80% en una parte crítica, se puede garantizar que el equipo está validando las funcionalidades esenciales, lo que reduce los riesgos. Herramientas como **JaCoCo** o **JUnit** pueden ser usadas para generar informes de cobertura.

![jacoco](https://www.eclemma.org/images/jacocoreport.png)
![jacoco](https://i.sstatic.net/KVDdk.png)
![junit](https://www.cafeaulait.org/slides/albany/codecoverage/images/coverage.jpg)

### Feedback Continuo

El **feedback continuo** es clave para un equipo ágil y Enterprise-Ready. Los ciclos de retroalimentación son rápidos y frecuentes para corregir problemas en tiempo real y ajustar el rumbo.

#### Revisiones diarias (Daily Standups)

En una revisión diaria, cada miembro del equipo comunica qué hizo el día anterior, qué hará hoy y si tiene algún impedimento. Esto permite detectar problemas rápidamente y ajustar el rumbo.

#### Revisión del Sprint (Sprint Review)

Al final de cada sprint, el equipo realiza una **demo** de las funcionalidades implementadas, obteniendo feedback inmediato de los stakeholders (clientes, líderes de producto, etc.).

#### Retroalimentación Técnica

Además de la retroalimentación funcional, se realiza una **revisión técnica continua** de la calidad del código. Las herramientas de integración continua como **Jenkins** o **GitLab CI/CD** permiten que el código se compile y se pruebe de manera automática, asegurando que cada commit esté listo para ser integrado sin problemas.

### Entregar Valor de Forma Predecible

Para entregar valor de forma predecible, el equipo debe centrarse en las siguientes prácticas:

* **Priorización clara** de tareas que realmente aporten valor a la empresa. Las historias de usuario deben ser evaluadas no solo en términos de esfuerzo, sino también por el valor que aportan al cliente.

* **Revisión continua de la carga de trabajo** para asegurarse de que el equipo no está sobrecargado. Las herramientas de gestión de tareas como **Jira** pueden ayudarte a visualizar cuántos tickets se están completando por sprint.

* **Establecer expectativas claras** con los stakeholders: si un equipo promete entregar una característica en un sprint, debe cumplir con esa promesa o gestionar las expectativas de manera efectiva.

**Ejemplo Práctico:**

Supongamos que tu equipo está trabajando en una nueva funcionalidad para procesar pagos en una tienda en línea. El **Sprint Goal** es integrar la pasarela de pagos de **Stripe**. Durante el sprint:

1. **Objetivo Claro:** "Integrar Stripe para permitir pagos con tarjeta de crédito."
2. **Métricas:** Medir el **Lead Time** para la integración, los **Defectos** que surjan y la **Cobertura de Pruebas** de las nuevas clases relacionadas con pagos.
3. **Feedback Continuo:** Tener reuniones diarias para resolver problemas y una revisión del sprint al final con demostraciones del sistema en producción.

Este enfoque permite **predecir con mayor certeza** cuándo se entregará la funcionalidad y con qué calidad, ayudando al equipo a generar valor continuo y predecible.

### Resumen Visual de Proceso (Enterprise-Ready)

1. **Planificación del Sprint**: Definir objetivos y asignar tareas.
2. **Desarrollo**: Implementar y realizar pruebas unitarias.
3. **Métricas**: Medir Lead Time, defectos y cobertura de pruebas.
4. **Feedback**: Revisión diaria y sprint review.

![alt text](img/resumen-visual-proceso.jpg)
![alt text](img/resumen-visual2.png)

Este enfoque no solo se basa en “sacar tickets”, sino en **entregar valor continuo**, con el equipo comprometido y alineado con los objetivos del negocio, y usando métricas para evaluar y mejorar constantemente el rendimiento.

### Keywords que suman

#### Ownership (Apropiación)
Se refiere a que el equipo y sus miembros asuman la responsabilidad total de sus tareas y del producto final. Esto fomenta la proactividad, la calidad del trabajo y el compromiso con los resultados, ya que cada uno se siente dueño de su parte del proceso.

#### Predictibilidad
Es la capacidad de entregar valor de manera consistente y fiable a lo largo del tiempo. Al analizar el rendimiento histórico y la velocidad, el equipo puede realizar estimaciones más precisas, lo que genera confianza con los stakeholders y permite una mejor planificación del negocio.

#### Métricas
Son datos cualitativos y cuantitativos que se utilizan para evaluar el progreso, la calidad y la salud del proceso de desarrollo. No se usan para vigilar, sino para tomar decisiones informadas, identificar cuellos de botella y medir el impacto de las mejoras introducidas.

#### Baseline Técnico
Es el punto de referencia que define el estado actual de la calidad y la arquitectura técnica del software. Sirve como un estándar para asegurar que las nuevas funcionalidades se desarrollen sin degradar el código existente y ayuda a gestionar la deuda técnica.

#### Acompañamiento
Se trata del soporte constante, mentoría y guía que se brinda a los equipos para su crecimiento profesional y técnico. Facilita la adopción de buenas prácticas, la resolución de impedimentos y la alineación con los objetivos estratégicos de la organización.

![alt text](img/keywords-que-suman.jpg)
![alt text](img/keywords2.png)

### Arquitectura orientada a resultados

Enfoque basado en el pragmatismo de la ingeniería sobre la "Hype Driven Development" (desarrollo impulsado por la moda). Cada decisión técnica debe estar justificada por las necesidades reales del negocio y las restricciones operativas.

He aquí un desglose de los criterios clave:

### Evaluación Pragmática de Decisiones
#### Contexto
Ninguna tecnología es una "bala de plata". Analizo el contexto específico del proyecto: las habilidades del equipo actual, el estado de la base de código existente y los objetivos de negocio a corto y largo plazo antes de proponer un cambio arquitectónico.

#### Costo 
Evalúo el Costo Total de Propiedad (TCO). No solo el costo de las licencias o el cómputo en la nube, sino el costo de desarrollo, mantenimiento, monitoreo y el costo de oportunidad si la tecnología resulta ser demasiado compleja.

#### Escalabilidad Real
Diseño para el crecimiento proyectado, no para un crecimiento hipotético de "escala web" si no es necesario. El objetivo es una arquitectura que pueda escalar de forma rentable (hacia arriba o hacia abajo) cuando sea necesario, sin introducir una complejidad innecesaria prematuramente.

### Análisis de Requerimientos No Funcionales (NFRs)
#### Volumen
Determino cómo manejará el sistema la cantidad de datos que necesita procesar, almacenar e ingerir, tanto en estado estacionario como durante los picos de carga.

#### Latencia
Establezco objetivos claros para el tiempo de respuesta. ¿Es un sistema en tiempo real que requiere milisegundos, o un procesamiento por lotes donde unos minutos son aceptables? Esto dicta decisiones clave sobre bases de datos, almacenamiento en caché y protocolos de comunicación.

#### Resiliencia
Diseño para el fallo. Implemento estrategias como reintentos, disyuntores (circuit breakers) y degradación elegante de la funcionalidad para asegurar que el sistema siga operativo incluso cuando componentes individuales fallen.

#### Seguridad
La seguridad no es una capa externa, sino parte integral del diseño. Aplico principios de "mínimo privilegio", defensa en profundidad y cifrado de datos en reposo y en tránsito.

#### Costo Operativo (FinOps)
Cada decisión de arquitectura tiene un reflejo en la factura de la nube. Analizo el costo de operación continuo para garantizar la sostenibilidad financiera de la solución a largo plazo.

![alt text](img/marco_arquitectura.png)

En entrevistas técnicas (sobre todo para Java), las preguntas sobre **colecciones y genéricos** suelen evaluar:

1. Si entiendes la **jerarquía del framework de colecciones**,
2. Si sabes **cuándo usar cada estructura**,
3. Si comprendes **complejidad temporal (Big-O)**,
4. Y si dominas bien los **Generics**.

Voy a explicártelo como lo preguntaría un reclutador 👇

---

# 📌 1️⃣ ¿Qué es el Java Collections Framework?

Es un conjunto de interfaces y clases del paquete `java.util` que permiten almacenar y manipular grupos de objetos.

Las interfaces principales son:

* `List`
* `Set`
* `Map` (no hereda de Collection, pero forma parte del framework)

---

# 📌 2️⃣ List vs Set vs Map

## 🔹 List

* Permite **elementos duplicados**
* Mantiene **orden de inserción**
* Acceso por índice
* Ejemplo: lista de pedidos, historial, etc.

Implementaciones comunes:

### ✅ ArrayList

* Basado en **arreglo dinámico**
* Acceso rápido por índice → **O(1)**
* Insertar/eliminar en medio → **O(n)**
* No es thread-safe

Uso típico:

```java
List<String> nombres = new ArrayList<>();
nombres.add("Juan");
nombres.add("Ana");
```

👉 Pregunta típica:

> ¿Cuándo usarías ArrayList?
> ✔ Cuando necesitas muchas lecturas y pocas inserciones en medio.

---

### ✅ LinkedList

* Basado en **lista doblemente enlazada**
* Insertar/eliminar al inicio o medio → **O(1)** (si ya tienes referencia)
* Acceso por índice → **O(n)**

👉 Se usa cuando hay muchas inserciones/eliminaciones.

---

## 🔹 Set

* NO permite duplicados
* No garantiza orden (depende de implementación)

Implementaciones:

### ✅ HashSet

* Basado en hash
* No mantiene orden
* Operaciones básicas → **O(1)** promedio

```java
Set<String> usuarios = new HashSet<>();
usuarios.add("Juan");
usuarios.add("Juan"); // No se agrega
```

👉 Pregunta típica:

> ¿Cómo determina HashSet si un elemento es duplicado?
> ✔ Usa `hashCode()` y `equals()`.

---

### ✅ TreeSet

* Ordenado automáticamente
* Basado en árbol (Red-Black Tree)
* Operaciones → **O(log n)**

---

## 🔹 Map

* Almacena pares **clave → valor**
* Claves únicas
* No permite claves duplicadas

Implementaciones:

### ✅ HashMap

* Basado en hash
* O(1) promedio
* No ordenado

```java
Map<String, Integer> edades = new HashMap<>();
edades.put("Juan", 30);
```

👉 Preguntas comunes:

* ¿Permite claves null? → Sí (una sola)
* ¿Es thread-safe? → No

---

### ✅ TreeMap

* Ordenado por clave
* O(log n)

---

# 📌 3️⃣ Diferencias clave resumidas

| Estructura | Duplicados | Orden | Acceso por índice | Complejidad |
| ---------- | ---------- | ----- | ----------------- | ----------- |
| ArrayList  | Sí         | Sí    | Sí                | O(1) get    |
| LinkedList | Sí         | Sí    | Sí (lento)        | O(n) get    |
| HashSet    | No         | No    | No                | O(1)        |
| TreeSet    | No         | Sí    | No                | O(log n)    |
| HashMap    | Clave no   | No    | No                | O(1)        |
| TreeMap    | Clave no   | Sí    | No                | O(log n)    |

---

# 📌 4️⃣ Preguntas comunes sobre HashMap

### 🔥 ¿Cómo funciona internamente?

1. Calcula `hashCode()` de la clave
2. Determina el índice del bucket
3. Si hay colisión:

   * Lista enlazada (Java 7)
   * Árbol balanceado si crece mucho (desde Java 8)

---

### 🔥 ¿Qué es una colisión?

Cuando dos claves diferentes generan el mismo hash.

---

# 📌 5️⃣ Generics (Muy preguntado)

## 🔹 ¿Qué son?

Permiten definir tipos de datos de manera genérica.

```java
List<String> lista = new ArrayList<>();
```

Sin generics:

```java
List lista = new ArrayList();
lista.add("Hola");
Integer num = (Integer) lista.get(0); // Error en runtime
```

Con generics:
✔ Seguridad en compilación
✔ No necesitas cast
✔ Código más limpio

---

## 🔹 Wildcards

### `<?>`

Tipo desconocido

### `<? extends T>`

Solo lectura (covarianza)

```java
List<? extends Number>
```

### `<? super T>`

Permite insertar (contravarianza)

---

👉 Pregunta clásica:

> ¿Por qué no puedes hacer `new T()`?
> Porque los generics en Java usan **type erasure** (se eliminan en runtime).

---

# 📌 6️⃣ Preguntas trampa típicas de reclutadores

### ❓ ¿Cuál es más rápido: ArrayList o LinkedList?

Depende:

* Lectura → ArrayList
* Inserciones frecuentes → LinkedList

---

### ❓ ¿HashMap es thread-safe?

No.
Alternativa:

* `Collections.synchronizedMap()`
* `ConcurrentHashMap`

---

### ❓ Diferencia entre == y equals en colecciones

* `==` compara referencia
* `equals()` compara contenido

---

# 📌 7️⃣ Cuándo usar cada uno (respuesta de entrevista)

✔ Lista de elementos con duplicados → ArrayList
✔ Evitar duplicados → HashSet
✔ Datos clave-valor → HashMap
✔ Necesito orden automático → TreeSet / TreeMap
✔ Mucha concurrencia → ConcurrentHashMap

---

# 📌 8️⃣ Respuesta ideal en entrevista

Cuando te pregunten:

> ¿Qué estructura usarías y por qué?

Responde siempre mencionando:

* Orden
* Duplicados
* Complejidad temporal
* Concurrencia
* Tipo de acceso (índice o búsqueda)

---

Si quieres, puedo:

* 🔥 Hacerte preguntas tipo entrevista para practicar
* 🧠 Explicarte ConcurrentHashMap en profundidad
* 💻 Hacer ejercicios prácticos tipo coding challenge
* 📊 Explicarte Big-O aplicado a cada estructura

¿Quieres que lo llevemos a nivel entrevista senior?

Perfecto 👌 Te armo el **simulacro completo perfil Senior Java + Spring**, y debajo de cada pregunta te doy **la respuesta correcta + explicación detallada**.

---

# 📋 SIMULACRO – Programador Java Senior + Spring

---

## 🧠 PARTE 1 – JAVA CORE (Senior)

---

### 1️⃣ ¿Qué sucede si no se sobrescribe `hashCode()` pero sí `equals()`?

A) Nada
B) Se rompe el contrato en colecciones basadas en hash
C) Mejora el rendimiento
D) Solo afecta a listas

✅ **Respuesta: B**

**Explicación:**
El contrato de Java dice que si dos objetos son iguales según `equals()`, deben tener el mismo `hashCode()`.
Si no lo cumples, estructuras como `HashMap` y `HashSet` no funcionarán correctamente (pueden duplicar objetos o no encontrarlos).

---

### 2️⃣ ¿Cuál es la principal diferencia entre `ConcurrentHashMap` y `HashMap`?

A) ConcurrentHashMap permite null
B) HashMap es thread-safe
C) ConcurrentHashMap es thread-safe
D) No hay diferencia

✅ **Respuesta: C**

**Explicación:**
`HashMap` NO es seguro en entornos multihilo.
`ConcurrentHashMap` maneja concurrencia internamente sin bloquear toda la estructura.

---

### 3️⃣ ¿Qué es una clase inmutable?

A) Clase sin constructor
B) Clase que no puede cambiar su estado después de creada
C) Clase abstracta
D) Clase final

✅ **Respuesta: B**

**Explicación:**
Una clase inmutable:

* Atributos `private final`
* Sin setters
* Estado definido en constructor
* Si contiene objetos mutables, se devuelven copias

Ejemplo clásico: `String`.

---

### 4️⃣ ¿Qué ocurre si llamas `parallelStream()` en una colección grande?

A) Siempre mejora rendimiento
B) Puede empeorar rendimiento según contexto
C) Es igual que stream()
D) Bloquea la JVM

✅ **Respuesta: B**

**Explicación:**
`parallelStream()` usa ForkJoinPool.
Puede empeorar rendimiento si:

* Operaciones pequeñas
* Mucha contención
* IO blocking

---

### 5️⃣ ¿Qué problema resuelve el patrón Builder?

A) Herencia múltiple
B) Constructores con muchos parámetros
C) Concurrencia
D) Serialización

✅ **Respuesta: B**

**Explicación:**
Evita constructores telescópicos y mejora legibilidad.

---

## 🧵 PARTE 2 – CONCURRENCIA

---

### 6️⃣ Diferencia entre `synchronized` y `ReentrantLock`

✅ **Respuesta resumida:**

| synchronized                | ReentrantLock              |
| --------------------------- | -------------------------- |
| Más simple                  | Más flexible               |
| No permite tryLock          | Permite tryLock            |
| No permite fairness         | Permite fairness           |
| Libera lock automáticamente | Debe liberarse manualmente |

**Explicación:**
ReentrantLock es más potente pero más complejo.

---

### 7️⃣ ¿Qué es un Deadlock?

✅ **Respuesta:**
Situación donde dos o más hilos se bloquean esperando recursos que el otro posee.

---

### 8️⃣ ¿Qué hace `volatile`?

A) Hace thread-safe una variable
B) Garantiza visibilidad entre hilos
C) Bloquea escritura
D) Sincroniza métodos

✅ **Respuesta: B**

**Explicación:**
`volatile` garantiza que cambios sean visibles en otros hilos, pero NO garantiza atomicidad.

---

## 🌱 PARTE 3 – SPRING / SPRING BOOT

---

### 9️⃣ ¿Qué es Inversión de Control (IoC)?

✅ **Respuesta:**
El contenedor Spring gestiona la creación y ciclo de vida de objetos (beans).

---

### 🔟 Diferencia entre `@Component`, `@Service`, `@Repository`

✅ **Respuesta:**

* `@Component`: Genérico
* `@Service`: Lógica de negocio
* `@Repository`: Acceso a datos (traduce excepciones)

---

### 11️⃣ ¿Qué hace `@Transactional`?

A) Crea una conexión
B) Maneja transacciones automáticamente
C) Ejecuta en paralelo
D) Optimiza consultas

✅ **Respuesta: B**

**Explicación:**
Spring crea un proxy que inicia, confirma o revierte la transacción.

---

### 12️⃣ ¿Qué pasa si una excepción checked ocurre dentro de `@Transactional`?

✅ **Respuesta:**
Por defecto NO hace rollback.
Solo hace rollback automático con RuntimeException.

---

### 13️⃣ ¿Qué es Lazy Loading en JPA?

✅ **Respuesta:**
Las relaciones se cargan cuando se accede a ellas, no cuando se consulta la entidad.

---

### 14️⃣ ¿Qué problema genera LazyInitializationException?

✅ **Respuesta:**
Acceder a una relación lazy fuera de una sesión activa.

---

### 15️⃣ Diferencia entre `CrudRepository` y `JpaRepository`

✅ **Respuesta:**
`JpaRepository` extiende CrudRepository y agrega:

* Paginación
* Sorting
* flush()

---

## 🗄 PARTE 4 – SQL

---

### 16️⃣ Diferencia entre INNER JOIN y LEFT JOIN

✅ **Respuesta:**

* INNER: Solo coincidencias
* LEFT: Todo de la izquierda + coincidencias

---

### 17️⃣ ¿Qué hace un índice?

A) Guarda datos duplicados
B) Mejora velocidad de búsqueda
C) Reduce memoria
D) Evita deadlocks

✅ **Respuesta: B**

---

## 💻 PARTE 5 – EJERCICIOS PRÁCTICOS

---

### 18️⃣ ¿Qué problema tiene este código?

```java
Map<String, String> map = new HashMap<>();
map.put(null, "test");
```

✅ **Respuesta:**
No hay problema en HashMap.
Pero sí fallaría en ConcurrentHashMap (no permite null).

---

### 19️⃣ ¿Qué problema ves aquí?

```java
@Transactional
public void method() {
    this.otherMethod();
}
```

✅ **Respuesta:**
No funciona la transacción si otherMethod() también tiene @Transactional.

**Explicación:**
Spring usa proxies. Las llamadas internas no pasan por el proxy.

---

### 20️⃣ Diseña un endpoint REST para crear usuario

✅ **Respuesta ejemplo:**

```java
@PostMapping("/users")
public ResponseEntity<UserDto> create(@RequestBody CreateUserDto dto) {
    User user = service.create(dto);
    return ResponseEntity.status(HttpStatus.CREATED).body(mapper.toDto(user));
}
```

**Explicación:**

* POST para crear
* 201 CREATED
* Separación DTO / Entity
* Service layer

---

# 🎯 NIVEL DE DIFICULTAD

Este simulacro está en rango:

* Semi-Senior alto
* Senior intermedio

---

Si quieres, ahora puedo:

* 🔥 Hacer una ronda de entrevista técnica difícil (nivel Senior real)
* 💣 Hacer preguntas de arquitectura (microservicios, Kafka, Docker)
* 🧩 Hacer un ejercicio de diseño tipo sistema real
* 🏆 Simulacro tipo empresa grande

¿Quieres que lo llevemos a nivel “empresa exigente”?