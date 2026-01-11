---
date: 2026-01-11
description: Aprenda cómo limpiar un documento de Word usando las opciones de limpieza
  de Aspose.Words para Java, incluyendo la eliminación de párrafos vacíos, filas de
  tabla vacías y campos no utilizados.
linktitle: Using Cleanup Options
second_title: Aspose.Words Java Document Processing API
title: Limpiar documento Word con las opciones de limpieza de Aspose.Words (Java)
url: /es/java/document-manipulation/using-cleanup-options/
weight: 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Limpiar documento Word usando opciones de limpieza de Aspose.Words (Java)

En este tutorial descubrirás cómo **limpiar documentos Word** con Aspose.Words para Java. Ya sea que estés generando facturas, contratos o informes masivos de combinación de correspondencia, los párrafos vacíos no deseados, los campos sin usar o las filas de tabla en blanco pueden hacer que el resultado final se vea poco profesional. Recorreremos cada opción de limpieza paso a paso, te mostraremos el código exacto que necesitas y explicaremos *por qué* cada configuración es importante para que puedas producir documentos pulidos cada vez.

## Respuestas rápidas
- **¿Qué significa “limpiar documento Word”?** Eliminar párrafos vacíos, regiones de combinación sin usar, filas de tabla vacías y otros elementos redundantes después de una operación de combinación de correspondencia.  
- **¿Qué opción de limpieza elimina los párrafos vacíos?** `MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS`.  
- **¿Cómo puedo borrar filas de tabla vacías?** Usa `MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`.  
- **¿Puedo deshacerme de los campos que nunca se rellenaron?** Sí – `MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` o `REMOVE_EMPTY_FIELDS`.  
- **¿Necesito una licencia para ejecutar estos ejemplos?** Una prueba gratuita sirve para evaluación; se requiere una licencia comercial para uso en producción.

## ¿Qué es “limpiar documento Word” en el contexto de la combinación de correspondencia?
Cuando realizas una combinación de correspondencia, Aspose.Words inserta datos en campos y regiones de combinación. Si algunos campos reciben `null` o cadenas vacías, el documento puede terminar con párrafos errantes, tablas vacías o regiones de marcador de posición. Las **opciones de limpieza** eliminan automáticamente estos artefactos, dejando un documento limpio y listo para imprimir.

## ¿Por qué usar opciones de limpieza?
- **Apariencia profesional:** Sin líneas en blanco ni tablas huérfanas.  
- **Tamaño de archivo reducido:** Eliminar elementos no usados disminuye el peso del documento.  
- **Procesamiento posterior simplificado:** Los documentos limpios son más fáciles de convertir a PDF, HTML u otros formatos.  
- **Ahorro de tiempo:** Configuraciones de una sola línea reemplazan scripts manuales de post‑procesamiento.

## Requisitos previos
- Entorno de desarrollo Java (JDK 8+).  
- Biblioteca Aspose.Words para Java – descárgala [aquí](https://releases.aspose.com/words/java/).  
- Familiaridad básica con los conceptos de combinación de correspondencia.

## Guía paso a paso

### Paso 1: Cómo eliminar párrafos vacíos (Java)
Primero, mostraremos cómo eliminar los párrafos que no contienen texto visible. Esto es especialmente útil cuando un campo de combinación se resuelve a `null`.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert merge fields
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Set cleanup options
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Enable cleanup of paragraphs that contain only punctuation marks
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Execute mail merge (both fields are null, so they become empty)
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

**¿Qué ocurre aquí?**  
- `REMOVE_EMPTY_PARAGRAPHS` indica a Aspose.Words que elimine cualquier párrafo que quede vacío después de la combinación.  
- Habilitar `cleanupParagraphsWithPunctuationMarks` también elimina los párrafos que consisten únicamente en signos de puntuación (p. ej., “?”).

### Paso 2: Cómo eliminar regiones no combinadas
Si una región de combinación no tiene datos correspondientes, puedes descartarla por completo.

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Set cleanup options to remove unused regions
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Execute mail merge with regions (the DataSet is empty)
doc.getMailMerge().executeWithRegions(data);

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

**Por qué es importante:**  
Las regiones no usadas a menudo dejan secciones en blanco o encabezados errantes. La bandera `REMOVE_UNUSED_REGIONS` las limpia automáticamente.

### Paso 3: Cómo eliminar campos vacíos
Cuando un campo recibe una cadena vacía, puede que quieras eliminar todo el campo en lugar de dejar un marcador de posición vacío.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Execute mail merge with a mix of populated and empty values
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

### Paso 4: Cómo eliminar campos no usados
Si ciertos campos nunca se referencian durante la combinación, puedes eliminarlos completamente.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove unused fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

### Paso 5: Cómo eliminar campos contenedores
A veces un campo de combinación está dentro de un párrafo que también deseas descartar.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove containing fields
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

### Paso 6: Cómo eliminar filas de tabla vacías
Las tablas a menudo terminan con filas que solo contienen campos vacíos. Esta opción poda esas filas.

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Set cleanup options to remove empty table rows
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Execute mail merge
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Save the cleaned document
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

## Problemas comunes y solución de errores
- **Los párrafos no se eliminan:** Asegúrate de que `setCleanupParagraphsWithPunctuationMarks(true)` se invoque *después* de establecer la opción de limpieza.  
- **Las filas de tabla vacías persisten:** Verifica que las celdas de la tabla contengan realmente cadenas vacías (no espacios en blanco).  
- **Los campos no usados permanecen:** Revisa que estés usando el enum correcto (`REMOVE_UNUSED_FIELDS`) y que los campos de combinación no se estén rellenando accidentalmente en otro lugar.

## Preguntas frecuentes

**P: ¿Cuál es la diferencia entre `REMOVE_EMPTY_FIELDS` y `REMOVE_UNUSED_FIELDS`?**  
R: `REMOVE_EMPTY_FIELDS` elimina los campos que reciben una cadena vacía o `null` durante la combinación, mientras que `REMOVE_UNUSED_FIELDS` elimina los campos que nunca fueron referenciados por la operación de combinación.

**P: ¿Puedo combinar múltiples opciones de limpieza?**  
R: Sí. El método `setCleanupOptions` acepta una combinación OR bit a bit de los valores del enum, lo que permite limpiar párrafos, tablas y regiones en una sola llamada.

**P: ¿Activar `cleanupParagraphsWithPunctuationMarks` afecta al texto normal?**  
R: Solo elimina los párrafos que consisten exclusivamente en caracteres de puntuación (p. ej., “?” o “---”). Las oraciones regulares permanecen sin cambios.

**P: ¿Es posible personalizar qué signos de puntuación se consideran?**  
R: La API actual usa un conjunto predefinido de caracteres de puntuación. Para un comportamiento personalizado, tendrías que post‑procesar el documento después de la combinación.

**P: ¿Estas opciones de limpieza funcionan con la conversión a PDF?**  
R: Absolutamente. Una vez que el documento Word está limpio, puedes convertirlo a PDF, HTML o cualquier otro formato compatible sin trasladar los elementos no deseados.

## Conclusión
Ahora dispones de un conjunto completo de herramientas para **limpiar documentos Word** durante la combinación de correspondencia con Aspose.Words para Java. Seleccionando las `MailMergeCleanupOptions` adecuadas, puedes eliminar automáticamente párrafos vacíos, filas de tabla vacías, campos no usados y más, obteniendo un documento elegante y listo para producción cada vez.

---

**Última actualización:** 2026-01-11  
**Probado con:** Aspose.Words para Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}