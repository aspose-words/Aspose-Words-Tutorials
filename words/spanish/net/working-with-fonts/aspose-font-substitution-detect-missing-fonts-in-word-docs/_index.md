---
category: general
date: 2026-05-04
description: 'Aprenda cómo usar la sustitución de fuentes de Aspose para detectar
  fuentes faltantes al cargar un documento de Word y obtener los detalles de las fuentes
  faltantes: guía paso a paso.'
draft: false
keywords:
- aspose font substitution
- detect missing fonts
- load word document
- retrieve missing font
language: es
og_description: Domina la sustitución de fuentes de Aspose para detectar fuentes faltantes
  al cargar un documento Word y recuperar la información de fuentes faltantes con
  código C# completo.
og_title: Sustitución de fuentes Aspose – Detectar fuentes faltantes en documentos
  Word
tags:
- Aspose.Words
- C#
- Font Management
title: 'Sustitución de fuentes Aspose: Detectar fuentes faltantes en documentos Word'
url: /es/net/working-with-fonts/aspose-font-substitution-detect-missing-fonts-in-word-docs/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose Font Substitution – Detectar fuentes faltantes en documentos Word

¿Alguna vez te has preguntado por qué un documento Word se ve mal en otra máquina? A menudo el culpable es una fuente faltante, y **Aspose font substitution** es la herramienta que te permite detectar esas ausencias antes de que se conviertan en un desastre visual. En este tutorial recorreremos cómo **detect missing fonts** en el momento en que **load a Word document**, y luego **retrieve missing font** details para que puedas corregirlas o reemplazarlas.

Cubrirémos todo, desde configurar la devolución de llamada de advertencia hasta obtener una lista limpia de fuentes faltantes. Al final, tendrás un fragmento de C# listo para ejecutar que te indica exactamente qué fuentes no se cargaron, y comprenderás por qué esto es importante para la fidelidad del documento.

---

## Prerequisitos – Lo que necesitas antes de comenzar

- **Aspose.Words for .NET** (v23.12 o posterior recomendado).  
- Un entorno de desarrollo .NET (Visual Studio, Rider, o la CLI `dotnet`).  
- Un DOCX de ejemplo que intencionalmente use una fuente que no tienes instalada —llámalo `DocumentWithMissingFont.docx`.  
- Conocimientos básicos de C# — nada sofisticado, solo la capacidad de ejecutar una aplicación de consola.

Si alguno de esos conceptos te resulta desconocido, detente e instala el paquete NuGet:

```bash
dotnet add package Aspose.Words
```

Eso es todo. No fuentes extra, sin servicios externos.

---

## Paso 1: Cargar el documento Word (y activar la comprobación de fuentes)

Lo primero que haces es **load a Word document**. Aspose.Words analiza el archivo y, si no puede localizar una fuente referenciada, genera una advertencia *FontSubstitution*. Aquí está el código que realiza la carga:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Path to the DOCX that may contain missing fonts
string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";

// Load the document – this is where Aspose starts checking fonts
Document doc = new Document(docPath);
```

> **Por qué es importante:** Cargar el documento temprano le da a Aspose la oportunidad de escanear cada ejecución de texto, estilo y objeto incrustado. Si una fuente no se encuentra en el sistema o en la carpeta de fuentes personalizada, recibirás una advertencia más adelante.

---

## Paso 2: Adjuntar una devolución de llamada de advertencia para capturar eventos de sustitución

Aspose.Words utiliza un mecanismo de devolución de llamada para informarte sobre problemas como fuentes faltantes. Al asignar una implementación de `IWarningCallback` a `doc.WarningCallback`, puedes interceptar cada advertencia a medida que ocurre.

```csharp
// Register the callback that will handle font substitution warnings
doc.WarningCallback = new FontSubstitutionWarningCallback();
```

> **Consejo profesional:** Puedes adjuntar múltiples devoluciones de llamada (p. ej., registro, actualizaciones de UI) envolviéndolas en un patrón compuesto, pero para este tutorial una única devolución de llamada mantiene las cosas claras.

---

## Paso 3: Implementar la devolución de llamada de advertencia de sustitución de fuentes

Ahora definimos la clase que realmente realiza el trabajo. La devolución de llamada recibe un objeto `WarningInfo`; filtramos por `WarningType.FontSubstitution` y almacenamos la descripción para uso posterior.

```csharp
class FontSubstitutionWarningCallback : IWarningCallback
{
    // A thread‑safe list to collect all missing‑font messages
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        // We only care about font substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Write to console for immediate feedback
            Console.WriteLine($"Font substituted: {info.Description}");
            // Keep the message for later retrieval
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

> **Qué está sucediendo:** Cuando Aspose encuentra una fuente faltante, crea una advertencia como “Font substitution: 'Comic Sans MS' was not found, using 'Arial' instead.” Nuestra devolución de llamada imprime esa línea y la guarda.

---

## Paso 4: Procesar el documento (opcional) y recopilar fuentes faltantes

Si solo necesitas **detect missing fonts**, el paso de carga es suficiente —las advertencias se disparan automáticamente. Sin embargo, muchos desarrolladores también necesitan **retrieve missing font** información después de realizar algunas operaciones (p. ej., guardar, convertir). A continuación forzamos una pequeña operación —guardar a PDF— para asegurar que se emitan todas las advertencias, y luego extraemos los mensajes recopilados.

```csharp
// Force a save to trigger any lazy warnings (optional but safe)
doc.Save("output.pdf");

// After processing, retrieve the list of missing fonts
if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
{
    Console.WriteLine("\n=== Missing Fonts Summary ===");
    foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
    {
        Console.WriteLine(msg);
    }
}
else
{
    Console.WriteLine("\nNo missing fonts were detected.");
}
```

> **Salida esperada en consola** (ejemplo):
> ```
> Font substituted: Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substituted: Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> 
> === Missing Fonts Summary ===
> Font substitution: 'Papyrus' was not found, using 'Times New Roman' instead.
> Font substitution: 'Brush Script MT' was not found, using 'Arial' instead.
> ```

Observa cómo cada línea indica claramente la fuente original y la sustituta que Aspose eligió. Ese es el núcleo del informe de **aspose font substitution**.

---

## Paso 5: Avanzado – Usar fuentes personalizadas para reducir sustituciones

A veces *sí* tienes las fuentes faltantes, solo que no están en la carpeta del sistema predeterminada. Aspose.Words te permite apuntar a un directorio personalizado mediante `FontSettings`. Añadir este paso puede reducir drásticamente la cantidad de advertencias de sustitución.

```csharp
// Optional: Add a folder that contains your custom fonts
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
doc.FontSettings = fontSettings;
```

> **¿Por qué añadir esto?** Si distribuyes documentos entre máquinas, empaquetar las fuentes requeridas en una carpeta conocida garantiza la misma apariencia visual en todas partes. También hace que tu rutina de **detect missing fonts** sea más precisa porque Aspose verifica esa carpeta antes de recurrir a una sustitución.

---

## Ejemplo completo en funcionamiento

Juntando todo, aquí tienes un programa de consola listo para copiar y pegar. Guárdalo como `Program.cs` y ejecútalo con `dotnet run`.

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // ---------- Step 1: Load the Word document ----------
        string docPath = @"YOUR_DIRECTORY/DocumentWithMissingFont.docx";
        Document doc = new Document(docPath);

