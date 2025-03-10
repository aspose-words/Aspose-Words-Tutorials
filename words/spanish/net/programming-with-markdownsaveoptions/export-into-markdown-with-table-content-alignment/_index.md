---
title: Exportar a Markdown con alineación de contenido de tabla
linktitle: Exportar a Markdown con alineación de contenido de tabla
second_title: API de procesamiento de documentos Aspose.Words
description: Aprenda a exportar documentos de Word a Markdown con tablas alineadas usando Aspose.Words para .NET. Siga nuestra guía paso a paso para obtener tablas Markdown perfectas.
weight: 10
url: /es/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Exportar a Markdown con alineación de contenido de tabla

## Introducción

¡Hola! ¿Alguna vez te preguntaste cómo exportar tu documento de Word al formato Markdown con tablas perfectamente alineadas? Ya seas un desarrollador que trabaja en documentación o simplemente alguien a quien le encanta Markdown, esta guía es para ti. Nos sumergiremos en los detalles del uso de Aspose.Words para .NET para lograrlo. ¿Estás listo para convertir tus tablas de Word en tablas Markdown perfectamente alineadas? ¡Comencemos!

## Prerrequisitos

Antes de sumergirnos en el código, hay algunas cosas que necesitarás tener en cuenta:

1.  Biblioteca Aspose.Words para .NET: asegúrese de tener la biblioteca Aspose.Words para .NET. Puede descargarla desde[Página de lanzamientos de Aspose](https://releases.aspose.com/words/net/).
2. Entorno de desarrollo: configure su entorno de desarrollo. Visual Studio es una opción popular para el desarrollo de .NET.
3. Conocimientos básicos de C#: comprender C# es esencial ya que escribiremos código en este lenguaje.
4. Documento de Word de muestra: Tenga un documento de Word que pueda usar para realizar pruebas.

## Importar espacios de nombres

Antes de comenzar a codificar, importemos los espacios de nombres necesarios. Estos nos darán acceso a las clases y métodos de Aspose.Words que usaremos.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Paso 1: Inicializar el documento y DocumentBuilder

Lo primero es lo primero, necesitamos crear un nuevo documento de Word e inicializar un`DocumentBuilder` objeto para comenzar a construir nuestro documento.

```csharp
// La ruta al directorio de documentos.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Crear un nuevo documento.
Document doc = new Document();

// Inicializar DocumentBuilder.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 2: Insertar celdas y alinear el contenido

A continuación, insertaremos algunas celdas en nuestro documento y estableceremos su alineación. Esto es fundamental para garantizar que la exportación de Markdown conserve la alineación correcta.

```csharp
// Insertar una celda y establecer la alineación a la derecha.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Inserte otra celda y establezca la alineación en el centro.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Paso 3: Establecer la alineación del contenido de la tabla para la exportación de Markdown

 Ahora, es el momento de configurar el`MarkdownSaveOptions` Para controlar la alineación del contenido de la tabla en el archivo Markdown exportado. Guardaremos el documento con diferentes configuraciones de alineación para ver cómo funciona.

```csharp
// Crear objeto MarkdownSaveOptions.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Guardar el documento con alineación a la izquierda.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Cambie la alineación a la derecha y guarde.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Cambie la alineación al centro y guarde.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Paso 4: Utilice la alineación automática del contenido de la tabla

 El`Auto`La opción de alineación toma la alineación del primer párrafo de la columna de la tabla correspondiente. Esto puede resultar útil cuando se tienen alineaciones mixtas en una sola tabla.

```csharp
// Establecer la alineación en Automático.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Guardar documento con alineación automática.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Conclusión

¡Y ya está! Exportar documentos de Word a Markdown con tablas alineadas usando Aspose.Words para .NET es muy fácil una vez que sabes cómo hacerlo. Esta potente biblioteca facilita el control del formato y la alineación de tus tablas, lo que garantiza que tus documentos de Markdown tengan el aspecto que deseas. ¡Que disfrutes codificando!

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?
Aspose.Words para .NET es una potente biblioteca que permite a los desarrolladores crear, modificar, convertir y exportar documentos de Word mediante programación.

### ¿Puedo establecer diferentes alineaciones para diferentes columnas en la misma tabla?
 Sí, mediante el uso del`Auto` Opción de alineación, puede tener diferentes alineaciones según el primer párrafo de cada columna.

### ¿Necesito una licencia para usar Aspose.Words para .NET?
 Sí, Aspose.Words para .NET requiere una licencia para tener todas sus funciones. Puede obtener una[licencia temporal](https://purchase.aspose.com/temporary-license/) para evaluación.

### ¿Es posible exportar otros elementos del documento a Markdown usando Aspose.Words?
Sí, Aspose.Words admite la exportación de varios elementos como encabezados, listas e imágenes al formato Markdown.

### ¿Dónde puedo obtener ayuda si tengo problemas?
 Puede obtener ayuda de la[Foro de soporte de Aspose.Words](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
