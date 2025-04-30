---
"description": "Aprenda a agregar y personalizar encabezados y pies de página en documentos de Word con Aspose.Words para .NET. Esta guía paso a paso garantiza un formato profesional de los documentos."
"linktitle": "Crear encabezado y pie de página"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Crear encabezado y pie de página"
"url": "/es/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crear encabezado y pie de página

## Introducción

Añadir encabezados y pies de página a sus documentos puede mejorar su profesionalidad y legibilidad. Con Aspose.Words para .NET, puede crear y personalizar fácilmente encabezados y pies de página para sus documentos de Word. En este tutorial, le guiaremos paso a paso por el proceso, asegurándose de que pueda implementar estas funciones sin problemas.

## Prerrequisitos

Antes de comenzar, asegúrese de tener lo siguiente:

- Aspose.Words para .NET: Descargar e instalar desde [enlace de descarga](https://releases.aspose.com/words/net/).
- Entorno de desarrollo: como Visual Studio, para escribir y ejecutar su código.
- Conocimientos básicos de C#: comprensión de C# y .NET Framework.
- Documento de muestra: Un documento de muestra para aplicar los encabezados y pies de página, o crear uno nuevo como se muestra en el tutorial.

## Importar espacios de nombres

Primero, debe importar los espacios de nombres necesarios para acceder a las clases y métodos de Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Paso 1: Definir el directorio del documento

Define el directorio donde se guardará tu documento. Esto facilita la gestión de la ruta.

```csharp
// La ruta al directorio de documentos
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Paso 2: Crear un nuevo documento

Crea un nuevo documento y un `DocumentBuilder` para facilitar la adición de contenido.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Paso 3: Configurar la configuración de la página

Configure los ajustes de la página, incluso si la primera página tendrá un encabezado/pie de página diferente.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Paso 4: Agregar un encabezado a la primera página

Vaya a la sección de encabezado de la primera página y configure el texto del encabezado.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Paso 5: Agregar un encabezado principal

Vaya a la sección del encabezado principal e inserte una imagen y texto.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Insertar una imagen en el encabezado
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Paso 6: Agregar un pie de página principal

Vaya a la sección de pie de página principal y cree una tabla para dar formato al contenido del pie de página.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Añadir numeración de páginas
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Paso 7: Agregar contenido y saltos de página

Vaya al final del documento, agregue un salto de página y cree una nueva sección con diferentes configuraciones de página.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Paso 8: Copiar encabezados y pies de página de la sección anterior

Si desea reutilizar encabezados y pies de página de una sección anterior, cópielos y aplique las modificaciones necesarias.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Conclusión

Siguiendo estos pasos, puede agregar y personalizar eficazmente encabezados y pies de página en sus documentos de Word con Aspose.Words para .NET. Esto mejora la apariencia y el profesionalismo de su documento, haciéndolo más legible y atractivo.

## Preguntas frecuentes

### ¿Qué es Aspose.Words para .NET?

Aspose.Words para .NET es una biblioteca que permite a los desarrolladores crear, editar y convertir documentos de Word mediante programación dentro de aplicaciones .NET.

### ¿Puedo agregar imágenes al encabezado o pie de página?

Sí, puedes agregar imágenes fácilmente al encabezado o pie de página usando el `DocumentBuilder.InsertImage` método.

### ¿Cómo configuro diferentes encabezados y pies de página para la primera página?

Puede configurar diferentes encabezados y pies de página para la primera página utilizando el `DifferentFirstPageHeaderFooter` propiedad de la `PageSetup` clase.

### ¿Dónde puedo encontrar más documentación sobre Aspose.Words?

Puede encontrar documentación completa en el [Página de documentación de la API de Aspose.Words](https://reference.aspose.com/words/net/).

### ¿Hay soporte disponible para Aspose.Words?

Sí, Aspose ofrece soporte a través de su [foro de soporte](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}