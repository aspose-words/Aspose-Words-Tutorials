---
title: Insertar código de barras DataMatrix en documento Word usando Aspose.Words para .NET
weight: 210
limit:
description: Agregue un código de barras DataMatrix a un documento Word programáticamente con Aspose.Words para .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Agregue un código de barras DataMatrix a un documento Word programáticamente
    con Aspose.Words para .NET.
  headline: Insertar código de barras DataMatrix en documento Word usando Aspose.Words
    para .NET
  type: TechArticle
- description: Agregue un código de barras DataMatrix a un documento Word programáticamente
    con Aspose.Words para .NET.
  name: Insertar código de barras DataMatrix en documento Word usando Aspose.Words
    para .NET
  steps:
  - name: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
    text: Cree un nuevo documento Word vacío y un DocumentBuilder para editarlo.
  - name: Inserte un campo DISPLAYBARCODE en la posición actual del cursor, lo que
      agrega un marcador de posición de campo al documento.
    text: Inserte un campo DISPLAYBARCODE en la posición actual del cursor, lo que
      agrega un marcador de posición de campo al documento.
  - name: Establezca la propiedad BarcodeType del campo a DataMatrix y proporcione
      la cadena de datos a codificar.
    text: Establezca la propiedad BarcodeType del campo a DataMatrix y proporcione
      la cadena de datos a codificar.
  - name: Opcionalmente, defina los colores de fondo y de primer plano del código
      de barras.
    text: Opcionalmente, defina los colores de fondo y de primer plano del código
      de barras.
  - name: Llame a UpdateFields en el documento para generar la imagen del código de
      barras dentro del campo.
    text: Llame a UpdateFields en el documento para generar la imagen del código de
      barras dentro del campo.
  - name: Guarde el documento en un archivo .docx.
    text: Guarde el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: El campo se insertará, pero `document.UpdateFields()` dejará el código
      de barras en blanco y Aspose.Words lanzará una `FieldException` indicando un
      tipo de código de barras inválido.
    question: ¿Qué ocurre si asigno un valor no compatible a `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` genera las imágenes del código de barras, por lo que
      puede insertar varios objetos `FieldDisplayBarcode` y llamar a `document.UpdateFields()`
      una sola vez al final para generar todos.'
    question: ¿Necesito llamar a `document.UpdateFields()` después de cada inserción
      de código de barras, o puedo actualizar una sola vez después de agregar todos
      los campos?
  - answer: Ambas propiedades esperan una cadena RGB hexadecimal con prefijo `0x`
      (p. ej., "0xFF0000" para rojo); cualquier otro formato será ignorado y se usarán
      los colores predeterminados.
    question: ¿En qué formato deben estar las cadenas de color para `BackgroundColor`
      y `ForegroundColor`?
  - answer: Sí—simplemente establezca `displayBarcodeField.BarcodeValue` a una nueva
      cadena y llame a `document.UpdateFields()` nuevamente para actualizar la imagen
      generada.
    question: ¿Puedo cambiar la carga útil del código de barras después de que el
      campo haya sido insertado?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Insertar un código de barras DataMatrix con Aspose.Words
og_description: Aprenda cómo agregar un código de barras DataMatrix a un archivo Word en solo unas pocas líneas de código .NET.
og_image_alt: Guía que muestra cómo insertar y generar un código de barras DataMatrix en un documento Word usando Aspose.Words para .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar código de barras DataMatrix en documento Word usando Aspose.Words para .NET
Con Aspose.Words para .NET puede agregar programáticamente un código de barras DataMatrix a un documento Word. Este tutorial muestra cómo crear un nuevo documento, insertar un campo DISPLAYBARCODE, establecer su tipo a DataMatrix y generar la imagen del código de barras usando las clases Document y DocumentBuilder. Siga los pasos para generar un código de barras imprimible directamente dentro de su archivo .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Qué ocurre si asigno un valor no compatible a `displayBarcodeField.BarcodeType`?**  
A: El campo se insertará, pero `document.UpdateFields()` dejará el código de barras en blanco y Aspose.Words lanzará una `FieldException` indicando un tipo de código de barras inválido.

**Q: ¿Necesito llamar a `document.UpdateFields()` después de cada inserción de código de barras, o puedo actualizar una sola vez después de agregar todos los campos?**  
A: `UpdateFields()` genera las imágenes del código de barras, por lo que puede insertar varios objetos `FieldDisplayBarcode` y llamar a `document.UpdateFields()` una sola vez al final para generar todos.

**Q: ¿En qué formato deben estar las cadenas de color para `BackgroundColor` y `ForegroundColor`?**  
A: Ambas propiedades esperan una cadena RGB hexadecimal con prefijo `0x` (p. ej., "0xFF0000" para rojo); cualquier otro formato será ignorado y se usarán los colores predeterminados.

**Q: ¿Puedo cambiar la carga útil del código de barras después de que el campo haya sido insertado?**  
A: Sí—simplemente establezca `displayBarcodeField.BarcodeValue` a una nueva cadena y llame a `document.UpdateFields()` nuevamente para actualizar la imagen generada.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}