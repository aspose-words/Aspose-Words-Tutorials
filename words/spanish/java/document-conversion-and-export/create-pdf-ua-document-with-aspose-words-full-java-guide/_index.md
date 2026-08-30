---
category: general
date: 2026-04-28
description: Crear documento PDF UA usando Aspose.Words para Java. Aprende a cargar
  docx con recuperación, exportar ecuaciones a LaTeX, guardar markdown desde Word
  y recuperar fuentes faltantes.
draft: false
keywords:
- create PDF UA document
- retrieve missing fonts
- export equations to LaTeX
- save markdown from Word
- load docx with recovery
language: es
og_description: Crear documento PDF UA con Aspose.Words para Java. Guía paso a paso
  que cubre la carga de recuperación, exportación a LaTeX, guardado en Markdown y
  recuperación de fuentes faltantes.
og_title: Crear documento PDF UA – Tutorial completo de Java
tags:
- Aspose.Words
- Java
- PDF/UA
title: Crear documento PDF UA con Aspose.Words – Guía completa de Java
url: /es/java/document-conversion-and-export/create-pdf-ua-document-with-aspose-words-full-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear documento PDF UA – Tutorial completo de Java

¿Necesita **crear un documento PDF UA** a partir de un archivo Word mientras maneja contenido corrupto? En este tutorial le guiaremos a cargar un DOCX con recuperación, exportar ecuaciones a LaTeX, guardar Markdown desde Word y recuperar fuentes faltantes, todo con Aspose.Words for Java.  

Si alguna vez ha mirado un .docx dañado y se ha preguntado por qué su PDF no es accesible, está en el lugar correcto. Al final tendrá un archivo PDF/UA 1 totalmente compatible, una versión Markdown que contiene ecuaciones LaTeX y una lista clara de cualquier sustitución de fuentes que ocurrió durante la carga.

## Lo que necesitará

- **Aspose.Words for Java** (última versión a partir de 2026) – agregue la dependencia Maven/Gradle o el JAR a su classpath.  
- Java 17 o superior (la API usa streams, por lo que se recomienda un JDK reciente).  
- Un archivo de ejemplo `input.docx` que puede contener secciones corruptas, ecuaciones Office Math y formas flotantes.  

No se requieren bibliotecas adicionales; todo está dentro de Aspose.Words.

---

## Paso 1 – Cargar DOCX con modo de recuperación  

Cuando un documento está parcialmente dañado, el cargador predeterminado lanza una excepción. Al habilitar el modo de recuperación le indica a Aspose.Words que continúe y muestre advertencias en su lugar.

```java
import com.aspose.words.*;

public class LatestFeaturesDemo {

    public static void main(String[] args) throws Exception {

        // 1️⃣ Load the document with recovery to gracefully handle corruption
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

*Por qué es importante:* El modo de recuperación evita que toda su cadena de procesamiento se interrumpa por un solo párrafo defectuoso. También rellena `doc.getWarnings()` para que luego pueda **recuperar fuentes faltantes** y otros problemas.

---

## Paso 2 – Exportar ecuaciones a LaTeX dentro de un archivo Markdown  

La mayoría de los desarrolladores adoran Markdown para documentación, pero las ecuaciones integradas de Word son difíciles de copiar. Aspose.Words puede traducirlas directamente a LaTeX.

```java
        // 2️⃣ Configure Markdown export with LaTeX for Office Math
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);

        // Store images in a sub‑folder so the Markdown stays tidy
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });

        // Save the Markdown file
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);
```

*Consejo profesional:* La devolución de llamada asegura que cada imagen extraída se guarde bajo `imgs/`. Esto refleja cómo GitHub renderiza Markdown: limpio y portátil.

---

## Paso 3 – Crear documento PDF / UA con etiquetado adecuado  

El cumplimiento de PDF/UA (Accesibilidad Universal) es obligatorio para muchos proyectos del sector público. Las siguientes opciones hacen que Aspose.Words etiquete correctamente las formas flotantes y establezca la bandera de cumplimiento PDF/UA.

```java
        // 3️⃣ Prepare PDF/UA export options
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);          // Enforce PDF/UA‑1
        pdfOptions.setExportFloatingShapesAsInlineTag(true);      // Tag floating shapes

        // Save the accessible PDF
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);
```

*Lo que verá:* Al abrir `output.pdf` en Adobe Acrobat Pro se mostrará “PDF/UA‑1 compliant” en las propiedades del documento. Todas las formas flotantes (cuadros de texto, imágenes) tendrán etiquetas apropiadas para lectores de pantalla.

---

## Paso 4 – Ajustar la sombra de una forma (estilizado opcional)  

Aunque no es necesario para la accesibilidad, ajustar aspectos visuales puede ser útil para informes internos.

```java
        // 4️⃣ Grab the first shape and modify its shadow
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(java.awt.Color.GRAY);
```

*¿Por qué molestarse?* Si el PDF también es una pieza de marketing, una sombra sutil hace que el diseño se vea pulido sin romper el cumplimiento.

---

## Paso 5 – Recuperar fuentes faltantes y otras advertencias  

Durante la carga con recuperación, Aspose.Words registra cualquier sustitución de fuentes. Listarlas le ayuda a decidir si incrusta la fuente correcta o acepta la alternativa.

```java
        // 5️⃣ Enumerate font‑substitution warnings
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName() +
                                   " → substituted: " + fsw.getSubstitutedFontName());
            }
        }

        // You can also handle other warning types here (e.g., content loss)
    }
}
```

*Salida típica* (su consola mostrará algo como):

```
=== Font Substitution Report ===
Missing: Calibri → substituted: Arial
Missing: Times New Roman → substituted: Liberation Serif
```

Si ve fuentes críticas faltantes, considere instalarlas en el servidor o incrustarlas mediante `PdfSaveOptions.setEmbedFullFonts(true)`.

---

## Ejemplo completo y funcional  

A continuación se muestra la clase Java completa y lista para ejecutar. Péguela en su IDE, ajuste las rutas y presione **Run**.

```java
import com.aspose.words.*;
import java.awt.Color;

