---
title: Aggiungi una Serie di Dati Nominata a un Grafico a Istogramma in Word usando Aspose.Words per .NET
weight: 610
limit:
description: Scopri come incorporare un grafico a istogramma in un documento Word e aggiungere una serie di dati nominata con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, add named series chart, histogram chart in Word, ChartSeriesCollection Add overload, DocumentBuilder chart example, named data series Word]
url: /net/programming-with-charts/add-named-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Scopri come incorporare un grafico a istogramma in un documento Word
    e aggiungere una serie di dati nominata con Aspose.Words per .NET.
  headline: Aggiungi una Serie di Dati Nominata a un Grafico a Istogramma in Word
    usando Aspose.Words per .NET
  type: TechArticle
- description: Scopri come incorporare un grafico a istogramma in un documento Word
    e aggiungere una serie di dati nominata con Aspose.Words per .NET.
  name: Aggiungi una Serie di Dati Nominata a un Grafico a Istogramma in Word usando
    Aspose.Words per .NET
  steps:
  - name: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
    text: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
  - name: Inserisci una forma di grafico a istogramma di dimensioni 500×300 nel documento
      e ottieni il relativo oggetto Chart.
    text: Inserisci una forma di grafico a istogramma di dimensioni 500×300 nel documento
      e ottieni il relativo oggetto Chart.
  - name: Rimuovi la serie segnaposto predefinita che Aspose.Words aggiunge ai nuovi
      grafici.
    text: Rimuovi la serie segnaposto predefinita che Aspose.Words aggiunge ai nuovi
      grafici.
  - name: Aggiungi una serie denominata "Demo Series" con i punti dati specificati
      al grafico a istogramma.
    text: Aggiungi una serie denominata "Demo Series" con i punti dati specificati
      al grafico a istogramma.
  - name: Salva il documento in un file .docx contenente la serie di grafico etichettata.
    text: Salva il documento in un file .docx contenente la serie di grafico etichettata.
  type: HowTo
- questions:
  - answer: '`InsertChart` crea una serie segnaposto predefinita; cancellandola rimuove
      quella serie vuota così il grafico mostra solo i dati che aggiungi con `Series.Add`.'
    question: Perché devo chiamare `histogramChart.Series.Clear()` prima di aggiungere
      le mie serie?
  - answer: Sì, chiama `histogramChart.Series.Add` più volte, ciascuna con un nome
      distinto e valori `double[]`; ogni serie sarà elencata nella legenda del grafico
      con il nome fornito.
    question: Posso aggiungere più di una serie usando lo stesso sovraccarico, e ciascuna
      apparirà con la propria etichetta?
  - answer: Il sovraccarico si aspetta un `double[]`; se hai `int[]` o altri array
      numerici, converti o castali a `double[]` prima di passarli.
    question: L'argomento `double[]` è l'unico tipo accettato per i punti dati?
  - answer: La stringa passata come primo argomento (ad esempio "Demo Series") è usata
      come titolo della serie ed è visualizzata nella legenda del grafico per impostazione
      predefinita.
    question: Il nome della serie che fornisco apparirà automaticamente nel grafico?
  type: FAQPage
images:
- /net/programming-with-charts/add-named-series/og-image.png
og_title: Aggiungi una Serie Nominata a un Grafico a Istogramma di Word
og_description: Etichetta rapidamente una serie di grafico in Word con Aspose.Words e vedi il risultato renderizzato istantaneamente.
og_image_alt: Screenshot che mostra un documento Word con un grafico a istogramma che include una serie di dati etichettata creata usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi una Serie di Dati Nominata a un Grafico a Istogramma in Word usando Aspose.Words per .NET
Questo tutorial dimostra come creare un documento Word con Aspose.Words per .NET, inserire un grafico a istogramma e aggiungere una serie di dati etichettata usando il sovraccarico ChartSeriesCollection.Add che accetta un nome e dei valori. Assegnando un nome alla serie è possibile identificare chiaramente ogni insieme di dati nel grafico, rendendo l'output visivo più facile da leggere e interpretare.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/add-named-series" >}}


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

**Q: Perché devo chiamare `histogramChart.Series.Clear()` prima di aggiungere le mie serie?**  
A: `InsertChart` crea una serie segnaposto predefinita; cancellandola rimuove quella serie vuota così il grafico mostra solo i dati che aggiungi con `Series.Add`.

**Q: Posso aggiungere più di una serie usando lo stesso sovraccarico, e ciascuna apparirà con la propria etichetta?**  
A: Sì, chiama `histogramChart.Series.Add` più volte, ciascuna con un nome distinto e valori `double[]`; ogni serie sarà elencata nella legenda del grafico con il nome fornito.

**Q: L'argomento `double[]` è l'unico tipo accettato per i punti dati?**  
A: Il sovraccarico si aspetta un `double[]`; se hai `int[]` o altri array numerici, converti o castali a `double[]` prima di passarli.

**Q: Il nome della serie che fornisco apparirà automaticamente nel grafico?**  
A: La stringa passata come primo argomento (ad esempio "Demo Series") è usata come titolo della serie ed è visualizzata nella legenda del grafico per impostazione predefinita.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}