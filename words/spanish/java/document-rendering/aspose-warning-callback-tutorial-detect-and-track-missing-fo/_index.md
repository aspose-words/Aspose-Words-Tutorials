---
category: general
date: 2026-03-17
description: Aprende el tutorial de devolución de llamada de advertencia de Aspose
  para detectar fuentes faltantes y rastrear fuentes faltantes en documentos Java
  con un ejemplo completo y ejecutable.
draft: false
keywords:
- aspose warning callback tutorial
- detect missing fonts
- track missing fonts
language: es
og_description: Domina el tutorial de devolución de llamada de advertencia de Aspose
  para detectar fuentes faltantes y rastrear fuentes faltantes en tu flujo de trabajo
  de procesamiento de Word en Java.
og_title: Tutorial de devolución de llamada de advertencia de Aspose – Detectar fuentes
  faltantes
tags:
- Aspose.Words
- Java
- Font Substitution
- Document Processing
title: Tutorial de devolución de llamada de advertencia de Aspose – Detectar y rastrear
  fuentes faltantes
url: /es/java/document-rendering/aspose-warning-callback-tutorial-detect-and-track-missing-fo/
---

keep code block placeholders.

Tables: translate cells but keep technical terms.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# aspose warning callback tutorial – Detectar y rastrear fuentes faltantes

¿Alguna vez te has preguntado cómo **detectar fuentes faltantes** al convertir o editar archivos Word con Aspose.Words? No estás solo. En muchos proyectos reales, una fuente extraviada puede causar fallos de maquetación, y necesitas una forma fiable de **rastrear fuentes faltantes** antes de que te causen problemas más adelante.  

¿La buena noticia? El **aspose warning callback tutorial** te ofrece un gancho programático limpio que imprime exactamente esas advertencias de sustitución de fuentes en el momento en que ocurren. En esta guía recorreremos la configuración del callback, la carga de un documento y la visualización de las advertencias en acción, todo en Java.

Al final de este artículo podrás identificar fuentes faltantes automáticamente, registrarlas y decidir si incrustas una sustituta o ajustas tus archivos fuente. No se requieren herramientas externas.

## Requisitos previos

- **Java 8+** (el código compila con cualquier JDK reciente)
- **Aspose.Words for Java** versión 23.10 o superior – descárgalo desde el portal de Aspose o agrega la dependencia Maven.
- Un archivo DOCX de muestra que intencionalmente haga referencia a una fuente que no tengas instalada (por ejemplo, “Comic Sans MS” en una máquina Linux).

Eso es todo—sin bibliotecas adicionales, sin pasos de compilación complejos.

## Paso 1: Registrar un Warning Callback – El núcleo del aspose warning callback tutorial

Lo primero que enseña el tutorial es cómo adjuntar un listener de advertencias. Aspose.Words genera un objeto `WarningInfo` por cada problema que encuentra, y la bandera `WarningSource.FONT_SUBSTITUTION` nos indica exactamente cuándo se está sustituyendo una fuente.

```java
import com.aspose.words.*;

public class FontDiagnostics {
    public static void main(String[] args) throws Exception {

        // Step 1: Register a warning callback to capture font substitution warnings.
        Document.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // We only care about font‑substitution events.
                if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                    System.out.println("Font substitution warning:");
                    System.out.println("  Original:   " + info.getDescription());
                    System.out.println("  Substituted:" + info.getAdditionalInfo());
                }
            }
        });
```

**Por qué es importante:** Sin el callback, Aspose sustituye silenciosamente las fuentes faltantes y nunca sabrás qué glifos pueden verse mal. Al registrar la advertencia, puedes **detectar fuentes faltantes** temprano y decidir si incrustas la correcta.

> **Consejo profesional:** Si necesitas recopilar advertencias para un informe posterior, almacénalas en un `List<WarningInfo>` en lugar de imprimirlas directamente.

## Paso 2: Cargar el documento – Donde pueden ocultarse fuentes faltantes

Ahora cargamos el DOCX que podría estar haciendo referencia a fuentes no presentes en la máquina. El acto de cargar dispara el warning callback si alguna fuente falta.

```java
        // Step 2: Load a document that may contain missing fonts.
        Document document = new Document("YOUR_DIRECTORY/input.docx");
```

**¿Qué ocurre tras bambalinas?** Aspose analiza las definiciones de estilo del documento, recorre cada ejecución de texto y verifica el repositorio de fuentes del sistema. Cuando no encuentra una coincidencia exacta, recurre a una sustituta y lanza la advertencia que acabamos de conectar.

## Paso 3: Guardar el documento – Liberando las advertencias

Finalmente, guardamos el documento. La operación de guardado también vuelve a evaluar las fuentes, por lo que cualquier advertencia que no se haya emitido durante la carga aparecerá ahora.

```java
        // Step 3: Save the document; any font substitution warnings will be printed by the callback.
        document.save("YOUR_DIRECTORY/output.docx");
    }
}
```

Al ejecutar el programa, verás una salida en consola similar a:

```
Font substitution warning:
  Original:   Font "Comic Sans MS" not found.
  Substituted: Using "Arial" as fallback.
```

