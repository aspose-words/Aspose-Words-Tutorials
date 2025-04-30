---
"description": "Aprenda a usar etiquetas de documento estructurado (SDT) en Aspose.Words para Java con esta guía completa. Cree, modifique y vincule SDT con datos XML personalizados."
"linktitle": "Uso de etiquetas de documentos estructurados (SDT)"
"second_title": "API de procesamiento de documentos Java de Aspose.Words"
"title": "Uso de etiquetas de documento estructurado (SDT) en Aspose.Words para Java"
"url": "/es/java/document-manipulation/using-structured-document-tags/"
"weight": 19
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Uso de etiquetas de documento estructurado (SDT) en Aspose.Words para Java


## Introducción al uso de etiquetas de documento estructurado (SDT) en Aspose.Words para Java

Las etiquetas de documento estructurado (EDE) son una potente función de Aspose.Words para Java que permite crear y manipular contenido estructurado en los documentos. En esta guía completa, le explicaremos los diversos aspectos del uso de las EDE en Aspose.Words para Java. Tanto si es principiante como si es un desarrollador experimentado, encontrará información valiosa y ejemplos prácticos en este artículo.

## Empezando

Antes de profundizar en los detalles, configuremos nuestro entorno y creemos un SDT básico. En esta sección, abordaremos los siguientes temas:

- Creando un nuevo documento
- Agregar una etiqueta de documento estructurado
- Guardando el documento

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Crear una etiqueta de documento estructurado de tipo CHECKBOX
StructuredDocumentTag sdtCheckBox = new StructuredDocumentTag(doc, SdtType.CHECKBOX, MarkupLevel.INLINE);
builder.insertNode(sdtCheckBox);

// Guardar el documento
doc.save("WorkingWithSDT.docx");
```

## Comprobación del estado actual de una casilla de verificación SDT

Una vez que haya añadido un SDT de casilla de verificación a su documento, puede que quiera comprobar su estado actual mediante programación. Esto puede ser útil cuando necesite validar la entrada del usuario o realizar acciones específicas según el estado de la casilla de verificación.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtCheckBox = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtCheckBox.getSdtType() == SdtType.CHECKBOX) {
    // La casilla de verificación está marcada
    sdtCheckBox.setChecked(true);
}

doc.save("UpdatedDocument.docx");
```

## Modificar controles de contenido

En esta sección, exploraremos cómo modificar los controles de contenido de su documento. Abordaremos tres tipos de controles de contenido: texto sin formato, lista desplegable e imagen.

### Modificar el control de contenido de texto sin formato

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPlainText = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtPlainText.getSdtType() == SdtType.PLAIN_TEXT) {
    // Borrar el contenido existente
    sdtPlainText.removeAllChildren();

    // Añadir nuevo texto
    Paragraph para = (Paragraph) sdtPlainText.appendChild(new Paragraph(doc));
    Run run = new Run(doc, "New text goes here");
    para.appendChild(run);
}

doc.save("ModifiedDocument.docx");
```

### Modificar el control de contenido de la lista desplegable

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtDropDown = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

if (sdtDropDown.getSdtType() == SdtType.DROP_DOWN_LIST) {
    // Seleccione el segundo elemento de la lista
    SdtListItem secondItem = sdtDropDown.getListItems().get(2);
    sdtDropDown.getListItems().setSelectedValue(secondItem);
}

doc.save("ModifiedDocument.docx");
```

### Modificar el control del contenido de la imagen

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdtPicture = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);
Shape shape = (Shape) sdtPicture.getChild(NodeType.SHAPE, 0, true);

if (shape.hasImage()) {
    // Reemplazar la imagen por una nueva
    shape.getImageData().setImage("Watermark.png");
}

doc.save("ModifiedDocument.docx");
```

## Creación de un control de contenido de cuadro combinado

Un control de contenido de cuadro combinado permite a los usuarios seleccionar entre una lista predefinida de opciones. Creemos uno en nuestro documento.

```java
Document doc = new Document();
StructuredDocumentTag sdtComboBox = new StructuredDocumentTag(doc, SdtType.COMBO_BOX, MarkupLevel.BLOCK);
sdtComboBox.getListItems().add(new SdtListItem("Choose an item", "-1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 1", "1"));
sdtComboBox.getListItems().add(new SdtListItem("Item 2", "2"));
doc.getFirstSection().getBody().appendChild(sdtComboBox);

doc.save("ComboBoxDocument.docx");
```

## Trabajar con control de contenido de texto enriquecido

Los controles de contenido de texto enriquecido son perfectos para añadir texto con formato a tus documentos. Crea uno y configura su contenido.

```java
Document doc = new Document();
StructuredDocumentTag sdtRichText = new StructuredDocumentTag(doc, SdtType.RICH_TEXT, MarkupLevel.BLOCK);
Paragraph para = new Paragraph(doc);
Run run = new Run(doc);
run.setText("Hello World");
run.getFont().setColor(Color.GREEN);
para.getRuns().add(run);
sdtRichText.getChildNodes().add(para);
doc.getFirstSection().getBody().appendChild(sdtRichText);

