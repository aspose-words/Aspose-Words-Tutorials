---
category: general
date: 2026-05-30
description: Registre una devolución de llamada de advertencia en Java para rastrear
  fuentes faltantes y personalizar la carga de documentos con Aspose.Words. Aprenda
  la solución completa paso a paso.
draft: false
keywords:
- register warning callback
- track missing fonts
- customize document loading
language: es
og_description: Registre una devolución de llamada de advertencia en Java para rastrear
  fuentes faltantes y personalizar la carga de documentos. Guía completa con código
  y explicaciones.
og_title: Registrar devolución de llamada de advertencia en Java – Rastrear fuentes
  faltantes
schemas:
- author: Aspose
  dateModified: '2026-05-30'
  description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  headline: Register warning callback in Java – Track missing fonts
  type: TechArticle
- description: Register warning callback in Java to track missing fonts and customize
    document loading with Aspose.Words. Learn the full step‑by‑step solution.
  name: Register warning callback in Java – Track missing fonts
  steps:
  - name: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
    text: '**Get real‑time insight** – every `FONT_SUBSTITUTION` warning is delivered
      instantly.'
  - name: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
    text: '**Log or react** – you could log to a file, raise an alert, or even replace
      the font programmatically.'
  - name: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
    text: '**Maintain clean output** – knowing which fonts are missing lets you fix
      the source document before publishing.'
  type: HowTo
- questions:
  - answer: It’s the interface Aspose.Words uses for all warning types, giving you
      a single entry point for many possible issues.
    question: Why `IWarningCallback`?
  - answer: Aspose.Words only allows one warning handler. If you need to log to both
      a file and the console, implement a composite callback that forwards the warning
      to multiple destinations.
    question: Multiple callbacks?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Font handling
title: Registrar callback de advertencia en Java – Rastrear fuentes faltantes
url: /es/java/document-loading-and-saving/register-warning-callback-in-java-track-missing-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Registrar callback de advertencia en Java – Rastrear fuentes faltantes

¿Alguna vez te has preguntado cómo **rastrear fuentes faltantes** al cargar un documento Word con Aspose.Words para Java? Tal vez hayas visto esas sustituciones silenciosas de fuentes y pensado: “¿Qué le pasó a mi diseño?”. La buena noticia es que no tienes que adivinar. Al **registrar un callback de advertencia**, puedes capturar cada evento de sustitución de fuente en el momento en que se lee el documento, y también puedes **personalizar la carga del documento** para adaptarla a tu flujo de trabajo.

En este tutorial recorreremos un ejemplo del mundo real que muestra exactamente cómo configurar el callback, por qué es importante y cómo mantener limpio el resto de tu pipeline de procesamiento. Al final tendrás una clase Java lista para ejecutar que imprime cada advertencia de fuente faltante y guarda una copia procesada del documento. No se requieren referencias externas, solo código puro y ejecutable.

> **Lo que obtendrás:**  
> • Un programa Java completo usando Aspose.Words  
> • Explicaciones paso a paso de cada línea  
> • Consejos para manejar casos extremos como archivos cifrados o lotes grandes  
> • Una rápida verificación que puedes ejecutar en cualquier archivo `.docx`

## Requisitos previos

Antes de sumergirnos, asegúrate de tener:

