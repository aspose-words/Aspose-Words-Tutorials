---
category: general
date: 2026-09-18
description: Crea un documento en blanco e inserta formas en Word con Aspose.Words
  – aprende cómo añadir una forma de triángulo y más.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- add shapes to word
- how to insert triangle
- add triangle shape
- create word document
language: es
lastmod: 2026-09-18
og_description: Crea un documento en blanco en Word usando Aspose.Words y aprende
  cómo insertar una forma de triángulo, agrupar formas y otros gráficos. Sigue esta
  guía completa.
og_image_alt: Screenshot of a Word document showing a grouped shape with a triangle
  inside
og_title: Crear un documento en blanco y agregar formas a Word – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank document and insert shapes to Word with Aspose.Words –
    learn how to add a triangle shape and more.
  headline: How to create blank document and add shapes to Word
  type: TechArticle
tags:
- Aspose.Words
- Java
- Word automation
- Shapes
title: Cómo crear un documento en blanco y agregar formas a Word
url: /es/java/images-shapes/how-to-create-blank-document-and-add-shapes-to-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo crear un documento en blanco y agregar formas a Word

Si necesitas **crear un documento en blanco** y luego enriquecerlo con gráficos, esta guía te muestra exactamente cómo hacerlo. Recorreremos la creación de un archivo Word desde cero y **agregar formas a Word**, incluido **cómo insertar una forma de triángulo**, usando Aspose.Words for Java.

Terminarás el tutorial con un archivo *.docx* listo para usar que contiene una forma agrupada que contiene un triángulo. Los pasos cubren todo, desde la configuración del proyecto hasta guardar el **crear documento Word** final. No se requieren herramientas externas más allá de Aspose.Words.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o posterior instalado  
* Maven o Gradle para la gestión de dependencias  
* Una licencia de Aspose.Words for Java (la evaluación gratuita funciona para esta demostración)  

Si prefieres un sistema de compilación diferente, ajusta la sintaxis de la dependencia en consecuencia. El código funciona en cualquier plataforma que soporte Java.

## Crear documento en blanco con Aspose.Words

La primera operación es **crear un documento en blanco** en memoria. Aspose.Words proporciona la clase `Document` que representa un archivo Word sin contenido.

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Create a new blank document
        Document doc = new Document();               // create blank document
```

El constructor `new Document()` crea una estructura *.docx* vacía, que luego puedes poblar con párrafos, tablas o gráficos. Debido a que el documento está en blanco, tienes control total sobre cada elemento que agregues.

## Agregar formas a Word – insertar una forma de grupo

Una forma de grupo te permite tratar varios gráficos como una única unidad. Esto es útil cuando deseas mover o cambiar el tamaño de varias formas al mismo tiempo.

```java
        // Step 2: Initialize a DocumentBuilder to construct content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert a group shape of size 300 × 300 points
        GroupShape group = builder.insertGroupShape(300.0, 300.0);
```

`DocumentBuilder` es la API principal para agregar contenido. La llamada `insertGroupShape` crea un contenedor de 300 × 300 puntos (aproximadamente 4 × 4 pulgadas). Después de esta llamada, el cursor se posiciona *dentro* del grupo, listo para formas adicionales.

### ¿Por qué usar una forma de grupo?

Agrupar mantiene los gráficos relacionados alineados y facilita la aplicación de un formato uniforme. Si más adelante decides mover el triángulo, todo el grupo se moverá junto, preservando el diseño.

## Cómo insertar una forma de triángulo dentro del grupo

Ahora abordamos **cómo insertar una forma de triángulo**. El triángulo es uno de los valores incorporados de `ShapeType`.

```java
        // Step 4: Move the cursor into the group's first paragraph
        builder.moveTo(group.getFirstParagraph());

        // Step 5: Insert a triangle shape of size 60 × 60 points inside the group
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);
```

La llamada `moveTo` asegura que el punto de inserción del builder sea el primer párrafo del grupo. `insertShape` luego agrega un triángulo de 60 × 60 puntos. Como el cursor está dentro del grupo, el triángulo se convierte en un hijo de la forma de grupo.

**Consejos para agregar una forma de triángulo**:

* El tamaño se mide en puntos; 72 puntos equivalen a una pulgada. Ajusta las dimensiones según tu diseño.  
* Si necesitas una orientación diferente, usa `builder.getCurrentParagraph().getParagraphFormat().setAlignment()` para alinear la forma dentro del grupo.  
* El triángulo hereda los estilos de relleno y línea del grupo a menos que los sobrescribas con `shape.getFillColor()` o `shape.getStrokeColor()`.

## Guardar el documento – crear documento Word

Después de construir los gráficos, guardas el archivo. Este paso finaliza la operación de **crear documento Word**.

```java
        // Step 6: Save the document with the extended group shape
        doc.save("ExtendedGroup.docx");               // create word document
    }
}
```

`doc.save` escribe la representación en memoria en el disco como un documento Word estándar. Puedes abrir `ExtendedGroup.docx` en Microsoft Word, LibreOffice o cualquier visor que admita el formato OOXML. El archivo mostrará una forma agrupada que contiene un triángulo, exactamente como fue creado por el código.

## Ejemplo completo ejecutable

Juntando todas las piezas, aquí está el programa completo que puedes copiar, compilar y ejecutar:

```java
import com.aspose.words.*;

