---
title: Comprobar el efecto de texto de DrawingML
linktitle: Comprobar el efecto de texto de DrawingML
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a comprobar los efectos de texto de DrawingML en documentos de Word con Aspose.Words para .NET con nuestra guía detallada paso a paso. Mejore sus documentos con facilidad.
weight: 10
url: /es/net/working-with-fonts/check-drawingml-text-effect/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Comprobar el efecto de texto de DrawingML

## Introducción

¡Bienvenido a otro tutorial detallado sobre cómo trabajar con Aspose.Words para .NET! Hoy nos adentraremos en el fascinante mundo de los efectos de texto de DrawingML. Ya sea que desee mejorar sus documentos de Word con sombras, reflejos o efectos 3D, esta guía le mostrará cómo buscar estos efectos de texto en sus documentos usando Aspose.Words para .NET. ¡Comencemos!

## Prerrequisitos

Antes de comenzar con el tutorial, hay algunos requisitos previos que deberá tener en cuenta:

-  Biblioteca Aspose.Words para .NET: asegúrese de tener instalada la biblioteca Aspose.Words para .NET. Puede descargarla desde[Página de lanzamiento de Aspose](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: debe tener configurado un entorno de desarrollo, como Visual Studio.
- Conocimientos básicos de C#: será útil tener cierta familiaridad con la programación en C#.

## Importar espacios de nombres

En primer lugar, debe importar los espacios de nombres necesarios. Estos espacios de nombres le brindarán acceso a las clases y métodos necesarios para manipular documentos de Word y verificar los efectos de texto de DrawingML.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

## Guía paso a paso para comprobar los efectos de texto de DrawingML

Ahora, vamos a dividir el proceso en varios pasos para que sea más fácil seguirlo.

## Paso 1: Cargue el documento

El primer paso es cargar el documento de Word en el que desea verificar los efectos de texto de DrawingML. 

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "DrawingML text effects.docx");
```

Este fragmento de código carga el documento denominado "DrawingML text effects.docx" desde el directorio especificado.

## Paso 2: Acceda a la colección de carreras

A continuación, debemos acceder a la colección de fragmentos del primer párrafo del documento. Los fragmentos son porciones de texto con el mismo formato.

```csharp
RunCollection runs = doc.FirstSection.Body.FirstParagraph.Runs;
```

Esta línea de código recupera las ejecuciones del primer párrafo de la primera sección del documento.

## Paso 3: Obtener la fuente de la primera ejecución

Ahora, obtendremos las propiedades de fuente de la primera ejecución en la colección de ejecuciones. Esto nos permite verificar los distintos efectos de texto de DrawingML aplicados al texto.

```csharp
Font runFont = runs[0].Font;
```

## Paso 4: Verifique los efectos de texto de DrawingML

Por último, podemos verificar diferentes efectos de texto de DrawingML, como Sombra, Efecto 3D, Reflejo, Contorno y Relleno.

```csharp
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Shadow));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Effect3D));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Reflection));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Outline));
Console.WriteLine(runFont.HasDmlEffect(TextDmlEffect.Fill));
```

 Estas líneas de código se imprimirán`true` o`false` dependiendo de si cada efecto de texto específico de DrawingML se aplica a la fuente de la ejecución.

## Conclusión

¡Felicitaciones! Acaba de aprender a verificar los efectos de texto de DrawingML en documentos de Word con Aspose.Words para .NET. Esta potente función le permite detectar y manipular mediante programación formatos de texto sofisticados, lo que le brinda un mayor control sobre las tareas de procesamiento de documentos.


## Preguntas frecuentes

### ¿Qué es un efecto de texto DrawingML?
Los efectos de texto de DrawingML son opciones avanzadas de formato de texto en documentos de Word, que incluyen sombras, efectos 3D, reflejos, contornos y rellenos.

### ¿Puedo aplicar efectos de texto DrawingML usando Aspose.Words para .NET?
Sí, Aspose.Words para .NET le permite verificar y aplicar efectos de texto DrawingML mediante programación.

### ¿Necesito una licencia para usar Aspose.Words para .NET?
 Sí, Aspose.Words para .NET requiere una licencia para su funcionalidad completa. Puede obtener una[licencia temporal](https://purchase.aspose.com/temporary-license/) para evaluación.

### ¿Hay una prueba gratuita disponible para Aspose.Words para .NET?
 Sí, puedes descargar un[prueba gratis](https://releases.aspose.com/) probar Aspose.Words para .NET antes de comprarlo.

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?
 Puede encontrar documentación detallada en el[Página de documentación de Aspose.Words para .NET](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
