---
category: general
date: 2026-07-06
description: Crea DocumentConfig en Java para rastrear fuentes faltantes usando Aspose.Words
  – una guía completa, paso a paso, para desarrolladores.
draft: false
keywords:
- create documentconfig
- track missing fonts
language: es
og_description: Crea DocumentConfig en Java para rastrear fuentes faltantes con Aspose.Words.
  Aprende el flujo de trabajo completo, desde la configuración hasta el manejo de
  advertencias.
og_title: Crear DocumentConfig en Java – Rastrear fuentes faltantes
schemas:
- author: Aspose
  dateModified: '2026-07-06'
  description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  headline: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  type: TechArticle
- description: Create DocumentConfig in Java to track missing fonts using Aspose.Words
    – a complete, step‑by‑step guide for developers.
  name: Create DocumentConfig in Java – Track Missing Fonts with Aspose.Words
  steps:
  - name: Prerequisites
    text: '| Requirement | Reason | |-------------|--------| | Java 8 or newer | Aspose.Words
      for Java supports JDK 8+. | | Aspose.Words for Java library (latest version)
      | Provides `DocumentConfig`, `IWarningCallback`, etc. | | An IDE or build tool
      (IntelliJ, Eclipse, Maven/Gradle) | To compile and run the sa'
  - name: Maven
    text: '```xml <dependency> <groupId>com.aspose</groupId> <artifactId>aspose-words</artifactId>
      <version>23.12</version> <!-- use the latest version --> </dependency> ```'
  - name: Gradle (Kotlin DSL)
    text: '```kotlin implementation("com.aspose:aspose-words:23.12") ```'
  type: HowTo
tags:
- Aspose.Words
- Java
- Font Substitution
title: Crear DocumentConfig en Java – Rastrear fuentes faltantes con Aspose.Words
url: /es/java/licensing-and-configuration/create-documentconfig-in-java-track-missing-fonts-with-aspos/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crear DocumentConfig en Java – Rastrear fuentes faltantes con Aspose.Words

**Crear DocumentConfig en Java** para monitorizar advertencias de sustitución de fuentes al cargar un documento Word. ¿Alguna vez te has preguntado por qué algunos caracteres se ven extraños después de abrir un DOCX? Lo más probable es que la fuente original no esté en la máquina, y Aspose.Words la sustituya silenciosamente. En este tutorial te mostraremos exactamente cómo **rastrear fuentes faltantes** para que nunca te sorprenda un glifo inesperado nuevamente.

Recorreremos todo lo que necesitas: la configuración Maven/Gradle, el código que crea un `DocumentConfig`, un `IWarningCallback` personalizado que filtra solo alertas de sustitución de fuentes, y una forma rápida de registrar esos mensajes. Al final tendrás un ejemplo ejecutable que imprime cada advertencia de fuente faltante en la consola (o en un archivo, si lo prefieres).

---

## Lo que aprenderás

- Por qué un `DocumentConfig` es el lugar adecuado para interceptar eventos de sustitución de fuentes.  
- Cómo **rastrear fuentes faltantes** sin contaminar tus registros con advertencias no relacionadas.  
- Un programa Java completo, listo para copiar y pegar, que demuestra la técnica.  
- Consejos para ampliar la solución—p. ej., escribir advertencias en una base de datos o enviar alertas por correo electrónico.

### Prerrequisitos

| Requisito | Razón |
|-----------|-------|
| Java 8 o superior | Aspose.Words for Java soporta JDK 8+. |
| Biblioteca Aspose.Words for Java (última versión) | Proporciona `DocumentConfig`, `IWarningCallback`, etc. |
| Un IDE o herramienta de compilación (IntelliJ, Eclipse, Maven/Gradle) | Para compilar y ejecutar el ejemplo. |
| Un archivo DOCX que haga referencia a fuentes que no tienes instaladas | Para ver la advertencia en acción. |

Si ya tienes un proyecto, solo agrega la dependencia de Aspose y estarás listo para continuar.

---

## Paso 1: Añadir Aspose.Words a tu compilación

### Maven

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.12</version> <!-- use the latest version -->
</dependency>
```

### Gradle (Kotlin DSL)

```kotlin
implementation("com.aspose:aspose-words:23.12")
```

> **Consejo profesional:** La versión de prueba gratuita funciona perfectamente para pruebas, pero recuerda aplicar una licencia para producción y eliminar la marca de agua de evaluación.

---

## Paso 2: Crear DocumentConfig y registrar un Warning Callback

El corazón de la solución vive en este fragmento. **Creamos un DocumentConfig**, adjuntamos un `IWarningCallback` personalizado y le indicamos que **solo rastree fuentes faltantes**.

```java
import com.aspose.words.*;

public class FontSubstitutionDiagnostics {

    public static void main(String[] args) throws Exception {
        // 1️⃣ Create a configuration object.
        DocumentConfig config = new DocumentConfig();

        // 2️⃣ Attach a warning callback that reacts only to font‑substitution warnings.
        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) {
                // 3️⃣ Filter for FONT_SUBSTITUTION type.
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    // 4️⃣ This is where we **track missing fonts**.
                    System.out.println("Font substituted: " + info.getDescription());
                }
            }
        });

        // 5️⃣ Load the document using the configuration we just prepared.
        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);

        // Optional: do something with the document, e.g., save as PDF.
        // doc.save("output.pdf");
    }
}
```

