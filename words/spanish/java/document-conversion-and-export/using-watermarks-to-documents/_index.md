---
date: 2025-12-18
description: Aprenda cómo agregar marcas de agua a documentos con Aspose.Words para
  Java, incluido un ejemplo de marca de agua con imagen, cambiar el color de la marca
  de agua, establecer la transparencia de la marca de agua y eliminar la marca de
  agua del documento.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Cómo agregar una marca de agua a documentos usando Aspose.Words para Java
url: /es/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agregar marca de agua a documentos usando Aspose.Words para Java

## Introducción a la adición de marcas de agua a documentos en Aspose.Words para Java

En este tutorial aprenderá **cómo agregar una marca de agua** a documentos Word con Aspose.Words para Java. Las marcas de agua son una forma rápida de etiquetar un archivo como confidencial, borrador o aprobado, y pueden ser basadas en texto o en imagen. Recorreremos la configuración de la biblioteca, la creación de marcas de agua de texto e imagen, la personalización de su apariencia (incluyendo cambiar el color de la marca de agua y establecer la transparencia de la marca de agua), e incluso la eliminación de una marca de agua del documento cuando ya no sea necesaria.

## Respuestas rápidas
- **¿Qué es una marca de agua?** Una superposición semitransparente (texto o imagen) que aparece detrás del contenido principal del documento.  
- **¿Puedo agregar varias marcas de agua?** Sí – cree varios objetos `Shape` y añada cada uno a las secciones deseadas.  
- **¿Cómo cambio el color de la marca de agua?** Ajuste la propiedad `Color` en `TextWatermarkOptions`.  
- **¿Hay un ejemplo de marca de agua de imagen?** Consulte la sección “Agregar marcas de agua de imagen” a continuación.  
- **¿Necesito una licencia para eliminar una marca de agua?** Se requiere una licencia válida de Aspose.Words para uso en producción.

## Configuración de Aspose.Words para Java

Antes de comenzar a agregar marcas de agua a los documentos, necesitamos configurar Aspose.Words para Java. Siga estos pasos para comenzar:

1. Descargue Aspose.Words para Java desde [aquí](https://releases.aspose.com/words/java/).  
2. Añada la biblioteca Aspose.Words para Java a su proyecto Java.  
3. Importe las clases necesarias en su código Java.

Ahora que tenemos la biblioteca configurada, vamos a sumergirnos en la creación real de la marca de agua.

## Agregar marcas de agua de texto

Las marcas de agua de texto son una opción común cuando desea agregar información textual a sus documentos. Aquí se muestra cómo puede agregar una marca de agua de texto usando Aspose.Words para Java:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Define TextWatermarkOptions
TextWatermarkOptions options = new TextWatermarkOptions();
options.setFontFamily("Arial");
options.setFontSize(36f);
options.setColor(Color.BLACK);
options.setLayout(WatermarkLayout.HORIZONTAL);
options.setSemitransparent(false);

// Set the watermark text and options
doc.getWatermark().setText("Test", options);

// Save the document with the watermark
doc.save("DocumentWithWatermark.docx");
```

**Por qué es importante:** Al ajustar `setFontFamily`, `setFontSize` y `setColor` puede **cambiar el color de la marca de agua** para que coincida con su identidad corporativa, y `setSemitransparent(true)` le permite **establecer la transparencia de la marca de agua** para un efecto sutil.

## Agregar marcas de agua de imagen

Además de las marcas de agua de texto, también puede agregar marcas de agua de imagen a sus documentos. A continuación se muestra un **ejemplo de marca de agua de imagen** que demuestra cómo incrustar un logotipo o sello PNG:

```java
// Create a Document instance
Document doc = new Document("Document.docx");

// Load the image for the watermark
byte[] imageBytes = Files.readAllBytes(Paths.get("watermark.png"));
Shape watermark = new Shape(doc, ShapeType.IMAGE);
watermark.getImageData().setImage(imageBytes);

// Set the watermark size and position
watermark.setWidth(200.0);
watermark.setHeight(100.0);
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.CENTER);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.CENTER);

// Add the watermark to the document
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Save the document with the watermark
doc.save("DocumentWithImageWatermark.docx");
```

Puede repetir este bloque con diferentes imágenes o posiciones para **agregar múltiples marcas de agua** a un solo archivo.

## Personalizar marcas de agua

Puede personalizar las marcas de agua ajustando su apariencia y posición. Para marcas de agua de texto, puede cambiar la fuente, el tamaño, el color y el diseño. Para marcas de agua de imagen, puede modificar el tamaño, la rotación y la alineación como se muestra en los ejemplos anteriores.

## Eliminar marcas de agua

Si necesita **eliminar el contenido de la marca de agua del documento**, el siguiente código recorre todas las formas y elimina aquellas identificadas como marcas de agua:

```java
// Create a Document instance
Document doc = new Document("DocumentWithWatermark.docx");

// Remove the watermark
for (Shape shape : doc.getShapes())
{
    if (shape.getName().contains("Watermark"))
    {
        shape.remove();
    }
}

// Save the document without the watermark
doc.save("DocumentWithoutWatermark.docx");
```

## Casos de uso comunes y consejos

- **Borradores confidenciales:** Aplique una marca de agua de texto semitransparente como “CONFIDENTIAL”.  
- **Branding:** Use una marca de agua de imagen que contenga el logotipo de su empresa.  
- **Marcas de agua específicas por sección:** Recorra `doc.getSections()` y agregue una marca de agua solo a las secciones que elija.  
- **Consejo de rendimiento:** Reutilice la misma instancia de `TextWatermarkOptions` al aplicar la misma marca de agua a muchos documentos.

## Preguntas frecuentes

### ¿Cómo puedo cambiar la fuente de una marca de agua de texto?

Para cambiar la fuente de una marca de agua de texto, modifique la propiedad `setFontFamily` en `TextWatermarkOptions`. Por ejemplo:

```java
options.setFontFamily("Times New Roman");
```

### ¿Puedo agregar múltiples marcas de agua a un solo documento?

Sí, puede agregar múltiples marcas de agua a un documento creando varios objetos `Shape` con diferentes configuraciones y añadiéndolos al documento.

### ¿Es posible rotar una marca de agua?

Sí, puede rotar una marca de agua estableciendo la propiedad `setRotation` en el objeto `Shape`. Los valores positivos rotan la marca de agua en sentido horario, y los valores negativos la rotan en sentido antihorario.

### ¿Cómo puedo hacer que una marca de agua sea semitransparente?

Para que una marca de agua sea semitransparente, establezca la propiedad `setSemitransparent` en `true` dentro de `TextWatermarkOptions`.

### ¿Puedo agregar marcas de agua a secciones específicas de un documento?

Sí, puede agregar marcas de agua a secciones específicas de un documento iterando a través de las secciones y añadiendo la marca de agua a las secciones deseadas.

---

**Última actualización:** 2025-12-18  
**Probado con:** Aspose.Words for Java 24.12  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}