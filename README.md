# Post-Contenido 1 — Refactorización Avanzada y Clean Code Profundo

Proyecto desarrollado para la asignatura **Patrones de Diseño de Software** en la unidad de **Refactorización Avanzada y Clean Code Profundo**.

---

# Objetivo

Identificar y refactorizar code smells de tipo:

- Long Method
- Large Class
- Primitive Obsession
- Data Clump

Aplicando las técnicas:

- Extract Method
- Extract Class
- Introducción de Value Objects

Verificando posteriormente la reducción de complejidad ciclomatica y mejora de mantenibilidad mediante SonarQube.

---

# Tecnologías Utilizadas

- Java 17
- Spring Boot
- Maven
- SonarQube
- Docker
- H2 Database

---

# Code Smells Encontrados

Durante el análisis inicial con SonarQube se detectaron los siguientes problemas:

- Método extremadamente largo (`procesarPedido`)
- Demasiados parámetros primitivos
- Responsabilidades mezcladas en una sola clase
- Inyección en campo (`@Autowired`)
- Alta complejidad ciclomatica
- Lógica de negocio acoplada

---

# Técnicas de Refactorización Aplicadas

## 1. Extract Method

El método `procesarPedido()` fue dividido en métodos pequeños con responsabilidad única:

- `calcularTotal()`
- `aplicarDescuento()`
- `persistirPedido()`

Esto permitió reducir la complejidad ciclomatica y mejorar la legibilidad del código.

---

## 2. Extract Class

La lógica de notificaciones fue extraída a una clase independiente:

```java
NotificacionService
```

Con esto, `PedidoService` dejó de tener múltiples responsabilidades.

---

## 3. Introducción de Value Objects

Se eliminaron grupos de parámetros primitivos creando objetos inmutables:

- `DatosCliente`
- `Direccion`
- `CodigoDescuento`

Esto redujo el problema de Primitive Obsession y Data Clump.

---

# Comparación de Métricas SonarQube

| Métrica | Antes | Después |
|---|---|---|
| Complejidad Ciclomática | Alta | Reducida |
| Code Smells | Muchos | Menos |
| Maintainability | Baja | Mejorada |
| Technical Debt Ratio | Alto | Reducido |

---

# Evidencias

## Dashboard de SonarQube

![SonarQube Dashboard](./docs/sonarqube_dashboard.PNG)

---

## Métricas Antes de la Refactorización

![Métricas Antes](./docs/metricas_antes_refactor.PNG)

---

## Compilación Exitosa Después de la Refactorización

![Compilación Exitosa](./docs/refactor_compile_success.PNG)

---

# Estructura del Proyecto

```plaintext
Cano-post1-u11/
│
├── docs/
│   ├── metricas_antes_refactor.PNG
│   ├── refactor_compile_success.PNG
│   └── sonarqube_dashboard.PNG
│
├── src/
│
├── README.md
│
└── pom.xml
```

---

# Checkpoints Cumplidos

- Proyecto compila correctamente con `mvn compile`
- `DatosCliente` es inmutable
- `procesarPedido()` fue reducido significativamente
- `NotificacionService` fue separado correctamente
- Se redujeron los Code Smells en SonarQube
- Se aplicaron correctamente las técnicas de refactorización
- Se realizaron los commits solicitados
- Se documentaron las mejoras en el README

---

# Commits Realizados

```bash
codigo original con code smells
refactorizacion con extract method class y value objects
analisis final sonarqube y mejoras documentadas
```

---

# Conclusión

La refactorización permitió mejorar significativamente la calidad del código, reduciendo la complejidad ciclomatica y separando responsabilidades. El uso de Value Objects mejoró la mantenibilidad y eliminó el uso excesivo de parámetros primitivos. Gracias a SonarQube fue posible verificar objetivamente las mejoras realizadas en el proyecto.