doc.save("RichTextDocument.docx");
```

## Configuración de estilos de control de contenido

Puedes aplicar estilos a los controles de contenido para mejorar la apariencia visual de tu documento. Veamos cómo configurar el estilo de un control de contenido.

```java
Document doc = new Document("WorkingWithSDT.docx");
StructuredDocumentTag sdt = (StructuredDocumentTag) doc.getChild(NodeType.STRUCTURED_DOCUMENT_TAG, 0, true);

// Aplicar un estilo personalizado
Style style = doc.getStyles().getByStyleIdentifier(StyleIdentifier.QUOTE);
sdt.setStyle(style);

doc.save("StyledDocument.docx");
```

## Vinculación de un SDT a datos XML personalizados

En algunos casos, puede que necesite vincular un SDT a datos XML personalizados para generar contenido dinámico. Veamos cómo lograrlo.

```java
Document doc = new Document();
CustomXmlPart xmlPart = doc.getCustomXmlParts().add(UUID.randomUUID().toString(), "<root><text>Hello, World!</text></root>");
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.BLOCK);
doc.getFirstSection().getBody().appendChild(sdt);
sdt.getXmlMapping().setMapping(xmlPart, "/root[1]/text[1]", "");

doc.save("CustomXMLBinding.docx");
```

## Creación de una tabla con secciones repetidas asignadas a datos XML personalizados

Las tablas con secciones repetidas pueden ser extremadamente útiles para presentar datos estructurados. Creemos una tabla de este tipo y asignémosla a datos XML personalizados.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
CustomXmlPart xmlPart = doc.getCustomXmlParts().add("Books", "<books>...</books>");
Table table = builder.startTable();
builder.insertCell();
builder.write("Title");
builder.insertCell();
builder.write("Author");
builder.endRow();
builder.endTable();

StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION, MarkupLevel.ROW);
repeatingSectionSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book", "");
table.appendChild(repeatingSectionSdt);

StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.REPEATING_SECTION_ITEM, MarkupLevel.ROW);
repeatingSectionSdt.appendChild(repeatingSectionItemSdt);

Row row = new Row(doc);
repeatingSectionItemSdt.appendChild(row);

StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
titleSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.appendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PLAIN_TEXT, MarkupLevel.CELL);
authorSdt.getXmlMapping().setMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.appendChild(authorSdt);

doc.save("RepeatingTableDocument.docx");
```

## Trabajar con etiquetas de documentos estructurados de varias secciones

Las etiquetas de documento estructurado (EDT) pueden abarcar varias secciones de un documento. En esta sección, exploraremos cómo trabajar con EDE multisección.

```java
Document doc = new Document("MultiSectionDocument.docx");
NodeCollection tags = doc.getChildNodes(NodeType.STRUCTURED_DOCUMENT_TAG_RANGE_START, true);

for (StructuredDocumentTagRangeStart tag : tags) {
    System.out.println(tag.getTitle());
}

doc.save("ModifiedMultiSectionDocument.docx");
```

## Conclusión

Las etiquetas de documento estructurado (EDT) en Aspose.Words para Java ofrecen una forma versátil de gestionar y dar formato al contenido de sus documentos. Ya sea que necesite crear plantillas, formularios o documentos dinámicos, las EDT le ofrecen la flexibilidad y el control que necesita. Siguiendo los ejemplos y las directrices de este artículo, podrá aprovechar al máximo las EDT para optimizar sus tareas de procesamiento de documentos.

## Preguntas frecuentes

### ¿Cuál es el propósito de las etiquetas de documentos estructurados (SDT)?

Las etiquetas de documento estructurado (SDT) sirven para organizar y dar formato al contenido dentro de los documentos, lo que facilita la creación de plantillas, formularios y documentos estructurados.

### ¿Cómo puedo comprobar el estado actual de una casilla de verificación SDT?

Puede comprobar el estado actual de una casilla de verificación SDT utilizando el `setChecked` método, como se demuestra en el artículo.

### ¿Puedo aplicar estilos a los controles de contenido?

Sí, puede aplicar estilos a los controles de contenido para personalizar su apariencia en el documento.

### ¿Es posible vincular un SDT a datos XML personalizados?

Sí, puede vincular un SDT a datos XML personalizados, lo que permite la generación dinámica de contenido y el mapeo de datos.

### ¿Qué son las secciones repetidas en los SDT?

Las secciones repetidas en SDT le permiten crear tablas con datos dinámicos, donde las filas se pueden repetir en función de los datos XML asignados.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}