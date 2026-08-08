---
category: general
date: 2026-08-07
description: recuperar el separador de notas al pie usando Aspose.Words para .NET.
  Aprende cómo extraer los separadores de notas al pie y notas finales, inspeccionar
  los tipos de nodo y modificarlos en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: es
lastmod: 2026-08-07
og_description: Recuperar el separador de notas al pie con Aspose.Words para .NET.
  Esta guía muestra cómo extraer los separadores de notas al pie y notas finales,
  verificar sus tipos de nodo y guardar los cambios.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: recuperar separador de notas al pie en C# – tutorial paso a paso de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: recuperar separador de notas al pie en C# – guía completa de Aspose.Words
url: /es/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# recuperar separador de nota al pie en C# – guía completa de Aspose.Words

Si necesita **retrieve footnote separator** de un documento Word, este tutorial le muestra exactamente cómo hacerlo con Aspose.Words for .NET. Ya sea que esté construyendo un servicio de procesamiento de documentos o limpiando el formato de notas al pie, verá un ejemplo completo y ejecutable que extrae tanto los separadores de notas al pie como de notas finales.

En esta guía aprenderá cómo cargar un archivo `.docx`, llamar a las propiedades `FootnoteSeparator` y `EndnoteSeparator`, inspeccionar los objetos `Node` devueltos y, opcionalmente, reemplazar la línea del separador. No se requiere documentación externa; todo lo que necesita está incluido a continuación.

## Requisitos previos

* .NET 6.0 o posterior (el código también funciona en .NET Framework 4.7.2)
* Paquete NuGet Aspose.Words for .NET (versión 24.9 o más reciente)
* Un documento Word que contenga notas al pie y/o notas finales (p. ej., `Footnotes.docx`)

Puede agregar el paquete Aspose.Words con el siguiente comando CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Paso 1: Configurar el proyecto e importar espacios de nombres

Cree un nuevo proyecto de consola o agregue el código a uno existente. Las directivas `using` requeridas se enumeran a continuación.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Estos espacios de nombres le dan acceso a la clase `Document`, la jerarquía `Node` y la enumeración `NodeType` necesarias para las operaciones de **retrieve footnote separator**.

## Paso 2: Cargar el documento que contiene notas al pie y notas finales

La primera operación en cualquier flujo de trabajo de Aspose.Words es cargar el archivo fuente. Reemplace la ruta del marcador de posición con la ubicación real de su `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Cargar el archivo prepara el árbol interno de nodos, lo cual es esencial para **retrieve footnote separator** porque los nodos del separador viven dentro de ese árbol.

## Paso 3: Recuperar el nodo del separador de nota al pie

Ahora puede **retrieve footnote separator** accediendo a la propiedad `FootnoteSeparator` del objeto `Document`. Este nodo representa la línea que separa las notas al pie del texto principal.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

El `NodeType` será `Paragraph` para una línea de separador estándar. Conocer el tipo de nodo le ayuda a decidir si necesita modificar el separador o reemplazarlo por completo.

## Paso 4: Recuperar el nodo del separador de nota final

De manera similar, puede **retrieve endnote separator** usando la propiedad `EndnoteSeparator`. Este nodo separa las notas finales del contenido principal.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Ambos nodos separadores comparten el mismo `NodeType` (`Paragraph`) en la mayoría de los documentos, pero pueden personalizarse de forma independiente.

## Paso 5: Inspeccionar o modificar el contenido del separador (opcional)

Si necesita cambiar la apariencia visual del separador —por ejemplo, reemplazar una línea de guiones por una regla delgada— puede editar directamente el nodo `Paragraph`. A continuación se muestra un ejemplo que reemplaza el texto predeterminado del separador por una cadena personalizada.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Después de modificar los nodos, puede guardar el documento para ver los cambios reflejados en Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Salida esperada en la consola

Al ejecutar el programa con el `Footnotes.docx` original, debería ver algo similar a:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Si abre `Footnotes_Updated.docx` en Microsoft Word, los separadores de notas al pie y notas finales mostrarán el texto personalizado que insertó.

## Preguntas comunes y casos límite

**¿Qué pasa si el documento no tiene notas al pie?**  
La propiedad `FootnoteSeparator` sigue devolviendo un nodo `Paragraph` porque Word siempre incluye un marcador de posición para el separador. El nodo estará vacío, por lo que puede agregar contenido de forma segura o dejarlo tal cual.

**¿Puedo recuperar el separador para una sección específica?**  
Los separadores de notas al pie y notas finales son a nivel de documento, no específicos de una sección. Si necesita control a nivel de sección, debe trabajar con `Section.FootnoteOptions` y `Section.EndnoteOptions` en lugar de los nodos separadores globales.

**¿Esto funciona con .NET Core?**  
Sí. Aspose.Words for .NET es multiplataforma, y el mismo código se ejecuta en Windows, Linux y macOS con .NET 6+.

**¿Qué tipo de nodo debería esperar?**  
Tanto `FootnoteSeparator` como `EndnoteSeparator` devuelven un nodo `Paragraph` (`NodeType.Paragraph`). Si encuentra un tipo diferente, el documento puede estar corrupto y debería volver a cargar o validar el archivo fuente.

## Código fuente completo para copiar y pegar rápidamente

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Copie el código en un archivo `Program.cs`, ajuste las rutas de los archivos y ejecute `dotnet run`. El programa demuestra el flujo completo de **retrieve footnote separator**, desde cargar el documento hasta guardar los cambios.

## Conclusión

Ahora sabe cómo **retrieve footnote separator** y **endnote separator retrieval** usando Aspose.Words for .NET, inspeccionar su `document node type` y, opcionalmente, reemplazar su contenido. Esta técnica le permite automatizar el formato de notas al pie, generar líneas de separador personalizadas o validar la estructura del documento en cualquier aplicación C#.

A continuación, podría explorar temas relacionados como **C# footnote extraction** para textos de notas al pie individuales, o aprender a **modify footnote reference marks** usando `FootnoteOptions`. Ambos conceptos se basan directamente en los fundamentos del árbol de nodos cubiertos aquí.

¡Feliz codificación, y siéntase libre de experimentar con diferentes estilos de separador para que coincidan con la identidad de su proyecto!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}