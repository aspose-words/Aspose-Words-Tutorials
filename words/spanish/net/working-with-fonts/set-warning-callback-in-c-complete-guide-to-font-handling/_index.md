---
category: general
date: 2026-02-10
description: Establezca la devolución de llamada de advertencia para supervisar los
  cambios de fuente mientras configura la fuente predeterminada y establece la fuente
  de importación predeterminada en Aspose.Words. Aprenda la solución completa paso
  a paso.
draft: false
keywords:
- set warning callback
- configure default font
- monitor font changes
- set default import font
language: es
og_description: Establezca la devolución de llamada de advertencia para monitorizar
  los cambios de fuente al configurar la fuente predeterminada y al establecer la
  fuente de importación predeterminada. Siga el tutorial completo de Aspose.Words.
og_title: Configurar la devolución de llamada de advertencia en C# – Guía completa
tags:
- Aspose.Words
- C#
- Document Import
title: Establecer la devolución de llamada de advertencia en C# – Guía completa de
  manejo de fuentes
url: /es/net/working-with-fonts/set-warning-callback-in-c-complete-guide-to-font-handling/
---

all markdown formatting, code placeholders unchanged.

Now produce final answer with only translated content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer callback de advertencia en C# – Guía completa de manejo de fuentes

¿Alguna vez necesitaste **set warning callback** al cargar un documento Word y te preguntaste cómo *configure default font* al mismo tiempo? No estás solo. En muchos proyectos del mundo real—como generadores automáticos de informes o pipelines de conversión de documentos—las fuentes faltantes pueden romper silenciosamente el diseño, y la única forma de detectar esos problemas es **monitor font changes** mediante un callback de advertencia.

En este tutorial recorreremos un ejemplo práctico que muestra cómo **set warning callback**, **configure default font**, e incluso **set default import font** usando Aspose.Words para .NET. Al final tendrás un fragmento listo para ejecutar, comprenderás por qué cada pieza es importante y sabrás cómo adaptarlo a casos extremos como carpetas de fuentes personalizadas o sustituciones silenciosas.

---

## Requisitos previos

- .NET 6.0 o posterior (el código también funciona en .NET Framework 4.6+)
- Paquete NuGet de Aspose.Words para .NET (`Install-Package Aspose.Words`)
- Una carpeta que contenga la fuente de reserva que deseas usar (p.ej., `fonts/Arial.ttf`)
- Familiaridad básica con aplicaciones de consola C#

No se requieren bibliotecas adicionales.

---

## Paso 1: Crear LoadOptions y **configure default font**

Lo primero que haces cuando deseas controlar el manejo de fuentes es crear una instancia de `LoadOptions`. Este objeto le indica a Aspose.Words cómo tratar las fuentes faltantes durante la importación.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Build LoadOptions with a default font
LoadOptions loadOptions = new LoadOptions
{
    // FontSettings lets you point to a folder or a specific file that will act as the fallback.
    FontSettings = new FontSettings()
};

// Point the FontSettings to a folder that contains the font you want as the default import font.
loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", /*recursive*/ true);
```

**Por qué esto es importante:**  
Si el documento fuente hace referencia a una fuente que no está instalada en el servidor, Aspose.Words buscará en la carpeta que proporcionaste. Este es el núcleo de **set default import font**—estás indicando explícitamente a la biblioteca dónde encontrar un reemplazo antes de que se generen advertencias.

---

## Paso 2: **Set warning callback** para **monitor font changes**

Aspose.Words emite una `WarningInfoCollection` cada vez que debe sustituir una fuente, entre otras cosas. Al adjuntar un manejador, puedes registrar o reaccionar a cada sustitución.

```csharp
// Step 2: Attach a warning callback to capture font substitution events
var warningCollector = new WarningInfoCollection();
loadOptions.WarningCallback = warningCollector;

// Subscribe to the Warning event
warningCollector.Warning += (sender, e) =>
{
    // We only care about font substitution warnings
    if (e.Type == WarningType.FontSubstitution)
    {
        Console.WriteLine($"Font substituted: {e.Description}");
    }
};
```

**Por qué esto es importante:**  
Simplemente **configure default font** no es suficiente si necesitas auditar qué fuentes fueron realmente intercambiadas. El callback te brinda un registro en tiempo real, cumpliendo con el requisito de **monitor font changes** y ayudándote a detectar sustituciones inesperadas temprano en una pipeline CI.

---

## Paso 3: Cargar el documento con las opciones preparadas

Ahora que las opciones de carga están completamente preparadas, puedes cargar de forma segura cualquier archivo `.docx`. El callback se dispara automáticamente si ocurre una sustitución.

```csharp
// Step 3: Load the document using the configured LoadOptions
string inputPath = @"C:\MyProject\input.docx";
Document doc = new Document(inputPath, loadOptions);

// Optional: verify the document loaded correctly
Console.WriteLine($"Document loaded – {doc.PageCount} page(s) total.");
```

**Lo que verás:**  
Si la fuente del origen no está presente, la consola imprimirá algo como:

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s) total.
```

Esa salida confirma que has **set warning callback** con éxito y que la **default import font** tuvo efecto.

---

