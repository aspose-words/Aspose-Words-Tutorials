---
date: 2025-12-20
description: Aprenda a organizar archivos por tipo y detectar formatos de documentos
  en Java con Aspose.Words. Compatible con DOC, DOCX, RTF y más.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: Organizar archivos por tipo usando Aspose.Words para Java
url: /es/java/document-loading-and-saving/determining-document-format/
weight: 25
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Organizar archivos por tipo usando Aspose.Words para Java

Cuando necesitas **organizar archivos por tipo** en una aplicación Java, el primer paso es determinar de forma fiable el formato de cada documento. Aspose.Words para Java simplifica esto, permitiéndote detectar DOC, DOCX, RTF, HTML, ODT y muchos otros formatos, incluso archivos cifrados o desconocidos. En esta guía recorreremos la configuración de carpetas, la detección de formatos de archivo y la clasificación automática de tus archivos.

## Respuestas rápidas
- **¿Qué significa “organizar archivos por tipo”?** Significa mover automáticamente los documentos a carpetas según el formato detectado (p. ej., DOCX, PDF, RTF).  
- **¿Qué biblioteca ayuda a detectar el formato de archivo en Java?** Aspose.Words para Java proporciona `FileFormatUtil.detectFileFormat()`.  
- **¿Puede la API identificar tipos de archivo desconocidos?** Sí, devuelve `LoadFormat.UNKNOWN` para archivos no compatibles o no reconocibles.  
- **¿Se admite la detección de documentos cifrados?** Absolutamente; la bandera `FileFormatInfo.isEncrypted()` indica si un archivo está protegido con contraseña.  
- **¿Necesito una licencia para uso en producción?** Se requiere una licencia válida de Aspose.Words para implementaciones comerciales.

## Introducción: Organizar archivos por tipo con Aspose.Words para Java

Al trabajar con procesamiento de documentos en Java, es crucial determinar el formato de los archivos que manejas. Aspose.Words para Java ofrece potentes funcionalidades para **detect file format java**, y te guiaremos a través del proceso de organizar tus archivos de manera eficiente.

## Requisitos previos

Antes de comenzar, asegúrate de contar con los siguientes requisitos:

