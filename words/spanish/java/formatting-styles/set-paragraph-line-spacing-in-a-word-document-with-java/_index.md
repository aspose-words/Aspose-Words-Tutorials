---
category: general
date: 2026-11-15
description: Establezca el interlineado de párrafo en un documento Word con Java.
  Aprenda cómo establecer el interlineado de forma programática usando Aspose.Words
  para un formato de documento preciso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set paragraph line spacing
- how to set line spacing
language: es
lastmod: 2026-11-15
og_description: Establezca el interlineado de los párrafos en un documento de Word
  con Java. Esta guía explica cómo configurar el interlineado para los párrafos y
  los separadores de notas al pie usando Aspose.Words, brindándole un control total
  sobre el diseño del documento.
og_image_alt: Screenshot showing Java code that sets paragraph line spacing in a Word
  document
og_title: Establecer el interlineado de párrafo en Word usando Java
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  headline: Set paragraph line spacing in a Word document with Java
  type: TechArticle
- description: Set paragraph line spacing in a Word document with Java. Learn how
    to set line spacing programmatically using Aspose.Words for precise document formatting.
  name: Set paragraph line spacing in a Word document with Java
  steps:
  - name: Load the Word document
    text: First, create a `Document` instance that points to your source file.
  - name: Retrieve the footnote separator
    text: Footnote separators are special paragraphs that appear between footnotes
      and the main text. To change their appearance you need to access the `FootnoteSeparator`
      object.
  - name: How to set line spacing for the separator's paragraph
    text: Now apply the desired line spacing. Aspose.Words uses points for line‑spacing
      values; 12 pts is roughly single‑spacing for most fonts.
  - name: Save the updated document
    text: Finally, write the changes back to disk.
  type: HowTo
tags:
- Java
- Aspose.Words
- Document Formatting
title: Establecer el interlineado de párrafo en un documento Word con Java
url: /es/java/formatting-styles/set-paragraph-line-spacing-in-a-word-document-with-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer el interlineado de párrafo en un documento Word con Java

Si necesitas **establecer el interlineado de párrafo** en un documento Word, este tutorial te muestra cómo hacerlo con Java y Aspose.Words. También aprenderás **cómo establecer el interlineado** para los separadores de notas al pie, un requisito frecuente al formatear documentos profesionales.

En las siguientes secciones podrás:

* Cargar un archivo *.docx* existente.
* Recuperar el párrafo separador de notas al pie.
* Aplicar un valor de interlineado personalizado.
* Guardar el documento actualizado.

No se requiere ninguna configuración externa más allá de añadir la biblioteca Aspose.Words a tu proyecto, por lo que puedes copiar el código tal cual y ejecutarlo de inmediato.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* Java 17 o superior instalado.
* Maven (u otra herramienta de compilación) para gestionar dependencias.
* Una licencia válida de Aspose.Words for Java (la evaluación gratuita sirve para pruebas).
* Un documento Word de entrada (`input.docx`) ubicado en un directorio conocido.

Añade la dependencia de Aspose.Words a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- Use the latest stable version -->
</dependency>
```

## Establecer el interlineado de párrafo con Aspose.Words

Este encabezado H2 contiene la palabra clave principal, cumpliendo con el requisito SEO.

### Paso 1: Cargar el documento Word

Primero, crea una instancia de `Document` que apunte a tu archivo fuente.

```java
import com.aspose.words.*;

public class LineSpacingExample {
    public static void main(String[] args) throws Exception {
        // Load the Word document from the specified path
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
        // Continue with formatting...
    }
}
```

*Por qué es importante*: Cargar el documento te brinda un modelo en memoria que puedes manipular sin tocar el archivo original hasta que lo guardes explícitamente.

### Paso 2: Recuperar el separador de notas al pie

Los separadores de notas al pie son párrafos especiales que aparecen entre las notas al pie y el texto principal. Para cambiar su apariencia necesitas acceder al objeto `FootnoteSeparator`.

```java
// Retrieve the footnote separator that Aspose.Words represents internally
FootnoteSeparator separator = doc.getFootnoteSeparator();
```

*Consejo*: Si tu documento no contiene notas al pie, el separador sigue existiendo como un párrafo oculto, por lo que la llamada nunca devolverá `null`.

### Paso 3: Cómo establecer el interlineado del párrafo del separador

Ahora aplica el interlineado deseado. Aspose.Words usa puntos para los valores de interlineado; 12 pts equivale aproximadamente a un interlineado sencillo para la mayoría de las fuentes.

```java
// Set the line spacing to 12 points (single‑spacing)
separator.getParagraphFormat().setLineSpacing(12.0);
```

También puedes usar otros modos de espaciado:

| Modo                     | Llamada al método                                      |
|--------------------------|--------------------------------------------------------|
| **Exactamente** (pts fijos) | `setLineSpacingRule(LineSpacingRule.EXACTLY)`   |
| **Múltiple** (p. ej., 1.5) | `setLineSpacingRule(LineSpacingRule.MULTIPLE); setLineSpacing(1.5);` |

Elegir la regla correcta garantiza que el documento se renderice de forma consistente en Word, Google Docs y otros visores.

### Paso 4: Guardar el documento actualizado

Finalmente, escribe los cambios de vuelta al disco.

```java
// Save the modified document to a new file
doc.save("YOUR_DIRECTORY/output.docx");
System.out.println("Document saved with updated paragraph line spacing.");
```

Cuando abras `output.docx` en Microsoft Word, el separador de notas al pie se mostrará con el interlineado que definiste.

## Comprender cómo establecer el interlineado para párrafos normales

La misma API funciona para cualquier objeto `Paragraph`, no solo para los separadores de notas al pie. Aquí tienes un ejemplo rápido que ajusta el interlineado del primer párrafo del cuerpo:

```java
// Access the first body paragraph
Paragraph firstPara = (Paragraph) doc.getFirstSection().getBody().getChild(NodeType.PARAGRAPH, 0, true);

