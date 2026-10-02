---
category: general
date: 2026-02-21
description: Ocultar fila en una tabla usando C# y Aspose.Words. Aprende cómo ocultar
  una fila, cómo ocultar una fila en Word y eliminar una fila de la tabla de forma
  rápida y segura.
draft: false
keywords:
- hide row in table
- how to hide row
- remove row from table
- hide row in word
- hide row c#
language: es
og_description: Ocultar fila en una tabla usando C# y Aspose.Words. Esta guía muestra
  cómo ocultar una fila, eliminar una fila de la tabla y ocultar una fila en documentos
  de Word.
og_title: Ocultar fila en tabla con C# – Método rápido y fiable
tags:
- C#
- Aspose.Words
- Word Automation
title: Ocultar fila en una tabla con C# – Guía sencilla para eliminar filas de tabla
url: /es/net/programming-with-tables/hide-row-in-table-with-c-simple-guide-to-removing-table-rows/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ocultar fila en tabla – Tutorial completo de C#

¿Alguna vez necesitaste **ocultar fila en tabla** mientras generas un documento Word de forma programática? No eres el único—los desarrolladores preguntan constantemente *cómo ocultar fila* sin romper el diseño. ¿La buena noticia? Con unas pocas líneas de C# y la potente biblioteca Aspose.Words, puedes ocultar una fila, eliminándola efectivamente del resultado final, y mantener tu código limpio.

En esta guía recorreremos todo el proceso: cargar un `.docx`, seleccionar la fila exacta, establecer su propiedad `Hidden` y guardar el resultado. Al final sabrás exactamente cómo **ocultar fila en Word**, cómo **eliminar fila de tabla** si prefieres la supresión, y tendrás un fragmento listo‑para‑ejecutar que puedes insertar en cualquier proyecto .NET. No se requieren referencias externas—solo el código y explicaciones claras.

**Lo que obtendrás**  
- Un recorrido paso a paso de la API de C#.  
- Código completo y ejecutable (incluyendo importaciones).  
- Consejos para casos límite como filas ocultas en celdas combinadas.  
- Tips profesionales sobre cuándo *ocultar fila* vs. *eliminar fila de tabla*.

