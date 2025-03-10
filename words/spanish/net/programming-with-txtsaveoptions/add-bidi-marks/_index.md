---
title: Agregar marcas bidireccionales en un documento de Word
linktitle: Agregar marcas bidireccionales en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar marcas bidireccionales (Bidi) en documentos de Word usando Aspose.Words para .NET con esta guía. Asegúrese de que la dirección del texto sea la adecuada para contenido en varios idiomas.
weight: 10
url: /es/net/programming-with-txtsaveoptions/add-bidi-marks/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar marcas bidireccionales en un documento de Word

## Introducción

En el mundo del procesamiento de documentos, el texto bidireccional (Bidi) puede resultar a menudo un poco complicado de gestionar. Esto es especialmente cierto cuando se trabaja con idiomas que tienen diferentes direcciones de texto, como el árabe o el hebreo. Afortunadamente, Aspose.Words para .NET facilita la gestión de estos escenarios. En este tutorial, explicaremos cómo agregar marcas Bidi a un documento de Word utilizando Aspose.Words para .NET.

## Prerrequisitos

Antes de sumergirnos en el código, asegúrese de tener lo siguiente:

1. Aspose.Words para .NET: Necesita tener instalado Aspose.Words para .NET. Puede descargarlo desde el sitio web[Página de descargas de Aspose](https://releases.aspose.com/words/net/).
2. .NET Framework o .NET Core: asegúrese de tener un entorno .NET compatible configurado para ejecutar los ejemplos.
3. Conocimientos básicos de C#: Familiaridad con el lenguaje de programación C# y operaciones básicas en .NET.

## Importar espacios de nombres

Para comenzar, debe importar los espacios de nombres necesarios. A continuación, le indicamos cómo incluirlos en su proyecto:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Vamos a desglosar el proceso de agregar marcas Bidi en un documento de Word en pasos claros. Cada paso lo guiará a través del código y su propósito.

## Paso 1: Configura tu documento

 Comience creando una nueva instancia de la`Document` clase y una`DocumentBuilder` para agregar contenido al documento.

```csharp
// Ruta a su directorio de documentos
string dataDir = "YOUR DOCUMENTS DIRECTORY";

// Crea el documento y añade contenido
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 En este paso, inicializa un nuevo documento de Word y configura un`DocumentBuilder` para facilitar la inserción de contenidos.

## Paso 2: Agrega contenido a tu documento

A continuación, agregue texto a su documento. Aquí, agregaremos texto en diferentes idiomas para ilustrar el manejo de texto bidireccional.

```csharp
builder.Writeln("Hello world!");
builder.ParagraphFormat.Bidi = true;
builder.Writeln("שלום עולם!");
builder.Writeln("مرحبا بالعالم!");
```

Aquí, primero agregamos una frase estándar en inglés. Luego, habilitamos el formato de texto bidireccional para el texto posterior, que está escrito en hebreo y árabe. Esto demuestra cómo incorporar texto bidireccional.

## Paso 3: Configurar las opciones de guardado para las marcas bidireccionales

 Para garantizar que las marcas Bidi se guarden correctamente en el documento, es necesario configurar el`TxtSaveOptions` y habilitar el`AddBidiMarks` opción.

```csharp
// Añadir marcas Bidi
TxtSaveOptions saveOptions = new TxtSaveOptions { AddBidiMarks = true };
doc.Save(dataDir + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
```

 En este paso, creamos una instancia de`TxtSaveOptions` y establecer el`AddBidiMarks`propiedad a`true`Esto garantiza que las marcas Bidi se incluyan al guardar el documento como un archivo de texto.

## Conclusión

Agregar marcas Bidi a sus documentos de Word puede ser un paso crucial cuando trabaja con contenido multilingüe que incluye idiomas con diferentes direcciones de texto. Con Aspose.Words para .NET, este proceso es sencillo y eficiente. Si sigue los pasos descritos anteriormente, puede asegurarse de que sus documentos representen correctamente el texto Bidi, lo que mejora la legibilidad y la precisión.

## Preguntas frecuentes

### ¿Qué son las marcas Bidi y por qué son importantes?
Las marcas bidireccionales son caracteres especiales que se utilizan para controlar la dirección del texto en los documentos. Son esenciales para la correcta visualización de los idiomas que se leen de derecha a izquierda, como el árabe y el hebreo.

### ¿Puedo usar Aspose.Words para .NET para manejar otros tipos de problemas de dirección de texto?
Sí, Aspose.Words para .NET proporciona soporte integral para diversas necesidades de formato y dirección de texto, incluidos idiomas de derecha a izquierda y de izquierda a derecha.

### ¿Es posible aplicar el formato Bidi solo a partes específicas de un documento?
Sí, puede aplicar el formato Bidi a párrafos o secciones específicos de su documento según sea necesario.

### ¿En qué formatos puedo guardar el documento con marcas Bidi?
En el ejemplo proporcionado, el documento se guarda como un archivo de texto. Sin embargo, Aspose.Words también permite guardar documentos en varios formatos y, al mismo tiempo, conservar las marcas bidireccionales.

### ¿Dónde puedo encontrar más información sobre Aspose.Words para .NET?
 Puede explorar más sobre Aspose.Words para .NET a través de[Documentación de Aspose](https://reference.aspose.com/words/net/) y acceder a la[Foro de soporte](https://forum.aspose.com/c/words/8) para obtener ayuda adicional.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
