---
category: general
date: 2026-02-15
description: Aprende cómo obtener fuentes faltantes al cargar un documento de Word
  en Java usando Aspose.Words. Incluye devoluciones de llamada de advertencia y manejo
  de sustitución de fuentes.
draft: false
keywords:
- how to get missing fonts
- Aspose.Words missing font
- font substitution warning
- Java LoadOptions warning callback
- document processing Java
language: es
og_description: Cómo obtener fuentes faltantes en Java con Aspose.Words. Descubre
  los callbacks de advertencia, la gestión de sustitución de fuentes y las mejores
  prácticas para el procesamiento de documentos.
og_title: Cómo obtener fuentes faltantes en Java – Guía de Aspose.Words
tags:
- Aspose.Words
- Java
- Font Management
title: Cómo obtener fuentes faltantes en Java – Guía de Aspose.Words
url: /es/java/document-loading-and-saving/how-to-get-missing-fonts-in-java-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo obtener fuentes faltantes en Java – Guía de Aspose.Words

¿Alguna vez abrió un documento Word en Java solo para ver extraños reemplazos de fuentes y se preguntó **cómo obtener fuentes faltantes**? No es la primera vez que se encuentra con esa sorpresa. En muchas aplicaciones empresariales, las advertencias de fuentes faltantes pueden romper la fidelidad visual de informes, contratos o material de marketing.

La buena noticia? Aspose.Words le brinda una forma sencilla de capturar esas advertencias mediante un callback, de modo que pueda registrar, reemplazar o incluso alertar a los usuarios antes de que el documento se renderice. En este tutorial recorreremos un ejemplo completo y ejecutable que muestra **cómo obtener fuentes faltantes**, explica por qué el callback es importante y cubre algunos trucos de casos límite que podría necesitar en proyectos del mundo real.

> **Consejo profesional:** Si ya está usando Aspose.Words 22.12 o una versión más reciente, la API mostrada a continuación funciona listo para usar sin configuración adicional.

---

![Diagram illustrating how to get missing fonts using Aspose.Words warning callback](how-to-get-missing-fonts-diagram.png "how to get missing fonts diagram")

## Qué cubre este tutorial

- Configurar un **callback de advertencias de Java LoadOptions** para capturar advertencias de sustitución de fuentes.  
- Filtrar las advertencias para que solo vea las relacionadas con fuentes faltantes.  
- Imprimir un informe claro y legible sobre qué fuentes fueron sustituidas y por qué fueron reemplazadas.  
- Consejos para manejar documentos grandes, personalizar el nivel de advertencia e integrar la solución en una canalización de procesamiento más grande.

Al final de esta guía podrá responder la pregunta “**cómo obtener fuentes faltantes**?” con un fragmento de código listo para ejecutar y una comprensión sólida de la mecánica subyacente.

### Requisitos previos

- Java 8 o una versión más reciente instalada.  
- Biblioteca Aspose.Words para Java (descárguela del sitio oficial o agréguela mediante Maven/Gradle).  
- Un documento Word que haga referencia a una fuente no instalada en su máquina (por ejemplo, `MissingFont.docx`).  

Si le falta alguno de estos, obtenga la biblioteca ahora—agregarla a Maven es tan simple como:

```xml
<dependency>
    <groupId>com.aspose</groupId>
    <artifactId>aspose-words</artifactId>
    <version>23.9</version> <!-- replace with the latest version -->
</dependency>
```

---

## Paso 1: Preparar una colección para advertencias de sustitución de fuentes

Antes de cargar el documento necesitamos un lugar para almacenar cualquier advertencia que emita Aspose.Words. Un `ArrayList<WarningInfo>` funciona bien porque preserva el orden y nos permite iterar después.

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

// Step 1: Create a list that will hold warning information.
List<WarningInfo> fontWarnings = new ArrayList<>();
```

*Por qué es importante:* El callback de advertencias puede activarse docenas de veces para un solo archivo—piense en cada glifo faltante, cada problema de imagen incrustada, etc. Al recopilarlos primero, mantiene la fase de carga rápida y difiere el procesamiento a un bucle controlado.

---

## Paso 2: Configurar LoadOptions con un callback de advertencias

Aspose.Words le permite conectar un `IWarningCallback`. Dentro del callback añadiremos cada `WarningInfo` a nuestra lista del Paso 1.

```java
// Step 2: Set up LoadOptions with a custom warning callback.
LoadOptions loadOptions = new LoadOptions();
loadOptions.setWarningCallback(new IWarningCallback() {
    @Override
    public void warning(WarningInfo info) {
        // Capture every warning; we'll filter later.
        fontWarnings.add(info);
    }
});
```

*Explicación:* El método `warning` se invoca **síncronamente** durante la carga del documento. Al simplemente insertar el `WarningInfo` en `fontWarnings`, evitamos cualquier I/O intensivo (como registrar en un archivo) que podría ralentizar la carga. Este patrón—recopilar‑luego‑procesar—es la forma recomendada de manejar grandes lotes de advertencias.

---

## Paso 3: Cargar el documento usando las opciones configuradas

Ahora realmente leemos el archivo Word. Si el documento contiene fuentes que no están instaladas, Aspose.Words las sustituirá automáticamente y disparará el callback de advertencias que acabamos de conectar.

```java
// Step 3: Load the document with the warning‑aware LoadOptions.
String filePath = "YOUR_DIRECTORY/MissingFont.docx"; // adjust to your environment
Document doc = new Document(filePath, loadOptions);
```

*¿Qué ocurre internamente?* Aspose.Words analiza la tabla de fuentes del archivo, la compara con las fuentes disponibles en el SO anfitrión, y por cada entrada faltante crea un `WarningInfo` con `WarningSource.FontSubstitution`. Esa fuente es la clave que usaremos para aislar las advertencias de fuentes faltantes.

---

## Paso 4: Filtrar y mostrar solo advertencias de sustitución de fuentes

Después de cargar, `fontWarnings` puede contener una mezcla de mensajes (p. ej., funciones obsoletas, problemas de imágenes). Solo nos importan las fuentes faltantes, así que recorremos la lista e imprimimos un informe conciso.

```java
// Step 4: Output any font‑substitution warnings that were captured.
for (WarningInfo warning : fontWarnings) {
    if (warning.getSource() == WarningSource.FontSubstitution) {
        System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                           warning.getAdditionalInfo() + "'");
    }
}
```

**Salida de ejemplo**

```
Substituted 'Comic Sans MS' with 'Arial'
Substituted 'Times New Roman PS' with 'Times New Roman'
```

*Por qué es útil:* El campo `description` le indica qué fuente solicitó el documento, mientras que `additionalInfo` le indica qué fuente usó realmente Aspose.Words. Con esos datos puede:

- Pedir al usuario que instale la fuente faltante.  
- Incrustar programáticamente una fuente sustituta en el documento (`doc.getFontInfos().add(...)`).  
- Registrar el evento para auditorías de cumplimiento.

---

## Manejo de casos límite y variaciones comunes

### 1. Suprimir advertencias que no son de fuentes

Si solo desea mensajes relacionados con fuentes, puede restringir el callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        fontWarnings.add(info);
    }
});
```

