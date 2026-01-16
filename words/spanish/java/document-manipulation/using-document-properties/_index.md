---
date: 2026-01-16
description: Aprenda a convertir pulgadas a puntos, leer los metadatos del documento
  en Java, agregar propiedades personalizadas en Java y establecer los márgenes de
  página en Java con Aspose.Words para Java.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Convertir pulgadas a puntos – Usando propiedades del documento en Aspose.Words
  para Java
url: /es/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Convertir pulgadas a puntos – Uso de propiedades de documento en Aspose.Words para Java

En este tutorial descubrirás cómo **convertir pulgadas a puntos** al establecer los márgenes de página, leer metadatos de documento en Java, agregar propiedades personalizadas en Java y trabajar con propiedades de documento incorporadas usando Aspose.Words para Java. Ya sea que estés generando informes, facturas o documentos legales, dominar estas técnicas te brinda un control fino sobre la apariencia y los metadatos de tus archivos Word.

## Quick Answers
- **¿Cómo convierto pulgadas a puntos?** Use `ConvertUtil.inchToPoint(value)` from Aspose.Words.
- **¿Puedo leer metadatos de documento en Java?** Yes – call `doc.getBuiltInDocumentProperties()` or `doc.getCustomDocumentProperties()`.
- **¿Cómo agrego una propiedad personalizada en Java?** Use `doc.getCustomDocumentProperties().add(name, value)`.
- **¿Qué método establece los márgenes de página en puntos?** `PageSetup.setTopMargin`, `setBottomMargin`, etc., accept point values.
- **¿Se admite enlazar a un marcador?** Yes – use `addLinkToContent` on the custom properties collection.

## Introduction to Document Properties

Las propiedades de documento son una parte vital de cualquier archivo Word. Almacenan información como título, autor, asunto, palabras clave y cualquier metadato personalizado que necesites para el procesamiento posterior. En Aspose.Words para Java puedes manipular tanto propiedades incorporadas como personalizadas, y también puedes controlar detalles de diseño como los márgenes convirtiendo unidades de medida (p. ej., **convertir pulgadas a puntos**).

## What is “convert inches to points”?

En Word, las medidas de diseño se expresan en puntos (1 punto = 1/72 de pulgada). Convertir pulgadas a puntos te permite definir márgenes, sangrías y espaciados usando unidades imperiales familiares mientras la API trabaja internamente con puntos.

## Why manage document metadata in Java?

Incorporar metadatos facilita la búsqueda, categorización y automatización de flujos de trabajo. Por ejemplo, podrías etiquetar un contrato con una bandera “Authorized” o almacenar un número de revisión para auditorías. Leer y escribir esta información programáticamente garantiza la consistencia en grandes lotes de documentos.

## Prerequisites
- Java 17+ (or compatible JDK)
- Aspose.Words for Java library added to your project (Maven/Gradle)
- Un archivo `.docx` de ejemplo (p. ej., `Properties.docx`) placed in an accessible directory

## Step‑by‑Step Guide

### Enumerating Built‑in Document Properties
A continuación tienes una prueba sencilla que abre un documento e imprime todas las propiedades incorporadas como Title, Author y Keywords.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Pro tip:** Use this snippet to verify that your metadata was correctly written during earlier steps.

### Adding Custom Document Properties (add custom properties java)
Las propiedades personalizadas te permiten almacenar cualquier tipo de dato que necesites—boolean, string, date, number, etc.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Why this matters:** Adding a flag like **Authorized** can drive downstream approval workflows without altering the document content.

### Removing a Custom Property
Si una propiedad ya no es necesaria, puedes eliminarla de forma limpia.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Configuring a Link to Content (bookmark linking)
Puedes crear un marcador y luego agregar una propiedad personalizada que apunte a ese marcador, habilitando referencias cruzadas dinámicas.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Converting Between Measurement Units (set page margins java)
Aquí es donde brilla la palabra clave principal. Establecemos los márgenes en pulgadas y luego **convertir pulgadas a puntos** usando `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Note:** `ConvertUtil` also provides `pointToInch`, `mmToPoint`, etc., for flexible layout handling.

### Using Control Characters (read document metadata java)
Los caracteres de control te ayudan a limpiar flujos de texto. Este ejemplo reemplaza un retorno de carro (`\r`) con la secuencia de salto de línea de Windows (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Common Issues & Solutions
| Issue | Cause | Fix |
|-------|-------|-----|
| Los márgenes se ven incorrectos después de la conversión | Uso de unidad incorrecta (p.ej., cm en lugar de pulgadas) | Verifique que llame a `ConvertUtil.inchToPoint` para valores en pulgadas |
| La propiedad personalizada no aparece | Propiedad añadida después de guardar el documento | Llame a `doc.save(...)` después de agregar propiedades |
| Enlace de marcador roto | Error tipográfico en el nombre del marcador | Asegúrese de que el nombre del marcador coincida exactamente en `addLinkToContent` |

## FAQ's

### How do I access built-in document properties?

Para acceder a las propiedades de documento incorporadas en Aspose.Words para Java, puedes usar el método `getBuiltInDocumentProperties` del objeto `Document`. Este método devuelve una colección de propiedades incorporadas que puedes iterar.

### Can I add custom document properties to a document?

Sí, puedes agregar propiedades de documento personalizadas a un documento usando la colección `CustomDocumentProperties`. Puedes definir propiedades personalizadas con varios tipos de datos, incluidos strings, booleans, dates y valores numéricos.

### How can I remove a specific custom document property?

Para eliminar una propiedad de documento personalizada específica, puedes usar el método `remove` de la colección `CustomDocumentProperties`, pasando el nombre de la propiedad que deseas eliminar como parámetro.

### What is the purpose of linking to content within a document?

Enlazar a contenido dentro de un documento permite crear referencias dinámicas a partes específicas del documento. Esto puede ser útil para crear documentos interactivos o referencias cruzadas entre secciones.

### How can I convert between different measurement units in Aspose.Words for Java?

Puedes convertir entre diferentes unidades de medida en Aspose.Words para Java usando la clase `ConvertUtil`. Proporciona métodos para convertir unidades como inches to points, points to centimeters, y más.

## Frequently Asked Questions

**Q: How do I read document metadata Java without loading the whole file?**  
A: Use `DocumentInfo` to retrieve core properties without fully loading the document content.

**Q: Can I set page margins Java programmatically for existing documents?**  
A: Yes—open the document, modify `PageSetup` margins (convert inches to points if needed), and save.

**Q: Is it possible to export custom properties to PDF metadata?**  
A: When saving to PDF, Aspose.Words automatically maps custom document properties to PDF custom metadata.

**Q: Do control characters affect PDF conversion?**  
A: They are preserved during conversion; however, you may want to normalize line endings for consistency.

**Q: Which Aspose.Words version is required for `ConvertUtil`?**  
A: `ConvertUtil` has been available since Aspose.Words 16.5; any recent version supports it.

## Conclusion

Al dominar **convertir pulgadas a puntos**, leer metadatos de documento en Java y agregar propiedades personalizadas en Java, obtienes control total sobre tanto el diseño visual como los datos ocultos de tus archivos Word. Estas capacidades te permiten construir pipelines de documentos automatizados, garantizar el cumplimiento y crear informes con formato rico, todo con Aspose.Words para Java.

---

**Last Updated:** 2026-01-16  
**Tested With:** Aspose.Words for Java 24.11  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}