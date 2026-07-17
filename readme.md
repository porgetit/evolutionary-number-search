# Genetic Algorithm in C

> Implementación desde cero de un algoritmo genético en lenguaje C, diseñada con fines educativos, experimentales y de investigación.

## Descripción

Este proyecto busca desarrollar un algoritmo genético completamente desde cero, sin depender de bibliotecas externas especializadas.

El objetivo principal no es construir el algoritmo más rápido o sofisticado, sino comprender en profundidad cada uno de los componentes que conforman un algoritmo genético moderno: representación de individuos, evaluación, selección, cruce, mutación y evolución de poblaciones.

Cada decisión de diseño será documentada y justificada para facilitar futuras modificaciones y experimentos.

---

# Objetivos del proyecto

- Implementar un algoritmo genético utilizando únicamente lenguaje C.
- Comprender el funcionamiento interno de cada operador genético.
- Diseñar estructuras de datos eficientes tanto en memoria como en tiempo de ejecución.
- Crear una base flexible que permita resolver diferentes tipos de problemas en el futuro.

Actualmente el primer problema de prueba consiste en encontrar un número natural objetivo.

---

# Estado del proyecto

> **Versión conceptual.**

En esta etapa el proyecto se encuentra en fase de diseño.

Muchas decisiones aún son susceptibles de modificarse conforme se realicen pruebas experimentales.

---

# Representación de los individuos

Cada individuo estará representado mediante un cromosoma binario.

La longitud del cromosoma será la mínima necesaria para representar el número objetivo.

Por ejemplo:

| Objetivo | Bits |
|----------|------|
| 7        | 3    |
| 18       | 5    |
| 255      | 8    |

La intención es evitar desperdiciar memoria almacenando bits que nunca serán utilizados.

Actualmente se estudian diferentes formas de representar estos cromosomas utilizando únicamente tipos estándar de C (`uint8_t`, `uint16_t`, `uint32_t`, etc.) junto con estructuras (`struct`), buscando minimizar el espacio ocupado por grandes poblaciones.

---

# Función de aptitud

La función de aptitud evaluará qué tan cercano se encuentra un individuo respecto al número objetivo.

Aún no se ha definido una fórmula definitiva, pero el criterio general será:

- cuanto menor sea la diferencia respecto al objetivo,
- mayor será la aptitud del individuo.

---

# Selección

La estrategia de selección elegida es **selección por truncamiento**.

Cada generación:

1. Se ordena la población según su aptitud.
2. Se conserva únicamente el 25 % de los mejores individuos.
3. Dichos individuos serán utilizados para generar la siguiente generación.

---

# Cruce

Los individuos seleccionados no serán emparejados aleatoriamente.

Después de ordenar la población por aptitud, las parejas se formarán mediante una simetría respecto al centro de la lista.

Ejemplo:

```
1°  ↔ último
2°  ↔ penúltimo
3°  ↔ antepenúltimo
...
```

El propósito de esta estrategia es combinar individuos muy aptos con otros relativamente menos aptos, intentando mantener diversidad genética dentro de la población.

---

# Mutación

Cada nuevo individuo podrá sufrir una mutación puntual.

Inicialmente se contempla una mutación de un único bit del cromosoma.

La probabilidad de mutación aún está pendiente de definirse experimentalmente.

---

# Diversidad genética

Además de los operadores clásicos, se contempla introducir periódicamente individuos completamente nuevos dentro de la población.

La finalidad es evitar convergencias prematuras y mantener una adecuada exploración del espacio de búsqueda.

La estrategia exacta de reinicialización aún se encuentra en estudio.

---

# Filosofía del proyecto

Este proyecto prioriza:

- comprensión antes que rendimiento;
- simplicidad antes que optimización prematura;
- documentación antes que complejidad.

Cada componente será implementado manualmente para comprender su funcionamiento interno antes de considerar mejoras o técnicas avanzadas.

---

# Trabajo futuro

Entre las tareas previstas se encuentran:

- Definir la representación definitiva del cromosoma.
- Diseñar la función de aptitud.
- Implementar operadores genéticos.
- Diseñar estructuras de memoria eficientes.
- Experimentar con distintos métodos de selección.
- Ajustar probabilidades de mutación y cruce.
- Incorporar nuevos problemas de optimización.
- Medir rendimiento y convergencia.

---

# Licencia

Pendiente.
