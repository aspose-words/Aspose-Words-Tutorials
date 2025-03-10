---
title: Relación de aspecto bloqueada
linktitle: Relación de aspecto bloqueada
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a bloquear la relación de aspecto de las formas en documentos de Word con Aspose.Words para .NET. Siga esta guía paso a paso para mantener la proporción de las imágenes y las formas.
weight: 10
url: /es/net/programming-with-shapes/aspect-ratio-locked/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Relación de aspecto bloqueada

## Introducción

¿Alguna vez te has preguntado cómo mantener las proporciones perfectas de las imágenes y formas en tus documentos de Word? A veces, necesitas asegurarte de que tus imágenes y formas no se distorsionen al cambiar de tamaño. Aquí es donde resulta útil bloquear la relación de aspecto. En este tutorial, exploraremos cómo establecer la relación de aspecto de las formas en documentos de Word usando Aspose.Words para .NET. Lo dividiremos en pasos fáciles de seguir, asegurándonos de que puedas aplicar estas habilidades a tus proyectos con confianza.

## Prerrequisitos

Antes de sumergirnos en el código, repasemos lo que necesitas para comenzar:

- Biblioteca Aspose.Words para .NET: debe tener instalado Aspose.Words para .NET. Si aún no lo ha hecho, puede[Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: asegúrese de tener configurado un entorno de desarrollo .NET. Visual Studio es una opción popular.
- Conocimientos básicos de C#: será útil tener cierta familiaridad con la programación en C#.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Estos espacios de nombres nos darán acceso a las clases y métodos que necesitamos para trabajar con documentos y formas de Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Paso 1: Configurar el directorio de documentos

 Antes de comenzar a manipular formas, debemos configurar un directorio donde se almacenarán nuestros documentos. Para simplificar, utilizaremos un marcador de posición`YOUR DOCUMENT DIRECTORY`Reemplace esto con la ruta real a su directorio de documentos.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Paso 2: Crear un nuevo documento

A continuación, crearemos un nuevo documento de Word con Aspose.Words. Este documento nos servirá como lienzo para agregar formas e imágenes.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Aquí, creamos una instancia de la`Document` clase y utilizar una`DocumentBuilder` para ayudarnos a construir el contenido del documento.

## Paso 3: Insertar una imagen

 Ahora, insertemos una imagen en nuestro documento. Usaremos el`InsertImage` método de la`DocumentBuilder`clase. Asegúrese de tener una imagen en el directorio especificado.

```csharp
Shape shape = builder.InsertImage(dataDir + "Transparent background logo.png");
```

 Reemplazar`dataDir + "Transparent background logo.png"` con la ruta a su archivo de imagen.

## Paso 4: Bloquear la relación de aspecto

Una vez insertada la imagen, podemos bloquear su relación de aspecto. Al bloquear la relación de aspecto, se garantiza que las proporciones de la imagen permanezcan constantes al cambiar de tamaño.

```csharp
shape.AspectRatioLocked = true;
```

 Configuración`AspectRatioLocked` a`true` garantiza que la imagen mantenga su relación de aspecto original.

## Paso 5: Guardar el documento

Por último, guardaremos el documento en el directorio especificado. Este paso escribe todos los cambios que hemos realizado en el archivo del documento.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AspectRatioLocked.docx");
```

## Conclusión

¡Felicitaciones! Aprendió a establecer la relación de aspecto de las formas en documentos de Word con Aspose.Words para .NET. Si sigue estos pasos, podrá asegurarse de que sus imágenes y formas mantengan sus proporciones, lo que hará que sus documentos tengan un aspecto profesional y refinado. Experimente con diferentes imágenes y formas para ver cómo funciona la función de bloqueo de la relación de aspecto en varios escenarios.

## Preguntas frecuentes

### ¿Puedo desbloquear la relación de aspecto después de bloquearla?
Sí, puedes desbloquear la relación de aspecto configurando`shape.AspectRatioLocked = false`.

### ¿Qué sucede si cambio el tamaño de una imagen con una relación de aspecto bloqueada?
La imagen cambiará de tamaño proporcionalmente, manteniendo su relación ancho-alto original.

### ¿Puedo aplicar esto a otras formas además de imágenes?
¡Por supuesto! La función de bloqueo de la relación de aspecto se puede aplicar a cualquier forma, incluidos rectángulos, círculos y más.

### ¿Aspose.Words para .NET es compatible con .NET Core?
Sí, Aspose.Words para .NET es compatible con .NET Framework y .NET Core.

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?
 Puede encontrar documentación completa[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
