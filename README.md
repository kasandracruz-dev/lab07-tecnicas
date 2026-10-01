# Bitacora de tecnicas avanzadas

Laboratorio 07: Tecnicas Avanzadas de Prompting. 
Herramienta de IA usada: Gemini

- [Bitacora de tecnicas avanzadas](prompts/BITACORA.md)

##	Ejercicio	2:	Zero-shot, one-shot y few-shot

| Tipo | Aciertos (de 5) | Formato de la respuesta | Todas con el mismo formato (Si/No) |
|------|-----------------|-------------------------|----------------------------|
| Zero-shot|   5        |Libre | Si|
| One-shot |   5        |Libre| Si|
| Few-shot |   5       |texto -> etiqueta | Si|

##	Ejercicio	3:	Chain of Thought

| Pedido | Respuesta de la IA | Muestra los pasos (Si/No) | Correcta (Si/No) |
|--------|--------------------|---------------------------|------------------|
| Directo |318.6 |Si|Si |
| Paso a paso |318.60 |Si |Si |

- Ver el razonamiento sirve para verificar que los calculos fueron los correctos y confirmar que el resultado final es el indicado.

##	Ejercicio	4:	Role prompting

| Version | Vocabulario (sencillo/tecnico) | Usa ejemplos o codigo | A quien le sirve mas |
|---------|--------------------------------|-----------------------|----------------------|
| A. Sin rol |Sencillo|Si |Personas que empiezan recien en programacion |
| B. Rol docente |Sencillo |Si |Personas que empiezan recien en programacion |
| C. Rol senior |Tecnico|Si|Personas mas experimentadas en el campo de programacion |

##	Ejercicio	5:	Descomposicion

| Paso | Mensaje| Resultado|
|------|--------|----------|
|1     |Voy a crear un sistema de inventario para una tienda pequena en Java. Lista los 5 requisitos principales del sistema| Definición de los 5 requisitos funcionales clave para una tienda pequeña en Java|
|2     |Con esos requisitos, disena las clases necesarias. Para cada clase indica sus atributos con su tipo de dato|Definición de los 5 requisitos funcionales clave para una tienda pequeña en Java.|Diseño conceptual en POO con las clases, atributos y tipos de datos requeridos en Java|
|3     |Escribe el codigo Java de la clase Producto con sus atributos, un constructor y los metodos get y set|Código fuente en Java de la clase Producto con sus atributos, constructor y métodos getter/setter|
|4     |Revisa el codigo de la clase Producto y propone 3 mejoras concretas|Propuesta de 3 mejoras técnico-prácticas (BigDecimal, validaciones y equals/hashCode) con código refactorizado|

- La respuesta que me dieron con mi primer prompt fue basica en Python/SQL, mientras que el resultado con los 5 prompt genero una evolución de esa idea hacia un modelo Java más robusto gracias al refinamiento que fui pidiendo.

##	Ejercicio	6:	Prompt estructurado y autocritica

| Qué revisar | Cumple (Sí / No)| 
|-------------|-----------------|
|¿Tiene las 4 columnas pedidas?|Si|
|¿Incluye el bloqueo después de 3 intentos?| Si|
|¿Incluye casos con campos vacíos?| Si|
|¿Indica qué casos agregó en la autocrítica?| Si|
|¿Hay algún caso repetido o que no tenga sentido?|Si|

```text
* PROMPT ESTRUCTURADO

<rol>Actua como analistade pruebas de software.</rol>

<contexto>Login web con correo y contrasena. La cuenta se bloquea

despues de 3 intentos fallidos.</contexto>

<tarea>Piensa paso a paso que puede fallary escribe 6 casos de prueba.</tarea>

<formato>Tabla con las columnas:ID, escenario, datos de entrada, resultado

esperado.</formato>

* MENSAJE DE AUTOCRITICA

Revisa tu tabla: faltan casos limite como campos vacios,correo sin @

o contrasena con espacios? Agrega los que falten e indica cuales agregaste.

```
