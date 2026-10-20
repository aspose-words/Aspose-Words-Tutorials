---
category: general
date: 2026-08-14
description: Ocultar imagen en Word usando Java. Aprende cómo ocultar una imagen,
  ocultar una foto, establecer la propiedad oculta y ocultar una forma en Word con
  Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- hide picture in word
- how to hide picture
- how to hide image
- set hidden property
- hide shape in word
language: es
lastmod: 2026-08-14
og_description: Ocultar imagen en Word usando Java y Aspose.Words. Este tutorial muestra
  cómo establecer la propiedad oculta en una imagen, ocultar una forma en Word y guardar
  el documento en segundos.
og_image_alt: Screenshot of Java code hiding a picture in a Word document
og_title: Ocultar imagen en Word – guía paso a paso de Java con Aspose
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: Hide picture in Word using Java. Learn how to hide picture, hide image,
    set hidden property, and hide shape in Word with Aspose.Words.
  headline: Hide picture in Word – step‑by‑step Java guide with Aspose
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
title: Ocultar imagen en Word – guía paso a paso en Java con Aspose
url: /es/java/images-shapes/hide-picture-in-word-step-by-step-java-guide-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar imagen en Word – guía paso a paso en Java con Aspose

Si necesitas **ocultar imagen en Word** de forma programática, esta guía muestra la solución completa. Verás cómo localizar una imagen, aplicar la marca de oculto y escribir el archivo actualizado en disco.

Ocultar un gráfico es un requisito común cuando generas informes, creas plantillas o preparas documentos para una revisión de cumplimiento. El ejemplo a continuación demuestra **cómo ocultar imagen** usando Aspose.Words para Java, pero los mismos conceptos se aplican a cualquier biblioteca de procesamiento de Word que exponga el método `setHidden` de una forma.

## Lo que lograrás

Al final de este tutorial podrás:

* Cargar un archivo `.docx` con Aspose.Words.
* Encontrar la primera forma de imagen en el documento.
* **Establecer la propiedad hidden** en esa forma para que no aparezca cuando el archivo se abra en Microsoft Word.
* Guardar el documento modificado sin alterar otro contenido.

El único requisito previo es un entorno de desarrollo Java (JDK 8 o superior) y una licencia válida de Aspose.Words para Java. No se requieren complementos Maven adicionales más allá de la biblioteca principal.

## Ocultar imagen en Word con Aspose.Words

El primer paso es crear un objeto `Document` que represente el archivo fuente. Aspose.Words lee todo el paquete de Word en memoria, lo que facilita recorrer nodos como formas, párrafos y tablas.

```java
// Step 1: Load the Word document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

Crear la instancia `Document` valida el formato del archivo y construye un árbol interno de nodos. Este árbol es la base para todas las operaciones posteriores, incluido **cómo ocultar objetos de imagen**.

## Cómo ocultar imagen usando la propiedad set hidden

Una imagen en un archivo Word se almacena como un nodo `Shape` con `ShapeType.IMAGE`. La biblioteca proporciona el método `setHidden(boolean)` para controlar la visibilidad de la forma. El siguiente fragmento filtra la colección de nodos para localizar la primera forma de imagen.

```java
// Step 2: Locate the first picture shape in the document
Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
        .stream()
        .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
        .findFirst()
        .orElse(null);
