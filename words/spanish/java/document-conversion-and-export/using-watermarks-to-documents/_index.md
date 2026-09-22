---
date: 2026-02-19
description: Aprenda cómo crear un documento con marca de agua usando Aspose.Words
  para Java y agregar una marca de agua de imagen en Java para documentos de aspecto
  profesional.
linktitle: Using Watermarks to Documents
second_title: Aspose.Words Java Document Processing API
title: Crear documento con marca de agua usando Aspose.Words para Java
url: /es/java/document-conversion-and-export/using-watermarks-to-documents/
weight: 15
---

, ensure proper RTL formatting if needed" - not needed.

Now produce final answer.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento con marca de agua usando Aspose.Words para Java

En este tutorial **crearás documento con marca de agua** usando la API de Aspose.Words para Java. Las marcas de agua—ya sean de texto o de imágenes—te ayudan a etiquetar un archivo como confidencial, borrador o aprobado, y pueden aplicarse programáticamente a cualquier documento Word. Recorreremos la configuración de la biblioteca, la adición de marcas de agua de texto e imagen, la personalización de su apariencia e incluso su eliminación cuando ya no sean necesarias.

## Respuestas rápidas
- **¿Qué hace una marca de agua?** Superpone texto o una imagen en cada página para transmitir estado o marca.  
- **¿Qué biblioteca agrega marcas de agua en Java?** Aspose.Words for Java proporciona soporte integrado para marcas de agua.  
- **¿Puedo agregar una marca de agua de imagen?** Sí—utilice la clase `Shape` y el enfoque `add image watermark java`.  
- **¿La marca de agua es semitransparente?** Puede controlar la opacidad mediante `setSemitransparent` para marcas de agua de texto.  
- **¿Necesito una licencia?** Una prueba gratuita funciona para pruebas; se requiere una licencia comercial para producción.

## Qué es una marca de agua y por qué usarla?

Una marca de agua es una superposición tenue—textual o gráfica—añadida a cada página de un documento. Se usa comúnmente para indicar **confidencialidad**, **estado de borrador** o **marca** sin alterar el contenido subyacente. Añadir marcas de agua programáticamente garantiza consistencia en grandes lotes de archivos y ahorra tiempo comparado con la edición manual.

## Configuración de Aspose.Words para Java

Antes de comenzar a agregar marcas de agua, asegúrese de que la biblioteca esté lista en su proyecto:

1. Descargue Aspose.Words for Java desde [aquí](https://releases.aspose.com/words/java/).  
2. Añada el JAR descargado (o la dependencia Maven/Gradle) al classpath de su proyecto.  
3. Importe las clases requeridas en su archivo fuente Java:

```java
import com.aspose.words.*;
import java.awt.Color;
import java.nio.file.*;
```

Ahora que la biblioteca está configurada, vamos a sumergirnos en el código real de la marca de agua.

## Cómo agregar una marca de agua de texto

Las marcas de agua de texto son ideales para etiquetar un documento como “CONFIDENTIAL” o “DRAFT”. El siguiente fragmento muestra una forma limpia de **crear documento con marca de agua** usando `TextWatermarkOptions`.

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

### Personalizando la marca de agua de texto
- **Familia y tamaño de fuente** – cambie `setFontFamily` y `setFontSize`.  
- **Color** – use cualquier `java.awt.Color`.  
- **Diseño** – elija `HORIZONTAL`, `DIAGONAL`, etc.  
- **Transparencia** – active `setSemitransparent(true)` para un aspecto más claro.

## Cómo agregar una marca de agua de imagen (add image watermark java)

Las marcas de agua de imagen son perfectas para logotipos o gráficos personalizados. A continuación se muestra el ejemplo **add image watermark java** que inserta un PNG en el centro de cada página.

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

### Consejos para marcas de agua de imagen
- **Redimensionar** usando `setWidth` / `setHeight` para ajustar a la página.  
- **Posición** puede estar centrada o alineada a cualquier margen usando `RelativeHorizontalPosition` / `RelativeVerticalPosition`.  
- **Transparencia** puede aplicarse ajustando el canal alfa de la imagen antes de cargarla.

## Cómo eliminar marcas de agua

Cuando un documento ya no necesita una marca de agua, puede eliminarla programáticamente. El código a continuación recorre todas las formas y elimina cualquier que contenga “Watermark” en su nombre.

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

## Problemas comunes y solución de errores

- **Marca de agua ausente después de guardar** – asegúrese de llamar a `doc.save()` después de establecer la marca de agua.  
- **La imagen no aparece** – verifique que la ruta de la imagen sea correcta y que el archivo sea de un formato compatible (PNG, JPEG, BMP).  
- **Transparencia no aplicada** – `setSemitransparent(true)` solo funciona para marcas de agua de texto; para imágenes, edite el canal alfa del PNG.  
- **Múltiples secciones** – si su documento tiene varias secciones, agregue la marca de agua al cuerpo de cada sección o use `doc.getWatermark().setText(...)` que se aplica globalmente.

## Preguntas frecuentes

**Q: ¿Cómo puedo cambiar la fuente de una marca de agua de texto?**  
A: Modifique la propiedad `setFontFamily` en `TextWatermarkOptions`, por ejemplo, `options.setFontFamily("Times New Roman");`.

**Q: ¿Puedo agregar múltiples marcas de agua a un solo documento?**  
A: Sí. Cree varios objetos `Shape` (para imágenes) o llame a `doc.getWatermark().setText(...)` con diferentes opciones para cada marca de agua.

**Q: ¿Es posible rotar una marca de agua?**  
A: Para marcas de agua de imagen, establezca la rotación en el objeto `Shape` con `watermark.setRotation(angle)`. Para marcas de agua de texto, use la propiedad `setLayout` (p. ej., `WatermarkLayout.DIAGONAL`).

**Q: ¿Cómo puedo hacer una marca de agua semitransparente?**  
A: Establezca `options.setSemitransparent(true)` en `TextWatermarkOptions`. Para imágenes, ajuste la opacidad de la imagen antes de cargarla.

**Q: ¿Puedo agregar marcas de agua a secciones específicas de un documento?**  
A: Sí. Recorra `doc.getSections()` y agregue la marca de agua solo a las secciones deseadas.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Última actualización:** 2026-02-19  
**Probado con:** Aspose.Words for Java 24.12 (latest)  
**Autor:** Aspose