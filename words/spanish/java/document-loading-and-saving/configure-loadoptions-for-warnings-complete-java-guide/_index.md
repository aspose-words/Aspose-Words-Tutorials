---
category: general
date: 2026-06-30
description: Configura LoadOptions para advertencias en Aspose.Words Java. Aprende
  a establecer una devolución de llamada de advertencia para la sustitución de fuentes
  y otras advertencias de opciones de carga.
draft: false
keywords:
- configure loadoptions for warnings
- Aspose.Words font substitution
- Java warning callback
- document loading options
- handle font warnings
language: es
og_description: Configure LoadOptions para advertencias en Aspose.Words Java. Esta
  guía muestra cómo capturar alertas de sustitución de fuentes con una devolución
  de llamada de advertencia.
og_title: Configurar LoadOptions para advertencias – Tutorial de Java
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Configure LoadOptions for warnings in Aspose.Words Java. Learn to set
    up a warning callback for font substitution and other load‑options warnings.
  headline: Configure LoadOptions for Warnings – Complete Java Guide
  type: TechArticle
tags:
- aspose-words
- java
- warnings
- font-substitution
title: Configurar LoadOptions para advertencias – Guía completa de Java
url: /es/java/document-loading-and-saving/configure-loadoptions-for-warnings-complete-java-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Configurar LoadOptions para advertencias – Guía completa de Java

¿Alguna vez necesitó **configurar LoadOptions para advertencias** al abrir un documento Word con Aspose.Words para Java? No está solo. Muchos desarrolladores se topan con un problema cuando una fuente faltante se sustituye silenciosamente, dejando el PDF final con un aspecto fuera de la marca. ¿La buena noticia? Al conectar un **callback de advertencia de Java** en su `LoadOptions`, puede capturar cada alerta de sustitución de fuentes en el momento en que ocurre.

En este tutorial recorreremos un ejemplo práctico que no solo muestra cómo configurar el callback, sino que también explica *por qué* cada parte es importante. Al final podrá **manejar advertencias de fuentes**, registrarlas o incluso reemplazar fuentes al vuelo—sin necesidad de adivinar.

## Qué obtendrá al finalizar

- Un programa Java completamente ejecutable que imprime cada advertencia de sustitución de fuentes.
- Una comprensión de la mecánica de **sustitución de fuentes de Aspose.Words**.
- Consejos para personalizar el manejo de advertencias en proyectos más grandes.
- Información sobre **opciones de carga de documentos** y cuándo ajustarlas.

> **Requisito previo:** Java 8+ y la biblioteca Aspose.Words para Java (versión 23.9 o posterior). No se necesitan otras dependencias externas.

---

## Paso 1: Configurar LoadOptions para advertencias

Lo primero que necesita es una instancia de `LoadOptions` que sepa que debe informar advertencias. Piense en `LoadOptions` como la caja de herramientas que entrega a Aspose.Words antes de que abra el archivo.

```java
// Step 1: Create LoadOptions and attach a warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Only react to font‑substitution warnings.
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            System.out.println("Font substitution detected: " + info.getDescription());
        }
    }
});
```

**Por qué esto es importante:**  
`LoadOptions` controla cómo la biblioteca lee el documento. Al asignar un `IWarningCallback`, le indica a Aspose.Words que invoque su código cada vez que encuentre algo relevante—como una fuente faltante. Sin esto, la biblioteca sustituiría la fuente silenciosamente y usted nunca lo sabría.

> **Consejo profesional:** Si desea capturar *todas* las advertencias, elimine la verificación `if`. Por ahora nos centramos en los problemas de fuentes porque son la fuente más común de sorpresas de diseño.

## Paso 2: Cargar el documento usando las opciones configuradas

Ahora que el callback está listo, cargue su `.docx` (o cualquier formato compatible) con el mismo `LoadOptions`. Aquí es donde las **opciones de carga de documentos** realmente entran en vigor.

```java
// Step 2: Load the document with the warning‑aware LoadOptions.
Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);
```

**Detrás de escena:**  
Cuando Aspose.Words analiza `input.docx`, escanea las tablas de fuentes. Si una fuente referenciada en el documento no está instalada en la máquina host, el motor genera una advertencia `FONT_SUBSTITUTION`, que activa inmediatamente el callback que definimos anteriormente.

## Paso 3: Guardar el documento – Las advertencias ya se han imprimido

Guardar el documento es sencillo, pero es el momento en que puede verificar que el callback se ejecutó correctamente. Todas las advertencias se imprimen durante el paso de carga, por lo que la operación de guardado es solo una limpieza.

```java
// Step 3: Save the document. Any warnings were already printed in Step 1.
document.save("YOUR_DIRECTORY/output.docx");
```

**Salida esperada en la consola:**  

```
Font substitution detected: Font 'Calibri' is not installed. Substituted with 'Arial'.
Font substitution detected: Font 'Times New Roman' is not installed. Substituted with 'Liberation Serif'.
```

Si no ve nada, es porque el documento usó solo fuentes instaladas, o el callback no se conectó correctamente—verifique nuevamente el Paso 1.

## Paso 4: Extender el callback para **manejar advertencias de fuentes** de forma elegante

Imprimir en la consola está bien para demostraciones, pero el código de producción a menudo necesita un manejo más completo: registrar en un archivo, enviar alertas o incluso cambiar fuentes programáticamente.

```java
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
            // Log to a file (simple example)
            try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                fw.write("WARN: " + info.getDescription() + System.lineSeparator());
            } catch (IOException e) {
                e.printStackTrace();
            }
            // Optionally replace the missing font with a fallback.
            FontSettings.getDefaultInstance().setSubstitutionSettings(
                new FontSubstitutionSettings() {{
                    getTableSubstitution().addSubstitutes("Calibri", "Arial");
                }}
            );
        }
    }
});
```

