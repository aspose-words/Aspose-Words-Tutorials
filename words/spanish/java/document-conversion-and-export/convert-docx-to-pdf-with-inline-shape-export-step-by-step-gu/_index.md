---
category: general
date: 2026-02-18
description: Aprende a convertir DOCX a PDF y a guardar Word como PDF mientras preservas
  las formas flotantes. Esta guía muestra cómo exportar correctamente las formas.
draft: false
keywords:
- convert docx to pdf
- save word as pdf
- how to export shapes
language: es
og_description: Convierte DOCX a PDF y aprende cómo exportar formas. Sigue este tutorial
  completo para guardar Word como PDF con etiquetado adecuado.
og_title: Convertir DOCX a PDF – Guía de exportación de formas en línea
tags:
- Aspose.Words
- Java
- PDF conversion
title: Convertir DOCX a PDF con exportación de formas en línea – Guía paso a paso
url: /es/java/document-conversion-and-export/convert-docx-to-pdf-with-inline-shape-export-step-by-step-gu/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Convertir DOCX a PDF – Guía de Exportación de Formas en Línea

¿Alguna vez necesitaste **convertir DOCX a PDF** y te preocupaba que tus imágenes flotantes o cuadros de texto desaparecieran o se desplazaran? No estás solo. En muchos proyectos —piense en generadores de informes automáticos o pipelines de procesamiento por lotes— preservar el diseño exacto de un documento Word es innegociable.  

¿La buena noticia? Con unas pocas líneas de código puedes **guardar Word como PDF** y controlar si esas formas flotantes se convierten en etiquetas en línea o permanecen como elementos a nivel de bloque. A continuación verás exactamente **cómo exportar formas** de la manera que deseas, además de una serie de consejos que te evitarán errores comunes.

---

## Lo que aprenderás

* Cargar un archivo `.docx` desde el disco.  
* Configurar `PdfSaveOptions` para que las formas flotantes se exporten como etiquetas en línea.  
* Guardar el PDF resultante en una carpeta de tu elección.  
* Entender por qué la bandera `setExportFloatingShapesAsInlineTag` es importante y cuándo podrías cambiarla.  

Sin servicios externos, sin una UI mágica de “clic‑para‑descargar”, solo código Java puro que puedes incorporar a cualquier proyecto Maven o Gradle.

---

## Requisitos previos

| Requisito | Por qué es importante |
|-------------|----------------|
| **Aspose.Words for Java** (v23.12 o posterior) | Proporciona las clases `Document` y `PdfSaveOptions` usadas en el ejemplo. |
| **JDK 8+** | La biblioteca está compilada para Java 8 y versiones superiores; entornos más antiguos lanzarán `UnsupportedClassVersionError`. |
| **Un archivo DOCX** con al menos una forma flotante (imagen, cuadro de texto, WordArt) | Para ver el efecto de la opción de exportación de formas, necesitas un documento que realmente contenga objetos flotantes. |

Si ya tienes estos elementos, genial—¡vamos al grano!

---

## Paso 1 – Cargar el documento fuente  

Primero creamos una instancia de `Document` que apunta al `.docx` que deseas convertir. El constructor lee el archivo en memoria, analiza el paquete OpenXML y prepara el modelo de objetos interno.

```java
import com.aspose.words.Document;
import com.aspose.words.SaveFormat;

// Adjust the path to your environment
String inputPath = "YOUR_DIRECTORY/input.docx";

Document doc = new Document(inputPath);
```

> **Consejo profesional:** Si procesas muchos archivos en un bucle, reutiliza un solo objeto `Document` solo después de haber llamado a `doc.close()` (o deja que el recolector de basura lo haga). Esto evita fugas de manejadores de archivo en Windows.

---

## Paso 2 – Configurar las opciones de guardado PDF para exportar formas  

El corazón del tutorial está aquí. `PdfSaveOptions` te permite dictar cómo se comporta la conversión. Establecer `setExportFloatingShapesAsInlineTag(true)` obliga a que cada forma flotante se trate como un elemento *en línea* en la estructura de etiquetas del PDF. Eso significa que los lectores de pantalla leerán la forma en el mismo orden que el texto circundante, lo cual suele ser necesario para cumplir con la accesibilidad.

```java
import com.aspose.words.PdfSaveOptions;

PdfSaveOptions pdfOptions = new PdfSaveOptions();
// true → inline tagging (shape behaves like a character)
// false → block‑level tagging (shape sits in its own block)
pdfOptions.setExportFloatingShapesAsInlineTag(true);
```

**¿Cuándo lo establecerías a `false`?**  
Si tu PDF está destinado solo a distribución impresa y deseas que las formas mantengan su posición original sin afectar el orden lógico de lectura, podrías preferir el etiquetado a nivel de bloque. El valor predeterminado es `false`, así que habilitamos explícitamente el comportamiento en línea para este tutorial.

---

## Paso 3 – Guardar el documento como PDF  

Ahora que las opciones están listas, llama a `save` con el nombre de archivo de destino y el objeto de opciones. La biblioteca se encarga del trabajo pesado: motor de diseño, incrustación de fuentes y generación de etiquetas.

```java
String outputPath = "YOUR_DIRECTORY/shapes.pdf";
doc.save(outputPath, pdfOptions);
```

