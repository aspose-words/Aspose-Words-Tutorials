---
category: general
date: 2026-03-14
description: Maneja fuentes faltantes rápidamente con Aspose.Words. Aprende a capturar
  advertencias de sustitución de fuentes, configurar LoadOptions y evitar problemas
  de renderizado.
draft: false
keywords:
- handle missing fonts
- Aspose.Words
- font substitution
- LoadOptions
- DocumentWarnings
- C# document loading
language: es
og_description: Maneje fuentes faltantes en Aspose.Words usando un recopilador de
  advertencias. Este tutorial muestra paso a paso cómo detectar y registrar sustituciones
  de fuentes.
og_title: Manejar fuentes faltantes en Aspose.Words – Guía completa de C#
tags:
- Aspose
- C#
- Fonts
- DocumentProcessing
title: Manejar fuentes faltantes en Aspose.Words – Guía completa en C#
url: /es/net/working-with-fonts/handle-missing-fonts-in-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Manejar fuentes faltantes en Aspose.Words – Guía completa en C#

¿Alguna vez necesitaste **manejar fuentes faltantes** al cargar un documento Word y te preguntaste por qué la salida en PDF o imagen se ve incorrecta? No eres el único. Los archivos de fuentes faltantes son un problema silencioso que puede convertir un informe perfectamente diseñado en un desastre confuso.  

¿La buena noticia? Aspose.Words te ofrece una forma sencilla de capturar esos eventos de sustitución de fuentes, registrarlos e incluso intercambiar una fuente de respaldo si lo deseas. En este tutorial recorreremos un ejemplo completo, listo para ejecutar, que muestra exactamente cómo configurar un colector de advertencias, conectarlo a `LoadOptions` y cargar un documento que pueda contener fuentes faltantes.

Al final de esta guía podrás:

* Detectar cada sustitución de fuente que ocurre durante la carga del documento.  
* Mostrar un mensaje amigable en la consola (o enviarlo a un logger) por cada fuente faltante.  
* Ampliar la solución para reemplazar fuentes, si es necesario.  

**Requisitos previos** – necesitarás:

* .NET 6.0 o posterior (el código funciona también con .NET Core y .NET Framework).  
* El paquete NuGet Aspose.Words for .NET (versión actual 23.11).  
* Un archivo Word que intencionalmente referencia una fuente que no tienes instalada – lo llamaremos `doc-with-missing-font.docx`.  

Si ya estás cómodo con C# y tienes un proyecto configurado, puedes pasar directamente al código. De lo contrario, sigue leyendo; primero cubriremos los pequeños pasos de configuración.

---

## Por qué es importante manejar fuentes faltantes

Cuando Aspose.Words carga un documento, intenta asignar cada glifo a una fuente instalada en la máquina. Si no puede encontrar la fuente exacta, sustituye silenciosamente la más cercana. Esa sustitución puede cambiar la altura de línea, el kerning e incluso hacer que desaparezcan caracteres. Al capturar el evento `WarningType.FontSubstitution` obtienes una visión transparente de **qué** se sustituyó y **por qué**, lo cual es esencial para:

* Mantener la consistencia de la marca (tu fuente corporativa debe aparecer exactamente como está diseñada).  
* Depurar problemas de conversión a PDF—a menudo el culpable es una fuente faltante.  
* Construir pipelines de documentos automatizados donde necesitas marcar archivos problemáticos para revisión manual.

Ahora que el “por qué” está claro, sumergámonos en el **cómo**.

---

## Paso 1 – Configurar el colector de advertencias

Lo primero que necesitamos es un objeto que pueda escuchar las advertencias de Aspose.Words. `DocumentWarnings` implementa `IWarningCallback`, lo que nos permite reaccionar cada vez que la biblioteca genera una advertencia.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Create a collector that will receive warning events.
DocumentWarnings fontWarnings = new DocumentWarnings();

// Subscribe to the Warning event.
fontWarnings.Warning += (sender, e) =>
{
    // We only care about font substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Log the original font name that was missing.
        Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
    }
};
```

**¿Qué está sucediendo?**  
* `DocumentWarnings` es una capa ligera alrededor de la interfaz de callback.  
* La lambda verifica `e.WarningType` para que ignoremos advertencias no relacionadas (como características obsoletas).  
* `e.WarningInfo` contiene el nombre de la fuente faltante, que imprimimos en la consola.  

*Consejo profesional*: Cambia `Console.WriteLine` por un logger estructurado (Serilog, NLog) en producción—de esta forma obtienes marcas de tiempo y niveles de registro sin esfuerzo.

---

## Paso 2 – Conectar el colector a LoadOptions

`LoadOptions` es el guardián de cada documento que abres con Aspose.Words. Al asignar nuestra instancia `fontWarnings` a su propiedad `WarningCallback`, aseguramos que el colector esté activo durante el proceso de carga.

```csharp
// Configure load options to use our warning callback.
LoadOptions loadOptions = new LoadOptions
{
    WarningCallback = fontWarnings
};
```

**¿Por qué usar LoadOptions?**  
Además de las advertencias, `LoadOptions` te permite controlar el manejo de contraseñas, la codificación e incluso la carga de recursos personalizados. Aquí nos enfocamos en el lado de las advertencias, pero el mismo patrón funciona para otros callbacks.

---

## Paso 3 – Cargar el documento con las opciones configuradas

Ahora finalmente cargamos el documento en memoria. Si falta alguna fuente, nuestro colector se activará y verás una línea en la consola por cada sustitución.

```csharp
// Path to the document that may reference missing fonts.
string docPath = Path.Combine(
    Environment.CurrentDirectory,
    "doc-with-missing-font.docx");

