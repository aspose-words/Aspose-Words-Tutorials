---
category: general
date: 2026-08-07
description: Cómo editar notas al pie en Java con Aspose.Words – añadir guion personalizado,
  cambiar la línea de la nota al pie y establecer la alineación del párrafo para documentos
  pulidos.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to edit footnote
- add custom dash
- change footnote line
- change footnote separator
- set paragraph alignment
language: es
lastmod: 2026-08-07
og_description: Cómo editar notas al pie en Java con Aspose.Words. Aprende a agregar
  un guion personalizado, cambiar la línea de la nota al pie y establecer la alineación
  del párrafo en solo unos pocos pasos.
og_image_alt: Java code editing footnote separator with a custom dash and centered
  alignment
og_title: 'Cómo editar una nota al pie en Java: agregar guion, cambiar línea, establecer
  alineación'
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  headline: How to edit footnote in Java with Aspose.Words
  type: TechArticle
- description: How to edit footnote in Java with Aspose.Words – add custom dash, change
    footnote line, and set paragraph alignment for polished documents.
  name: How to edit footnote in Java with Aspose.Words
  steps:
  - name: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
    text: '**Loading the document** – `new Document(...)` reads the DOCX file into
      memory, giving you access to all its nodes.'
  - name: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
    text: '**Fetching the separator** – `getFootnoteSeparator()` returns the special
      paragraph that Aspose.Words treats as the footnote line. This object is the
      only place you can safely modify the separator.'
  - name: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
    text: '**Setting paragraph alignment** – `setAlignment(ParagraphAlignment.CENTER)`
      changes the line’s alignment. The keyword *set paragraph alignment* is applied
      directly to the separator, ensuring a centered dash.'
  - name: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
    text: '**Adding a custom dash** – By clearing existing runs and adding a new `Run`
      with the em‑dash character (`—`), you achieve the *add custom dash* effect while
      also *change footnote line* to your desired style.'
  - name: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
    text: '**Saving the document** – `doc.save(...)` writes the changes back to disk,
      producing an output file that reflects all modifications.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Footnotes
title: Cómo editar una nota al pie en Java con Aspose.Words
url: /es/java/document-styling/how-to-edit-footnote-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo editar notas al pie en Java con Aspose.Words

Si necesitas **cómo editar notas al pie** en un documento Word usando Java, esta guía muestra el flujo de trabajo completo. Aprenderás a agregar un guion personalizado, cambiar la línea de la nota al pie y establecer la alineación del párrafo para que el separador de notas al pie tenga un aspecto profesional.

Editar notas al pie es un requisito común al preparar contratos legales, trabajos académicos o folletos de marketing. Los pasos a continuación cubren todo lo que necesitas, desde cargar el documento hasta guardar el archivo final, sin requerir herramientas adicionales.

## Requisitos previos

Antes de comenzar, asegúrate de tener:

* Java 17 o superior instalado.
* Aspose.Words for Java (última versión) añadido al classpath de tu proyecto.
* Un archivo DOCX (`input.docx`) que contenga al menos una nota al pie.

Estos elementos garantizan que el código se ejecute sin errores en tiempo de ejecución.

## Cómo editar el separador y la línea de la nota al pie

El separador de notas al pie es el párrafo que aparece entre el texto principal y la lista de notas al pie. Cambiar su apariencia mejora la legibilidad y coincide con la identidad corporativa.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the document containing footnotes
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Get the footnote separator paragraph (the line before the footnote list)
        Paragraph separator = doc.getFootnoteSeparator();

        // Step 3: Center‑align the separator for better appearance
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Step 4: Replace the default separator line with a custom dash
        separator.getRuns().clear();                 // Remove existing runs
        separator.getRuns().add(new Run(doc, "—"));   // Add a custom dash character

        // Step 5: Save the modified document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Por qué cada línea es importante

1. **Cargando el documento** – `new Document(...)` lee el archivo DOCX en memoria, dándote acceso a todos sus nodos.
2. **Obteniendo el separador** – `getFootnoteSeparator()` devuelve el párrafo especial que Aspose.Words trata como la línea de la nota al pie. Este objeto es el único lugar donde puedes modificar de forma segura el separador.
3. **Estableciendo la alineación del párrafo** – `setAlignment(ParagraphAlignment.CENTER)` cambia la alineación de la línea. La palabra clave *set paragraph alignment* se aplica directamente al separador, garantizando un guion centrado.
4. **Agregando un guion personalizado** – Al borrar los runs existentes y agregar un nuevo `Run` con el carácter em‑dash (`—`), logras el efecto de *add custom dash* mientras también *change footnote line* al estilo deseado.
5. **Guardando el documento** – `doc.save(...)` escribe los cambios de vuelta al disco, produciendo un archivo de salida que refleja todas las modificaciones.

