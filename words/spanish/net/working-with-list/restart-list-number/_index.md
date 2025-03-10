---
title: Número de lista de reinicio
linktitle: Número de lista de reinicio
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a reiniciar números de listas en documentos de Word con Aspose.Words para .NET. Esta guía detallada de 2000 palabras cubre todo lo que necesita saber, desde la configuración hasta la personalización avanzada.
weight: 10
url: /es/net/working-with-list/restart-list-number/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Número de lista de reinicio

## Introducción

¿Quieres dominar el arte de la manipulación de listas en tus documentos de Word con Aspose.Words para .NET? ¡Pues estás en el lugar correcto! En este tutorial, profundizaremos en el reinicio de números de listas, una función ingeniosa que llevará tus habilidades de automatización de documentos al siguiente nivel. ¡Abróchate el cinturón y comencemos!

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas:

1.  Aspose.Words para .NET: Necesita tener instalado Aspose.Words para .NET. Si aún no lo ha instalado, puede[Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: asegúrese de tener un entorno de desarrollo adecuado, como Visual Studio.
3. Conocimientos básicos de C#: un conocimiento básico de C# le ayudará a seguir el tutorial.

## Importar espacios de nombres

Lo primero es lo primero: importemos los espacios de nombres necesarios. Son fundamentales para acceder a las funciones de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Ahora, desglosaremos el proceso en pasos fáciles de seguir. Cubriremos todo, desde la creación de una lista hasta el reinicio de su numeración.

## Paso 1: Configura tu documento y generador

Antes de poder empezar a manipular listas, necesitas un documento y un DocumentBuilder. DocumentBuilder es tu herramienta preferida para agregar contenido a tu documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Crea y personaliza tu primera lista

A continuación, crearemos una lista basada en una plantilla y personalizaremos su apariencia. En este ejemplo, utilizaremos el formato de número arábigo con paréntesis.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Aquí, configuramos el color de fuente en rojo y alineamos el texto a la derecha.

## Paso 3: Agrega elementos a tu primera lista

 Con la lista lista, es hora de agregar algunos elementos. DocumentBuilder`ListFormat.List` La propiedad ayuda a aplicar el formato de lista al texto.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Paso 4: Reiniciar la numeración de listas

Para reutilizar la lista y reiniciar su numeración, es necesario crear una copia de la lista original. Esto permite modificar la nueva lista de forma independiente.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

En este ejemplo, la nueva lista comienza en el número 10.

## Paso 5: Agregar elementos a la nueva lista

Al igual que antes, agregue elementos a su nueva lista. Esto demuestra que la lista se reinicia en el número especificado.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Paso 6: Guarde su documento

Por último, guarde el documento en el directorio especificado.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusión

Reiniciar los números de listas en documentos de Word con Aspose.Words para .NET es sencillo e increíblemente útil. Ya sea que esté generando informes, creando documentos estructurados o simplemente necesite un mejor control sobre sus listas, esta técnica lo ayudará.

## Preguntas frecuentes

### ¿Puedo utilizar otras plantillas de lista además de NumberArabicParenthesis?

¡Por supuesto! Aspose.Words ofrece varias plantillas de listas, como viñetas, letras, números romanos y más. Puedes elegir la que mejor se adapte a tus necesidades.

### ¿Cómo cambio el nivel de la lista?

 Puede cambiar el nivel de la lista modificando el`ListLevels` propiedad. Por ejemplo,`list1.ListLevels[1]` se referiría al segundo nivel de la lista.

### ¿Puedo reiniciar la numeración en cualquier número?

 Sí, puedes establecer el número inicial en cualquier valor entero usando el`StartAt` propiedad del nivel de lista.

### ¿Es posible tener diferentes formatos para diferentes niveles de lista?

¡Por supuesto! Cada nivel de lista puede tener sus propios ajustes de formato, como fuente, alineación y estilo de numeración.

### ¿Qué pasa si quiero continuar numerando desde una lista anterior en lugar de reiniciar?

Si desea continuar con la numeración, no necesita crear una copia de la lista. Simplemente continúe agregando elementos a la lista original.



{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
