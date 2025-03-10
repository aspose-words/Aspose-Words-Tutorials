---
title: Código Cercado
linktitle: Código Cercado
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar código restringido y cadenas de información a documentos de Word con Aspose.Words para .NET. Incluye una guía paso a paso. Mejore sus habilidades de formato de documentos.
weight: 10
url: /es/net/working-with-markdown/fenced-code/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Código Cercado

## Introducción

¡Hola, colega programador! Hoy nos adentraremos en el mundo de Aspose.Words para .NET para dominar el arte de agregar código restringido y código restringido con cadenas de información a sus documentos de Word. Imagine que su documento de Word es un lienzo y que usted, el artista, está a punto de pintar con la precisión de un desarrollador experimentado. Con Aspose.Words, obtiene el poder de mejorar programáticamente sus documentos con bloques de código estructurados y formateados, lo que hace que sus documentos técnicos brillen con profesionalismo y claridad.

## Prerrequisitos

Antes de comenzar con el tutorial, asegurémonos de que tienes todo lo que necesitas:

- Conocimientos básicos de C#: una comprensión general de C# le ayudará a comprender los conceptos rápidamente.
-  Aspose.Words para .NET: Necesitas tener Aspose.Words para .NET instalado. Si aún no lo tienes, descárgalo[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Visual Studio o cualquier otro IDE de C# con el que se sienta cómodo.

## Importar espacios de nombres

Lo primero es lo primero: debes importar los espacios de nombres necesarios. Esto es como reunir todas tus herramientas antes de comenzar un proyecto.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Ahora, analicemos el proceso paso a paso.

## Paso 1: Configuración del proyecto

Antes de poder crear bloques de código hermosos y formateados en nuestro documento de Word, necesitamos configurar un nuevo proyecto en Visual Studio.

1. Crear un nuevo proyecto: abra Visual Studio y cree una nueva aplicación de consola C#.
2. Agregar referencia de Aspose.Words: Instale Aspose.Words a través del Administrador de paquetes NuGet. Puede hacerlo haciendo clic derecho en su proyecto en el Explorador de soluciones, seleccionando "Administrar paquetes NuGet" y buscando Aspose.Words.

## Paso 2: Inicializar DocumentBuilder

Ahora que su proyecto está configurado, inicialicemos DocumentBuilder, que será nuestra herramienta principal para agregar contenido al documento de Word.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Paso 3: Crear un estilo para el código protegido

Para agregar código protegido, primero debemos crear un estilo. Piense en esto como si estuviera configurando el tema para nuestro bloque de código.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Paso 4: Agregar código restringido al documento

Con nuestro estilo listo, ahora podemos agregar un bloque de código cercado al documento.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Paso 5: Crear un estilo para código protegido con cadena de información

A veces, es posible que quieras especificar el lenguaje de programación o agregar información adicional a tu bloque de código. Creemos un estilo para eso.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Paso 6: Agregue código restringido con cadena de información al documento

Ahora, agreguemos un bloque de código cercado con una cadena de información para indicar que es código C#.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Conclusión

¡Felicitaciones! Acaba de agregar bloques de código cercado y código cercado con cadenas de información a sus documentos de Word usando Aspose.Words para .NET. Esto es solo la punta del iceberg. Con Aspose.Words, puede automatizar y mejorar el procesamiento de sus documentos a nuevas alturas. ¡Siga explorando y disfrute de la codificación!

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, manipular y convertir documentos de Word mediante programación.

### ¿Puedo usar Aspose.Words con otros lenguajes de programación?
Aspose.Words admite principalmente lenguajes .NET, pero hay versiones disponibles para Java, Python y otros lenguajes.

### ¿Aspose.Words es de uso gratuito?
 Aspose.Words es un producto comercial, pero puedes descargar una versión de prueba gratuita[aquí](https://releases.aspose.com/)para explorar sus características.

### ¿Cómo puedo obtener soporte para Aspose.Words?
 Puede obtener soporte de la comunidad y los desarrolladores de Aspose.[aquí](https://forum.aspose.com/c/words/8).

### ¿Qué otras características ofrece Aspose.Words?
Aspose.Words ofrece una amplia gama de funciones que incluyen conversión de documentos, generación de documentos basada en plantillas, informes y mucho más.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
