---
category: general
date: 2026-11-25
description: Aprende cómo crear un documento de Word, agregar una forma de rectángulo,
  resumir el documento con IA, traducir texto usando IA y guardar el documento como
  DOCX usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- summarize document with ai
- save document as docx
- translate text using ai
language: es
lastmod: 2026-11-25
og_description: Crea un documento de Word, agrega una forma de rectángulo, resume
  el documento con IA, traduce el texto usando IA y guarda el documento como DOCX,
  todo en un solo tutorial de C#.
og_image_alt: Screenshot showing a generated Word document with a rectangle shape
  and AI‑generated summary
og_title: Crear un documento de Word con formas, resumen de IA y traducción en C#
schemas:
- author: Aspose
  dateModified: '2026-11-25'
  description: Learn how to create a Word document, add rectangle shape, summarize
    document with AI, translate text using AI, and save document as DOCX using Aspose.Words.
  headline: How to create a Word document with shapes, AI summarization, and translation
    in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- AI integration
title: Cómo crear un documento de Word con formas, resumen con IA y traducción en
  C#
url: /es/net/ai-powered-document-processing/how-to-create-a-word-document-with-shapes-ai-summarization-a/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento Word con formas, resumen con IA y traducción en C#

Si necesitas **crear un documento Word** de forma programática, esta guía te muestra exactamente cómo. Usando Aspose.Words para .NET aprenderás a **añadir una forma rectangular**, invocar un servicio de IA para **resumir el documento con IA**, traducir un párrafo con **traducir texto usando IA**, y finalmente **guardar el documento como DOCX**.

Muchos desarrolladores tienen dificultades para combinar la automatización de documentos con las funciones modernas de IA. Al final de este tutorial tendrás un proyecto C# único y autocontenido que genera un archivo *.docx* completamente formateado, con una forma visual, un resumen generado por IA y contenido multilingüe.

## Requisitos previos

