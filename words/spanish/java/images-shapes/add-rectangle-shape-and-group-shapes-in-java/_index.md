---
category: general
date: 2026-11-22
description: Agregar una forma rectangular en un documento de Word con Java, establecer
  el tamaño de la forma, agrupar múltiples formas y añadir la forma al grupo de manera
  eficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add rectangle shape
- set shape size
- group multiple shapes
- set shape dimensions
- append shape to group
language: es
lastmod: 2026-11-22
og_description: Agregar una forma rectangular en un documento de Word usando Java,
  luego establecer el tamaño de la forma, agrupar varias formas y añadir una forma
  al grupo en un único flujo de trabajo.
og_image_alt: Screenshot showing a rectangle shape added and grouped in a Word document
  using Java
og_title: Agregar forma de rectángulo y agrupar formas en Java – guía completa
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  headline: Add rectangle shape and group shapes in Java
  type: TechArticle
- description: Add rectangle shape in a Word document with Java, set shape size, group
    multiple shapes, and append shape to group efficiently.
  name: Add rectangle shape and group shapes in Java
  steps:
  - name: Insert the rectangle shape
    text: The rectangle is the first visual element we want to place inside the document.
      By using the `Shape` constructor with `ShapeType.RECTANGLE`, you get a fully
      editable object.
  - name: Set shape size and dimensions
    text: Set shape size and dimensions
  - name: Create a group shape container
    text: '```java // Step 6: Create a group shape that will hold the rectangle and
      other shapes GroupShape groupShape = builder.insertGroupShape(); ```'
  - name: Append shape to group
    text: Append shape to group
  - name: Save the document
    text: '```java // Save the result to a new file doc.save("output.docx"); } } ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Shape manipulation
title: Añadir forma de rectángulo y agrupar formas en Java
url: /es/java/images-shapes/add-rectangle-shape-and-group-shapes-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar forma rectangular y agrupar formas en Java

Si necesitas **agregar una forma rectangular** a un documento Word con Java, esta guía te muestra los pasos exactos. También aprenderás a **establecer el tamaño de la forma**, **agrupar varias formas** y **añadir una forma al grupo** sin salir del IDE.

Trabajar con gráficos vectoriales dentro de un archivo DOCX a menudo se siente como manejar APIs separadas. Al final de este tutorial tendrás un programa autónomo que crea un rectángulo, una elipse y cualquier forma adicional que necesites, y luego los agrupa para que se muevan como un solo objeto. No se requieren herramientas externas más allá de Aspose.Words para Java.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o posterior instalado.
* Maven 3.8+ (o Gradle) para gestionar dependencias.
* Una licencia válida de Aspose.Words para Java (la versión de evaluación sirve para pruebas).
* Un IDE como IntelliJ IDEA o VS Code, aunque cualquier editor de texto será suficiente.

Estos requisitos permiten que el código compile y se ejecute en cualquier entorno de desarrollo moderno.

## Paso 1: Configurar el proyecto Maven

Crea un nuevo proyecto Maven o añade la dependencia de Aspose.Words a un `pom.xml` existente:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>shape‑demo</artifactId>
  <version>1.0.0</version>

  <dependencies>
    <dependency>
      <groupId>com.aspose</groupId>
      <artifactId>aspose-words</artifactId>
      <version>23.12</version>
    </dependency>
  </dependencies>
</project>
```

La dependencia incluye todas las clases necesarias para la manipulación de documentos, incluidas `Document`, `DocumentBuilder`, `Shape` y `GroupShape`. Maven descargará los JAR automáticamente cuando ejecutes `mvn compile`.

## Paso 2: Cargar el documento y crear un DocumentBuilder

Un `DocumentBuilder` proporciona la API fluida para insertar contenido. Carga un DOCX existente o comienza con un documento en blanco:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Load an existing document or create a new one
        Document doc = new Document("input.docx");          // replace with your path
        DocumentBuilder builder = new DocumentBuilder(doc);
```

Crear el builder al principio te da un cursor posicionado al inicio del documento, listo para la inserción de formas.

## Agregar forma rectangular a un documento Word

### Paso 3: Insertar la forma rectangular

El rectángulo es el primer elemento visual que queremos colocar dentro del documento. Al usar el constructor `Shape` con `ShapeType.RECTANGLE`, obtienes un objeto totalmente editable.

```java
        // Step 3: Insert a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.RECTANGLE);
        // The shape is not yet sized; we will set its dimensions next.
```

Agregar el rectángulo en este punto no afecta el diseño hasta que se defina su tamaño y se añada a un contenedor.

### Establecer el tamaño y las dimensiones de la forma

#### Paso 4: Definir ancho y alto

Establecer las dimensiones de la forma determina cómo aparecerá en la página. Los valores de ancho y alto se miden en puntos (1 pt = 1/72 in).

```java
        // Step 4: Set shape size (width = 100 pt, height = 50 pt)
        rectangle.setWidth(100);
        rectangle.setHeight(50);
```

Puedes ajustar estos números para que coincidan con los requisitos de tu diseño. Los mismos métodos se aplican a cualquier instancia de `Shape`, por lo que puedes reutilizarlos para círculos, flechas o dibujos personalizados.

