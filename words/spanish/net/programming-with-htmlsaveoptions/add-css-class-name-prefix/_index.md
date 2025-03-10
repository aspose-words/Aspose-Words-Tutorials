---
title: Agregar prefijo al nombre de la clase CSS
linktitle: Agregar prefijo al nombre de la clase CSS
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a agregar un prefijo de nombre de clase CSS al guardar documentos de Word como HTML con Aspose.Words para .NET. Incluye una guía paso a paso, fragmentos de código y preguntas frecuentes.
weight: 10
url: /es/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Agregar prefijo al nombre de la clase CSS

## Introducción

¡Bienvenido! Si te estás adentrando en el mundo de Aspose.Words para .NET, te espera una sorpresa. Hoy, exploraremos cómo agregar un prefijo de nombre de clase CSS al guardar un documento de Word como HTML usando Aspose.Words para .NET. Esta función es muy útil cuando quieres evitar conflictos de nombres de clase en tus archivos HTML.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

-  Aspose.Words para .NET: Si aún no lo ha instalado,[Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: Visual Studio o cualquier otro IDE de C#.
-  Un documento de Word: usaremos un documento llamado`Rendering.docx`Colóquelo en el directorio de su proyecto.

## Importar espacios de nombres

En primer lugar, asegúrese de haber importado los espacios de nombres necesarios en su proyecto de C#. Añádalos en la parte superior de su archivo de código:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

¡Ahora, profundicemos en la guía paso a paso!

## Paso 1: Configura tu proyecto

Antes de que podamos comenzar a agregar un prefijo de nombre de clase CSS, configuremos nuestro proyecto.

### Paso 1.1: Crear un nuevo proyecto

 Abra Visual Studio y cree un nuevo proyecto de aplicación de consola. Asígnele un nombre llamativo, como`AsposeCssPrefixExample`.

### Paso 1.2: Agregar Aspose.Words para .NET

Si aún no lo ha hecho, agregue Aspose.Words para .NET a su proyecto a través de NuGet. Simplemente abra la consola del administrador de paquetes NuGet y ejecute:

```bash
Install-Package Aspose.Words
```

¡Genial! Ahora estamos listos para comenzar a codificar.

## Paso 2: Cargue su documento

Lo primero que debemos hacer es cargar el documento de Word que queremos convertir a HTML.

### Paso 2.1: Definir la ruta del documento

 Establezca la ruta al directorio de su documento. Para los fines de este tutorial, supongamos que su documento está en una carpeta llamada`Documents` dentro del directorio de su proyecto.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Paso 2.2: Cargar el documento

Ahora, carguemos el documento usando Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Paso 3: Configurar las opciones de guardado de HTML

A continuación, debemos configurar las opciones de guardado de HTML para incluir un prefijo de nombre de clase CSS.

### Paso 3.1: Crear opciones de guardado de HTML

 Instanciar el`HtmlSaveOptions` objeto y establezca el tipo de hoja de estilo CSS en`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Paso 3.2: Establecer el prefijo del nombre de clase CSS

 Ahora, vamos a configurar el`CssClassNamePrefix` propiedad al prefijo que desee. Para este ejemplo, utilizaremos`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Paso 4: Guardar el documento como HTML

Por último, guardemos el documento como un archivo HTML con nuestras opciones configuradas.


Especifique la ruta del archivo HTML de salida y guarde el documento.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Paso 5: Verificar la salida

 Después de ejecutar su proyecto, navegue hasta su`Documents` carpeta. Deberías encontrar un archivo HTML llamado`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` Abra este archivo en un editor de texto o navegador para verificar que las clases CSS tengan el prefijo`pfx_`.

## Conclusión

¡Y ya está! Si sigue estos pasos, habrá agregado con éxito un prefijo de nombre de clase CSS a su salida HTML mediante Aspose.Words para .NET. Esta función simple pero poderosa puede ayudarlo a mantener estilos limpios y sin conflictos en sus documentos HTML.

## Preguntas frecuentes

### ¿Puedo utilizar un prefijo diferente para cada operación de guardado?
 Sí, puedes personalizar el prefijo cada vez que guardes un documento cambiando el`CssClassNamePrefix` propiedad.

### ¿Este método admite CSS en línea?
 El`CssClassNamePrefix`La propiedad funciona con CSS externo. Para CSS en línea, necesitarás un enfoque diferente.

### ¿Cómo puedo incluir otras opciones de guardado HTML?
 Puede configurar varias propiedades de`HtmlSaveOptions` Para personalizar la salida HTML, marque la casilla[documentación](https://reference.aspose.com/words/net/) Para más detalles.

### ¿Es posible guardar el HTML en un stream?
 ¡Por supuesto! Puedes guardar el documento en una secuencia pasando el objeto de secuencia a la`Save` método.

### ¿Cómo puedo obtener ayuda si tengo problemas?
 Puede obtener ayuda de la[Foro de Aspose](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
