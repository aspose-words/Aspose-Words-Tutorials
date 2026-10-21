---
category: general
date: 2026-09-11
description: Aprende cómo cambiar el formato de las notas al pie en Java con Aspose.Words.
  Esta guía explica cómo editar la nota al pie, actualizar el estilo de la nota al
  pie y modificar el separador de notas al pie.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote formatting
- how to edit footnote
- update footnote style
- modify footnote separator
language: es
lastmod: 2026-09-11
og_description: Cambie el formato de notas al pie en Java con Aspose.Words. Siga esta
  guía completa para editar notas al pie, actualizar el estilo de notas al pie y modificar
  el separador de notas al pie.
og_image_alt: Screenshot showing change footnote formatting in a Java editor
og_title: Cambiar el formato de las notas al pie en Java – guía paso a paso
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to change footnote formatting in Java with Aspose.Words.
    This guide explains how to edit footnote, update footnote style, and modify footnote
    separator.
  headline: How to change footnote formatting in a Word document using Java
  type: TechArticle
tags:
- Aspose.Words
- Java
- Footnote
- Document processing
title: Cómo cambiar el formato de las notas al pie en un documento de Word usando
  Java
url: /es/java/formatting-styles/how-to-change-footnote-formatting-in-a-word-document-using-j/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo cambiar el formato de las notas al pie en un documento Word usando Java

Si necesitas **cambiar el formato de las notas al pie** en un documento Word, este tutorial te guía paso a paso usando Aspose.Words for Java. Ya sea que estés construyendo una canalización de publicación o simplemente necesites **cómo editar la apariencia de las notas al pie** de forma programática, la solución a continuación cubre todo, desde cargar el archivo hasta guardar la versión actualizada.

Aprenderás cómo **actualizar el estilo de las notas al pie**, hacer que el separador de notas al pie sea negrita, e incluso **modificar las propiedades del separador de notas al pie** como el tamaño de fuente o el color. La guía asume que tienes conocimientos básicos de Java y una licencia funcional de Aspose.Words for Java.

## Requisitos previos

* Java 17 o una versión más reciente instalada.
* Aspose.Words for Java (versión 23.12 o posterior) añadido al classpath de tu proyecto.
* Un documento Word (`input.docx`) que contenga al menos una nota al pie.
* Un IDE o herramienta de compilación (Maven/Gradle) para compilar y ejecutar el código.

Si no estás seguro de cómo agregar Aspose.Words a un proyecto Maven, incluye la siguiente dependencia en tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version>
</dependency>
```

## Cambiar el formato de las notas al pie con Aspose.Words for Java

El núcleo de la solución es un breve programa Java que carga un documento, accede al párrafo del separador de notas al pie, cambia su formato y guarda el resultado. El código es completamente autónomo, por lo que puedes copiarlo en una nueva clase y ejecutarlo de inmediato.

```java
import com.aspose.words.*;

public class ChangeFootnoteFormatting {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // Step 2: Retrieve the footnote separator paragraph
        Paragraph footnoteSeparator = doc.getFootnoteSeparator();

        // Defensive check – the separator may be empty in some documents
        if (footnoteSeparator.getRuns().getCount() == 0) {
            // Create a new run so we have something to format
            Run run = new Run(doc);
            run.setText("\u2022"); // bullet character as placeholder
            footnoteSeparator.appendChild(run);
        }

        // Step 3: Change the first run's formatting – this is where we
        //          modify footnote separator appearance
        Run firstRun = footnoteSeparator.getRuns().get(0);
        Font font = firstRun.getFont();
        font.setBold(true);                // make the separator bold
        font.setItalic(true);              // optional: also italic
        font.setSize(10.0);                // set font size to 10 pt
        font.setColor(java.awt.Color.GRAY); // change color to a subtle gray

