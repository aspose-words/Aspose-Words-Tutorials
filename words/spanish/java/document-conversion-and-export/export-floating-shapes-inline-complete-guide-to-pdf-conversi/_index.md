---
category: general
date: 2026-07-03
description: Exporta formas flotantes en línea al convertir Word a PDF en línea. Aprende
  cómo configurar opciones de PDF y guardar Word como PDF con opciones en Java.
draft: false
keywords:
- export floating shapes inline
- convert word to pdf inline
- how to set pdf options
- save word as pdf options
language: es
og_description: Exportar formas flotantes en línea al convertir un documento de Word
  a PDF. Este tutorial muestra cómo configurar las opciones de PDF y guardar Word
  como PDF.
og_title: Exportar formas flotantes en línea – Guía de conversión de PDF en Java
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  headline: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  type: TechArticle
- description: Export floating shapes inline while converting Word to PDF inline.
    Learn how to set PDF options and save Word as PDF options in Java.
  name: Export Floating Shapes Inline – Complete Guide to PDF Conversion
  steps:
  - name: 1. “What if my document contains complex SmartArt?”
    text: SmartArt is treated as a drawing object. The inline flag works for most
      vector shapes, but very intricate SmartArt may still be rendered as an image.
      In those cases, consider flattening the SmartArt in Word before conversion,
      or use `pdfOptions.setExportSmartArtAsImage(true)` to force image export.
  - name: 2. “Can I combine inline and block exports in the same document?”
    text: Unfortunately the API applies the setting globally. If you need mixed behavior,
      split the document into sections, export each section separately with different
      options, then merge the PDFs using `PdfMerger`.
  - name: 3. “Does this affect font embedding?”
    text: No. Font embedding is controlled by `pdfOptions.setEmbedFullFonts(true)`
      (default). You can safely enable or disable it without touching the inline shape
      flag.
  - name: 4. “How do I verify that shapes are really `<span>`?”
    text: Open the resulting PDF in a tool like **PDF.js** or **Adobe Acrobat** →
      **Edit PDF** → **Object Inspector**. You’ll see the shape wrapped in a `<span>`
      element in the underlying XML. If you see `<div>`, the option wasn’t applied.
  type: HowTo
tags:
- Java
- PDF
- Aspose.Words
title: Exportar formas flotantes en línea – Guía completa de conversión a PDF
url: /es/java/document-conversion-and-export/export-floating-shapes-inline-complete-guide-to-pdf-conversi/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportar formas flotantes en línea – Guía completa de conversión a PDF

¿Alguna vez necesitaste **exportar formas flotantes en línea** al convertir un documento Word a PDF? No estás solo—muchos desarrolladores se encuentran con este problema cuando sus diagramas o íconos se desplazan misteriosamente a capas separadas. La buena noticia es que una única opción de PDF puede mantener esas formas ajustadas dentro de etiquetas `<span>`, preservando el diseño exactamente como lo ves en Word.

En este tutorial recorreremos **cómo establecer opciones de PDF** en Java, te mostraremos el código exacto para **guardar Word como opciones de PDF**, y explicaremos por qué podrías querer **convertir Word a PDF en línea** en lugar de la exportación predeterminada a nivel de bloque. Al final, tendrás un fragmento listo para ejecutar que puedes insertar en cualquier proyecto Maven o Gradle.

## Lo que aprenderás

- La diferencia entre la exportación en línea `<span>` y la exportación en bloque `<div>` para formas flotantes.  
- Cómo configurar `PdfSaveOptions` para forzar el renderizado en línea.  
- Código paso a paso que carga un `.docx`, aplica la opción y genera un PDF.  
- Problemas comunes (fuentes faltantes, formas no compatibles) y cómo evitarlos.  
- Consejos para probar la salida y ampliar el enfoque a otros elementos del documento.

**Prerequisites** – necesitarás Java 8 o superior, la biblioteca Aspose.Words for Java (o cualquier API que refleje su clase `PdfSaveOptions`), y un archivo Word de muestra con formas flotantes (el tutorial usa `FloatingShapes.docx`). No se requieren otras herramientas externas.