/**
 * Demonstrates how to:
 *  • load a DOCX with recovery,
 *  • export equations to LaTeX inside Markdown,
 *  • create a PDF/UA‑1 compliant PDF,
 *  • modify shape shadows,
 *  • and list any font‑substitution warnings.
 */
public class LatestFeaturesDemo {
    public static void main(String[] args) throws Exception {

        // ---- Step 1: Load DOCX with recovery ----
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setRecoveryMode(RecoveryMode.RECOVER_WITH_WARNINGS);
        Document doc = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // ---- Step 2: Export equations to LaTeX in Markdown ----
        MarkdownSaveOptions mdOptions = new MarkdownSaveOptions();
        mdOptions.setOfficeMathExportMode(OfficeMathExportMode.LATEX);
        mdOptions.setResourceSavingCallback(resourceInfo -> {
            if (resourceInfo.getResourceType() == ResourceType.IMAGE) {
                resourceInfo.setResourceFileName("imgs/" + resourceInfo.getResourceFileName());
            }
        });
        doc.save("YOUR_DIRECTORY/output.md", mdOptions);

        // ---- Step 3: Save as PDF/UA with proper tagging ----
        PdfSaveOptions pdfOptions = new PdfSaveOptions();
        pdfOptions.setCompliance(PdfCompliance.PDF_UA_1);
        pdfOptions.setExportFloatingShapesAsInlineTag(true);
        doc.save("YOUR_DIRECTORY/output.pdf", pdfOptions);

        // ---- Step 4: Optional – adjust the first shape’s shadow ----
        Shape firstShape = (Shape) doc.getChild(NodeType.SHAPE, 0, true);
        ShadowFormat shadow = firstShape.getShadowFormat();
        shadow.setBlurRadius(4);
        shadow.setDistanceX(2);
        shadow.setDistanceY(2);
        shadow.setColor(Color.getGray());

        // ---- Step 5: List any missing‑font warnings ----
        System.out.println("=== Font Substitution Report ===");
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsw = (FontSubstitutionWarning) warning;
                System.out.println("Missing: " + fsw.getMissingFontName()
                                   + " → substituted: " + fsw.getSubstitutedFontName());
            }
        }
    }
}
```

**Resultados esperados**

| Salida | Descripción |
|--------|-------------|
| `output.md` | Archivo Markdown donde cada ecuación Office Math aparece como LaTeX (`$…$`). Las imágenes se guardan en `imgs/`. |
| `output.pdf` | Documento PDF/UA‑1 compatible; ábralo en Acrobat para ver “PDF/UA‑1” bajo Archivo → Propiedades → Estándares. |
| Console | Lista de cualquier fuente faltante, p. ej., “Missing: Calibri → substituted: Arial”. |

---

## Preguntas frecuentes (FAQ)

**Q: ¿Esto funciona con versiones anteriores de Aspose.Words?**  
A: Los enums `RecoveryMode`, `OfficeMathExportMode.LATEX` y `PdfCompliance.PDF_UA_1` se introdujeron en la versión 22.8. Si está en una versión anterior, actualice: las funciones de accesibilidad no se retroportan.

**Q: ¿Qué pasa si necesito incrustar las fuentes originales en lugar de la sustitución?**  
A: Configure `pdfOptions.setEmbedFullFonts(true)` y asegúrese de que los archivos de fuentes sean accesibles en la ruta de fuentes de la JVM.

**Q: ¿Puedo exportar a otros formatos de marcado (p. ej., HTML) manteniendo las ecuaciones LaTeX?**  
A: Sí. Use `HtmlSaveOptions` y establezca `setOfficeMathExportMode(OfficeMathExportMode.LATEX)`; el mismo enum funciona en todos los formatos.

**Q: Mi DOCX contiene muchas formas flotantes; ¿se etiquetarán todas?**  
A: Con `setExportFloatingShapesAsInlineTag(true)`, Aspose.Words envuelve cada forma flotante en una etiqueta `<Figure>` para PDF/UA, cumpliendo la mayoría de las verificaciones de lectores de pantalla.

---

## Conclusión  

Hemos demostrado cómo **crear un documento PDF UA** a partir de una fuente Word, mientras también **cargamos docx con recuperación**, **exportamos ecuaciones a LaTeX**, **guardamos markdown desde Word** y **recuperamos fuentes faltantes**. El código es completamente autónomo, se ejecuta en cualquier entorno Java 17+ y produce activos listos tanto para auditorías de accesibilidad como para desarrolladores

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}