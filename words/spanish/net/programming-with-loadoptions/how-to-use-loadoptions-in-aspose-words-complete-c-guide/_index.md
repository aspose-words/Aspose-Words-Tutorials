---
category: general
date: 2026-04-10
description: Cómo usar LoadOptions en Aspose.Words para capturar advertencias de sustitución
  de fuentes al cargar documentos. Aprende una solución paso a paso en C# con un ejemplo
  de código completo.
draft: false
keywords:
- how to use loadoptions
- warningcallback
- font substitution warning
- aspose.words loadoptions example
- c# document loading
language: es
og_description: Cómo usar LoadOptions en Aspose.Words para capturar advertencias de
  sustitución de fuentes al cargar documentos. Esta guía le guía a través de una implementación
  completa en C#.
og_title: Cómo usar LoadOptions en Aspose.Words – Guía completa de C#
tags:
- Aspose.Words
- C#
- Document Processing
- Font Management
title: Cómo usar LoadOptions en Aspose.Words – Guía completa de C#
url: /es/net/programming-with-loadoptions/how-to-use-loadoptions-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo usar LoadOptions en Aspose.Words – Guía completa en C#

Cómo usar LoadOptions en Aspose.Words es un obstáculo frecuente cuando necesitas un control estricto sobre la carga de documentos. En este tutorial te mostraremos exactamente **cómo usar LoadOptions** para capturar advertencias de sustitución de fuentes y reaccionar a ellas en C#.  

Si alguna vez has abierto un DOCX que hacía referencia a una fuente que falta y te has preguntado por qué el resultado se ve extraño, estás en el lugar correcto. Recorreremos todo el proceso, desde crear una instancia de `LoadOptions` hasta imprimir los detalles de la advertencia en la consola. Al final tendrás un fragmento listo‑para‑ejecutar que podrás insertar en cualquier proyecto .NET.

## Qué aprenderás

- Por qué `LoadOptions` es importante para importaciones de documentos fiables.  
- Cómo conectar un **WarningCallback** que vigile específicamente las **advertencias de sustitución de fuentes**.  
- El código exacto necesario para cargar un archivo Word con estas opciones habilitadas.  
- Consejos para manejar casos límite, como documentos que contienen varias fuentes faltantes.  

No se requiere documentación externa—todo lo que necesitas está aquí.

## Requisitos previos

| Requisito | Razón |
|-----------|-------|
| .NET 6.0 o posterior | Proporciona el runtime para la sintaxis C# 10 usada en los ejemplos. |
| Aspose.Words for .NET (última versión) | La biblioteca que incluye `LoadOptions` y la infraestructura de advertencias. |
| Un archivo DOCX que pueda referenciar fuentes que no tienes instaladas | Para ver el callback de advertencias en acción. |
| Visual Studio 2022 (o cualquier IDE que prefieras) | Facilita la depuración y las pruebas. |

Si ya cuentas con esto, genial—¡vamos al grano!

## Paso 1 – Crear un objeto LoadOptions y conectar el WarningCallback

Lo primero que haces cuando **cómo usar LoadOptions** es instanciarlo. La parte crucial es asignar un delegado a `WarningCallback`. Este delegado se dispara cada vez que Aspose.Words encuentra una situación que quiere informarte—principalmente, una fuente faltante.

```csharp
using System;
using Aspose.Words;

// Step 1: Build LoadOptions with a warning listener.
LoadOptions loadOptions = new LoadOptions
{
    // The lambda receives the sender (unused) and a WarningInfo object.
    WarningCallback = (sender, args) =>
    {
        // We'll filter for font‑substitution warnings later.
        if (args.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        }
    }
};
```

**Por qué es importante:** Sin el callback, Aspose.Words sustituye silenciosamente las fuentes faltantes por predeterminadas, y puede que nunca notes el cambio visual. Al registrar un `WarningCallback`, obtienes un registro en tiempo real de cada sustitución, lo cual es esencial para pipelines de documentos con garantía de calidad.

## Paso 2 – Reaccionar solo a las advertencias de sustitución de fuentes

Quizás te preguntes si el callback te inundará con advertencias no relacionadas (como características obsoletas). La respuesta es *sí*—pero podemos filtrarlas. En el fragmento anterior ya verificamos `args.WarningType == WarningType.FontSubstitution`. Esa línea es la **guardia de advertencia de sustitución de fuentes**, una palabra clave secundaria que mantiene la salida enfocada.

Si alguna vez necesitas manejar otros tipos de advertencia, simplemente amplía el bloque `if`:

```csharp
if (args.WarningType == WarningType.FontSubstitution)
{
    // Existing handling…
}
else if (args.WarningType == WarningType.UnknownFileFormat)
{
    Console.WriteLine($"❓ Unknown format: {args.Description}");
}
```

Este patrón muestra cuán flexible es el mecanismo **warningcallback**, permitiéndote adaptar respuestas exactamente a los escenarios que te importan.

## Paso 3 – Cargar tu documento usando el LoadOptions configurado

Ahora que el listener está listo, la pieza final es pasar la instancia de `LoadOptions` al constructor de `Document`. Este es el momento en que el **ejemplo de Aspose.Words LoadOptions** realmente brilla.

```csharp
// Step 3: Load the DOCX while the warning callback is active.
try
{
    Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
    Console.WriteLine("✅ Document loaded successfully.");
}
catch (Exception ex)
{
    Console.WriteLine($"🚨 Failed to load document: {ex.Message}");
}
```

