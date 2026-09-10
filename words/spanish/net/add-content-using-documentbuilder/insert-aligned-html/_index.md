---
title: Insertar HTML alineado en un documento Word usando Aspose.Words for .NET
weight: 210
limit:
description: Aprende cómo insertar HTML con alineación específica en un documento Word usando Aspose.Words for .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar HTML alineado en un documento Word usando Aspose.Words
Este tutorial muestra cómo usar DocumentBuilder de Aspose.Words for .NET para incrustar marcado HTML en un documento Word y controlar su alineación. Verás cómo insertar el HTML, establecer la alineación del párrafo (izquierda, centro o derecha) y luego guardar el documento resultante. El ejemplo es ideal para desarrolladores que necesitan preservar el formato estilo web al generar archivos Word de forma programática.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: ¿Puede InsertHtml usarse para añadir HTML en un documento Word existente en lugar de uno nuevo?**
A: Sí. Crea un Document a partir del archivo existente, posiciona el cursor del DocumentBuilder donde deseas insertar el HTML (p. ej., usando builder.MoveToDocumentEnd()), y luego llama a builder.InsertHtml con tu marcado.

**Q: ¿Qué atributos HTML son respetados por InsertHtml para la alineación?**
A: InsertHtml respeta el atributo "align" en elementos de nivel de bloque como <p>, <div> y etiquetas de encabezado, aplicando la alineación de párrafo correspondiente en el documento Word resultante.

**Q: ¿Qué ocurre si la cadena HTML contiene etiquetas o CSS no compatibles?**
A: Las etiquetas no compatibles se ignoran y su texto interno se inserta como texto plano; los estilos CSS en línea que Aspose.Words no reconoce también se ignoran, por lo que solo se renderiza el subconjunto de HTML admitido.

**Q: ¿Necesito cerrar el DocumentBuilder antes de guardar el documento?**
A: No se requiere un cierre explícito; después de insertar el HTML puedes llamar directamente a doc.Save con el nombre y formato de archivo deseados, y los recursos del builder se liberan automáticamente.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}