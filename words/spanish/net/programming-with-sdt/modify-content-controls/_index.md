---
title: Modificar controles de contenido
linktitle: Modificar controles de contenido
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a modificar etiquetas de documentos estructurados en Word con Aspose.Words para .NET. Actualice texto, menús desplegables e imágenes paso a paso.
weight: 10
url: /es/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modificar controles de contenido

## Introducción

Si alguna vez trabajó con documentos de Word y necesitó modificar controles de contenido estructurado (como texto sin formato, listas desplegables o imágenes) con Aspose.Words para .NET, ¡está en el lugar correcto! Las etiquetas de documento estructurado (SDT) son herramientas poderosas que hacen que la automatización de documentos sea más fácil y flexible. En este tutorial, analizaremos en profundidad cómo puede modificar estas SDT para que se ajusten a sus necesidades. Ya sea que esté actualizando texto, cambiando selecciones de menús desplegables o intercambiando imágenes, esta guía lo guiará a través del proceso paso a paso.

## Prerrequisitos

Antes de entrar en los detalles de la modificación de los controles de contenido, asegúrese de tener lo siguiente:

1.  Aspose.Words para .NET instalado: asegúrese de tener instalada la biblioteca Aspose.Words. Si no es así, puede[Descárgalo aquí](https://releases.aspose.com/words/net/).

2. Conocimientos básicos de C#: este tutorial asume que está familiarizado con los conceptos básicos de programación de C#.

3. Un entorno de desarrollo .NET: debe tener un IDE como Visual Studio configurado para ejecutar aplicaciones .NET.

4. Un documento de muestra: usaremos un documento de Word de muestra con varios tipos de SDT. Puede usar el del ejemplo o crear uno propio.

5.  Acceso a la documentación de Aspose: para obtener información más detallada, consulte la[Documentación de Aspose.Words](https://reference.aspose.com/words/net/).

## Importar espacios de nombres

Para comenzar a trabajar con Aspose.Words, debe importar los espacios de nombres correspondientes a su proyecto de C#. A continuación, le indicamos cómo hacerlo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Estos espacios de nombres le darán acceso a las clases y métodos necesarios para manipular etiquetas de documentos estructurados en sus documentos de Word.

## Paso 1: Configurar la ruta del documento

 Antes de realizar cualquier cambio, debe especificar la ruta a su documento. Reemplazar`"YOUR DOCUMENT DIRECTORY"` con la ruta real donde se almacena su documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Paso 2: Recorrer las etiquetas de documentos estructurados

 Para modificar los SDT, primero debe recorrer todos los SDT del documento. Esto se hace usando el comando`GetChildNodes` método para obtener todos los nodos del tipo`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modificar los SDT en función de su tipo
}
```

## Paso 3: Modificar los SDT de texto sin formato

Si el SDT es un tipo de texto sin formato, puede reemplazar su contenido. Primero, borre el contenido existente y luego agregue texto nuevo.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Explicación: Aquí,`RemoveAllChildren()`Borra el contenido existente del SDT. Luego creamos uno nuevo.`Paragraph` y`Run` objeto para insertar el nuevo texto.

## Paso 4: Modificar los SDT de la lista desplegable

 Para los SDT de lista desplegable, puede cambiar el elemento seleccionado accediendo a`ListItems` Colección. Aquí, seleccionamos el tercer elemento de la lista.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Explicación: Este fragmento de código selecciona el elemento en el índice 2 (tercer elemento) de la lista desplegable. Ajuste el índice según sus necesidades.

## Paso 5: Modificar los SDT de imágenes

Para actualizar una imagen dentro de un SDT de imágenes, puede reemplazar la imagen existente por una nueva.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

 Explicación: Este código verifica si la forma contiene una imagen y luego la reemplaza con una nueva imagen ubicada en`ImagesDir`.

## Paso 6: Guarde el documento modificado

Después de realizar todos los cambios necesarios, guarde el documento modificado con un nuevo nombre para mantener intacto el documento original.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Explicación: Esto guarda el documento con un nuevo nombre de archivo para que pueda diferenciarlo fácilmente del original.

## Conclusión

Modificar los controles de contenido en un documento de Word con Aspose.Words para .NET es sencillo una vez que comprende los pasos necesarios. Ya sea que esté actualizando texto, cambiando selecciones de menús desplegables o intercambiando imágenes, Aspose.Words proporciona una API sólida para estas tareas. Si sigue este tutorial, podrá administrar y personalizar de manera eficaz los controles de contenido estructurado de su documento, lo que hará que sus documentos sean más dinámicos y se adapten a sus necesidades.

## Preguntas frecuentes

1. ¿Qué es una etiqueta de documento estructurado (SDT)?

Los SDT son elementos en los documentos de Word que ayudan a administrar y dar formato al contenido del documento, como cuadros de texto, listas desplegables o imágenes.

2. ¿Cómo puedo agregar un nuevo elemento desplegable a un SDT?

 Para agregar un nuevo elemento, utilice el`ListItems` propiedad y agregar una nueva`SdtListItem` A la colección.

3. ¿Puedo usar Aspose.Words para eliminar SDT de un documento?

Sí, puede eliminar SDT accediendo a los nodos del documento y eliminando el SDT deseado.

4. ¿Cómo manejo los SDT que están anidados dentro de otros elementos?

 Utilice el`GetChildNodes` Método con parámetros apropiados para acceder a SDT anidados.

5. ¿Qué debo hacer si el SDT que necesito modificar no está visible en el documento?

Asegúrese de que el SDT no esté oculto ni protegido. Verifique la configuración del documento y asegúrese de que su código esté orientado correctamente al tipo de SDT.


### Código fuente de ejemplo para modificar controles de contenido mediante Aspose.Words para .NET 

```csharp
// Ruta al directorio de su documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

¡Eso es todo! Has modificado con éxito distintos tipos de controles de contenido en tu documento de Word usando Aspose.Words para .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
