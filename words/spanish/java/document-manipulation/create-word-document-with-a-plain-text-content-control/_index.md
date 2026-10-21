---
category: general
date: 2026-10-04
description: Crear documento de Word usando Java que incluya un control de contenido
  de texto sin formato y un marcador de posición. Aprende cómo agregar el marcador
  de posición a la etiqueta y cómo insertar sdt.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- plain text content control
- docx with placeholder
- add placeholder to tag
- how to insert sdt
language: es
lastmod: 2026-10-04
og_description: Cree un documento de Word con un control de contenido de texto sin
  formato y un marcador de posición. Este tutorial muestra cómo agregar un marcador
  de posición a la etiqueta y cómo insertar sdt usando Aspose.Words para Java.
og_image_alt: Screenshot of a generated DOCX showing a plain text content control
  with placeholder
og_title: Crear documento de Word con control de contenido – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  headline: Create word document with a plain text content control
  type: TechArticle
- description: Create word document using Java that includes a plain text content
    control and a placeholder. Learn how to add placeholder to tag and how to insert
    sdt.
  name: Create word document with a plain text content control
  steps:
  - name: Initialise the document and builder
    text: '```java import com.aspose.words.*;'
  - name: Insert a plain‑text Structured Document Tag (SDT)
    text: '```java private static void insertPlainTextControl(DocumentBuilder builder)
      throws Exception { // Step 2 – create a plain text content control (SDT) with
      a unique tag name StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
      StructuredDocumentTagType.PLAIN_TEXT, "MyTag");'
  - name: Add regular content after the SDT
    text: '```java private static void addTrailingContent(DocumentBuilder builder)
      throws Exception { // Step 3 – write a line after the SDT to prove the control
      is correctly positioned builder.writeln("After SDT"); } ```'
  - name: Save the resulting file
    text: '```java private static void saveDocument(Document doc) throws Exception
      { // Step 4 – persist the document as a DOCX with placeholder String outPath
      = "SdtDemo.docx"; doc.save(outPath); System.out.println("Document saved to "
      + outPath); } ```'
  - name: Expected output
    text: 'Running the program creates `SdtDemo.docx`. Opening the file in Word shows:'
  - name: Next steps
    text: '* Explore **how to insert sdt** inside tables for form‑like layouts. *
      Combine this technique with **docx with placeholder** merging to build automated
      report generators. * Experiment with other control types (`RICH_TEXT`, `CHECKBOX`)
      to create richer Word forms.'
  type: HowTo
tags:
- Word
- Java
- Aspose.Words
title: Crear documento de Word con un control de contenido de texto plano
url: /es/java/document-manipulation/create-word-document-with-a-plain-text-content-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento de Word con un control de contenido de texto sin formato

Si necesitas **crear documento de Word** que contenga una región editable por el usuario, un control de contenido de texto sin formato es el enfoque más fiable. Este tutorial muestra exactamente cómo insertar una Structured Document Tag (SDT), establecer un marcador de posición y guardar el resultado como un **docx con marcador de posición**. Verás un ejemplo completo y ejecutable en Java que funciona con Aspose.Words for Java 23.8.

La guía cubre todos los requisitos previos, explica por qué cada llamada a la API es importante y brinda consejos para manejar casos límite como marcadores de posición multilingües o etiquetas anidadas. Al final podrás generar un archivo de Word que solicite a los usuarios “Enter text…” directamente dentro del documento.

## Requisitos previos

* Java 17 (o posterior) instalado y configurado en tu PATH.  
* Maven 3.8+ para gestionar dependencias.  
* Una licencia de Aspose.Words for Java (la evaluación funciona para pruebas).  
* Un IDE de desarrollo (IntelliJ IDEA, Eclipse o VS Code).

Agrega Aspose.Words a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.8</version>
</dependency>
```

## Crear documento de Word con un control de contenido de texto sin formato

El flujo de trabajo principal consta de cuatro pasos lógicos. Cada paso está encapsulado en un método con un nombre claro para que puedas reutilizar la lógica en proyectos más grandes.

