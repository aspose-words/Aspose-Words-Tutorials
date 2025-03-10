---
title: Trabajar con el modelo de IA abierta
linktitle: Trabajar con el modelo de IA abierta
second_title: API de procesamiento de documentos Aspose.Words
description: Descubra cómo realizar resúmenes de documentos de manera eficiente con Aspose.Words para .NET y los potentes modelos de OpenAI. Sumérjase en esta guía completa ahora.
weight: 10
url: /es/net/ai-powered-document-processing/working-with-open-ai-model/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Trabajar con el modelo de IA abierta

## Introducción

En el mundo digital actual, el contenido es el rey. Ya seas estudiante, profesional de negocios o un escritor ávido, la capacidad de manipular, resumir y generar documentos de manera eficiente es invaluable. Aquí es donde entra en juego la biblioteca Aspose.Words para .NET, que te permite administrar documentos como un profesional. En este tutorial completo, profundizaremos en cómo aprovechar Aspose.Words junto con los modelos OpenAI para resumir documentos de manera efectiva. ¿Estás listo para liberar tu potencial de administración de documentos? ¡Comencemos!

## Prerrequisitos

Antes de arremangarnos y sumergirnos en el código, hay algunos elementos esenciales que necesitarás tener en cuenta:

### Marco .NET
Asegúrate de que estás utilizando una versión de .NET Framework que sea compatible con Aspose.Words. Por lo general, .NET 5.0 y versiones posteriores deberían funcionar perfectamente.

