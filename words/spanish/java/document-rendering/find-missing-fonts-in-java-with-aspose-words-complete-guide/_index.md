---
category: general
date: 2026-06-08
description: Encuentre fuentes faltantes rápidamente usando Aspose.Words para Java.
  Aprenda a diagnosticar advertencias de sustitución de fuentes y a solucionar problemas
  de fuentes faltantes en solo unos pocos pasos.
draft: false
keywords:
- find missing fonts
- Aspose.Words for Java
- FontSubstitutionWarning
- LoadOptions
- document warnings
language: es
og_description: Encuentre fuentes faltantes en sus archivos DOCX con Aspose.Words
  para Java. Este tutorial muestra cómo habilitar diagnósticos, leer los eventos FontSubstitutionWarning
  y mostrar los nombres de fuentes originales frente a los sustituidos.
og_title: Encontrar fuentes faltantes en Java – Aspose.Words paso a paso
schemas:
- author: Aspose
  dateModified: '2026-06-08'
  description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  headline: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  type: TechArticle
- description: Find missing fonts quickly using Aspose.Words for Java. Learn to diagnose
    font substitution warnings and fix missing font issues in just a few steps.
  name: Find Missing Fonts in Java with Aspose.Words – Complete Guide
  steps:
  - name: Expected Console Output
    text: '``` Font substituted: Comic Sans MS → Arial Font substituted: MyCustomFont
      → Times New Roman ```'
  - name: Missing Font but No Warning
    text: Sometimes a font is embedded in the DOCX, but the embedding is corrupted.
      Aspose will still raise a `FontSubstitutionWarning` because it cannot render
      the text. To differentiate, check `fsWarning.isFontEmbedded()` (available in
      newer versions).
  - name: Multiple Substitutions for the Same Font
    text: A single missing font may be substituted multiple times across different
      runs if the fallback hierarchy changes (e.g., first tries Arial, then falls
      back to Helvetica). Keep a `Set<String>` of `getOriginalFontName()` to deduplicate
      if you only need a list of unique missing fonts.
  - name: Performance Considerations
    text: Loading very large DOCX files (hundreds of MB) while collecting warnings
      can add overhead. If you only need font diagnostics, set `loadOptions.setValidateStructure(false)`
      to skip deep validation. This speeds up the process without affecting warning
      generation.
  type: HowTo
tags:
- Java
- Aspose.Words
- fonts
- diagnostics
title: Encontrar fuentes faltantes en Java con Aspose.Words – Guía completa
url: /es/java/document-rendering/find-missing-fonts-in-java-with-aspose-words-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Encontrar fuentes faltantes en Java con Aspose.Words – Guía completa

¿Alguna vez te has preguntado cómo **encontrar fuentes faltantes** en un documento Word antes de que arruinen tu diseño? No eres el único: los desarrolladores se topan constantemente con sustituciones silenciosas de fuentes que estropean PDFs o informes impresos. La buena noticia es que Aspose.Words para Java ofrece una API de diagnóstico incorporada que hace que detectar esas fuentes faltantes sea muy sencillo.

En este tutorial recorreremos un ejemplo del mundo real que carga un DOCX, habilita la recopilación de advertencias y muestra cada *FontSubstitutionWarning* que necesitas conocer. Al final podrás registrar el nombre de la fuente original, la alternativa que Aspose eligió y decidir si incrustas la fuente faltante tú mismo.

## Lo que necesitarás

Antes de comenzar, asegúrate de tener:

* **Aspose.Words for Java** (última versión 23.x) en tu classpath.  
* Un entorno de desarrollo Java 8+ (IDE de tu preferencia, Maven/Gradle funciona bien).  
* Un DOCX de ejemplo que intencionalmente haga referencia a una fuente que no esté instalada en tu máquina — lo llamaremos `MissingFonts.docx`.

Eso es todo. Sin bibliotecas adicionales, sin configuraciones complejas, solo Java puro y Aspose.

![Find missing fonts diagram](https://example.com/find-missing-fonts.png "Find missing fonts diagram")
*La imagen anterior ilustra el flujo: cargar → diagnóstico → advertencias → salida.*

## Paso 1: Preparar LoadOptions y especificar el formato del documento

Lo primero que hacemos es crear un objeto **LoadOptions**. Esto le indica a Aspose.Words cómo interpretar el archivo entrante y, lo que es crucial, habilita la recopilación de *advertencias del documento*.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {
    public static void main(String[] args) throws Exception {
        // Create LoadOptions and force DOCX format (helps when the file extension is misleading)
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setLoadFormat(LoadFormat.DOCX);
```

*¿Por qué usar LoadOptions?*  
Sin él, Aspose aún carga el archivo pero puede omitir algunos datos de diagnóstico. Al establecer explícitamente el formato garantizas una generación consistente de advertencias, especialmente al trabajar con archivos antiguos o corruptos.

## Paso 2: Cargar el documento con diagnóstico habilitado

Ahora leemos realmente el archivo. El constructor `Document` inicia automáticamente la recopilación de advertencias, que más adelante incluirá cualquier instancia de **FontSubstitutionWarning**.

```java
        // Load the document located in your project folder
        Document doc = new Document("YOUR_DIRECTORY/MissingFonts.docx", loadOptions);
```

