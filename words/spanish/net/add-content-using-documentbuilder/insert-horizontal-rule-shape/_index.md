---
title: Insertar forma de regla horizontal en documento Word usando Aspose.Words for .NET
weight: 110
limit:
description: Aprende a agregar una forma de regla horizontal a un documento Word con Aspose.Words for .NET usando DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma de regla horizontal en documento Word usando Aspose.Words
En este tutorial aprenderás cómo insertar programáticamente una forma de regla horizontal en un documento Word con Aspose.Words for .NET. Usando las clases Document y DocumentBuilder creamos un nuevo documento, agregamos un párrafo de texto y luego colocamos una forma de línea horizontal en la ubicación deseada. La regla horizontal proporciona un separador visual que puede ser útil para saltos de sección o énfasis visual.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: ¿Dónde exactamente coloca `builder.InsertHorizontalRule()` la línea en el documento?**
A: `InsertHorizontalRule` inserta una forma de regla horizontal en la posición actual del cursor del `DocumentBuilder`; si deseas que esté en una línea propia, llama a `builder.Writeln()` antes de la inserción.

**Q: ¿Puedo cambiar el grosor, color o ancho de la regla horizontal insertada?**
A: `InsertHorizontalRule` agrega una regla con estilo predeterminado y no expone opciones de formato; para personalizar esas propiedades debes insertar un `Shape` manualmente (p. ej., `builder.InsertShape(ShapeType.HorizontalLine)`) y luego establecer sus propiedades `LineFormat`.

**Q: ¿Es posible agregar más de una regla horizontal en el mismo documento?**
A: Sí—simplemente llama a `builder.InsertHorizontalRule()` cada vez que necesites una nueva regla; cada llamada crea una forma separada en la ubicación actual del builder.

**Q: ¿Será visible la regla horizontal cuando el .docx guardado se abra en Microsoft Word?**
A: Absolutamente; la regla se guarda como una forma dentro del archivo .docx, por lo que Word la muestra exactamente como aparece en el documento generado.

**Q: ¿Qué ocurre si la carpeta `dataDir` no existe antes de llamar a `doc.Save(...)`?**
A: `doc.Save` lanzará una `DirectoryNotFoundException`; asegúrate de que el directorio de destino exista o créalo programáticamente antes de guardar.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}