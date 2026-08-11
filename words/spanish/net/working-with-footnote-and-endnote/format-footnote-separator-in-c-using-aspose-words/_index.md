---
category: general
date: 2026-08-10
description: Formatea el separador de notas al pie en C# con Aspose.Words para personalizar
  las líneas de notas al pie y notas finales. Aprende el formato de notas al pie en
  C# en minutos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: es
lastmod: 2026-08-10
og_description: Formatea el separador de notas al pie en C# usando Aspose.Words. Sigue
  este tutorial para dar estilo a los separadores de notas al pie y notas finales
  de forma rápida y fiable.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Formatear separador de notas al pie en C# – guía completa de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formatear el separador de notas al pie en C# usando Aspose.Words
url: /es/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formatear el separador de notas al pie en C# con Aspose.Words

Si necesitas **formatear el separador de notas al pie** en un documento Word, esta guía te muestra cómo hacerlo con Aspose.Words para .NET. Verás un ejemplo completo y ejecutable que cambia la alineación y el color del párrafo separador, y aprenderás a aplicar la misma técnica a los separadores de notas finales.

El tutorial cubre cada paso, desde cargar el archivo de origen hasta guardar el documento modificado, para que puedas copiar‑pegar el código en tu propio proyecto sin necesidad de investigar más.

## Lo que necesitarás

Antes de comenzar, asegúrate de tener:

* .NET 6.0 o posterior (el código también funciona con .NET Framework 4.6+)
* Una licencia válida de Aspose.Words para .NET (la prueba gratuita sirve para evaluación)
* Un archivo Word que contenga al menos una nota al pie o una nota final (por ejemplo, `Footnotes.docx`)
* Visual Studio 2022 o cualquier IDE de C# que prefieras

Tener estos elementos listos te permite centrarte en la lógica de **formateo de notas al pie en C#** en lugar de la configuración del entorno.

## Paso 1: Cargar el documento que contiene notas al pie y notas finales

La primera operación es crear un objeto `Document` que apunte a tu archivo de origen. Aspose.Words lee todo el paquete DOCX en memoria, dándote acceso completo a los nodos de notas al pie y notas finales.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Por qué es importante*: Cargar el documento es un requisito previo para cualquier manipulación. Si la ruta del archivo es incorrecta, Aspose.Words lanza una `FileNotFoundException`, así que verifica la ruta antes de continuar.

## Paso 2: Obtener los nodos de separador y separador de continuación

Los separadores de notas al pie y notas finales se almacenan como nodos especiales dentro de las colecciones `Footnotes` y `Endnotes`. Cada colección expone las propiedades `Separator` y `ContinuationSeparator` que devuelven una referencia a un `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Por qué es importante*: El nodo `Separator` representa la línea que separa visualmente el texto principal del bloque de notas al pie. Al obtener una referencia, puedes modificar su formato de párrafo, fuente o incluso reemplazar el nodo por completo.

## Paso 3: Cambiar el estilo visual del separador de notas al pie

En la mayoría de los documentos Word, el separador es un solo párrafo que contiene un guion o un asterisco. El código a continuación verifica si el separador es un `Paragraph` y, de ser así, lo centra y cambia su color de texto a gris.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Estilizando el separador de continuación (opcional)

El separador de continuación aparece cuando una nota al pie abarca varias páginas. Puedes estilizarlo de forma similar:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Por qué es importante*: Alinear el separador mejora la legibilidad, y cambiar el color lo diferencia del texto de párrafo normal. Puedes reemplazar `ParagraphAlignment.Center` por `Left` o `Right` para ajustarlo a las directrices de diseño de tu documento.

## Paso 4: Guardar el documento modificado

Después de aplicar el estilo deseado, escribe el documento de nuevo en disco. Puedes sobrescribir el archivo original o crear una nueva versión.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Cuando abras `Footnotes_Styled.docx` en Microsoft Word, el separador de notas al pie aparecerá centrado y gris, exactamente como lo especifica el código.

## Variaciones avanzadas

### Formatear el separador de notas finales

Si tu documento también usa notas finales, puedes aplicar la misma lógica a la colección `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Usar una cadena personalizada para el separador

A veces deseas que el separador sea una serie de asteriscos (`***`). Reemplaza los `Run` existentes con uno nuevo:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Manejar documentos sin nodo separador

Un caso raro es un documento que omite el nodo separador (por ejemplo, cuando el autor lo eliminó). En ese escenario `document.Footnotes.Separator` devuelve `null`. Protege tu código contra ello:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **El separador no es un `Paragraph`** | Algunas plantillas Word usan una `Table` o `Shape` como separador. | Verifica el tipo de nodo con `is Paragraph` antes de hacer cast. |
| **La colección `Runs` está vacía** | El separador puede ser un párrafo vacío. | Comprueba `Runs.Count > 0` antes de acceder a `Runs[0]`. |
| **Licencia no aplicada** | Sin una licencia, Aspose.Words inserta una marca de agua y puede limitar el uso de la API. | Llama `License license = new License(); license.SetLicense("Aspose.Words.lic");` al inicio de tu programa. |
| **Guardado en una carpeta de solo lectura** | El método `Save` lanza una `UnauthorizedAccessException`. | Asegúrate de que el directorio de destino tenga permisos de escritura. |

Abordar estos problemas desde el principio evita excepciones en tiempo de ejecución y garantiza una experiencia fluida al **modificar el separador de notas al pie**.

## Ejemplo completo y ejecutable

A continuación tienes una aplicación de consola autocontenida que demuestra cada paso descrito. Copia el código en un nuevo proyecto de consola .NET, reemplaza las rutas de archivo y ejecútalo.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Resultado esperado**  

Al abrir `Footnotes_Styled.docx`:

* La línea del separador de notas al pie está centrada bajo el texto principal.
* Su color aparece como un gris claro, haciéndolo visualmente distintivo.
* Si el documento contiene notas finales, sus separadores también están centrados y coloreados en gris (o pizarra).


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}