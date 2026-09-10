---
title: Insertar forma de regla horizontal en documento Word usando Aspose.Words para .NET
weight: 110
limit:
description: Guía paso a paso para insertar una forma de regla horizontal en un documento Word con Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar forma de regla horizontal en documento Word usando Aspose.Words para .NET
Aprenda a usar Aspose.Words para .NET para insertar una forma de regla horizontal en un documento Word. Este tutorial le guía paso a paso en la creación de un nuevo documento, la adición de una línea de texto, la colocación de una forma de regla horizontal con DocumentBuilder y el guardado del archivo. La regla horizontal proporciona un separador visual sencillo para su contenido.

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

**Q: ¿Puedo cambiar la apariencia (color, grosor) de la regla horizontal insertada con DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule crea una forma de línea horizontal incorporada con formato predeterminado; para modificar su apariencia debe obtener el objeto Shape insertado (builder.CurrentParagraph.LastChild) y ajustar sus propiedades LineFormat.

**Q: ¿Qué ocurre si llamo a InsertHorizontalRule() después de un párrafo que ya termina con un salto de línea?**
A: El método inserta la regla como un párrafo separado, por lo que cualquier salto de línea anterior simplemente crea un párrafo vacío antes de la regla; la regla seguirá apareciendo en su propia línea.

**Q: ¿Es posible insertar más de una regla horizontal en el mismo documento usando DocumentBuilder?**
A: Sí, cada llamada a builder.InsertHorizontalRule() agrega una nueva forma de regla horizontal en la posición actual del cursor, lo que permite múltiples reglas a lo largo del documento.

**Q: ¿Funciona InsertHorizontalRule() al guardar el documento en formatos diferentes a DOCX, como PDF?**
A: La regla horizontal se almacena como una forma en el modelo del documento, por lo que al guardar en PDF, XPS u otros formatos compatibles la regla se renderiza correctamente en la salida.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}