// Load the document using the previously configured LoadOptions.
Document document = new Document(docPath, loadOptions);
```

Si ejecutas este fragmento con un documento que referencia, por ejemplo, *Calibri Light* mientras tu máquina de prueba solo tiene *Calibri*, obtendrás una salida similar a:

```
Font 'Calibri Light' was substituted.
```

Ese es todo el bucle de detección—simple, pero poderoso.

---

## Paso 4 – (Opcional) Reemplazar fuentes faltantes con un sustituto conocido

A veces no solo deseas registrar el problema; quieres aplicar una fuente de respaldo para que la salida renderizada sea consistente. Aspose.Words te permite proporcionar un objeto `FontSettings` personalizado que asigna fuentes faltantes a un reemplazo.

```csharp
// Create FontSettings and map any missing font to Arial.
FontSettings fontSettings = new FontSettings();
fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
    "*", // wildcard – applies to any missing font
    new[] { "Arial" } // fallback font(s)
);

// Apply the FontSettings to the document.
document.FontSettings = fontSettings;

// Now re-save the document; all missing fonts will render as Arial.
document.Save("output-with-fallback.pdf");
Console.WriteLine("Document saved with fallback font applied.");
```

**Explicación**  
* El comodín `"*"` indica a Aspose.Words que trate *cualquier* fuente faltante de la misma manera.  
* También puedes mapear fuentes específicas individualmente si necesitas un control más fino.  
* Después de establecer `document.FontSettings`, cualquier renderizado posterior (PDF, imagen, HTML) respeta la sustitución.

---

## Ejemplo completo funcional

A continuación se muestra el programa completo que puedes copiar y pegar en una aplicación de consola. Incluye todas las declaraciones `using` requeridas, manejo de errores y comentarios para mayor claridad.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        try
        {
            // -------------------------------------------------
            // Step 1: Create a warnings collector.
            // -------------------------------------------------
            DocumentWarnings fontWarnings = new DocumentWarnings();
            fontWarnings.Warning += (sender, e) =>
            {
                if (e.WarningType == WarningType.FontSubstitution)
                {
                    Console.WriteLine($"Font '{e.WarningInfo}' was substituted.");
                }
            };

            // -------------------------------------------------
            // Step 2: Attach the collector to LoadOptions.
            // -------------------------------------------------
            LoadOptions loadOptions = new LoadOptions
            {
                WarningCallback = fontWarnings
            };

            // -------------------------------------------------
            // Step 3: Load the document (may contain missing fonts).
            // -------------------------------------------------
            string docPath = Path.Combine(
                Environment.CurrentDirectory,
                "doc-with-missing-font.docx");

            Document doc = new Document(docPath, loadOptions);

            // -------------------------------------------------
            // Step 4 (optional): Apply a fallback font.
            // -------------------------------------------------
            FontSettings fontSettings = new FontSettings();
            fontSettings.SubstitutionSettings.FontSubstitutionTable.AddSubstitutes(
                "*", new[] { "Arial" });

            doc.FontSettings = fontSettings;

            // Save the result to verify the substitution.
            string outPath = Path.Combine(
                Environment.CurrentDirectory,
                "output-with-fallback.pdf");

            doc.Save(outPath);
            Console.WriteLine($"Document saved to '{outPath}'.");
        }
        catch (Exception ex)
        {
            Console.Error.WriteLine($"Error: {ex.Message}");
        }
    }
}
```

**Salida esperada**  

```
Font 'Times New Roman PS' was substituted.
Document saved to 'C:\MyProject\output-with-fallback.pdf'.
```

Si el documento fuente ya contiene todas las fuentes requeridas, la línea de advertencia simplemente no aparecerá—no hay de qué preocuparse.

---

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| **¿Qué pasa si solo quiero registrar, no reemplazar fuentes?** | Omite el bloque `FontSettings` por completo; el colector de advertencias por sí solo es suficiente. |
| **¿Puedo redirigir las advertencias a un archivo?** | Sí—reemplaza `Console.WriteLine` con `File.AppendAllText("font-warnings.log", …)`. |
| **¿Esto funciona para DOC, DOCX y ODT?** | Absolutamente. `LoadOptions` se aplica a todos los formatos compatibles con Aspose.Words. |
| **¿Qué pasa con fuentes personalizadas incrustadas en el documento?** | Las fuentes incrustadas evitan el mecanismo de sustitución; se usan tal cual. |
| **¿Hay un impacto en el rendimiento?** | La sobrecarga es mínima—solo una callback por fuente faltante. Para lotes grandes, considera agregar las advertencias en lugar de escribir por cada evento. |

---

## Conclusión

Hemos demostrado **cómo manejar fuentes faltantes** en Aspose.Words conectando un colector `DocumentWarnings` a `LoadOptions`, opcionalmente intercambiando una fuente de respaldo y guardando el resultado. Este patrón te brinda total visibilidad de los eventos de sustitución de fuentes, ayudándote a mantener la fidelidad visual en conversiones a PDF, imagen o HTML.

Próximos pasos que podrías explorar:

* Integrar el colector de advertencias con un framework de registro centralizado.  
* Construir un panel UI que liste documentos con fuentes faltantes para procesamiento por lotes.  
* Combinar este enfoque con Aspose.PDF para verificar que los PDFs generados realmente usen la fuente de respaldo.  

Siéntete libre de experimentar—cambia `"Arial"` por `"Tahoma"` o carga un conjunto de documentos diferente. La idea central sigue siendo la misma: captura la advertencia, actúa en consecuencia y mantén tus documentos con el aspecto exacto que deseas.

¡Feliz codificación! 🚀

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}