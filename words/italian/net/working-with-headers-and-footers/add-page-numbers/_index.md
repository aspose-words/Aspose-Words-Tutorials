---
title: Aggiungi numeri di pagina al piè di pagina di un documento Word usando Aspose.Words per .NET
weight: 210
limit:
description: Aggiungi numeri di pagina aggiornati automaticamente al piè di pagina primario di un documento Word usando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, add page numbers, word document footer, documentbuilder page numbers, automatic page numbering, c# aspose.words]
url: /net/working-with-headers-and-footers/add-page-numbers/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Aggiungi numeri di pagina aggiornati automaticamente al piè di pagina
    primario di un documento Word usando Aspose.Words per .NET.
  headline: Aggiungi numeri di pagina al piè di pagina di un documento Word usando
    Aspose.Words per .NET
  type: TechArticle
- description: Aggiungi numeri di pagina aggiornati automaticamente al piè di pagina
    primario di un documento Word usando Aspose.Words per .NET.
  name: Aggiungi numeri di pagina al piè di pagina di un documento Word usando Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo oggetto Document e un DocumentBuilder collegato ad esso.
    text: Crea un nuovo oggetto Document e un DocumentBuilder collegato ad esso.
  - name: Sposta il cursore del builder al piè di pagina primario della prima sezione.
    text: Sposta il cursore del builder al piè di pagina primario della prima sezione.
  - name: Imposta l'allineamento del paragrafo al centro in modo che il testo del
      piè di pagina sia centrato.
    text: Imposta l'allineamento del paragrafo al centro in modo che il testo del
      piè di pagina sia centrato.
  - name: Scrivi l'etichetta "Page " e inserisci un campo PAGE che visualizza il numero
      di pagina corrente.
    text: Scrivi l'etichetta "Page " e inserisci un campo PAGE che visualizza il numero
      di pagina corrente.
  - name: Scrivi " of " e inserisci un campo NUMPAGES che mostra il conteggio totale
      delle pagine.
    text: Scrivi " of " e inserisci un campo NUMPAGES che mostra il conteggio totale
      delle pagine.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: No. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` sposta il builder
      solo al piè di pagina primario della *prima* sezione, quindi i campi vengono
      inseriti solo lì.
    question: Se il documento ha più di una sezione, questo codice aggiungerà i numeri
      di pagina al piè di pagina di ogni sezione?
  - answer: Imposta `builder.ParagraphFormat.Alignment` su un altro valore `ParagraphAlignment`
      (ad es., `ParagraphAlignment.Right`) prima di scrivere i campi.
    question: Come posso cambiare l'allineamento del paragrafo del numero di pagina
      nel piè di pagina?
  - answer: '`InsertField` accetta il codice del campo e un risultato opzionale; passare
      `null` indica ad Aspose.Words di lasciare che Word calcoli il risultato a runtime.'
    question: Cosa rappresenta l'argomento `null` in `InsertField("PAGE", null)`?
  - answer: Sì—sostituisci `HeaderFooterType.FooterPrimary` con `HeaderFooterType.HeaderPrimary`
      (o un altro tipo di intestazione) prima di inserire i campi.
    question: Posso inserire gli stessi campi "Page X of Y" nell'intestazione invece
      che nel piè di pagina?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/add-page-numbers/og-image.png
og_title: Inserisci numeri di pagina automatici nel piè di pagina di Word
og_description: Codice passo‑paso per aggiungere numeri di pagina in tempo reale a un piè di pagina Word con Aspose.Words per .NET.
og_image_alt: Guida che mostra come aggiungere numeri di pagina automatici al piè di pagina di un documento Word usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi numeri di pagina al piè di pagina di un documento Word usando Aspose.Words per .NET
Questo tutorial mostra come utilizzare Aspose.Words Document e DocumentBuilder per inserire numeri di pagina aggiornati automaticamente nel piè di pagina primario di un documento Word. Aggiungendo i numeri di pagina programmaticamente, garantisci una paginazione coerente in tutto il file senza modifiche manuali. Il codice di esempio è pronto per essere eseguito in un ambiente .NET.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/add-page-numbers" >}}


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

**Q: Se il documento ha più di una sezione, questo codice aggiungerà i numeri di pagina al piè di pagina di ogni sezione?**  
A: No. `MoveToHeaderFooter(HeaderFooterType.FooterPrimary)` sposta il builder solo al piè di pagina primario della *prima* sezione, quindi i campi vengono inseriti solo lì.

**Q: Come posso cambiare l'allineamento del paragrafo del numero di pagina nel piè di pagina?**  
A: Imposta `builder.ParagraphFormat.Alignment` su un altro valore `ParagraphAlignment` (ad es., `ParagraphAlignment.Right`) prima di scrivere i campi.

**Q: Cosa rappresenta l'argomento `null` in `InsertField("PAGE", null)`?**  
A: `InsertField` accetta il codice del campo e un risultato opzionale; passare `null` indica ad Aspose.Words di lasciare che Word calcoli il risultato a runtime.

**Q: Posso inserire gli stessi campi "Page X of Y" nell'intestazione invece che nel piè di pagina?**  
A: Sì—sostituisci `HeaderFooterType.FooterPrimary` con `HeaderFooterType.HeaderPrimary` (o un altro tipo di intestazione) prima di inserire i campi.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}