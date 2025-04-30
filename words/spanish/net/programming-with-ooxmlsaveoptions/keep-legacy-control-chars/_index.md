---
"description": "Aprenda a conservar caracteres de control heredados en documentos de Word usando Aspose.Words para .NET con esta guía paso a paso."
"linktitle": "Mantener los personajes de control heredados"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Mantener los personajes de control heredados"
"url": "/es/net/programming-with-ooxmlsaveoptions/keep-legacy-control-chars/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mantener los personajes de control heredados

## Introducción

¿Alguna vez te han intrigado esos extraños e invisibles caracteres de control en tus documentos de Word? Son como pequeños duendes ocultos que pueden arruinar el formato y la funcionalidad. Por suerte, Aspose.Words para .NET ofrece una práctica función para mantener intactos estos caracteres de control antiguos al guardar documentos. En este tutorial, profundizaremos en cómo administrar estos caracteres de control con Aspose.Words para .NET. Lo explicaremos paso a paso para que comprendas todos los detalles. ¿Listo para empezar? ¡Comencemos!

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

1. Aspose.Words para .NET: Descargar e instalar desde [aquí](https://releases.aspose.com/words/net/).
2. Una licencia Aspose válida: Puede obtener una licencia temporal [aquí](https://purchase.aspose.com/temporary-license/).
3. Entorno de desarrollo: Visual Studio o cualquier otro IDE que admita .NET.
4. Conocimientos básicos de C#: será útil estar familiarizado con el lenguaje de programación C#.

## Importar espacios de nombres

Antes de escribir el código, debe importar los espacios de nombres necesarios. Agregue las siguientes líneas al principio del archivo de C#:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Configuración de su proyecto

Primero, necesitarás configurar tu proyecto en Visual Studio (o tu IDE preferido). 

1. Cree un nuevo proyecto de C#: abra Visual Studio y cree un nuevo proyecto de aplicación de consola de C#.
2. Instalar Aspose.Words para .NET: Use el Administrador de paquetes NuGet para instalar Aspose.Words para .NET. Haga clic con el botón derecho en su proyecto en el Explorador de soluciones, seleccione "Administrar paquetes NuGet", busque "Aspose.Words" e instálelo.

## Paso 2: Cargue su documento

A continuación, cargará el documento de Word que contiene los caracteres de control heredados.

1. Especifique la ruta del documento: establezca la ruta a su directorio de documentos.
   
   ```csharp
   string dataDir = "YOUR DOCUMENT DIRECTORY";
   ```

2. Cargar el documento: Utilice el `Document` clase para cargar su documento.

   ```csharp
   Document doc = new Document(dataDir + "Legacy control character.doc");
   ```

## Paso 3: Configurar las opciones de guardado

Ahora, configuremos las opciones de guardado para mantener intactos los caracteres de control heredados.

1. Crear opciones de guardado: Inicializar una instancia de `OoxmlSaveOptions` y establecer el `KeepLegacyControlChars` propiedad a `true`.

   ```csharp
   OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.FlatOpc)
   {
       KeepLegacyControlChars = true
   };
   ```

## Paso 4: Guardar el documento

Por último, guarde el documento con las opciones de guardado configuradas.

1. Guardar el documento: Utilice el `Save` método de la `Document` clase para guardar el documento con las opciones de guardado especificadas.

   ```csharp
   doc.Save(dataDir + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
   ```

## Conclusión

¡Listo! Siguiendo estos pasos, puede asegurarse de que sus caracteres de control antiguos se conserven al trabajar con documentos de Word en Aspose.Words para .NET. Esta función puede ser fundamental, especialmente al trabajar con documentos complejos donde los caracteres de control son cruciales. 

## Preguntas frecuentes

### ¿Qué son los caracteres de control heredados?

Los caracteres de control heredados son caracteres no imprimibles que se utilizan en documentos antiguos para controlar el formato y el diseño.

### ¿Puedo eliminar estos personajes de control en lugar de conservarlos?

Sí, puede usar Aspose.Words para .NET para eliminar o reemplazar estos caracteres si es necesario.

### ¿Esta función está disponible en todas las versiones de Aspose.Words para .NET?

Esta función está disponible en versiones recientes. Asegúrate de usar la última versión para acceder a todas las funciones.

### ¿Necesito una licencia para usar Aspose.Words para .NET?

Sí, necesita una licencia válida. Puede obtener una licencia temporal para fines de evaluación. [aquí](https://purchase.aspose.com/temporary-license/).

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words para .NET?

Puede encontrar documentación detallada [aquí](https://reference.aspose.com/words/net/).
 


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}