### Biblioteca Aspose.Words para .NET
 Necesitará descargar e instalar la biblioteca Aspose.Words. Puede descargarla desde[Este enlace](https://releases.aspose.com/words/net/).

### Clave API de OpenAI
Para integrar los modelos de lenguaje de OpenAI para el resumen de documentos, necesitará una clave API. Puede obtenerla registrándose en la plataforma OpenAI y recuperando su clave desde la configuración de su cuenta.

### IDE para desarrollo
Tener un entorno de desarrollo integrado (IDE) como Visual Studio configurado es ideal para desarrollar aplicaciones .NET.

### Conocimientos básicos de programación
Una comprensión básica de C# y de la programación orientada a objetos le ayudará a comprender los conceptos más fácilmente.

## Importar paquetes

Ahora que tenemos todo preparado, vamos a importar nuestros paquetes. Abra su proyecto de Visual Studio y agregue las bibliotecas necesarias. A continuación, le indicamos cómo hacerlo:

### Agregar paquete Aspose.Words

Puede agregar el paquete Aspose.Words a través del Administrador de paquetes NuGet. A continuación, le indicamos cómo hacerlo:
- Vaya a Herramientas -> Administrador de paquetes NuGet -> Administrar paquetes NuGet para la solución.
- Busque "Aspose.Words" y haga clic en Instalar.

### Agregar entorno del sistema

 Asegúrese de incluir el`System`espacio de nombres para manejar variables de entorno:
```csharp
using System.Text;
using Aspose.Words;
using System;
using Aspose.Words.AI;
```

### Agregar Aspose.Words

Luego, incluya el espacio de nombres Aspose.Words en su archivo C#:
```csharp
using Aspose.Words;
```

### Agregar biblioteca OpenAI

Si usa una biblioteca para interactuar con OpenAI (como un cliente REST), asegúrese de incluirla también. Es posible que deba agregarla a través de NuGet de la misma manera que agregamos Aspose.Words.

Ahora que hemos preparado nuestro entorno e importado los paquetes necesarios, analicemos el proceso de resumen de documentos paso a paso.

## Paso 1: Defina sus directorios de documentos

Antes de poder comenzar a jugar con sus documentos, debe configurar los directorios donde residirán sus documentos y artefactos:

```csharp
// Su directorio de documentos
string MyDir = "YOUR_DOCUMENT_DIRECTORY";
// Su directorio de artefactos
string ArtifactsDir = "YOUR_ARTIFACTS_DIRECTORY";
```
 Esto hace que su código sea más manejable, ya que puede cambiar fácilmente las rutas si es necesario.`MyDir` es donde se almacenan sus documentos de entrada, mientras`ArtifactsDir` Es donde guardarás los resúmenes generados.

## Paso 2: Cargue sus documentos

continuación, deberá cargar los documentos que desea resumir. Esto es muy sencillo con Aspose.Words:

```csharp
Document firstDoc = new Document(MyDir + "Big document.docx");
Document secondDoc = new Document(MyDir + "Document.docx");
```
Asegúrate de que los nombres de tus documentos coincidan con los que pretendes utilizar, de lo contrario, ¡te encontrarás con errores!

## Paso 3: Obtenga su clave API

Ahora que sus documentos están cargados, es momento de obtener su clave API de OpenAI. La obtendrá de las variables de entorno para mantenerla segura:
```csharp
string apiKey = Environment.GetEnvironmentVariable("API_KEY");
```
Es esencial administrar su clave API de forma segura para mantener a raya a los usuarios no autorizados.

## Paso 4: Crear una instancia del modelo OpenAI

Con la clave API lista, ya puede crear una instancia del modelo OpenAI. Para el resumen del documento, utilizaremos el modelo Gpt4OMini:

```csharp
IAiModelText model = (IAiModelText)AiModel.Create(AiModelType.Gpt4OMini).WithApiKey(apiKey);
```
Este paso básicamente configura la capacidad intelectual necesaria para resumir sus documentos, lo que le brinda acceso al resumen impulsado por IA.

## Paso 5: Resumir un solo documento

Resumamos primero el primer documento. Aquí es donde ocurre la magia:

```csharp
Document oneDocumentSummary = model.Summarize(firstDoc, new SummarizeOptions() { SummaryLength = SummaryLength.Short });
oneDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.One.docx");
```
 Aquí, estamos usando el`Summarize` método del modelo.`SummaryLength.Short`El parámetro especifica que queremos un resumen breve, ¡perfecto para una descripción general rápida!

## Paso 6: Resume varios documentos

¿Te sientes ambicioso? Puedes resumir varios documentos a la vez. Mira lo fácil que es:

```csharp
Document multiDocumentSummary = model.Summarize(new Document[] { firstDoc, secondDoc }, new SummarizeOptions() { SummaryLength = SummaryLength.Long });
multiDocumentSummary.Save(ArtifactsDir + "AI.AiSummarize.Multi.docx");
```
Esta función es especialmente útil para comparar varios archivos. Tal vez te estés preparando para una reunión y necesites notas concisas de varios informes extensos. ¡Este es tu nuevo mejor amigo!

## Conclusión

Resumir documentos con Aspose.Words para .NET y OpenAI no es solo una habilidad beneficiosa, sino que también te empodera. Si sigues esta guía, habrás convertido textos largos y complicados en resúmenes concisos, lo que te permitirá ahorrar tiempo y esfuerzo. Ya sea que quieras garantizar la claridad para los clientes o preparar esa presentación importante, ahora tienes las herramientas para hacerlo de manera eficiente.

Entonces, ¿qué estás esperando? ¡Sumérgete en tus documentos con confianza y deja que la tecnología haga el trabajo pesado!

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?  
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, manipular y convertir documentos mediante programación.

### ¿Necesito una clave API para OpenAI?  
Sí, debe tener una clave API de OpenAI válida para acceder a las capacidades de resumen utilizando sus modelos.

### ¿Puedo resumir varios documentos a la vez?  
¡Por supuesto! Puedes resumir varios documentos en una sola llamada, lo que resulta ideal para informes extensos.

### ¿Cómo instalo Aspose.Words?  
Puede instalarlo a través del Administrador de paquetes NuGet en Visual Studio buscando "Aspose.Words".

### ¿Existe una prueba gratuita de Aspose.Words?  
 Sí, puedes acceder a una prueba gratuita de Aspose.Words a través de su[sitio web](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
