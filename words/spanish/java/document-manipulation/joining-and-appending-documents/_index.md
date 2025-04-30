---
"description": "Aprenda a unir y anexar documentos fácilmente con Aspose.Words para Java. Conserve el formato, administre encabezados, pies de página y más."
"linktitle": "Unir y anexar documentos"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "Unir y anexar documentos en Aspose.Words para Java"
"url": "/es/java/document-manipulation/joining-and-appending-documents/"
"weight": 30
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Unir y anexar documentos en Aspose.Words para Java


## Introducción a la unión y anexión de documentos en Aspose.Words para Java

En este tutorial, exploraremos cómo unir y anexar documentos con la biblioteca Aspose.Words para Java. Aprenderá a combinar varios documentos sin problemas, conservando el formato y la estructura.

## Prerrequisitos

Antes de comenzar, asegúrese de tener la API Aspose.Words para Java configurada en su proyecto Java.

## Opciones de unión de documentos

### Anexión simple

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Añadir con opciones de formato de importación

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

### Añadir a documento en blanco

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document();
dstDoc.removeAllChildren();
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Añadir con conversión de número de página

```java
Document srcDoc = new Document("source.docx");
Document dstDoc = new Document("destination.docx");
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
convertNumPageFieldsToPageRef(dstDoc); // Convertir campos NUMPAGES
dstDoc.updatePageLayout(); // Actualizar el diseño de la página para una numeración correcta
```

## Manejo de diferentes configuraciones de página

Al adjuntar documentos con diferentes configuraciones de página:

```java
srcDoc.getFirstSection().getPageSetup().setSectionStart(SectionStart.CONTINUOUS);
srcDoc.getFirstSection().getPageSetup().setRestartPageNumbering(true);
// Asegúrese de que la configuración de la página coincida con el documento de destino
```

## Unir documentos con diferentes estilos

```java
dstDoc.appendDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES);
```

## Comportamiento de estilo inteligente

```java
ImportFormatOptions options = new ImportFormatOptions();
options.setSmartStyleBehavior(true);
builder.insertDocument(srcDoc, ImportFormatMode.USE_DESTINATION_STYLES, options);
```

## Insertar documentos con DocumentBuilder

```java
DocumentBuilder builder = new DocumentBuilder(dstDoc);
builder.insertDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Mantener la numeración de fuentes

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setKeepSourceNumbering(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Manejo de cuadros de texto

```java
ImportFormatOptions importFormatOptions = new ImportFormatOptions();
importFormatOptions.setIgnoreTextBoxes(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING, importFormatOptions);
```

## Administrar encabezados y pies de página

### Vinculación de encabezados y pies de página

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(true);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

### Desvincular encabezados y pies de página

```java
srcDoc.getFirstSection().getHeadersFooters().linkToPrevious(false);
dstDoc.appendDocument(srcDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
```

## Conclusión

Aspose.Words para Java ofrece herramientas flexibles y potentes para unir y anexar documentos, ya sea para mantener el formato, gestionar diferentes configuraciones de página o administrar encabezados y pies de página. Experimente con estas técnicas para satisfacer sus necesidades específicas de procesamiento de documentos.

## Preguntas frecuentes

### ¿Cómo puedo unir documentos con diferentes estilos sin problemas?

Para unir documentos con diferentes estilos, utilice `ImportFormatMode.USE_DESTINATION_STYLES` Al agregar.

### ¿Puedo conservar la numeración de páginas al adjuntar documentos?

Sí, puede conservar la numeración de páginas utilizando el `convertNumPageFieldsToPageRef` método y actualización del diseño de la página.

### ¿Qué es el comportamiento de estilo inteligente?

El comportamiento de estilo inteligente ayuda a mantener estilos consistentes al anexar documentos. Úselo con `ImportFormatOptions` para obtener mejores resultados.

### ¿Cómo puedo manejar cuadros de texto al adjuntar documentos?

Colocar `importFormatOptions.setIgnoreTextBoxes(false)` para incluir cuadros de texto durante la adición.

### ¿Qué pasa si quiero vincular o desvincular encabezados y pies de página entre documentos?

Puede vincular encabezados y pies de página con `linkToPrevious(true)` o desvincularlos con `linkToPrevious(false)` según sea necesario.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}