---
title: Mantener los personajes de control heredados
linktitle: Mantener los personajes de control heredados
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a conservar caracteres de control heredados en documentos de Word usando Aspose.Words para .NET con esta guía paso a paso.
weight: 10
url: /es/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mantener los personajes de control heredados

## Introducción

¿Alguna vez te has sentido desconcertado por esos extraños e invisibles caracteres de control en tus documentos de Word? Son como pequeños duendes ocultos que pueden arruinar el formato y la funcionalidad. Afortunadamente, Aspose.Words para .NET ofrece una función útil para mantener intactos estos caracteres de control heredados al guardar documentos. En este tutorial, profundizaremos en cómo administrar estos caracteres de control con Aspose.Words para .NET. Lo desglosaremos paso a paso, asegurándonos de que comprendas cada detalle a lo largo del camino. ¿Listo para comenzar? ¡Vamos a sumergirnos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET: descargar e instalar desde[aquí](https://releases.aspose.com/words/net/).
2.  Una licencia Aspose válida: Puede obtener una licencia temporal[aquí](https://purchase.aspose.com/temporary-license/).
3. Entorno de desarrollo: Visual Studio o cualquier otro IDE que admita .NET.
4. Conocimientos básicos de C#: será útil estar familiarizado con el lenguaje de programación C#.

## Importar espacios de nombres

Antes de escribir el código, debe importar los espacios de nombres necesarios. Agregue las siguientes líneas en la parte superior del archivo C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Configuración del proyecto

Primero, necesitarás configurar tu proyecto en Visual Studio (o tu IDE preferido). 

1. Cree un nuevo proyecto de C#: abra Visual Studio y cree un nuevo proyecto de aplicación de consola de C#.
2. Instalar Aspose.Words para .NET: utilice el Administrador de paquetes NuGet para instalar Aspose.Words para .NET. Haga clic con el botón derecho en su proyecto en el Explorador de soluciones, seleccione "Administrar paquetes NuGet", busque "Aspose.Words" e instálelo.

## Paso 2: Cargue su documento

A continuación, cargará el documento de Word que contiene los caracteres de control heredados.

1. Especifique la ruta del documento: establezca la ruta a su directorio de documentos.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2.  Cargar el documento: Utilice el`Document` clase para cargar su documento.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Paso 3: Configurar las opciones de guardado

Ahora, configuremos las opciones de guardado para mantener intactos los caracteres de control heredados.

1.  Crear Opciones de guardado: Inicializar una instancia de`OoxmlSaveOptions` y establecer el`KeepLegacyControlChars`propiedad a`true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Paso 4: Guardar el documento

Por último, guarde el documento con las opciones de guardado configuradas.

1.  Guardar el documento: Utilice el`Save` método de la`Document` clase para guardar el documento con las opciones de guardado especificadas.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusión

¡Y ya está! Si sigue estos pasos, podrá asegurarse de que sus caracteres de control heredados se conserven al trabajar con documentos de Word en Aspose.Words para .NET. Esta función puede ser un salvavidas, especialmente cuando se trabaja con documentos complejos en los que los caracteres de control desempeñan un papel crucial. 

## Preguntas frecuentes

### ¿Qué son los caracteres de control heredados?

Los caracteres de control heredados son caracteres no imprimibles que se utilizan en documentos más antiguos para controlar el formato y el diseño.

### ¿Puedo eliminar estos personajes de control en lugar de conservarlos?

Sí, puede usar Aspose.Words para .NET para eliminar o reemplazar estos caracteres si es necesario.

### ¿Esta función está disponible en todas las versiones de Aspose.Words para .NET?

Esta función está disponible en versiones recientes. Asegúrate de utilizar la última versión para acceder a todas las funciones.

### ¿Necesito una licencia para usar Aspose.Words para .NET?

 Sí, necesitas una licencia válida. Puedes obtener una licencia temporal para fines de evaluación.[aquí](https://purchase.aspose.com/temporary-license/).

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?

 Puede encontrar documentación detallada[aquí](https://reference.aspose.com/words/net/).
 
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
