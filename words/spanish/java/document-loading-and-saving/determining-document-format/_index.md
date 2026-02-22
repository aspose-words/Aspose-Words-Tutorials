---
date: 2026-02-22
description: Aprende a detectar el formato de documentos en Java con Aspose.Words
  y mover archivos automáticamente según el formato. Identifica DOC, DOCX y más.
linktitle: Determining Document Format
second_title: Aspose.Words Java Document Processing API
title: detectar formato de documento Java usando Aspose.Words para Java
url: /es/java/document-loading-and-saving/determining-document-format/
weight: 25
---

.{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# detectar formato de documento java usando Aspose.Words for Java

Cuando necesitas **detect document format java** en un lote de archivos, la capacidad de ordenarlos automáticamente en las carpetas correctas puede ahorrar horas de trabajo manual. En este tutorial te mostraremos cómo Aspose.Words for Java facilita la identificación de Word, RTF, HTML, ODT y muchos otros formatos, y luego **move files by format** en directorios organizados.

## Respuestas rápidas
- **What does “detect document format java” mean?** Es el proceso de identificar programáticamente el formato de procesamiento de texto de un archivo (DOC, DOCX, RTF, etc.) usando código Java.  
- **Which library provides this capability?** Aspose.Words for Java ofrece la API `FileFormatUtil.detectFileFormat`.  
- **Can the utility also handle encrypted files?** Sí – la bandera `FileFormatInfo.isEncrypted()` indica si un documento está protegido con contraseña.  
- **Do I need a license for production use?** Se requiere una licencia comercial de Aspose.Words para implementaciones que no sean de evaluación.  
- **Is it possible to move files automatically after detection?** Absolutamente – combina el resultado de la detección con `FileUtils.copyFile` para ordenar los archivos en carpetas personalizadas.

## ¿Qué es detect document format java?
`detect document format java` se refiere a usar código Java para inspeccionar el encabezado binario de un archivo y determinar a qué formato de procesamiento de texto pertenece (p. ej., DOC, DOCX, ODT). Aspose.Words lee el archivo sin cargar completamente el documento, lo que hace que la operación sea rápida y eficiente en memoria.

## ¿Por qué mover archivos por formato?
Organizar documentos por su formato nativo simplifica el procesamiento posterior:

- **Batch conversions** se vuelven sencillas cuando todos los archivos DOCX están en una carpeta.  
- **Legacy support**: puedes aislar los archivos Word pre‑97 para un manejo especial.  
- **Security**: los documentos cifrados pueden ser puestos en cuarentena automáticamente.  

## Requisitos previos

Antes de comenzar, asegúrate de tener:

- [Aspose.Words for Java](https://releases.aspose.com/words/java/) (descarga la última versión)  
- Java Development Kit (JDK) 8 o superior instalado  
- Familiaridad básica con Java I/O y streams  

## Paso 1: Configurar directorios para cada formato

Primero creamos una estructura de carpetas limpia donde se moverán los archivos detectados. Esto mantiene el flujo de trabajo ordenado y facilita agregar nuevas categorías de formato más adelante.

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

> **Pro tip:** Usa rutas absolutas o configura el directorio base mediante un archivo de propiedades para evitar codificar rutas de forma rígida en el código de producción.

## Paso 2: Detectar el formato del documento y mover los archivos

El núcleo de **detect document format java** se encuentra en el bucle a continuación. Escanea cada archivo, determina su tipo y lo copia a la carpeta correspondiente.

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

El bloque `switch` puede ampliarse para cubrir todos los formatos que te interesen. Cada caso imprime un mensaje amigable y luego mueve el archivo a la carpeta correspondiente.

## Código fuente completo para detectar formato de documento java

A continuación se muestra el ejemplo completo, listo para ejecutar, que combina la configuración de directorios y la lógica de detección. Cópialo en una clase Java, ajusta la ruta base y ejecútalo contra una carpeta de documentos mixtos.

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

## Problemas comunes y solución de problemas

| Issue | Why it happens | How to fix |
|-------|----------------|------------|
| **`FileFormatUtil.detectFileFormat` returns `UNKNOWN`** | El archivo está corrupto o utiliza un formato que no es Word. | Verifica la extensión del archivo, o agrega una alternativa para moverlo a la carpeta *Unknown* (ya incluida en el ejemplo). |
| **Encrypted files throw an exception** | La API intenta leer el contenido antes de comprobar el cifrado. | Siempre llama a `info.isEncrypted()` antes de cualquier otra operación sobre el documento. |
| **Directory creation fails on Linux** | Permisos insuficientes o falta la carpeta padre. | Asegúrate de que el proceso Java tenga permisos de escritura y de que la ruta base exista. |

## Preguntas frecuentes

**Q: ¿Cómo instalo Aspose.Words for Java?**  
A: Puedes descargar Aspose.Words for Java desde el [aquí](https://releases.aspose.com/words/java/) y seguir las instrucciones de instalación proporcionadas.

**Q: ¿Qué formatos de documento son compatibles para la detección?**  
A: Aspose.Words puede detectar DOC, DOCX, DOT, DOTX, DOCM, DOTM, RTF, HTML, MHTML, ODT, OTT, FLAT_OPC, WORD_ML y formatos anteriores a 97, entre otros.

**Q: ¿Puede este código manejar documentos protegidos con contraseña?**  
A: Sí. La bandera `FileFormatInfo.isEncrypted()` identifica los archivos cifrados, lo que permite moverlos a una carpeta segura sin abrirlos.

**Q: ¿Hay impacto en el rendimiento al escanear carpetas grandes?**  
A: La detección solo lee el encabezado del archivo, por lo que incluso miles de archivos se procesan rápidamente. Para lotes muy grandes, considera usar streams paralelos.

**Q: ¿Cómo puedo extender el script para convertir formatos no compatibles?**  
A: Después de la detección, puedes llamar a `Document.save` con el formato de salida deseado para cualquier tipo de origen compatible.

## Conclusión

Al usar **detect document format java** con Aspose.Words, obtienes una forma fiable de ordenar, poner en cuarentena o convertir automáticamente archivos relacionados con Word. El código de ejemplo muestra cómo crear una jerarquía de carpetas limpia, identificar el formato de cada archivo y moverlo en consecuencia, ahorrándote tiempo y reduciendo errores manuales.

---

**Last Updated:** 2026-02-22  
**Tested With:** Aspose.Words for Java 24.12 (latest)  
**Author:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}