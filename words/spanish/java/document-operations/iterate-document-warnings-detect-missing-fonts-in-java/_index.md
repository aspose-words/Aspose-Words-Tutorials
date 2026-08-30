---
category: general
date: 2026-04-28
description: Iterar las advertencias del documento en un archivo Word para detectar
  fuentes faltantes, obtener los nombres de las fuentes faltantes e imprimir los detalles
  de las fuentes faltantes usando Aspose.Words para Java.
draft: false
keywords:
- iterate document warnings
- detect missing fonts
- load word document
- retrieve missing font
- print missing font
language: es
og_description: Itera las advertencias del documento para encontrar fuentes faltantes,
  recupera los nombres de las fuentes faltantes y muestra los detalles de las fuentes
  faltantes con un ejemplo completo en Java.
og_title: 'Iterar advertencias del documento: Detectar fuentes faltantes en Java'
tags:
- Aspose.Words
- Java
- Document Processing
title: 'Iterar advertencias del documento: Detectar fuentes faltantes en Java'
url: /es/java/document-operations/iterate-document-warnings-detect-missing-fonts-in-java/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Iterar advertencias del documento – Detectar fuentes faltantes en Java

¿Alguna vez necesitaste **iterar advertencias del documento** al abrir un archivo Word y te preguntaste qué fuentes faltan? No eres el único. Las fuentes faltantes pueden arruinar el aspecto de un informe, y sin una forma de detectarlas podrías distribuir un documento que no se parece en nada al original.  

En este tutorial te mostraremos cómo **detectar fuentes faltantes** cargando un documento Word, iterando sus advertencias, obteniendo los nombres de las fuentes faltantes y, finalmente, imprimiendo la información de fuentes faltantes, todo con Aspose.Words para Java.  

Cubriremos todo desde la primera línea de código hasta la salida esperada en la consola, para que puedas copiar‑pegar una solución funcional en tu proyecto ahora mismo. No se requieren documentos adicionales.

## Requisitos previos

- Java 8 o superior instalado.
- Biblioteca Aspose.Words para Java (la última versión a fecha de 2026‑04‑28).
- Un archivo Word que potencialmente contenga fuentes no instaladas en tu máquina (p. ej., `doc-with-missing-font.docx`).

Si ya los tienes, genial—estás listo para **cargar documento Word** y comenzar a iterar.

## Paso 1 – Cargar documento Word con opciones predeterminadas

Antes de poder **iterar advertencias del documento**, el archivo debe cargarse en memoria. Aspose.Words te permite hacerlo con una única llamada al constructor. Usar `LoadOptions` predeterminadas suele ser suficiente, pero mostraremos la creación explícita para mayor claridad.

```java
import com.aspose.words.*;

public class MissingFontDetector {
    public static void main(String[] args) throws Exception {

        // Step 1: Prepare load options (default settings are fine for this example)
        LoadOptions loadOptions = new LoadOptions();

        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/doc-with-missing-font.docx", loadOptions);
```

> **Por qué es importante:**  
> Cargar el documento hace que Aspose.Words escanee el archivo en busca de recursos que no pueda resolver, como fuentes que no están instaladas localmente. esos problemas se almacenan como **advertencias**, que **iteraremos advertencias del documento** en el siguiente paso.

## Paso 2 – Iterar advertencias del documento para encontrar problemas de fuentes

Ahora llega el núcleo de la solución: recorremos cada advertencia que la biblioteca recopiló al cargar. Los objetos `WarningInfo` nos indican qué salió mal, y podemos filtrar por `FontSubstitutionWarning` para **detectar fuentes faltantes**.

```java
        // Step 3: Iterate over all warnings generated during loading
        for (WarningInfo warningInfo : document.getWarnings()) {
            // Step 4: Identify font substitution warnings
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;

                // Step 5: Output the missing font name and the font that was used as a substitute
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }
    }
}
```

> **Consejo:** La comprobación `instanceof` garantiza que solo manejemos advertencias relacionadas con fuentes, ignorando otras como problemas de carga de imágenes. Esto hace que el bucle sea eficiente y mantiene la salida centrada en las fuentes de las que realmente necesitas **obtener información de fuentes faltantes**.