## Paso 4: (Opcional) Ajustar finamente el comportamiento de sustitución de fuentes

A veces podrías querer reemplazar *todas* las fuentes faltantes con una única familia, sin importar la solicitud original. Aspose.Words te permite establecer una *fallback font* de forma global.

```csharp
// Step 4: Force all missing fonts to use a specific fallback
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";
```

**Cuándo usar esto:**  
Si estás generando PDFs para una marca que solo permite un conjunto limitado de fuentes, esto garantiza consistencia en cada documento, incluso si el origen intenta usar algo exótico.

---

## Paso 5: Guardar o procesar adicionalmente el documento

Después de cargar, puedes continuar con cualquier procesamiento que necesites—edición, conversión a PDF, extracción de texto, etc. Aquí tienes un ejemplo rápido de guardar el documento como PDF manteniendo las fuentes sustituidas.

```csharp
// Step 5: Save the document as PDF to verify the visual result
string outputPath = @"C:\MyProject\output.pdf";
doc.Save(outputPath, SaveFormat.Pdf);
Console.WriteLine($"PDF saved to {outputPath}");
```

El PDF resultante mostrará la fallback font donde se haya producido una sustitución, dándote una confirmación visual de que el **set warning callback** funcionó como se esperaba.

---

## Problemas comunes y consejos profesionales

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **Callback never fires** | `LoadOptions.WarningCallback` no se asignó *antes* de cargar el documento. | Siempre adjunta el callback **antes** de llamar a `new Document(...)`. |
| **Wrong font folder** | Error tipográfico en la ruta o permisos de lectura faltantes. | Verifica que la carpeta exista y que la aplicación tenga acceso `Read`. Usa rutas absolutas para mayor fiabilidad. |
| **Multiple substitutions, noisy output** | Documentos grandes con muchas fuentes faltantes. | Filtra advertencias por `WarningType.FontSubstitution` (como se muestra) o escríbelas en un archivo de registro en lugar de la consola. |
| **Fallback font not applied** | La fallback font no está instalada en la máquina. | Coloca el archivo `.ttf`/`.otf` en la carpeta que pasaste a `SetFontsFolder`. Aspose.Words lo carga directamente, sin necesidad de instalarlo en el SO. |

**Consejo profesional:** Cuando ejecutas esto en una pipeline CI/CD, redirige la salida de la consola a un artefacto de compilación. Así tendrás un registro de auditoría de cada sustitución de fuentes que ocurrió durante la compilación.

---

## Ejemplo completo (listo para copiar y pegar)

A continuación se muestra el programa completo que puedes colocar en un nuevo proyecto de aplicación de consola. Incluye todos los pasos, sentencias using y comentarios que necesitas.

```csharp
// Full example: Set warning callback, configure default font, and monitor font changes
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontWarningDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create LoadOptions and point to a fallback font folder
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            // Adjust the path to where your fallback fonts live
            loadOptions.FontSettings.SetFontsFolder(@"C:\MyProject\fonts", true);

            // 2️⃣ Set up the warning callback to catch font substitutions
            var warningCollector = new WarningInfoCollection();
            loadOptions.WarningCallback = warningCollector;
            warningCollector.Warning += (sender, e) =>
            {
                if (e.Type == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font substituted: {e.Description}");
                }
            };

            // 3️⃣ Load the document with the prepared options
            string inputPath = @"C:\MyProject\input.docx";
            Document doc = new Document(inputPath, loadOptions);
            Console.WriteLine($"Document loaded – {doc.PageCount} page(s).");

            // 4️⃣ (Optional) Force a single default font for *all* missing fonts
            // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "Arial";

            // 5️⃣ Save as PDF to see the visual result
            string outputPath = @"C:\MyProject\output.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

**Salida esperada en la consola** (asumiendo que `Times New Roman` estaba ausente):

```
Font substituted: Font "Times New Roman" was not found. Substituted with "Arial".
Document loaded – 3 page(s).
PDF saved to C:\MyProject\output.pdf
```

Ejecuta el programa, abre `output.pdf`, y verás el documento renderizado con la fallback font donde sea necesario.

---

## Conclusión

Ahora tienes un patrón sólido y listo para producción sobre cómo **set warning callback** en C#, **configure default font**, **monitor font changes**, y **set default import font** al trabajar con Aspose.Words. Al adjuntar un recopilador de advertencias antes de cargar, apuntar `FontSettings` a una carpeta de fuentes confiable y, opcionalmente, forzar una fallback global, obtienes total visibilidad y control sobre la sustitución de fuentes—exactamente lo que cualquier pipeline robusto de procesamiento de documentos necesita.

¿Listo para el siguiente nivel? Prueba combinar este enfoque con:

- **Dynamic font loading** desde una base de datos (usa `FontSettings.SetFontsFolder` en tiempo de ejecución).  
- **Custom warning handlers** que escriban a un registro estructurado (JSON o CSV) para análisis.  
- **Parallel document processing** donde cada hilo obtenga su propio `LoadOptions` para evitar interferencias.

Siéntete libre de experimentar, adaptar el código a tu propia arquitectura y compartir cualquier descubrimiento en los comentarios. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}