**Por qué funciona:** Cuando Aspose.Words analiza un documento, emite objetos `WarningInfo` por cualquier irregularidad. Al proporcionar un callback, interceptas esas advertencias *antes* de que desaparezcan en el vacío. La condición `if` garantiza que solo **rastreemos fuentes faltantes**, ignorando otras advertencias como etiquetas obsoletas o características no soportadas.

---

## Paso 3: Ejecutar el ejemplo y observar la salida

Coloca un DOCX que haga referencia a una fuente que no tienes (p. ej., “Comic Sans MS” en una máquina Linux). Ejecuta el programa:

```bash
$ javac -cp "aspose-words-23.12.jar" FontSubstitutionDiagnostics.java
$ java -cp ".:aspose-words-23.12.jar" FontSubstitutionDiagnostics
```

Deberías ver algo similar a:

```
Font substituted: Font "Comic Sans MS" was not found. Substituted with "Arial".
Font substituted: Font "Times New Roman" was not found. Substituted with "Liberation Serif".
```

Cada línea corresponde a una fuente faltante que Aspose sustituyó automáticamente. Si no existen fuentes faltantes, el programa permanece silencioso—exactamente lo que deseas para un registro limpio.

---

## Paso 4: Persistir la lista de fuentes faltantes (Opcional)

Imprimir en la consola es útil para demostraciones, pero en un servicio real probablemente querrás almacenar los datos. Aquí tienes una forma rápida de escribir las advertencias en un archivo de texto.

```java
import java.io.FileWriter;
import java.io.IOException;

public class FontSubstitutionDiagnostics {

    private static final String LOG_PATH = "missing-fonts.log";

    public static void main(String[] args) throws Exception {
        DocumentConfig config = new DocumentConfig();

        config.setWarningCallback(new IWarningCallback() {
            @Override
            public void warning(WarningInfo info) throws IOException {
                if (info.getWarningType() == WarningType.FONT_SUBSTITUTION) {
                    String message = "Font substituted: " + info.getDescription();
                    System.out.println(message);
                    try (FileWriter fw = new FileWriter(LOG_PATH, true)) {
                        fw.write(message + System.lineSeparator());
                    }
                }
            }
        });

        Document doc = new Document("YOUR_DIRECTORY/input.docx", config);
    }
}
```

Ahora cada evento de fuente faltante agrega una línea a `missing-fonts.log`. Más tarde puedes analizar ese archivo, alimentarlo a un panel de monitoreo o incluso activar una alerta si una fuente crítica desaparece de tu servidor.

---

## Paso 5: Problemas comunes y cómo evitarlos

| Síntoma | Causa probable | Solución |
|---------|----------------|----------|
| No aparecen advertencias aunque el DOCX use fuentes desconocidas | Callback no registrado o `setWarningCallback` llamado después de cargar el documento | Asegúrate de que `config.setWarningCallback(...)` se ejecute **antes** de crear la instancia `Document`. |
| La aplicación se bloquea con `NullPointerException` | `info.getDescription()` devuelve `null` para algunos tipos raros de advertencia | Protégete contra null: `String desc = info.getDescription(); if (desc != null) …` |
| Demasiadas advertencias no relacionadas inundan la consola | ¿El callback filtra solo `FONT_SUBSTITUTION`? | Verifica la condición `if (info.getWarningType() == WarningType.FONT_SUBSTITUTION)`. |
| Ralentización del rendimiento en lotes grandes | Escribir en archivo de forma sincrónica para cada advertencia | Escribe en lotes o usa un `BufferedWriter` para reducir la sobrecarga de I/O. |

---

## Paso 6: Ampliando la solución – De la consola a la empresa

- **Registro en base de datos:** Reemplaza el `FileWriter` con una inserción JDBC; almacena `documentName`, `missingFont` y `timestamp`.  
- **Alertas por correo electrónico:** Conecta con JavaMail; envía un resumen después de procesar un lote de documentos.  
- **Lógica de sustitución personalizada:** En lugar de dejar que Aspose elija una alternativa, podrías cargar una colección de fuentes local mediante `FontSettings.setFontsFolder()` y volver a cargar si ocurre una sustitución.

Estas extensiones conservan la idea central—**crear documentconfig** y **rastrear fuentes faltantes**—manteniéndola intacta mientras se escala a necesidades de producción.

---

## Conclusión

Ahora dispones de un patrón sólido, listo para copiar y pegar, para **crear un DocumentConfig** en Java y usarlo para **rastrear fuentes faltantes** con Aspose.Words. El enfoque es liviano, requiere solo unas pocas líneas de código y te brinda control total sobre cómo se manejan las advertencias de sustitución de fuentes. Ya sea que estés construyendo un servicio de conversión de documentos, un generador automático de informes o una herramienta de auditoría de cumplimiento, saber exactamente qué fuentes faltan puede ahorrarte horas de depuración.

¿Próximos pasos? Prueba a cambiar la salida de consola por un registro JSON estructurado, o integra el callback en un microservicio Spring Boot que procese cargas en tiempo real. Y si te encuentras con casos límite—por ejemplo, una fuente OpenType personalizada que Aspose no pueda analizar—deja un comentario abajo; lo resolveremos juntos.

¡Feliz codificación, y que tus PDFs siempre se rendericen con las fuentes que esperas!

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar funciones adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Uso de fuentes en Aspose.Words para Java](/words/english/java/using-document-elements/using-fonts/)
- [Personalizar colores de tema y fuentes en Aspose.Words Java: Guía completa](/words/english/java/formatting-styles/customize-theme-colors-fonts-aspose-words-java/)
- [Cómo crear documentos PDF con Aspose.Words para Java | API de procesamiento de documentos](/words/english/java/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}