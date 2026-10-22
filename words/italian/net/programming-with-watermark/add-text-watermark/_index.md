---
title: Aggiungi una filigrana di testo rossa diagonale ai documenti Word usando Aspose.Words per .NET
weight: 110
limit:
description: Applica automaticamente una filigrana di testo rossa diagonale a ogni file Word generato in batch usando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, text watermark, red diagonal watermark, batch document generation, DocumentBuilder watermark, automated report]
url: /net/programming-with-watermark/add-text-watermark/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Applica automaticamente una filigrana di testo rossa diagonale a ogni
    file Word generato in batch usando Aspose.Words per .NET.
  headline: Aggiungi una filigrana di testo rossa diagonale ai documenti Word usando
    Aspose.Words per .NET
  type: TechArticle
- description: Applica automaticamente una filigrana di testo rossa diagonale a ogni
    file Word generato in batch usando Aspose.Words per .NET.
  name: Aggiungi una filigrana di testo rossa diagonale ai documenti Word usando Aspose.Words
    per .NET
  steps:
  - name: Crea la cartella "GeneratedReports" dove verranno salvati i file di output.
    text: Crea la cartella "GeneratedReports" dove verranno salvati i file di output.
  - name: Avvia un ciclo che genererà tre documenti separati.
    text: Avvia un ciclo che genererà tre documenti separati.
  - name: Crea un nuovo oggetto documento Word vuoto.
    text: Crea un nuovo oggetto documento Word vuoto.
  - name: Usa DocumentBuilder per scrivere una riga di titolo e una descrizione nel
      documento.
    text: Usa DocumentBuilder per scrivere una riga di titolo e una descrizione nel
      documento.
  - name: Definisci l'aspetto della filigrana, includendo font, dimensione, colore
      e layout diagonale.
    text: Definisci l'aspetto della filigrana, includendo font, dimensione, colore
      e layout diagonale.
  - name: Applica la filigrana rossa diagonale configurata con il testo "PROTECTED"
      al documento.
    text: Applica la filigrana rossa diagonale configurata con il testo "PROTECTED"
      al documento.
  - name: Salva il documento con filigrana nella cartella "GeneratedReports" con un
      nome file univoco.
    text: Salva il documento con filigrana nella cartella "GeneratedReports" con un
      nome file univoco.
  - name: Chiudi il ciclo dopo aver elaborato il documento corrente.
    text: Chiudi il ciclo dopo aver elaborato il documento corrente.
  type: HowTo
- questions:
  - answer: IsSemitrasparent determina se la filigrana viene renderizzata con opacità
      parziale; impostarla su **true** rende il testo semi‑trasparente così il contenuto
      sottostante rimane più leggibile.
    question: Cosa controlla l'opzione **IsSemitrasparent** e quale effetto ha impostarla
      su **true**?
  - answer: Sì—imposta la proprietà **Layout** su **WatermarkLayout.Horizontal** in
      **TextWatermarkOptions** prima di chiamare **document.Watermark.SetText**.
    question: Posso cambiare l'orientamento della filigrana in orizzontale invece
      che diagonale?
  - answer: Lo snippet crea una nuova istanza di **Document**, ma è possibile aprire
      qualsiasi file esistente (ad es., `new Document("Existing.docx")`) e poi chiamare
      **document.Watermark.SetText** per applicare la stessa filigrana.
    question: Questo codice aggiungerà una filigrana a un file Word esistente o solo
      a documenti appena creati?
  - answer: Assegna un colore personalizzato con **Color.FromArgb(red, green, blue)**
      alla proprietà **Color** di **TextWatermarkOptions**, ad esempio `Color = Color.FromArgb(128,
      0, 128)` per il viola.
    question: Come posso usare un colore RGB personalizzato per la filigrana invece
      del **Color.Red** predefinito?
  type: FAQPage
images:
- /net/programming-with-watermark/add-text-watermark/og-image.png
og_title: Aggiungi una filigrana di testo rossa diagonale ai documenti Word
og_description: Scopri come auto‑applicare una filigrana rossa diagonale a ciascun documento Word in batch con Aspose.Words.
og_image_alt: Guida che mostra come aggiungere una filigrana di testo rossa diagonale ai documenti Word usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi una filigrana di testo rossa diagonale ai documenti Word usando Aspose.Words per .NET
Questo tutorial dimostra come incorporare automaticamente una filigrana di testo rossa diagonale in ogni documento Word creato durante la generazione di report batch. Utilizzando le classi Document e DocumentBuilder di Aspose.Words per .NET, la filigrana viene applicata programmaticamente mentre i file vengono prodotti, garantendo che ogni documento riporti lo stesso branding o avviso di riservatezza senza sforzo manuale.

---

{{< tutorial-widget sourcePath="words/net/programming-with-watermark/add-text-watermark" >}}


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

**Q: Cosa controlla l'opzione **IsSemitrasparent** e quale effetto ha impostarla su **true**?**  
A: IsSemitrasparent determina se la filigrana viene renderizzata con opacità parziale; impostarla su **true** rende il testo semi‑trasparente così il contenuto sottostante rimane più leggibile.

**Q: Posso cambiare l'orientamento della filigrana in orizzontale invece che diagonale?**  
A: Sì—imposta la proprietà **Layout** su **WatermarkLayout.Horizontal** in **TextWatermarkOptions** prima di chiamare **document.Watermark.SetText**.

**Q: Questo codice aggiungerà una filigrana a un file Word esistente o solo a documenti appena creati?**  
A: Lo snippet crea una nuova istanza di **Document**, ma è possibile aprire qualsiasi file esistente (ad es., `new Document("Existing.docx")`) e poi chiamare **document.Watermark.SetText** per applicare la stessa filigrana.

**Q: Come posso usare un colore RGB personalizzato per la filigrana invece del **Color.Red** predefinito?**  
A: Assegna un colore personalizzato con **Color.FromArgb(red, green, blue)** alla proprietà **Color** di **TextWatermarkOptions**, ad esempio `Color = Color.FromArgb(128, 0, 128)` per il viola.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}