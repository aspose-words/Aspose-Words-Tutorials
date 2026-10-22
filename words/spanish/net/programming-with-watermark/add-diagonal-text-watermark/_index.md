---
title: Crear una marca de agua de texto diagonal con fuente personalizada en un documento Word usando Aspose.Words for .NET
weight: 210
limit:
description: Código paso a paso para añadir una marca de agua de texto diagonal con fuente personalizada a un .docx de Word usando Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Código paso a paso para añadir una marca de agua de texto diagonal
    con fuente personalizada a un .docx de Word usando Aspose.Words for .NET.
  headline: Crear una marca de agua de texto diagonal con fuente personalizada en
    un documento Word usando Aspose.Words for .NET
  type: TechArticle
- description: Código paso a paso para añadir una marca de agua de texto diagonal
    con fuente personalizada a un .docx de Word usando Aspose.Words for .NET.
  name: Crear una marca de agua de texto diagonal con fuente personalizada en un documento
    Word usando Aspose.Words for .NET
  steps:
  - name: Crea una nueva instancia vacía de documento Word llamada `document`.
    text: Crea una nueva instancia vacía de documento Word llamada `document`.
  - name: Configura `watermarkSettings` con fuente Arial de 48 pt en color gris, diseño
      diagonal y renderizado opaco.
    text: Configura `watermarkSettings` con fuente Arial de 48 pt en color gris, diseño
      diagonal y renderizado opaco.
  - name: Aplica la marca de agua de texto "Private" a `document` usando la configuración
      definida previamente.
    text: Aplica la marca de agua de texto "Private" a `document` usando la configuración
      definida previamente.
  - name: Define la ruta del archivo donde se guardará el documento con marca de agua.
    text: Define la ruta del archivo donde se guardará el documento con marca de agua.
  - name: Guarda el `document` modificado en la ruta especificada como un archivo
      .docx.
    text: Guarda el `document` modificado en la ruta especificada como un archivo
      .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` determina si la marca de agua se renderiza con opacidad
      parcial; establecerlo en `false` hace que la marca de agua sea totalmente opaca,
      mientras que `true` aplica un efecto semitransparente predeterminado.'
    question: ¿Qué controla la bandera **IsSemitrasparent** en `TextWatermarkOptions`?
  - answer: Sí—establece la propiedad `Layout` a `WatermarkLayout.Horizontal` (u otro
      valor del enum) antes de llamar a `document.Watermark.SetText`.
    question: ¿Puedo cambiar la orientación de la marca de agua a horizontal en lugar
      de diagonal?
  - answer: Word recurrirá a su fuente predeterminada para la marca de agua, por lo
      que el texto seguirá apareciendo pero puede verse diferente al estilo previsto.
    question: ¿Qué ocurre si la `FontFamily` especificada (p.ej., "Arial") no está
      instalada en la máquina destino?
  - answer: Carga el archivo existente con `Document document = new Document("Existing.docx");`
      luego configura `TextWatermarkOptions` y llama a `document.Watermark.SetText`
      como se muestra.
    question: ¿Es posible añadir una marca de agua a un archivo `.docx` existente
      en lugar de crear uno nuevo?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Agregar una marca de agua de texto diagonal con fuente personalizada
og_description: Aprende a incrustar una marca de agua de texto inclinado con tu propia fuente en un archivo Word en minutos.
og_image_alt: Guía que muestra cómo añadir una marca de agua de texto diagonal con fuente personalizada a un documento Word usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crear una marca de agua de texto diagonal con fuente personalizada en un documento Word usando Aspose.Words
Este tutorial te guía paso a paso para crear un nuevo documento Word, configurar una marca de agua de texto diagonal con los ajustes de fuente que elijas, aplicarla mediante la API Document.Watermark.SetText y guardar el resultado como un archivo .docx. Al final tendrás un documento con marca de agua profesional que muestra tu marca o propiedad. El código paso a paso está listo para copiarse en cualquier proyecto .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-diagonal-text-watermark" >}}


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

**Q: ¿Qué controla la bandera **IsSemitrasparent** en `TextWatermarkOptions`?**  
A: `IsSemitrasparent` determina si la marca de agua se renderiza con opacidad parcial; establecerlo en `false` hace que la marca de agua sea totalmente opaca, mientras que `true` aplica un efecto semitransparente predeterminado.

**Q: ¿Puedo cambiar la orientación de la marca de agua a horizontal en lugar de diagonal?**  
A: Sí—establece la propiedad `Layout` a `WatermarkLayout.Horizontal` (u otro valor del enum) antes de llamar a `document.Watermark.SetText`.

**Q: ¿Qué ocurre si la `FontFamily` especificada (p.ej., "Arial") no está instalada en la máquina destino?**  
A: Word recurrirá a su fuente predeterminada para la marca de agua, por lo que el texto seguirá apareciendo pero puede verse diferente al estilo previsto.

**Q: ¿Es posible añadir una marca de agua a un archivo `.docx` existente en lugar de crear uno nuevo?**  
A: Carga el archivo existente con `Document document = new Document("Existing.docx");` luego configura `TextWatermarkOptions` y llama a `document.Watermark.SetText` como se muestra.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}