```

La llamada `getChildNodes` recorre todo el árbol del documento (`true` habilita la búsqueda profunda). La expresión lambda verifica el `ShapeType` de cada nodo. Este patrón es la forma recomendada de **cómo ocultar imagen** cuando necesitas un control preciso sobre la selección de nodos.

## Cómo ocultar imagen en un documento Word

Una vez identificada la forma objetivo, aplica la marca de oculto. Establecer esta propiedad no elimina la imagen; simplemente indica a Word que trate la forma como oculta durante la renderización.

```java
// Step 3: Hide the picture if it was found
if (picture != null) {
    picture.setHidden(true);
}
```

La llamada `setHidden(true)` se traduce directamente al atributo XML subyacente `w:hidden="true"`. Word respeta este atributo tanto en los editores de escritorio como en los en línea, garantizando que la imagen permanezca invisible para todos los usuarios.

## Ocultar forma en Word – consideraciones adicionales

Aunque el ejemplo oculta solo la primera imagen, puedes ampliar la lógica para procesar múltiples formas:

```java
// Hide all picture shapes
for (Node node : doc.getChildNodes(NodeType.SHAPE, true)) {
    Shape shape = (Shape) node;
    if (shape.getShapeType() == ShapeType.IMAGE) {
        shape.setHidden(true);
    }
}
```

* **Rendimiento** – Recorrer el árbol de nodos es O(n); para documentos muy grandes, considera limitar la búsqueda a secciones específicas.
* **Compatibilidad** – La marca de oculto funciona con Word 2007+ (`.docx`) y Word 97‑2003 (`.doc`).
* **Alternar visibilidad** – Para volver a mostrar una imagen oculta, llama a `shape.setHidden(false)`.

Estos consejos te ayudarán a dominar escenarios de **ocultar forma en Word** más allá del caso básico.

## Guardar el documento modificado

Después de actualizar la marca de oculto, escribe el documento de nuevo en el almacenamiento. Aspose.Words preserva automáticamente todas las demás partes del documento, como estilos, encabezados y pies de página.

```java
// Step 4: Save the modified document
doc.save("YOUR_DIRECTORY/output.docx");
```

El método `save` admite una amplia gama de formatos (PDF, HTML, ODT). En este tutorial mantenemos la salida como un archivo Word para demostrar directamente el efecto de la imagen oculta.

## Ejemplo completo ejecutable

Unir todos los pasos produce un programa autónomo que puedes compilar y ejecutar de inmediato.

```java
import com.aspose.words.*;

public class HidePictureExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Locate the first picture shape in the document
        Shape picture = (Shape) doc.getChildNodes(NodeType.SHAPE, true)
                .stream()
                .filter(node -> ((Shape) node).getShapeType() == ShapeType.IMAGE)
                .findFirst()
                .orElse(null);

        // Hide the picture if it was found
        if (picture != null) {
            picture.setHidden(true);
        }

        // Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Resultado esperado:** Abre `output.docx` en Microsoft Word. La imagen original no se mostrará, pero el resto del documento (texto, tablas, otros gráficos) permanecerá sin cambios. Si inspeccionas el XML (`document.xml`) verás el atributo `w:hidden="true"` en el elemento `<w:pict>` que corresponde a la imagen oculta.

## Conclusión

Ahora sabes cómo **ocultar imagen en Word** usando Java, Aspose.Words y la propiedad `setHidden`. El tutorial cubrió la localización de una forma de imagen, la aplicación de la marca de oculto y la persistencia de los cambios. Con estos fundamentos también puedes **ocultar forma en Word**, procesar múltiples imágenes o alternar la visibilidad según reglas de negocio.

**Próximos pasos**

* Explora **cómo ocultar imagen** de forma condicional basada en metadatos (p. ej., rol de usuario).
* Combina esta técnica con combinación de correspondencia para generar documentos personalizados y respetuosos con la privacidad.
* Revisa la referencia de la API de Aspose.Words para manipulaciones avanzadas de formas, como cambiar la rotación o aplicar marcas de agua.

Siéntete libre de experimentar con variaciones, como ocultar gráficos o objetos SmartArt, y comparte tus hallazgos con la comunidad de desarrolladores. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Hide Chart Axis In A Word Document](/words/english/net/programming-with-charts/hide-chart-axis/)
- [Show Hide Bookmarked Content In Word Document](/words/english/net/programming-with-bookmarks/show-hide-bookmarked-content/)
- [Insert Inline Image in Word Document using Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}