# Guion breve para exposición · APIAQ

## 1. Portada
Presentar el nombre del proyecto y al equipo. Explicar en una frase que APIAQ transforma datos abiertos de calidad del aire en información más fácil de interpretar.

## 2. Ruta del proyecto
Contar que no se empezó programando: primero se definió el problema, luego el diseño, Scrum, desarrollo en Python, pruebas y cierre. Resaltar 8 sprints, 40 actividades y 52 pruebas automatizadas.

## 3. Problema y objetivo
Explicar que OpenAQ entrega datos técnicos: estaciones, unidades, periodos y fechas. El objetivo fue construir una experiencia web que organice y contextualice esos datos sin inventar información.

## 4. ODS
Relacionar el proyecto principalmente con ODS 3 y 11. Para ODS 13 aclarar que la contribución es complementaria por el uso de datos ambientales y cultura de monitoreo.

## 5. Arquitectura
Seguir la flecha: Angular envía la consulta al backend Flask. Python trabaja con dos fuentes externas: OpenAQ y, en la actualización final, Open-Meteo Air Quality. Después valida y procesa la información, guarda en SQLite y genera reportes. La clave de OpenAQ nunca llega al navegador.

## 6. Scrum
Explicar los ocho sprints y la lógica de cada etapa. Señalar que seis informes fueron cargados al aula porque eran los solicitados, pero Jira registra los ocho sprints completos.

## 7. UML y diseño
Mostrar que los diagramas guiaron la implementación: qué hace el usuario, qué clases existen, qué pasos sigue una consulta y cómo se comunican los componentes.

## 8. Del mockup al producto
Comparar la idea inicial con la interfaz final. Resaltar que el diseño se mantuvo, pero el producto agregó conexión real, historial, errores y administración.

## 9. Python en el proyecto
Esta es una diapositiva clave. Decir que Python no es una parte secundaria: es el motor de la lógica. Flask, requests, SQLite, pandas, Matplotlib y pytest se ejecutan en Python.

## 10. main.py
Explicar que este archivo coordina el backend. Mostrar cómo recibe JSON, valida la ciudad, llama la lógica de consulta, guarda el historial y devuelve JSON. Mencionar decoradores Flask.

## 11. Cliente OpenAQ
Explicar la clase ClienteOpenAQ. Mostrar que maneja headers, API key, GET, timeout, paginación y excepciones. Resaltar `try/except` y la excepción propia `ErrorOpenAQ`.

## 12. Open-Meteo y ciudades habilitadas
Explicar que en la actualización final se añadió Open-Meteo Air Quality como fuente complementaria basada en coordenadas. Mostrar el diccionario `COORDENADAS`: cada nombre de ciudad es una clave y cada valor es una tupla `(latitud, longitud)`. Las diez ciudades habilitadas son Bogotá, Medellín, Cali, Barranquilla, Cartagena, Bucaramanga, Pereira, Cúcuta, Santa Marta y Manizales. La idea clave es: ciudad → coordenadas → petición HTTP → JSON → procesamiento en Python.

## 13. Normalización
Explicar que antes de calcular cualquier cosa se verifica que los datos tengan valor, contaminante, unidad, fecha, estación y fuente. Se eliminan duplicados con `set()`.

## 14. AQI EPA
Mostrar la interpolación y explicar que el algoritmo busca el breakpoint correcto. Recalcar que no se convierte una unidad cuando no existe compatibilidad válida.

## 15. OMS
Aclarar que OMS no es un segundo AQI. `comparar_medicion()` revisa periodo y unidad, y `comparar_oms()` selecciona una comparación principal para el usuario.

## 16. Persistencia
Explicar SQLite, `with` para la conexión, SQL parametrizado, filtros y construcción del CSV con `csv.DictWriter`.

## 17. pandas + Matplotlib
Explicar DataFrame, conversión de tipos, groupby, mean/min/max y generación de PNG. Resaltar que los huecos no se rellenan artificialmente.

## 18. Pruebas
Explicar que hay 52 funciones de prueba distribuidas en 11 archivos. Mencionar ejemplos: AQI, OpenAQ, historial, normalización, API Flask y reportes.

## 19. Producto final
Hacer una demostración breve del flujo: ciudad → estación → consultar → mediciones → AQI/OMS → historial → gráfica.

## 20. Evidencias
Mostrar Jira, GitHub, VS Code y Meet para demostrar que hubo trazabilidad del proceso y trabajo colaborativo.

## 21. Repositorios
Mostrar backend y frontend. Explicar cómo levantar ambos servicios en localhost y por qué están separados.

## 22. Aprendizajes y cierre
Cerrar diciendo que el proyecto permitió aplicar Python de forma completa: servicios web, validación, reglas de negocio, datos, persistencia, análisis, pruebas e integración con un frontend real.
