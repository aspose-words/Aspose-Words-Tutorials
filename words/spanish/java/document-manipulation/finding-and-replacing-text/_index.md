---
title: Búsqueda y reemplazo de texto en Aspose.Words para Java
linktitle: Búsqueda y reemplazo de texto
second_title: API de procesamiento de documentos Java Aspose.Words
description: Aprenda a buscar y reemplazar texto en documentos de Word con Aspose.Words para Java. Guía paso a paso con ejemplos de código. Mejore sus habilidades de manipulación de documentos Java.
weight: 15
url: /es/java/document-manipulation/finding-and-replacing-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Búsqueda y reemplazo de texto en Aspose.Words para Java


## Introducción a la búsqueda y reemplazo de texto en Aspose.Words para Java

Aspose.Words para Java es una potente API de Java que le permite trabajar con documentos de Word de forma programática. Una de las tareas habituales al trabajar con documentos de Word es buscar y reemplazar texto. Ya sea que necesite actualizar marcadores de posición en plantillas o realizar manipulaciones de texto más complejas, Aspose.Words para Java puede ayudarlo a lograr sus objetivos de manera eficiente.

## Prerrequisitos

Antes de profundizar en los detalles de cómo buscar y reemplazar texto, asegúrese de tener los siguientes requisitos previos:

