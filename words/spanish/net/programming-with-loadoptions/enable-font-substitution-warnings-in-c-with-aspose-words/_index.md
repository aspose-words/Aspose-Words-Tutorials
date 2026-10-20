---
category: general
date: 2026-06-20
description: Habilite las advertencias de sustitución de fuentes en C# usando Aspose.Words.
  Aprenda cómo configurar LoadOptions, capturar advertencias y manejar fuentes faltantes
  de manera eficiente.
draft: false
keywords:
- enable font substitution warnings
- Aspose.Words LoadOptions
- C# font substitution warnings
- document warning handling
- font substitution messages
language: es
og_description: Habilita advertencias de sustitución de fuentes en C# con Aspose.Words.
  Esta guía te muestra cómo configurar LoadOptions, leer WarningInfo y mostrar mensajes
  de fuentes faltantes.
og_title: Habilitar advertencias de sustitución de fuentes en C# – Guía completa
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: Enable font substitution warnings in C# using Aspose.Words. Learn how
    to configure LoadOptions, capture warnings, and handle missing fonts efficiently.
  headline: Enable Font Substitution Warnings in C# with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Font Substitution
- Warnings
title: Activar advertencias de sustitución de fuentes en C# con Aspose.Words
url: /es/net/programming-with-loadoptions/enable-font-substitution-warnings-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar advertencias de sustitución de fuentes en C# con Aspose.Words

¿Alguna vez te has preguntado cómo **habilitar advertencias de sustitución de fuentes** cuando un documento de Word hace referencia a una fuente que no está instalada en el servidor? No eres el único. Las fuentes faltantes pueden corromper silenciosamente el diseño de los PDFs o imágenes generados, y la única forma de detectarlo a tiempo es escuchar las advertencias que emite Aspose.Words.

En este tutorial recorreremos un ejemplo práctico que te muestra exactamente cómo activar esas advertencias, extraerlas de la colección `WarningInfo` y imprimir mensajes significativos en la consola. Al final sabrás cómo configurar **Aspose.Words LoadOptions**, manejar **advertencias de sustitución de fuentes en C#** y mantener a prueba de fallos tu canal de procesamiento de documentos.

También abordaremos algunos casos límite—qué ocurre si suprimes las advertencias, o si necesitas registrarlas en lugar de imprimirlas—y te proporcionaremos un ejemplo de código completo, listo para copiar y pegar, que funciona con la última versión de Aspose.Words para .NET (a partir de la versión 24.10).

## Lo que necesitarás

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.7+)
- Una referencia NuGet a `Aspose.Words` (instalar mediante `dotnet add package Aspose.Words`)
- Un archivo Word que haga referencia a una fuente que **no** tienes instalada (p. ej., `DocumentWithMissingFont.docx`)
- Un IDE decente (Visual Studio, Rider o VS Code)

Eso es todo—sin servicios adicionales, sin herramientas propietarias. ¿Listo? Vamos a sumergirnos.

## Paso 1: Habilitar advertencias de sustitución de fuentes

Lo primero que debes hacer es indicarle a Aspose.Words que deseas ser notificado cuando sustituye una fuente faltante. Esto se hace a través de la propiedad `FontSettings` de un objeto `LoadOptions`. Por defecto, las advertencias están **desactivadas** para mantener la API silenciosa, por lo que debemos activar la opción nosotros mismos.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

// Create LoadOptions and enable detailed font‑substitution warnings.
LoadOptions loadOpts = new LoadOptions
{
    // FontSettings is the gateway for all font‑related behavior.
    FontSettings = new FontSettings()
    // No extra code needed here; simply having a FontSettings instance
    // makes Aspose.Words collect font‑substitution warnings.
};
```

> **Por qué funciona:** Cuando `FontSettings` no es `null`, la biblioteca rellena automáticamente `Document.WarningInfo` con cualquier entrada `WarningType.FontSubstitution` que encuentre al cargar un documento. Piénsalo como activar un “modo de depuración” para fuentes.

## Paso 2: Cargar el documento con opciones configuradas

Ahora que la colección de advertencias está activa, carga tu documento usando el `LoadOptions` que acabamos de preparar. Si el documento contiene una fuente faltante, Aspose.Words sustituirá una fuente de respaldo y enviará una advertencia a la lista `WarningInfo`.

```csharp
// Path to a DOCX that references a font not present on the machine.
string docPath = @"C:\Samples\DocumentWithMissingFont.docx";

// Load the document while respecting the LoadOptions we set up.
Document doc = new Document(docPath, loadOpts);
```

> **Consejo profesional:** Si procesas muchos archivos en un bucle, reutiliza la misma instancia de `LoadOptions`; crearla una sola vez ahorra unos pocos milisegundos por iteración.

## Paso 3: Recorrer WarningInfo y mostrar mensajes de sustitución de fuentes

Una vez que el documento está cargado, la colección `WarningInfo` contiene todas las advertencias que ocurrieron durante la carga. Solo nos interesan las `WarningType.FontSubstitution`, por lo que filtramos en consecuencia.

```csharp
foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        Console.WriteLine($"Substituted: {warning.Description}");
}
```

Ejecutar el fragmento anterior contra un documento que hace referencia a la fuente faltante “Papyrus” podría producir una salida como:

```
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Comic Sans MS' is not installed. Substituted with 'Times New Roman'.
```

Esos son los **mensajes de sustitución de fuentes** que estabas buscando—claros, accionables y listos para registrarse o enviarse a un sistema de alertas.

## Ejemplo completo funcional

A continuación tienes un programa de consola autónomo que reúne todo. Copia‑pega el código en un nuevo `.csproj` y pulsa **Run**.

```csharp
// ---------------------------------------------------------------
// Enable Font Substitution Warnings – Complete Example
// ---------------------------------------------------------------

