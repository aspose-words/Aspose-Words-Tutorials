---
category: general
date: 2026-03-19
description: Aprenda a capturar advertencias en Aspose.Words para Java y a detectar
  fuentes faltantes. Esta guía paso a paso también muestra cómo manejar las fuentes
  faltantes de forma elegante.
draft: false
keywords:
- how to capture warnings
- detect missing fonts
- how to detect missing fonts
- handle missing fonts
language: es
og_description: Cómo capturar advertencias en Aspose.Words para Java, detectar fuentes
  faltantes y manejar fuentes faltantes con un ejemplo de código completo.
og_title: Cómo capturar advertencias – Detectar fuentes faltantes en Aspose.Words
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Cómo capturar advertencias – Detectar fuentes faltantes en Aspose.Words
url: /es/java/document-rendering/how-to-capture-warnings-detect-missing-fonts-in-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo capturar advertencias – Detectar fuentes faltantes en Aspose.Words

¿Alguna vez te has preguntado **cómo capturar advertencias** cuando un documento Word se carga y algunas fuentes no están disponibles en la máquina? No estás solo. En muchos proyectos del mundo real, las fuentes faltantes provocan cambios de diseño silenciosos, y la única forma de saber qué ocurrió es escuchando el flujo de advertencias que emite Aspose.Words.  

En este tutorial recorreremos un ejemplo completo y listo para ejecutar que **detecta fuentes faltantes**, te muestra **cómo detectar fuentes faltantes** programáticamente, y además ofrece un consejo rápido sobre **cómo manejar fuentes faltantes** para que tu salida sea predecible.

> **Nota rápida:** El código funciona con Aspose.Words 23.9 (o superior) y requiere Java 8+.

---

## Lo que necesitarás

- **Aspose.Words for Java** (dependencia Maven/Gradle o JAR en el classpath)  
- Un archivo Word (`input.docx`) que hace referencia a una fuente no instalada en tu sistema (p. ej., “Comic Sans MS”)  
- Un IDE de Java o una configuración simple de línea de comandos `javac`/`java`  

No se requieren otras bibliotecas—todo lo demás vive dentro del paquete Aspose.Words.

---

## Paso 1 – Configurar LoadOptions para capturar advertencias  

Para comenzar a escuchar advertencias debes crear una instancia de `LoadOptions`. Este objeto indica al cargador que registre cualquier problema que encuentre, como fuentes faltantes.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Create LoadOptions that will store warning information
        LoadOptions loadOptions = new LoadOptions();

        // ... the rest of the code follows
```

**Por qué es importante:** Sin `LoadOptions` el cargador reemplaza silenciosamente las fuentes faltantes con la fuente predeterminada del sistema, y nunca sabrías que se realizó una sustitución. Habilitar las advertencias te brinda total visibilidad.

---

## Paso 2 – Cargar el documento usando LoadOptions  

Ahora realmente cargamos el documento. El `LoadOptions` que acabamos de crear se pasa al constructor, por lo que cualquier advertencia generada durante el análisis se captura.

```java
        // Step 2: Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Consejo profesional:** Si estás procesando muchos archivos en lote, reutiliza la misma instancia de `LoadOptions` para evitar la creación innecesaria de objetos.

---

## Paso 3 – Iterar sobre las advertencias capturadas  

Aspose.Words almacena cada advertencia como un objeto `WarningInfo`. Solo nos interesan las advertencias relacionadas con fuentes, por lo que filtramos `FontSubstitutionWarningInfo`.

```java
        // Step 3: Loop through all warnings generated while loading
        for (WarningInfo warning : document.getWarnings()) {
            // Step 3a: Keep only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // Step 4: Output the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());
            }
        }
    }
}
```

**Explicación:**  
- `document.getWarnings()` devuelve una lista de todas las advertencias que ocurrieron durante la carga.  
- `FontSubstitutionWarningInfo` contiene dos datos cruciales: la **fuente solicitada** (la que el DOCX pidió) y la **fuente real** a la que Aspose.Words recurrió.  
- Al imprimir ambas, ves instantáneamente qué fuentes faltan y qué sustitución se realizó.

---

## Paso 4 – (Opcional) Manejar fuentes faltantes programáticamente  

Capturar advertencias es solo la mitad de la historia. Una vez que sabes que una fuente falta, puede que quieras **manejar fuentes faltantes** proporcionando una sustitución personalizada o registrando el problema para revisarlo más tarde.

```java
                // Optional: Replace the missing font with a known fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
```

**¿Por qué hacer esto?**  
- Garantiza una renderización consistente en todas las máquinas.  
- Previene cambios inesperados de diseño en PDFs o imágenes generados posteriormente.  

También puedes almacenar los detalles de la advertencia en una base de datos, enviar un correo electrónico al equipo de contenido, o incluso abortar el proceso si una fuente crítica falta.

