---
category: general
date: 2026-06-02
description: Crear documento compatible con PDF/UA‑2 con Aspose.Words en C#. Tutorial
  paso a paso que cubre la conformidad PDF/UA‑2, PdfSaveOptions y accesibilidad.
draft: false
keywords:
- create pdf/ua-2 compliant document
- Aspose.Words PDF/UA
- C# document conversion
- PDF accessibility
- PdfSaveOptions
language: es
og_description: Aprende a crear documentos compatibles con PDF/UA-2 usando Aspose.Words
  para .NET. Código completo, consejos de cumplimiento y accesibilidad PDF explicados.
og_title: Crear documento compatible con PDF/UA‑2 – Guía completa de C#
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  headline: Create pdf/ua-2 compliant document – Complete C# Guide
  type: TechArticle
- description: create pdf/ua-2 compliant document with Aspose.Words in C#. Step‑by‑step
    tutorial covering PDF/UA‑2 compliance, PdfSaveOptions and accessibility.
  name: Create pdf/ua-2 compliant document – Complete C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code works with .NET Core, .NET Framework 4.7+,
      and .NET 5+). - A licensed copy of **Aspose.Words for .NET** (the free trial
      works for testing). - Basic familiarity with C# and Visual Studio (or your favourite
      IDE).'
  - name: Why These Settings Matter
    text: '- **Compliance = PdfUa2** – This flag adds the *PDF/UA* metadata and logical
      structure tree. - **EmbedFullFonts** – PDF/UA requires that all glyphs used
      in the document are embedded, otherwise a screen reader might miss characters.
      - **ExportDocumentStructure** – Tags the PDF so assistive technologi'
  - name: Quick Validation with the PDF/UA Validator
    text: 1. Download the free **PDF/UA‑2 validator** from the PDF Association (search
      “PDF/UA validator”). 2. Drag `Doc_UA.pdf` onto the validator window. 3. The
      tool will report “No errors” if the document meets the standard.
  - name: Custom Fonts
    text: If your source uses a font that isn’t installed on the server, enable `FontEmbeddingMode
      = FontEmbeddingMode.Always` to force embedding.
  - name: Complex Tables
    text: PDF/UA‑2 requires that tables have proper structure. Ensure every table
      in the Word file has header rows defined (`Table Tools → Layout → Repeat Header
      Rows`). Aspose.Words respects this setting automatically.
  - name: Images Without Alt Text
    text: 'Screen readers rely on alternative text. If an image lacks alt text, Aspose.Words
      will insert an empty description, which may cause a compliance warning. Add
      alt text in Word (`Picture Tools → Alt Text`) or programmatically:'
  type: HowTo
tags:
- PDF
- C#
- Aspose.Words
- Accessibility
title: Crear documento compatible con pdf/ua-2 – Guía completa de C#
url: /es/net/programming-with-pdfsaveoptions/create-pdf-ua-2-compliant-document-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento compatible con pdf/ua-2 – Guía completa de C#

¿Necesita **crear un documento compatible con pdf/ua-2** pero no está seguro por dónde empezar? En este tutorial le guiaremos paso a paso sobre cómo crear un documento compatible con pdf/ua-2 con Aspose.Words para .NET, garantizando la accesibilidad del PDF y el cumplimiento total de PDF/UA‑2.  

Si alguna vez ha lidiado con los requisitos de accesibilidad para PDFs, apreciará la simplicidad del enfoque que cubriremos. Al final, tendrá un fragmento de C# listo para usar, entenderá por qué cada configuración es importante y sabrá cómo verificar que la salida realmente cumpla con el estándar PDF/UA‑2.

## Lo que aprenderá

- Cómo configurar el soporte **Aspose.Words PDF/UA** en un proyecto C#.  
- El papel exacto de **PdfSaveOptions** al apuntar a PDF/UA‑2.  
- Consejos para manejar casos extremos como fuentes personalizadas y tablas complejas.  
- Una forma rápida de validar el archivo generado con validadores gratuitos de PDF/UA.  

