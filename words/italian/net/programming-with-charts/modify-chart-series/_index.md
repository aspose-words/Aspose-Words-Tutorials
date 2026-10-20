---
title: Aggiorna i dati delle serie del grafico in un documento Word utilizzando Aspose.Words per .NET
weight: 610
limit:
description: Impara a modificare i punti dati delle serie del grafico in un documento Word e a aggiornare il grafico utilizzando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, modify chart series, update chart data points, Word chart manipulation, C# chart editing, column chart in Word]
url: /net/programming-with-charts/modify-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara a modificare i punti dati delle serie del grafico in un documento
    Word e a aggiornare il grafico utilizzando Aspose.Words per .NET.
  headline: Aggiorna i dati delle serie del grafico in un documento Word utilizzando
    Aspose.Words per .NET
  type: TechArticle
- description: Impara a modificare i punti dati delle serie del grafico in un documento
    Word e a aggiornare il grafico utilizzando Aspose.Words per .NET.
  name: Aggiorna i dati delle serie del grafico in un documento Word utilizzando Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo Document, inserisci un grafico a colonne con un DocumentBuilder
      e salvalo come file iniziale.
    text: Crea un nuovo Document, inserisci un grafico a colonne con un DocumentBuilder
      e salvalo come file iniziale.
  - name: Apri il file salvato e individua la forma del grafico per ottenere l'oggetto
      Chart esistente.
    text: Apri il file salvato e individua la forma del grafico per ottenere l'oggetto
      Chart esistente.
  - name: Cancella i valori della prima serie e aggiungi nuovi punti, quindi regola
      la seconda serie rimuovendo il suo primo punto e aggiungendone uno nuovo.
    text: Cancella i valori della prima serie e aggiungi nuovi punti, quindi regola
      la seconda serie rimuovendo il suo primo punto e aggiungendone uno nuovo.
  - name: Salva il documento modificato in un nuovo file contenente il grafico aggiornato.
    text: Salva il documento modificato in un nuovo file contenente il grafico aggiornato.
  type: HowTo
- questions:
  - answer: Usa `document.GetChildNodes(NodeType.Shape, true)` per ottenere tutte
      le forme, poi filtra con `s.HasChart` e scegli la prima (o quella di cui hai
      bisogno) – questo evita di selezionare immagini o caselle di testo non correlate.
    question: Come posso individuare in modo affidabile la forma del grafico in un
      documento che può contenere altre forme?
  - answer: '`ClearValues()` rimuove i punti dati esistenti; senza di esso i nuovi
      punti vengono aggiunti a quelli vecchi, il che può generare categorie duplicate
      o totali errati.'
    question: Perché devo chiamare `ClearValues()` prima di aggiungere nuovi punti
      a una serie?
  - answer: Usa `FromString` quando le categorie dell'asse X del grafico sono testuali
      (ad esempio \"Group A\"), e `FromDouble` quando l'asse si aspetta valori numerici
      come date o misurazioni.
    question: Quando dovrei usare `ChartXValue.FromString` rispetto a `ChartXValue.FromDouble`
      per i valori dell'asse X?
  - answer: Tentare di accedere a una serie inesistente genera un `ArgumentOutOfRangeException`;
      controlla sempre `existingChart.Series.Count` prima di fare riferimento a un
      indice specifico.
    question: Cosa succede se il grafico ha una sola serie e provo ad accedere a `existingChart.Series[1]`?
  - answer: Salvare `openedDoc` è sufficiente perché è l'istanza del documento che
      contiene il grafico modificato; il `document` originale è stato usato solo per
      creare il file iniziale.
    question: Devo risalvare il `document` originale dopo aver modificato il grafico,
      o è sufficiente salvare `openedDoc`?
  type: FAQPage
images:
- /net/programming-with-charts/modify-chart-series/og-image.png
og_title: Modifica i dati delle serie del grafico in Word
og_description: Guida passo‑passo per modificare i valori delle serie di un grafico in un file Word con Aspose.Words per .NET.
og_image_alt: Guida che mostra un documento Word con un grafico a colonne prima e dopo l'aggiornamento dei dati delle sue serie usando Aspose.Words per .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiorna i dati delle serie del grafico in un documento Word utilizzando Aspose.Words per .NET
Questo tutorial mostra come creare un documento Word contenente un grafico a colonne, quindi riaprire il file, recuperare le serie del grafico esistenti, modificare i loro punti dati e salvare il documento in modo che il grafico visualizzi i nuovi valori. Segui il codice passo‑passo per vedere quanto sia semplice regolare programmaticamente i dati del grafico con Aspose.Words per .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/modify-chart-series" >}}


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

**Q: Come posso individuare in modo affidabile la forma del grafico in un documento che può contenere altre forme?**  
A: Usa `document.GetChildNodes(NodeType.Shape, true)` per ottenere tutte le forme, poi filtra con `s.HasChart` e scegli la prima (o quella di cui hai bisogno) – questo evita di selezionare immagini o caselle di testo non correlate.

**Q: Perché devo chiamare `ClearValues()` prima di aggiungere nuovi punti a una serie?**  
A: `ClearValues()` rimuove i punti dati esistenti; senza di esso i nuovi punti vengono aggiunti a quelli vecchi, il che può generare categorie duplicate o totali errati.

**Q: Quando dovrei usare `ChartXValue.FromString` rispetto a `ChartXValue.FromDouble` per i valori dell'asse X?**  
A: Usa `FromString` quando le categorie dell'asse X del grafico sono testuali (ad esempio \"Group A\"), e `FromDouble` quando l'asse si aspetta valori numerici come date o misurazioni.

**Q: Cosa succede se il grafico ha una sola serie e provo ad accedere a `existingChart.Series[1]`?**  
A: Tentare di accedere a una serie inesistente genera un `ArgumentOutOfRangeException`; controlla sempre `existingChart.Series.Count` prima di fare riferimento a un indice specifico.

**Q: Devo risalvare il `document` originale dopo aver modificato il grafico, o è sufficiente salvare `openedDoc`?**  
A: Salvare `openedDoc` è sufficiente perché è l'istanza del documento che contiene il grafico modificato; il `document` originale è stato usato solo per creare il file iniziale.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}