- .NET 6.0 SDK o posterior instalado  
- Visual Studio 2022 (o cualquier IDE de C#)  
- Una licencia de Aspose.Words para .NET (o una clave de evaluación gratuita)  
- Acceso a Internet para las llamadas de resumen y traducción con IA  

No se requieren paquetes NuGet adicionales más allá de `Aspose.Words` y `Aspose.Words.AI`.

## Paso 1: Configurar el proyecto y agregar los paquetes requeridos

Crea un nuevo proyecto de consola y agrega las bibliotecas de Aspose.Words.

```bash
dotnet new console -n WordAiDemo
cd WordAiDemo
dotnet add package Aspose.Words
dotnet add package Aspose.Words.AI
```

> **Consejo profesional:** Si planeas usar el modo de evaluación, llama a `Aspose.Words.License.SetLicense("Aspose.Words.lic");` al inicio de `Main` para evitar marcas de agua.

## Paso 2: Inicializar el documento – el núcleo de **create word document**

La primera línea de código ejecutable crea un nuevo objeto **Word document**. Este objeto es el lienzo para todas las operaciones posteriores.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // Create a new, empty Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

El `DocumentBuilder` simplifica la inserción de texto, formas y controles sin manejar manualmente los árboles de nodos de bajo nivel.

## Paso 3: **Add rectangle shape** al documento

Una forma rectangular puede usarse como marcador visual, fondo de etiqueta o gráfico simple. Primero creamos un `GroupShape`, luego insertamos un `Rectangle` dentro de él.

```csharp
        // Step 3: Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50); // width=100pt, height=50pt
```

El rectángulo tiene 100 puntos de ancho y 50 puntos de alto. Como está dentro de un `GroupShape`, puedes agregar más elementos más adelante (p. ej., cuadros de texto) sin preocuparte por colisiones de diseño.

## Paso 4: Insertar un StructuredDocumentTag (SDT) de texto plano

Los objetos StructuredDocumentTag son útiles para controles de contenido que pueden enlazarse a fuentes de datos más adelante.

```csharp
        // Step 4: Add a plain‑text StructuredDocumentTag (SDT) to the document
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);
```

El indicador `true` marca la etiqueta como un control **repeating**, lo cual es útil para plantillas.

## Paso 5: Agregar un control ActiveX CommandButton (interfaz opcional)

Si el documento generado se usará en un entorno que soporta ActiveX, puedes incrustar un botón.

```csharp
        // Step 5: Insert an ActiveX CommandButton control (Forms2 OLE control)
        builder.InsertForms2OleControl(OleControlType.CommandButton);
```

Este paso es opcional; puedes eliminarlo si tu público objetivo nunca interactúa con el documento en un entorno Windows.

## Paso 6: **Summarize document with AI**

Aspose.Words.AI ofrece un contenedor conveniente alrededor de los servicios de modelos de lenguaje extensos. Aquí llamamos a `DocumentSummarizer.Summarize` con el backend de OpenAI.

```csharp
        // Step 6: Summarize the document content using an AI service
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);
```

El método analiza el árbol de nodos actual, extrae las frases más relevantes y devuelve un párrafo conciso. Este es el núcleo de la funcionalidad **summarize document with AI**.

## Paso 7: **Translate text using AI**

A continuación demostramos cómo traducir una cadena de ejemplo del inglés al francés. El método `Translator.Translate` llama internamente a un modelo de IA de Google.

```csharp
        // Step 7: Translate a sample paragraph to French using Google AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);
```

Puedes reemplazar `Language.French` por cualquier valor de enumeración de idioma soportado, habilitando la generación multilingüe de documentos al instante.

## Paso 8: **Save document as DOCX**

Finalmente, guarda el documento editado en disco. El método `Save` escribe automáticamente un archivo *.docx* cuando especificas la extensión `.docx`.

```csharp
        // Step 8: Save the modified document
        document.Save("Result.docx"); // **save document as docx**
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

El archivo `Result.docx` ahora contiene:

- Una forma rectangular dentro de un group shape  
- Un control de contenido de texto plano (SDT)  
- Un ActiveX CommandButton (si mantuviste el Paso 5)  
- Un párrafo de resumen generado por IA  
- Una traducción al francés de “Hello world”

Puedes abrir el archivo en Microsoft Word para verificar cada elemento.

## Código fuente completo

A continuación se muestra el programa completo, listo para ejecutar. Cópialo en `Program.cs` y ejecuta `dotnet run`.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.AI;          // AI‑powered features
using Aspose.Words.Charts;     // chart‑related properties
using System;

class Program
{
    static void Main()
    {
        // 1. Create a new Word document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert a group shape and add a rectangle inside it
        GroupShape groupShape = new GroupShape(document);
        builder.InsertNode(groupShape);
        builder.MoveTo(groupShape);
        builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3. Add a plain‑text StructuredDocumentTag (SDT)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(document, SdtType.PlainText, true);
        builder.InsertNode(plainTextTag);

        // 4. Insert an ActiveX CommandButton (optional)
        builder.InsertForms2OleControl(OleControlType.CommandButton);

        // 5. Summarize the document using AI
        string summary = DocumentSummarizer.Summarize(document, SummarizerOptions.OpenAI);
        Console.WriteLine("Document summary:");
        Console.WriteLine(summary);

        // 6. Translate a paragraph to French using AI
        string translatedParagraph = Translator.Translate("Hello world", Language.French);
        Console.WriteLine("\nTranslated paragraph (English → French):");
        Console.WriteLine(translatedParagraph);

        // 7. Save the document as DOCX
        document.Save("Result.docx");
        Console.WriteLine("\nDocument saved as Result.docx");
    }
}
```

### Salida esperada

```
Document summary:
[AI‑generated concise summary of the document’s current content]

Translated paragraph (English → French):
Bonjour le monde

Document saved as Result.docx
```

Al abrir `Result.docx`, verás la forma rectangular cerca de la parte superior, el marcador de posición SDT, el botón, el párrafo de resumen y la traducción al francés insertada como texto plano.

## Conclusión

Ahora sabes cómo **crear un documento Word** desde cero, **añadir una forma rectangular**, **resumir el documento con IA**, **traducir texto usando IA**, y **guardar el documento como DOCX**—todo con unas pocas líneas concisas de C#. Este patrón escala: puedes reemplazar las cadenas codificadas por datos dinámicos, agregar más formas o gráficos, y cambiar el proveedor de IA ajustando los parámetros `SummarizerOptions` o `Translator`.

### ¿Qué sigue?

- Explora variaciones de **add rectangle shape**: cambia el color de relleno, el estilo de línea o agrega texto dentro de la forma.  
- Utiliza **summarize document with AI** en documentos más grandes para generar resúmenes ejecutivos automáticamente.  
- Amplía **translate text using AI** para procesar por lotes párrafos o tablas completas para informes multilingües.  
- Combina las APIs de gráficos de Aspose.Words para incrustar visualizaciones de datos junto a los insights generados por IA.  

¡Siéntete libre de experimentar y compartir tus resultados en los comentarios o en GitHub. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear un documento Word en blanco y agregar una forma rectangular](/words/english/net/programming-with-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/)
- [Crear Group Shape en un documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Agregar marca de agua de texto en un documento Word usando Aspose.Words para .NET](/words/english/net/working-with-watermark/add-text-watermark/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}