> **Consejo profesional:** Si utilizas Maven, agrega la dependencia de Aspose.Words a tu `pom.xml`. Así el JAR se descargará automáticamente y no tendrás que gestionar el classpath manualmente.

## Paso 3: Analizar las advertencias del documento en busca de eventos de sustitución de fuentes

Aspose almacena cada advertencia en una colección que puedes iterar. Filtramos los objetos `FontSubstitutionWarning` porque indican específicamente una fuente faltante que fue reemplazada.

```java
        // Iterate over all warnings generated during load
        for (WarningInfo warning : doc.getWarnings()) {
            if (warning instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fsWarning = (FontSubstitutionWarning) warning;
```

*¿Qué está ocurriendo aquí?*  
`doc.getWarnings()` devuelve una `List<WarningInfo>`. Al comprobar `instanceof FontSubstitutionWarning` aislamos solo las entradas relacionadas con fuentes, ignorando otras advertencias como “característica no compatible” o “conversión de imagen”.

## Paso 4: Mostrar los nombres de la fuente original y la sustituta

Finalmente, imprimimos tanto el nombre de la fuente faltante (original) como la fuente que Aspose eligió como sustituta. Esta salida es perfecta para registros o para alimentar una verificación en una canalización de compilación.

```java
                // Print the original font and the font Aspose substituted it with
                System.out.println("Font substituted: " + fsWarning.getOriginalFontName()
                        + " → " + fsWarning.getSubstitutedFontName());
            }
        }
    }
}
```

### Salida esperada en la consola

```
Font substituted: Comic Sans MS → Arial
Font substituted: MyCustomFont → Times New Roman
```

Si no ves nada impreso, eso significa que **no se detectaron fuentes faltantes** — tu documento ya contiene fuentes que existen en la máquina donde se ejecuta el código.

## Paso 5: Manejo de casos límite y errores comunes

### Fuente faltante pero sin advertencia

A veces una fuente está incrustada en el DOCX, pero la incrustación está corrupta. Aspose seguirá generando un `FontSubstitutionWarning` porque no puede renderizar el texto. Para diferenciar, verifica `fsWarning.isFontEmbedded()` (disponible en versiones más recientes).

### Múltiples sustituciones para la misma fuente

Una única fuente faltante puede ser sustituida varias veces en diferentes ejecuciones si la jerarquía de alternativas cambia (por ejemplo, primero intenta Arial y luego recurre a Helvetica). Mantén un `Set<String>` de `getOriginalFontName()` para desduplicar si solo necesitas una lista de fuentes faltantes únicas.

### Consideraciones de rendimiento

Cargar archivos DOCX muy grandes (cientos de MB) mientras se recopilan advertencias puede añadir sobrecarga. Si solo necesitas diagnóstico de fuentes, establece `loadOptions.setValidateStructure(false)` para omitir la validación profunda. Esto acelera el proceso sin afectar la generación de advertencias.

## Bonus: Automatizar la incrustación de fuentes

Una vez que sabes qué fuentes faltan, puedes incrustarlas programáticamente:

```java
for (String missingFont : missingFontsSet) {
    // Assume you have the TTF file for the missing font in a known folder
    FontSettings.getDefaultInstance().setFontsFolder("YOUR_FONTS_FOLDER", true);
}
```

Incrustar garantiza que el PDF final o el DOCX guardado se renderice exactamente como se pretende en cualquier máquina — sin sustituciones inesperadas.

## Recapitulación: Cómo encontrar fuentes faltantes con Aspose.Words

- **Crear LoadOptions** y establecer el formato de carga.  
- **Cargar el documento** mientras Aspose captura advertencias.  
- **Iterar sobre `doc.getWarnings()`**, filtrando por `FontSubstitutionWarning`.  
- **Imprimir** `getOriginalFontName()` y `getSubstitutedFontName()` para ver qué fuentes faltan.  
- **Opcional:** desduplicar, comprobar el estado de incrustación o incrustar automáticamente las fuentes faltantes.

Esa es la solución completa para **encontrar fuentes faltantes** en una aplicación Java usando Aspose.Words. Ahora dispones de un método fiable para detectar problemas de fuentes temprano, mantener tus PDFs consistentes y evitar sorpresas desagradables en producción.

## ¿Qué explorar a continuación?

* **Incrustar fuentes** automáticamente (consulta el fragmento bonus).  
* **Generar un PDF** después de corregir las fuentes para verificar la salida visual.  
* **Usar FontSettings de Aspose.Words** para definir una cadena de sustitución personalizada.  
* **Ejecutar los mismos diagnósticos** en archivos DOC, RTF o HTML — solo cambia `LoadFormat` según corresponda.

Siéntete libre de experimentar con diferentes tipos de documentos y familias tipográficas. Si encuentras algún obstáculo, deja un comentario abajo o consulta la documentación oficial de la API Java de Aspose para una personalización más profunda.

¡Feliz codificación, y que tus documentos siempre se rendericen con las fuentes que pretendes!

## ¿Qué deberías aprender después?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques alternativos de implementación en tus propios proyectos.

- [Using Fonts in Aspose.Words for Java](/words/english/java/using-document-elements/using-fonts/)
- [Capture Font Substitution Warnings in Java with Aspose.Words – Complete Guide](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [How to Detect Fonts in Aspose.Words – Handle Warnings & Settings](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}