---
title: Enumerar propiedades
linktitle: Enumerar propiedades
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a enumerar propiedades en un documento de Word con Aspose.Words para .NET con esta guía paso a paso. Perfecta para desarrolladores de todos los niveles.
weight: 10
url: /es/net/programming-with-document-properties/enumerate-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Enumerar propiedades

## Introducción

¿Quiere trabajar con documentos de Word de forma programada? Aspose.Words para .NET es una herramienta potente que puede ayudarlo a lograrlo. Hoy, le mostraré cómo enumerar las propiedades de un documento de Word utilizando Aspose.Words para .NET. Ya sea que sea un principiante o tenga algo de experiencia, esta guía lo desglosará paso a paso de una manera conversacional y fácil de seguir.

## Prerrequisitos

Antes de sumergirnos en el tutorial, hay algunas cosas que necesitarás para comenzar:

-  Aspose.Words para .NET: puedes[Descárgalo aquí](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: se recomienda Visual Studio, pero puede utilizar cualquier IDE de C#.
- Conocimientos básicos de C#: una comprensión fundamental de C# le ayudará a seguir adelante.

¡Ahora, vamos a empezar!

## Paso 1: Configuración del proyecto

Lo primero es lo primero: debes configurar tu proyecto en Visual Studio.

1. Crear un nuevo proyecto: abra Visual Studio y cree un nuevo proyecto de aplicación de consola.
2. Instalar Aspose.Words para .NET: utilice el Administrador de paquetes NuGet para instalar Aspose.Words para .NET. Haga clic con el botón derecho en su proyecto en el Explorador de soluciones, seleccione "Administrar paquetes NuGet" y busque "Aspose.Words". Instale el paquete.

## Paso 2: Importar espacios de nombres

Para trabajar con Aspose.Words, debe importar los espacios de nombres necesarios. Agregue lo siguiente en la parte superior del archivo Program.cs:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Properties;
```

## Paso 3: Cargue su documento

A continuación, carguemos el documento de Word con el que desea trabajar. Para este ejemplo, utilizaremos un documento llamado "Properties.docx" ubicado en el directorio de su proyecto.

1. Definir la ruta del documento: especifique la ruta a su documento.
2.  Cargar el documento: utilizar Aspose.Words`Document` clase para cargar el documento.

Aquí está el código:

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Properties.docx");
```

## Paso 4: Mostrar el nombre del documento

Una vez cargado el documento, es posible que desee mostrar su nombre. Aspose.Words ofrece una propiedad para esto:

```csharp
Console.WriteLine("1. Document name: {0}", doc.OriginalFileName);
```

## Paso 5: Enumerar las propiedades integradas

Las propiedades integradas son propiedades de metadatos predefinidas por Microsoft Word. Entre ellas se incluyen el título, el autor y más.

1.  Acceda a las propiedades integradas: utilice el`BuiltInDocumentProperties` recopilación.
2. Recorrer propiedades en bucle: recorre las propiedades y muestra sus nombres y valores.

Aquí está el código:

```csharp
Console.WriteLine("2. Built-in Properties");

foreach (DocumentProperty prop in doc.BuiltInDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Paso 6: Enumerar propiedades personalizadas

Las propiedades personalizadas son propiedades de metadatos definidas por el usuario. Pueden ser cualquier cosa que desee agregar a su documento.

1.  Acceder a propiedades personalizadas: utilice el`CustomDocumentProperties` recopilación.
2. Recorrer propiedades en bucle: recorre las propiedades y muestra sus nombres y valores.

Aquí está el código:

```csharp
Console.WriteLine("3. Custom Properties");

foreach (DocumentProperty prop in doc.CustomDocumentProperties)
    Console.WriteLine("{0} : {1}", prop.Name, prop.Value);
```

## Conclusión

¡Y ya está! Ha enumerado con éxito las propiedades integradas y personalizadas de un documento de Word con Aspose.Words para .NET. Esto es solo la punta del iceberg de lo que puede hacer con Aspose.Words. Ya sea que esté automatizando la generación de documentos o manipulando documentos complejos, Aspose.Words ofrece un amplio conjunto de funciones para facilitarle la vida.

## Preguntas frecuentes

### ¿Puedo agregar nuevas propiedades a un documento?
 Sí, puedes agregar nuevas propiedades personalizadas usando el`CustomDocumentProperties` recopilación.

### ¿Aspose.Words es de uso gratuito?
 Aspose.Words ofrece una[prueba gratis](https://releases.aspose.com/) y diferente[Opciones de compra](https://purchase.aspose.com/buy).

### ¿Cómo puedo obtener soporte para Aspose.Words?
 Puede obtener soporte de la comunidad Aspose[aquí](https://forum.aspose.com/c/words/8).

### ¿Puedo usar Aspose.Words con otros lenguajes .NET?
Sí, Aspose.Words admite varios lenguajes .NET, incluido VB.NET.

### ¿Dónde puedo encontrar más ejemplos?
 Echa un vistazo a la[Documentación de Aspose.Words para .NET](https://reference.aspose.com/words/net/) para más ejemplos e información detallada.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
