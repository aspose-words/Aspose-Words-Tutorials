---
category: general
date: 2026-09-11
description: Mail merge de Aspose le permite cargar una plantilla de Word y completarla
  con datos, automatizando la generación de documentos para crear cartas personalizadas.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- mail merge aspose
- populate word template
- load word template
- automate document generation
- create personalized letters
language: es
lastmod: 2026-09-11
og_description: Mail merge aspose le permite cargar una plantilla de Word y completarla,
  optimizando la generación de documentos para que pueda crear cartas personalizadas
  rápidamente.
og_image_alt: Screenshot of C# code using Aspose.Words to perform a mail merge on
  a Word template
og_title: 'Combinar correspondencia Aspose: rellena una plantilla de Word en minutos'
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Mail merge aspose lets you load word template and populate word template
    with data, automating document generation for creating personalized letters.
  headline: How to perform mail merge aspose to populate a Word template
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
title: Cómo realizar una combinación de correspondencia con Aspose para rellenar una
  plantilla de Word
url: /es/net/working-with-fields/how-to-perform-mail-merge-aspose-to-populate-a-word-template/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cómo realizar mail merge con Aspose para rellenar una plantilla de Word

Si necesitas **mail merge con Aspose** para generar un lote de cartas personalizadas, esta guía te muestra exactamente cómo cargar una plantilla de Word, rellenarla con datos y automatizar la generación de documentos en unas pocas líneas de C#. Ya sea que estés construyendo un sistema de envío de correos o una herramienta de informes, el ejemplo completo a continuación te permite crear cartas personalizadas sin escribir lógica de combinación manual.

Aprenderás a **cargar la plantilla de Word**, usar la clase de bajo código `MailMerger` y **poblar la plantilla de Word** con una fuente de datos anónima. Al final del tutorial tendrás una aplicación de consola lista para ejecutar que produce un documento Word combinado que puedes enviar por correo, imprimir o archivar.

## Prerrequisitos

Antes de comenzar, asegúrate de tener:

* SDK de .NET 6.0 o posterior instalado  
* Una licencia válida de Aspose.Words for .NET (o una clave de evaluación gratuita)  
* El paquete NuGet `Aspose.Words` (versión 23.10 o más reciente) instalado en tu proyecto  
* Un archivo Word (`MailMergeTemplate.docx`) que contenga marcadores MERGEFIELD como **«Name»** y **«Age»**  

Puedes crear la plantilla en Microsoft Word insertando *Insert → Quick Parts → Field → MergeField* y nombrando los campos exactamente como los nombres de propiedad en tu fuente de datos.

## Paso 1 – Preparar la fuente de datos para el mail merge

La combinación de bajo código funciona con cualquier colección enumerable. En este ejemplo usamos una matriz de objetos anónimos, pero también podrías pasar un `DataTable`, una lista de POCOs o datos leídos de una base de datos.

```csharp
using Aspose.Words;
using Aspose.Words.LowCode;

// Sample data that will replace the MERGEFIELDs in the template
var data = new[]
{
    new { Name = "Alice",   Age = 30 },
    new { Name = "Bob",     Age = 45 },
    new { Name = "Charlie", Age = 28 }
};
```

**Por qué es importante:**  
El nombre de la propiedad de cada objeto (`Name`, `Age`) debe coincidir con un MERGEFIELD en la plantilla. La clase `MailMerger` asigna automáticamente las propiedades a los campos, eliminando la necesidad de eventos manuales `FieldMerging`.

## Paso 2 – Cargar la plantilla de Word que contiene MERGEFIELDs

Cargar la plantilla es sencillo con la clase `Document`. La ruta puede ser absoluta o relativa al directorio de trabajo del ejecutable.

```csharp
// Load the Word template that contains MERGEFIELDs
Document template = new Document("YOUR_DIRECTORY/MailMergeTemplate.docx");
```

**Consejo profesional:**  
Si ejecutas el código desde Visual Studio, establece *Copy to Output Directory* para el archivo de plantilla en **Copy always**. Esto garantiza que el archivo esté disponible cuando el binario compilado se ejecute.

## Paso 3 – Crear una instancia de MailMerger vinculada a la plantilla

La clase `MailMerger` se encuentra en el espacio de nombres `Aspose.Words.LowCode` y proporciona un único método `Execute` que acepta la fuente de datos.

```csharp
// Bind the template to a MailMerger instance
MailMerger merger = new MailMerger(template);
```

**¿Por qué usar MailMerger?**  
`MailMerger` abstrae las llamadas boilerplate a `MailMerge.Execute`, manejando la detección de campos, el enlace de datos y la clonación del documento internamente. Esto hace que el código sea ideal para escenarios de **automatizar la generación de documentos** donde deseas una solución limpia y de bajo código.

## Paso 4 – Ejecutar la combinación de bajo código usando los datos preparados

Llamar a `Execute` devuelve un nuevo `Document` que contiene

## ¿Qué deberías aprender a continuación?

Los siguientes tutoriales cubren temas estrechamente relacionados que amplían las técnicas demostradas en esta guía. Cada recurso incluye ejemplos de código completos y funcionales con explicaciones paso a paso para ayudarte a dominar características adicionales de la API y explorar enfoques de implementación alternativos en tus propios proyectos.

- [Rename Word Merge Fields with Aspose.Words for Java](/words/english/java/mail-merge-reporting/rename-word-merge-fields-aspose-words-java/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Create and Style a Word Document in Aspose.Words for .NET](/words/english/net/document-styling/apply-paragraph-style/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}