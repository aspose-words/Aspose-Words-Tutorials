---
category: general
date: 2026-06-20
description: cómo establecer una devolución de llamada en Aspose.Words Java para detectar
  fuentes faltantes y personalizar la carga del documento. Aprende paso a paso el
  manejo de advertencias de sustitución de fuentes.
draft: false
keywords:
- how to set callback
- detect missing fonts
- handle missing fonts
- customize document loading
language: es
og_description: Cómo configurar una devolución de llamada en Aspose.Words Java para
  detectar fuentes faltantes, manejar sustituciones y personalizar la carga de documentos.
  Guía completa con código.
og_title: Cómo establecer la devolución de llamada – Detectar fuentes faltantes en
  Aspose.Words Java
schemas:
- author: Aspose
  dateModified: '2026-06-20'
  description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  headline: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  type: TechArticle
- description: how to set callback in Aspose.Words Java to detect missing fonts and
    customize document loading. Learn step‑by‑step handling of font substitution warnings.
  name: how to set callback in Aspose.Words Java – Detect and Handle Missing Fonts
  steps:
  - name: What if I want the program to stop loading when a font is missing?
    text: 'Throw an exception inside the `warning` method:'
  - name: Does this work for PDFs generated from DOCX?
    text: Absolutely. The callback fires during the **loading** phase, which is identical
      for all output formats (`save` to PDF, DOCX, HTML, etc.). As long as you load
      the source document with the same `LoadOptions`, you’ll catch missing fonts
      before they affect the final PDF.
  - name: Can I capture other warning types (e.g., image conversion)?
    text: Yes—`WarningInfo.getWarningType()` can be compared against other enums like
      `WarningType.IMAGE_CONVERSION`. Just add more `if` branches in the callback.
  - name: Is there a performance impact?
    text: Negligible. The callback runs synchronously during loading, and the extra
      checks are lightweight. If you’re loading thousands of documents, you might
      want to disable warnings in production by setting `loadOptions.setWarningCallback(null);`.
  - name: What’s Next?
    text: '- Explore **font substitution tables** for bulk mapping of many missing
      fonts. - Combine this callback with **document validation** to enforce style
      guides. - Try **custom warning callbacks** that write to a log file or a monitoring
      system instead of `System.out`.'
  type: HowTo
tags:
- Aspose.Words
- Java
- Document Processing
title: Cómo establecer una devolución de llamada en Aspose.Words Java – Detectar y
  manejar fuentes faltantes
url: /es/java/document-loading-and-saving/how-to-set-callback-in-aspose-words-java-detect-and-handle-m/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# cómo establecer callback en Aspose.Words Java – Detectar y manejar fuentes faltantes

¿Alguna vez te has preguntado **cómo establecer callback** en Aspose.Words Java para poder detectar fuentes faltantes antes de que arruinen tu PDF o DOCX? No eres el único. Las advertencias de fuentes faltantes pueden corromper silenciosamente el diseño, y sin un callback de advertencia adecuado podrías no notar el problema hasta que el documento final se vea mal.  

En este tutorial recorreremos un ejemplo completo, listo para ejecutar, que **detecta fuentes faltantes**, **maneja fuentes faltantes** de forma elegante y te muestra cómo **personalizar la carga del documento** con un callback de advertencia. Al final tendrás una clase Java autónoma que puedes incorporar a cualquier proyecto—sin necesidad de buscar documentación adicional.

## Qué necesitarás

- Java 8 o superior (el código también funciona con Java 11+)  
- Biblioteca Aspose.Words para Java (versión 23.9 o posterior)  
- Un archivo DOCX que haga referencia a una fuente que no tengas instalada (por ejemplo, una fuente corporativa personalizada)  

