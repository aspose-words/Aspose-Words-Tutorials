---
title: Código en línea
linktitle: Código en línea
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a aplicar estilos de código en línea en documentos de Word con Aspose.Words para .NET. Este tutorial cubre el uso de comillas simples y múltiples para el formato de código.
weight: 10
url: /es/net/working-with-markdown/inline-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Código en línea

## Introducción

Si está trabajando en la generación o manipulación de documentos de Word mediante programación, es posible que necesite dar formato al texto para que se parezca al código. Ya sea para documentación o fragmentos de código en un informe, Aspose.Words para .NET proporciona una forma sólida de gestionar el estilo del texto. En este tutorial, nos centraremos en cómo aplicar estilos de código en línea al texto mediante Aspose.Words. Exploraremos cómo definir y utilizar estilos personalizados para comillas simples y múltiples, lo que hará que sus segmentos de código se destaquen claramente en sus documentos.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Biblioteca Aspose.Words para .NET: asegúrese de tener Aspose.Words instalado en su entorno .NET. Puede descargarlo desde[Página de lanzamiento de Aspose.Words para .NET](https://releases.aspose.com/words/net/).

2. Conocimientos básicos de programación .NET: esta guía asume que usted tiene un conocimiento fundamental de la programación en C# y .NET.

3. Entorno de desarrollo: debe tener configurado un entorno de desarrollo .NET, como Visual Studio, donde pueda escribir y ejecutar código C#.

## Importar espacios de nombres

Para comenzar a utilizar Aspose.Words en su proyecto, deberá importar los espacios de nombres necesarios. A continuación, le indicamos cómo hacerlo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Dividamos el proceso en pasos claros:

## Paso 1: Inicializar el documento y DocumentBuilder

 Primero, necesitas crear un nuevo documento y un`DocumentBuilder` instancia. El`DocumentBuilder`La clase te ayuda a agregar contenido y formatearlo en un documento de Word.

```csharp
// Inicialice DocumentBuilder con el nuevo documento.
DocumentBuilder builder = new DocumentBuilder();
```

## Paso 2: Agregar estilo de código en línea con una comilla invertida

En este paso, definiremos un estilo para el código en línea con una sola comilla invertida. Este estilo formateará el texto para que parezca código en línea.

### Definir el estilo

```csharp
// Define un nuevo estilo de carácter para el código en línea con una comilla invertida.
Style inlineCode1BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode");
inlineCode1BackTicks.Font.Name = "Courier New"; // Una fuente típica para código.
inlineCode1BackTicks.Font.Size = 10.5; // Tamaño de fuente para el código en línea.
inlineCode1BackTicks.Font.Color = System.Drawing.Color.Blue; // Color del texto del código.
inlineCode1BackTicks.Font.Bold = true; // Poner el texto del código en negrita.
```

### Aplicar el estilo

Ahora, puedes aplicar este estilo al texto de tu documento.

```csharp
// Utilice DocumentBuilder para insertar texto con el estilo de código en línea.
builder.Font.Style = inlineCode1BackTicks;
builder.Writeln("Text with InlineCode style with 1 backtick");
```

## Paso 3: Agregar estilo de código en línea con tres comillas invertidas

A continuación, definiremos un estilo para el código en línea con tres comillas invertidas, que normalmente se utiliza para bloques de código de varias líneas.

### Definir el estilo

```csharp
// Define un nuevo estilo de carácter para el código en línea con tres comillas invertidas.
Style inlineCode3BackTicks = builder.Document.Styles.Add(StyleType.Character, "InlineCode.3");
inlineCode3BackTicks.Font.Name = "Courier New"; // Fuente consistente para el código.
inlineCode3BackTicks.Font.Size = 10.5; // Tamaño de fuente para el bloque de código.
inlineCode3BackTicks.Font.Color = System.Drawing.Color.Green; //Diferentes colores para mayor visibilidad.
inlineCode3BackTicks.Font.Bold = true; // Manténgalo en negrita para enfatizar.
```

### Aplicar el estilo

Aplique este estilo al texto para formatearlo como un bloque de código de varias líneas.

```csharp
// Aplicar el estilo al bloque de código.
builder.Font.Style = inlineCode3BackTicks;
builder.Writeln("Text with InlineCode style with 3 backticks");
```

## Conclusión

Dar formato al texto como código en línea en documentos de Word con Aspose.Words para .NET es sencillo una vez que conoces los pasos. Al definir y aplicar estilos personalizados con una o varias comillas invertidas, puedes hacer que tus fragmentos de código se destaquen claramente. Este método es particularmente útil para documentación técnica o cualquier documento donde la legibilidad del código sea esencial.

Experimente con diferentes estilos y opciones de formato para adaptarlos mejor a sus necesidades. Aspose.Words ofrece una gran flexibilidad, lo que le permite personalizar en gran medida la apariencia de su documento.

## Preguntas frecuentes

### ¿Puedo utilizar fuentes diferentes para estilos de código en línea?
Sí, puedes utilizar cualquier fuente que se adapte a tus necesidades. Las fuentes como "Courier New" se utilizan normalmente para el código debido a su naturaleza monoespaciada.

### ¿Cómo cambio el color del texto del código en línea?
 Puedes cambiar el color configurando el`Font.Color` propiedad del estilo a cualquier`System.Drawing.Color`.

### ¿Puedo aplicar varios estilos al mismo texto?
En Aspose.Words, solo se puede aplicar un estilo a la vez. Si necesita combinar estilos, considere crear un nuevo estilo que incorpore todo el formato deseado.

### ¿Cómo aplico estilos a un texto existente en un documento?
 Para aplicar estilos a un texto existente, primero debe seleccionar el texto y luego aplicar el estilo deseado usando el`Font.Style` propiedad.

### ¿Puedo utilizar Aspose.Words para otros formatos de documentos?
Aspose.Words está diseñado específicamente para documentos de Word. Para otros formatos, es posible que deba utilizar bibliotecas diferentes o convertir los documentos a un formato compatible.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
