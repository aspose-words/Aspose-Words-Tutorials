---
title: Tachado
linktitle: Tachado
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a aplicar formato de tachado al texto con Aspose.Words para .NET con nuestra guía paso a paso. Mejore sus habilidades de procesamiento de documentos.
weight: 10
url: /es/net/working-with-markdown/strikethrough/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tachado

## Introducción

Bienvenido a esta guía detallada sobre cómo aplicar formato de tachado al texto mediante Aspose.Words para .NET. Si busca mejorar sus habilidades de procesamiento de documentos y agregar un toque único a su texto, está en el lugar correcto. ¡Vamos a profundizar!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET: Descárgalo[aquí](https://releases.aspose.com/words/net/).
- .NET Framework: asegúrese de tener .NET Framework instalado en su sistema.
- Entorno de desarrollo: un IDE como Visual Studio.
- Conocimientos básicos de C#: Es necesario estar familiarizado con la programación en C#.

## Importar espacios de nombres

Para comenzar, deberá importar los espacios de nombres necesarios. Estos son esenciales para acceder a la biblioteca Aspose.Words y sus funciones.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Inicializar DocumentBuilder

 El`DocumentBuilder` La clase es una herramienta poderosa en Aspose.Words que le permite agregar contenido a su documento con facilidad.

```csharp
// Inicializar un DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder();
```

## Paso 2: Establecer la propiedad de tachado

Ahora, apliquemos la propiedad de tachado a nuestro texto. Esto implica configurar el`StrikeThrough` propiedad de la`Font` oponerse a`true`.

```csharp
// Tacha el texto.
builder.Font.StrikeThrough = true;
```

## Paso 3: Escribe texto tachado

 Con la propiedad de tachado establecida, ahora podemos agregar nuestro texto.`Writeln` El método agregará el texto al documento.

```csharp
// Escribe texto tachado.
builder.Writeln("This text will be StrikeThrough");
```

## Conclusión

¡Y ya está! Ha añadido con éxito el formato de tachado a su texto con Aspose.Words para .NET. Esta potente biblioteca abre un mundo de posibilidades para el procesamiento y la personalización de documentos. Ya sea que esté creando informes, cartas o cualquier otro tipo de documento, dominar estas funciones sin duda mejorará su productividad y la calidad de sus resultados.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca de procesamiento de documentos que permite a los desarrolladores crear, manipular y convertir documentos de Word mediante programación.

### ¿Puedo utilizar Aspose.Words para .NET en un proyecto comercial?
 Sí, puede utilizar Aspose.Words para .NET en proyectos comerciales. Para conocer las opciones de compra, visite el sitio web[página de compra](https://purchase.aspose.com/buy).

### ¿Hay una prueba gratuita disponible para Aspose.Words para .NET?
 Sí, puedes descargar una versión de prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Cómo puedo obtener soporte para Aspose.Words para .NET?
Puede obtener soporte de la comunidad Aspose y de expertos en el[foro de soporte](https://forum.aspose.com/c/words/8).

### ¿Puedo aplicar otras opciones de formato de texto usando Aspose.Words para .NET?
¡Por supuesto! Aspose.Words para .NET admite una amplia variedad de opciones de formato de texto, incluidas negrita, cursiva, subrayado y más.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