Esa salida demuestra que el **aspose warning callback tutorial** funciona, y has **detectado fuentes faltantes** y ahora estás **rastreando fuentes faltantes** a través del registro.

## Cómo detectar fuentes faltantes en un documento Word – Más allá de lo básico

El enfoque con callback es excelente para ejecuciones puntuales, pero a veces necesitas una utilidad reutilizable. Aquí tienes un contenedor rápido que puedes incorporar a cualquier proyecto:

```java
public class FontMissingChecker {
    private final List<String> missingFonts = new ArrayList<>();

    public FontMissingChecker() {
        Document.setWarningCallback((WarningInfo info) -> {
            if (info.getSource() == WarningSource.FONT_SUBSTITUTION) {
                missingFonts.add(info.getDescription());
            }
        });
    }

    public List<String> check(String path) throws Exception {
        new Document(path); // triggers warnings
        return missingFonts;
    }
}
```

Llamarlo así:

```java
FontMissingChecker checker = new FontMissingChecker();
List<String> fonts = checker.check("input.docx");
if (!fonts.isEmpty()) {
    System.out.println("Missing fonts detected:");
    fonts.forEach(System.out::println);
}
```

Ahora dispones de un método reutilizable de **detectar fuentes faltantes** que devuelve una lista que puedes alimentar a una canalización CI o a una interfaz de usuario.

## Rastrear fuentes faltantes con Aspose.Words – Informes para equipos

En un equipo más grande, quizá quieras generar un informe CSV de todas las fuentes faltantes en muchos documentos. Combina la utilidad anterior con una simple iteración de archivos:

```java
import java.nio.file.*;
import java.io.*;

public class BulkFontReporter {
    public static void main(String[] args) throws Exception {
        Path folder = Paths.get("YOUR_DIRECTORY");
        try (BufferedWriter writer = Files.newBufferedWriter(folder.resolve("missing-fonts-report.csv"))) {
            writer.write("Document,Missing Font\n");
            Files.list(folder)
                 .filter(p -> p.toString().endsWith(".docx"))
                 .forEach(p -> {
                     try {
                         FontMissingChecker checker = new FontMissingChecker();
                         List<String> missing = checker.check(p.toString());
                         for (String msg : missing) {
                             // Extract font name from description
                             String font = msg.replaceAll("Font \"(.*?)\".*", "$1");
                             writer.write(p.getFileName() + "," + font + "\n");
                         }
                     } catch (Exception e) {
                         // In a real app, log the error
                     }
                 });
        }
        System.out.println("Report generated at missing-fonts-report.csv");
    }
}
```

Ejecutar este script te proporcionará un CSV de **track missing fonts** que cada desarrollador podrá revisar antes de subir un documento a producción.

## Errores comunes y cómo evitarlos

| Problema | Por qué ocurre | Solución |
|----------|----------------|----------|
| **Callback no se dispara** | Olvidaste establecer el callback **antes** de cargar el documento. | Coloca `Document.setWarningCallback` al inicio de `main`. |
| **Solo aparece la primera advertencia** | Aspose almacena en caché las advertencias por instancia de `Document`. | Usa un objeto `Document` nuevo para cada archivo, o restablece el callback entre ejecuciones. |
| **Nombre de fuente incorrecto en el registro** | La descripción contiene texto extra (“Font … not found”). | Elimina con expresiones regulares como se muestra en el ejemplo CSV. |
| **Impacto de rendimiento en lotes grandes** | El callback se ejecuta en cada ejecución de texto, lo que puede ser costoso. | Limita la comprobación a un paso de pre‑vuelo; omite el guardado si solo necesitas detección. |

## Resultados esperados y verificación

1. **Salida en consola** – Deberías ver al menos una línea de “Font substitution warning” por cada fuente faltante.  
2. **Informe CSV** – Tras finalizar el script por lotes, abre `missing-fonts-report.csv` y verifica que cada fila enumere el nombre del documento y la fuente faltante exacta.  
3. **Documento guardado** – El DOCX de salida se renderizará usando las fuentes de sustitución, pero el diseño visual puede diferir del original.

Si alguno de estos pasos no se comporta como se describe, verifica que el JAR de Aspose.Words esté en tu classpath y que `input.docx` realmente haga referencia a una fuente ausente en tu sistema operativo.

## Conclusión

Acabas de completar un **aspose warning callback tutorial** que muestra cómo **detectar fuentes faltantes** y **rastrear fuentes faltantes** en aplicaciones Java. Al registrar un listener de advertencias, cargar el documento y, opcionalmente, exportar los hallazgos, obtienes total visibilidad sobre problemas relacionados con fuentes antes de que aparezcan en producción.

A continuación, podrías explorar:

- Incrustar la fuente faltante directamente con `LoadOptions.setFontSubstitution`.
- Usar la clase `FontSettings` para mapear fuentes faltantes a sustitutos específicos.
- Integrar el informe CSV en una canalización CI/CD para fallar compilaciones cuando aparezcan fuentes no documentadas.

Pruébalo, ajusta los callbacks a tu framework de registro y observa cómo tu flujo de trabajo documental se vuelve mucho más robusto. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}