### Paso 1: Inicializar el documento y el builder

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Step 1 – create an empty Document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        insertPlainTextControl(builder);
        addTrailingContent(builder);
        saveDocument(doc);
    }
}
```

**Por qué es importante:** `Document` representa el archivo de Word en memoria. `DocumentBuilder` es la API fluida que permite insertar párrafos, tablas y SDTs. Comenzar con un documento vacío garantiza que el marcador de posición aparezca al principio, lo cual es útil para plantillas.

### Paso 2: Insertar una Structured Document Tag (SDT) de texto sin formato

```java
private static void insertPlainTextControl(DocumentBuilder builder) throws Exception {
    // Step 2 – create a plain text content control (SDT) with a unique tag name
    StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
            StructuredDocumentTagType.PLAIN_TEXT, "MyTag");

    // Step 2.1 – add a placeholder that appears when the tag is empty
    sdt.setPlaceholderName("Enter text…");   // add placeholder to tag
}
```

**Por qué es importante:** `StructuredDocumentTagType.PLAIN_TEXT` crea un control de contenido que solo acepta caracteres simples, evitando formato accidental. La llamada `setPlaceholderName` rellena el texto de sugerencia gris que los usuarios ven antes de escribir—esta es la operación **add placeholder to tag** que hace que el documento se sienta como un formulario.

### Paso 3: Añadir contenido regular después del SDT

```java
private static void addTrailingContent(DocumentBuilder builder) throws Exception {
    // Step 3 – write a line after the SDT to prove the control is correctly positioned
    builder.writeln("After SDT");
}
```

**Por qué es importante:** Añadir contenido después del control verifica que el SDT no consuma todo el flujo del documento. También demuestra cómo mezclar etiquetas estructuradas con párrafos ordinarios, un requisito común al crear plantillas.

### Paso 4: Guardar el archivo resultante

```java
private static void saveDocument(Document doc) throws Exception {
    // Step 4 – persist the document as a DOCX with placeholder
    String outPath = "SdtDemo.docx";
    doc.save(outPath);
    System.out.println("Document saved to " + outPath);
}
```

**Por qué es importante:** El método `save` escribe el modelo en memoria a un archivo físico **docx con marcador de posición**. El archivo generado puede abrirse en Microsoft Word, LibreOffice o cualquier biblioteca que soporte el formato OpenXML.

## Código fuente completo

Unir todas las piezas te brinda un programa autónomo que puedes compilar y ejecutar:

```java
import com.aspose.words.*;

public class SdtDemo {
    public static void main(String[] args) throws Exception {
        // Initialise document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert plain‑text content control and set placeholder
        StructuredDocumentTag sdt = builder.insertStructuredDocumentTag(
                StructuredDocumentTagType.PLAIN_TEXT, "MyTag");
        sdt.setPlaceholderName("Enter text…");   // add placeholder to tag

        // Add normal text after the control
        builder.writeln("After SDT");

        // Save the file
        String outPath = "SdtDemo.docx";
        doc.save(outPath);
        System.out.println("Document saved to " + outPath);
    }
}
```

### Salida esperada

Ejecutar el programa crea `SdtDemo.docx`. Al abrir el archivo en Word se muestra:

* Un marcador de posición gris “Enter text…” dentro de un control de contenido de texto sin formato etiquetado **MyTag**.  
* La línea **After SDT** inmediatamente debajo del control.

El marcador de posición desaparece tan pronto como el usuario escribe, preservando el formato original.

## Variaciones comunes y casos límite

| Escenario | Cambio recomendado |
|----------|--------------------|
| **Marcador de posición multilingüe** | Use Unicode characters in `setPlaceholderName`, e.g., `sdt.setPlaceholderName("Введите текст…");`. |
| **Controles de contenido anidados** | Insert a second SDT inside the first by calling `builder.moveTo(sdt.getParagraph());` before the second `insertStructuredDocumentTag`. |
| **Control de solo lectura** | Call `sdt.setLockContentControl(true);` to prevent users from deleting the tag. |
| **Texto enriquecido en lugar de texto sin formato** | Replace `StructuredDocumentTagType.PLAIN_TEXT` with `StructuredDocumentTagType.RICH_TEXT`. |
| **Guardar en un flujo** | Use `doc.save(OutputStream, SaveFormat.DOCX);` when you need to send the file over HTTP. |

## Consejos profesionales

* **Reutilizar IDs de etiqueta** – Si generas muchos documentos a partir de la misma plantilla, mantén el nombre de la etiqueta (`"MyTag"`) consistente para que el procesamiento posterior (p. ej., combinación de correspondencia) pueda localizarla de forma fiable.  
* **Rendimiento** – Para plantillas grandes, crea el `DocumentBuilder` una sola vez y reutilízalo; insertar muchos SDTs en un bucle es más rápido que recrear el builder en cada iteración.  
* **Pruebas** – Después de generar el DOCX, verifica programáticamente que el marcador de posición exista con `doc.getRange().getStructuredDocumentTags().getCount()`.

## Conclusión

Ahora sabes cómo **crear documento de Word** que contiene un **control de contenido de texto sin formato** con un marcador de posición personalizado, produciendo eficazmente un **docx con marcador de posición** listo para la entrada del usuario. El ejemplo muestra el ciclo completo desde la inicialización del documento, **how to insert sdt**, **add placeholder to tag**, la adición de contenido regular y, finalmente, guardar el archivo.

### Próximos pasos

* Explora **how to insert sdt** dentro de tablas para diseños tipo formulario.  
* Combina esta técnica con la fusión de **docx with placeholder** para crear generadores de informes automatizados.  
* Experimenta con otros tipos de control (`RICH_TEXT`, `CHECKBOX`) para crear formularios de Word más ricos.

¡Siéntete libre de adaptar el código a tu propio motor de plantillas y comparte tus resultados en los comentarios!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words for Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Crear documento de Word Java – Añadir forma rectangular con efecto de sombra](/words/english/java/images-shapes/create-word-document-java-add-rectangle-shape-with-shadow-ef/)
- [Cómo crear documentos PDF con Aspose.Words for Java | API de procesamiento de documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}