Después de que la llamada finalice, encontrarás `shapes.pdf` en la carpeta especificada. Ábrelo en Adobe Acrobat o cualquier visor de PDF que muestre etiquetas (normalmente bajo **Archivo → Propiedades → Etiquetas**) y verás que la forma flotante aparece como una etiqueta en línea.

---

## Ejemplo completo y ejecutable  

Juntando todo, aquí tienes una clase Java autosuficiente que puedes compilar y ejecutar. Asegúrate de que el JAR de Aspose.Words esté en tu classpath.

```java
import com.aspose.words.*;

public class DocxToPdfWithShapes {
    public static void main(String[] args) {
        try {
            // 1️⃣ Load the source DOCX
            String inputPath = "YOUR_DIRECTORY/input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Configure PDF options – export floating shapes as inline tags
            PdfSaveOptions pdfOptions = new PdfSaveOptions();
            pdfOptions.setExportFloatingShapesAsInlineTag(true); // true → inline tagging

            // 3️⃣ Save as PDF
            String outputPath = "YOUR_DIRECTORY/shapes.pdf";
            doc.save(outputPath, pdfOptions);

            System.out.println("✅ Conversion complete! PDF saved to: " + outputPath);
        } catch (Exception e) {
            System.err.println("❌ Something went wrong: " + e.getMessage());
            e.printStackTrace();
        }
    }
}
```

**Resultado esperado:**  
- El archivo PDF contiene el mismo contenido textual que el DOCX original.  
- Cualquier imagen o cuadro de texto flotante ahora está etiquetado *en línea*, lo que significa que aparece en el orden de lectura en lugar de como bloques separados.  
- Si abres el panel **Etiquetas** del PDF, verás un elemento `<Figure>` anidado dentro de un `<Paragraph>` —exactamente lo que garantiza `setExportFloatingShapesAsInlineTag(true)`.

---

## Preguntas frecuentes y casos límite  

### 1️⃣ ¿Esto funciona con archivos DOCX protegidos con contraseña?  
Sí—solo proporciona la contraseña antes de cargar:

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setPassword("mySecret");
Document doc = new Document(inputPath, loadOptions);
```

### 2️⃣ ¿Qué pasa con imágenes SVG o EMF dentro del archivo Word?  
Aspose.Words rasteriza automáticamente los gráficos vectoriales al guardar en PDF. Si necesitas que permanezcan como vectores, establece:

```java
pdfOptions.setRasterizeTransformedElements(false);
```

### 3️⃣ ¿Cómo conservo los hipervínculos al convertir?  
Los enlaces se mantienen por defecto. Sin embargo, si deshabilitas las etiquetas (`pdfOptions.setSaveFormat(SaveFormat.PDF)` sin opciones), podrías perder la estructura lógica. Mantén el objeto `PdfSaveOptions` para conservar tanto etiquetas como enlaces.

### 4️⃣ ¿Puedo procesar por lotes una carpeta de archivos DOCX?  
Absolutamente. Envuelve la lógica `DocxToPdfWithShapes` en un bucle que itere sobre `Files.list(Paths.get("YOUR_DIRECTORY"))`. Recuerda manejar excepciones por archivo para que un documento defectuoso no detenga toda la ejecución.

---

## Consejos de la práctica  

* **Cuidado con las fuentes faltantes.** Si el DOCX fuente usa una fuente personalizada que no está instalada en el servidor, el PDF sustituirá una fuente de respaldo, lo que podría romper el diseño. Usa `pdfOptions.setFontEmbeddingMode(FontEmbeddingMode.EMBED_ALL)` para forzar la incrustación.  
* **Pruebas de accesibilidad.** Después de la conversión, ejecuta el **Comprobador de accesibilidad** de Acrobat. El etiquetado en línea suele mejorar la puntuación, pero aún podrías necesitar añadir texto alternativo a las imágenes manualmente.  
* **Consejo de rendimiento:** Para documentos grandes (más de 100 páginas), habilita `pdfOptions.setMemoryOptimization(true)` para reducir el uso de heap.

---

## Confirmación visual  

A continuación se muestra una captura rápida del PDF abierto en Adobe Acrobat, donde la forma etiquetada en línea está resaltada en el panel **Etiquetas**.

![Convert DOCX to PDF example output](image.png)

*Texto alternativo: salida de ejemplo de conversión de docx a pdf que muestra etiquetas de forma en línea.*

---

## Conclusión  

Ahora sabes **cómo convertir DOCX a PDF** controlando la forma en que se exportan los objetos flotantes. Al alternar `setExportFloatingShapesAsInlineTag`, decides si las formas forman parte del orden de lectura o permanecen como bloques independientes—crucial tanto para la accesibilidad como para la fidelidad visual.  

A partir de aquí puedes:

* **Guardar Word como PDF** en lote para archivado.  
* Experimentar con otras `PdfSaveOptions` como `setCompliance(PdfCompliance.PDF_A_1B)` para preservación a largo plazo.  
* Profundizar en **cómo exportar formas** explorando la documentación completa de Aspose.Words o probando la bandera `setExportDocumentStructure(true)` para árboles de etiquetas más ricos.

Pruébalo, ajusta las opciones y haz que tus PDFs se vean exactamente como los necesitas. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}