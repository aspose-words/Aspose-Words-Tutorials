---
title: Insertar salto de página en un documento Word con Aspose.Words for .NET
weight: 110
limit:
description: Aprenda a agregar saltos de página a un archivo Word con Aspose.Words for .NET usando Document y DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar salto de página en un documento Word con Aspose.Words
En este tutorial interactivo aprenderá cómo agregar programáticamente saltos de página a un documento Word usando Aspose.Words for .NET. Al crear un objeto Document y usar DocumentBuilder, puede controlar dónde comienzan las nuevas páginas, lo cual es esencial para formatear informes, facturas o cualquier documento de varias secciones. Siga el ejemplo paso a paso para ver el código en acción y previsualizar el archivo resultante.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: ¿Puedo usar InsertBreak para agregar un salto de línea o un salto de sección en lugar de un salto de página?**
A: Sí, InsertBreak acepta cualquier valor del enum BreakType, como BreakType.LineBreak o BreakType.SectionBreakContinuous, para insertar el salto correspondiente.

**Q: ¿Necesito llamar a InsertBreak antes o después de escribir el texto para la nueva página?**
A: InsertBreak debe llamarse después del contenido que desea en la página actual; la siguiente Writeln comenzará entonces en la nueva página creada por el salto.

**Q: ¿Qué ocurre si la ruta dataDir no termina con un separador de directorio?**
A: Si dataDir no tiene una barra diagonal final, el nombre del archivo se concatenará directamente (p. ej., "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), lo que puede generar una ruta inválida; asegúrese de que la ruta termine con "\\" o use Path.Combine.

**Q: ¿Puedo reutilizar la misma instancia de DocumentBuilder para insertar múltiples saltos a lo largo del documento?**
A: Sí, la misma DocumentBuilder puede usarse repetidamente; cada llamada a InsertBreak inserta un salto en la posición actual del cursor del builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}