Si aún no has añadido Aspose.Words a tu proyecto Maven, simplemente incluye:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version>
</dependency>
```

Eso es todo—sin plugins extra, sin dependencias nativas.

---

## Paso 1: Entender el mecanismo WarningCallback

El **warning callback** es la forma que tiene Aspose.Words de avisarte cuando ocurre algo inesperado al cargar o guardar un documento. Al implementar `IWarningCallback` obtienes control total sobre lo que se registra, se ignora o incluso se convierte en una excepción.

> **Por qué es importante:**  
> Cuando falta una fuente, Aspose sustituye una fuente de reserva. El resultado visual puede ser drásticamente diferente, especialmente en PDFs con mucha identidad de marca. Al capturar `WarningType.FONT_SUBSTITUTION`, puedes registrar el nombre exacto de la fuente, decidir si abortar o sustituir tu propia fuente personalizada mediante código.

---

## Paso 2: Crear una instancia de LoadOptions

`LoadOptions` es el punto de entrada para personalizar la carga del documento. Adjuntarás el callback a este objeto antes de cargar realmente el archivo.

```java
// Step 2: Prepare LoadOptions
LoadOptions loadOptions = new LoadOptions();
```

En este punto `loadOptions` es solo un contenedor simple—todavía no ocurre nada. La verdadera magia comienza cuando conectamos el callback.

---

## Paso 3: Implementar y adjuntar el callback

A continuación tienes una clase anónima compacta que implementa `IWarningCallback`. Imprime una línea amigable en la consola cada vez que ocurre una sustitución de fuente.

```java
// Step 3: Attach a warning callback to capture font substitution warnings
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Detect missing fonts
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Missing Font] " + info.getDescription());
            // Optional: you could throw an exception here to abort loading
            // throw new RuntimeException("Font missing: " + info.getDescription());
        }
    }
});
```

> **Consejo profesional:** Si deseas **manejar fuentes faltantes** proporcionando un reemplazo, también puedes establecer `FontSettings` en el `LoadOptions` y mapear fuentes faltantes a una fuente de reserva conocida.

---

## Paso 4: Cargar el documento con tus opciones personalizadas

Ahora que el callback está configurado, carga el documento. Si el archivo hace referencia a una fuente que no tienes, verás la advertencia impresa.

```java
// Step 4: Load the document using the configured LoadOptions
String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
Document document = new Document(docPath, loadOptions);
```

Al ejecutar el programa, la consola podría mostrar:

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Arial".
```

Esa línea demuestra que has **detectado fuentes faltantes** con éxito y que ahora puedes **manejar fuentes faltantes** como consideres apropiado.

---

## Paso 5: Opcional – Reemplazar fuentes faltantes con una fuente conocida

Si prefieres reemplazar automáticamente cualquier fuente faltante con, por ejemplo, `Times New Roman`, puedes añadir un objeto `FontSettings`:

```java
// Optional Step 5: Map missing fonts to a fallback
FontSettings fontSettings = new FontSettings();
fontSettings.setMissingFontNotification(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // This will be called for each missing font
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("[Auto‑Replace] " + info.getDescription());
        }
    }
});
// Force substitution to Times New Roman
fontSettings.getSubstitutionSettings().getTableSubstitution().addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
loadOptions.setFontSettings(fontSettings);
```

Ahora el documento se carga y cualquier referencia a `MyCustomFont` se sustituye silenciosamente por `Times New Roman`. La consola seguirá indicando qué se reemplazó, manteniéndote informado.

---

## Ejemplo completo funcionando

A continuación tienes una única clase Java que incorpora todos los pasos anteriores. Copia‑pega en tu IDE, ajusta `docPath` y ejecuta.

