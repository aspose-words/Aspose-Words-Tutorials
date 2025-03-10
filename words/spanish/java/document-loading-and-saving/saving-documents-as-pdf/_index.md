---
title: Cómo guardar documentos como PDF en Aspose.Words para Java
linktitle: Guardar documentos como PDF
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a guardar documentos de Word como PDF con Aspose.Words para Java. Personalice fuentes, propiedades y calidad de imagen. Una guía completa para la conversión de archivos PDF.
weight: 22
url: /es/java/document-loading-and-saving/saving-documents-as-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo guardar documentos como PDF en Aspose.Words para Java


## Introducción a cómo guardar documentos como PDF en Aspose.Words para Java

En esta guía paso a paso, exploraremos cómo guardar documentos como PDF con Aspose.Words para Java. Cubriremos varios aspectos de la conversión de PDF y brindaremos ejemplos de código para facilitar el proceso.

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:

- Java Development Kit (JDK) instalado en su sistema.
-  Biblioteca Aspose.Words para Java. Puedes descargarla desde[aquí](https://releases.aspose.com/words/java/).

## Convertir un documento a PDF

Para convertir un documento de Word a PDF, puede utilizar el siguiente fragmento de código:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Reemplazar`"input.docx"` con la ruta a su documento de Word y`"output.pdf"` con la ruta del archivo PDF de salida deseada.

## Controlar las opciones de guardado de PDF

 Puede controlar varias opciones de guardado de PDF utilizando el`PdfSaveOptions` clase. Por ejemplo, puede configurar el título que se mostrará en el documento PDF de la siguiente manera:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDisplayDocTitle(true);
doc.save("output.pdf", saveOptions);
```

## Incrustar fuentes en PDF

Para incrustar fuentes en el PDF generado, utilice el siguiente código:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

## Personalización de las propiedades del documento

Puede personalizar las propiedades del documento en el PDF generado. Por ejemplo:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

## Exportación de la estructura del documento

 Para exportar la estructura del documento, configure el`exportDocumentStructure` Opción a`true`:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setExportDocumentStructure(true);
doc.save("output.pdf", saveOptions);
```

## Compresión de imagen

Puede controlar la compresión de imágenes utilizando el siguiente código:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setImageCompression(PdfImageCompression.JPEG);
doc.save("output.pdf", saveOptions);
```

## Actualizar la última propiedad impresa

Para actualizar la propiedad "Última impresión" en el PDF, utilice:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setUpdateLastPrintedProperty(true);
doc.save("output.pdf", saveOptions);
```

## Representación de efectos 3D DML

Para una representación avanzada de efectos DML 3D, configure el modo de representación:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setDml3DEffectsRenderingMode(Dml3DEffectsRenderingMode.ADVANCED);
doc.save("output.pdf", saveOptions);
```

## Interpolación de imágenes

Puede habilitar la interpolación de imágenes para mejorar la calidad de la imagen:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setInterpolateImages(true);
doc.save("output.pdf", saveOptions);
```

## Conclusión

Aspose.Words para Java ofrece funciones integrales para convertir documentos de Word a formato PDF con flexibilidad y opciones de personalización. Puede controlar varios aspectos de la salida PDF, incluidas las fuentes, las propiedades del documento, la compresión de imágenes y más.

## Preguntas frecuentes

### ¿Cómo convierto un documento de Word a PDF usando Aspose.Words para Java?

Para convertir un documento de Word a PDF, utilice el siguiente código:

```java
Document doc = new Document("input.docx");
PdfSaveOptions saveOptions = new PdfSaveOptions();
doc.save("output.pdf", saveOptions);
```

 Reemplazar`"input.docx"` con la ruta a su documento de Word y`"output.pdf"` con la ruta del archivo PDF de salida deseada.

### ¿Puedo incrustar fuentes en el PDF generado por Aspose.Words para Java?

 Sí, puedes incrustar fuentes en el PDF configurando la`setEmbedFullFonts` Opción a`true` en`PdfSaveOptions`He aquí un ejemplo:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setEmbedFullFonts(true);
doc.save("output.pdf", saveOptions);
```

### ¿Cómo puedo personalizar las propiedades del documento en el PDF generado?

 Puede personalizar las propiedades del documento en el PDF utilizando el`setCustomPropertiesExport` Opción en`PdfSaveOptions`. Por ejemplo:

```java
PdfSaveOptions saveOptions = new PdfSaveOptions();
saveOptions.setCustomPropertiesExport(PdfCustomPropertiesExport.STANDARD);
doc.save("output.pdf", saveOptions);
```

### ¿Cuál es el propósito de la compresión de imágenes en Aspose.Words para Java?

 La compresión de imágenes le permite controlar la calidad y el tamaño de las imágenes en el PDF generado. Puede configurar el modo de compresión de imágenes utilizando`setImageCompression` en`PdfSaveOptions`.

### ¿Cómo actualizo la propiedad "Última impresión" en el PDF?

 Puede actualizar la propiedad "Última impresión" en el PDF configurando`setUpdateLastPrintedProperty` a`true` en`PdfSaveOptions`Esto reflejará la última fecha de impresión en los metadatos del PDF.

### ¿Cómo puedo mejorar la calidad de la imagen al convertir a PDF?

 Para mejorar la calidad de la imagen, habilite la interpolación de imágenes configurando`setInterpolateImages` a`true` en`PdfSaveOptions`Esto dará como resultado imágenes más fluidas y de mayor calidad en el PDF.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
