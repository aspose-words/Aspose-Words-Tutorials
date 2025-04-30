---
"description": "Descubre cómo obtener una lista de fuentes disponibles con Aspose.Words para .NET en este detallado tutorial paso a paso. Mejora tus habilidades de gestión de fuentes."
"linktitle": "Obtener lista de fuentes disponibles"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Obtener lista de fuentes disponibles"
"url": "/es/net/working-with-fonts/get-list-of-available-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Obtener lista de fuentes disponibles

## Introducción

¿Alguna vez has tenido dificultades para administrar las fuentes en tus documentos de Word? Si eres desarrollador .NET, ¡Aspose.Words para .NET está aquí para ayudarte! Esta potente biblioteca no solo te ayuda a crear y manipular documentos de Word mediante programación, sino que también ofrece amplias funciones de gestión de fuentes. En esta guía, te guiaremos paso a paso en un tutorial sobre cómo obtener una lista de fuentes disponibles con Aspose.Words para .NET. Lo dividiremos en pasos fáciles de entender para que puedas seguirlo fácilmente. ¡Comencemos y hagamos que la gestión de fuentes sea pan comido!

## Prerrequisitos

Antes de comenzar, necesitarás algunas cosas:

- Aspose.Words para .NET: Asegúrate de tener instalada la biblioteca Aspose.Words para .NET. Puedes descargarla desde [aquí](https://releases.aspose.com/words/net/).
- Visual Studio: este ejemplo utiliza Visual Studio como entorno de desarrollo.
- .NET Framework: asegúrese de tener .NET Framework instalado en su máquina.
- Directorio de documentos: una ruta de directorio donde se almacenan sus documentos.

## Importar espacios de nombres

Primero, importe los espacios de nombres necesarios en su proyecto:

```csharp
using System;
using System.Collections.Generic;
using Aspose.Words;
using Aspose.Words.Fonts;
```

## Paso 1: Inicializar la configuración de fuentes

El primer paso es inicializar la configuración de fuentes. Esto le permitirá administrar las fuentes de sus documentos.

```csharp
FontSettings fontSettings = new FontSettings();
List<FontSourceBase> fontSources = new List<FontSourceBase>(fontSettings.GetFontsSources());
```

- FontSettings: esta clase se utiliza para especificar la configuración para la sustitución de fuentes y las fuentes de fuentes.
- fontSources: Creamos una lista de fuentes existentes a partir de la configuración de fuentes actual.

## Paso 2: Definir el directorio del documento

A continuación, especifique la ruta del directorio de su documento. Aquí es donde Aspose.Words buscará las fuentes.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

- dataDir: Esta variable de cadena contiene la ruta al directorio donde se encuentran sus fuentes. Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta actual.

## Paso 3: Agregar carpeta de fuentes personalizadas

Ahora, agregue una nueva carpeta de origen para indicarle a Aspose.Words que busque fuentes en esta carpeta.

```csharp
FolderFontSource folderFontSource = new FolderFontSource(dataDir, true);
```

- FolderFontSource: Esta clase representa la fuente de una carpeta. El segundo parámetro (`true`indica si se deben buscar fuentes de forma recursiva en subcarpetas.

## Paso 4: Actualizar las fuentes

Agregue la carpeta de fuentes personalizadas a la lista de fuentes existentes y actualice la configuración de fuentes.

```csharp
fontSources.Add(folderFontSource);
FontSourceBase[] updatedFontSources = fontSources.ToArray();
```

- fontSources.Add(folderFontSource): agrega la carpeta de fuentes personalizadas a las fuentes de fuentes existentes.
- updatedFontSources: Convierte la lista de fuentes en una matriz.

## Paso 5: Recuperar y mostrar fuentes

Por último, recupere las fuentes disponibles y muestre sus detalles.

```csharp
foreach (PhysicalFontInfo fontInfo in updatedFontSources[0].GetAvailableFonts())
{
    Console.WriteLine("FontFamilyName : " + fontInfo.FontFamilyName);
    Console.WriteLine("FullFontName  : " + fontInfo.FullFontName);
    Console.WriteLine("Version  : " + fontInfo.Version);
    Console.WriteLine("FilePath : " + fontInfo.FilePath);
}
```

- GetAvailableFonts(): recupera la lista de fuentes disponibles de la primera fuente de fuente en la lista actualizada.
- fontInfo: Una instancia de `PhysicalFontInfo` Contiene detalles sobre cada fuente.

## Conclusión

¡Felicitaciones! Ha obtenido correctamente una lista de fuentes disponibles con Aspose.Words para .NET. Este tutorial le ha guiado paso a paso, desde la configuración inicial de las fuentes hasta la visualización de sus detalles. Con esta información, ahora puede administrar las fuentes en sus documentos de Word fácilmente. Recuerde que Aspose.Words para .NET es una herramienta potente que puede mejorar significativamente sus capacidades de procesamiento de documentos. Así que continúe y explore más funciones para que su proceso de desarrollo sea aún más eficiente.

## Preguntas frecuentes

### ¿Puedo utilizar Aspose.Words para .NET con otros marcos .NET?
Sí, Aspose.Words para .NET es compatible con varios marcos .NET, incluidos .NET Core y .NET 5+.

### ¿Cómo instalo Aspose.Words para .NET?
Puede instalarlo a través del Administrador de paquetes NuGet en Visual Studio buscando "Aspose.Words".

### ¿Es posible agregar varias carpetas de fuentes personalizadas?
Sí, puedes agregar varias carpetas de fuentes personalizadas creando varias `FolderFontSource` instancias y agregarlas a la lista de fuentes.

### ¿Puedo recuperar detalles de fuente de una fuente de fuente específica?
Sí, puede recuperar detalles de fuentes de cualquier fuente especificando el índice de la fuente de fuentes en el `updatedFontSources` formación.

### ¿Aspose.Words para .NET admite la sustitución de fuentes?
Sí, admite la sustitución de fuentes para garantizar que el texto se represente correctamente incluso si la fuente original no está disponible.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}