---
category: general
date: 2026-06-27
description: Aprende a capturar advertencias de sustitución de fuentes en Java usando
  Aspose.Words. Este tutorial paso a paso también cubre los callbacks de advertencia
  y el uso de LoadOptions.
draft: false
keywords:
- capture font substitution warnings
- Aspose.Words warning callback
- Java LoadOptions example
- font substitution handling
- document processing with Aspose
language: es
og_description: Captura advertencias de sustitución de fuentes en Java con Aspose.Words.
  Sigue esta guía para configurar callbacks de advertencia, usar LoadOptions y manejar
  fuentes faltantes.
og_title: Capturar advertencias de sustitución de fuentes en Java – Tutorial de Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-06-27'
  description: Learn how to capture font substitution warnings in Java using Aspose.Words.
    This step‑by‑step tutorial also covers warning callbacks and LoadOptions usage.
  headline: Capture Font Substitution Warnings in Java with Aspose.Words – Complete
    Guide
  type: TechArticle
- questions:
  - answer: Yes. The warning callback is format‑agnostic; it fires for any document
      type that Aspose.Words loads (DOC, DOCX, RTF, HTML, etc.). The only difference
      is the set of warnings that may appear.
    question: Does this work with PDF or other formats?
  - answer: Absolutely. Inside the `warning` method, inspect `info.getWarningType()`
      for other enum values such as `WarningType.IMAGE_RESOLUTION`. Then handle them
      accordingly.
    question: Can I capture other warning types, like *image resolution* warnings?
  - answer: 'Store each `info.getDescription()` in a `List<String>` inside the callback.
      After loading, you’ll have a collection you can log, send to a monitoring service,
      or use to trigger a font‑download routine. ## Conclusion You now know **how
      to capture font substitution warnings** in Java using Aspose.Word'
    question: What if I need the list of substituted fonts after the document loads?
  type: FAQPage
tags:
- Aspose.Words
- Java
- Document Conversion
title: Captura de advertencias de sustitución de fuentes en Java con Aspose.Words
  – Guía completa
url: /es/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa

¿Alguna vez necesitaste **capturar advertencias de sustitución de fuentes** al cargar un DOCX que usa tipografías exóticas? No eres el único. En muchos proyectos del mundo real —piensa en generadores automáticos de informes o convertidores por lotes de documentos—las fuentes faltantes provocan sustituciones silenciosas que pueden arruinar la fidelidad del diseño.  

Afortunadamente, Aspose.Words te ofrece una forma sencilla de escuchar esas advertencias. En este tutorial recorreremos la configuración de **LoadOptions**, la conexión de un **callback de advertencias de Aspose.Words**, y la impresión de cada notificación de *sustitución de fuentes* en la consola. Al final sabrás exactamente cuándo se ha reemplazado una fuente y cómo reaccionar programáticamente.

> **Lo que obtendrás:** un fragmento de Java completamente ejecutable, una explicación de *por qué* cada pieza es importante, y consejos para manejar casos límite como directorios de fuentes personalizados.

## Requisitos previos y lo que necesitarás

- Java 8 o superior instalado (el código también funciona con Java 11+).
- El último JAR de Aspose.Words for Java (descárgalo del sitio oficial o Maven Central).
- Un archivo DOCX que haga referencia a fuentes no instaladas en tu máquina (p. ej., un *font‑rich.docx* que puedes encontrar en el conjunto de demostración de Aspose).
- Un IDE decente (IntelliJ IDEA, Eclipse, o incluso VS Code con extensiones de Java).

No se requieren bibliotecas externas más allá de Aspose.Words, y el ejemplo se ejecuta en un método `main` simple.

## Paso 1: Configurar LoadOptions – El punto de entrada para la carga personalizada

`LoadOptions` es la bolsa de configuración de Aspose.Words que indica a la biblioteca *cómo* leer un documento. Por defecto sustituye silenciosamente las fuentes faltantes, pero puedes cambiar ese comportamiento con un callback de advertencias.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions to customize loading behavior
        LoadOptions loadOptions = new LoadOptions();
```

**Por qué es importante:** Sin `LoadOptions`, el documento se carga silenciosamente y pierdes visibilidad de las fuentes faltantes. Al crear una instancia obtienes un gancho para el sistema de advertencias.

## Paso 2: Definir un callback de advertencias para *capturar advertencias de sustitución de fuentes*

Aspose.Words envía eventos de advertencia a través de la interfaz `IWarningCallback`. Impléméntala en línea (o como una clase separada) y filtra por `WarningType.FONT_SUBSTITUTION`.

```java
        // Step 2: Define a warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // Only react to font substitution warnings
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });
```

**Explicación:**  
- `info.getWarningType()` te indica la categoría de la advertencia.  
- `WarningType.FONT_SUBSTITUTION` es el valor enum que nos interesa.  
- `info.getDescription()` contiene un mensaje legible, por ejemplo, *“Font 'Comic Sans MS' not found, substituted with 'Arial'.”*  

Al imprimir la descripción, **capturas advertencias de sustitución de fuentes** en tiempo real.

## Paso 3: Cargar el documento usando los LoadOptions configurados

Ahora que el callback está configurado, carga tu DOCX. El callback de advertencias se dispara automáticamente durante el análisis.

```java
        // Step 3: Load the document using the configured LoadOptions
        Document document = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);
```

Reemplaza `YOUR_DIRECTORY` con la ruta real a tu archivo de prueba. Cuando se ejecuta el constructor `Document`, cualquier fuente faltante dispara el callback definido anteriormente, y verás los mensajes de sustitución en la consola.

## Paso 4: Verificar el documento cargado (Opcional pero útil)

Después de cargar, puede que quieras confirmar la integridad del documento —recuento de páginas, extracción de texto, etc. Este paso no es necesario para capturar advertencias, pero te ayuda a ver el impacto de las sustituciones.

```java
        // Optional: Output basic document info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + document.getPageCount());
