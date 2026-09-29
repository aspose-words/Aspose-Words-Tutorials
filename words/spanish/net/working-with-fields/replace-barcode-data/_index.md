---
title: Reemplazar datos de código de barras en documentos Word usando Aspose.Words for .NET
weight: 110
limit:
description: Aprende cómo insertar un campo DISPLAYBARCODE y reemplazar su cadena de datos con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aprende cómo insertar un campo DISPLAYBARCODE y reemplazar su cadena
    de datos con Aspose.Words for .NET.
  headline: Reemplazar datos de código de barras en documentos Word usando Aspose.Words
    for .NET
  type: TechArticle
- description: Aprende cómo insertar un campo DISPLAYBARCODE y reemplazar su cadena
    de datos con Aspose.Words for .NET.
  name: Reemplazar datos de código de barras en documentos Word usando Aspose.Words
    for .NET
  steps:
  - name: Crea un nuevo objeto Document y un DocumentBuilder para construir su contenido.
    text: Crea un nuevo objeto Document y un DocumentBuilder para construir su contenido.
  - name: Inserta un campo DISPLAYBARCODE y establece su tipo, valor inicial y caracteres
      de inicio/fin, luego agrega un salto de línea.
    text: Inserta un campo DISPLAYBARCODE y establece su tipo, valor inicial y caracteres
      de inicio/fin, luego agrega un salto de línea.
  - name: Llama a UpdateFields para renderizar el campo de código de barras recién
      insertado.
    text: Llama a UpdateFields para renderizar el campo de código de barras recién
      insertado.
  - name: Utiliza el motor de Buscar/Reemplazar para cambiar la cadena de datos del
      código de barras de INIT123 a NEWVAL.
    text: Utiliza el motor de Buscar/Reemplazar para cambiar la cadena de datos del
      código de barras de INIT123 a NEWVAL.
  - name: Actualiza los campos nuevamente para que DISPLAYBARCODE refleje la nueva
      cadena de datos.
    text: Actualiza los campos nuevamente para que DISPLAYBARCODE refleje la nueva
      cadena de datos.
  - name: Guarda el documento en un archivo .docx.
    text: Guarda el documento en un archivo .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` solo cambia el texto subyacente; el resultado visual
      del campo DISPLAYBARCODE se regenera solo cuando se llama a `UpdateFields()`,
      por lo que el nuevo código de barras aparece en el documento guardado.'
    question: ¿Por qué necesito llamar a `myDocument.UpdateFields()` después de ejecutar
      `Range.Replace`?
  - answer: Sí, `Document.Range.Replace` funciona en todo el rango del documento,
      por lo que cualquier texto coincidente en otro lugar será reemplazado a menos
      que restrinjas la búsqueda usando `FindReplaceOptions` (p. ej., estableciendo
      un `Range` específico o usando `.MatchWholeWord`).
    question: ¿Afectará la llamada `Replace("INIT123", "NEWVAL", ...)` a otras ocurrencias
      de "INIT123" fuera del campo de código de barras?
  - answer: Puedes asignar un nuevo valor a `displayBarcode.BarcodeType` en cualquier
      momento, pero debes llamar a `myDocument.UpdateFields()` después para que el
      cambio se refleje en el código de barras renderizado.
    question: ¿Puedo cambiar el tipo de código de barras (p. ej., de CODE39 a QR)
      después de que el campo haya sido insertado?
  - answer: Cuando `AddStartStopChar` es true, Aspose.Words agrega automáticamente
      los caracteres de inicio/fin requeridos (`*`) alrededor del valor del código
      de barras, lo cual es necesario para CODE39; configúralo a false si tu simbología
      no los necesita.
    question: ¿Qué hace la propiedad `AddStartStopChar = true` para los códigos de
      barras CODE39?
  - answer: No se requieren configuraciones especiales para una coincidencia exacta
      simple, pero puedes habilitar `.MatchCase` o `.MatchWholeWord` en `FindReplaceOptions`
      para evitar reemplazos parciales accidentales.
    question: ¿Necesito configurar alguna opción especial en `FindReplaceOptions`
      para reemplazar el valor del código de barras de forma segura?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Actualizar un campo de código de barras en Word con Aspose.Words
og_description: Intercambia la cadena de datos de un código de barras y actualízala al instante en un archivo Word.
og_image_alt: Captura de pantalla que muestra un documento Word con un campo DISPLAYBARCODE antes y después del reemplazo de datos usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Reemplazar datos de código de barras en documentos Word usando Aspose.Words
Este tutorial demuestra cómo insertar un campo DISPLAYBARCODE en un documento Word y luego usar el método Document.Range.Replace para cambiar la cadena de datos del código de barras. Después del reemplazo, el campo se actualiza para que el código de barras actualizado aparezca en el archivo guardado. Sigue los pasos para ver la actualización del código de barras al instante sin recrear el campo.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


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

**Q: ¿Por qué necesito llamar a `myDocument.UpdateFields()` después de ejecutar `Range.Replace`?**  
A: `Range.Replace` solo cambia el texto subyacente; el resultado visual del campo DISPLAYBARCODE se regenera solo cuando se llama a `UpdateFields()`, por lo que el nuevo código de barras aparece en el documento guardado.

**Q: ¿Afectará la llamada `Replace("INIT123", "NEWVAL", ...)` a otras ocurrencias de "INIT123" fuera del campo de código de barras?**  
A: Sí, `Document.Range.Replace` funciona en todo el rango del documento, por lo que cualquier texto coincidente en otro lugar será reemplazado a menos que restrinjas la búsqueda usando `FindReplaceOptions` (p. ej., estableciendo un `Range` específico o usando `.MatchWholeWord`).

**Q: ¿Puedo cambiar el tipo de código de barras (p. ej., de CODE39 a QR) después de que el campo haya sido insertado?**  
A: Puedes asignar un nuevo valor a `displayBarcode.BarcodeType` en cualquier momento, pero debes llamar a `myDocument.UpdateFields()` después para que el cambio se refleje en el código de barras renderizado.

**Q: ¿Qué hace la propiedad `AddStartStopChar = true` para los códigos de barras CODE39?**  
A: Cuando `AddStartStopChar` es true, Aspose.Words agrega automáticamente los caracteres de inicio/fin requeridos (`*`) alrededor del valor del código de barras, lo cual es necesario para CODE39; configúralo a false si tu simbología no los necesita.

**Q: ¿Necesito configurar alguna opción especial en `FindReplaceOptions` para reemplazar el valor del código de barras de forma segura?**  
A: No se requieren configuraciones especiales para una coincidencia exacta simple, pero puedes habilitar `.MatchCase` o `.MatchWholeWord` en `FindReplaceOptions` para evitar reemplazos parciales accidentales.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}