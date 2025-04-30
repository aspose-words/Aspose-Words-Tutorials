---
"description": "Aprenda a reiniciar números de lista en documentos de Word con Aspose.Words para .NET. Esta guía detallada de 2000 palabras cubre todo lo que necesita saber, desde la configuración hasta la personalización avanzada."
"linktitle": "Número de lista de reinicio"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Número de lista de reinicio"
"url": "/es/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Número de lista de reinicio

## Introducción

¿Quieres dominar la manipulación de listas en tus documentos de Word con Aspose.Words para .NET? ¡Estás en el lugar correcto! En este tutorial, profundizaremos en el reinicio de números de listas, una función ingeniosa que te permitirá llevar tus habilidades de automatización de documentos al siguiente nivel. ¡Prepárate y comencemos!

## Prerrequisitos

Antes de pasar al código, asegurémonos de que tienes todo lo que necesitas:

1. Aspose.Words para .NET: Necesita tener Aspose.Words para .NET instalado. Si aún no lo ha instalado, puede... [Descárgalo aquí](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: asegúrese de tener un entorno de desarrollo adecuado como Visual Studio.
3. Conocimientos básicos de C#: una comprensión básica de C# le ayudará a seguir el tutorial.

## Importar espacios de nombres

Primero, importemos los espacios de nombres necesarios. Estos son cruciales para acceder a las funciones de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Ahora, desglosemos el proceso en pasos fáciles de seguir. Cubriremos todo, desde la creación de una lista hasta el reinicio de su numeración.

## Paso 1: Configure su documento y generador

Antes de empezar a manipular listas, necesitas un documento y un DocumentBuilder. DocumentBuilder es tu herramienta ideal para añadir contenido a tu documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Crea y personaliza tu primera lista

continuación, crearemos una lista basada en una plantilla y personalizaremos su apariencia. En este ejemplo, usamos el formato de números arábigos con paréntesis.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Aquí, establecemos el color de fuente en rojo y alineamos el texto a la derecha.

## Paso 3: Agrega elementos a tu primera lista

Con la lista lista, es hora de agregar algunos elementos. DocumentBuilder `ListFormat.List` La propiedad ayuda a aplicar el formato de lista al texto.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Paso 4: Reiniciar la numeración de listas

Para reutilizar la lista y reiniciar su numeración, debe crear una copia de la lista original. Esto le permite modificar la nueva lista de forma independiente.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

En este ejemplo, la nueva lista comienza en el número 10.

## Paso 5: Agregar elementos a la nueva lista

Al igual que antes, añade elementos a tu nueva lista. Esto demuestra que la lista se reinicia en el número especificado.

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

Reiniciar la numeración de listas en documentos de Word con Aspose.Words para .NET es sencillo y muy útil. Ya sea que generes informes, crees documentos estructurados o simplemente necesites un mejor control de tus listas, esta técnica te ayudará.

## Preguntas frecuentes

### ¿Puedo utilizar otras plantillas de lista además de NumberArabicParenthesis?

¡Por supuesto! Aspose.Words ofrece varias plantillas de listas, como viñetas, letras, números romanos y más. Puedes elegir la que mejor se adapte a tus necesidades.

### ¿Cómo cambio el nivel de la lista?

Puede cambiar el nivel de la lista modificando el `ListLevels` propiedad. Por ejemplo, `list1.ListLevels[1]` se referiría al segundo nivel de la lista.

### ¿Puedo reiniciar la numeración en cualquier número?

Sí, puedes establecer el número inicial en cualquier valor entero usando el `StartAt` propiedad del nivel de lista.

### ¿Es posible tener diferentes formatos para diferentes niveles de lista?

¡Claro! Cada nivel de lista puede tener sus propios ajustes de formato, como fuente, alineación y estilo de numeración.

### ¿Qué pasa si quiero continuar numerando desde una lista anterior en lugar de reiniciar?

Si desea continuar con la numeración, no necesita crear una copia de la lista. Simplemente siga añadiendo elementos a la lista original.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}