---

## Paso 1: Cargar el documento Word de origen

Lo primero que haces es abrir el `.docx` que deseas transformar. Esto es sencillo, pero asegúrate de que la ruta sea absoluta o esté resuelta correctamente desde tu classpath.

```java
import com.aspose.words.Document;

// Step 1: Load the source Word document
Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");
```

*Why this matters:*  
Si el documento no se carga correctamente, la conversión posterior a PDF lanzará una `FileNotFoundException`. Usar `Document` garantiza que el modelo interno de objetos esté completamente poblado, incluidas las formas flotantes que aparecen en la página.

## Paso 2: Crear opciones de guardado PDF y establecer las formas flotantes como en línea

Aquí es donde ocurre la magia. Por defecto Aspose.Words exporta las formas flotantes como elementos `<div>` a nivel de bloque, lo que puede romper el flujo en PDFs basados en HTML. Configurar `setExportFloatingShapesAsInlineTag(true)` indica al motor que envuelva cada forma en un `<span>` en línea en su lugar.

```java
import com.aspose.words.PdfSaveOptions;

// Step 2: Create PDF save options and set floating shapes to be exported as inline <span> elements
PdfSaveOptions pdfOptions = new PdfSaveOptions();
pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → <span>, false → <div>
```

*Why this matters:*  
- **Layout fidelity** – Las etiquetas en línea mantienen la forma alineada con el texto circundante, evitando espacios no deseados.  
- **Searchability** – Los elementos en línea tienen más probabilidades de ser indexados correctamente por los lectores de PDF.  
- **Styling control** – Puedes apuntar al `<span>` con CSS si más adelante conviertes el PDF de nuevo a HTML.

> **Pro tip:** Si alguna vez necesitas el comportamiento antiguo de bloque para un documento específico, simplemente pasa `false` o omite la llamada por completo.

## Paso 3: Guardar el documento como PDF usando las opciones configuradas

Ahora combinas el `Document` cargado con el `PdfSaveOptions` y escribes el archivo. Esta única línea realiza el trabajo pesado.

```java
// Step 3: Save the document as a PDF using the configured options
doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);
```

*Why this matters:*  
El método `save` respeta cada bandera que establezcas en `pdfOptions`. Olvidar pasar las opciones revertirá a la exportación de bloque predeterminada, anulando el propósito de **exportar formas flotantes en línea**.

## Ejemplo completo funcionando

Juntándolo todo, aquí tienes un programa compacto que puedes compilar y ejecutar ahora mismo. Reemplaza `YOUR_DIRECTORY` con una ruta real en tu máquina.