> **Prerequisite:** Visual Studio (o cualquier IDE de C#) y el paquete NuGet Aspose.Words for .NET (versión 23.9 o posterior). Si eres nuevo en Aspose.Words, la biblioteca es una solución totalmente administrada—no se necesita instalación de Office.

---

## Ocultar fila en tabla – Implementación paso a paso

A continuación tienes el ejemplo completo y autónomo. Demuestra la tarea **principal**—*ocultar fila en tabla*—y también muestra cómo podrías *eliminar fila de tabla* si decides borrarla.

![Ejemplo de ocultar fila en tabla](hide-row-in-table.png "Captura de pantalla que muestra una tabla Word con la tercera fila oculta")

### 1. Cargar el documento fuente  

Primero, necesitamos cargar el archivo Word en memoria. La clase `Document` representa todo el archivo.

```csharp
using Aspose.Words;

// Step 1: Load the source document
Document doc = new Document(@"C:\MyDocs\input.docx");
```

*Why this matters:* Cargar el documento te da acceso a secciones, cuerpos y tablas. Sin este paso no puedes manipular filas en absoluto.

### 2. Localizar la tabla deseada  

Para simplificar, tomamos la primera tabla de la primera sección, pero puedes buscar por índice, nombre o incluso contenido.

```csharp
// Step 2: Get the first table in the document body
Table table = doc.FirstSection.Body.Tables[0];
```

> **Tip:** Si tu documento tiene varias tablas, itera `doc.GetChildNodes(NodeType.Table, true)` y elige la que necesites.

### 3. Elegir la fila que deseas ocultar  

Aquí apuntamos a la tercera fila (índice base cero `2`). También podrías usar `Rows.Count` para verificar que el índice exista.

```csharp
// Step 3: Choose the row you want to hide (third row, index 2)
Row rowToHide = table.Rows[2];
```

*Why this matters:* Seleccionar la fila correcta es el núcleo de **cómo ocultar fila**. Equivocar el índice ocultará el contenido equivocado.

### 4. Ocultar la fila seleccionada  

Establecer `Hidden = true` indica a Aspose.Words que omita la fila al guardar el documento. La fila sigue existiendo en el modelo de objetos, por lo que puedes volver a mostrarla más tarde si lo necesitas.

```csharp
// Step 4: Hide the selected row – it will be omitted from the output
rowToHide.Hidden = true;
```

> **Pro tip:** Si realmente quieres *eliminar fila de tabla* en lugar de ocultarla, llama a `table.Rows.Remove(rowToHide);`. Ocultar preserva los metadatos de la fila, lo que puede ser útil para formato condicional.

### 5. Guardar el documento actualizado  

Finalmente, escribe los cambios de vuelta al disco.

```csharp
// Step 5: Save the document with the hidden row applied
doc.Save(@"C:\MyDocs\output.docx");
```

Cuando abras `output.docx` en Word, la tercera fila será invisible—exactamente lo que **ocultar fila en Word** significa en la práctica.

---

## Cómo ocultar fila – Variaciones comunes y casos límite

### Ocultar varias filas  

Si necesitas ocultar varias filas, recorre la colección:

```csharp
int[] rowsToHide = { 1, 3, 5 }; // zero‑based indexes
foreach (int i in rowsToHide)
{
    table.Rows[i].Hidden = true;
}
```

### Trabajar con celdas combinadas  

Una fila oculta que contiene una celda combinada verticalmente puede generar advertencias de diseño. El enfoque seguro es dividir la combinación antes de ocultar:

```csharp
Cell mergedCell = rowToHide.Cells[0];
if (mergedCell.CellFormat.VerticalMerge != CellMerge.None)
{
    // Break the merge to avoid Word warnings
    mergedCell.CellFormat.VerticalMerge = CellMerge.None;
}
rowToHide.Hidden = true;
```

### Compatibilidad con versiones antiguas de Word  

Aspose.Words escribe el atributo `w:hideMark`, que es entendido por Word 2007+ y LibreOffice. Si apuntas a Word 97‑2003 (`.doc`), la fila oculta seguirá siendo omitida, pero tablas complejas pueden renderizarse de forma distinta. Usa `.docx` para obtener resultados predecibles.

### Cuándo *ocultar fila* vs. *eliminar fila de tabla*  

- **Ocultar fila** – Mantén la fila para volver a mostrarla después, preserva la altura de la fila para cálculos de salto de página.  
- **Eliminar fila** – Reduce el tamaño del archivo, elimina permanentemente los datos. Usa `table.Rows.Remove(row)` si estás seguro de que la fila no se volverá a necesitar.

---

## Tips profesionales y advertencias

- **Pro tip:** Siempre verifica `table.Rows.Count` antes de acceder a un índice para evitar `ArgumentOutOfRangeException`.  
- **Watch out for:** Las filas ocultas siguen participando en cálculos de tabla como la altura total. Si notas espacios inesperados, considera establecer `row.Height = 0` después de ocultar.  
- **Performance:** Ocultar filas es barato; eliminar filas desencadena un re‑diseño de toda la tabla, lo que puede ser más lento en documentos muy grandes.  
- **Testing:** Abre el archivo guardado en Word y usa **Reveal Formatting** (`Shift+F1`) para verificar que la bandera `Hidden` de la fila esté activada.

---

## Ejemplo completo y funcional (listo para copiar y pegar)

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Tables;

class HideRowInTableDemo
{
    static void Main()
    {
        // Load the source document (ensure the path exists)
        Document doc = new Document(@"C:\MyDocs\input.docx");

        // Get the first table – adapt if you have multiple tables
        Table table = doc.FirstSection.Body.Tables[0];

        // Verify we have at least three rows
        if (table.Rows.Count < 3)
        {
            Console.WriteLine("The table doesn't have a third row to hide.");
            return;
        }

        // Choose the third row (index 2) and hide it
        Row rowToHide = table.Rows[2];
        rowToHide.Hidden = true; // This hides the row in the output document

        // Save the modified document
        doc.Save(@"C:\MyDocs\output.docx");
        Console.WriteLine("Row hidden successfully. Check output.docx.");
    }
}
```

**Resultado esperado:** Abre `output.docx` y verás la tabla sin la tercera fila, mientras el resto del contenido permanece intacto. La fila oculta sigue formando parte del modelo del documento, por lo que podrías más adelante establecer `row.Hidden = false` para volver a hacerla visible.

---

## Conclusión

Acabamos de cubrir **cómo ocultar fila** en una tabla Word usando C#. Al cargar el documento, localizar la tabla, elegir la fila objetivo, marcarla como oculta y guardar, logras una operación limpia de *ocultar fila en tabla* sin eliminar datos. El mismo patrón te permite *eliminar fila de tabla* si necesitas un cambio permanente, y los consejos adicionales aseguran que evites errores comunes al trabajar con celdas combinadas o versiones antiguas de Word.

¿Listo para el próximo desafío? Prueba combinar esta técnica con lógica condicional—oculta filas según la entrada del usuario, o genera informes dinámicos donde ciertas secciones desaparecen automáticamente. También podrías explorar **ocultar fila en Word** para encabezados, pies de página o incluso secciones completas.

¿Tienes preguntas sobre *ocultar fila c#* o necesitas ayuda para integrar esto en un flujo de trabajo más amplio? Deja un comentario abajo o consulta nuestros tutoriales relacionados sobre **manipular tablas en Word con Aspose.Words**. ¡Feliz codificación!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}