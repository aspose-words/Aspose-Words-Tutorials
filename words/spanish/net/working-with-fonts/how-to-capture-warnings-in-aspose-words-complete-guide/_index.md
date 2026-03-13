---
category: general
date: 2026-03-13
description: Cómo capturar advertencias al cargar documentos con Aspose.Words, además
  de consejos para manejar fuentes faltantes y establecer configuraciones de fuentes
  personalizadas. Aprende una solución completa en C#.
draft: false
keywords:
- how to capture warnings
- handle missing fonts
- set custom font settings
language: es
og_description: Cómo capturar advertencias al cargar archivos Word con Aspose.Words,
  además de formas prácticas de manejar fuentes faltantes y configurar ajustes de
  fuentes personalizados.
og_title: Cómo capturar advertencias en Aspose.Words – Guía completa
tags:
- Aspose.Words
- C#
- Document Processing
title: Cómo capturar advertencias en Aspose.Words – Guía completa
url: /es/net/working-with-fonts/how-to-capture-warnings-in-aspose-words-complete-guide/
---

.

Make sure we didn't translate any code block placeholders. Keep them.

Now produce final content.{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo capturar advertencias en Aspose.Words – Guía completa

¿Alguna vez te has preguntado **cómo capturar advertencias** que aparecen cuando Aspose.Words carga un documento? En muchos proyectos del mundo real verás alertas de sustitución de fuentes, notas sobre funciones obsoletas o incluso mensajes relacionados con la seguridad. Ignorarlas es como conducir con el parabrisas agrietado: puedes llegar a tu destino, pero nunca sabrás cuándo algo está a punto de romperse.

La buena noticia es que Aspose.Words te ofrece una forma limpia, basada en callbacks, de interceptar esos mensajes. En este tutorial recorreremos un **ejemplo completo en C#** que no solo captura advertencias, sino que también te muestra cómo **manejar fuentes faltantes** y **establecer configuraciones de fuentes personalizadas** para que tus documentos se rendericen exactamente como esperas.

---

## Qué aprenderás

- Configurar `LoadOptions` para conectar un objeto `FontSettings` personalizado.  
- Registrar un callback de advertencias que filtre los eventos `FontSubstitution`.  
- Mostrar los detalles de la advertencia en la consola (o en cualquier registrador que prefieras).  
- Extender la solución para manejar elegantemente fuentes faltantes en diferentes plataformas.  

Al final de esta guía tendrás un fragmento listo‑para‑ejecutar que podrás insertar en cualquier proyecto .NET, además de un puñado de consejos prácticos para evitar errores comunes.

---

## Requisitos previos

| Requirement | Why It Matters |
|-------------|----------------|
| **Aspose.Words for .NET** (v23.12 o posterior) | La API que usamos (`LoadOptions`, `IWarningCallback`) se encuentra aquí. |
| **.NET 6+** (o .NET Framework 4.7.2+) | Las características modernas del lenguaje hacen que el código sea más limpio. |
| **Un DOCX de ejemplo** (llamado `input.docx`) colocado en una carpeta conocida | Necesitamos algo para cargar y generar una advertencia. |
| **Una consola o framework de registro** (opcional) | Para ver las advertencias capturadas en acción. |

No se requieren paquetes NuGet adicionales más allá de Aspose.Words mismo.

---

## Paso 1: Configurar fuentes personalizadas  

Antes de cargar un documento puedes indicarle a Aspose.Words dónde buscar fuentes. Esta es la parte de **establecer configuraciones de fuentes personalizadas** del rompecabezas.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

// 1️⃣ Create a FontSettings instance and point it at your font folder.
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

// 2️⃣ Plug the FontSettings into LoadOptions.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = fontSettings
};
```

**Por qué es importante:**  

Si un DOCX hace referencia a una fuente que no está instalada en la máquina, Aspose.Words sustituirá silenciosamente una fuente de respaldo *a menos que* hayas configurado una carpeta con las fuentes requeridas. Al establecer una carpeta personalizada reduces la probabilidad de advertencias de “sustitución de fuentes” desde el principio.

> **Consejo profesional:** En Linux puede que necesites agregar el paquete `fonts-dejavu-core` o cualquier colección TrueType de la que dependan tus documentos.

---

## Paso 2: Registrar un callback de advertencias  

Aspose.Words implementa `IWarningCallback`. Crearemos un pequeño manejador que imprima solo las advertencias que nos importan: fuentes faltantes o sustituidas.

```csharp
// 3️⃣ Register the callback.
loadOptions.WarningCallback = new FontWarningHandler();
```

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warn(IWarningInfo info)
    {
        // Filter for font‑substitution warnings only.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // You could log to a file, send to telemetry, etc.
            Console.WriteLine($"[Font Substitution] {info.Description}");
        }
        // Optionally handle other warning types here.
    }
}
```

**Por qué es importante:**  

El escenario de **manejar fuentes faltantes** ahora es visible para ti. En lugar de adivinar qué fuente se sustituyó, obtienes una descripción clara como “Font 'Calibri' was substituted with 'Arial'”. Esto es invaluable al depurar problemas de diseño en PDFs generados o informes impresos.

---

## Paso 3: Cargar el documento con las opciones configuradas  

Ahora finalmente cargamos el documento en memoria, usando el `LoadOptions` que acabamos de preparar.

