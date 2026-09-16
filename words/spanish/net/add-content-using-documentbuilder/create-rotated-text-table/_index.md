---
title: Crear tabla de texto rotado en documento Word usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a crear una tabla Word con anchos de columna fijos, texto rotado, alturas de fila precisas y celdas rellenadas usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, rotated text table, fixed column widths, vertical alignment Aspose.Words, set row height Word, populate table cells .NET]
url: /net/add-content-using-documentbuilder/create-rotated-text-table/
date: '2026-09-16'
lastmod: '2026-09-16'
schemas:
- author: Aspose
  dateModified: '2026-09-16'
  description: Aprenda a crear una tabla Word con anchos de columna fijos, texto rotado,
    alturas de fila precisas y celdas rellenadas usando Aspose.Words for .NET.
  headline: Crear tabla de texto rotado en documento Word usando Aspose.Words for
    .NET
  type: TechArticle
- description: Aprenda a crear una tabla Word con anchos de columna fijos, texto rotado,
    alturas de fila precisas y celdas rellenadas usando Aspose.Words for .NET.
  name: Crear tabla de texto rotado en documento Word usando Aspose.Words for .NET
  steps:
  - name: Instanciar un nuevo Document y un DocumentBuilder que se utilizarán para
      construir la tabla.
    text: Instanciar un nuevo Document y un DocumentBuilder que se utilizarán para
      construir la tabla.
  - name: Iniciar una nueva tabla, insertar la primera celda y fijar los anchos de
      columna para que no se ajusten automáticamente.
    text: Iniciar una nueva tabla, insertar la primera celda y fijar los anchos de
      columna para que no se ajusten automáticamente.
  - name: Alinear verticalmente al centro el contenido en la celda actual y escribir
      el texto de la primera celda de la primera fila.
    text: Alinear verticalmente al centro el contenido en la celda actual y escribir
      el texto de la primera celda de la primera fila.
  - name: Insertar la segunda celda de la primera fila y escribir su texto.
    text: Insertar la segunda celda de la primera fila y escribir su texto.
  - name: Cerrar la primera fila, finalizando su diseño.
    text: Cerrar la primera fila, finalizando su diseño.
  - name: Iniciar la primera celda de la segunda fila, establecer la altura de la
      fila en exactamente 100 puntos, rotar el texto hacia arriba y escribir el texto
      de la celda.
    text: Iniciar la primera celda de la segunda fila, establecer la altura de la
      fila en exactamente 100 puntos, rotar el texto hacia arriba y escribir el texto
      de la celda.
  - name: Insertar la segunda celda de la segunda fila, rotar su texto hacia abajo
      y escribir el texto de la celda.
    text: Insertar la segunda celda de la segunda fila, rotar su texto hacia abajo
      y escribir el texto de la celda.
  - name: Cerrar la segunda fila, completando la segunda línea de la tabla.
    text: Cerrar la segunda fila, completando la segunda línea de la tabla.
  - name: Terminar la construcción de la tabla, sellando la estructura de la tabla.
    text: Terminar la construcción de la tabla, sellando la estructura de la tabla.
  - name: Guardar el documento completado en un archivo .docx.
    text: Guardar el documento completado en un archivo .docx.
  type: HowTo
- questions:
  - answer: Después de fijar los anchos de columna, asigne un ancho a cada celda usando
      `builder.CellFormat.Width = <valueInPoints>;` antes de insertar la siguiente
      celda; la tabla mantendrá esos anchos exactos.
    question: ¿Cómo puedo establecer anchos de columna específicos después de llamar
      a `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?
  - answer: '`builder.CellFormat.VerticalAlignment` es una configuración a nivel de
      celda, por lo que debe establecerla nuevamente para las celdas de la segunda
      fila (p. ej., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`)
      antes de escribir su contenido.'
    question: ¿Por qué la alineación vertical solo afecta a la primera fila y no a
      la segunda fila?
  - answer: Sí—establezca `builder.RowFormat.Height` y `builder.RowFormat.HeightRule
      = HeightRule.Exactly` antes de cada llamada a `builder.EndRow();`; la siguiente
      fila puede tener un valor de altura diferente.
    question: ¿Puedo asignar a cada fila una altura exacta diferente y, de ser así,
      cómo?
  - answer: Restablezca la orientación asignando `builder.CellFormat.Orientation =
      TextOrientation.Horizontal;` antes de escribir en la siguiente celda.
    question: ¿Cómo puedo revertir la orientación del texto al valor predeterminado
      después de usar `TextOrientation.Upward` o `Downward`?
  type: FAQPage
images:
- /net/add-content-using-documentbuilder/create-rotated-text-table/og-image.png
og_title: Crear tabla de texto rotado en Word con Aspose.Words
og_description: Código paso a paso para crear una tabla de ancho fijo con texto rotado verticalmente y alturas de fila exactas.
og_image_alt: Captura de pantalla que muestra un documento Word con una tabla que tiene anchos de columna fijos, texto rotado en las celdas y alturas de fila definidas, creada usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crear tabla de texto rotado en documento Word usando Aspose.Words
Este tutorial muestra cómo generar un documento Word y agregar una tabla cuyas columnas tienen anchos fijos, las filas tienen alturas exactas y el texto de las celdas está rotado verticalmente. Aprenderá a establecer la alineación vertical, aplicar la orientación del texto, rellenar cada celda con contenido y, finalmente, guardar el documento, todo con Aspose.Words for .NET.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/create-rotated-text-table" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Cómo puedo establecer anchos de columna específicos después de llamar a `table.AutoFit(AutoFitBehavior.FixedColumnWidths)`?**  
A: Después de fijar los anchos de columna, asigne un ancho a cada celda usando `builder.CellFormat.Width = <valueInPoints>;` antes de insertar la siguiente celda; la tabla mantendrá esos anchos exactos.

**Q: ¿Por qué la alineación vertical solo afecta a la primera fila y no a la segunda fila?**  
A: `builder.CellFormat.VerticalAlignment` es una configuración a nivel de celda, por lo que debe establecerla nuevamente para las celdas de la segunda fila (p. ej., `builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;`) antes de escribir su contenido.

**Q: ¿Puedo asignar a cada fila una altura exacta diferente y, de ser así, cómo?**  
A: Sí—establezca `builder.RowFormat.Height` y `builder.RowFormat.HeightRule = HeightRule.Exactly` antes de cada llamada a `builder.EndRow();`; la siguiente fila puede tener un valor de altura diferente.

**Q: ¿Cómo puedo revertir la orientación del texto al valor predeterminado después de usar `TextOrientation.Upward` o `Downward`?**  
A: Restablezca la orientación asignando `builder.CellFormat.Orientation = TextOrientation.Horizontal;` antes de escribir en la siguiente celda.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}