## Agregar guion personalizado al separador de la nota al pie

El código en **Step 4** demuestra la técnica de *add custom dash*. Puedes reemplazar el em‑dash con cualquier cadena, como `"***"` o `"---"`, para que coincida con el lenguaje visual de tu documento.

```java
separator.getRuns().clear();                     // Remove default line
separator.getRuns().add(new Run(doc, "***"));    // Insert three asterisks as a custom dash
```

Usar un guion personalizado es especialmente útil cuando la línea delgada predeterminada no cumple con las directrices de la marca.

## Cambiar el estilo de la línea de la nota al pie

Si prefieres una línea sólida en lugar de un guion, puedes insertar un carácter Unicode de dibujo de caja o un guion bajo repetido.

```java
separator.getRuns().clear();
separator.getRuns().add(new Run(doc, "_____")); // Five underscores create a solid line
```

El paso *change footnote line* funciona de la misma manera sin importar el carácter que elijas, porque el párrafo separador simplemente muestra el texto que contiene.

## Establecer la alineación del párrafo para el separador de la nota al pie

La operación *set paragraph alignment* no se limita a la alineación centrada. Puedes alinear a la izquierda, derecha o justificar según las necesidades de tu diseño.

```java
separator.getParagraphFormat().setAlignment(ParagraphAlignment.RIGHT); // Right‑align
```

Alinear el separador a la derecha puede ser útil para documentos que usan notas al pie alineadas a la derecha, como publicaciones bilingües.

## Ejemplo completo y ejecutable

A continuación se muestra el programa completo que incorpora todos los conceptos: cargar un documento, editar el separador de notas al pie, agregar un guion personalizado, cambiar el estilo de la línea y establecer la alineación.

```java
import com.aspose.words.*;

public class FootnoteSeparatorDemo {
    public static void main(String[] args) throws Exception {
        // Load the source document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Retrieve the footnote separator paragraph
        Paragraph separator = doc.getFootnoteSeparator();

        // Set the desired alignment (center, left, right, or justify)
        separator.getParagraphFormat().setAlignment(ParagraphAlignment.CENTER);

        // Clear any existing content in the separator
        separator.getRuns().clear();

        // Add a custom dash – replace with any string to change footnote line
        separator.getRuns().add(new Run(doc, "—")); // Em‑dash as the custom dash

        // Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

**Salida esperada:** El archivo `output.docx` contiene un em‑dash centrado donde antes estaba la línea delgada original. Todas las notas al pie permanecen intactas y el diseño del documento refleja el nuevo estilo del separador.

## Problemas comunes y cómo evitarlos

| Problema | Razón | Solución |
|----------|-------|----------|
| Separador no encontrado | El documento no tiene notas al pie o usa un estilo de nota al pie personalizado | Asegúrate de que el DOCX de origen contenga al menos una nota al pie antes de llamar a `getFootnoteSeparator()` |
| Guion personalizado no visible | La fuente no soporta el carácter elegido | Usa un carácter Unicode que sea compatible con la fuente predeterminada del documento, o incrusta una fuente compatible |
| La alineación parece sin cambios | El formato del párrafo se sobrescribe más tarde en el código | Aplica la alineación **después** de cualquier otra llamada de formato que pueda restablecerla |

Abordar estos puntos evita errores en tiempo de ejecución y garantiza que el proceso de *how to edit footnote* funcione de manera fiable.

## Próximos pasos

Ahora que sabes **cómo editar notas al pie** puedes explorar tareas relacionadas:

* **Agregar estilo personalizado de referencia de nota al pie** – modifica los nodos `FootnoteReference` para cambiar la numeración o los símbolos.
* **Insertar notas al pie nuevas programáticamente** – usa `DocumentBuilder.insertFootnote()` para contenido dinámico.
* **Aplicar formato condicional** – cambia la apariencia de la nota al pie según el estilo del párrafo o la longitud del contenido.

Cada una de estas extensiones se basa en la misma superficie de API que usaste para *add custom dash*, *change footnote line* y *set paragraph alignment*.

---

*¡Feliz codificación! Si el tutorial te ayudó a dominar la edición de notas al pie, considera compartirlo con tu equipo o contribuir con un pull request para mejorar aún más el ejemplo.*

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Establecer posición de nota al pie y nota final](/words/hindi/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Cómo crear campos de formulario y agregar contenido usando DocumentBuilder en Aspose.Words para Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Cómo establecer LoadOptions en Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}