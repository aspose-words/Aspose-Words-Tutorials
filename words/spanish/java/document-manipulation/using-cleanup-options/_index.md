---
title: Uso de opciones de limpieza en Aspose.Words para Java
linktitle: Uso de las opciones de limpieza
second_title: API de procesamiento de documentos Java Aspose.Words
description: Mejore la claridad de los documentos con las opciones de limpieza de Aspose.Words para Java. Aprenda a eliminar párrafos vacíos, regiones no utilizadas y más.
weight: 10
url: /es/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Uso de opciones de limpieza en Aspose.Words para Java


## Introducción al uso de opciones de limpieza en Aspose.Words para Java

En este tutorial, exploraremos cómo usar las opciones de limpieza en Aspose.Words para Java para manipular y limpiar documentos durante el proceso de combinación de correspondencia. Las opciones de limpieza le permiten controlar varios aspectos de la limpieza de documentos, como eliminar párrafos vacíos, regiones no utilizadas y más.

## Prerrequisitos

 Antes de comenzar, asegúrese de tener la biblioteca Aspose.Words para Java integrada en su proyecto. Puede descargarla desde[aquí](https://releases.aspose.com/words/java/).

## Paso 1: Eliminar párrafos vacíos

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insertar campos de combinación
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Establecer opciones de limpieza
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Habilitar la limpieza de párrafos con signos de puntuación
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Ejecutar combinación de correspondencia
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Guardar el documento
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

En este ejemplo, creamos un nuevo documento, insertamos campos de combinación y configuramos las opciones de limpieza para eliminar los párrafos vacíos. Además, habilitamos la eliminación de párrafos con signos de puntuación. Después de ejecutar la combinación de correspondencia, el documento se guarda con la limpieza especificada aplicada.

## Paso 2: eliminar regiones no fusionadas

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Establecer opciones de limpieza para eliminar regiones no utilizadas
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Ejecutar combinación de correspondencia con regiones
doc.getMailMerge().executeWithRegions(data);

// Guardar el documento
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

En este ejemplo, abrimos un documento existente con regiones de fusión, configuramos las opciones de limpieza para eliminar las regiones no utilizadas y, a continuación, ejecutamos la fusión de correspondencia con datos vacíos. Este proceso elimina automáticamente las regiones no utilizadas del documento.

## Paso 3: Eliminar campos vacíos

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Establecer opciones de limpieza para eliminar campos vacíos
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Ejecutar combinación de correspondencia
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Guardar el documento
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

En este ejemplo, abrimos un documento con campos de combinación, configuramos las opciones de limpieza para eliminar los campos vacíos y ejecutamos la combinación de correspondencia con los datos. Después de la combinación, se eliminarán todos los campos vacíos del documento.

## Paso 4: Eliminar campos no utilizados

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Establecer opciones de limpieza para eliminar campos no utilizados
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Ejecutar combinación de correspondencia
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Guardar el documento
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

En este ejemplo, abrimos un documento con campos de combinación, configuramos las opciones de limpieza para eliminar los campos no utilizados y ejecutamos la combinación de correspondencia con los datos. Después de la combinación, se eliminarán del documento todos los campos no utilizados.

## Paso 5: Eliminar campos contenedores

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Establecer opciones de limpieza para eliminar los campos que contienen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Ejecutar combinación de correspondencia
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Guardar el documento
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

En este ejemplo, abrimos un documento con campos de combinación, configuramos las opciones de limpieza para eliminar los campos que los contienen y ejecutamos la combinación de correspondencia con los datos. Después de la combinación, los campos mismos se eliminarán del documento.

## Paso 6: Eliminar filas vacías de la tabla

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Establecer opciones de limpieza para eliminar filas de tablas vacías
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Ejecutar combinación de correspondencia
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Guardar el documento
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

En este ejemplo, abrimos un documento con una tabla y combinamos campos, configuramos las opciones de limpieza para eliminar las filas vacías de la tabla y ejecutamos la combinación de correspondencia con los datos. Después de la combinación, se eliminarán del documento todas las filas vacías de la tabla.

## Conclusión

En este tutorial, aprendió a usar las opciones de limpieza en Aspose.Words para Java para manipular y limpiar documentos durante el proceso de combinación de correspondencia. Estas opciones brindan un control detallado sobre la limpieza de documentos, lo que le permite crear documentos pulidos y personalizados con facilidad.

## Preguntas frecuentes

### ¿Cuáles son las opciones de limpieza en Aspose.Words para Java?

Las opciones de limpieza en Aspose.Words para Java son configuraciones que le permiten controlar varios aspectos de la limpieza del documento durante el proceso de combinación de correspondencia. Le permiten eliminar elementos innecesarios, como párrafos vacíos, regiones no utilizadas y más, lo que garantiza que el documento final esté bien estructurado y pulido.

### ¿Cómo puedo eliminar párrafos vacíos de mi documento?

 Para eliminar párrafos vacíos de su documento usando Aspose.Words para Java, puede configurar el`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` Opción en verdadero. Esto eliminará automáticamente los párrafos que no tengan contenido, lo que dará como resultado un documento más limpio.

###  ¿Cuál es el propósito de la`REMOVE_UNUSED_REGIONS` cleanup option?

 El`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Esta opción se utiliza para eliminar regiones de un documento que no tienen datos correspondientes durante el proceso de combinación de correspondencia. Ayuda a mantener el documento ordenado al eliminar los marcadores de posición no utilizados.

### ¿Puedo eliminar filas de tabla vacías de un documento usando Aspose.Words para Java?

 Sí, puede eliminar filas de tabla vacías de un documento configurando la`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`Establezca la opción de limpieza en verdadera. Esto eliminará automáticamente todas las filas de la tabla que no contengan datos, lo que garantiza una tabla bien estructurada en su documento.

###  ¿Qué sucede cuando configuro el`REMOVE_CONTAINING_FIELDS` option?

 Configuración de la`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` La opción eliminará todo el campo de combinación, incluido el párrafo que lo contiene, del documento durante el proceso de combinación de correspondencia. Esto resulta útil cuando desea eliminar los campos de combinación y el texto asociado.

### ¿Cómo puedo eliminar campos de combinación no utilizados de mi documento?

 Para eliminar campos de combinación no utilizados de un documento, puede configurar la`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` opción en verdadero. Esto eliminará automáticamente los campos de combinación que no se completen durante la combinación de correspondencia, lo que dará como resultado un documento más limpio.

###  ¿Cuál es la diferencia entre`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 El`REMOVE_EMPTY_FIELDS` La opción elimina los campos de combinación que no tienen datos o que están vacíos durante el proceso de combinación de correspondencia. Por otro lado, la opción`REMOVE_UNUSED_FIELDS`La opción elimina los campos de combinación que no se rellenan con datos durante la combinación. La elección entre ellos depende de si desea eliminar los campos sin contenido o aquellos que no se utilizan en la operación de combinación específica.

### ¿Cómo puedo habilitar la eliminación de párrafos con signos de puntuación?

 Para habilitar la eliminación de párrafos con signos de puntuación, puede configurar la`cleanupParagraphsWithPunctuationMarks` Opción en verdadero y especifique los signos de puntuación que se deben tener en cuenta para la limpieza. Esto le permite crear un documento más refinado al eliminar párrafos innecesarios que solo contienen signos de puntuación.

### ¿Puedo personalizar las opciones de limpieza en Aspose.Words para Java?

Sí, puedes personalizar las opciones de limpieza según tus necesidades específicas. Puedes elegir qué opciones de limpieza aplicar y configurarlas según tus requisitos de limpieza de documentos, lo que garantiza que el documento final cumpla con los estándares deseados.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