Esto reduce el consumo de memoria al procesar lotes enormes.

### 2. Ajustar la severidad de las advertencias

Aspose.Words categoriza las advertencias por `WarningType`. Para fuentes faltantes típicamente verá `WarningType.FontSubstitution`. Si necesita tratarlas como errores (p. ej., abortar la carga), lance una excepción dentro del callback:

```java
loadOptions.setWarningCallback(info -> {
    if (info.getSource() == WarningSource.FontSubstitution) {
        throw new RuntimeException("Missing font detected: " + info.getDescription());
    }
});
```

### 3. Trabajar con streams en lugar de archivos

A veces los documentos provienen de una base de datos o una solicitud HTTP. El mismo enfoque funciona con un `InputStream`:

```java
InputStream docStream = new ByteArrayInputStream(bytesFromDb);
Document doc = new Document(docStream, loadOptions);
```

Solo recuerde cerrar el stream después de la carga.

### 4. Usar una carpeta de fuentes personalizada

Si tiene una colección de fuentes corporativas almacenadas en una unidad compartida, indique a Aspose.Words esa carpeta:

```java
loadOptions.setFontSettings(new FontSettings());
loadOptions.getFontSettings().setFontsFolder("C:/CorporateFonts", true);
```

Ahora la biblioteca buscará allí *antes* de recurrir a las fuentes del sistema, reduciendo drásticamente el número de advertencias de fuentes faltantes.

---

## Ejemplo completo y funcional

Juntando todo, aquí tiene una clase autónoma que puede insertar en cualquier proyecto Java:

```java
import com.aspose.words.*;
import java.util.ArrayList;
import java.util.List;

public class MissingFontDetector {

    public static void main(String[] args) {
        // 1️⃣ Prepare a collection for warnings.
        List<WarningInfo> fontWarnings = new ArrayList<>();

        // 2️⃣ Create LoadOptions with a warning callback.
        LoadOptions loadOptions = new LoadOptions();
        loadOptions.setWarningCallback(info -> fontWarnings.add(info));

        // (Optional) Point to a custom font folder.
        // FontSettings fontSettings = new FontSettings();
        // fontSettings.setFontsFolder("C:/CorporateFonts", true);
        // loadOptions.setFontSettings(fontSettings);

        // 3️⃣ Load the document.
        String docPath = "YOUR_DIRECTORY/MissingFont.docx";
        Document doc;
        try {
            doc = new Document(docPath, loadOptions);
        } catch (Exception e) {
            System.err.println("Failed to load document: " + e.getMessage());
            return;
        }

        // 4️⃣ Print missing‑font warnings.
        System.out.println("=== Missing Font Report ===");
        for (WarningInfo warning : fontWarnings) {
            if (warning.getSource() == WarningSource.FontSubstitution) {
                System.out.println("Substituted '" + warning.getDescription() + "' with '" +
                                   warning.getAdditionalInfo() + "'");
            }
        }
        System.out.println("=== End of Report ===");
    }
}
```

Ejecútelo y verá una lista ordenada de cada fuente que Aspose.Words tuvo que reemplazar. Sin bibliotecas extra, sin magia oculta—solo Java puro y el poder de la API de **fuentes faltantes de Aspose.Words**.

---

## Conclusión

Hemos respondido la pregunta central **cómo obtener fuentes faltantes** en un entorno Java usando Aspose.Words. Al adjuntar un callback de advertencias `LoadOptions`, recopilar objetos `WarningInfo` y filtrar por fuentes `FontSubstitution`, obtiene una visibilidad completa de los problemas relacionados con fuentes antes de que ocurra cualquier renderizado. El enfoque escala desde utilidades de un solo archivo hasta procesadores por lotes masivos, y es lo suficientemente flexible para acomodar carpetas de fuentes personalizadas, manejo de severidad o entradas basadas en streams.

¿Próximos pasos? Intente incrustar las fuentes sustitutas directamente en el documento (`doc.getFontInfos().add(...)`) para que el archivo final sea realmente autónomo, o integre el informe de advertencias en un panel de monitoreo. También puede explorar temas relacionados como **procesamiento de documentos Java**, **advertencia de sustitución de fuentes Aspose.Words** y **callback de advertencias Java LoadOptions** para profundizar su experiencia.

¡Feliz codificación, y que sus documentos siempre se rendericen con las fuentes que espera!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}