---
title: Insertar fecha dinámica en el encabezado de un documento Word usando Aspose.Words for .NET
weight: 110
limit:
description: Aprenda cómo agregar un campo DATE dinámico al encabezado principal de un documento Word con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aprenda cómo agregar un campo DATE dinámico al encabezado principal
    de un documento Word con Aspose.Words for .NET.
  headline: Insertar fecha dinámica en el encabezado de un documento Word usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprenda cómo agregar un campo DATE dinámico al encabezado principal
    de un documento Word con Aspose.Words for .NET.
  name: Insertar fecha dinámica en el encabezado de un documento Word usando Aspose.Words
    for .NET
  steps:
  - name: Crear un nuevo Document y un DocumentBuilder para editarlo.
    text: Crear un nuevo Document y un DocumentBuilder para editarlo.
  - name: Mueva el cursor del builder al encabezado principal para que las inserciones
      posteriores afecten al encabezado.
    text: Mueva el cursor del builder al encabezado principal para que las inserciones
      posteriores afecten al encabezado.
  - name: Escriba la etiqueta estática e inserte un campo DATE con formato “MMMM d,
      yyyy” en el encabezado, creando una fecha dinámica.
    text: Escriba la etiqueta estática e inserte un campo DATE con formato “MMMM d,
      yyyy” en el encabezado, creando una fecha dinámica.
  - name: Regrese al cuerpo principal y agregue un párrafo de ejemplo, demostrando
      contenido normal del documento junto al encabezado.
    text: Regrese al cuerpo principal y agregue un párrafo de ejemplo, demostrando
      contenido normal del documento junto al encabezado.
  - name: Guarde el documento en un archivo .docx.
    text: Guarde el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: La llamada `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` posiciona
      el builder en el encabezado principal existente, y `Write`/`InsertField` simplemente
      añaden texto a lo que ya está allí; no eliminan el contenido existente.
    question: ¿Qué ocurre si el documento ya tiene un encabezado principal – mi código
      lo sobrescribirá?
  - answer: Sí – modifique el formato del switch en el código del campo pasado a `InsertField`,
      por ejemplo `builder.InsertField("DATE \\@ \"yyyy-MM-dd\"")` producirá una fecha
      como 2026-09-22.
    question: ¿Puedo cambiar el formato de fecha usado por el campo DATE, y cómo?
  - answer: Reemplace `HeaderFooterType.HeaderPrimary` por `HeaderFooterType.HeaderFirst`
      al llamar a `MoveToHeaderFooter`; el resto del código funciona igual.
    question: Si necesito el campo de fecha en el encabezado de la primera página
      en lugar del encabezado principal, ¿qué debo hacer?
  - answer: El campo se inserta solo con el switch `\@`, lo que indica a Word que
      muestre la fecha actual cada vez que el campo se actualiza (por ejemplo, al
      abrir el archivo o cuando presiona Ctrl+Alt+F9).
    question: ¿El campo DATE se actualiza automáticamente cuando el documento se abre
      más tarde?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Agregar una fecha dinámica a un encabezado de Word
og_description: Guía paso a paso para incrustar un campo de fecha en vivo en el encabezado de su Word con Aspose.Words.
og_image_alt: Captura de pantalla que muestra cómo insertar un campo DATE dinámico en el encabezado de un documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Insertar fecha dinámica en el encabezado de un documento Word usando Aspose.Words
Este tutorial demuestra cómo usar las clases Document y DocumentBuilder en Aspose.Words for .NET para insertar un campo DATE dinámico en el encabezado principal de un documento Word. El campo añadido se actualiza automáticamente a la fecha actual cada vez que se abre el documento, asegurando que su encabezado siempre refleje la fecha más reciente. Siga el código paso a paso para agregar el campo y guardar el archivo actualizado.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: ¿Qué ocurre si el documento ya tiene un encabezado principal – mi código lo sobrescribirá?**  
A: La llamada `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` posiciona el builder en el encabezado principal existente, y `Write`/`InsertField` simplemente añaden texto a lo que ya está allí; no eliminan el contenido existente.

**Q: ¿Puedo cambiar el formato de fecha usado por el campo DATE, y cómo?**  
A: Sí – modifique el formato del switch en el código del campo pasado a `InsertField`, por ejemplo `builder.InsertField("DATE \\@ \"yyyy-MM-dd\"")` producirá una fecha como 2026-09-22.

**Q: Si necesito el campo de fecha en el encabezado de la primera página en lugar del encabezado principal, ¿qué debo hacer?**  
A: Reemplace `HeaderFooterType.HeaderPrimary` por `HeaderFooterType.HeaderFirst` al llamar a `MoveToHeaderFooter`; el resto del código funciona igual.

**Q: ¿El campo DATE se actualiza automáticamente cuando el documento se abre más tarde?**  
A: El campo se inserta solo con el switch `\@`, lo que indica a Word que muestre la fecha actual cada vez que el campo se actualiza (por ejemplo, al abrir el archivo o cuando presiona Ctrl+Alt+F9).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}