using System;
using Aspose.Words;
using Aspose.Words.Loading;
using Aspose.Words.Warnings;

class Program
{
    static void Main()
    {
        // 1️⃣ Configure LoadOptions to capture font‑substitution warnings.
        LoadOptions loadOpts = new LoadOptions
        {
            FontSettings = new FontSettings()   // Enabling warning collection.
        };

        // 2️⃣ Load the target document (adjust the path to match your environment).
        string docPath = @"C:\Samples\DocumentWithMissingFont.docx";
        Document doc = new Document(docPath, loadOpts);

        // 3️⃣ Process the warning collection.
        Console.WriteLine("=== Font Substitution Warnings ===");
        bool anyWarnings = false;

        foreach (WarningInfo warning in doc.WarningInfo)
        {
            if (warning.Type == WarningType.FontSubstitution)
            {
                anyWarnings = true;
                Console.WriteLine($"Substituted: {warning.Description}");
            }
        }

        if (!anyWarnings)
            Console.WriteLine("No font substitution warnings were generated.");

        // Optional: keep the console window open.
        Console.WriteLine("\nPress any key to exit...");
        Console.ReadKey();
    }
}
```

### Salida esperada

Si el documento hace referencia a fuentes que no están instaladas, verás algo similar a:

```
=== Font Substitution Warnings ===
Substituted: Font 'Papyrus' is not installed. Substituted with 'Arial'.
Substituted: Font 'Courier New' is not installed. Substituted with 'Times New Roman'.
Press any key to exit...
```

Si todas las fuentes están presentes en la máquina, el programa simplemente imprimirá:

```
=== Font Substitution Warnings ===
No font substitution warnings were generated.
Press any key to exit...
```

## Errores comunes y consejos profesionales

| Problema | Por qué ocurre | Cómo arreglar / evitar |
|----------|----------------|------------------------|
| **Las advertencias desaparecen** | Has borrado `FontSettings` o usaste un `LoadOptions` sin él. | Siempre instancia `FontSettings` aunque no modifiques ninguna propiedad. |
| **Demasiadas advertencias** | El documento usa muchas fuentes exóticas. | Considera agregar una carpeta de fuentes personalizada a `FontSettings` mediante `SetFontsFolder` para reducir sustituciones. |
| **Impacto de rendimiento en un bucle ajustado** | Re‑crear `LoadOptions` en cada iteración añade sobrecarga. | Reutiliza una única instancia de `LoadOptions` para todos los documentos. |
| **Salida de consola ausente** | Ejecutándose dentro de una aplicación GUI donde `Console.WriteLine` se ignora. | Redirige las advertencias a un registrador (`ILogger`) o escríbelas en un archivo. |

### Manejo de advertencias en un servicio del mundo real

En una API web probablemente no quieras escribir en la consola. En su lugar, canaliza las advertencias a un registro estructurado:

```csharp
var logger = LoggerFactory.Create(builder => builder.AddConsole()).CreateLogger<Program>();

foreach (WarningInfo warning in doc.WarningInfo)
{
    if (warning.Type == WarningType.FontSubstitution)
        logger.LogWarning("Font substitution: {Description}", warning.Description);
}
```

De esa manera mantienes el **manejo de advertencias de documentos** mientras mantienes tu servicio limpio.

## Extender el ejemplo

- **Capturar otros tipos de advertencia** (p. ej., `WarningType.UnknownFileFormat`) eliminando el filtro `if`.
- **Guardar un informe** de todas las advertencias en JSON para análisis posteriores.
- **Forzar una fuente de respaldo específica** estableciendo `FontSettings.SubstitutionSettings.DefaultFontName`.

Todas estas son extensiones naturales una vez que domines **habilitar advertencias de sustitución de fuentes**.

## Conclusión

Te hemos mostrado cómo **habilitar advertencias de sustitución de fuentes** en C# usando Aspose.Words, desde la configuración de `LoadOptions` hasta iterar sobre `WarningInfo` e imprimir mensajes amigables. Siguiendo los pasos anteriores puedes proteger tus canalizaciones de procesamiento de documentos contra cambios silenciosos de diseño causados por fuentes faltantes.

A continuación, intenta agregar una carpeta de fuentes personalizada, registrar las advertencias en un archivo, o incluso enviarlas a un panel de monitoreo. El mismo patrón funciona para cualquier escenario de **manejo de advertencias de documentos**, ya sea que estés convirtiendo a PDF, renderizando imágenes o realizando combinación de correspondencia.

¿Tienes preguntas sobre **advertencias de sustitución de fuentes en C#** o quieres compartir una solución ingeniosa? ¡Deja un comentario abajo—feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Habilitar advertencias de sustitución de fuentes en Aspose.Words – Guía completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cómo detectar fuentes en Aspose.Words – Manejar advertencias y configuraciones](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}