### Requisitos previos

- .NET 6.0 o posterior (el código funciona con .NET Core, .NET Framework 4.7+ y .NET 5+).  
- Una copia con licencia de **Aspose.Words for .NET** (la prueba gratuita funciona para pruebas).  
- Familiaridad básica con C# y Visual Studio (o su IDE favorito).  

Si marca esas casillas, sumérjase—no se requieren herramientas adicionales.

![ejemplo de documento compatible con pdf/ua-2](images/pdf-ua2-example.png "ejemplo de documento compatible con pdf/ua-2")

## Paso 1: Instalar Aspose.Words y agregar referencias  

Primero lo primero, necesita la biblioteca Aspose.Words. Abra una terminal en la carpeta de su proyecto y ejecute:

```bash
dotnet add package Aspose.Words
```

Alternativamente, use el Administrador de paquetes NuGet en Visual Studio. Esto incorpora las capacidades **Aspose.Words PDF/UA**, incluida la clase `PdfSaveOptions` de la que dependeremos más adelante.  

> **Consejo profesional:** Si planea distribuir la función de generación de PDF a un cliente, agregue el archivo de licencia (`Aspose.Words.lic`) a su proyecto y llame a `License license = new License(); license.SetLicense("Aspose.Words.lic");` al inicio de `Main()`—esto elimina la marca de agua de evaluación.

## Paso 2: Cargar el documento fuente  

Nuestro objetivo es convertir un archivo Word (`.docx`) en un documento compatible con PDF/UA‑2. La fuente puede ser cualquier documento Word, pero para una auditoría de accesibilidad limpia, comience con un archivo sencillo que incluya encabezados, texto alternativo para imágenes y estructuras de tabla correctas.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

class PdfUaGenerator
{
    static void Main()
    {
        // Load the source .docx file
        Document doc = new Document(@"YOUR_DIRECTORY\input.docx");
        
        // Proceed to configure PDF/UA‑2 options
        SaveAsPdfUa2(doc);
    }
}
```

¿Por qué cargar el documento primero? Aspose.Words analiza el archivo Word en un modelo de objetos, permitiéndonos inspeccionar o modificar el contenido antes de la conversión—útil si necesita inyectar etiquetas de accesibilidad más adelante.

## Paso 3: Configurar PdfSaveOptions para PDF/UA‑2  

La clase **PdfSaveOptions** es donde ocurre la magia. Establecer `Compliance = PdfCompliance.PdfUa2` indica a Aspose.Words que incruste las etiquetas necesarias, los elementos de estructura lógica y que establezca la versión correcta de PDF.

```csharp
static void SaveAsPdfUa2(Document doc)
{
    // Create a new PdfSaveOptions instance
    PdfSaveOptions pdfOptions = new PdfSaveOptions
    {
        // Enforce PDF/UA‑2 compliance
        Compliance = PdfCompliance.PdfUa2,

        // Optional but recommended: embed all fonts to avoid substitution issues
        EmbedFullFonts = true,

        // Ensure the document is tagged (required for PDF/UA)
        ExportDocumentStructure = true,

        // Preserve hyperlinks and bookmarks for better navigation
        ExportHyperlinks = true,
        ExportBookmarks = true
    };

    // Save the PDF/UA‑2 file
    doc.Save(@"YOUR_DIRECTORY\Doc_UA.pdf", pdfOptions);
}
```

### Por qué estos ajustes son importantes  

- **Compliance = PdfUa2** – Esta bandera agrega los metadatos *PDF/UA* y el árbol de estructura lógica.  
- **EmbedFullFonts** – PDF/UA requiere que todos los glifos usados en el documento estén incrustados, de lo contrario un lector de pantalla podría omitir caracteres.  
- **ExportDocumentStructure** – Etiqueta el PDF para que las tecnologías de asistencia puedan interpretar correctamente encabezados, párrafos y tablas.  
- **ExportHyperlinks / ExportBookmarks** – Mejora la navegación para usuarios que dependen de atajos de teclado o atajos de lectores de pantalla.

## Paso 4: Ejecutar el código y verificar la salida  

Compila y ejecuta el proyecto. Si todo está configurado correctamente, encontrará `Doc_UA.pdf` en la carpeta de destino. Ábralo en Adobe Acrobat Reader y revise **File → Properties → Description**—debería ver *PDF/UA‑2* listado bajo el campo “PDF/A”.

### Validación rápida con el validador PDF/UA  

1. Descargue el **validador PDF/UA‑2** gratuito de la PDF Association (busque “PDF/UA validator”).  
2. Arrastre `Doc_UA.pdf` a la ventana del validador.  
3. La herramienta informará “No errors” si el documento cumple con el estándar.  

Si encuentra advertencias sobre etiquetas de idioma faltantes, agregue un atributo de idioma al documento Word (`Review → Language → Set Proofing Language`) antes de la conversión.

## Paso 5: Manejar casos extremos comunes  

### Fuentes personalizadas  

Si su fuente de origen utiliza una tipografía que no está instalada en el servidor, habilite `FontEmbeddingMode = FontEmbeddingMode.Always` para forzar la incrustación.  

```csharp
pdfOptions.FontEmbeddingMode = FontEmbeddingMode.Always;
```

### Tablas complejas  

PDF/UA‑2 requiere que las tablas tengan una estructura adecuada. Asegúrese de que cada tabla en el archivo Word tenga filas de encabezado definidas (`Table Tools → Layout → Repeat Header Rows`). Aspose.Words respeta esta configuración automáticamente.

### Imágenes sin texto alternativo  

Los lectores de pantalla dependen del texto alternativo. Si una imagen carece de texto alternativo, Aspose.Words insertará una descripción vacía, lo que puede generar una advertencia de cumplimiento. Añada texto alternativo en Word (`Picture Tools → Alt Text`) o programáticamente:

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.HasImage && string.IsNullOrEmpty(shape.AlternativeText))
    {
        shape.AlternativeText = "Descriptive text for accessibility";
    }
}
```

