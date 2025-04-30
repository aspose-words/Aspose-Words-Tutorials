---
"description": "Aprenda a gestionar la sustitución de fuentes sin sufijos en Aspose.Words para .NET. Siga nuestra guía paso a paso para garantizar que sus documentos se vean perfectos en todo momento."
"linktitle": "Obtener sustitución sin sufijos"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Obtener sustitución sin sufijos"
"url": "/es/net/working-with-fonts/get-substitution-without-suffixes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Obtener sustitución sin sufijos

## Introducción

Bienvenido a esta guía completa sobre cómo gestionar la sustitución de fuentes con Aspose.Words para .NET. Si alguna vez ha tenido problemas con fuentes que no se muestran correctamente en sus documentos, está en el lugar correcto. Este tutorial le guiará paso a paso para gestionar la sustitución de fuentes sin sufijos de forma eficiente.

## Prerrequisitos

Antes de sumergirse en el tutorial, asegúrese de tener lo siguiente:

- Conocimientos básicos de C#: comprender la programación en C# hará que sea más fácil seguir e implementar los pasos.
- Biblioteca Aspose.Words para .NET: Descargue e instale la biblioteca desde [enlace de descarga](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: configure un entorno de desarrollo como Visual Studio para escribir y ejecutar su código.
- Documento de muestra: Un documento de muestra (por ejemplo, `Rendering.docx`) para trabajar durante este tutorial.

## Importar espacios de nombres

Primero, necesitamos importar los espacios de nombres necesarios para acceder a las clases y métodos proporcionados por Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
using System.Collections.Generic;
```

## Paso 1: Definir el directorio del documento

Para comenzar, especifique el directorio donde se encuentra su documento. Esto le ayudará a localizar el documento en el que desea trabajar.

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Configurar el controlador de advertencia de sustitución

A continuación, necesitamos configurar un controlador de advertencias que nos notifique cada vez que se produzca una sustitución de fuente durante el procesamiento del documento. Esto es crucial para detectar y gestionar cualquier problema de fuente.

```csharp
DocumentSubstitutionWarnings substitutionWarningHandler = new DocumentSubstitutionWarnings();
Document doc = new Document(dataDir + "Rendering.docx");
doc.WarningCallback = substitutionWarningHandler;
```

## Paso 3: Agregar fuentes personalizadas

En este paso, agregaremos fuentes personalizadas para garantizar que Aspose.Words pueda localizar y usar las fuentes correctas. Esto es especialmente útil si tiene fuentes específicas almacenadas en directorios personalizados.

```csharp
List<FontSourceBase> fontSources = new List<FontSourceBase>(FontSettings.DefaultInstance.GetFontsSources());

FolderFontSource folderFontSource = new FolderFontSource("C:\\MyFonts\\", true);
fontSources.Add(folderFontSource);

FontSourceBase[] updatedFontSources = fontSources.ToArray();
FontSettings.DefaultInstance.SetFontsSources(updatedFontSources);
```

En este código:
- Recuperamos las fuentes de fuentes actuales y agregamos una nueva `FolderFontSource` apuntando a nuestro directorio de fuentes personalizadas (`C:\\MyFonts\\`).
- Luego actualizamos las fuentes de fuentes con esta nueva lista.

## Paso 4: Guardar el documento

Finalmente, guarde el documento después de aplicar la configuración de sustitución de fuentes. En este tutorial, lo guardaremos como PDF.

```csharp
doc.Save(dataDir + "WorkingWithFonts.GetSubstitutionWithoutSuffixes.pdf");
```

## Paso 5: Crear la clase de controlador de advertencias

Para gestionar las advertencias de manera efectiva, cree una clase personalizada que implemente la `IWarningCallback` Interfaz. Esta clase capturará y registrará cualquier advertencia de sustitución de fuentes.

```csharp
public class DocumentSubstitutionWarnings : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
            FontWarnings.Warning(info);
    }

    public WarningInfoCollection FontWarnings = new WarningInfoCollection();
}
```

En esta clase:
- El `Warning` El método captura advertencias relacionadas con la sustitución de fuentes.
- El `FontWarnings` La colección almacena estas advertencias para su posterior inspección o registro.

## Conclusión

Ya domina el proceso de sustitución de fuentes sin sufijos con Aspose.Words para .NET. Este conocimiento garantizará que sus documentos mantengan la apariencia deseada, independientemente de las fuentes disponibles en el sistema. Siga experimentando con diferentes configuraciones y fuentes para aprovechar al máximo el potencial de Aspose.Words.

## Preguntas frecuentes

### ¿Cómo puedo utilizar fuentes de varios directorios personalizados?

Puedes agregar varios `FolderFontSource` instancias a la `fontSources` enumerar y actualizar las fuentes de fuentes según corresponda.

### ¿Dónde puedo descargar una prueba gratuita de Aspose.Words para .NET?

Puede descargar una versión de prueba gratuita desde [Página de prueba gratuita de Aspose](https://releases.aspose.com/).

### ¿Puedo gestionar varios tipos de advertencias utilizando? `IWarningCallback`?

Sí, el `IWarningCallback` La interfaz le permite manejar varios tipos de advertencias, no solo la sustitución de fuentes.

### ¿Dónde puedo obtener soporte para Aspose.Words?

Para obtener ayuda, visite el sitio [Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8).

### ¿Es posible comprar una licencia temporal?

Sí, puede obtener una licencia temporal de la [página de licencia temporal](https://purchase.aspose.com/temporary-license/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}