---
category: general
date: 2026-07-26
description: Insertar una forma rectangular en Java usando Aspose.Words. Aprende cómo
  establecer el tamaño de la forma, posicionar la forma y cómo agrupar formas en un
  archivo DOCX.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- set shape size
- position shape
- how to group shapes
- how to add rectangle
language: es
lastmod: 2026-07-26
og_description: Inserte una forma rectangular en Java para crear gráficos DOCX enriquecidos.
  Siga esta guía paso a paso para establecer el tamaño de la forma, posicionarla y
  agrupar formas sin esfuerzo.
og_image_alt: Screenshot showing a rectangle shape inserted and grouped in a Java‑generated
  Word document
og_title: Insertar forma de rectángulo en Java – Domina la agrupación y el posicionamiento
schemas:
- author: Aspose
  dateModified: '2026-07-26'
  description: Insert rectangle shape in Java using Aspose.Words. Learn how to set
    shape size, position shape, and how to group shapes in a DOCX file.
  headline: Insert Rectangle Shape in Java – Group and Position Shapes
  type: TechArticle
tags:
- Aspose.Words
- Java
- Shapes
- DOCX
title: Insertar forma de rectángulo en Java – Agrupar y posicionar formas
url: /es/java/images-shapes/insert-rectangle-shape-in-java-group-and-position-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma rectangular en Java – Agrupar y posicionar formas

¿Alguna vez necesitaste **insertar una forma rectangular** en un documento Word mientras escribías código Java? No eres el único: los desarrolladores que crean informes, facturas o plantillas personalizadas se topan con este problema todo el tiempo. La buena noticia es que con unas pocas líneas de Aspose.Words para Java puedes **insertar una forma rectangular**, **establecer el tamaño de la forma**, **posicionar la forma**, e incluso **cómo agrupar formas** para que se muevan como una sola unidad.

En esta guía recorreremos todo el proceso, desde crear un documento en blanco hasta guardar un `.docx` que contiene dos rectángulos agrupados ordenadamente. Al final sabrás **cómo añadir objetos rectangulares**, controlar sus dimensiones, colocarlos exactamente donde deseas y agruparlos en un conjunto reutilizable. No se requieren bibliotecas externas más allá de Aspose.Words, y el código funciona con Java 8 o superior.

## Requisitos previos

- Java 8 o superior instalado (yo uso JDK 17, pero cualquier versión que soporte Maven funciona)
- Aspose.Words para Java 23.9 o posterior – agrega la dependencia a tu `pom.xml` o descarga el JAR
- Conocimientos básicos de sintaxis Java (si puedes escribir un método `main`, estás listo)
- Un IDE o editor de texto de tu preferencia (IntelliJ IDEA, Eclipse, VS Code…)

> **Consejo profesional:** Si utilizas Maven, la dependencia se ve así:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Ahora que tenemos la base preparada, vamos al código.

## Insertar forma rectangular y establecer su tamaño

Lo primero que harás es crear un `Document` nuevo y un `DocumentBuilder`. El builder es tu “pluma” que dibuja formas en la página. A continuación **insertamos una forma rectangular** y, de inmediato, **establecemos el tamaño de la forma** a 100 × 80 puntos.

```java
import com.aspose.words.*;

public class GroupedRectanglesDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new document and a builder to add content
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a GroupShape that will act as a container for other shapes
        GroupShape group = builder.insertGroupShape(400, 200);
        // The group itself is 400×200 points – adjust as needed

        // ---------- First rectangle ----------
        // Insert rectangle shape
        Shape rectangle1 = new Shape(document, ShapeType.RECTANGLE);
        // Set shape size
        rectangle1.setWidth(100);
        rectangle1.setHeight(80);
        // Position shape inside the group
        rectangle1.setLeft(20);   // 20 points from the left edge of the group
        rectangle1.setTop(30);    // 30 points from the top edge of the group
        // Add the rectangle to the group
        group.appendChild(rectangle1);
```

Observa cómo las llamadas `setWidth`/`setHeight` **establecen el tamaño de la forma** en puntos (1 pt ≈ 1/72 pulgada). También podrías usar `setSize` si prefieres un solo método, pero las llamadas explícitas dejan la intención perfectamente clara.

## Posicionar la forma en la página

Después de crear el primer rectángulo, necesitamos **posicionar la forma** del segundo para que no se superponga al primero. El posicionamiento funciona de la misma manera: estableces las propiedades `Left` y `Top` relativas al origen del grupo.

```java
        // ---------- Second rectangle ----------
        Shape rectangle2 = new Shape(document, ShapeType.RECTANGLE);
        rectangle2.setWidth(120);
        rectangle2.setHeight(60);
        // Position this rectangle a bit farther to the right and lower down
        rectangle2.setLeft(150);
        rectangle2.setTop(50);
        group.appendChild(rectangle2);
```

