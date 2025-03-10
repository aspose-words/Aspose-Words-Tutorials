---
title: Detectar formato de archivo de documento
linktitle: Detectar formato de archivo de documento
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a detectar formatos de archivos de documentos utilizando Aspose.Words para .NET con esta guía completa paso a paso.
weight: 10
url: /es/net/programming-with-fileformat/detect-file-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Detectar formato de archivo de documento

## Introducción

En el mundo digital actual, es fundamental gestionar distintos formatos de documentos de forma eficaz. Ya sea que trabaje con Word, PDF, HTML u otros formatos, poder detectar y procesar estos archivos correctamente puede ahorrarle mucho tiempo y esfuerzo. En este tutorial, exploraremos cómo detectar formatos de archivos de documentos con Aspose.Words para .NET. Esta guía le explicará todo lo que necesita saber, desde los requisitos previos hasta una guía detallada paso a paso.

## Prerrequisitos

Antes de sumergirnos en el código, asegurémonos de que tienes todo lo que necesitas:

-  Aspose.Words para .NET: Puedes descargarlo desde[aquí](https://releases.aspose.com/words/net/) Asegúrese de tener una licencia válida. Si no, puede obtener una[licencia temporal](https://purchase.aspose.com/temporary-license/).
- Visual Studio: cualquier versión reciente funcionará bien.
- .NET Framework: asegúrese de tener instalada la versión correcta.

## Importar espacios de nombres

Para comenzar, deberá importar los espacios de nombres necesarios en su proyecto:

```csharp
using Aspose.Words;
using Aspose.Words.FileFormats;
using Aspose.Words.FileFormats.Util;
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
```

Dividamos el ejemplo en varios pasos para que sea más fácil de seguir.

## Paso 1: Configurar directorios

Primero, necesitamos configurar directorios donde se ordenarán los archivos según su formato.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
string supportedDir = dataDir + "Supported";
string unknownDir = dataDir + "Unknown";
string encryptedDir = dataDir + "Encrypted";
string pre97Dir = dataDir + "Pre97";

// Crea los directorios si aún no existen.
if (!Directory.Exists(supportedDir))
    Directory.CreateDirectory(supportedDir);
if (!Directory.Exists(unknownDir))
    Directory.CreateDirectory(unknownDir);
if (!Directory.Exists(encryptedDir))
    Directory.CreateDirectory(encryptedDir);
if (!Directory.Exists(pre97Dir))
    Directory.CreateDirectory(pre97Dir);
```

## Paso 2: Obtener la lista de archivos

A continuación, obtendremos una lista de archivos del directorio, excluyendo cualquier documento dañado.

```csharp
IEnumerable<string> fileList = Directory.GetFiles(dataDir).Where(name => !name.EndsWith("Corrupted document.docx"));
```

## Paso 3: Detectar formatos de archivos

Ahora, iteramos a través de cada archivo y detectamos su formato usando Aspose.Words.

```csharp
foreach (string fileName in fileList)
{
    string nameOnly = Path.GetFileName(fileName);

    Console.Write(nameOnly);

    FileFormatInfo info = FileFormatUtil.DetectFileFormat(fileName);

    // Mostrar el tipo de documento
    switch (info.LoadFormat)
    {
        case LoadFormat.Doc:
            Console.WriteLine("\tMicrosoft Word 97-2003 document.");
            break;
        case LoadFormat.Dot:
            Console.WriteLine("\tMicrosoft Word 97-2003 template.");
            break;
        case LoadFormat.Docx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Document.");
            break;
        case LoadFormat.Docm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Document.");
            break;
        case LoadFormat.Dotx:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Free Template.");
            break;
        case LoadFormat.Dotm:
            Console.WriteLine("\tOffice Open XML WordprocessingML Macro-Enabled Template.");
            break;
        case LoadFormat.FlatOpc:
            Console.WriteLine("\tFlat OPC document.");
            break;
        case LoadFormat.Rtf:
            Console.WriteLine("\tRTF format.");
            break;
        case LoadFormat.WordML:
            Console.WriteLine("\tMicrosoft Word 2003 WordprocessingML format.");
            break;
        case LoadFormat.Html:
            Console.WriteLine("\tHTML format.");
            break;
        case LoadFormat.Mhtml:
            Console.WriteLine("\tMHTML (Web archive) format.");
            break;
        case LoadFormat.Odt:
            Console.WriteLine("\tOpenDocument Text.");
            break;
        case LoadFormat.Ott:
            Console.WriteLine("\tOpenDocument Text Template.");
            break;
        case LoadFormat.DocPreWord60:
            Console.WriteLine("\tMS Word 6 or Word 95 format.");
            break;
        case LoadFormat.Unknown:
            Console.WriteLine("\tUnknown format.");
            break;
    }

    if (info.IsEncrypted)
    {
        Console.WriteLine("\tAn encrypted document.");
        File.Copy(fileName, Path.Combine(encryptedDir, nameOnly), true);
    }
    else
    {
        switch (info.LoadFormat)
        {
            case LoadFormat.DocPreWord60:
                File.Copy(fileName, Path.Combine(pre97Dir, nameOnly), true);
                break;
            case LoadFormat.Unknown:
                File.Copy(fileName, Path.Combine(unknownDir, nameOnly), true);
                break;
            default:
                File.Copy(fileName, Path.Combine(supportedDir, nameOnly), true);
                break;
        }
    }
}
```

## Conclusión

Detectar formatos de archivos de documentos con Aspose.Words para .NET es un proceso sencillo. Al configurar los directorios, obtener la lista de archivos y utilizar Aspose.Words para detectar formatos de archivos, puede organizar y administrar sus documentos de manera eficiente. Este enfoque no solo ahorra tiempo, sino que también garantiza que maneje varios formatos de documentos correctamente.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca para trabajar con documentos de Word de forma programática. Permite a los desarrolladores crear, modificar y convertir documentos en varios formatos.

### ¿Puede Aspose.Words detectar documentos cifrados?
Sí, Aspose.Words puede detectar si un documento está encriptado y puede manejar dichos documentos en consecuencia.

### ¿Qué formatos puede detectar Aspose.Words?
Aspose.Words puede detectar una amplia gama de formatos, incluidos DOC, DOCX, RTF, HTML, MHTML, ODT y muchos más.

### ¿Cómo puedo obtener una licencia temporal para Aspose.Words?
 Puede obtener una licencia temporal de la[Compra de Aspose](https://purchase.aspose.com/temporary-license/) página.

### ¿Dónde puedo encontrar la documentación de Aspose.Words?
 La documentación de Aspose.Words se puede encontrar[aquí](https://reference.aspose.com/words/net/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