- [Aspose.Words para Java](https://releases.aspose.com/words/java/)
- Java Development Kit (JDK) instalado en tu sistema
- Conocimientos básicos de programación en Java

## Paso 1: Configuración de directorios

Primero, necesitamos crear los directorios necesarios para organizar nuestros archivos de manera eficaz. Crearemos carpetas para diferentes tipos de documentos.

```java
File supportedDir = new File("Your Directory Path" + "Supported");
File unknownDir = new File("Your Directory Path" + "Unknown");
File encryptedDir = new File("Your Directory Path" + "Encrypted");
File pre97Dir = new File("Your Directory Path" + "Pre97");

// Create the directories if they do not already exist.
if (!supportedDir.exists())
    supportedDir.mkdir();
if (!unknownDir.exists())
    unknownDir.mkdir();
if (!encryptedDir.exists())
    encryptedDir.mkdir();
if (!pre97Dir.exists())
    pre97Dir.mkdir();
```

Hemos creado directorios para tipos soportados, desconocidos, cifrados y documentos pre‑97.

## Paso 2: Detección del formato del documento

Ahora, detectemos el formato de los documentos en nuestras carpetas. Utilizaremos Aspose.Words para Java para lograrlo.

```java
Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
    .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
    .map(File::getPath)
    .collect(Collectors.toSet());

for (String fileName : listFiles) {
    String nameOnly = Paths.get(fileName).getFileName().toString();
    System.out.println(nameOnly);
    FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);

    // Display the document type
    switch (info.getLoadFormat()) {
        case LoadFormat.DOC:
            System.out.println("\tMicrosoft Word 97-2003 document.");
            break;
        // Add cases for other document formats as needed
    }

    // Handle encrypted documents
    if (info.isEncrypted()) {
        System.out.println("\tAn encrypted document.");
        FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
    } else {
        // Handle other document types
        switch (info.getLoadFormat()) {
            case LoadFormat.DOC_PRE_WORD_60:
                FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                break;
            case LoadFormat.UNKNOWN:
                FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                break;
            default:
                FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                break;
        }
    }
}
```

En este fragmento iteramos sobre los archivos, **detect file format java**, y los organizamos en las carpetas correspondientes.

## Código fuente completo para determinar el formato del documento en Aspose.Words para Java

```java
        File supportedDir = new File("Your Directory Path" + "Supported");
        File unknownDir = new File("Your Directory Path" + "Unknown");
        File encryptedDir = new File("Your Directory Path" + "Encrypted");
        File pre97Dir = new File("Your Directory Path" + "Pre97");
        // Create the directories if they do not already exist.
        if (supportedDir.exists() == false)
            supportedDir.mkdir();
        if (unknownDir.exists() == false)
            unknownDir.mkdir();
        if (encryptedDir.exists() == false)
            encryptedDir.mkdir();
        if (pre97Dir.exists() == false)
            pre97Dir.mkdir();
        Set<String> listFiles = Stream.of(new File("Your Directory Path").listFiles())
                .filter(file -> !file.getName().endsWith("Corrupted document.docx") && !Files.isDirectory(file.toPath()))
                .map(File::getPath)
                .collect(Collectors.toSet());
        for (String fileName : listFiles) {
            String nameOnly = Paths.get(fileName).getFileName().toString();
            System.out.println(nameOnly);
            FileFormatInfo info = FileFormatUtil.detectFileFormat(fileName);
            // Display the document type
            switch (info.getLoadFormat()) {
                case LoadFormat.DOC:
                    System.out.println("\tMicrosoft Word 97-2003 document.");
                    break;
                case LoadFormat.DOT:
                    System.out.println("\tMicrosoft Word 97-2003 template.");
                    break;
                case LoadFormat.DOCX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Document.");
                    break;
                case LoadFormat.DOCM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
                    break;
                case LoadFormat.DOTX:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Free Template.");
                    break;
                case LoadFormat.DOTM:
                    System.out.println("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
                    break;
                case LoadFormat.FLAT_OPC:
                    System.out.println("\tFlat OPC document.");
                    break;
                case LoadFormat.RTF:
                    System.out.println("\tRTF format.");
                    break;
                case LoadFormat.WORD_ML:
                    System.out.println("\tMicrosoft Word 2003 WordprocessingML format.");
                    break;
                case LoadFormat.HTML:
                    System.out.println("\tHTML format.");
                    break;
                case LoadFormat.MHTML:
                    System.out.println("\tMHTML (Web archive) format.");
                    break;
                case LoadFormat.ODT:
                    System.out.println("\tOpenDocument Text.");
                    break;
                case LoadFormat.OTT:
                    System.out.println("\tOpenDocument Text Template.");
                    break;
                case LoadFormat.DOC_PRE_WORD_60:
                    System.out.println("\tMS Word 6 or Word 95 format.");
                    break;
                case LoadFormat.UNKNOWN:
                    System.out.println("\tUnknown format.");
                    break;
            }
            if (info.isEncrypted()) {
                System.out.println("\tAn encrypted document.");
                FileUtils.copyFile(new File(fileName), new File(encryptedDir, nameOnly));
            } else {
                switch (info.getLoadFormat()) {
                    case LoadFormat.DOC_PRE_WORD_60:
                        FileUtils.copyFile(new File(fileName), new File(pre97Dir, nameOnly));
                        break;
                    case LoadFormat.UNKNOWN:
                        FileUtils.copyFile(new File(fileName), new File(unknownDir, nameOnly));
                        break;
                    default:
                        FileUtils.copyFile(new File(fileName), new File(supportedDir, nameOnly));
                        break;
                }
            }
        }

```

## Cómo detectar el formato de archivo en Java

El método `FileFormatUtil.detectFileFormat()` inspecciona el encabezado del archivo y devuelve un objeto `FileFormatInfo`. Este objeto indica el **load format**, si el archivo está cifrado y otros metadatos útiles. Con esta información puedes **identificar tipos de archivo desconocidos** de forma programática y decidir cómo procesar cada uno.

## Identificar tipos de archivo desconocidos

Cuando la API devuelve `LoadFormat.UNKNOWN`, el archivo está dañado o utiliza un formato que Aspose.Words no soporta. En nuestro código de ejemplo movemos esos archivos a la carpeta **Unknown** para que puedas revisarlos más tarde.

## Problemas comunes y soluciones

| Problema | Razón | Solución |
|----------|-------|----------|
| Los archivos siempre se colocan en la carpeta *Supported* | `FileFormatUtil` no pudo leer el encabezado (p. ej., el archivo está vacío) | Asegúrate de pasar la ruta correcta del archivo y de que el archivo no tenga cero bytes. |
| Los archivos cifrados generan una excepción | Intento de lectura sin manejar el cifrado | Usa la verificación `info.isEncrypted()` antes de cualquier procesamiento adicional, como se muestra en el código. |
| No se detectan documentos Word pre‑97 | Los formatos antiguos requieren el caso `DOC_PRE_WORD_60` | Mantén el bloque `case LoadFormat.DOC_PRE_WORD_60` para redirigirlos a la carpeta *Pre97*. |

## Preguntas frecuentes

### ¿Cómo instalo Aspose.Words para Java?

Puedes descargar Aspose.Words para Java desde el [aquí](https://releases.aspose.com/words/java/) y seguir las instrucciones de instalación proporcionadas.

### ¿Cuáles son los formatos de documento compatibles?

Aspose.Words para Java soporta varios formatos de documento, incluidos DOC, DOCX, RTF, HTML, ODT y más. Consulta la documentación oficial para obtener una lista completa.

### ¿Cómo puedo detectar documentos cifrados usando Aspose.Words para Java?

Utiliza el método `FileFormatUtil.detectFileFormat()`; la bandera `FileFormatInfo.isEncrypted()` devuelta indica el cifrado, como se muestra en esta guía.

### ¿Existen limitaciones al trabajar con formatos de documento antiguos?

Los formatos antiguos, como MS Word 6 o Word 95, pueden carecer de funciones modernas y presentar problemas de compatibilidad. Considera convertirlos a formatos más recientes cuando sea posible.

### ¿Puedo automatizar la detección del formato de documentos en mi aplicación Java?

Sí, incorpora el código proporcionado en el flujo de procesamiento de tu aplicación. Esto permite la clasificación y el manejo automáticos basados en los formatos detectados.

---

**Última actualización:** 2025-12-20  
**Probado con:** Aspose.Words para Java 24.12 (última)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}