```java
import com.aspose.words.*;

public class DetectMissingFontsDemo {
    public static void main(String[] args) {
        try {
            // 1️⃣ Create LoadOptions
            LoadOptions loadOptions = new LoadOptions();

            // 2️⃣ Attach warning callback (detect missing fonts)
            loadOptions.setWarningCallback(new IWarningCallback() {
                @Override
                public void warning(WarningInfo info) {
                    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                        System.out.println("[Missing Font] " + info.getDescription());
                    }
                }
            });

            // 3️⃣ (Optional) Set up automatic font substitution
            FontSettings fontSettings = new FontSettings();
            fontSettings.getSubstitutionSettings()
                        .getTableSubstitution()
                        .addSubstitutes("MyCustomFont", new String[]{"Times New Roman"});
            loadOptions.setFontSettings(fontSettings);

            // 4️⃣ Load the document with custom loading behavior
            String docPath = "YOUR_DIRECTORY/doc-with-missing-font.docx";
            Document doc = new Document(docPath, loadOptions);

            // 5️⃣ Save to PDF to see the final result (optional)
            doc.save("output.pdf");
            System.out.println("Document loaded and saved successfully.");

        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

**Salida esperada**

```
[Missing Font] Font substitution: The font "MyCustomFont" was not found. Substituted with "Times New Roman".
Document loaded and saved successfully.
```

Ahora dispones de una forma reproducible de **detectar fuentes faltantes**, **manejar fuentes faltantes** y **personalizar la carga del documento**—todo aprendiendo **cómo establecer callback** correctamente.

---

## Preguntas frecuentes

### ¿Qué pasa si quiero que el programa deje de cargar cuando falta una fuente?

Lanza una excepción dentro del método `warning`:

```java
throw new RuntimeException("Critical: Missing font - " + info.getDescription());
```

El bloque `catch` al final la capturará, y podrás decidir cómo registrar o alertar al usuario.

### ¿Esto funciona para PDFs generados a partir de DOCX?

Absolutamente. El callback se dispara durante la fase de **carga**, que es idéntica para todos los formatos de salida (`save` a PDF, DOCX, HTML, etc.). Mientras cargues el documento fuente con los mismos `LoadOptions`, capturarás fuentes faltantes antes de que afecten al PDF final.

### ¿Puedo capturar otros tipos de advertencia (p. ej., conversión de imágenes)?

Sí—`WarningInfo.getWarningType()` puede compararse con otros enums como `WarningType.IMAGE_CONVERSION`. Simplemente añade más ramas `if` en el callback.

### ¿Hay impacto en el rendimiento?

Negligible. El callback se ejecuta de forma síncrona durante la carga, y las comprobaciones adicionales son ligeras. Si estás cargando miles de documentos, podrías desactivar las advertencias en producción estableciendo `loadOptions.setWarningCallback(null);`.

---

## Visión general visual

![how to set callback example in Aspose.Words Java](https://example.com/images/callback-diagram.png "how to set callback")

*El diagrama ilustra el flujo: `LoadOptions` → `IWarningCallback` → Carga del documento → Manejo de sustitución de fuentes.*

---

## Conclusión

Hemos cubierto **cómo establecer callback** en Aspose.Words Java, demostrado **cómo detectar fuentes faltantes**, mostrado formas prácticas de **manejar fuentes faltantes** y explicado cómo **personalizar la carga del documento** con `LoadOptions`.  

Con este conocimiento puedes proteger tus canalizaciones de documentos contra sustituciones de fuentes silenciosas, mantener la coherencia de la marca y ofrecer a tus usuarios una retroalimentación clara cuando algo falla.

### ¿Qué sigue?

- Explora **tablas de sustitución de fuentes** para mapear en bloque muchas fuentes faltantes.  
- Combina este callback con **validación de documentos** para aplicar guías de estilo.  
- Prueba **callbacks de advertencia personalizados** que escriban en un archivo de registro o en un sistema de monitoreo en lugar de `System.out`.  

¡Experimenta y cuéntanos cómo personalizaste el callback para tus propios proyectos! ¡Feliz codificación!

---


## ¿Qué deberías aprender a continuación?


Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funcionalidades adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [How to Set LoadOptions in Aspose.Words for Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [How to Capture Fonts in Aspose.Words – Complete Guide](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}