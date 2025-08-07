# Implementación del Algoritmo Tornado-Optimizer con Optimización de Fuerza de Coriolis (TOC) para el Problema de Localización de Hubs

Este proyecto implementa el algoritmo Tornado-Optimizer con Optimización de Fuerza de Coriolis (TOC) para resolver un problema de optimización de asignación de clientes a hubs. El objetivo es minimizar el costo total, que incluye las distancias entre clientes y hubs asignados, así como los costos fijos de los hubs utilizados, respetando las capacidades de los hubs y una distancia máxima permitida.

El código presenta la aplicación del algoritmo a diferentes instancias del problema, variando el número de clientes y hubs, así como sus parámetros asociados.

## Contenido del Repositorio (Notebook)

El notebook de Google Colab contiene las siguientes secciones:

1.  **Instancia Baja**: Implementación y ejecución del algoritmo TOC para un problema con un número reducido de clientes y hubs.
2.  **Instancia Media**: Implementación y ejecución del algoritmo TOC para un problema con un número moderado de clientes y hubs.
3.  **Instancia Alta**: Implementación y ejecución del algoritmo TOC para un problema con un número elevado de clientes y hubs.
4.  **MiniZinc**: Resolución del problema para las instancias Baja y Media utilizando el lenguaje de modelado de optimización MiniZinc (requiere archivos `.mzn` y `.dzn` externos).
5.  **Solución Heurística en Python (Backup)**: Una implementación simple de una heurística voraz como método de respaldo para resolver el problema.

## Algoritmo Tornado-Optimizer con Optimización de Fuerza de Coriolis (TOC)

El algoritmo TOC es un metaheurística de optimización basada en la simulación de fenómenos naturales, específicamente tornados y la fuerza de Coriolis. La implementación en este código incluye:

-   **Representación de la Solución**: Cada solución (individuo) se representa como un arreglo donde el índice corresponde a un cliente y el valor al hub asignado.
-   **Función de Evaluación (`evaluar`)**: Calcula el costo total de una solución, penalizando las asignaciones infactibles (fuera de `D_MAX` o excediendo la capacidad del hub).
-   **Inicialización de Población (`init_population`)**: Genera una población inicial de soluciones factibles.
-   **Operadores de Búsqueda**: El algoritmo utiliza movimientos inspirados en tornados, tormentas eléctricas (thunderstorms) y vendavales (windstorms) para explorar el espacio de soluciones y mejorar la población a lo largo de iteraciones (`toc_optimizer`).
-   **Manejo de Restricciones**: Las restricciones de distancia máxima y capacidad de los hubs se manejan dentro de la función de evaluación y durante la generación y mejora de soluciones para asegurar la factibilidad.

## MiniZinc

La sección de MiniZinc demuestra cómo modelar y resolver el problema de localización de hubs utilizando un solver exacto o de programación con restricciones. Requiere tener el modelo (`.mzn`) y los archivos de datos específicos de cada instancia (`.dzn`) disponibles.

## Heurística de Respaldo

La heurística de respaldo implementada es un enfoque simple y rápido que asigna clientes a hubs basándose en un criterio de costo y disponibilidad, sin garantizar la optimalidad de la solución.

## Cómo Ejecutar el Código

1.  Abre el notebook en Google Colab.
2.  Ejecuta cada celda de código en orden.
3.  Para la sección de MiniZinc, asegúrate de tener los archivos `modelo_hubs.mzn`, `instancia_baja.dzn` e `instancia_media.dzn` (y opcionalmente para la instancia Alta) subidos a tu entorno de Colab o accesibles (por ejemplo, desde Google Drive).
4.  Observa las salidas para ver los resultados del algoritmo TOC en las diferentes instancias, así como los resultados de MiniZinc y la heurística.

## Resultados Reportados

El notebook imprime estadísticas detalladas para las 30 corridas del algoritmo TOC en cada instancia, incluyendo el mejor, peor, promedio, mediana y desviación estándar del costo total, así como métricas de tiempo de ejecución. También muestra la mejor solución encontrada por el TOC y verifica su factibilidad. Los resultados de MiniZinc y la heurística también se muestran para comparación.

## Posibles Mejoras

-   Implementar operadores de mutación o cruce adicionales para el algoritmo TOC.
-   Comparar el rendimiento del algoritmo TOC con otras metaheurísticas.
-   Desarrollar instancias de problema más grandes y complejas.
-   Mejorar la heurística de respaldo.
-   Automatizar la generación de archivos `.dzn` para MiniZinc a partir de los datos de las instancias en Python.