## Paso 6: Mejores prácticas para proyectos PDF/UA‑2 continuos  

- **Automatizar la validación**: Integre el validador PDF/UA en su pipeline CI para que cada PDF generado se verifique antes del lanzamiento.  
- **Mantener las bibliotecas actualizadas**: Aspose.Words publica actualizaciones frecuentes que mejoran el soporte PDF/UA—actualice al menos una vez al año.  
- **Documentar su flujo de trabajo**: Guarde una lista de verificación (incrustación de fuentes, texto alternativo, encabezados de tabla) para asegurar que los miembros no técnicos del equipo puedan mantener el cumplimiento.  

---

## Conclusión  

Ahora sabe exactamente cómo **crear un documento compatible con pdf/ua-2** usando C# y Aspose.Words. Configurando `PdfSaveOptions` con las banderas correctas, incrustando fuentes y asegurándose de que su archivo Word de origen siga las mejores prácticas de accesibilidad, puede generar PDFs que superen la validación oficial PDF/UA‑2 sin problemas.  

¿Listo para el próximo desafío? Intente agregar funcionalidades de **accesibilidad PDF** como orden de lectura lógico para diseños de varias columnas, o explore la **conversión de documentos C#** a otros formatos como EPUB manteniendo los mismos metadatos de accesibilidad.  

Si encuentra algún obstáculo, deje un comentario abajo—¡feliz codificación y disfrute creando PDFs inclusivos!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Crear PDF accesible – Guía paso a paso para cumplimiento PDF/UA](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-step-by-step-guide-for-pdf-ua-complian/)
- [Crear PDF accesible en C# – Tutorial de accesibilidad PDF](/words/english/net/programming-with-pdfsaveoptions/create-accessible-pdf-in-c-pdf-accessibility-tutorial/)
- [Convertir Word a PDF en C# usando Aspose.Words – Guía](/words/english/net/basic-conversions/convert-word-to-pdf-in-c-using-aspose-words-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}