#### Paso 5: Insertar el rectángulo en el documento

Ahora que el rectángulo tiene un tamaño, colócalo en la página. El método `insertShape` de `DocumentBuilder` añade la forma en la posición actual del cursor.

```java
        // Insert the rectangle at the builder’s current position
        builder.insertShape(rectangle);
```

En esta etapa el rectángulo aparece solo en la página. Los siguientes pasos muestran cómo combinarlo con otras formas.

## Agrupar varias formas juntas

Agrupar formas te permite moverlas, rotarlas o redimensionarlas como una sola unidad. Esto es especialmente útil para crear diagramas complejos.

### Paso 6: Crear un contenedor de forma de grupo

```java
        // Step 6: Create a group shape that will hold the rectangle and other shapes
        GroupShape groupShape = builder.insertGroupShape();
```

La llamada `insertGroupShape` añade un contenedor vacío al documento. Cualquier forma añadida a este contenedor pasa a formar parte del grupo.

### Añadir forma al grupo

#### Paso 7: Agregar el rectángulo al grupo

```java
        // Append the previously created rectangle to the group
        groupShape.appendChild(rectangle);
```

Al añadirla, el rectángulo se mueve del cuerpo del documento a la colección interna del grupo. Ahora el rectángulo respeta las transformaciones del grupo.

#### Paso 8: Añadir una elipse como demostración

```java
        // Create an ellipse, set its size, and add it to the same group
        Shape ellipse = new Shape(doc, ShapeType.ELLIPSE);
        ellipse.setWidth(80);
        ellipse.setHeight(80);
        groupShape.appendChild(ellipse);
```

La elipse comparte el mismo espacio de coordenadas que el rectángulo, por lo que puedes alinearlas visualmente ajustando sus propiedades `setLeft` y `setTop` si es necesario.

### Paso 9: Guardar el documento

```java
        // Save the result to a new file
        doc.save("output.docx");
    }
}
```

Ejecutar el programa genera `output.docx`. Abre el archivo en Microsoft Word o LibreOffice; verás un rectángulo y una elipse agrupados. Al seleccionar cualquiera de las formas se resaltará todo el grupo, confirmando que **añadir forma al grupo** se realizó con éxito.

![Add rectangle shape example in Java](image.png){alt="Ejemplo de agregar forma rectangular en Java"}

*La captura de pantalla muestra el rectángulo y la elipse dentro de un único grupo, listos para manipulación conjunta.*

## Por qué este enfoque es importante

* **Fuente única de verdad** – Todas las propiedades de la forma se establecen antes de crear el grupo, evitando fallos de diseño.
* **Reutilización** – Los mismos métodos `setWidth`/`setHeight` funcionan para cualquier forma, de modo que puedes ampliar el ejemplo a flechas, estrellas o SVG personalizados.
* **Rendimiento** – Agrupar reduce la cantidad de objetos de dibujo que el renderizador de Word debe manejar, lo que mejora la velocidad de apertura de documentos grandes.
* **Mantenibilidad** – Al mantener la lógica de creación y agrupación de formas juntas, los desarrolladores futuros pueden modificar dimensiones o añadir nuevas formas sin buscar en código no relacionado.

## Variaciones comunes y casos límite

| Escenario | Ajuste |
|----------|------------|
| **Unidades diferentes** | Usa la conversión `PointsToPixels` o establece `Shape.setWrapType(WrapType.INLINE)` para colocación en línea. |
| **Rotar el grupo** | Llama a `groupShape.setRotation(45);` para rotar todas las formas hijas 45°. |
| **Añadir texto a una forma** | Usa `Shape.setText("Label");` después de establecer el tamaño. |
| **Tamaño dinámico** | Obtén las dimensiones de la página mediante `doc.getFirstSection().getPageSetup().getPageWidth()` y calcula los tamaños de las formas proporcionalmente. |

Estas variaciones ilustran cómo el patrón central —**agregar forma rectangular**, **establecer tamaño de la forma**, **agrupar varias formas**, **añadir forma al grupo**— se adapta a muchos requisitos del mundo real.

## Conclusión

Ahora sabes cómo **agregar una forma rectangular** a un documento Word usando Java, **establecer el tamaño de la forma**, **agrupar varias formas** y **añadir una forma al grupo** de manera limpia y mantenible. El ejemplo completo se compila en una única clase ejecutable, y el archivo DOCX resultante demuestra la salida esperada.

A partir de aquí puedes explorar:

* Añadir etiquetas de texto o hipervínculos a cada forma.
* Anidar grupos para construir diagramas jerárquicos.
* Exportar el documento a PDF manteniendo los grupos de formas.

Siéntete libre de experimentar con diferentes dimensiones, colores y tipos de forma adicionales. Dominar la manipulación de formas abre la puerta a la generación automática de informes, diagramas dinámicos y experiencias de documento enriquecidas, todo directamente desde código Java.

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Insertar forma rectangular en Java – Agrupar y posicionar formas](/words/english/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/)
- [Cómo crear e insertar formas de elipse y rectángulo dentro de un grupo en un documento Word usando Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Crear forma rectangular en un documento Word usando Java](/words/english/java/images-shapes/create-rectangle-shape-in-a-word-document-using-java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}