---
title: Aggiungi un commento con collegamento ipertestuale ed esporta come annotazione PDF usando Aspose.Words per .NET
weight: 110
limit:
description: Impara ad aggiungere un commento con collegamento ipertestuale in un file Word ed esportarlo come annotazione PDF con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara ad aggiungere un commento con collegamento ipertestuale in un
    file Word ed esportarlo come annotazione PDF con Aspose.Words per .NET.
  headline: Aggiungi un commento con collegamento ipertestuale ed esporta come annotazione
    PDF usando Aspose.Words per .NET
  type: TechArticle
- description: Impara ad aggiungere un commento con collegamento ipertestuale in un
    file Word ed esportarlo come annotazione PDF con Aspose.Words per .NET.
  name: Aggiungi un commento con collegamento ipertestuale ed esporta come annotazione
    PDF usando Aspose.Words per .NET
  steps:
  - name: Crea un nuovo oggetto Document vuoto e un DocumentBuilder per lavorarci.
    text: Crea un nuovo oggetto Document vuoto e un DocumentBuilder per lavorarci.
  - name: Scrivi una riga di testo visibile che ospiterà il commento imminente.
    text: Scrivi una riga di testo visibile che ospiterà il commento imminente.
  - name: Crea un Comment scritto da Jane Doe e allegalo al primo paragrafo del documento.
    text: Crea un Comment scritto da Jane Doe e allegalo al primo paragrafo del documento.
  - name: All'interno del commento, aggiungi un paragrafo e inserisci un collegamento
      ipertestuale blu e sottolineato al sito web della Aspose.Words Library.
    text: All'interno del commento, aggiungi un paragrafo e inserisci un collegamento
      ipertestuale blu e sottolineato al sito web della Aspose.Words Library.
  - name: Configura il documento per renderizzare i commenti come annotazioni PDF
      e aggiorna il layout.
    text: Configura il documento per renderizzare i commenti come annotazioni PDF
      e aggiorna il layout.
  - name: Crea una cartella "Output" nella directory corrente per memorizzare il PDF
      generato.
    text: Crea una cartella "Output" nella directory corrente per memorizzare il PDF
      generato.
  - name: Salva il documento preparato come file PDF usando PdfSaveOptions.
    text: Salva il documento preparato come file PDF usando PdfSaveOptions.
  - name: Verifica che il file PDF esista e contenga dati, quindi stampa il risultato
      sulla console.
    text: Verifica che il file PDF esista e contenga dati, quindi stampa il risultato
      sulla console.
  type: HowTo
- questions:
  - answer: Il terzo parametro di `InsertHyperlink` specifica se il collegamento deve
      essere trattato come un campo; impostandolo a `false` inserisce un semplice
      collegamento ipertestuale che funziona nell'annotazione PDF senza necessità
      di un codice di campo.
    question: Cosa controlla il terzo argomento (`false`) in `InsertHyperlink`?
  - answer: Imposta `myDocument.LayoutOptions.CommentDisplayMode` su `CommentDisplayMode.ShowInBalloons`
      prima di chiamare `Save`; il PDF conterrà quindi il commento come un commento
      Word normale anziché come un'annotazione.
    question: Come posso far apparire il commento come un balloon nel documento Word
      invece che come un'annotazione PDF?
  - answer: Sì—ogni `Comment` che aggiungi a un paragrafo può contenere la propria
      chiamata a `InsertHyperlink`, e tutti i collegamenti ipertestuali saranno preservati
      come annotazioni PDF separate quando il documento viene salvato.
    question: Se aggiungo più di un commento, ogni collegamento ipertestuale funzionerà
      nel PDF esportato?
  - answer: Apri il PDF generato, individua l'annotazione del commento (di solito
      mostrata come un'icona a forma di nota), cliccaci sopra per rivelare il testo
      del commento e poi clicca sul collegamento blu sottolineato; dovrebbe aprire
      l'URL di destinazione nel browser web.
    question: Come verifico che il collegamento ipertestuale all'interno del commento
      funzioni effettivamente dopo che il PDF è stato generato?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Inserisci commento con collegamento ipertestuale ed esporta in PDF
og_description: Impara a incorporare un collegamento cliccabile in un commento Word e trasformarlo in un'annotazione PDF.
og_image_alt: Guida che mostra come aggiungere un commento con un collegamento ipertestuale cliccabile a un documento Word ed esportarlo come annotazione PDF usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi un commento con collegamento ipertestuale ed esporta come annotazione PDF usando Aspose.Words per .NET
In questo tutorial vedrai come creare un documento Word, inserire un commento che contiene un collegamento ipertestuale cliccabile a un sito web esterno, configurare quel commento affinché appaia come un'annotazione PDF, esportare il documento in PDF e verificare il file PDF risultante. Il codice passo‑passo ti consente di aggiungere commenti ricchi e con link e di preservarli durante la conversione in PDF, facilitando la condivisione di note interattive con i lettori.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


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

**Q: Cosa controlla il terzo argomento (`false`) in `InsertHyperlink`?**  
A: Il terzo parametro di `InsertHyperlink` specifica se il collegamento deve essere trattato come un campo; impostandolo a `false` inserisce un semplice collegamento ipertestuale che funziona nell'annotazione PDF senza necessità di un codice di campo.

**Q: Come posso far apparire il commento come un balloon nel documento Word invece che come un'annotazione PDF?**  
A: Imposta `myDocument.LayoutOptions.CommentDisplayMode` su `CommentDisplayMode.ShowInBalloons` prima di chiamare `Save`; il PDF conterrà quindi il commento come un commento Word normale anziché come un'annotazione.

**Q: Se aggiungo più di un commento, ogni collegamento ipertestuale funzionerà nel PDF esportato?**  
A: Sì—ogni `Comment` che aggiungi a un paragrafo può contenere la propria chiamata a `InsertHyperlink`, e tutti i collegamenti ipertestuali saranno preservati come annotazioni PDF separate quando il documento viene salvato.

**Q: Come verifico che il collegamento ipertestuale all'interno del commento funzioni effettivamente dopo che il PDF è stato generato?**  
A: Apri il PDF generato, individua l'annotazione del commento (di solito mostrata come un'icona a forma di nota), cliccaci sopra per rivelare il testo del commento e poi clicca sul collegamento blu sottolineato; dovrebbe aprire l'URL di destinazione nel browser web.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}