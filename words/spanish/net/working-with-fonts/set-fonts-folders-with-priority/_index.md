---
title: Establecer carpetas de fuentes con prioridad
linktitle: Establecer carpetas de fuentes con prioridad
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a configurar carpetas de fuentes con prioridad en documentos de Word con Aspose.Words para .NET. Nuestra guía garantiza que sus documentos se representen perfectamente en todo momento.
weight: 10
url: /es/net/working-with-fonts/set-fonts-folders-with-priority/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Establecer carpetas de fuentes con prioridad

## Introducción

En el mundo de la manipulación de documentos, configurar carpetas de fuentes personalizadas puede marcar una gran diferencia a la hora de garantizar que sus documentos se representen perfectamente, sin importar dónde se visualicen. Hoy, analizaremos en profundidad cómo puede configurar carpetas de fuentes con prioridad en sus documentos de Word utilizando Aspose.Words para .NET. Esta guía completa lo guiará paso a paso para que el proceso sea lo más sencillo posible.

## Prerrequisitos

Antes de comenzar, asegurémonos de que tenemos todo lo que necesitamos. A continuación, se incluye una lista de verificación rápida:

-  Aspose.Words para .NET: Necesita tener instalada esta biblioteca. Si aún no la tiene, puede[Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: asegúrese de tener un entorno de desarrollo .NET en funcionamiento, como Visual Studio.
-  Directorio de documentos: asegúrese de tener un directorio para sus documentos. Para nuestros ejemplos, utilizaremos`"YOUR DOCUMENT DIRECTORY"` como marcador de posición para esta ruta.

## Importar espacios de nombres

Lo primero es lo primero: debemos importar los espacios de nombres necesarios. Estos espacios de nombres son esenciales para acceder a las clases y métodos que ofrece Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ahora, analicemos cada paso para configurar las carpetas de fuentes con prioridad.

## Paso 1: Configura tus fuentes

Para comenzar, deberá definir las fuentes de las fuentes. Aquí es donde le indica a Aspose.Words dónde buscar las fuentes. Puede especificar varias carpetas de fuentes e incluso establecer su prioridad.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

En este ejemplo, configuramos dos fuentes de fuente:
- SystemFontSource: esta es la fuente de fuente predeterminada que incluye todas las fuentes instaladas en su sistema.
-  FolderFontSource: Esta es una carpeta de fuentes personalizada ubicada en`C:\\MyFonts\\` . El`true` El parámetro especifica que esta carpeta debe escanearse recursivamente y`1` Establece su prioridad.

## Paso 2: Cargue su documento

A continuación, cargue el documento con el que desea trabajar. Asegúrese de que el documento se encuentre en el directorio especificado.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

 Esta línea de código carga un documento llamado`Rendering.docx` desde su directorio de documentos.

## Paso 3: Guarde el documento con la nueva configuración de fuente

Por último, guarde el documento. Cuando lo guarde, Aspose.Words utilizará la configuración de fuente que haya especificado.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

 Esto guarda el documento como PDF en su directorio de documentos con el nombre`WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Conclusión

¡Y ya está! Ha configurado correctamente las carpetas de fuentes con prioridad mediante Aspose.Words para .NET. Al especificar carpetas de fuentes y prioridades personalizadas, puede asegurarse de que sus documentos se representen de manera uniforme, independientemente de dónde se visualicen. Esto resulta especialmente útil en entornos en los que no se instalan fuentes específicas de manera predeterminada.

## Preguntas frecuentes

### ¿Por qué necesitaría configurar carpetas de fuentes personalizadas?
La configuración de carpetas de fuentes personalizadas garantiza que sus documentos se representen correctamente, incluso si utilizan fuentes que no están instaladas en el sistema en el que se están visualizando.

### ¿Puedo configurar varias carpetas de fuentes personalizadas?
Sí, puedes especificar varias carpetas de fuentes. Aspose.Words te permite establecer la prioridad de cada carpeta, lo que garantiza que las fuentes más importantes se encuentren primero.

### ¿Qué sucede si falta una fuente en todas las fuentes especificadas?
Si falta una fuente en todas las fuentes especificadas, Aspose.Words utilizará una fuente alternativa para garantizar que el documento aún sea legible.

### ¿Puedo cambiar la prioridad de las fuentes del sistema?
Las fuentes del sistema siempre se incluyen de forma predeterminada, pero puedes establecer su prioridad en relación con tus carpetas de fuentes personalizadas.

### ¿Es posible utilizar rutas de red para carpetas de fuentes personalizadas?
Sí, puede especificar rutas de red como carpetas de fuentes personalizadas, lo que le permite centralizar los recursos de fuentes en una ubicación de red.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