        // Step 4: Save the updated document
        doc.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Por qué cada paso es importante

* **Cargar el documento** (`new Document`) crea una representación en memoria que Aspose.Words puede manipular.  
* **Obtener el separador de notas al pie** (`getFootnoteSeparator`) te brinda acceso directo al párrafo que separa las notas al pie del texto principal. Este es el elemento que debes apuntar cuando deseas **cambiar el formato de las notas al pie**.  
* **Formatear el run** (`setBold`, `setItalic`, `setSize`, `setColor`) muestra cómo **modificar las propiedades del separador de notas al pie**. Puedes añadir cualquier atributo de fuente adicional aquí, como subrayado o resaltado, para controlar completamente la apariencia.  
* **Guardar el documento** escribe los cambios de vuelta al disco, produciendo un nuevo archivo (`output.docx`) que refleja el estilo de nota al pie actualizado.

> **Consejo profesional:** Si tu documento fuente usa un separador de notas al pie personalizado que contiene varios runs (p. ej., una combinación de símbolos), recorre `footnoteSeparator.getRuns()` y aplica la misma configuración de `Font` a cada run para lograr un estilo coherente.

## Cómo editar el separador de notas al pie programáticamente

A veces puede ser necesario editar no solo el separador sino también el texto de la nota al pie. La misma API puede usarse para acceder a cada nota al pie, ajustar su formato de párrafo o cambiar el estilo de numeración.

```java
for (Footnote footnote : (Iterable<Footnote>) doc.getFootnotes()) {
    // Example: make all footnote text italic and 9 pt
    for (Paragraph para : (Iterable<Paragraph>) footnote.getParagraphs()) {
        para.getParagraphFormat().setStyleIdentifier(StyleIdentifier.FOOTNOTE_TEXT);
        para.getRuns().forEach(run -> {
            Font f = run.getFont();
            f.setItalic(true);
            f.setSize(9.0);
        });
    }
}
```

El fragmento anterior muestra **cómo editar los cuerpos de las notas al pie** después de haber **cambiado el formato de las notas al pie** del separador. Al iterar sobre `doc.getFootnotes()`, garantizas que cada nota al pie herede el mismo estilo, lo cual es esencial para un documento con aspecto profesional.

## Actualizar el estilo de las notas al pie para una apariencia de documento consistente

Si prefieres trabajar con estilos en lugar de runs individuales, Aspose.Words te permite crear o modificar un objeto `Style` y luego aplicarlo a las notas al pie y al separador. Este enfoque es útil cuando necesitas **actualizar el estilo de las notas al pie** en varios documentos.

```java
// Create or retrieve a style named "MyFootnoteStyle"
Style footnoteStyle = doc.getStyles().add(StyleType.PARAGRAPH, "MyFootnoteStyle");
footnoteStyle.getFont().setBold(true);
footnoteStyle.getFont().setSize(10);
footnoteStyle.getFont().setColor(java.awt.Color.DARK_GRAY);

// Apply the style to the separator
footnoteSeparator.getParagraphFormat().setStyle(footnoteStyle);

// Apply the same style to every footnote paragraph
for (Footnote fn : (Iterable<Footnote>) doc.getFootnotes()) {
    for (Paragraph p : (Iterable<Paragraph>) fn.getParagraphs()) {
        p.getParagraphFormat().setStyle(footnoteStyle);
    }
}
```

Usar un estilo dedicado facilita el mantenimiento futuro: cambia el estilo una vez y todas las notas al pie y separadores se actualizan automáticamente. Esta técnica es la forma recomendada de **actualizar el estilo de las notas al pie** en flujos de trabajo de publicación a gran escala.

## Modificar el separador de notas al pie para que coincida con tu marca

Las directrices de marca a veces dictan que el separador de notas al pie use un carácter específico (p. ej., un asterisco) o una línea personalizada. Aspose.Words permite reemplazar completamente el contenido del separador predeterminado.

```java
// Remove existing runs
footnoteSeparator.getRuns().clear();

// Insert a custom separator line
Run customRun = new Run(doc);
customRun.setText("--- Custom Separator ---");
Font customFont = customRun.getFont();
customFont.setBold(true);
customFont.setSize(8);
customFont.setColor(java.awt.Color.BLUE);
footnoteSeparator.appendChild(customRun);
```

El código anterior **modifica el separador de notas al pie** al borrar cualquier run existente e insertar un nuevo run con el texto y formato deseados. También puedes usar caracteres Unicode como `\u2022` (viñeta) o `\u2014` (raya larga) para lograr el efecto visual exacto requerido por tu marca.

## Resultado esperado

Después de ejecutar el programa:

* El separador de notas al pie en `output.docx` aparece **negrita**, **cursiva**, 10 pt y gris (o el color que hayas configurado).  
* Todos los párrafos de notas al pie adoptan el estilo que definiste, garantizando una apariencia uniforme en todo el documento.  
* Si reemplazaste el texto del separador, la nueva línea personalizada es visible exactamente donde estaba la línea original.

Abre el archivo resultante en Microsoft Word o LibreOffice Writer para verificar los cambios. Deberías ver el separador actualizado justo encima de la primera nota al pie, y el texto de la nota al pie debería reflejar cualquier modificación de estilo que hayas aplicado.

## Problemas comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| `footnoteSeparator.getRuns().getCount() == 0` lanza una excepción | Algunos documentos tienen un párrafo separador vacío. | Agrega una verificación defensiva y crea un run si no existen (consulta el ejemplo de código). |
| Los cambios de fuente no son visibles | El documento usa un tema que sobrescribe el formato directo. | Establece `font.setThemeFont(null)` o aplica un estilo personalizado en lugar de formato directo. |
| El archivo guardado no refleja los cambios | El archivo original sigue abierto en Word, bloqueando la ruta de salida. | Cierra cualquier instancia del archivo antes de ejecutar el programa, o |

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Procesamiento de palabras con notas al pie y notas finales](/words/english/net/working-with-footnote-and-endnote/)
- [Establecer la posición de la nota al pie y la nota final](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Cómo mostrar la información de versión de Aspose.Words en Java: Guía completa](/words/english/java/getting-started/aspose-words-java-version-info/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}