---
title: Agregar un campo TC a un documento Word con Aspose.Words for .NET
weight: 310
limit:
description: Aprenda a insertar un campo TC en un nuevo documento Word con Aspose.Words for .NET usando DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar un campo TC a un documento Word con Aspose.Words
En este tutorial interactivo aprenderá cómo agregar programáticamente un campo TC —un marcador oculto utilizado por las funciones de indexación y tabla de contenido de Word— a un documento recién creado usando Aspose.Words for .NET. Al usar DocumentBuilder puede colocar el campo exactamente donde lo necesite y luego guardar el archivo, listo para procesamiento adicional.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: ¿Qué hace realmente el campo "TC" insertado por `builder.InsertField("TC \"Entry Text\" \\f t")` en el documento Word?**
A: Crea una entrada en la tabla de contenido con el texto visible "Entry Text" y la marca como una entrada TC (Tabla de contenido), que Word puede usar posteriormente al generar una tabla de contenido.

**Q: ¿Cuál es el propósito del interruptor `\f t` en la cadena del campo TC?**
A: El interruptor `\f t` indica a Word que trate la entrada como una entrada de texto normal (en lugar de un encabezado) y que la incluya en la tabla de contenido cuando se genere.

**Q: ¿Puedo insertar varios campos TC con diferentes textos de entrada usando la misma instancia de `DocumentBuilder`?**
A: Sí; simplemente llame a `builder.InsertField` nuevamente con una cadena diferente, por ejemplo, `builder.InsertField("TC \"Another Entry\" \\f t")`, y cada llamada inserta un nuevo campo TC en la posición actual del cursor.

**Q: Si necesito que el texto de la entrada sea dinámico (p. ej., proveniente de una variable), ¿cómo debo formatear la llamada a `InsertField`?**
A: Construya la cadena del campo con interpolación de cadenas o `String.Format`, por ejemplo: `string entry = "Chapter 1"; builder.InsertField($"TC \"{entry}\" \\f t");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}