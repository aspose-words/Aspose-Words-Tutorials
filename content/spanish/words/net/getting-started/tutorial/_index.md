---
language: es
url: /spanish/net/getting-started/tutorial/
---

{{< layout-start >}}

{{< layout-start >}}

```yaml
---
title: "Detect Missing Fonts in Aspose.Words Documents – Complete C# Guide"
description: "Detect missing fonts in your Aspose.Words documents using a warning callback. Learn how to log font substitutions with C# and keep your PDFs looking right."
date: 2025-12-08
draft: false
language: "en"
category: "general"
url: "PLACEHOLDER_URL"
keywords:
  - detect missing fonts
  - Aspose.Words warning callback
  - font substitution
  - LoadOptions C#
  - document loading C#
  - missing font detection
tags:
  - Aspose.Words
  - C#
  - Font Management
og_title: "Detect Missing Fonts in Aspose.Words – Step‑by‑Step C# Guide"
og_description: "Detect missing fonts in Aspose.Words documents instantly. Follow this guide to set up a warning callback and capture font substitution events in C#."
---
```

# Detectar fuentes faltantes en documentos Aspose.Words – Guía completa en C# 

¿Alguna vez te has preguntado cómo **detectar fuentes faltantes** al cargar un archivo Word con Aspose.Words? En mi trabajo diario, me he encontrado con algunos PDFs que se veían extraños porque el documento original usaba una fuente que no tenía instalada. ¿La buena noticia? Aspose.Words puede indicarte exactamente cuándo sustituye una fuente, y puedes capturar esa información con una simple devolución de llamada de advertencia.  

En este tutorial repasaremos un **ejemplo completo y ejecutable** que muestra cómo registrar cada sustitución de fuente, por qué es importante la devolución de llamada y un par de trucos adicionales para una detección robusta de fuentes faltantes. Sin rodeos, solo el código y el razonamiento que necesitas para hacerlo funcionar hoy.

---

## Lo que aprenderás

- Cómo implementar **Aspose.Words warning callback** para capturar eventos de sustitución de fuentes.  
- Cómo configurar **LoadOptions C#** para que la devolución de llamada se invoque al cargar un documento.  
- Cómo verificar que la detección de fuentes faltantes realmente funcionó y cómo se ve la salida en la consola.  
- Ajustes opcionales para lotes grandes o entornos sin interfaz.  

**Prerequisitos** – Necesitas una versión reciente de Aspose.Words para .NET (el código se probó con la 23.12), .NET 6 o posterior, y un conocimiento básico de C#. Si los tienes, estás listo para comenzar.

---

## Detectar fuentes faltantes con una devolución de llamada de advertencia

El núcleo de la solución es una implementación de `IWarningCallback`. Aspose.Words genera un objeto `WarningInfo` para muchas situaciones, pero solo nos interesan los de tipo `WarningType.FontSubstitution`. Veamos cómo engancharlo.

### Paso 1: Crear un recolector de advertencias de fuentes

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;

