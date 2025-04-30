---
"description": "Aprenda a modificar etiquetas de documentos estructurados en Word con Aspose.Words para .NET. Actualice texto, menús desplegables e imágenes paso a paso."
"linktitle": "Modificar controles de contenido"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Modificar controles de contenido"
"url": "/es/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Modificar controles de contenido

## Introducción

Si alguna vez has trabajado con documentos de Word y has necesitado modificar controles de contenido estructurado (como texto sin formato, listas desplegables o imágenes) con Aspose.Words para .NET, ¡estás en el lugar correcto! Las etiquetas de documento estructurado (EDE) son herramientas potentes que facilitan y flexibilizan la automatización de documentos. En este tutorial, te explicaremos cómo modificar estas EDE para adaptarlas a tus necesidades. Ya sea que estés actualizando texto, cambiando las selecciones de los menús desplegables o intercambiando imágenes, esta guía te guiará paso a paso por el proceso.

## Prerrequisitos

Antes de entrar en los detalles de la modificación de los controles de contenido, asegúrese de tener lo siguiente:

1. Aspose.Words para .NET instalado: Asegúrese de tener instalada la biblioteca Aspose.Words. De lo contrario, puede... [Descárgalo aquí](https://releases.aspose.com/words/net/).

2. Conocimientos básicos de C#: este tutorial asume que está familiarizado con los conceptos básicos de programación de C#.

3. Un entorno de desarrollo .NET: debe tener un IDE como Visual Studio configurado para ejecutar aplicaciones .NET.

4. Documento de muestra: Usaremos un documento de Word de muestra con varios tipos de SDT. Puedes usar el del ejemplo o crear el tuyo propio.

5. Acceso a la documentación de Aspose: para obtener información más detallada, consulte la [Documentación de Aspose.Words](https://reference.aspose.com/words/net/).

## Importar espacios de nombres

Para empezar a trabajar con Aspose.Words, necesitas importar los espacios de nombres relevantes a tu proyecto de C#. Así es como se hace:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Estos espacios de nombres le darán acceso a las clases y métodos necesarios para manipular etiquetas de documentos estructurados en sus documentos de Word.

## Paso 1: Configure la ruta de su documento

Antes de realizar cualquier cambio, debe especificar la ruta de su documento. Reemplazar `"YOUR DOCUMENT DIRECTORY"` con la ruta real donde se almacena su documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Paso 2: Recorrer las etiquetas de documentos estructurados

Para modificar las SDT, primero debe recorrer todas las SDT del documento. Esto se hace usando el `GetChildNodes` método para obtener todos los nodos de tipo `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Modificar los SDT según su tipo
}
```

## Paso 3: Modificar los SDT de texto sin formato

Si el SDT es de texto sin formato, puede reemplazar su contenido. Primero, borre el contenido existente y luego agregue texto nuevo.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Explicación:Aquí, `RemoveAllChildren()` Borra el contenido existente del SDT. Luego creamos uno nuevo. `Paragraph` y `Run` objeto para insertar el nuevo texto.

## Paso 4: Modificar los SDT de la lista desplegable

Para los SDT de lista desplegable, puede cambiar el elemento seleccionado accediendo a la `ListItems` Colección. Aquí, seleccionamos el tercer elemento de la lista.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Explicación: Este fragmento de código selecciona el elemento con el índice 2 (tercer elemento) de la lista desplegable. Ajuste el índice según sus necesidades.

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

Explicación: Este código verifica si la forma contiene una imagen y luego la reemplaza con una nueva imagen ubicada en `ImagesDir`.

## Paso 6: Guarde el documento modificado

Después de realizar todos los cambios necesarios, guarde el documento modificado con un nuevo nombre para mantener intacto el documento original.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Explicación: Esto guarda el documento con un nuevo nombre de archivo para que pueda diferenciarlo fácilmente del original.

## Conclusión

Modificar los controles de contenido en un documento de Word con Aspose.Words para .NET es sencillo una vez que comprende los pasos. Ya sea que esté actualizando texto, cambiando las selecciones de los menús desplegables o intercambiando imágenes, Aspose.Words proporciona una API robusta para estas tareas. Siguiendo este tutorial, podrá administrar y personalizar eficazmente los controles de contenido estructurado de su documento, haciéndolos más dinámicos y adaptados a sus necesidades.

## Preguntas frecuentes

1. ¿Qué es una etiqueta de documento estructurado (SDT)?

Los SDT son elementos en los documentos de Word que ayudan a administrar y dar formato al contenido del documento, como cuadros de texto, listas desplegables o imágenes.

2. ¿Cómo puedo agregar un nuevo elemento desplegable a un SDT?

Para agregar un nuevo elemento, utilice el `ListItems` propiedad y añadir una nueva `SdtListItem` A la colección.

3. ¿Puedo usar Aspose.Words para eliminar SDT de un documento?

Sí, puede eliminar SDT accediendo a los nodos del documento y eliminando el SDT deseado.

4. ¿Cómo manejo los SDT que están anidados dentro de otros elementos?

Utilice el `GetChildNodes` Método con parámetros apropiados para acceder a SDT anidados.

5. ¿Qué debo hacer si el SDT que necesito modificar no está visible en el documento?

Asegúrese de que el SDT no esté oculto ni protegido. Revise la configuración del documento y asegúrese de que su código esté dirigido correctamente al tipo de SDT.


### Código fuente de ejemplo para modificar controles de contenido usando Aspose.Words para .NET 

```csharp
// Ruta a su directorio de documentos 
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

¡Listo! Has modificado correctamente diferentes tipos de controles de contenido en tu documento de Word con Aspose.Words para .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}