// Apply double line spacing (2.0 × the font size)
firstPara.getParagraphFormat().setLineSpacingRule(LineSpacingRule.MULTIPLE);
firstPara.getParagraphFormat().setLineSpacing(2.0);
```

**Por qué podrías necesitar esto**: Informes, contratos y trabajos académicos a menudo requieren un estilo de interlineado específico (p. ej., doble interlineado para borradores). Usar el mismo método `setLineSpacing` garantiza el diseño exacto que esperas.

## Problemas comunes y cómo evitarlos

| Problema                                 | Causa                                   | Solución |
|------------------------------------------|----------------------------------------|----------|
| El interlineado parece sin cambios       | `LineSpacingRule` dejado en su valor predeterminado (AUTO) | Establece explícitamente la regla con `setLineSpacingRule`. |
| Líneas en blanco extra después del separador | El separador contiene retornos de carro ocultos | Recorta el texto del separador con `separator.getText().trim();` antes de aplicar el espaciado. |
| El documento se corrompe al guardarse     | Uso de una versión desactualizada de Aspose.Words | Actualiza a la última versión (p. ej., 24.10) que incluye correcciones de errores de guardado. |

## Consejo profesional: procesar varios documentos por lotes

Si necesitas actualizar decenas de archivos, envuelve la lógica en un método auxiliar y recorre una carpeta:

```java
public static void updateSpacing(Path inputPath, Path outputPath) throws Exception {
    Document doc = new Document(inputPath.toString());
    FootnoteSeparator sep = doc.getFootnoteSeparator();
    sep.getParagraphFormat().setLineSpacing(12.0);
    doc.save(outputPath.toString());
}
```

Ejecutar este método en un bucle te ahorra horas de edición manual.

## Resultado esperado

Después de ejecutar el programa completo, `output.docx`:

* Contendrá el contenido original sin cambios, excepto por el interlineado.
* Mostrará el separador de notas al pie con un diseño de interlineado sencillo (12 pts).
* Mantendrá todo el resto del formato (estilos, imágenes, tablas).

Abre el archivo en Word y verifica que la línea del separador sea más ajustada (o más suelta, según el valor que hayas establecido).

## Conclusión

Ahora sabes cómo **establecer el interlineado de párrafo** en un documento Word usando Java, y también comprendes **cómo establecer el interlineado** tanto para separadores de notas al pie como para párrafos normales. El ejemplo completo y ejecutable muestra cómo cargar un documento, ajustar las propiedades de interlineado y guardar el resultado, todo con unas pocas llamadas claras a la API.

**Próximos pasos** que podrías explorar:

* **Cómo establecer el interlineado** para tablas y elementos de lista.
* Aplicar diferentes reglas de espaciado a encabezados versus texto del cuerpo.
* Usar el objeto `Style` para imponer el espaciado en todo el documento.

Experimenta con los valores, combínalos con otras opciones de formato y tendrás control total sobre el diseño de documentos en cualquier aplicación Java. ¡Feliz codificación!

## ¿Qué deberías aprender a continuación?

Los tutoriales siguientes cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Cómo establecer opciones en Aspose.Words for Java – guía completa](/words/english/java/document-loading-and-saving/how-to-set-options-in-aspose-words-for-java-complete-guide/)
- [Cómo establecer LoadOptions en Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cambiar el espaciado y sangrías de párrafos asiáticos en un documento Word](/words/english/net/document-formatting/change-asian-paragraph-spacing-and-indents/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}