/// <summary>
/// Collects font‑substitution warnings emitted by Aspose.Words.
/// </summary>
class FontWarningCollector : IWarningCallback
{
    // The Warning method is called automatically by the library.
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings.
        if (info.Type == WarningType.FontSubstitution)
        {
            // Write a helpful message to the console.
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

*Por qué es importante*: Al filtrar por `WarningType.FontSubstitution` evitamos el desorden de advertencias no relacionadas (como características obsoletas). `info.Description` ya contiene el nombre de la fuente original y la fuente de reemplazo utilizada, proporcionándote una pista de auditoría clara.

---

## Configurar LoadOptions para usar la devolución de llamada

Ahora le indicamos a Aspose.Words que use nuestro recolector al cargar un archivo.

### Paso 2: Configurar LoadOptions

```csharp
// Create a LoadOptions instance – this controls how the document is read.
LoadOptions loadOptions = new LoadOptions
{
    // Assign our custom warning callback.
    WarningCallback = new FontWarningCollector()
};
```

*Por qué es importante*: `LoadOptions` es el único lugar donde puedes conectar la devolución de llamada, contraseñas de cifrado y otros comportamientos de carga. Mantenerlo separado del constructor `Document` hace que el código sea reutilizable en muchos archivos.

---

## Cargar el documento y capturar fuentes faltantes

Con la devolución de llamada configurada, el siguiente paso es simplemente cargar el documento.

### Paso 3: Cargar tu DOCX (o cualquier formato compatible)

```csharp
// Replace the path with the location of your test document.
string inputPath = @"C:\Docs\input.docx";

try
{
    // The warning callback fires automatically during this call.
    Document doc = new Document(inputPath, loadOptions);
    Console.WriteLine("Document loaded successfully.");
}
catch (Exception ex)
{
    // Handle file‑not‑found, access‑denied, etc.
    Console.WriteLine($"Error loading document: {ex.Message}");
}
```

Cuando el constructor `Document` analiza el archivo, cualquier fuente faltante activa nuestro `FontWarningCollector`. La consola mostrará líneas como:

```
Font substituted: Arial (substituted with Liberation Sans)
Document loaded successfully.
```

Esa línea es la evidencia concreta de que **detect missing fonts** funcionó.

---

## Verificar la salida – Qué esperar

Ejecuta el programa desde una terminal o Visual Studio. Si el documento fuente contiene una fuente que no tienes instalada, verás al menos una línea “Font substituted”. Si el documento usa solo fuentes instaladas, la devolución de llamada permanecerá silenciosa y solo obtendrás el mensaje “Document loaded successfully.”.

**Consejo**: Para comprobarlo, abre el archivo Word en Microsoft Word y revisa la lista de fuentes. Cualquier fuente que aparezca en *Replace Fonts* bajo el grupo *Home → Font* es una candidata para sustitución.

---

## Avanzado: Detectar fuentes faltantes en lote

A menudo necesitas escanear docenas de archivos. El mismo patrón escala sin problemas:

```csharp
string[] files = Directory.GetFiles(@"C:\Docs\Batch", "*.docx");

foreach (var file in files)
{
    Console.WriteLine($"\nProcessing: {Path.GetFileName(file)}");
    Document doc = new Document(file, loadOptions);
}
```

Debido a que `FontWarningCollector` escribe en la consola cada vez que se invoca, obtendrás un informe por archivo sin tuberías adicionales. Para escenarios de producción podrías registrar en un archivo o base de datos – simplemente reemplaza `Console.WriteLine` por tu registrador preferido.

---

## Errores comunes y consejos profesionales

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparecen advertencias** | El documento en realidad solo contiene fuentes instaladas. | Verifícalo abriendo el archivo en Word o eliminando deliberadamente una fuente de tu sistema. |
| **Devolución de llamada no invocada** | `LoadOptions.WarningCallback` nunca se asignó o se utilizó una nueva instancia de `LoadOptions` más tarde. | Mantén un único objeto `LoadOptions` y reutilízalo para cada carga. |
| **Demasiadas advertencias no relacionadas** | No filtraste por `WarningType.FontSubstitution`. | Añade la condición `if (info.Type == WarningType.FontSubstitution)` como se muestra. |
| **Ralentización del rendimiento en archivos grandes** | La devolución de llamada se ejecuta en cada advertencia, lo que puede ser muchas en documentos grandes. | Desactiva otros tipos de advertencia mediante `LoadOptions.WarningCallback` o establece `LoadOptions.LoadFormat` a un tipo específico si lo conoces. |

---

## Ejemplo completo funcional (listo para copiar y pegar)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class FontWarningCollector : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.Type == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}

class Program
{
    static void Main()
    {
        // Step 2 – configure LoadOptions with our warning callback.
        LoadOptions loadOptions = new LoadOptions
        {
            WarningCallback = new FontWarningCollector()
        };

        // Path to a single document or a folder for batch processing.
        string inputPath = @"C:\Docs\input.docx";

        try
        {
            // Step 3 – load the document; warnings are emitted automatically.
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine("Document loaded successfully.");
        }
        catch (Exception ex)
        {
            Console.WriteLine($"Error loading document: {ex.Message}");
        }
    }
}
```

**Salida esperada en la consola** (cuando se encuentra una fuente faltante):

```
Font substituted: Times New Roman (substituted with Liberation Serif)
Document loaded successfully.
```

Si no ocurre sustitución, solo verás la línea de éxito.

---

## Conclusión

Ahora tienes una **solución completa y lista para producción para detectar fuentes faltantes** en cualquier documento procesado por Aspose.Words. Aprovechando la **devolución de llamada de advertencia de Aspose.Words** y configurando **LoadOptions C#**, puedes registrar cada sustitución de fuente, solucionar problemas de y garantizar que tus PDFs mantengan el aspecto y la sensación previstos.  

Desde un solo archivo hasta un lote masivo, el patrón sigue siendo el mismo: implementa `IWarningCallback`, conéctalo a `LoadOptions` y deja que Aspose.Words haga el trabajo pesado.  

¿Listo para el siguiente paso? Prueba combinar esto con **font embedding** o **fallback font families** para corregir automáticamente el problema, o explora la API **DocumentVisitor** para un análisis de contenido más profundo. ¡Feliz codificación, y que todas tus fuentes permanezcan donde esperas!

---

![Detectar fuentes faltantes en Aspose.Words – captura de pantalla de la salida de consola](https://example.com/images/detect-missing-fonts.png "salida de consola de detección de fuentes faltantes")

{{< layout-end >}}

{{< layout-end >}}