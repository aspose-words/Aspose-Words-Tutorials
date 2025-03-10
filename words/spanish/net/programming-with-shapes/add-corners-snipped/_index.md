---
title: Agregar esquinas recortadas
linktitle: Agregar esquinas recortadas
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar una forma de esquinas recortadas a sus documentos de Word con Aspose.Words para .NET. Esta guía paso a paso le garantiza que podrá mejorar sus documentos fácilmente.
weight: 10
url: /es/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar esquinas recortadas

## Introducción

Agregar formas personalizadas a sus documentos de Word puede ser una forma divertida y visualmente atractiva de resaltar información importante o agregar un poco de estilo a su contenido. En este tutorial, veremos cómo puede insertar formas "Corners Snipped" en sus documentos de Word usando Aspose.Words para .NET. Esta guía lo guiará por cada paso, asegurándose de que pueda agregar estas formas sin esfuerzo y personalizar sus documentos como un profesional.

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas para comenzar:

1.  Aspose.Words para .NET: si aún no lo ha hecho, descargue la última versión desde[Página de lanzamiento de Aspose](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: configure su entorno de desarrollo. Visual Studio es una opción popular, pero puede utilizar cualquier IDE que admita .NET.
3.  Licencia: Si solo estás experimentando, puedes usar una[prueba gratis](https://releases.aspose.com/) o conseguir uno[licencia temporal](https://purchase.aspose.com/temporary-license/) para desbloquear la funcionalidad completa.
4. Comprensión básica de C#: la familiaridad con la programación en C# le ayudará a seguir los ejemplos.

## Importar espacios de nombres

Antes de que podamos comenzar a trabajar con Aspose.Words para .NET, debemos importar los espacios de nombres necesarios. Añádalos en la parte superior de su archivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ahora, desglosemos el proceso de agregar una forma con "Esquinas recortadas" en varios pasos. Siga estos pasos atentamente para asegurarse de que todo funcione sin problemas.

## Paso 1: Inicializar el documento y DocumentBuilder

 Lo primero que debemos hacer es crear un nuevo documento e inicializar un`DocumentBuilder` objeto. Este constructor nos ayudará a agregar contenido a nuestro documento.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 En este paso, hemos configurado nuestro documento y generador. Piense en el`DocumentBuilder` como su lápiz digital, listo para escribir y dibujar en su documento de Word.

## Paso 2: Insertar la forma recortada en las esquinas

 A continuación, utilizaremos el`DocumentBuilder` para insertar una forma con esquinas recortadas. Este tipo de forma está predefinido en Aspose.Words y se puede insertar fácilmente con una sola línea de código.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Aquí, especificamos el tipo de forma y sus dimensiones (50 x 50). Imagina que estás colocando una pequeña pegatina con una esquina perfectamente recortada en tu documento. 

## Paso 3: Definir opciones de guardado con cumplimiento

Antes de guardar nuestro documento, debemos definir las opciones de guardado para garantizar que nuestro documento cumpla con estándares específicos. Usaremos el`OoxmlSaveOptions` clase para esto.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Estas opciones de guardado garantizan que nuestro documento cumpla con el estándar ISO/IEC 29500:2008, lo cual es crucial para la compatibilidad y la longevidad del documento.

## Paso 4: Guardar el documento

Finalmente, guardamos nuestro documento en el directorio especificado utilizando las opciones de guardado que definimos anteriormente.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

Y así de fácil, su documento ahora contiene una forma personalizada "Esquinas recortadas", guardada con las opciones de cumplimiento necesarias.

## Conclusión

¡Y listo! Agregar formas personalizadas a sus documentos de Word con Aspose.Words para .NET es sencillo y puede mejorar enormemente el atractivo visual de sus documentos. Si sigue estos pasos, podrá insertar fácilmente una forma con "Esquinas recortadas" y asegurarse de que su documento cumpla con los estándares requeridos. ¡Que disfrute codificando!

## Preguntas frecuentes

### ¿Puedo personalizar el tamaño de la forma "Esquinas recortadas"?
Sí, puedes ajustar el tamaño cambiando las dimensiones en el`InsertShape` método.

### ¿Es posible agregar otros tipos de formas?
 ¡Por supuesto! Aspose.Words admite varias formas. Solo cambia el`ShapeType` a la forma deseada.

### ¿Necesito una licencia para utilizar Aspose.Words?
Si bien puede utilizar una prueba gratuita o una licencia temporal, se requiere una licencia completa para un uso sin restricciones.

### ¿Cómo puedo darle más estilo a las formas?
Puede utilizar propiedades y métodos adicionales proporcionados por Aspose.Words para personalizar la apariencia y el comportamiento de las formas.

### ¿Aspose.Words es compatible con otros formatos?
Sí, Aspose.Words admite múltiples formatos de documentos, incluidos DOCX, PDF, HTML y más.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