**Lo que verás:** Si el DOCX hace referencia a una fuente que no está instalada en la máquina, la consola mostrará una línea como:

```
⚠️ Font substitution: Font 'Calibri Light' has been substituted with 'Arial'.
✅ Document loaded successfully.
```

Esa salida confirma que has usado con éxito **cómo usar LoadOptions** para monitorizar problemas de fuentes.

## Ejemplo completo (listo para copiar y pegar)

A continuación tienes el programa completo que puedes compilar y ejecutar de inmediato. Reúne los tres pasos, agrega un par de detalles (como un banner amigable) y demuestra el manejo de errores.

```csharp
using System;
using Aspose.Words;

class Program
{
    static void Main()
    {
        Console.WriteLine("=== Aspose.Words LoadOptions Demo ===");

        // 1️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = (sender, args) =>
            {
                if (args.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"⚠️ Font substitution: {args.Description}");
                }
            }
        };

        // 2️⃣ Attempt to load the document.
        try
        {
            // Replace the path with your own file that may contain missing fonts.
            Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
            Console.WriteLine("✅ Document loaded without fatal errors.");

            // Optional: Do something with the document, e.g., save as PDF.
            // doc.Save("output.pdf");
        }
        catch (Exception e)
        {
            Console.WriteLine($"🚨 Error: {e.Message}");
        }

        Console.WriteLine("=== End of Demo ===");
    }
}
```

### Salida esperada

Ejecutar el programa en una máquina que carezca de una fuente referenciada en `input.docx` produce algo similar a:

```
=== Aspose.Words LoadOptions Demo ===
⚠️ Font substitution: Font 'Times New Roman' has been substituted with 'Arial'.
✅ Document loaded without fatal errors.
=== End of Demo ===
```

Si todas las fuentes están presentes, solo verás los mensajes de éxito—no aparecerán líneas de advertencia.

## Errores comunes y consejos profesionales

- **Error:** Olvidar establecer `WarningCallback`. El código seguirá cargando, pero perderás los detalles de sustitución.  
  **Consejo:** Asigna siempre el callback justo después de crear `LoadOptions`; es barato y paga dividendos más adelante.

- **Error:** Usar una ruta relativa que apunte a la carpeta equivocada.  
  **Consejo:** Utiliza `Path.Combine(Environment.CurrentDirectory, "input.docx")` para una búsqueda de archivo más robusta.

- **Error:** Suponer que la advertencia detendrá la carga.  
  **Consejo:** Las advertencias de sustitución de fuentes son *informativas*; no abortan la carga. Si necesitas una validación más estricta, lanza una excepción dentro del callback cuando ocurra una sustitución.

- **Error:** Ejecutar en un servidor sin fuentes instaladas (p. ej., una imagen Docker mínima).  
  **Consejo:** Pre‑instala las fuentes requeridas o inclúyelas con tu aplicación, y verifica con el callback que no haya sustituciones en producción.

## Cuándo usar LoadOptions vs. inspección posterior a la carga

Podrías preguntar, “¿Por qué no inspeccionar el documento después de cargarlo?” La respuesta está en rendimiento y corrección. Al manejar advertencias **durante** la carga, capturas problemas temprano—antes de que se realicen cálculos de diseño o conversiones a PDF. Esto es especialmente valioso en pipelines de procesamiento por lotes donde cada paso adicional suma tiempo.

## Extensión del ejemplo: guardar un informe de todas las fuentes sustituidas

Si necesitas un registro permanente (quizá por cumplimiento), modifica el callback para recopilar los mensajes en una lista y escribirlos en un archivo después de la carga:

```csharp
var substitutions = new List<string>();

loadOptions.WarningCallback = (s, a) =>
{
    if (a.WarningType == WarningType.FontSubstitution)
    {
        substitutions.Add(a.Description);
        Console.WriteLine($"⚠️ {a.Description}");
    }
};

// After loading:
File.WriteAllLines("font-substitutions.txt", substitutions);
```

Ahora tienes tanto retroalimentación en consola como un log duradero.

## Temas relacionados que podrías explorar a continuación

- **Cómo incrustar fuentes personalizadas en Aspose.Words** – elimina la sustitución por completo.  
- **Usar LoadOptions para limitar el tamaño del documento** – ayuda a proteger contra archivos maliciosamente grandes.  
- **Convertir Word a PDF con tipografía preservada** – combina muy bien con el enfoque de warning‑callback.  

Cada uno de estos se basa en la base que acabas de establecer con `LoadOptions`.

## Conclusión

Hemos cubierto **cómo usar LoadOptions** en Aspose.Words de principio a fin: crear las opciones, conectar un `WarningCallback` que se centre en **advertencias de sustitución de fuentes**, y cargar un documento con confianza. El ejemplo completo funciona out‑of‑the‑box, y los consejos adicionales te ayudarán a evitar trampas comunes.  

Siéntete libre de experimentar—cambia el callback por otros tipos de advertencia, registra en una base de datos, o integra la lógica en un servicio web que valide archivos Word subidos. El patrón es flexible, fiable y, lo más importante, te brinda visibilidad sobre el proceso oculto de sustitución de fuentes que de otro modo podría arruinar la renderización de tus documentos.

¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como deseas!

![Diagram showing the flow of using LoadOptions with a warning callback in Aspose.Words](https://example.com/images/loadoptions-flow.png "How to use LoadOptions diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}