- **Java 17** (o cualquier JDK reciente) instalado y `JAVA_HOME` configurado.  
- **Aspose.Words para Java** JAR en tu classpath. Puedes obtener la última versión desde el repositorio Maven Central:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- replace with the newest -->
</dependency>
```

- Un documento Word de ejemplo (`input.docx`) que sospeches contiene fuentes no instaladas en tu máquina.  
- Un IDE o herramienta de compilación por línea de comandos (Maven/Gradle) con la que te sientas cómodo.

Eso es todo. Sin fuentes extra, sin servicios adicionales, solo Java puro y Aspose.Words.

## ¿Por qué registrar un callback de advertencia?

Piensa en el **callback de advertencia** como una cámara de seguridad para el proceso de carga de tu documento. Cuando Aspose.Words encuentra un glifo faltante, no lanza una excepción; simplemente cambia a una fuente de respaldo de forma silenciosa. Esa sustitución silenciosa puede romper tu diseño, especialmente en PDFs o facturas donde la marca es crítica. Al registrar un callback, tú:

1. **Obtienes información en tiempo real** – cada advertencia `FONT_SUBSTITUTION` se entrega al instante.  
2. **Registras o reaccionas** – puedes escribir en un archivo, generar una alerta o incluso reemplazar la fuente programáticamente.  
3. **Mantienes una salida limpia** – saber qué fuentes faltan te permite corregir el documento fuente antes de publicarlo.

En resumen, el callback convierte un problema oculto en uno visible, haciendo que tu pipeline de documentos sea mucho más fiable.

## Paso 1 – Crear `LoadOptions` para personalizar cómo se carga el documento

Lo primero que hacemos es instanciar `LoadOptions`. Este objeto es la puerta de entrada para cada ajuste de tiempo de carga que puedas necesitar, desde el manejo de contraseñas hasta nuestra característica de **registrar callback de advertencia**.

```java
// Step 1: Prepare LoadOptions for custom loading behavior
LoadOptions loadOptions = new LoadOptions();
```

¿Por qué no simplemente llamar a `new Document("file.docx")`? Porque sin `LoadOptions` pierdes la oportunidad de engancharte a los eventos de carga. `LoadOptions` es el único lugar donde Aspose.Words te permite **personalizar la carga del documento**.

## Paso 2 – Registrar un callback de advertencia para rastrear fuentes faltantes

Ahora llega la estrella del espectáculo: **registramos un callback de advertencia** que implementa `IWarningCallback`. Dentro del método `warning` filtramos `WarningType.FONT_SUBSTITUTION` y mostramos un mensaje útil.

```java
// Step 2: Register a warning handler that reports font substitution events
loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font substitution warnings
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

Algunos puntos a tener en cuenta:

- **¿Por qué `IWarningCallback`?** Es la interfaz que Aspose.Words usa para todos los tipos de advertencia, dándote un único punto de entrada para muchos posibles problemas.  
- **El filtrado es crucial** – sin la condición `if` verías advertencias sobre imágenes faltantes, características obsoletas, etc., lo que saturaría tus registros.  
- **Seguridad en hilos** – el callback se ejecuta en el mismo hilo que carga el documento, por lo que puedes actualizar estructuras compartidas de forma segura si necesitas agregar resultados más tarde.

Ese fragmento **registra el callback de advertencia**, y a partir de ese momento cada evento de fuente faltante se imprimirá en `stdout`. Este es el núcleo de **rastrear fuentes faltantes**.

## Paso 3 – Cargar el documento usando el `LoadOptions` configurado

Con el callback en su lugar, finalmente cargamos el archivo. Si el documento hace referencia a una fuente que no tienes, el callback se dispara antes de que el objeto `Document` esté completamente construido.

```java
// Step 3: Load the document with our custom LoadOptions
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

Reemplaza `YOUR_DIRECTORY` con la ruta real en tu máquina. El constructor `Document` lee el archivo, aplica cualquier contraseña (si la configuraste en `loadOptions`) y activa el callback de advertencia por cada fuente faltante. Verás una salida similar a:

```
Font substitution detected: Font 'Calibri' was substituted with 'Arial'.
```

Esa línea demuestra que has **rastreado fuentes faltantes** con éxito.

## Paso 4 – Continuar procesando el documento (opcional)

En esta etapa puedes manipular el documento como desees—reemplazar texto, insertar imágenes o incluso intercambiar programáticamente las fuentes sustituidas. El callback ya te proporcionó una lista de fuentes problemáticas, por lo que podrías, por ejemplo, incrustar una fuente de respaldo:

```java
// Optional: Replace missing fonts with a known fallback (e.g., Liberation Sans)
FontSettings fontSettings = new FontSettings();
fontSettings.setSubstitutionSettings(new FontSubstitutionSettings());
fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
    .add("Calibri", "Liberation Sans");
