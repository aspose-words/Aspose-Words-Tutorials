---
category: general
date: 2026-09-05
description: Aprende cómo crear un grupo de formas en docx, insertar un botón de comando
  ActiveX y cargar Markdown en un documento de Word con un ejemplo completo en C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create group shape docx
- insert activex command button
- load markdown into word document
language: es
lastmod: 2026-09-05
og_description: Crear un documento docx con forma de grupo, insertar un botón de comando
  ActiveX y cargar Markdown en un documento de Word usando C#. Sigue este tutorial
  paso a paso.
og_image_alt: Screenshot of a Word document showing a grouped shape and an ActiveX
  button
og_title: Crear forma de grupo en docx e incrustar controles ActiveX – Guía de C#
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Learn how to create group shape docx, insert ActiveX command button,
    and load Markdown into a Word document with a complete C# example.
  headline: How to create group shape docx and add interactive controls in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document automation
title: Cómo crear un grupo de formas en docx y agregar controles interactivos en C#
url: /es/java/images-shapes/how-to-create-group-shape-docx-and-add-interactive-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear group shape docx y agregar controles interactivos en C#

Si necesitas **create group shape docx** archivos programáticamente, esta guía te muestra exactamente cómo. También verás cómo **insert ActiveX command button** controles y **load Markdown into a Word document** sin perder el formato de subrayado. Al final del tutorial tendrás un `.docx` completamente funcional que combina gráficos vectoriales, elementos UI interactivos y contenido basado en markdown.

Este tutorial asume que tienes un entorno básico de desarrollo en C# y la biblioteca Aspose.Words para .NET instalada. No se requieren herramientas externas; todo se ejecuta dentro de una consola o aplicación de escritorio .NET estándar.

## Requisitos previos

- .NET 6.0 SDK o posterior (el código también funciona con .NET Framework 4.7+)
- Aspose.Words para .NET (paquete NuGet `Aspose.Words`)
- Un certificado X.509 válido (`.pfx`) si deseas probar el paso de firma
- Un archivo de imagen (p. ej., `logo.png`) y un archivo markdown (`sample.md`) ubicados en una carpeta conocida

> **Pro tip:** Mantén todos los archivos de entrada en una única carpeta *resources* para simplificar las rutas relativas.

## Paso 1: Configurar el proyecto e importar espacios de nombres

Crea un nuevo proyecto de consola y agrega las directivas `using` requeridas. Este bloque también muestra cómo referenciar las clases de Aspose.Words que usarás más adelante.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving;
using Aspose.Words.Saving.XpsSaveOptions; // only needed for signing example
using Aspose.Words.Saving.Signature;

// Ensure the license is applied if you have one
// Aspose.Words.License license = new Aspose.Words.License();
// license.SetLicense("Aspose.Words.lic");
```

Las sentencias `using` te dan acceso directo a `Document`, `DocumentBuilder`, `GroupShape`, `Forms2OleControl` y otros tipos utilizados a lo largo del tutorial.

## Paso 2: **Create group shape docx** – agregar una forma agrupada con elementos hijos

Una *group shape* te permite tratar varios objetos de dibujo como una única unidad. Esto es útil para mover o redimensionar gráficos relacionados juntos.

```csharp
// Initialize a new empty document
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a group shape container
GroupShape group = builder.InsertGroupShape();

// Add a rectangle (100 × 50 points) as the first child
Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
group.AppendChild(rect);

// Add an ellipse (80 × 40 points) as the second child
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 40);
group.AppendChild(ellipse);

// Optional: set a fill color for visual distinction
rect.FillColor = System.Drawing.Color.LightBlue;
ellipse.FillColor = System.Drawing.Color.LightCoral;

// Save the intermediate document so you can inspect the group
document.Save("Output/GroupShape.docx");
```

**¿Por qué una group shape?**  
Agrupar mantiene el rectángulo y la elipse alineados cuando el usuario los arrastra en Word. También simplifica operaciones posteriores, como aplicar un borde común o mover todo el gráfico programáticamente.

## Paso 3: Insertar un control de contenido de texto plano (marcador de posición para la entrada del usuario)

Los controles de contenido le dan a los usuarios finales un área estructurada para escribir texto. El texto del marcador de posición desaparece una vez que el usuario comienza a escribir.

```csharp
// Insert a plain‑text StructuredDocumentTag (SDT) after the group shape
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Set a friendly placeholder that appears in the UI
sdt.PlaceholderName = "Enter text here";

