---
category: general
date: 2026-10-20
description: Cómo agrupar formas en Aspose.Words para Java – aprenda a insertar una
  forma rectangular, agruparlas y guardar el documento en una única guía.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- how to insert rectangle
language: es
lastmod: 2026-10-20
og_description: Cómo agrupar formas en Aspose.Words para Java. Este tutorial muestra
  cómo insertar una forma rectangular, agruparlas y exportar el resultado.
og_image_alt: Screenshot of a Word document showing two grouped rectangle shapes created
  with Aspose.Words for Java
og_title: 'Cómo agrupar formas en Aspose.Words para Java: guía paso a paso'
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: How to group shapes in Aspose.Words for Java – learn how to insert
    rectangle shape, group them, and save the document in a single guide.
  headline: How to group shapes in Aspose.Words for Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- shape manipulation
title: Cómo agrupar formas en Aspose.Words para Java
url: /es/java/images-shapes/how-to-group-shapes-in-aspose-words-for-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo agrupar formas en Aspose.Words para Java

Si necesitas **how to group shapes** en un documento Word usando Aspose.Words para Java, esta guía te muestra el flujo de trabajo completo. Aprenderás cómo **insert rectangle shape**, agregar un segundo rectángulo, agrupar las dos formas y, finalmente, guardar el archivo, todo con código claro y ejecutable.

Agrupar formas es útil cuando deseas mover, rotar o aplicar estilo a varios dibujos como una única unidad. Ya sea que estés creando una plantilla de informe, un diagrama o un folleto personalizado, dominar el agrupamiento de formas te ahorra tiempo y mantiene tu diseño consistente.

En este tutorial tú:

* Crear un nuevo `Document` y un `DocumentBuilder`.
* **How to insert rectangle** shapes with precise dimensions.
* Agrupar los rectángulos en un `GroupShape`.
* Guardar el documento y verificar el resultado.

> **Prerequisite** – Debes tener Aspose.Words for Java (v23.12 o posterior) añadido a tu proyecto. Los usuarios de Maven pueden incluir la dependencia mostrada a continuación.

```xml
<!-- Maven dependency -->
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

---

## Lo que necesitarás

| Elemento | Razón |
|----------|-------|
| Java 17+ | Características modernas del lenguaje y mejor rendimiento |
| Aspose.Words for Java | Proporciona las APIs `DocumentBuilder`, `Shape` y `GroupShape` |
| An IDE (IntelliJ IDEA, Eclipse, VS Code, etc.) | Para compilar y ejecutar el ejemplo |
| Write permission to a folder | El documento se guardará en disco |

---

## Cómo insertar una forma de rectángulo

El primer paso es crear un `Document` y un `DocumentBuilder`. El builder te brinda métodos como `insertShape` para colocar objetos de dibujo.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new empty document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert the first rectangle (100 × 50 points).
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        // Optional: give the rectangle a fill color for visibility.
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Step 3: Insert the second rectangle (80 × 40 points).
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // The two rectangles are currently independent objects.
        // Below we will group them together.
```

> **Why this matters** – Usar `insertShape` es la forma estándar **how to insert rectangle** objetos en Aspose.Words. Añade automáticamente la forma al párrafo actual del documento, por lo que no tienes que gestionar OpenXML de bajo nivel.

## Ajustar posiciones del rectángulo (opcional)

Si el segundo rectángulo necesita una ubicación personalizada respecto al primero, puedes modificar sus propiedades `left` y `top`. Este paso es opcional pero a menudo necesario para un diseño de diagrama preciso.

```java
        // Optional: reposition the second rectangle 20 points to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        // Optional: align the top edges.
        rectangle2.setTop(rectangle1.getTop());
```

> **Pro tip:** Todas las medidas están en puntos (1 pt ≈ 1/72 in). Usa `convertPointsToPixels` si necesitas valores en píxeles para cálculos basados en UI.

## Cómo agrupar formas

Ahora que los rectángulos existen, puedes colocarlos dentro de un `GroupShape`. Agrupar hace que los dos rectángulos se comporten como un solo objeto: mover, rotar o formatear el grupo afectará a ambas formas.

```java
        // Step 4: Insert an empty GroupShape.
        GroupShape group = builder.insertGroupShape();

        // Step 5: Add the rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Optional: set a border for the whole group.
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);
```