        // ---------- Optional: Point to a custom font folder ----------
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyCustomFonts", recursive: true);
        doc.FontSettings = fontSettings;

        // ---------- Step 2: Register the warning callback ----------
        doc.WarningCallback = new FontSubstitutionWarningCallback();

        // ---------- Step 3: Force a save to trigger all warnings ----------
        doc.Save("output.pdf");

        // ---------- Step 4: Retrieve and display missing fonts ----------
        if (FontSubstitutionWarningCallback.MissingFontMessages.Any())
        {
            Console.WriteLine("\n=== Missing Fonts Summary ===");
            foreach (var msg in FontSubstitutionWarningCallback.MissingFontMessages)
            {
                Console.WriteLine(msg);
            }
        }
        else
        {
            Console.WriteLine("\nNo missing fonts were detected.");
        }
    }
}

// ---------- Callback implementation ----------
class FontSubstitutionWarningCallback : IWarningCallback
{
    public static readonly List<string> MissingFontMessages = new List<string>();

    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
            lock (MissingFontMessages)
            {
                MissingFontMessages.Add(info.Description);
            }
        }
    }
}
```

**Lo que deberías ver:** Si el DOCX de origen referencia fuentes que no tienes, la consola imprimirá cada línea de sustitución seguida de un resumen conciso. Si todas las fuentes están presentes, obtendrás el mensaje “No missing fonts were detected.”

---

## Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparecen advertencias** | El documento usa solo fuentes del sistema, o ya agregaste una carpeta personalizada que contiene las fuentes faltantes. | Verifica que el DOCX realmente haga referencia a una fuente no disponible. Puedes abrirlo en Word y cambiar un párrafo a una fuente rara (p. ej., “Papyrus”). |
| **Mensajes duplicados** | La misma fuente se usa en múltiples ejecuciones, lo que genera varias advertencias. | Elimina duplicados de la lista con `Distinct()` si solo necesitas un conjunto único. |
| **Impacto de rendimiento en documentos grandes** | Cada advertencia se procesa en el hilo de UI. | Ejecuta la carga en una tarea en segundo plano o usa `Parallel.ForEach` para el post‑procesamiento. |
| **Fuente de sustitución incorrecta** | La sustitución predeterminada de Aspose puede no coincidir con tu identidad de marca. | Establece `FontSettings.SubstitutionSettings.DefaultFontName` a una sustituta preferida (p. ej., “Calibri”). |

---

## Extender la solución – Exportar fuentes faltantes a JSON

Si estás construyendo un servicio web que necesita informar fuentes faltantes a un cliente, serializar la lista es trivial:

```csharp
using System.Text.Json;

// After gathering messages...
string json = JsonSerializer.Serialize(FontSubstitutionWarningCallback.MissingFontMessages);
File.WriteAllText("missing-fonts.json", json);
Console.WriteLine("Missing fonts exported to missing-fonts.json");
```

Ahora tu API puede devolver una carga JSON limpia que otro sistema pueda consumir.

---

## Conclusión

En esta guía demostramos **Aspose font substitution** de principio a fin: cargar un documento Word, adjuntar una devolución de llamada de advertencia, capturar cada evento de *detect missing fonts*, y finalmente obtener información **retrieve missing font** para informes o remediación. Al añadir carpetas de fuentes personalizadas opcionales puedes reducir la lista de sustituciones, y con unas pocas líneas extra incluso puedes exportar los resultados como JSON.

Recuerda, la integridad visual de tus documentos depende de las fuentes que utilizan. Con la técnica mostrada aquí, nunca volverás a sorprenderte con una sustitución inesperada.  

¿Listo para dar el siguiente paso? Prueba integrar esta lógica en una canalización de procesamiento de documentos más grande, o explora otras características de Aspose.Words como la incrustación de fuentes (`doc.FontSettings.EmbeddedFonts`). Las posibilidades son infinitas, y tus usuarios te agradecerán por el resultado pulido.

---

![Screenshot of

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}