**Por qué haría esto:**  
Un archivo de registro le brinda información post‑mortem, especialmente al procesar lotes de documentos. El bloque de sustitución opcional muestra cómo **configurar LoadOptions para advertencias** *y* intervenir para aplicar una política de fuentes corporativa.

## Avanzado: Controlar otros escenarios de **sustitución de fuentes de Aspose.Words**

El callback de advertencia no se limita a fuentes faltantes. También puede capturar:

- **Caracteres Unicode no compatibles** (`WarningType.UNSUPPORTED_CHAR`).
- **Problemas de scripts complejos** (`WarningType.COMPLEX_SCRIPT`).

Simplemente expanda la sentencia `if`:

```java
if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
    // handle fonts
} else if (info.getWarningType() == WarningType.UNSUPPORTED_CHAR) {
    System.out.println("Unsupported character: " + info.getDescription());
}
```

Esto hace que su solución sea robusta para documentos multilingües, un caso límite común en aplicaciones globales.

## Ejemplo completo y funcional

A continuación se muestra el programa completo, listo para ejecutar. Péguelo en cualquier IDE de Java, reemplace los marcadores `YOUR_DIRECTORY` y presione *Run*.

```java
import com.aspose.words.*;

import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDemo {
    public static void main(String[] args) throws Exception {

        // Step 1: Configure LoadOptions for warnings.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution: " + info.getDescription());

                    // Optional: Log to a file.
                    try (FileWriter fw = new FileWriter("font-warnings.log", true)) {
                        fw.write("WARN: " + info.getDescription() + System.lineSeparator());
                    } catch (IOException e) {
                        e.printStackTrace();
                    }

                    // Optional: Force a specific fallback font.
                    FontSettings.getDefaultInstance().setSubstitutionSettings(
                        new FontSubstitutionSettings() {{
                            getTableSubstitution().addSubstitutes("Calibri", "Arial");
                        }}
                    );
                }
            }
        });

        // Step 2: Load the document using the configured LoadOptions.
        Document document = new Document("YOUR_DIRECTORY/input.docx", loadOptions);

        // Step 3: Save the document. Warnings have already been printed.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

### Resultado esperado

- La consola imprime cualquier advertencia de sustitución de fuentes.
- `font-warnings.log` contiene una lista con marca de tiempo (si mantuvo el registro opcional).
- `output.docx` se guarda con fuentes sustituidas, coincidiendo con la alternativa que definió.

## Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **No aparecen advertencias** | El callback no se adjuntó, o el documento usa solo fuentes instaladas. | Verifique que `loadOptions.setWarningCallback(...)` se llame *antes* de cargar el documento. |
| **FileNotFoundException** on `input.docx` | La ruta es incorrecta o el archivo no está incluido en el proyecto. | Utilice una ruta absoluta o coloque el archivo en la carpeta de recursos del proyecto. |
| **Ralentización del rendimiento** al procesar miles de documentos | Registro excesivo en disco por cada advertencia. | Almacene los registros en búfer y escríbalos en lotes, o limite el registro a advertencias críticas únicamente. |
| **Sustitución de fuente inesperada** a pesar del fallback | La tabla de sustitución no se aplicó lo suficientemente pronto. | Establezca la configuración de sustitución **antes** de cargar el documento, o use `FontSettings.setSubstitutionSettings` globalmente. |

## Próximos pasos

Ahora que ha dominado **configurar LoadOptions para advertencias**, considere los siguientes temas de seguimiento:

- **Procesamiento por lotes**: Recorrer un directorio de documentos, agregando todas las advertencias de fuentes en un informe único.
- **Proveedores de fuentes personalizados**: Cargar fuentes desde un recurso compartido en red o recursos incrustados en lugar del SO local.
- **Integrar con frameworks de registro** como Log4j para trazabilidad a nivel empresarial.
- Explore otras **opciones de carga de documentos** como la detección de `LoadFormat` o el manejo de `Password` para archivos protegidos.

Cada uno de estos se basa en el mismo patrón—crear un objeto `LoadOptions`, adjuntar los callbacks apropiados y dejar que Aspose.Words haga el trabajo pesado.

## Conclusión

Hemos profundizado en cómo **configurar LoadOptions para advertencias** en Aspose.Words para Java, configurar un **callback de advertencia de Java** y usar esa información para **manejar advertencias de fuentes** de manera inteligente. El código es compacto, los conceptos son claros, y ahora tiene una base sólida para ampliar el manejo de advertencias a otros escenarios como caracteres no compatibles o scripts complejos.

Pruébelo, ajuste la tabla de sustitución para que coincida con las fuentes de su marca, y observe cómo desaparecen esas sustituciones silenciosas de fuentes. ¡Feliz codificación!

--- 

![Diagram showing the flow of configuring LoadOptions for warnings, loading a document, capturing font substitution events, and saving the output](configure-loadoptions-for-warnings-diagram.png "Configure LoadOptions for warnings flow")


## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que se basan en las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarle a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en sus propios proyectos.

- [Capturar advertencias de sustitución de fuentes en Java con Aspose.Words – Guía completa](/words/english/java/document-loading-and-saving/capture-font-substitution-warnings-in-java-with-aspose-words/)
- [Cómo establecer LoadOptions en Aspose.Words para Java](/words/english/java/document-loading-and-saving/using-load-options/)
- [Cómo cargar documentos RTF configurando opciones de carga RTF en Aspose.Words para Java](/words/english/java/document-loading-and-saving/configuring-rtf-load-options/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}