document.setFontSettings(fontSettings);
```

Si solo necesitas **rastrear fuentes faltantes**, puedes omitir este bloque. La clave es que ahora dispones de la información necesaria para tomar una decisión informada.

## Paso 5 – Guardar el documento procesado

Finalmente, persiste el documento. Puedes sobrescribir el original, guardarlo en una nueva ubicación o exportarlo a PDF, todo sin perder los datos de advertencia que capturaste antes.

```java
// Step 5: Save the processed document
document.save("YOUR_DIRECTORY/processed.docx");
System.out.println("Document saved successfully.");
```

Ejecutar la clase completa producirá una salida en consola para cada fuente faltante y un nuevo archivo llamado `processed.docx` en la misma carpeta.

## Ejemplo completo y funcional

A continuación tienes la clase Java completa que puedes copiar‑pegar en tu IDE. Incluye todo lo que hemos discutido, más un pequeño método `main`.

```java
import com.aspose.words.*;

public class FontDiagnostic {
    public static void main(String[] args) throws Exception {
        // Step 1: Create LoadOptions to customize how the document is loaded
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Register a warning handler that reports font substitution events
        loadOptions.setFontSubstitutionWarningHandler(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution detected: " + info.getDescription());
                }
            }
        });

        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Optional Step 4: Replace missing fonts with a fallback (if desired)
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.getSubstitutionSettings().getDefaultFontSubstitutes()
        //     .add("Calibri", "Liberation Sans");
        // document.setFontSettings(fontSettings);

        // Step 5: Save the processed document
        document.save("YOUR_DIRECTORY/processed.docx");
        System.out.println("Document saved successfully.");
    }
}
```

### Salida esperada

Al ejecutar el programa contra un documento que usa una fuente no instalada en tu sistema, verás algo como:

```
Font substitution detected: Font 'Times New Roman' was substituted with 'Arial'.
Font substitution detected: Font 'Cambria Math' was substituted with 'Arial Unicode MS'.
Document saved successfully.
```

Si el documento **no contiene fuentes faltantes**, la consola permanecerá silenciosa hasta la línea final “Document saved successfully.” — exactamente lo que esperas de una implementación bien comportada del **registro de callback de advertencia**.

## Consejos profesionales y errores comunes

- **¿Múltiples callbacks?** Aspose.Words solo permite un manejador de advertencias. Si necesitas registrar tanto en un archivo como en la consola, implementa un callback compuesto que reenvíe la advertencia a varias destinaciones.  
- **Lotes grandes** – al procesar cientos de archivos, considera reutilizar una única instancia de `LoadOptions`; crear una por archivo genera sobrecarga innecesaria.  
- **Documentos cifrados** – establece la contraseña en `LoadOptions` antes de cargar, de lo contrario obtendrás una `IncorrectPasswordException` antes de que el callback se active.  
- **Rendimiento** – el callback se ejecuta de forma síncrona. Si registras en un servicio remoto, almacena los mensajes en un búfer y envíalos después de que la carga termine para evitar cuellos de botella de I/O.  
- **Fuente de respaldo** – también puedes proporcionar una colección personalizada de `FontSource` si dispones de fuentes propietarias que deseas que Aspose.Words considere antes de recurrir a las fuentes del sistema.

## Conclusión

Acabas de aprender cómo **registrar un callback de advertencia** en Java, rastrear **fuentes faltantes** y **personalizar la carga del documento** con Aspose.Words. La solución es autónoma, se ejecuta con un único método `main` y te brinda visibilidad inmediata sobre cualquier sustitución de fuente que de otro modo pasaría desapercibida.

¿Próximos pasos? Prueba a extender el callback para escribir advertencias en un archivo CSV para auditoría, o combínalo con un procesador por lotes que incruste automáticamente las fuentes faltantes. También podrías explorar otros tipos de advertencia como `IMAGE_SUBSTITUTION` o `DEPRECATED_FEATURE` — el mismo patrón se aplica.

¡Feliz codificación, y que tus documentos siempre se rendericen exactamente como los imaginaste!

![Diagrama de registro de callback de advertencia](register-warning-callback.png "Flujo de registro de callback de advertencia")


## ¿Qué deberías aprender a continuación?

- [Warning Callback In Word Document](/words/english/net/programming-with-loadoptions/warning-callback/)
- [Customize Theme Colors & Fonts in Aspose.Words Java: A Comprehensive Guide](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Track Changes in Word Documents Using Aspose.Words Java: A Complete Guide to Document Revisions](/words/english/java/document-comparison-tracking/aspose-words-java-track-changes-revisions/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}