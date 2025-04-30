---
"description": "Aprenda a habilitar o deshabilitar la sustitución de fuentes en documentos de Word con Aspose.Words para .NET. Asegúrese de que sus documentos se vean uniformes en todas las plataformas."
"linktitle": "Habilitar Deshabilitar Sustitución de Fuentes"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Habilitar Deshabilitar Sustitución de Fuentes"
"url": "/es/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar Deshabilitar Sustitución de Fuentes

## Introducción

¿Alguna vez te has encontrado en la situación de que las fuentes que elegiste con tanto cuidado en un documento de Word se reemplazan al visualizarlo en otro ordenador? Molesto, ¿verdad? Esto ocurre debido a la sustitución de fuentes, un proceso en el que el sistema reemplaza una fuente faltante por una disponible. ¡Pero no te preocupes! Con Aspose.Words para .NET, puedes administrar y controlar fácilmente la sustitución de fuentes. En este tutorial, te guiaremos por los pasos para activar o desactivar la sustitución de fuentes en tus documentos de Word, garantizando que tus documentos siempre se vean exactamente como quieres.

## Prerrequisitos

Antes de sumergirnos en los pasos, asegurémonos de tener todo lo que necesitas:

- Aspose.Words para .NET: Descarga la última versión [aquí](https://releases.aspose.com/words/net/).
- Visual Studio: cualquier versión compatible con .NET.
- Conocimientos básicos de C#: esto le ayudará a seguir los ejemplos de codificación.

## Importar espacios de nombres

Para empezar, asegúrese de haber importado los espacios de nombres necesarios en su proyecto. Añádalos al principio de su archivo de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ahora, dividamos el proceso en pasos simples y manejables.

## Paso 1: Configura tu proyecto

Primero, configure un nuevo proyecto en Visual Studio y agregue una referencia a la biblioteca Aspose.Words para .NET. Si aún no lo ha hecho, descárguela desde [Sitio web de Aspose](https://releases.aspose.com/words/net/).

## Paso 2: Cargue su documento

A continuación, cargue el documento con el que desea trabajar. Así es como se hace:

```csharp
// Ruta a su directorio de documentos 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Reemplazar `"YOUR DOCUMENT DIRECTORY"` Con la ruta real al directorio de tu documento. Este código carga el documento en memoria para que puedas manipularlo.

## Paso 3: Configurar los ajustes de fuente

Ahora, vamos a crear un `FontSettings` objeto para administrar la configuración de sustitución de fuentes:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Paso 4: Establecer la sustitución de fuente predeterminada

Establezca la sustitución de fuente predeterminada con una fuente de su elección. Esta fuente se usará si la fuente original no está disponible:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

En este ejemplo, utilizamos Arial como fuente predeterminada.

## Paso 5: Desactivar la sustitución de información de fuente

Para deshabilitar la sustitución de información de fuentes, que impide que el sistema reemplace las fuentes faltantes con las disponibles, utilice el siguiente código:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Paso 6: Aplicar la configuración de fuente al documento

Ahora, aplique estas configuraciones a su documento:

```csharp
doc.FontSettings = fontSettings;
```

## Paso 7: Guarde su documento

Finalmente, guarde el documento modificado. Puede guardarlo en el formato que desee. Para este tutorial, lo guardaremos como PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusión

¡Listo! Siguiendo estos pasos, puedes controlar fácilmente la sustitución de fuentes en tus documentos de Word con Aspose.Words para .NET. Esto garantiza que tus documentos mantengan su aspecto original, independientemente de dónde se visualicen.

## Preguntas frecuentes

### ¿Puedo utilizar fuentes distintas a Arial para la sustitución?

¡Por supuesto! Puedes especificar cualquier fuente disponible en tu sistema cambiando el nombre de la fuente en el... `DefaultFontName` propiedad.

### ¿Qué sucede si la fuente predeterminada especificada no está disponible?

Si la fuente predeterminada no está disponible, Aspose.Words utilizará un mecanismo de respaldo del sistema para encontrar un reemplazo apropiado.

### ¿Puedo habilitar nuevamente la sustitución de fuentes después de deshabilitarla?

Sí, puedes alternar el `Enabled` propiedad de `FontInfoSubstitution` volver a `true` Si desea habilitar nuevamente la sustitución de fuentes.

### ¿Hay alguna manera de comprobar qué fuentes se están sustituyendo?

Sí, Aspose.Words proporciona métodos para registrar y rastrear la sustitución de fuentes, lo que le permite ver qué fuentes se están reemplazando.

### ¿Puedo utilizar este método para otros formatos de documentos además de DOCX?

¡Por supuesto! Aspose.Words admite varios formatos y puedes aplicar esta configuración de fuente a cualquier formato compatible.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}