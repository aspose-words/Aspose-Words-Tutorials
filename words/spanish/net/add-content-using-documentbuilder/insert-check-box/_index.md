---
title: Agregar un campo de formulario de casilla de verificación a un documento Word con Aspose.Words for .NET
weight: 210
limit:
description: Aprenda cómo agregar programáticamente un campo de formulario de casilla de verificación a un nuevo documento Word usando Aspose.Words for .NET y guardar el archivo.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Agregar un campo de formulario de casilla de verificación a un documento Word con Aspose.Words
Este tutorial muestra cómo crear un documento Word nuevo y usar DocumentBuilder de Aspose.Words for .NET para insertar un campo de formulario de casilla de verificación. Al seguir los pasos, verá el código exacto necesario para agregar el elemento interactivo y luego guardar el documento en un archivo. Es una forma rápida de crear archivos Word con formularios habilitados de manera programática.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: ¿Qué representa el cuarto argumento (0) en InsertCheckBox?**
A: Especifica el tamaño visual de la casilla de verificación en puntos; un valor de 0 indica a Aspose.Words que use el tamaño predeterminado.

**Q: ¿Puedo insertar más de una casilla de verificación con el mismo nombre?**
A: No – cada nombre de campo de formulario debe ser único; intentar insertar otra casilla de verificación llamada "CheckBox" lanzará una ArgumentException.

**Q: ¿Cómo agrego una casilla de verificación a un documento existente en lugar de a uno nuevo?**
A: Cargue el documento primero (p. ej., `Document doc = new Document("Existing.docx");`) luego cree un DocumentBuilder para ese documento y llame a `InsertCheckBox` en la posición del cursor deseada.

**Q: ¿Cómo puedo leer el estado de la casilla de verificación insertada después de que el documento se haya guardado?**
A: Recupere el campo de formulario mediante `doc.Range.FormFields["CheckBox"]` y examine su propiedad `Checked` para ver si estaba marcado.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}