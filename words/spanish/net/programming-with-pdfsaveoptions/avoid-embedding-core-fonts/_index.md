---
title: Reducir el tamaño de los archivos PDF al no incorporar fuentes principales
linktitle: Reducir el tamaño de los archivos PDF al no incorporar fuentes principales
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a reducir el tamaño de los archivos PDF sin incorporar fuentes principales con Aspose.Words para .NET. Siga nuestra guía paso a paso para optimizar sus archivos PDF.
weight: 10
url: /es/net/programming-with-pdfsaveoptions/avoid-embedding-core-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Reducir el tamaño de los archivos PDF al no incorporar fuentes principales

## Introducción

¿Alguna vez te has preguntado por qué tus archivos PDF son tan grandes? Bueno, no eres el único. Un culpable común es la incrustación de fuentes básicas como Arial y Times New Roman. Afortunadamente, Aspose.Words para .NET tiene una forma ingeniosa de abordar este problema. En este tutorial, te mostraré cómo reducir el tamaño de tus archivos PDF evitando la incrustación de estas fuentes básicas. ¡Vamos directo al grano!

## Prerrequisitos

Antes de embarcarnos en este emocionante viaje, asegurémonos de que tienes todo lo que necesitas. Aquí tienes una lista de verificación rápida:

-  Aspose.Words para .NET: Asegúrate de tener instalado Aspose.Words para .NET. Si aún no lo tienes, puedes descargarlo[aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: necesitará un entorno de desarrollo como Visual Studio.
- Un documento de Word: utilizaremos un documento de Word (por ejemplo, "Rendering.docx") para este tutorial.
- Conocimientos básicos de C#: una comprensión básica de C# le ayudará a seguir adelante.

Bien, ahora que estamos todos listos, ¡vamos al meollo del asunto!

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Este paso garantiza que tengamos acceso a todas las funciones de Aspose.Words que necesitamos.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Inicialice su directorio de documentos

Antes de comenzar a manipular nuestro documento, debemos especificar el directorio donde se almacenan nuestros documentos. Esto es esencial para acceder a los archivos.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real donde se encuentra su documento de Word.

## Paso 2: Cargue el documento de Word

A continuación, debemos cargar el documento de Word que queremos convertir a PDF. En este ejemplo, utilizamos un documento llamado "Rendering.docx".

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

Esta línea de código carga el documento en la memoria, listo para su posterior procesamiento.

## Paso 3: Configurar las opciones para guardar PDF

Ahora viene la parte mágica. Configuraremos las opciones de guardado del PDF para evitar la incorporación de fuentes principales. Este es el paso clave que ayuda a reducir el tamaño del archivo PDF.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    UseCoreFonts = true
};
```

 Configuración`UseCoreFonts` a`true` garantiza que las fuentes principales como Arial y Times New Roman no se incrusten en el PDF, lo que reduce significativamente el tamaño del archivo.

## Paso 4: Guardar el documento como PDF

Por último, guardamos el documento de Word como PDF utilizando las opciones de guardado configuradas. Este paso genera el archivo PDF sin incrustar las fuentes principales.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.AvoidEmbeddingCoreFonts.pdf", saveOptions);
```

¡Y ya está! Tu archivo PDF ahora está guardado en el directorio especificado sin esas fuentes voluminosas.

## Conclusión

Reducir el tamaño de los archivos PDF puede ser muy fácil con Aspose.Words para .NET. Al evitar la incrustación de fuentes principales, puede reducir significativamente el tamaño del archivo, lo que facilita compartir y almacenar sus documentos. Espero que este tutorial le haya resultado útil y le haya permitido comprender claramente el proceso. Recuerde que los pequeños ajustes pueden marcar una gran diferencia.

## Preguntas frecuentes

### ¿Por qué debería evitar incrustar fuentes principales en archivos PDF?
Al evitar incrustar fuentes principales se reduce el tamaño del archivo, lo que hace que sea más fácil compartirlo y almacenarlo.

### ¿Puedo seguir viendo el PDF correctamente sin fuentes principales incrustadas?
Sí, las fuentes principales como Arial y Times New Roman generalmente están disponibles en la mayoría de los sistemas.

### ¿Qué pasa si necesito incorporar fuentes personalizadas?
 Puedes personalizar el`PdfSaveOptions`para incrustar fuentes específicas según sea necesario.

### ¿Aspose.Words para .NET es de uso gratuito?
 Aspose.Words para .NET requiere una licencia. Puede obtener una versión de prueba gratuita[aquí](https://releases.aspose.com/).

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?
 Puede encontrar documentación detallada[aquí](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