```csharp
// 4️⃣ Load the DOCX. Any warnings will flow through FontWarningHandler.
Document doc = new Document(@"C:\Docs\input.docx", loadOptions);

// Quick sanity check – render the first page to PDF (optional).
doc.Save(@"C:\Docs\output.pdf");
Console.WriteLine("Document loaded and saved successfully.");
```

Si el archivo fuente usa una fuente que no está presente en `C:\MyFonts`, verás una salida similar a:

```
[Font Substitution] Font 'OpenSans-Regular' was substituted with 'Arial'.
Document loaded and saved successfully.
```

Esa línea es el resultado de **cómo capturar advertencias** que buscabas.

---

## Paso 4: Ejemplo completo funcional (listo para copiar‑pegar)

A continuación se muestra el programa completo, listo para compilar. Pégalo en un nuevo proyecto de consola y ejecútalo—solo asegúrate de que las rutas apunten a ubicaciones reales en tu máquina.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;
using System;

namespace AsposeWarningDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // -------------------------------------------------
            // Step 1: Prepare LoadOptions with custom FontSettings.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SetFontsFolder(@"C:\MyFonts", recursive: true);

            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = fontSettings,
                // Step 2: Attach the warning callback.
                WarningCallback = new FontWarningHandler()
            };

            // -------------------------------------------------
            // Step 3: Load the document – warnings flow to handler.
            // -------------------------------------------------
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath, loadOptions);

            // Optional: Save as PDF to verify rendering.
            string outputPath = @"C:\Docs\output.pdf";
            doc.Save(outputPath);

            Console.WriteLine("Document processed. Check console for any warning messages.");
        }
    }

    // -------------------------------------------------
    // Warning handler that focuses on missing‑font events.
    // -------------------------------------------------
    public class FontWarningHandler : IWarningCallback
    {
        public void Warn(IWarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"[Font Substitution] {info.Description}");
            }
            // You could add more branches for other warning types.
        }
    }
}
```

**Salida esperada:**  

- Si todas las fuentes están disponibles:  
  `Document processed. Check console for any warning messages.`  

- Si falta una fuente:  
  ```
  [Font Substitution] Font 'Times New Roman' was substituted with 'Arial'.
  Document processed. Check console for any warning messages.
  ```

---

## Paso 5: Variaciones comunes y casos límite  

| Situation | What to Adjust |
|-----------|----------------|
| **Múltiples carpetas de fuentes** | Llama a `fontSettings.AddFontFolder(@"C:\MoreFonts", true);` para cada ubicación adicional. |
| **Suprimir todas las advertencias** | Implementa `Warn` pero deja el cuerpo vacío, o establece `loadOptions.WarningCallback = null;`. |
| **Capturar otros tipos de advertencias** | Comprueba `info.WarningType` contra `WarningType.DeprecatedFeature`, `WarningType.UnexpectedContent`, etc. |
| **Ejecutar en Linux/macOS** | Asegúrate de que la carpeta de fuentes contenga archivos `.ttf`/`.otf` compatibles con Linux; puede que necesites instalar `libfontconfig`. |
| **Documentos grandes** | Considera transmitir el documento (`LoadOptions.LoadFormat = LoadFormat.Docx;`) para reducir la presión de memoria. |

Al anticipar estos escenarios evitarás sorpresas al pasar de una máquina de desarrollo a una canalización CI o a una VM en la nube.

---

## Paso 6: Confirmación visual (opcional)

Si prefieres una pista visual rápida, puedes volcar las advertencias capturadas a un pequeño informe HTML. Aquí tienes un fragmento diminuto que escribe los mensajes en `warnings.html`:

```csharp
using System.IO;
using System.Text;

public class HtmlWarningHandler : IWarningCallback
{
    private readonly StringBuilder _sb = new StringBuilder();

    public void Warn(IWarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            _sb.AppendLine($"<li>{info.Description}</li>");
        }
    }

    public void WriteReport(string path)
    {
        string html = $"<html><body><h2>Font Substitution Warnings</h2><ul>{_sb}</ul></body></html>";
        File.WriteAllText(path, html);
    }
}
```

Después de cargar el documento, llama a `handler.WriteReport(@"C:\Docs\warnings.html");` y ábrelo en un navegador. La imagen a continuación muestra cómo podría verse el informe

![Cómo capturar advertencias captura de pantalla](/images/capture-warnings.png)

*Texto alternativo:* **cómo capturar advertencias** – captura de pantalla de la salida de consola y del informe HTML.

---

## Conclusión  

Hemos cubierto **cómo capturar advertencias** en Aspose.Words, demostrado una forma fiable de **manejar fuentes faltantes**, y mostrado cómo **establecer configuraciones de fuentes personalizadas** para un renderizado determinista. El ejemplo completo está listo para insertarse en cualquier solución .NET, y el módulo `FontWarningHandler` puede ampliarse para adaptarse a tu estrategia de registro o telemetría.

¿Próximos pasos? Prueba a reemplazar las llamadas a `Console.WriteLine` por un registrador estructurado como Serilog, o envía las advertencias a Application Insights para monitoreo en tiempo real. También podrías explorar el patrón `DocumentVisitor` si necesitas inspeccionar el contenido del documento después de cargarlo.

¿Tienes preguntas sobre otros tipos de advertencias o estrategias de incrustación de fuentes? Deja un comentario abajo—¡feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}