### Salida esperada en la consola

```
Missing font: Arial Black
Substituted with: Liberation Sans
Missing font: Calibri
Substituted with: Liberation Sans
```

Si el documento no contiene fuentes faltantes, el bucle finaliza silenciosamente—nada que **imprimir fuentes faltantes**.

## Paso 3 – ¿Por qué no simplemente capturar una excepción?

Podrías preguntarte, “¿Por qué no envolver la llamada `new Document(...)` en un try‑catch y buscar una excepción?” La respuesta es doble:

1. **Información granular:** Las excepciones solo indican que algo falló. Las advertencias te dan el nombre exacto de la fuente y la sustitución que Aspose.Words eligió.
2. **Problemas no fatales:** Las fuentes faltantes suelen ser no fatales; el documento se carga, pero la fidelidad visual se ve comprometida. Al **iterar advertencias del documento**, conservas la capacidad de procesar el resto del archivo.

## Paso 4 – Extender el ejemplo: recopilar fuentes faltantes en una lista

A veces necesitas las fuentes faltantes para un procesamiento posterior—quizá incrustarlas o alertar a un usuario mediante UI. Aquí tienes un ajuste rápido que reúne los nombres en un `Set<String>`.

```java
        // Collect missing fonts for later use
        Set<String> missingFonts = new HashSet<>();

        for (WarningInfo warningInfo : document.getWarnings()) {
            if (warningInfo instanceof FontSubstitutionWarning) {
                FontSubstitutionWarning fontWarning = (FontSubstitutionWarning) warningInfo;
                missingFonts.add(fontWarning.getMissingFontName());

                // Still print for immediate feedback
                System.out.println("Missing font: " + fontWarning.getMissingFontName());
                System.out.println("Substituted with: " + fontWarning.getSubstitutedFontName());
            }
        }

        // Example of using the collected data
        System.out.println("Total missing fonts: " + missingFonts.size());
```

Ahora dispones de una forma limpia de **obtener información de fuentes faltantes** programáticamente, que puedes pasar a un módulo de informes o a un asistente de instalación de fuentes.

## Paso 5 – Consideraciones del mundo real

- **Múltiples sustituciones:** Una sola fuente faltante puede ser sustituida por diferentes fuentes en distintas partes del documento. La lista de advertencias contendrá cada ocurrencia, por lo que podrías ver entradas duplicadas de fuentes faltantes.
- **Rendimiento:** Cargar documentos muy grandes puede generar miles de advertencias. Si solo te interesan las fuentes, filtra temprano como se muestra para mantener el bucle rápido.
- **Fuentes multiplataforma:** En Linux, la fuente de sustitución predeterminada suele ser *Liberation Sans*. En Windows, podría ser *Arial*. Conocer la sustitución te ayuda a decidir si necesitas distribuir fuentes personalizadas con tu aplicación.

## Paso 6 – Ayuda visual

A continuación se muestra una captura de pantalla de la salida de la consola (el texto alternativo incluye la palabra clave principal para SEO).

![Iterate document warnings salida de consola que muestra fuentes faltantes y sus sustitutos](/images/iterate-document-warnings.png)

*Texto alternativo:* *ejemplo de iterate document warnings que muestra nombres de fuentes faltantes y detalles de sustitución.*

## Conclusión

Acabas de aprender cómo **iterar advertencias del documento** en Aspose.Words para Java, **detectar fuentes faltantes**, **cargar documento Word** de forma segura, **obtener información de fuentes faltantes** y **imprimir fuentes faltantes** en la consola. El fragmento de código completo funciona tal cual, y puedes adaptarlo para registrar en un archivo, mostrar un cuadro de diálogo UI o incluso incrustar automáticamente las fuentes faltantes.

A continuación, podrías explorar cómo **cargar documento Word** con fuentes personalizadas (p. ej., añadiendo una carpeta de fuentes corporativas) o cómo incrustar fuentes faltantes directamente en el archivo para preservar el diseño en diferentes máquinas. Ambos temas se basan naturalmente en lo que cubrimos aquí.

¡Feliz codificación, y que tus PDFs siempre se vean exactamente como lo deseas!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}