- Entorno de desarrollo Java
- Biblioteca Aspose.Words para Java
- Un documento de Word de muestra con el que trabajar

 Puede descargar la biblioteca Aspose.Words para Java desde[aquí](https://releases.aspose.com/words/java/).

## Cómo buscar y reemplazar texto simple

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Crear un DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Buscar y reemplazar texto
builder.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Guardar el documento modificado
doc.save("modified-document.docx");
```

 En este ejemplo, cargamos un documento de Word, creamos un`DocumentBuilder` , y utiliza el`replace` método para buscar y reemplazar "texto antiguo" con "texto nuevo" dentro del documento.

## Uso de expresiones regulares

Las expresiones regulares proporcionan potentes capacidades de búsqueda y reemplazo de patrones para la búsqueda y el reemplazo de texto. Aspose.Words para Java admite expresiones regulares para operaciones de búsqueda y reemplazo más avanzadas.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Crear un DocumentBuilder
DocumentBuilder builder = new DocumentBuilder(doc);

// Utilice expresiones regulares para buscar y reemplazar texto
Pattern regex = Pattern.compile("your-pattern");
builder.getRange().replace(regex, "replacement-text", new FindReplaceOptions());

// Guardar el documento modificado
doc.save("modified-document.docx");
```

En este ejemplo, utilizamos un patrón de expresión regular para buscar y reemplazar texto dentro del documento.

## Ignorar texto dentro de los campos

Puede configurar Aspose.Words para ignorar el texto dentro de los campos al realizar operaciones de búsqueda y reemplazo.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions y configure IgnoreFields como verdadero
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreFields(true);

// Utilice opciones al reemplazar texto
doc.getRange().replace("text-to-replace", "new-text", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto es útil cuando desea excluir texto dentro de campos, como campos de combinación, para que no sea reemplazado.

## Ignorar texto dentro de Eliminar revisiones

Puede configurar Aspose.Words para ignorar el texto dentro de las revisiones eliminadas durante las operaciones de búsqueda y reemplazo.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions y configure IgnoreDeleted como verdadero
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreDeleted(true);

// Utilice opciones al reemplazar texto
doc.getRange().replace("text-to-replace", "new-text", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite excluir el texto que ha sido marcado para su eliminación en los cambios registrados para que no sea reemplazado.

## Ignorar texto dentro de las revisiones de inserción

Puede configurar Aspose.Words para ignorar el texto dentro de las revisiones de inserción durante las operaciones de búsqueda y reemplazo.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions y configure IgnoreInserted como verdadero
FindReplaceOptions options = new FindReplaceOptions();
options.setIgnoreInserted(true);

// Utilice opciones al reemplazar texto
doc.getRange().replace("text-to-replace", "new-text", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite excluir el texto que ha sido marcado como insertado en los cambios controlados para que no sea reemplazado.

## Reemplazar texto con HTML

Puede utilizar Aspose.Words para Java para reemplazar texto con contenido HTML.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions con una devolución de llamada de reemplazo personalizada
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceWithHtmlEvaluator(options));

// Utilice opciones al reemplazar texto
doc.getRange().replace("text-to-replace", "new-html-content", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

 En este ejemplo, utilizamos un personalizado`ReplaceWithHtmlEvaluator` para reemplazar texto con contenido HTML.

## Reemplazo de texto en encabezados y pies de página

Puede buscar y reemplazar texto dentro de los encabezados y pies de página de su documento de Word.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Obtenga la colección de encabezados y pies de página
HeaderFooterCollection headersFooters = doc.getFirstSection().getHeadersFooters();

// Elija el tipo de encabezado o pie de página en el que desea reemplazar el texto (por ejemplo, HeaderFooterType.FOOTER_PRIMARY)
HeaderFooter footer = headersFooters.getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);

// Cree una instancia de FindReplaceOptions y aplíquela al rango del pie de página
FindReplaceOptions options = new FindReplaceOptions();
footer.getRange().replace("text-to-replace", "new-text", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite realizar reemplazos de texto específicamente en encabezados y pies de página.

## Cómo mostrar cambios en los pedidos de encabezado y pie de página

Puede utilizar Aspose.Words para mostrar cambios en los órdenes de encabezado y pie de página en su documento.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Obtenga la primera sección
Section firstPageSection = doc.getFirstSection();

//Cree una instancia de FindReplaceOptions y aplíquela al rango del documento
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceLog());

// Reemplazar el texto que afecta el orden del encabezado y pie de página
doc.getRange().replace(Pattern.compile("(header|footer)"), "", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite visualizar los cambios relacionados con el orden de encabezado y pie de página en su documento.

## Reemplazar texto con campos

Puede reemplazar texto con campos usando Aspose.Words para Java.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions y configure una devolución de llamada de reemplazo personalizada para los campos
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new ReplaceTextWithFieldHandler(FieldType.FIELD_MERGE_FIELD));

// Utilice opciones al reemplazar texto
doc.getRange().replace(Pattern.compile("PlaceHolder(\\d+)"), "", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

 En este ejemplo, reemplazamos el texto con campos y especificamos el tipo de campo (por ejemplo,`FieldType.FIELD_MERGE_FIELD`).

## Reemplazar por un evaluador

Puede utilizar un evaluador personalizado para determinar el texto de reemplazo de forma dinámica.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions y configure una devolución de llamada de reemplazo personalizada
FindReplaceOptions options = new FindReplaceOptions();
options.setReplacingCallback(new MyReplaceEvaluator());

// Utilice opciones al reemplazar texto
doc.getRange().replace(Pattern.compile("[s|m]ad"), "", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

En este ejemplo, utilizamos un evaluador personalizado (`MyReplaceEvaluator`) para reemplazar el texto.

## Reemplazar con expresiones regulares

Aspose.Words para Java le permite reemplazar texto utilizando expresiones regulares.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Utilice expresiones regulares para buscar y reemplazar texto
doc.getRange().replace(Pattern.compile("[s|m]ad"), "bad", new FindReplaceOptions());

// Guardar el documento modificado
doc.save("modified-document.docx");
```

En este ejemplo, utilizamos un patrón de expresión regular para buscar y reemplazar texto dentro del documento.

## Reconocimiento y sustituciones dentro de patrones de reemplazo

Puede reconocer y realizar sustituciones dentro de patrones de reemplazo utilizando Aspose.Words para Java.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions con UseSubstitutions establecido en verdadero
FindReplaceOptions options = new FindReplaceOptions();
options.setUseSubstitutions(true);

// Utilice opciones al reemplazar texto con un patrón
doc.getRange().replace(Pattern.compile("([A-z]+) give money to ([A-z]+)"), "$2 take money from $1", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite realizar sustituciones dentro de los patrones de reemplazo para reemplazos más avanzados.

## Reemplazar con una cadena

Puede reemplazar texto con una cadena simple usando Aspose.Words para Java.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Reemplazar texto con una cadena
doc.getRange().replace("text-to-replace", "new-string", new FindReplaceOptions());

// Guardar el documento modificado
doc.save("modified-document.docx");
```

En este ejemplo, reemplazamos "text-to-replace" con "new-string" dentro del documento.

## Uso de la orden heredada

Puede utilizar el orden heredado al realizar operaciones de búsqueda y reemplazo.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Cree una instancia de FindReplaceOptions y configure UseLegacyOrder como verdadero
FindReplaceOptions options = new FindReplaceOptions();
options.setUseLegacyOrder(true);

// Utilice opciones al reemplazar texto
doc.getRange().replace(Pattern.compile("\\[(.*?)\\]"), "", options);

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite utilizar el orden heredado para operaciones de búsqueda y reemplazo.

## Reemplazar texto en una tabla

Puede buscar y reemplazar texto dentro de tablas en su documento de Word.

```java
// Cargar el documento
Document doc = new Document("your-document.docx");

// Obtener una tabla específica (por ejemplo, la primera tabla)
Table table = (Table) doc.getChild(NodeType.TABLE, 0, true);

//Utilice FindReplaceOptions para reemplazar texto en la tabla
table.getRange().replace("old-text", "new-text", new FindReplaceOptions());

// Guardar el documento modificado
doc.save("modified-document.docx");
```

Esto le permite realizar reemplazos de texto específicamente dentro de las tablas.

## Conclusión

Aspose.Words para Java ofrece funciones integrales para buscar y reemplazar texto en documentos de Word. Ya sea que necesite realizar reemplazos de texto simples u operaciones más avanzadas mediante expresiones regulares, manipulaciones de campos o evaluadores personalizados, Aspose.Words para Java lo tiene cubierto. Asegúrese de explorar la extensa documentación y los ejemplos que ofrece Aspose para aprovechar todo el potencial de esta poderosa biblioteca de Java.

## Preguntas frecuentes

### ¿Cómo descargo Aspose.Words para Java?

 Puede descargar Aspose.Words para Java desde el sitio web visitando[Este enlace](https://releases.aspose.com/words/java/).

### ¿Puedo usar expresiones regulares para reemplazar texto?

Sí, puede utilizar expresiones regulares para reemplazar texto en Aspose.Words para Java. Esto le permite realizar operaciones de búsqueda y reemplazo más avanzadas y flexibles.

### ¿Cómo puedo ignorar el texto dentro de los campos durante el reemplazo?

Para ignorar el texto dentro de los campos durante el reemplazo, puede configurar la`IgnoreFields` propiedad de la`FindReplaceOptions` a`true`Esto garantiza que el texto dentro de los campos, como los campos de combinación, se excluya del reemplazo.

### ¿Puedo reemplazar el texto dentro de los encabezados y pies de página?

 Sí, puedes reemplazar el texto dentro de los encabezados y pies de página de tu documento de Word. Simplemente accede al encabezado o pie de página correspondiente y usa el`replace` método con el deseado`FindReplaceOptions`.

### ¿Para qué sirve la opción UseLegacyOrder?

 El`UseLegacyOrder` Opción en`FindReplaceOptions` Permite utilizar el orden heredado al realizar operaciones de búsqueda y reemplazo. Esto puede resultar útil en determinadas situaciones en las que se desea un comportamiento del orden heredado.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
