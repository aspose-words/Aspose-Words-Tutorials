---
title: Crea una filigrana di testo diagonale con font personalizzato in un documento Word utilizzando Aspose.Words per .NET
weight: 210
limit:
description: Codice passo‑passo per aggiungere una filigrana di testo diagonale con font personalizzato a un file Word .docx utilizzando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, diagonal text watermark, custom font watermark, Word document watermark, Document.Watermark.SetText, C# watermark API]
url: /net/programming-with-watermark/add-diagonal-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Codice passo‑passo per aggiungere una filigrana di testo diagonale
    con font personalizzato a un file Word .docx utilizzando Aspose.Words per .NET.
  headline: Crea una filigrana di testo diagonale con font personalizzato in un documento
    Word utilizzando Aspose.Words per .NET
  type: TechArticle
- description: Codice passo‑passo per aggiungere una filigrana di testo diagonale
    con font personalizzato a un file Word .docx utilizzando Aspose.Words per .NET.
  name: Crea una filigrana di testo diagonale con font personalizzato in un documento
    Word utilizzando Aspose.Words per .NET
  steps:
  - name: Crea una nuova istanza vuota di documento Word denominata `document`.
    text: Crea una nuova istanza vuota di documento Word denominata `document`.
  - name: Configura `watermarkSettings` con carattere Arial 48 pt grigio, layout diagonale
      e rendering opaco.
    text: Configura `watermarkSettings` con carattere Arial 48 pt grigio, layout diagonale
      e rendering opaco.
  - name: Applica la filigrana di testo "Private" a `document` utilizzando le impostazioni
      precedentemente definite.
    text: Applica la filigrana di testo "Private" a `document` utilizzando le impostazioni
      precedentemente definite.
  - name: Definisci il percorso file in cui verrà salvato il documento con filigrana.
    text: Definisci il percorso file in cui verrà salvato il documento con filigrana.
  - name: Salva il `document` modificato nel percorso specificato come file .docx.
    text: Salva il `document` modificato nel percorso specificato come file .docx.
  type: HowTo
- questions:
  - answer: '`IsSemitrasparent` determina se la filigrana viene renderizzata con opacità
      parziale; impostandolo su `false` la filigrana è completamente opaca, mentre
      `true` applica un effetto semi‑trasparente predefinito.'
    question: Cosa controlla il flag **IsSemitrasparent** in `TextWatermarkOptions`?
  - answer: Sì—imposta la proprietà `Layout` su `WatermarkLayout.Horizontal` (o un
      altro valore enum) prima di chiamare `document.Watermark.SetText`.
    question: Posso cambiare l'orientamento della filigrana in orizzontale anziché
      diagonale?
  - answer: Word tornerà al suo font predefinito per la filigrana, quindi il testo
      apparirà comunque ma potrebbe avere un aspetto diverso dallo stile previsto.
    question: Cosa succede se la `FontFamily` specificata (ad es., "Arial") non è
      installata sulla macchina di destinazione?
  - answer: Carica il file esistente con `Document document = new Document("Existing.docx");`
      quindi configura `TextWatermarkOptions` e chiama `document.Watermark.SetText`
      come mostrato.
    question: È possibile aggiungere una filigrana a un file `.docx` esistente invece
      di crearne uno nuovo?
  type: FAQPage
images:
- /net/programming-with-watermark/add-diagonal-text-watermark/og-image.png
og_title: Aggiungi una filigrana di testo diagonale con font personalizzato
og_description: Impara a inserire una filigrana di testo inclinata con il tuo font in un file Word in pochi minuti.
og_image_alt: Guida che mostra come aggiungere una filigrana di testo diagonale con font personalizzato a un documento Word utilizzando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crea una filigrana di testo diagonale con font personalizzato in un documento Word utilizzando Aspose.Words per .NET
Questo tutorial ti guida nella creazione di un nuovo documento Word, nella configurazione di una filigrana di testo diagonale con le impostazioni di font scelte, nella sua applicazione tramite l'API Document.Watermark.SetText e nel salvataggio del risultato come file .docx. Alla fine avrai un documento professionalmente filigranato che mostra il tuo marchio o la tua proprietà. Il codice passo‑passo è pronto per essere copiato in qualsiasi progetto .NET.

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

**Q: Cosa controlla il flag **IsSemitrasparent** in `TextWatermarkOptions`?**  
A: `IsSemitrasparent` determina se la filigrana viene renderizzata con opacità parziale; impostandolo su `false` la filigrana è completamente opaca, mentre `true` applica un effetto semi‑trasparente predefinito.

**Q: Posso cambiare l'orientamento della filigrana in orizzontale anziché diagonale?**  
A: Sì—imposta la proprietà `Layout` su `WatermarkLayout.Horizontal` (o un altro valore enum) prima di chiamare `document.Watermark.SetText`.

**Q: Cosa succede se la `FontFamily` specificata (ad es., "Arial") non è installata sulla macchina di destinazione?**  
A: Word tornerà al suo font predefinito per la filigrana, quindi il testo apparirà comunque ma potrebbe avere un aspetto diverso dallo stile previsto.

**Q: È possibile aggiungere una filigrana a un file `.docx` esistente invece di crearne uno nuovo?**  
A: Carica il file esistente con `Document document = new Document("Existing.docx");` quindi configura `TextWatermarkOptions` e chiama `document.Watermark.SetText` come mostrato.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}