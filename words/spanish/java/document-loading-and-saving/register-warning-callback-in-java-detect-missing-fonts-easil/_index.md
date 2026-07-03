---
category: general
date: 2026-07-03
description: Registre una devolución de llamada de advertencia en Java para detectar
  fuentes faltantes al procesar documentos Word. Aprenda el manejo de advertencias
  de Aspose.Words y la detección de sustitución de fuentes.
draft: false
keywords:
- register warning callback
- detect missing fonts
- font substitution warning
- Aspose.Words warning callback
- Java missing font detection
- document font handling
language: es
og_description: Registre una devolución de llamada de advertencia en Java para detectar
  fuentes faltantes. Esta guía muestra cómo capturar advertencias de sustitución de
  fuentes con Aspose.Words.
og_title: Registrar devolución de llamada de advertencia en Java – Detectar fuentes
  faltantes
schemas:
- author: Aspose
  dateModified: '2026-07-03'
  description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  headline: Register warning callback in Java – Detect missing fonts easily
  type: TechArticle
- description: Register warning callback in Java to detect missing fonts while processing
    Word docs. Learn Aspose.Words warning handling and font substitution detection.
  name: Register warning callback in Java – Detect missing fonts easily
  steps:
  - name: Why this matters
    text: '* **Visibility:** Without a callback, the substitution happens silently,
      and you might ship a document with the wrong appearance. * **Automation:** In
      batch pipelines you can log every missing‑font incident and later feed the list
      to a font‑installation script. * **Compliance:** Some industries (e.g'
  - name: Expected console output
    text: 'Assuming `input.docx` references the font *“Comic Sans MS”* which isn’t
      installed, you’ll see something like:'
  - name: Multiple missing fonts
    text: If a document references several unavailable fonts, the callback will fire
      once per font. You can aggregate the messages into a list if you need a summary
      report later.
  - name: Controlling substitution behavior
    text: 'Sometimes you *do* want to force a particular fallback font. Use `FontSettings`
      before loading the document:'
  - name: Performance considerations
    text: 'Registering a warning callback introduces a tiny overhead—only a few nanoseconds
      per warning. In high‑throughput services (e.g., converting thousands of docs
      per hour) the impact is negligible. However, if you’re processing millions,
      consider disabling warnings after you’ve verified the font set is '
  - name: Cross‑platform notes
    text: The callback works identically on Windows, macOS, and Linux. The only difference
      is the set of fonts available on each OS. If you run the same job on multiple
      agents, you might see different substitution messages. To keep results deterministic,
      ship a **custom font folder** and point Aspose.Words to
  type: HowTo
tags:
- Aspose.Words
- Java
- Fonts
title: Registrar callback de advertencia en Java – Detectar fuentes faltantes fácilmente
url: /es/java/document-loading-and-saving/register-warning-callback-in-java-detect-missing-fonts-easil/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar callback de advertencia en Java – Detectar fuentes faltantes fácilmente

¿Alguna vez te has preguntado cómo **registrar un callback de advertencia** para poder **detectar fuentes faltantes** al convertir o editar documentos Word? No eres el único. Las fuentes faltantes pueden corromper silenciosamente los diseños, convertir un informe elegante en un desastre desordenado, y la mayoría de los desarrolladores ni siquiera se dan cuenta hasta que el PDF final se ve mal.  

En este tutorial recorreremos un ejemplo completo, listo‑para‑ejecutar, que te muestra exactamente cómo conectar al sistema de advertencias de Aspose.Words for Java, capturar esas molestas alertas de sustitución de fuentes y registrarlas o reaccionar como necesites. No hay atajos vagos de “ver la documentación”; solo código puro, listo para copiar y pegar, y la lógica detrás de cada línea.

## Requisitos previos

Antes de sumergirnos, asegúrate de tener:

* **Java 17** (o cualquier JDK reciente) instalado y `JAVA_HOME` configurado.  
* **Aspose.Words for Java** JAR (descárgalo desde el sitio oficial o inclúyelo vía Maven).  
* Un archivo `.docx` de muestra que haga referencia a una fuente **no** instalada en tu máquina—esto disparará la advertencia.  
* Tu IDE favorito o un simple editor de texto y herramientas de compilación por línea de comandos.

Eso es todo. Sin frameworks adicionales, sin servicios externos. ¿Listo? Comencemos.

## Paso 1: Configurar el proyecto y agregar Aspose.Words

Si estás usando Maven, agrega la siguiente dependencia a tu `pom.xml`:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>24.10</version> <!-- use the latest stable version -->
</dependency>
```

Para Gradle, coloca esto en `build.gradle`:

```groovy
implementation 'com.aspose:aspose-words:24.10'
```

Si prefieres la ruta manual, simplemente coloca el `aspose-words-24.10.jar` en tu classpath.  
**Consejo profesional:** mantén el JAR junto a tu carpeta `src`; simplifica el comando `javac` más adelante.

## Paso 2: Cargar el documento que puede contener fuentes faltantes

Lo primero que haces es crear un objeto `Document` que apunte al archivo fuente. Este paso es sencillo, pero también es donde la biblioteca escanea el archivo y *potencialmente* descubre fuentes faltantes.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // Adjust the path to point at your test document
        String inputPath = "YOUR_DIRECTORY/input.docx";

        // Load the document – Aspose.Words will start parsing it now
        Document doc = new Document(inputPath);
```

Aquí, `Document` es el punto de entrada para todas las operaciones de Aspose.Words. Cuando se ejecuta el constructor, la biblioteca analiza el XML del documento, resuelve las fuentes y, si alguna fuente no está disponible, *encola* una advertencia que luego podemos capturar.

## Paso 3: Registrar un callback de advertencia para capturar alertas de sustitución de fuentes

Ahora, la estrella del espectáculo: **registrar un callback de advertencia**. Aspose.Words te permite conectar una implementación de la interfaz `IWarningCallback`. Cada vez que el motor encuentra una situación que vale la pena señalar—como una fuente faltante—invoca tu método `warning`.

```java
        // Register the warning callback
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We’re only interested in font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                }
            }
        });
```

### Por qué es importante

* **Visibilidad:** Sin un callback, la sustitución ocurre silenciosamente, y podrías entregar un documento con una apariencia incorrecta.  
* **Automatización:** En pipelines por lotes puedes registrar cada incidente de fuente faltante y luego alimentar la lista a un script de instalación de fuentes.  
* **Cumplimiento:** Algunas industrias (p. ej., legal) requieren pruebas de que se usaron las fuentes originales o se sustituyeron correctamente.

Observa que filtramos por `WarningType.FONT_SUBSTITUTION`. Aspose.Words emite muchos tipos de advertencia—desbordamiento de diseño, características obsoletas, etc.—pero solo nos interesan los que indican que una fuente estaba faltando. Esto mantiene la consola limpia y se centra en el objetivo de **detectar fuentes faltantes**.

## Paso 4: Guardar el documento y activar el callback

Cuando finalmente llamas a `save`, el motor finaliza cualquier carga diferida y dispara el callback de advertencia por cada fuente faltante que descubrió durante la operación de guardado.

```java
        // Save the document – this is where the warning callback gets invoked
        String outputPath = "YOUR_DIRECTORY/output.docx";
        doc.save(outputPath);

        System.out.println("✅ Document saved to " + outputPath);
    }
}
```

### Salida esperada en la consola

Suponiendo que `input.docx` haga referencia a la fuente *“Comic Sans MS”* que no está instalada, verás algo como:

```
⚠️ Font substituted: Font 'Comic Sans MS' is not available. Substituted with 'Arial'.
✅ Document saved to YOUR_DIRECTORY/output.docx
```

Si el documento fuente ya contiene solo fuentes instaladas, la línea de advertencia simplemente nunca aparece—lo que significa que **detectar fuentes faltantes** se completó silenciosamente.

![Salida de consola mostrando el registro del callback de advertencia en acción y detección de fuentes faltantes](register-warning-callback-output.png)

*Texto alternativo de la imagen: salida del registro del callback de advertencia mostrando detección de fuentes faltantes*

## Paso 5: Manejo de casos límite y consejos de mejores prácticas

### Múltiples fuentes faltantes

Si un documento hace referencia a varias fuentes no disponibles, el callback se disparará una vez por fuente. Puedes agregar los mensajes en una lista si necesitas un informe resumido más adelante.

```java
List<String> missingFonts = new ArrayList<>();
doc.setWarningCallback(info -> {
    if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
        missingFonts.add(info.getDescription());
    }
});
// After saving
if (!missingFonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    missingFonts.forEach(System.out::println);
}
```

### Controlar el comportamiento de sustitución

A veces *sí* deseas forzar una fuente de respaldo específica. Usa `FontSettings` antes de cargar el documento:

```java
FontSettings settings = new FontSettings();
settings.setSubstitutionSettings(new FontSubstitutionSettings()
        .addSubstitutes("Comic Sans MS", "Times New Roman"));
doc.setFontSettings(settings);
```

Ahora el callback seguirá disparándose, pero sabrás exactamente qué fuente se usará.

### Consideraciones de rendimiento

Registrar un callback de advertencia introduce una pequeña sobrecarga—solo unos pocos nanosegundos por advertencia. En servicios de alto rendimiento (p. ej., convirtiendo miles de documentos por hora) el impacto es insignificante. Sin embargo, si procesas millones, considera desactivar las advertencias después de haber verificado que el conjunto de fuentes está completo:

```java
doc.setWarningCallback(null); // turn off after initial scan
```

### Notas multiplataforma

El callback funciona idénticamente en Windows, macOS y Linux. La única diferencia es el conjunto de fuentes disponible en cada SO. Si ejecutas el mismo trabajo en varios agentes, podrías ver diferentes mensajes de sustitución. Para mantener resultados determinísticos, entrega una **carpeta de fuentes personalizada** y apunta Aspose.Words a ella mediante `FontSettings.setFontsFolder("path/to/fonts", true);`.

## Ejemplo completo y ejecutable

A continuación se muestra la clase Java completa que puedes copiar‑pegar en `src/main/java/FontWarningDemo.java`. Incluye todas las importaciones, manejo de errores y comentarios que necesitas para ejecutarla de inmediato.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

/**
 * Demonstrates how to register a warning callback in Aspose.Words for Java
 * to detect missing fonts during document processing.
 */
public class FontWarningDemo {
    public static void main(String[] args) throws Exception {
        // 1️⃣ Paths – adjust to your environment
        String inputPath = "YOUR_DIRECTORY/input.docx";
        String outputPath = "YOUR_DIRECTORY/output.docx";

        // 2️⃣ Load the document (parsing begins here)
        Document doc = new Document(inputPath);

        // 3️⃣ Optional: set a custom font folder if you ship fonts with your app
        // FontSettings fs = new FontSettings();
        // fs.setFontsFolder("fonts", true);
        // doc.setFontSettings(fs);

        // 4️⃣ Register the warning callback to catch missing‑font warnings
        List<String> missingFonts = new ArrayList<>();
        doc.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // Log to console
                    System.out.println("⚠️ Font substituted: " + info.getDescription());
                    // Collect for later reporting
                    missingFonts.add(info.getDescription());
                }
            }
        });

        // 5️⃣ Save the document – triggers the callback
        doc.save(outputPath);
        System.out.println("✅ Document saved to " + outputPath);

        // 6️⃣ Post‑save reporting (if any fonts were missing)
        if (!missingFonts.isEmpty()) {
            System.out.println("\nSummary of missing fonts:");
            missingFonts.forEach(System.out::println);
        } else {
            System.out.println("\nNo missing fonts detected.");
        }
    }
}
```

Compila y ejecuta:

```bash
javac -cp "aspose-words-24.10.jar" FontWarningDemo.java
java -cp ".:aspose-words-24.10.jar" FontWarningDemo
```

Deberías ver las líneas de advertencia (si las hay) seguidas del mensaje de éxito.

## Conclusión

Acabas de aprender **cómo registrar un callback de advertencia** en Java para **detectar fuentes faltantes** al trabajar con Aspose.Words. Al conectar al sistema de advertencias de la biblioteca obtienes total visibilidad de los eventos de sustitución de fuentes, puedes registrarlos para cumplimiento y, incluso, reemplazar fuentes programáticamente si es necesario.

A partir de aquí podrías explorar:

* **Detectar fuentes faltantes** en un lote de archivos usando un bucle o flujos paralelos.  
* Integrar el callback con un framework de registro (SLF4J, Log4j) para informes de nivel producción.  
* Usar `FontSettings` para aplicar una paleta de fuentes corporativa y evitar sustituciones no deseadas.

Pruébalo: cambia el documento de entrada, prueba diferentes escenarios de fuentes faltantes y observa cómo se comporta el callback. Si encuentras alguna anomalía, deja un comentario abajo; ¡feliz codificación!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Callback de advertencia en documento Word](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Aspose Words Java Callback Ahorro personalizado](/words/hindi/java/images-shapes/aspose-words-java-callback-custom-savings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}