---
category: general
date: 2026-10-13
description: Cómo cambiar el separador de notas al pie en un documento de Word usando
  Aspose.Words. Aprende a cambiar el color de fuente en un documento de Word de forma
  programática.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to change footnote separator
- change font color in word document
- style footnote separator programmatically
- Aspose.Words footnote formatting
- C# Word automation
language: es
lastmod: 2026-10-13
og_description: Cómo cambiar el separador de notas al pie en un documento Word con
  Aspose.Words. Este tutorial le muestra cómo cambiar el color de la fuente en un
  documento Word usando C#.
og_image_alt: Screenshot of a Word document showing red footnote separator and blue
  endnote separator
og_title: Cómo cambiar el separador de notas al pie en un documento de Word – guía
  paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  headline: How to change footnote separator and customize its style in a Word document
  type: TechArticle
- description: How to change footnote separator in a Word document using Aspose.Words.
    Learn to change font color in Word document programmatically.
  name: How to change footnote separator and customize its style in a Word document
  steps:
  - name: Why each line matters
    text: '* **Loading the document** (`new Document`) gives you an in‑memory representation
      that Aspose.Words can manipulate. * **`GetChild` with `ParagraphNodeType.FootnoteSeparator`**
      returns the hidden paragraph that Word uses to draw the line separating footnotes
      from the main text. The same method works '
  - name: Expected output
    text: 'When you open `FootnoteSeparatorsStyled.docx` in Microsoft Word:'
  - name: 1. Install Aspose.Words
    text: 'Open a terminal in your project folder and run:'
  - name: 2. Prepare the input file
    text: Place `Footnotes.docx` in a known directory (e.g., `C:\Docs`). Ensure the
      file contains at least one footnote and one endnote so the separator nodes exist.
  - name: 3. Write the C# program
    text: Create a new console project (`dotnet new console -n FootnoteStyler`) and
      replace the generated `Program.cs` with the full code block from the **How to
      change footnote separator** section. Remember to adjust the file paths to match
      your environment.
  - name: 4. Run and verify
    text: 'Execute the program:'
  - name: 5. Extend the solution
    text: '* **Different colors:** Use any `System.Drawing.Color` value, e.g., `Color.FromArgb(255,
      128, 0)` for orange. * **Custom line style:** Instead of changing the color,
      you can modify `ParagraphFormat` properties such as `LineSpacing`, `Shading`,
      or even replace the separator character. * **Multiple do'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- footnotes
- document styling
title: Cómo cambiar el separador de notas al pie y personalizar su estilo en un documento
  de Word
url: /es/net/working-with-footnote-and-endnote/how-to-change-footnote-separator-and-customize-its-style-in/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo cambiar el separador de notas al pie y personalizar su estilo en un documento Word

Si necesitas **how to change footnote separator** en un documento Word, esta guía te brinda una solución completa y lista para ejecutar. Usando Aspose.Words para .NET también puedes **change font color in Word document** en elementos como los separadores de notas al pie y notas finales, haciendo que el archivo final coincida con tu branding o guía de estilo.

Los autores de documentos a menudo preguntan: *¿Por qué el separador de notas al pie predeterminado se ve sencillo y cómo puedo hacerlo destacar?* La respuesta es acceder directamente a los objetos de párrafo del separador, ajustar sus propiedades de fuente y guardar el resultado. Este tutorial te guía paso a paso, desde cargar un archivo .docx hasta guardar la salida con estilo.

Aprenderás a:

* Cargar un archivo Word que ya contiene notas al pie y notas finales.  
* Ubicar los párrafos separadores de notas al pie y notas finales.  
* Cambiar el color de fuente de cada separador (rojo para notas al pie, azul para notas finales).  
* Guardar el documento modificado sin perder ningún contenido existente.

No se requieren herramientas externas más allá de la biblioteca Aspose.Words y un entorno de desarrollo .NET.

## Requisitos previos

* .NET 6.0 SDK o posterior (el código también funciona con .NET Framework 4.7+).  
* Visual Studio 2022, Rider o cualquier editor de C# que prefieras.  
* Paquete NuGet Aspose.Words for .NET (`Aspose.Words`).  
* Un archivo Word de ejemplo (`Footnotes.docx`) que contenga al menos una nota al pie y una nota final.

> **Consejo profesional:** Si no tienes un archivo de ejemplo, crea un nuevo documento Word, inserta una nota al pie (`References → Insert Footnote`) y una nota final (`References → Insert Endnote`). Guárdalo como `Footnotes.docx` en una carpeta que puedas referenciar desde el código.

## Cómo cambiar el separador de notas al pie con Aspose.Words

El núcleo de la tarea es obtener los párrafos especiales que Aspose.Words expone como nodos *separator*. Estos nodos son del tipo `Paragraph` y pueden formatearse como cualquier otro párrafo.

```csharp
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

