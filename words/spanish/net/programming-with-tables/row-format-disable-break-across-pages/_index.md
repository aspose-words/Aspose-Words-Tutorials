---
"description": "Aprenda a deshabilitar los saltos de fila en las páginas de documentos de Word usando Aspose.Words para .NET para mantener la legibilidad y el formato de la tabla."
"linktitle": "Formato de fila Deshabilitar salto entre páginas"
"second_title": "API de procesamiento de documentos de Aspose.Words"
"title": "Formato de fila Deshabilitar salto entre páginas"
"url": "/es/net/programming-with-tables/row-format-disable-break-across-pages/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formato de fila Deshabilitar salto entre páginas

## Introducción

Al trabajar con tablas en documentos de Word, conviene asegurarse de que las filas no se dividan entre páginas, lo cual es esencial para mantener la legibilidad y el formato de los documentos. Aspose.Words para .NET ofrece una forma sencilla de desactivar los saltos de fila entre páginas.

En este tutorial, lo guiaremos a través del proceso de deshabilitar saltos de fila en las páginas de un documento de Word usando Aspose.Words para .NET.

## Prerrequisitos

Antes de comenzar, asegúrese de tener los siguientes requisitos previos:
- Biblioteca Aspose.Words para .NET instalada.
- Un documento de Word con una tabla que ocupa varias páginas.

## Importar espacios de nombres

Primero, importe los espacios de nombres necesarios en su proyecto:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Paso 1: Cargar el documento

Cargue el documento que contiene la tabla que abarca varias páginas.

```csharp
// Ruta a su directorio de documentos 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

## Paso 2: Acceder a la tabla

Acceda a la primera tabla del documento. Esto supone que la tabla que desea modificar es la primera del documento.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

## Paso 3: Deshabilitar la división entre páginas para todas las filas

Recorra cada fila de la tabla y establezca el `AllowBreakAcrossPages` propiedad a `false`Esto garantiza que las filas no se dividan entre páginas.

```csharp
// Deshabilitar la división entre páginas para todas las filas de la tabla.
foreach (Row row in table.Rows)
    row.RowFormat.AllowBreakAcrossPages = false;
```

## Paso 4: Guardar el documento

Guarde el documento modificado en el directorio especificado.

```csharp
doc.Save(dataDir + "WorkingWithTables.RowFormatDisableBreakAcrossPages.docx");
```

## Conclusión

En este tutorial, mostramos cómo deshabilitar los saltos de fila entre páginas en un documento de Word con Aspose.Words para .NET. Siguiendo los pasos descritos anteriormente, puede garantizar que las filas de su tabla permanezcan intactas y no se dividan entre páginas, manteniendo así la legibilidad y el formato del documento.

## Preguntas frecuentes

### ¿Puedo desactivar los saltos de fila en las páginas para una fila específica en lugar de para todas las filas?  
Sí, puede deshabilitar los saltos de fila para filas específicas accediendo a la fila deseada y configurando su `AllowBreakAcrossPages` propiedad a `false`.

### ¿Este método funciona para tablas con celdas fusionadas?  
Sí, este método funciona para tablas con celdas fusionadas. La propiedad `AllowBreakAcrossPages` se aplica a toda la fila, independientemente de la fusión de celdas.

### ¿Funcionará este método si la tabla está anidada dentro de otra tabla?  
Sí, puede acceder y modificar tablas anidadas de la misma manera. Asegúrese de referenciar correctamente la tabla anidada por su índice u otras propiedades.

### ¿Cómo puedo comprobar si una fila permite dividirse en varias páginas?  
Puede comprobar si una fila permite dividirla entre páginas accediendo a la `AllowBreakAcrossPages` propiedad de la `RowFormat` y comprobar su valor.

### ¿Hay alguna manera de aplicar esta configuración a todas las tablas de un documento?  
Sí, puede recorrer todas las tablas del documento y aplicar esta configuración a cada una.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}