```java
import com.aspose.words.*;

public class ExportFloatingShapesInlineDemo {
    public static void main(String[] args) {
        try {
            // Load the source Word document
            Document doc = new Document("YOUR_DIRECTORY/FloatingShapes.docx");

            // Configure PDF options to export floating shapes as inline <span>
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true);

            // Save as PDF with the above options
            doc.save("YOUR_DIRECTORY/FloatingShapes.pdf", pdfOptions);

            System.out.println("PDF created successfully with inline floating shapes.");
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Expected output** – Después de ejecutar el programa, abre `FloatingShapes.pdf`. Deberías ver las formas alineadas con el texto, sin espacio blanco adicional, y la representación HTML (si inspeccionas la estructura interna del PDF) contendrá etiquetas `<span>` alrededor de cada forma.

![Ejemplo de exportar formas flotantes en línea](https://example.com/export-inline.png "Captura de pantalla que muestra formas flotantes renderizadas en línea en el PDF")

*Texto alternativo de la imagen:* **export floating shapes inline** captura de pantalla del PDF con formas en línea.

## Preguntas frecuentes y casos límite

### 1. “¿Qué pasa si mi documento contiene SmartArt complejo?”

SmartArt se trata como un objeto de dibujo. La bandera en línea funciona para la mayoría de las formas vectoriales, pero SmartArt muy intrincado puede seguir renderizándose como una imagen. En esos casos, considera aplanar el SmartArt en Word antes de la conversión, o usa `pdfOptions.setExportSmartArtAsImage(true)` para forzar la exportación como imagen.

### 2. “¿Puedo combinar exportaciones en línea y en bloque en el mismo documento?”

Desafortunadamente la API aplica la configuración globalmente. Si necesitas un comportamiento mixto, divide el documento en secciones, exporta cada sección por separado con diferentes opciones y luego fusiona los PDFs usando `PdfMerger`.

### 3. “¿Esto afecta la incrustación de fuentes?”

No. La incrustación de fuentes se controla con `pdfOptions.setEmbedFullFonts(true)` (valor predeterminado). Puedes habilitarla o deshabilitarla sin tocar la bandera de forma en línea.

### 4. “¿Cómo verifico que las formas sean realmente `<span>`?”

Abre el PDF resultante en una herramienta como **PDF.js** o **Adobe Acrobat** → **Edit PDF** → **Object Inspector**. Verás la forma envuelta en un elemento `<span>` en el XML subyacente. Si ves `<div>`, la opción no se aplicó.

## Ampliando el enfoque – Opciones relacionadas

Mientras estás aquí, también podrías explorar otros ajustes de conversión a PDF:

| Opción | Qué hace | Caso de uso típico |
|--------|----------|--------------------|
| `setCompressImages(true)` | Reduce el tamaño de la imagen | Descargas más rápidas |
| `setUseHighQualityRendering(true)` | Mejora el renderizado vectorial | PDFs listos para imprimir |
| `setExportDocumentStructure(true)` | Añade etiquetas estructurales para accesibilidad | Cumplimiento de WCAG |
| `setSaveFormat(SaveFormat.PDF)` | Establece explícitamente el formato (raramente necesario) | Pipelines multiformato |

Estas configuraciones combinan bien con escenarios de **convertir word a pdf en línea** donde necesitas tanto fidelidad de diseño como rendimiento.

## Probando tu conversión

1. **Visual check** – Abre el PDF en dos visores (Chrome y Adobe Reader) para asegurarte de que las formas estén alineadas.  
2. **Automated diff** – Usa una biblioteca como `pdfbox` para extraer el XML y afirmar la presencia de etiquetas `<span>`.  
3. **Performance benchmark** – Mide el tiempo tomado con y sin `setCompressImages` para ver la compensación.

Un ejemplo rápido de JUnit:

```java
@Test
public void testInlineExport() throws Exception {
    Document doc = new Document("src/test/resources/FloatingShapes.docx");
    PdfSaveOptions opts = new PdfSaveOptions();
    opts.setExportFloatingShapesAsInlineTag(true);
    ByteArrayOutputStream out = new ByteArrayOutputStream();
    doc.save(out, opts);
    String pdfXml = new String(out.toByteArray(), StandardCharsets.UTF_8);
    assertTrue(pdfXml.contains("<span"));
}
```

## Conclusión

Ahora tienes una solución sólida, de extremo a extremo, para **exportar formas flotantes en línea** cuando **conviertes Word a PDF en línea**. Configurando `PdfSaveOptions` controlas la etiqueta HTML usada para cada forma, manteniendo tus PDFs ordenados y buscables. Recuerda probar la salida, ajustar opciones relacionadas como la compresión de imágenes y manejar casos límite como SmartArt complejo.

¿Listo para el siguiente paso? Prueba aplicar la misma técnica para **exportar tablas flotantes en línea** o experimenta con PDFs con estilo CSS usando `HtmlSaveOptions` de Aspose. El mismo patrón—cargar, configurar, guardar—se aplica a casi cualquier escenario de documento a PDF.

¿Tienes más preguntas sobre **cómo establecer opciones de pdf** o necesitas ayuda con **guardar word como opciones de pdf** para otra biblioteca? Deja un comentario, ¡y feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Convertir Word a PDF con Aspose.Words for Java](/words/english/java/document-converting/)
- [Cómo guardar documento como pdf con Aspose.Words for Java](/words/english/java/document-loading-and-saving/saving-documents-as-pdf/)
- [Exportar estructura del documento Word a documento PDF](/words/english/net/programming-with-pdfsaveoptions/export-document-structure/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}