class FootnoteSeparatorStyler
{
    static void Main()
    {
        // Step 1: Load the source document that already contains footnotes/endnotes.
        Document doc = new Document(@"C:\Docs\Footnotes.docx");

        // Step 2: Get the footnote separator paragraph.
        Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

        // Step 3: Get the endnote separator paragraph.
        Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
            NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

        // Step 4: Change the font color of the footnote separator to red.
        footnoteSeparator.Font.Color = Color.Red;

        // Step 5: Change the font color of the endnote separator to blue.
        endnoteSeparator.Font.Color = Color.Blue;

        // Step 6: Save the modified document.
        doc.Save(@"C:\Docs\FootnoteSeparatorsStyled.docx");
    }
}
```

### Por qué cada línea es importante

* **Loading the document** (`new Document`) te brinda una representación en memoria que Aspose.Words puede manipular.  
* **`GetChild` con `ParagraphNodeType.FootnoteSeparator`** devuelve el párrafo oculto que Word usa para dibujar la línea que separa las notas al pie del texto principal. El mismo método funciona para el separador de notas finales.  
* **Changing `Font.Color`** afecta directamente la apariencia de la línea porque Word representa el separador como un párrafo con un solo carácter “‑”. Establecer el color a `Color.Red` (o cualquier `System.Drawing.Color`) actualiza el estilo visual.  
* **Saving** escribe los cambios de vuelta a un archivo .docx que cualquier procesador de Word puede abrir.

### Resultado esperado

Al abrir `FootnoteSeparatorsStyled.docx` en Microsoft Word:

* La línea del separador de notas al pie aparece **roja**.  
* La línea del separador de notas finales aparece **azul**.  

Todo el contenido original de notas al pie y notas finales permanece sin cambios.

## Cambiar el color de fuente en documentos Word usando C#

La operación demostrada arriba es un caso específico de una capacidad más amplia: **change font color in Word document** programáticamente. Una vez que tienes un `Paragraph`, `Run` o cualquier `Node` que contiene texto, puedes ajustar su propiedad `Font.Color`.

```csharp
// Example: Change the color of all headings (style "Heading 1") to dark green.
foreach (Paragraph para in doc.GetChildNodes(NodeType.Paragraph, true))
{
    if (para.ParagraphFormat.StyleIdentifier == StyleIdentifier.Heading1)
        para.Font.Color = Color.DarkGreen;
}
```

* Este fragmento recorre cada párrafo, verifica si usa el estilo `Heading 1` y establece su color de fuente.  
* Puedes adaptar la condición para apuntar a notas al pie, tablas o cualquier otro tipo de nodo.

## Desglose paso a paso

### 1. Instalar Aspose.Words

Abre una terminal en la carpeta de tu proyecto y ejecuta:

```bash
dotnet add package Aspose.Words
```

### 2. Preparar el archivo de entrada

Coloca `Footnotes.docx` en un directorio conocido (p.ej., `C:\Docs`). Asegúrate de que el archivo contenga al menos una nota al pie y una nota final para que existan los nodos separadores.

### 3. Escribir el programa C#

Crea un nuevo proyecto de consola (`dotnet new console -n FootnoteStyler`) y reemplaza el `Program.cs` generado con el bloque de código completo de la sección **How to change footnote separator**. Recuerda ajustar las rutas de archivo para que coincidan con tu entorno.

### 4. Ejecutar y verificar

Ejecuta el programa:

```bash
dotnet run
```

Después de que la ejecución termine, abre `FootnoteSeparatorsStyled.docx`. Deberías ver las líneas separadoras roja y azul como se describió.

### 5. Extender la solución

* **Different colors:** Usa cualquier valor de `System.Drawing.Color`, por ejemplo, `Color.FromArgb(255, 128, 0)` para naranja.  
* **Custom line style:** En lugar de cambiar el color, puedes modificar propiedades de `ParagraphFormat` como `LineSpacing`, `Shading`, o incluso reemplazar el carácter del separador.  
* **Multiple documents:** Encapsula la lógica en un método que acepte rutas de entrada y salida, y luego llámalo en un bucle para procesamiento por lotes.

## Problemas comunes y cómo evitarlos

| Symptom | Cause | Fix |
|---------|-------|-----|
| `GetChild` returns `null` | El documento fuente no tiene separador de nota al pie/nota final (p. ej., no hay notas al pie). | Agrega al menos una nota al pie o nota final, o verifica que sea `null` antes de acceder a `Font`. |
| Color change not visible | El separador se muestra como una línea en lugar de un carácter en algunas versiones de Word. | Establece `ParagraphFormat.LineSpacingRule = LineSpacingRule.Exactly` y `ParagraphFormat.LineSpacing = 1` para forzar un carácter visible. |
| Runtime exception `FileNotFoundException` | Ruta de archivo incorrecta. | Usa rutas absolutas o `Path.Combine` con `Environment.CurrentDirectory`. |

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que puedes copiar y pegar en una aplicación de consola. Incluye manejo de errores y comentarios que explican cada operación.

```csharp
using System;
using System.Drawing;
using Aspose.Words;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // Paths – update these to match your environment.
            const string inputPath = @"C:\Docs\Footnotes.docx";
            const string outputPath = @"C:\Docs\FootnoteSeparatorsStyled.docx";

            // Load the document.
            Document doc = new Document(inputPath);

            // Retrieve footnote separator.
            Paragraph footnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.FootnoteSeparator, true);

            // Retrieve endnote separator.
            Paragraph endnoteSeparator = (Paragraph)doc.GetChild(
                NodeType.Paragraph, (int)ParagraphNodeType.EndnoteSeparator, true);

            // Guard against missing separators.
            if (footnoteSeparator == null || endnoteSeparator == null)
            {
                Console.WriteLine("The document does not contain footnote or endnote separators.");
                return;
            }

            // Change colors – this is the core of “change font color in word document”.
            footnoteSeparator.Font.Color = Color.Red;   // Footnote separator → red
            endnoteSeparator.Font.Color = Color.Blue; // Endnote separator → blue

            // Save the result.
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Ejecutar este programa genera un archivo Word donde la línea del separador de notas al pie es roja y la línea del separador de notas finales es azul, cumpliendo con el requisito **how to change footnote separator** y también demostrando **change font color in word document**.

## Conclusión

Ahora sabes **how to change footnote separator** en un documento Word usando Aspose.Words para .NET y cómo **change font color in Word document** programáticamente. El enfoque es:

1. Cargar el documento.  
2. Recuperar los párrafos ocultos del separador.  
3. Establecer sus propiedades `Font.Color`.  
4. Guardar el archivo modificado.

A partir de aquí puedes explorar estilos más avanzados—ajustar el grosor de la línea, aplicar diferentes fuentes o automatizar el proceso en muchos archivos. Dominar estas técnicas te brinda un control detallado sobre la apariencia de los documentos Word directamente desde código C#.

---

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Add Page Numbers to the Footer of a Word Document Using Aspose.Words for .NET](/words/english/net/working-with-headers-and-footers/add-page-numbers/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}