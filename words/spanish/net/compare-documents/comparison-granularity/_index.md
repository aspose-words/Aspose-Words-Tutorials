---
title: Granularidad de comparación en un documento de Word
linktitle: Granularidad de comparación en un documento de Word
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda la función Comparar granularidad en documentos de Word de Aspose.Words para .NET que permite comparar documentos carácter por carácter e informar los cambios realizados.
weight: 10
url: /es/net/compare-documents/comparison-granularity/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Granularidad de comparación en un documento de Word

A continuación se muestra una guía paso a paso para explicar el código fuente de C# a continuación, que utiliza la función Comparar granularidad en documentos de Word de Aspose.Words para .NET.

## Paso 1: Introducción

La función Comparar granularidad de Aspose.Words para .NET le permite comparar documentos a nivel de caracteres. Esto significa que se comparará cada carácter y se informarán los cambios en consecuencia.

## Paso 2: Configuración del entorno

Antes de comenzar, debe configurar su entorno de desarrollo para trabajar con Aspose.Words para .NET. Asegúrese de tener instalada la biblioteca Aspose.Words y de tener un proyecto C# adecuado para integrar el código.

## Paso 3: Agregar los ensambles requeridos

Para utilizar la función Comparar granularidad de Aspose.Words para .NET, debe agregar los ensambles necesarios a su proyecto. Asegúrese de tener las referencias adecuadas a Aspose.Words en su proyecto.

```csharp
using Aspose.Words;
using Aspose.Words.DocumentBuilder;
```

## Paso 4: Creación de documentos

En este paso, crearemos dos documentos utilizando la clase DocumentBuilder. Estos documentos se utilizarán para la comparación.

```csharp
// Crear documento A.
DocumentBuilder builderA = new DocumentBuilder(new Document());
builderA.Writeln("This is a simple A word.");

// Crear documento B.
DocumentBuilder builderB = new DocumentBuilder(new Document());
builderB.Writeln("This is simple B words.");
```

## Paso 5: Configurar las opciones de comparación

En este paso, configuraremos las opciones de comparación para especificar la granularidad de la comparación. Aquí utilizaremos la granularidad a nivel de caracteres.

```csharp
CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };
```

## Paso 6: Comparación de documentos

Ahora comparemos los documentos utilizando el método Compare de la clase Document. Los cambios se guardarán en el documento A.

```csharp
builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);
```

 El`Compare`El método compara el documento A con el documento B y guarda los cambios en el documento A. Puede especificar el nombre del autor y la fecha de comparación como referencia.

## Conclusión

En este artículo, exploramos la función Comparar granularidad de Aspose.Words para .NET. Esta función le permite comparar documentos a nivel de caracteres e informar cambios. Puede utilizar este conocimiento para realizar comparaciones detalladas de documentos en sus proyectos.

### Código fuente de muestra para granularidad de comparación con Aspose.Words para .NET

```csharp
            
DocumentBuilder builderA = new DocumentBuilder(new Document());
DocumentBuilder builderB = new DocumentBuilder(new Document());

builderA.Writeln("This is A simple word");
builderB.Writeln("This is B simple words");

CompareOptions compareOptions = new CompareOptions { Granularity = Granularity.CharLevel };

builderA.Document.Compare(builderB.Document, "author", DateTime.Now, compareOptions);            
        
```

## Conclusión

En este tutorial, exploramos la función de granularidad de comparación de Aspose.Words para .NET. Esta función le permite especificar el nivel de detalle al comparar documentos. Al elegir diferentes niveles de granularidad, puede realizar comparaciones detalladas a nivel de caracteres, palabras o bloques, según sus requisitos específicos. Aspose.Words para .NET proporciona una capacidad de comparación de documentos flexible y potente, lo que facilita la identificación de diferencias en documentos con distintos niveles de granularidad.

### Preguntas frecuentes

#### P: ¿Cuál es el propósito de utilizar la granularidad de comparación en Aspose.Words para .NET?

A: La granularidad de comparación en Aspose.Words para .NET le permite especificar el nivel de detalle al comparar documentos. Con esta función, puede comparar documentos en diferentes niveles, como nivel de caracteres, nivel de palabras o incluso nivel de bloques. Cada nivel de granularidad proporciona un nivel de detalle diferente en los resultados de la comparación.

#### P: ¿Cómo uso la granularidad de comparación en Aspose.Words para .NET?

R: Para utilizar la granularidad de comparación en Aspose.Words para .NET, siga estos pasos:
1. Configure su entorno de desarrollo con la biblioteca Aspose.Words.
2. Agregue los ensamblajes necesarios a su proyecto haciendo referencia a Aspose.Words.
3.  Crea los documentos que quieras comparar utilizando el`DocumentBuilder` clase.
4.  Configure las opciones de comparación creando una`CompareOptions` objeto y configuración del`Granularity` propiedad al nivel deseado (por ejemplo,`Granularity.CharLevel` para comparación a nivel de personaje).
5.  Utilice el`Compare`método en un documento, pasando el otro documento y el`CompareOptions` objeto como parámetros. Este método comparará los documentos según la granularidad especificada y guardará los cambios en el primer documento.

#### P: ¿Cuáles son los niveles de granularidad de comparación disponibles en Aspose.Words para .NET?

R: Aspose.Words para .NET proporciona tres niveles de granularidad de comparación:
- `Granularity.CharLevel`:Compara documentos a nivel de carácter.
- `Granularity.WordLevel`:Compara documentos a nivel de palabra.
- `Granularity.BlockLevel`:Compara documentos a nivel de bloque.

#### P: ¿Cómo puedo interpretar los resultados de la comparación con granularidad a nivel de carácter?

R: Con la granularidad a nivel de carácter, se analiza cada carácter de los documentos comparados para detectar diferencias. Los resultados de la comparación mostrarán cambios a nivel de carácter individual, incluidas adiciones, eliminaciones y modificaciones.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