Si te preguntas por qué usamos `setLeft` en lugar de `setX`, es porque Aspose.Words adopta el clásico sistema de coordenadas GDI de Windows—`Left` es el desplazamiento horizontal, `Top` es el desplazamiento vertical. Cambiar estos valores te permite afinar el diseño sin tener que manipular tablas o párrafos.

## Cómo agrupar formas

Podrías preguntar, “¿Por qué molestarse en crear un grupo?” Agrupar tiene sentido cuando deseas que las formas se muevan juntas, roten como una unidad o compartan un estilo común. En el fragmento anterior ya creamos un `GroupShape` mediante `builder.insertGroupShape`. Ese objeto es esencialmente un contenedor—piénsalo como una carpeta que contiene otros archivos de forma.

> **Por qué es importante:** Si más adelante decides añadir una leyenda o rotar todo el diagrama, solo tendrás que modificar el grupo, no cada rectángulo individualmente.

## Cómo añadir un rectángulo a un grupo

El proceso de **cómo añadir un rectángulo** al grupo consiste simplemente en llamar a `group.appendChild(rectangle)`. Internamente Aspose.Words actualiza la colección interna del grupo y recalcula automáticamente el cuadro delimitador para que el grupo siga ajustándose al ancho y alto declarados.

```java
        // At this point the group already contains both rectangles.
        // You can also set the group’s border or fill if you like.
        group.getShapeStyle().setLineColor(Color.BLACK);
        group.getShapeStyle().setFillColor(Color.LIGHTGRAY);
```

Puedes experimentar con otros `ShapeType`s—`ShapeType.ELLIPSE`, `ShapeType.TRIANGLE`, etc.—y el mismo patrón `appendChild` funciona.

## Guardar el documento

Finalmente, persistimos el documento en disco. La ruta puede ser absoluta o relativa; solo asegúrate de que la carpeta exista.

```java
        // Step 5: Save the document containing the grouped shapes
        String outPath = "output/GroupShape.docx";
        document.save(outPath);
        System.out.println("Document saved to: " + outPath);
    }
}
```

Al abrir `GroupShape.docx` en Microsoft Word, verás dos rectángulos lado a lado, ambos encerrados dentro de un cuadro gris claro. Seleccionar el cuadro gris resaltará ambos rectángulos a la vez—prueba de que **cómo agrupar formas** realmente funciona.

![Grouped rectangles in a Word document](placeholder-image.png){: .center-image alt="Insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file"}

*Texto alternativo de la imagen (SEO):* **insert rectangle shape example showing two rectangles grouped in a Java‑generated DOCX file**.

## Resultado esperado

- Un archivo `GroupShape.docx` ubicado en la carpeta `output`.
- Dentro del documento: un grupo de 400 × 200 pt que contiene dos rectángulos (100 × 80 pt y 120 × 60 pt) posicionados en (20, 30) y (150, 50) respectivamente.
- El grupo tiene un borde negro delgado y un relleno gris claro, lo que hace que la agrupación sea visualmente evidente.

Abre el archivo y prueba arrastrar el cuadro gris—ambos rectángulos deberían moverse juntos. Si no lo hacen, verifica que hayas llamado `group.appendChild` para cada forma.

## Problemas comunes y casos límite

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **Los rectángulos aparecen fuera de la página** | Los valores `Left`/`Top` superan las dimensiones del grupo | Aumenta el tamaño del grupo (`insertGroupShape(width, height)`) o reduce los desplazamientos |
| **El grupo desaparece después de guardar** | Los atributos `Width`/`Height` del grupo están en 0 | Proporciona dimensiones distintas de cero al llamar a `insertGroupShape` |
| **Los colores de la forma se ven incorrectos** | El relleno predeterminado es transparente; Word puede renderizarlo como blanco | Establece explícitamente `setFillColor` o usa `ShapeStyle` |
| **Excepción `ArgumentOutOfRangeException`** | Uso de coordenadas negativas | Mantén `Left` y `Top` sin valores negativos |

Abordar estos puntos desde el principio te ahorrará los dolores de cabeza del “¿por qué mi forma desaparece?” que muchos principiantes experimentan.

## Recapitulación y próximos pasos

Hemos cubierto todo el ciclo de vida de **insertar forma rectangular** en Java: crear un documento, **establecer el tamaño de la forma**, **posicionar la forma**, **cómo agrupar formas**, y **cómo añadir un rectángulo** a ese grupo. El ejemplo completo y ejecutable está en el bloque de código anterior, y puedes pegarlo directamente en un proyecto Maven para ver el resultado.

¿Qué sigue? Considera experimentar con:

- Añadir texto dentro de cada rectángulo mediante


## ¿Qué deberías aprender a continuación?


Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Create Word Document Java – Add Rectangle Shape with Shadow Effect](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}