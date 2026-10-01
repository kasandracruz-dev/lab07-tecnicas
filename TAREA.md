# Tarea: Mi prompt avanzado 

## Tarea elegida

* **Tarea de software seleccionada:** Diseñar la arquitectura de clases y la estructura del dominio para un Sistema de Gestión de Notas Académicas.
* **Objetivo:** Generar un diseño UML conceptual en PlantUML, la definición de entidades en código (C# / .NET) y los casos de uso principales.

## Version 1: prompt basico 

```text
Crea las clases para un sistema de gestión de notas académicas.
```
|Técnica agregada | Por qué se uso y que mejoró|
|-----------------|----------------------------|
|Ninguna(prompt basico) |La respuesta devuelta por el modelo fue demasiado genérica, sin formato estructurado, omitiendo reglas de negocio clave como el cálculo de promedios ponderados o restricciones de estado (aprobado/desaprobado)| 

## Version 2

```text
Actúa como un Arquiteto de Software especializado en sistemas edtech y DDD (Domain-Driven Design). 
Diseña las clases para un sistema de gestión de notas académicas.
Estructura tu respuesta con las siguientes secciones obligatorias:
1. Diagrama de Clases (en formato Markdown).
2. Código C# de las Entidades Principales.
3. Reglas de Negocio Implementadas.
```
|Técnica agregada | Por qué se uso y que mejoró|
|-----------------|----------------------------|
|Role Prompting + Prompt Estructurado |Para guiar al modelo a asumir una perspectiva profesional precisa y forzar un formato estandarizado que garantice legibilidad. La respuesta incluyó explicaciones más profesionales y organizadas en secciones explícitas, pero aún faltaban detalles paso a paso en el razonamiento del modelo y ejemplos concretos de las reglas de cálculo.|

## Version 3: prompt final

```text
Actúa como un Arquitecto de Software Principal especializado en Domain-Driven Design (DDD) y sistemas de educación superior.

Tu objetivo es diseñar la capa de dominio para un Sistema de Gestión de Notas Académicas.

### Instrucciones de Razonamiento (Chain of Thought)
Antes de generar la solución final, piensa paso a paso analizando los siguientes puntos:
1. Identifica los Agregados, Entidades y Objetos de Valor (Value Objects).
2. Analiza las reglas de cálculo (ej. promedio ponderado, peso de evaluaciones).
3. Diseña las relaciones de cardinalidad entre Estudiante, Curso, Matricula y Evaluacion.

### Ejemplo de Referencia (Few-Shot)
Ejemplo de cómo debes modelar un Value Object de Nota:
```csharp
public readonly record struct Nota
{
    public decimal Valor { get; }
    public Nota(decimal valor)
    {
        if (valor < 0 || valor > 20) 
            throw new ArgumentOutOfRangeException("La nota debe estar entre 0 y 20.");
        Valor = valor;
    }
}
```

|Técnica agregada | Por qué se uso y que mejoró|
|-----------------|----------------------------|
|Chain of Thought (CoT) + Few-Shot Prompting|CoT obliga al modelo a descomponer la lógica de dominio antes de programar, y Few-Shot le da un ejemplo claro de la calidad del código esperada. El modelo produjo un análisis de diseño explícito, código con patrones DDD reales y un diagrama válido sin saltarse pasos lógicos|
## Tecnicas usadas en el prompt final 

| Parte del Prompt Final | Técnica Aplicada |
| :--- | :--- |
| `Actúa como un Arquitecto de Software Principal especializado en...` | **Role Prompting** |
| `### Instrucciones de Razonamiento (Chain of Thought)...` | **Chain of Thought (CoT)** |
| `### Ejemplo de Referencia (Few-Shot)...` | **Few-Shot Prompting** |
| `### Formato de Salida Requerido...` | **Prompt Estructurado** |


## Evaluacion del resultado

| Criterio de Evaluación | Resultado (Sí / No) | Observaciones |
| :--- | :---: | :--- |
| ¿El rol asignado delimitó adecuadamente el estilo y calidad de la respuesta? | Sí | Mantuvo un enfoque técnico avanzado en DDD. |
| ¿El formato de salida cumplió exactamente con las secciones solicitadas? | Sí | Entregó exactamente los 4 bloques especificados. |
| ¿El diagrama y el código generados fueron válidos y sin errores? | Sí | El diagrama PlantUML y el código compilan correctamente. |
| ¿Se incluyeron reglas de negocio como validación de rangos? | Sí | Se garantizó la validación de notas dentro del rango permitido. |

## Por que elegi estas tecnicas

Elegí **Role Prompting**, **Chain of Thought**, **Few-Shot** y **Prompt Estructurado** porque el diseño de software exige tanto rigor conceptual como precisión técnica. El rol establece el nivel de exigencia arquitectónica; *Chain of Thought* evita errores lógicos al forzar al modelo a analizar antes de escribir; *Few-Shot* sirve como estándar de código limpio para evitar tipos genéricos; y el *Prompt Estructurado* garantiza un documento final limpio, claro y fácil de auditar.

