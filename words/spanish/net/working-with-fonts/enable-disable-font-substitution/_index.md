---
title: Habilitar Deshabilitar Sustitución de fuentes
linktitle: Habilitar Deshabilitar Sustitución de fuentes
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a habilitar o deshabilitar la sustitución de fuentes en documentos de Word con Aspose.Words para .NET. Asegúrese de que sus documentos tengan un aspecto uniforme en todas las plataformas.
weight: 10
url: /es/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Habilitar Deshabilitar Sustitución de fuentes

## Introducción

¿Alguna vez te has encontrado en una situación en la que las fuentes que elegiste meticulosamente en un documento de Word se reemplazan cuando se visualiza en otra computadora? Molesto, ¿verdad? Esto sucede debido a la sustitución de fuentes, un proceso en el que el sistema reemplaza una fuente faltante por una disponible. ¡Pero no te preocupes! Con Aspose.Words para .NET, puedes administrar y controlar fácilmente la sustitución de fuentes. En este tutorial, te guiaremos por los pasos para habilitar o deshabilitar la sustitución de fuentes en tus documentos de Word, asegurándote de que tus documentos siempre se vean como quieres.

## Prerrequisitos

Antes de sumergirnos en los pasos, asegurémonos de que tienes todo lo que necesitas:

-  Aspose.Words para .NET: descargue la última versión[aquí](https://releases.aspose.com/words/net/).
- Visual Studio: cualquier versión que admita .NET.
- Conocimientos básicos de C#: esto le ayudará a seguir los ejemplos de codificación.

## Importar espacios de nombres

Para comenzar, asegúrese de haber importado los espacios de nombres necesarios en su proyecto. Añádalos en la parte superior de su archivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ahora, dividamos el proceso en pasos simples y manejables.

## Paso 1: Configura tu proyecto

En primer lugar, configure un nuevo proyecto en Visual Studio y agregue una referencia a la biblioteca Aspose.Words para .NET. Si aún no lo ha hecho, descárguela desde[Sitio web de Aspose](https://releases.aspose.com/words/net/).

## Paso 2: Cargue su documento

A continuación, cargue el documento con el que desea trabajar. A continuación, le indicamos cómo hacerlo:

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta actual al directorio de su documento. Este código carga el documento en la memoria para que pueda manipularlo.

## Paso 3: Configurar los ajustes de fuente

 Ahora, vamos a crear un`FontSettings` objeto para administrar la configuración de sustitución de fuentes:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Paso 4: Establecer la sustitución de fuente predeterminada

Establezca la sustitución de fuente predeterminada en una fuente de su elección. Esta fuente se utilizará si la fuente original no está disponible:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

En este ejemplo, utilizamos Arial como fuente predeterminada.

## Paso 5: Desactivar la sustitución de información de fuente

Para deshabilitar la sustitución de información de fuente, que impide que el sistema reemplace las fuentes faltantes por las disponibles, utilice el siguiente código:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Paso 6: Aplicar la configuración de fuentes al documento

Ahora, aplique estas configuraciones a su documento:

```csharp
doc.FontSettings = fontSettings;
```

## Paso 7: Guarde su documento

Por último, guarda el documento modificado. Puedes guardarlo en el formato que desees. Para este tutorial, lo guardaremos como PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusión

¡Y ya está! Siguiendo estos pasos, podrá controlar fácilmente la sustitución de fuentes en sus documentos de Word mediante Aspose.Words para .NET. Esto garantiza que sus documentos mantengan el aspecto deseado, sin importar dónde se visualicen.

## Preguntas frecuentes

### ¿Puedo utilizar fuentes distintas a Arial para la sustitución?

 ¡Por supuesto! Puede especificar cualquier fuente disponible en su sistema cambiando el nombre de la fuente en el`DefaultFontName` propiedad.

### ¿Qué sucede si la fuente predeterminada especificada no está disponible?

Si la fuente predeterminada no está disponible, Aspose.Words utilizará un mecanismo de respaldo del sistema para encontrar un reemplazo apropiado.

### ¿Puedo volver a habilitar la sustitución de fuentes después de deshabilitarla?

 Sí, puedes alternar el`Enabled` propiedad de`FontInfoSubstitution` volver a`true` Si desea habilitar nuevamente la sustitución de fuentes.

### ¿Hay alguna manera de comprobar qué fuentes se están sustituyendo?

Sí, Aspose.Words proporciona métodos para registrar y rastrear la sustitución de fuentes, lo que le permite ver qué fuentes se están reemplazando.

### ¿Puedo utilizar este método para otros formatos de documentos además de DOCX?

¡Por supuesto! Aspose.Words admite varios formatos y puedes aplicar estas configuraciones de fuente a cualquier formato compatible.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