```

Si una fuente fue sustituida, el diseño puede desplazarse ligeramente; comprobar el recuento de páginas puede revelar esos cambios.

## Paso 5: Avanzado – Manejar fuentes sustituidas programáticamente

A veces no solo quieres registrar la advertencia —puedes necesitar incrustar una fuente de respaldo o ajustar el estilo. A continuación tienes un patrón rápido que puedes adoptar.

```java
        // Advanced: Register a fallback font folder to reduce substitutions
        FontSettings fontSettings = new FontSettings();
        // Point to a folder that contains the missing fonts
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);
```

Al apuntar Aspose.Words a una carpeta que contiene las fuentes originales, puedes *evitar* la sustitución por completo. Si la carpeta falta, el callback de advertencias aún captura el evento, dándote una estrategia de respaldo.

## Ejemplo completo y funcional

Juntándolo todo, aquí tienes el programa completo, listo para ejecutar:

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Initialize LoadOptions
        LoadOptions loadOptions = new LoadOptions();

        // Set up warning callback to capture font substitution warnings
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // OPTIONAL: Register a custom fonts folder to avoid substitution
        FontSettings fontSettings = new FontSettings();
        fontSettings.setFontsFolder("YOUR_DIRECTORY/custom-fonts", true);
        loadOptions.setFontSettings(fontSettings);

        // Load the document – warnings will be printed automatically
        Document doc = new Document("YOUR_DIRECTORY/font-rich.docx", loadOptions);

        // Verify basic info
        System.out.println("Document loaded successfully.");
        System.out.println("Page count: " + doc.getPageCount());
    }
}
```

**Salida esperada en la consola** (cuando se encuentra una fuente faltante):

```
Font substituted: Font 'Pacifico' not found, substituted with 'Arial'.
Document loaded successfully.
Page count: 3
```

Si todas las fuentes están presentes, el callback permanece silencioso —no se imprime nada, que es exactamente lo que se esperaría.

## Errores comunes y consejos profesionales

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **El callback nunca se dispara** | Olvidaste adjuntar el callback a `LoadOptions` **o** usaste el constructor por defecto de `Document` sin pasar `loadOptions`. | Siempre llama a `loadOptions.setWarningCallback(...)` **y** usa la sobrecarga `new Document(path, loadOptions)`. |
| **Demasiadas advertencias saturan el registro** | Los documentos grandes con muchas fuentes faltantes generan una advertencia por sustitución. | Filtra más comprobando `info.getDescription()` para nombres de fuentes específicos, o agrupa las advertencias en una lista para procesarlas después. |
| **Las fuentes sustituidas afectan el diseño** | La fuente de respaldo puede tener métricas diferentes (tamaño, espaciado). | Proporciona una carpeta de fuentes personalizada (ver Paso 5) o ajusta el estilo del documento después de cargar. |
| **Ejecutándose en un servidor sin interfaz gráfica** | La sustitución de fuentes por defecto puede depender de fuentes del sistema que no están instaladas en el servidor. | Incluye las fuentes necesarias con tu aplicación y apunta `FontSettings` a esa carpeta. |

## Preguntas frecuentes

**Q: ¿Esto funciona con PDF u otros formatos?**  
A: Sí. El callback de advertencias es independiente del formato; se dispara para cualquier tipo de documento que Aspose.Words cargue (DOC, DOCX, RTF, HTML, etc.). La única diferencia es el conjunto de advertencias que pueden aparecer.

**Q: ¿Puedo capturar otros tipos de advertencias, como advertencias de *resolución de imágenes*?**  
A: Por supuesto. Dentro del método `warning`, inspecciona `info.getWarningType()` para otros valores enum como `WarningType.IMAGE_RESOLUTION`. Luego manéjalos según corresponda.

**Q: ¿Qué pasa si necesito la lista de fuentes sustituidas después de cargar el documento?**  
A: Almacena cada `info.getDescription()` en una `List<String>` dentro del callback. Después de cargar, tendrás una colección que puedes registrar, enviar a un servicio de monitoreo, o usar para iniciar una rutina de descarga de fuentes.

## Conclusión

Ahora sabes **cómo capturar advertencias de sustitución de fuentes** en Java usando Aspose.Words, por qué cada pieza del rompecabezas es importante, y cómo ampliar la solución para escenarios del mundo real. Al aprovechar `LoadOptions`, un `callback de advertencias de Aspose.Words` y opcionalmente `FontSettings`, obtienes total visibilidad de las fuentes faltantes y puedes mantener fiables tus pipelines de conversión de documentos.

¿Listo para el siguiente paso? Prueba reemplazar `System.out.println` con un logger como SLF4J, o integra la lista de advertencias en una interfaz que alerte a los usuarios antes de finalizar una conversión por lotes. También podrías explorar el **callback de advertencias de Aspose.Words** para otros tipos de advertencias, como *funcionalidades no soportadas* o alertas de *imágenes de alta resolución*.

¡Feliz codificación, y que tus PDFs nunca vuelvan a sufrir cambios inesperados de fuentes!

![Captura de salida de consola de advertencias de sustitución de fuentes](image-placeholder.png "captura de advertencias de sustitución de fuentes")


## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Habilitar advertencias de sustitución de fuentes en Aspose.Words – Guía completa](/words/english/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/)
- [Cómo establecer LoadOptions en Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cómo crear documentos PDF con Aspose.Words para Java | API de procesamiento de documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}