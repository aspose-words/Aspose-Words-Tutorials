---
"description": "Aprenda a configurar carpetas de fuentes con prioridad en documentos de Word con Aspose.Words para .NET. Nuestra guía garantiza que sus documentos se visualicen perfectamente en todo momento."
"linktitle": "Establecer carpetas de fuentes con prioridad"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Establecer carpetas de fuentes con prioridad"
"url": "/es/net/working-with-fonts/set-fonts-folders-with-priority/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Establecer carpetas de fuentes con prioridad

## Introducción

En el mundo de la manipulación de documentos, configurar carpetas de fuentes personalizadas puede marcar la diferencia para garantizar que sus documentos se visualicen perfectamente, independientemente de dónde se visualicen. Hoy, profundizaremos en cómo configurar carpetas de fuentes con prioridad en sus documentos de Word usando Aspose.Words para .NET. Esta guía completa le guiará paso a paso, simplificando al máximo el proceso.

## Prerrequisitos

Antes de empezar, asegurémonos de tener todo lo necesario. Aquí tienes una lista de verificación rápida:

- Aspose.Words para .NET: Necesita tener esta biblioteca instalada. Si aún no la tiene, puede... [Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: asegúrese de tener un entorno de desarrollo .NET en funcionamiento, como Visual Studio.
- Directorio de documentos: Asegúrate de tener un directorio para tus documentos. Para nuestros ejemplos, usaremos `"YOUR DOCUMENT DIRECTORY"` como marcador de posición para esta ruta.

## Importar espacios de nombres

Primero, necesitamos importar los espacios de nombres necesarios. Estos espacios de nombres son esenciales para acceder a las clases y métodos proporcionados por Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ahora, analicemos cada paso para configurar las carpetas de fuentes con prioridad.

## Paso 1: Configura tus fuentes

Para empezar, deberá definir las fuentes. Aquí es donde le indica a Aspose.Words dónde buscar las fuentes. Puede especificar varias carpetas de fuentes e incluso establecer su prioridad.

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENT DIRECTORY";

FontSettings.DefaultInstance.SetFontsSources(new FontSourceBase[]
{
    new SystemFontSource(), 
    new FolderFontSource("C:\\MyFonts\\", true, 1)
});
```

En este ejemplo, configuramos dos fuentes:
- SystemFontSource: esta es la fuente de fuente predeterminada que incluye todas las fuentes instaladas en su sistema.
- FolderFontSource: Esta es una carpeta de fuentes personalizadas ubicada en `C:\\MyFonts\\`. El `true` El parámetro especifica que esta carpeta debe escanearse de forma recursiva y `1` Establece su prioridad.

## Paso 2: Cargue su documento

A continuación, cargue el documento con el que desea trabajar. Asegúrese de que esté ubicado en el directorio especificado.

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Esta línea de código carga un documento llamado `Rendering.docx` desde su directorio de documentos.

## Paso 3: Guarde su documento con la nueva configuración de fuente

Finalmente, guarde el documento. Al hacerlo, Aspose.Words usará la configuración de fuente que especificó.

```csharp
doc.Save(dataDir + "WorkingWithFonts.SetFontsFoldersWithPriority.pdf");
```

Esto guarda el documento como PDF en su directorio de documentos con el nombre `WorkingWithFonts.SetFontsFoldersWithPriority.pdf`.

## Conclusión

¡Listo! Has configurado correctamente las carpetas de fuentes con prioridad usando Aspose.Words para .NET. Al especificar carpetas de fuentes y prioridades personalizadas, puedes garantizar que tus documentos se visualicen de forma consistente, independientemente de dónde se visualicen. Esto es especialmente útil en entornos donde no se instalan fuentes específicas por defecto.

## Preguntas frecuentes

### ¿Por qué necesitaría configurar carpetas de fuentes personalizadas?
La configuración de carpetas de fuentes personalizadas garantiza que sus documentos se representen correctamente, incluso si utilizan fuentes que no están instaladas en el sistema en el que se están visualizando.

### ¿Puedo configurar varias carpetas de fuentes personalizadas?
Sí, puedes especificar varias carpetas de fuentes. Aspose.Words te permite establecer la prioridad de cada carpeta, garantizando que las fuentes más importantes se encuentren primero.

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