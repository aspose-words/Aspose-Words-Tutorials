---
title: Leer las propiedades de Active XControl desde un archivo de Word
linktitle: Leer las propiedades de Active XControl desde un archivo de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a leer las propiedades de los controles ActiveX de los archivos de Word con Aspose.Words para .NET en una guía paso a paso. Mejore sus habilidades de automatización de documentos.
weight: 10
url: /es/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Leer las propiedades de Active XControl desde un archivo de Word

## Introducción

En la era digital actual, la automatización es clave para mejorar la productividad. Si trabaja con documentos de Word que contienen controles ActiveX, es posible que necesite leer sus propiedades para diversos fines. Los controles ActiveX, como las casillas de verificación y los botones, pueden contener datos importantes. Con Aspose.Words para .NET, puede extraer y manipular estos datos de manera eficiente mediante programación.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Biblioteca Aspose.Words para .NET: puede descargarla desde[aquí](https://releases.aspose.com/words/net/).
2. Visual Studio o cualquier IDE de C#: para escribir y ejecutar su código.
3. Un documento de Word con controles ActiveX: por ejemplo, "Controles ActiveX.docx".
4. Conocimientos básicos de C#: Es necesario estar familiarizado con la programación en C# para seguir el curso.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios para trabajar con Aspose.Words para .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Paso 1: Cargue el documento de Word

Para comenzar, deberá cargar el documento de Word que contiene los controles ActiveX.

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Paso 2: Inicializar una cadena para almacenar propiedades

A continuación, inicialice una cadena vacía para almacenar las propiedades de los controles ActiveX.

```csharp
string properties = "";
```

## Paso 3: Iterar a través de las formas en el documento

Necesitamos iterar a través de todas las formas del documento para encontrar los controles ActiveX.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Procesar el control ActiveX
    }
}
```

## Paso 4: Extraer propiedades de los controles ActiveX

Dentro del bucle, verifique si el control es un Forms2OleControl. Si lo es, conviértalo en un método y extraiga las propiedades.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Paso 5: Contar el total de controles ActiveX

Después de iterar por todas las formas, cuente la cantidad total de controles ActiveX encontrados.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Paso 6: Mostrar las propiedades

Por último, imprima las propiedades extraídas en la consola.

```csharp
Console.WriteLine("\n" + properties);
```

## Conclusión

¡Y ya está! Aprendió a leer las propiedades de un control ActiveX desde un documento de Word con Aspose.Words para .NET. Este tutorial abarcó la carga de un documento, la iteración de formas y la extracción de propiedades de los controles ActiveX. Si sigue estos pasos, podrá automatizar la extracción de datos importantes de sus documentos de Word, lo que mejorará la eficiencia de su flujo de trabajo.

## Preguntas frecuentes

### ¿Qué son los controles ActiveX en los documentos de Word?
Los controles ActiveX son objetos interactivos incrustados en documentos de Word, como casillas de verificación, botones y campos de texto, que se utilizan para crear formularios y automatizar tareas.

### ¿Puedo modificar las propiedades de los controles ActiveX usando Aspose.Words para .NET?
Sí, Aspose.Words para .NET le permite modificar las propiedades de los controles ActiveX mediante programación.

### ¿Aspose.Words para .NET es de uso gratuito?
 Aspose.Words para .NET ofrece una versión de prueba gratuita, pero deberá comprar una licencia para continuar usándola. Puede obtener una versión de prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Puedo usar Aspose.Words para .NET con otros lenguajes .NET además de C#?
Sí, Aspose.Words para .NET se puede utilizar con cualquier lenguaje .NET, incluidos VB.NET y F#.

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?
 Puede encontrar documentación detallada[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