---

## Ejemplo completo y funcional  

A continuación se muestra el programa completo y ejecutable. Simplemente reemplaza `YOUR_DIRECTORY/input.docx` con la ruta a tu archivo de prueba, agrega el JAR de Aspose.Words a tu classpath y ejecuta.

```java
import com.aspose.words.*;

public class FontWarningDemo {
    public static void main(String[] args) throws Exception {

        // 1️⃣ Create LoadOptions to capture warnings
        LoadOptions loadOptions = new LoadOptions();

        // 2️⃣ Load the document that may contain missing fonts
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // 3️⃣ Iterate through all warnings
        for (WarningInfo warning : document.getWarnings()) {
            // 3a️⃣ Filter only font substitution warnings
            if (warning instanceof FontSubstitutionWarningInfo) {
                FontSubstitutionWarningInfo fontWarning = (FontSubstitutionWarningInfo) warning;

                // 4️⃣ Display the requested and actual font names
                System.out.println("Requested: " + fontWarning.getRequestedFontName()
                        + " → Substituted: " + fontWarning.getActualFontName());

                // 5️⃣ (Optional) Provide a custom fallback
                FontSettings fontSettings = new FontSettings();
                fontSettings.getSubstitutionSettings().getTableSubstitution()
                    .addSubstitutes(fontWarning.getRequestedFontName(), "Arial");
                document.setFontSettings(fontSettings);
            }
        }

        // 6️⃣ Save the document if you need to see the result with the fallback applied
        document.save("output.docx");
    }
}
```

**Salida esperada** (cuando “Comic Sans MS” falta):

```
Requested: Comic Sans MS → Substituted: Arial
```

Después de que se ejecute el código de sustitución opcional, el `output.docx` guardado se renderizará usando **Arial** donde originalmente se hacía referencia a “Comic Sans MS”.

---

## Preguntas frecuentes y casos límite  

| Pregunta | Respuesta |
|----------|-----------|
| *¿Qué pasa si el documento tiene varias fuentes faltantes?* | El bucle emitirá una advertencia por cada una. Puedes recopilarlas en un `Map<String, String>` para procesamiento por lotes. |
| *¿Esto funciona para PDFs generados a partir del documento?* | Absolutamente. La sustitución de fuentes ocurre durante la fase de carga, por lo que cualquier exportación posterior (PDF, HTML, imagen) utiliza las fuentes resueltas. |
| *¿Puedo suprimir las advertencias en lugar de capturarlas?* | Sí—establece `loadOptions.setWarningCallback(null);` pero perderás visibilidad de las fuentes faltantes. |
| *¿Se limpia la lista de advertencias después de guardar?* | La colección de advertencias pertenece a la instancia `Document`. Después de llamar a `document.save()`, la lista permanece sin cambios a menos que crees un nuevo `Document`. |
| *¿Qué pasa con las fuentes personalizadas incrustadas en el DOCX?* | Las fuentes incrustadas se consideran disponibles; Aspose.Words las usará incluso si no están instaladas en el sistema host. |

---

## Consejos profesionales para uso en producción  

- **Cache FontSettings:** Si procesas cientos de archivos, crea una única `FontSettings` con tus sustituciones preferidas y reutilízala para evitar sobrecarga.  
- **Registra datos estructurados:** En lugar de `System.out` simple, escribe las advertencias en un registro JSON—esto hace que el análisis posterior (p. ej., “las fuentes más faltantes”) sea trivial.  
- **Validar temprano:** Ejecuta una rápida “carga en seco” con `LoadOptions` antes del procesamiento intensivo; aborta temprano si faltan fuentes críticas.  
- **Seguridad de hilos:** Los objetos `Document` no son seguros para hilos. Mantén el procesamiento de cada archivo en su propio hilo o usa un `LoadOptions` local al hilo.  

---

## Conclusión  

Ahora sabes **cómo capturar advertencias** en Aspose.Words para Java, **detectar fuentes faltantes**, y **manejar fuentes faltantes** con una estrategia de sustitución limpia. Al aprovechar `LoadOptions` e iterar sobre `document.getWarnings()`, obtienes una visión completa de los eventos de sustitución de fuentes, asegurando que tus documentos generados se vean exactamente como se pretende en todos los entornos.

¿Listo para el siguiente paso? Intenta ampliar este patrón para **detectar imágenes faltantes**, **rastrear características no compatibles**, o incluso **auto‑incrustar fuentes faltantes** en el archivo de salida. El mismo enfoque de captura de advertencias funciona para muchos otros escenarios de procesamiento de documentos, haciendo que tu código sea robusto y a prueba de futuro.

¡Feliz codificación, y que tus documentos siempre se rendericen hermosamente!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}