> **Why grouping works** – `GroupShape` hereda de `Shape`, por lo que puedes tratar el grupo exactamente como cualquier otro objeto de dibujo. Cuando llamas a `appendChild`, las formas se eliminan de su ubicación original y se convierten en hijos del grupo.

## Guardar el documento que contiene las formas agrupadas

Finalmente, escribe el documento en disco. El archivo contendrá un único `GroupShape` con dos rectángulos dentro.

```java
        // Step 6: Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Resultado esperado

Abre `GroupShape.docx` en Microsoft Word:

* Verás dos rectángulos (azul y verde) posicionados lado a lado.
* Seleccionar cualquiera de los rectángulos selecciona todo el grupo—arrastrar mueve ambos juntos.
* El grupo tiene un borde rojo delgado, confirmando que se aplican las propiedades del `GroupShape`.

Si haces clic derecho en el grupo y eliges **Group → Ungroup**, los rectángulos vuelven a ser formas independientes, demostrando que la operación de agrupamiento es reversible.

## Variaciones comunes y casos límite

| Situación | Cómo manejarlo |
|-----------|----------------|
| **More than two shapes** | Inserta cada forma, luego agrega todas al mismo `GroupShape`. |
| **Different shape types** (e.g., ellipse, picture) | Usa `builder.insertShape(ShapeType.ELLIPSE, …)` o `builder.insertImage(...)` antes de agregar. |
| **Scaling the group** | Llama a `group.setWidth(newWidth)` o `group.setHeight(newHeight)`; los hijos se escalan proporcionalmente. |
| **Rotating the group** | `group.setRotationAngle(45);` rota toda la colección alrededor de su centro. |
| **Preserving original positions** | Almacena los `left`/`top` de cada forma antes de agrupar y restáuralos después de desagrupar si es necesario. |

## Ejemplo completo y ejecutable

A continuación se muestra la clase Java completa que puedes copiar y pegar en tu IDE. Incluye todas las importaciones, manejo de errores y comentarios para mayor claridad.

```java
import com.aspose.words.*;

public class GroupShapesDemo {
    public static void main(String[] args) throws Exception {
        // Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert the first rectangle (100 × 50 points) and give it a blue fill.
        Shape rectangle1 = builder.insertShape(ShapeType.RECTANGLE, 100, 50);
        rectangle1.getFill().setForeColor(java.awt.Color.BLUE);

        // Insert the second rectangle (80 × 40 points) with a green fill.
        Shape rectangle2 = builder.insertShape(ShapeType.RECTANGLE, 80, 40);
        rectangle2.getFill().setForeColor(java.awt.Color.GREEN);

        // Optional positioning – move the second rectangle 20 pt to the right.
        rectangle2.setLeft(rectangle1.getLeft() + 20);
        rectangle2.setTop(rectangle1.getTop());

        // Insert an empty group shape.
        GroupShape group = builder.insertGroupShape();

        // Add both rectangles to the group.
        group.appendChild(rectangle1);
        group.appendChild(rectangle2);

        // Style the group (red border, 1.5 pt weight).
        group.getStroke().setColor(java.awt.Color.RED);
        group.getStroke().setWeight(1.5);

        // Save the document.
        String outPath = "output/GroupShape.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

Ejecuta el programa, abre el `GroupShape.docx` resultante y verás los rectángulos agrupados exactamente como se describe.

## Conclusión

Ahora sabes **how to group shapes** en Aspose.Words para Java, desde crear un documento hasta insertar formas de rectángulo, ajustar sus posiciones y, finalmente, agruparlas con `GroupShape`. Esta técnica te permite tratar varios dibujos como una única entidad, simplificando los ajustes de diseño y la consistencia visual.

**Next steps**

* Explora **how to insert rectangle** formas con diferentes patrones de relleno o bordes.
* Combina **insert rectangle shape** con cuadros de texto para crear diagramas etiquetados.
* Experimenta rotando o escalando el grupo para producir gráficos más complejos.

¡Siéntete libre de adaptar el código para otros tipos de formas, grupos más grandes o escenarios de generación dinámica de documentos! ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar forma de rectángulo en Java – Agrupar y posicionar formas](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [cómo insertar forma de grupo en Java – Guía completa](/words/english/java/images-shapes/how-to-insert-group-shape-in-java-complete-guide/)
- [Cómo aplicar sombra a una forma en Aspose.Words – Guía completa](/words/english/java/images-shapes/how-to-set-shadow-on-a-shape-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}