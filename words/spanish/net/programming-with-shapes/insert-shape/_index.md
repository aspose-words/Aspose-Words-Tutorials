---
"description": "Aprenda a insertar y manipular formas en documentos de Word usando Aspose.Words para .NET con nuestra guía paso a paso."
"linktitle": "Insertar forma"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Insertar forma"
"url": "/es/net/programming-with-shapes/insert-shape/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma

## Introducción

Al crear documentos de Word visualmente atractivos y bien estructurados, las formas son fundamentales. Ya sea que añada flechas, cuadros o incluso formas personalizadas complejas, la posibilidad de manipular estos elementos mediante programación ofrece una flexibilidad inigualable. En este tutorial, exploraremos cómo insertar y manipular formas en documentos de Word con Aspose.Words para .NET.

## Prerrequisitos

Antes de sumergirse en el tutorial, asegúrese de tener los siguientes requisitos previos:

1. Aspose.Words para .NET: Descargue e instale la última versión desde [Página de lanzamiento de Aspose](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: un entorno de desarrollo .NET adecuado, como Visual Studio.
3. Conocimientos básicos de C#: Familiaridad con el lenguaje de programación C# y conceptos básicos.

## Importar espacios de nombres

Para comenzar, deberá importar los espacios de nombres necesarios en su proyecto de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Paso 1: Configura tu proyecto

Antes de poder comenzar a insertar formas, debe configurar su proyecto y agregar la biblioteca Aspose.Words para .NET.

1. Crear un nuevo proyecto: abra Visual Studio y cree un nuevo proyecto de aplicación de consola C#.
2. Agregue Aspose.Words para .NET: instale la biblioteca Aspose.Words para .NET a través del Administrador de paquetes NuGet.

```bash
Install-Package Aspose.Words
```

## Paso 2: Inicializar el documento

Primero, necesitarás inicializar un nuevo documento y un generador de documentos, que te ayudará a construir el documento.

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Inicializar un nuevo documento
Document doc = new Document();

// Inicializar un DocumentBuilder para ayudar a construir el documento
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Insertar una forma

Ahora, insertemos una forma en el documento. Empezaremos añadiendo un cuadro de texto simple.

```csharp
// Insertar una forma de cuadro de texto en el documento
Shape shape = builder.InsertShape(ShapeType.TextBox, RelativeHorizontalPosition.Page, 100, RelativeVerticalPosition.Page, 100, 50, 50, WrapType.None);

// Girar la forma
shape.Rotation = 30.0;
```

En este ejemplo, insertamos un cuadro de texto en la posición (100, 100) con un ancho y una altura de 50 unidades cada uno. También giramos la forma 30 grados.

## Paso 4: Agrega otra forma

Agreguemos otra forma al documento, esta vez sin especificar la posición.

```csharp
// Agregar otra forma de cuadro de texto
Shape secondShape = builder.InsertShape(ShapeType.TextBox, 50, 50);

// Girar la forma
secondShape.Rotation = 30.0;
```

Este fragmento de código inserta otro cuadro de texto con las mismas dimensiones y rotación que el primero, pero sin especificar su posición.

## Paso 5: Guardar el documento

Después de agregar las formas, el último paso es guardar el documento. Usaremos el `OoxmlSaveOptions` para especificar el formato de guardado.

```csharp
// Definir opciones de guardado con cumplimiento
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};

// Guardar el documento
doc.Save(dataDir + "WorkingWithShapes.InsertShape.docx", saveOptions);
```

## Conclusión

¡Listo! Has insertado y manipulado formas correctamente en un documento de Word con Aspose.Words para .NET. Este tutorial cubrió los conceptos básicos, pero Aspose.Words ofrece muchas más funciones avanzadas para trabajar con formas, como estilos personalizados, conectores y formas de grupo.

Para obtener información más detallada, visite el [Documentación de Aspose.Words para .NET](https://reference.aspose.com/words/net/).

## Preguntas frecuentes

### ¿Cómo inserto diferentes tipos de formas?
Puedes cambiar el `ShapeType` en el `InsertShape` Método para insertar diferentes tipos de formas, como círculos, rectángulos y flechas.

### ¿Puedo agregar texto dentro de las formas?
Sí, puedes utilizar el `builder.Write` Método para agregar texto dentro de las formas después de insertarlas.

### ¿Es posible darle estilo a las formas?
Sí, puedes darle estilo a las formas configurando propiedades como `FillColor`, `StrokeColor`, y `StrokeWeight`.

### ¿Cómo posiciono las formas en relación con otros elementos?
Utilice el `RelativeHorizontalPosition` y `RelativeVerticalPosition` Propiedades para posicionar formas en relación con otros elementos del documento.

### ¿Puedo agrupar varias formas juntas?
Sí, Aspose.Words para .NET le permite agrupar formas utilizando el `GroupShape` clase.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}