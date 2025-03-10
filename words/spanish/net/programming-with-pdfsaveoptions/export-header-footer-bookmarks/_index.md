---
title: Exportar marcadores de encabezado y pie de página de un documento de Word a un documento PDF
linktitle: Exportar marcadores de encabezado y pie de página de un documento de Word a un documento PDF
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a exportar marcadores de encabezado y pie de página de un documento de Word a PDF usando Aspose.Words para .NET con nuestra guía paso a paso.
weight: 10
url: /es/net/programming-with-pdfsaveoptions/export-header-footer-bookmarks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportar marcadores de encabezado y pie de página de un documento de Word a un documento PDF

## Introducción

Convertir documentos de Word a PDF es una tarea habitual, especialmente cuando se quieren compartir o archivar documentos conservando su formato. A veces, estos documentos contienen marcadores importantes en los encabezados y pies de página. En este tutorial, explicaremos el proceso de exportación de estos marcadores desde un documento de Word a un PDF con Aspose.Words para .NET.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

- Aspose.Words para .NET: Necesita tener instalado Aspose.Words para .NET. Puede descargarlo desde[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: configure su entorno de desarrollo. Puede utilizar Visual Studio o cualquier otro entorno de desarrollo integrado (IDE) compatible con .NET.
- Conocimientos básicos de C#: se requiere familiaridad con la programación en C# para seguir los ejemplos de código.

## Importar espacios de nombres

Lo primero es lo primero: debes importar los espacios de nombres necesarios en tu proyecto de C#. Agrega estas líneas en la parte superior de tu archivo de código:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Dividamos el proceso en pasos fáciles de seguir.

## Paso 1: Inicializar el documento

El primer paso es cargar el documento de Word. A continuación, le indicamos cómo hacerlo:

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Bookmarks in headers and footers.docx");
```

En este paso, simplemente especifica la ruta al directorio de su documento y carga el documento de Word.

## Paso 2: Configurar las opciones para guardar PDF

A continuación, debe configurar las opciones de guardado de PDF para garantizar que los marcadores en los encabezados y pies de página se exporten correctamente.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.OutlineOptions.DefaultBookmarksOutlineLevel = 1;
saveOptions.HeaderFooterBookmarksExportMode = HeaderFooterBookmarksExportMode.First;
```

 Aquí estamos configurando el`PdfSaveOptions` . El`DefaultBookmarksOutlineLevel` La propiedad establece el nivel de esquema para los marcadores y la`HeaderFooterBookmarksExportMode` La propiedad garantiza que solo se exporte la primera aparición de marcadores en encabezados y pies de página.

## Paso 3: Guardar el documento como PDF

Por último, guarde su documento como PDF con las opciones configuradas.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.ExportHeaderFooterBookmarks.pdf", saveOptions);
```

En este paso, guardará el documento en la ruta especificada con las opciones que haya configurado.

## Conclusión

¡Y ya está! Siguiendo estos pasos, podrá exportar fácilmente los marcadores de los encabezados y pies de página de un documento de Word a un PDF mediante Aspose.Words para .NET. Este método garantiza que las ayudas de navegación importantes dentro de su documento se conserven en el formato PDF, lo que facilita la navegación de los lectores por el documento.

## Preguntas frecuentes

### ¿Puedo exportar todos los marcadores del documento de Word a PDF?

 Sí, puedes. En el`PdfSaveOptions`, puede ajustar la configuración para incluir todos los marcadores si es necesario.

### ¿Qué pasa si también quiero exportar marcadores del cuerpo del documento?

 Puedes configurar el`OutlineOptions` en`PdfSaveOptions` para incluir marcadores del cuerpo del documento.

### ¿Es posible personalizar los niveles de marcadores en el PDF?

 ¡Por supuesto! Puedes personalizar el`DefaultBookmarksOutlineLevel` Propiedad para establecer diferentes niveles de esquema para sus marcadores.

### ¿Cómo manejo los documentos que no tienen marcadores?

Si su documento no tiene marcadores, el PDF se generará sin ningún contorno de marcador. Asegúrese de que su documento contenga marcadores si los necesita en el PDF.

### ¿Puedo utilizar este método para otros tipos de documentos como DOCX o RTF?

Sí, Aspose.Words para .NET admite varios tipos de documentos, incluidos DOCX, RTF y otros.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
