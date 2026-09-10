---
title: Insertar campo TC en documento Word usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda cómo insertar un campo TC con texto personalizado en un documento Word usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar campo TC en documento Word usando Aspose.Words
Este tutorial muestra cómo usar Aspose.Words for .NET para insertar un campo TC (Tabla de contenido) en un documento Word recién creado. Mediante DocumentBuilder puede agregar un campo TC con texto de entrada personalizado, lo que es útil para crear un índice buscable para una tabla de contenido. El ejemplo también demuestra cómo guardar el documento en disco.

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

**Q: ¿Qué significa el interruptor \"\\f t\" en el código del campo TC?**
A: El interruptor \"\\f t\" indica a Word que trate la entrada como una entrada de tabla, lo que hace que aparezca en una Tabla de contenido generada con el interruptor \\f.

**Q: ¿Cómo puedo cambiar el texto que aparece en el campo TC?**
A: Reemplace \"Entry Text\" en la llamada InsertField por cualquier cadena que desee, por ejemplo, builder.InsertField(\"TC \\\"Chapter 1\\\" \\f t\");

**Q: ¿Puedo insertar varios campos TC en el mismo documento?**
A: Sí; simplemente llame a builder.InsertField con diferentes textos de entrada en las ubicaciones deseadas antes de guardar el documento.

**Q: ¿Este código funciona para formatos distintos a .docx, como .pdf?**
A: El documento se guarda como .docx en el ejemplo, pero Aspose.Words puede guardarse en otros formatos (p. ej., .pdf) cambiando la extensión del archivo en doc.Save y asegurándose de que el formato de salida correspondiente esté soportado.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}