// Optionally, lock the content control to prevent deletion
sdt.LockContents = false;
sdt.LockContentControl = false;
```

La propiedad `PlaceholderName` es lo que Word muestra como una pista de color gris claro. Los usuarios pueden reemplazarla con su propio texto, y el XML subyacente sigue estando bien formado.

## Paso 4: **Insert ActiveX command button** – agregar UI interactiva al documento

Los controles ActiveX siguen siendo compatibles en los archivos Word modernos y pueden activar macros o automatizaciones externas. A continuación agregamos un *command button* y establecemos su leyenda.

```csharp
// Insert an ActiveX Forms2OleControl at the current cursor position
Forms2OleControl commandBtn = builder.InsertForms2OleControl();

// Define the control type as a command button
commandBtn.ControlType = Forms2OleControl.ControlType.CommandButton;

// Set the visible caption
commandBtn.Caption = "Click Me";

// Position the button relative to the page (optional)
commandBtn.Left = 150;   // points from the left margin
commandBtn.Top = 300;    // points from the top margin
```

**¿Cuándo usar un botón ActiveX?**  
Si distribuyes el documento dentro de un entorno corporativo que depende de macros VBA, un botón ActiveX puede lanzar una macro o iniciar una aplicación externa. Para interactividad basada puramente en HTML, considera usar *content controls* con *Office.js* en su lugar.

## Paso 5: Insertar una imagen oculta (p. ej., un logotipo) para branding o acceso posterior mediante script

Las formas ocultas no se muestran en el documento impreso pero permanecen en el XML, lo que permite recuperarlas programáticamente más tarde.

```csharp
// Insert an image from disk
Shape logo = builder.InsertImage("Resources/logo.png");

// Hide the image from the view/layout
logo.Hidden = true;

// You can still reference the image via its ShapeId if needed
string logoId = logo.Name;
```

## Paso 6: **Load markdown into a Word document** mientras se preserva el formato de subrayado

Aspose.Words puede importar Markdown directamente. Habilitar `ImportUnderlineFormatting` asegura que los subrayados de markdown (`<u>` o `__texto__`) se conviertan en estilos de subrayado de Word en lugar de texto plano.

```csharp
// Configure markdown load options
MarkdownLoadOptions mdOptions = new MarkdownLoadOptions
{
    ImportUnderlineFormatting = true
};

// Load the markdown file into a new Document instance
Document markdownDoc = new Document("Resources/sample.md", mdOptions);

// Append the markdown content to the main document after the previous elements
builder.MoveToDocumentEnd();
builder.InsertDocument(markdownDoc, ImportFormatMode.KeepSourceFormatting);
```

**Caso límite:** Si el archivo markdown contiene tablas, se convierten automáticamente en tablas de Word. Si necesitas un estilo de tabla personalizado, aplica un `DocumentBuilder` después de la inserción.

## Paso 7: Firmar el documento con XAdES‑EPES (paso de seguridad opcional)

Las firmas digitales garantizan la integridad del documento. El siguiente código firma el archivo **create group shape docx** usando un perfil XAdES‑EPES.

```csharp
// Initialize the signature object for the current document
Signature signature = new Signature(document);

// Choose the XAdES‑EPES level
signature.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;

// Sign using a .pfx certificate (replace path and password)
signature.Sign("Resources/cert.pfx", "password");