public class ShapeDemo {
    public static void main(String[] args) throws Exception {
        // 1. Create a new blank document
        Document doc = new Document();

        // 2. Prepare a builder for inserting content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 3. Insert a group shape (300 × 300 points)
        GroupShape group = builder.insertGroupShape(300.0, 300.0);

        // 4. Position the cursor inside the group
        builder.moveTo(group.getFirstParagraph());

        // 5. Insert a triangle shape (60 × 60 points)
        builder.insertShape(ShapeType.TRIANGLE, 60.0, 60.0);

        // 6. Save the file – this creates the final Word document
        doc.save("ExtendedGroup.docx");
    }
}
```

### Resultado esperado

Al abrir `ExtendedGroup.docx`, verás una única forma de grupo ocupando el centro de la página. Dentro de ese grupo, aparece un pequeño triángulo en la posición predeterminada. El triángulo puede seleccionarse y moverse como parte del grupo, confirmando que **agregar formas a Word** funcionó como se esperaba.

## Preguntas frecuentes y casos límite

| Pregunta | Respuesta |
|----------|-----------|
| *¿Puedo agregar más de una forma dentro del grupo?* | Sí. Después de insertar el triángulo, mantén el cursor dentro del grupo y llama a `builder.insertShape` nuevamente con un `ShapeType` diferente. |
| *¿Qué pasa si necesito que el triángulo sea rojo?* | Obtén la `Shape` devuelta por `insertShape` y llama a `shape.getFillColor().setColor(Color.RED)`. |
| *¿Esto funciona con archivos .doc antiguos?* | Aspose.Words guarda en el formato que especificas. Usa `doc.save("file.doc", SaveFormat.DOC)` para crear un documento Word heredado. |
| *¿Cómo cambio el borde del grupo?* | Usa `group.getStrokeColor().setColor(Color.BLUE)` y `group.setLineWeight(2.0)` para personalizar el contorno. |
| *¿Hay alguna forma de rotar el triángulo?* | Llama a `shape.getRotation()` para establecer un ángulo en grados. |

## Consejos profesionales

* **Reutiliza el builder** – crear un nuevo `DocumentBuilder` para cada forma genera sobrecarga. Mantén un solo builder por documento.  
* **Conversión de unidades** – si trabajas con milímetros, conviértelos a puntos (`points = mm * 2.83465`).  
* **Rendimiento** – para documentos grandes, llama a `doc.updatePageLayout()` solo una vez después de agregar todas las formas.

## Conclusión

Ahora sabes cómo **crear un documento en blanco**, **agregar formas a Word**, y específicamente **cómo insertar una forma de triángulo** usando Aspose.Words for Java. El ejemplo completo muestra el flujo de trabajo completo desde un archivo vacío hasta un **crear documento Word** guardado que contiene un triángulo agrupado.

Desde aquí puedes explorar valores adicionales de `ShapeType`, aplicar estilos personalizados o combinar varios grupos para crear diagramas complejos. Experimenta con diferentes tamaños, colores y posiciones para dominar la automatización de Word en Java.

--- 

*¿Listo para automatizar tu próximo informe? Clona el ejemplo, ajusta las dimensiones e integra el código en tu propia aplicación hoy mismo.*

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Crear forma de grupo en documento Word usando Aspose.Words para .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crear documento Word en blanco con forma de rectángulo sombreado – Guía paso a paso](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crear forma de rectángulo en Word con Aspose.Words – Guía paso a paso](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}