// Save the signed document
document.Save("Output/SignedGroupShape.docx");
```

> **Security note:** Mantén la contraseña del certificado fuera del control de versiones. Usa variables de entorno o una bóveda segura en producción.

## Ejemplo completo ejecutable

Al combinar todos los pasos se obtiene un programa único y autocontenido. Guarda el archivo como `Program.cs` y ejecútalo desde la línea de comandos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Loading;
using Aspose.Words.Saving.Signature;

class Program
{
    static void Main()
    {
        // 1️⃣ Create the document and group shape
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        GroupShape group = builder.InsertGroupShape();
        group.AppendChild(builder.InsertShape(ShapeType.Rectangle, 100, 50));
        group.AppendChild(builder.InsertShape(ShapeType.Ellipse, 80, 40));

        // 2️⃣ Add a plain‑text content control
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText, "MyTag");
        sdt.PlaceholderName = "Enter text here";

        // 3️⃣ Insert an ActiveX command button
        Forms2OleControl btn = builder.InsertForms2OleControl();
        btn.ControlType = Forms2OleControl.ControlType.CommandButton;
        btn.Caption = "Click Me";

        // 4️⃣ Insert a hidden logo image
        Shape logo = builder.InsertImage("Resources/logo.png");
        logo.Hidden = true;

        // 5️⃣ Load markdown while keeping underline formatting
        MarkdownLoadOptions mdOpts = new MarkdownLoadOptions
        {
            ImportUnderlineFormatting = true
        };
        Document mdDoc = new Document("Resources/sample.md", mdOpts);
        builder.MoveToDocumentEnd();
        builder.InsertDocument(mdDoc, ImportFormatMode.KeepSourceFormatting);

        // 6️⃣ Sign the document (optional)
        Signature sig = new Signature(doc);
        sig.XmlDsigLevel = XmlDsigLevel.XAdES_EPES;
        sig.Sign("Resources/cert.pfx", "password");

        // Save the final file
        doc.Save("Output/CompleteGroupShape.docx");
        Console.WriteLine("Document created successfully.");
    }
}
```

Ejecutar el programa genera `CompleteGroupShape.docx` que contiene:

- Un rectángulo + elipse agrupados (el núcleo **create group shape docx**)
- Un control de contenido de texto plano con texto de marcador de posición
- Un **insert ActiveX command button** etiquetado “Click Me”
- Una imagen de logotipo oculta
- Contenido markdown con subrayados preservados
- Una firma digital XAdES‑EPES (si se proporciona el certificado)

## Preguntas frecuentes y solución de problemas

| Pregunta | Respuesta |
|---|---|
| **¿Funcionará el botón ActiveX en Word para macOS?** | Word para macOS no soporta controles ActiveX. El botón aparecerá como una imagen estática. Usa content controls con Office.js para interactividad multiplataforma. |
| **¿Qué pasa si el archivo markdown contiene CSS personalizado?** | Aspose.Words ignora CSS; solo se procesa la sintaxis estándar de markdown. Convierte los elementos con estilo CSS a estilos de Word manualmente después de la importación. |
| **¿Puedo agregar más formas al mismo grupo más tarde?** | Sí. Recupera el `GroupShape` por su nombre o índice, luego llama a `AppendChild(newShape)`. Recuerda volver a guardar el documento después de las modificaciones. |
| **¿Cómo cambio el algoritmo de firma?** | Establece `signature.SignatureAlgorithm` antes de llamar a `Sign`. El valor predeterminado es SHA‑256, que cumple con la mayoría de los requisitos de cumplimiento. |
| **¿La imagen oculta es visible en la interfaz de Word?** | No, pero puede mostrarse activando *Show hidden text* en las opciones de Word. Esto es útil para almacenar metadatos sin saturar el diseño. |

## Próximos pasos

Ahora que puedes **create group shape docx**, **insert ActiveX command button** y **load markdown into a Word document**, podrías explorar:

- **Embedding VBA macros** que reaccionen al clic del botón ActiveX.  
- **Applying custom styles** a los párrafos generados a partir de markdown.  
- **Generating PDFs** desde el mismo documento usando `doc.Save("output.pdf", SaveFormat.Pdf)`.  
- **Automating batch processing** de múltiples archivos markdown en un único informe compilado.  

Estas extensiones te permiten construir pipelines de documentos totalmente automatizados que combinan gráficos ricos, controles interactivos y autoría basada en markdown, todo desde C#.

---

*¡Feliz codificación! Si encontraste este tutorial

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create markdown from word – Complete C# Guide](/words/english/java/document-conversion-and-export/create-markdown-from-word-complete-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}