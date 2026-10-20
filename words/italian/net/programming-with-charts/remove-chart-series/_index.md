---
title: Rimuovi una Chart Series da un Word Document utilizzando Aspose.Words for .NET
weight: 510
limit:
description: Scopri come eliminare una serie di dati specifica da un grafico a colonne in un Word Document con Aspose.Words for .NET.
keywords: [Aspose.Words for .NET, remove chart series, ChartSeriesCollection.RemoveAt, column chart manipulation, Word document chart editing, C# chart series removal]
url: /net/programming-with-charts/remove-chart-series/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Scopri come eliminare una serie di dati specifica da un grafico a colonne
    in un Word Document con Aspose.Words for .NET.
  headline: Rimuovi una Chart Series da un Word Document utilizzando Aspose.Words
    for .NET
  type: TechArticle
- description: Scopri come eliminare una serie di dati specifica da un grafico a colonne
    in un Word Document con Aspose.Words for .NET.
  name: Rimuovi una Chart Series da un Word Document utilizzando Aspose.Words for
    .NET
  steps:
  - name: Crea un nuovo Word Document e un DocumentBuilder collegato ad esso.
    text: Crea un nuovo Word Document e un DocumentBuilder collegato ad esso.
  - name: Inserisci un grafico a colonne di dimensioni 432×252 punti e ottieni l'oggetto
      Chart per ulteriori manipolazioni.
    text: Inserisci un grafico a colonne di dimensioni 432×252 punti e ottieni l'oggetto
      Chart per ulteriori manipolazioni.
  - name: Definisci l'indice basato su zero della serie da rimuovere (la seconda serie).
    text: Definisci l'indice basato su zero della serie da rimuovere (la seconda serie).
  - name: Se l'indice è valido, chiama RemoveAt sulla collezione Series del grafico
      per eliminare quella serie.
    text: Se l'indice è valido, chiama RemoveAt sulla collezione Series del grafico
      per eliminare quella serie.
  - name: Salva il documento aggiornato in un file .docx.
    text: Salva il documento aggiornato in un file .docx.
  type: HowTo
- questions:
  - answer: Il controllo `if` (`targetSeriesIdx < columnChart.Series.Count`) fallirà,
      quindi `RemoveAt` non verrà mai chiamato e il grafico rimarrà invariato.
    question: Cosa succede se passo un indice uguale al numero di serie nel grafico?
  - answer: Sì, dopo `columnChart.Series.RemoveAt` la legenda viene rigenerata per
      riflettere le serie rimanenti, quindi la voce rimossa scompare dalla legenda.
    question: La rimozione di una serie aggiorna automaticamente la legenda del grafico?
  - answer: Il codice funziona per qualsiasi tipo di grafico che supporti una collezione
      `Series`; basta cambiare `ChartType.Column` nel tipo desiderato quando si inserisce
      il grafico.
    question: Posso usare lo stesso codice per eliminare una serie da un grafico a
      linee o a torta?
  - answer: Un grafico senza serie è comunque una `Shape` valida e verrà salvato,
      ma apparirà vuoto nel documento risultante.
    question: Se rimuovo l'unica serie in un grafico, il grafico verrà comunque salvato
      correttamente?
  type: FAQPage
images:
- /net/programming-with-charts/remove-chart-series/og-image.png
og_title: Elimina una Chart Series in un Word Document
og_description: Guida passo‑passo per rimuovere una serie di dati da un grafico Word usando Aspose.Words for .NET.
og_image_alt: Guida che mostra come eliminare una serie di dati specifica da un grafico a colonne in un Word Document usando Aspose.Words for .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Rimuovi una Chart Series da un Word Document utilizzando Aspose.Words
Questo tutorial mostra come creare un Word Document, aggiungere un grafico a colonne con DocumentBuilder e quindi eliminare una serie di dati specifica da quel grafico utilizzando il metodo ChartSeriesCollection.RemoveAt. Alla fine avrai un documento salvato con la serie indesiderata rimossa, offrendoti un controllo preciso sul contenuto del grafico direttamente dal codice .NET.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/remove-chart-series" >}}


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

**Q: Cosa succede se passo un indice uguale al numero di serie nel grafico?**  
A: Il controllo `if` (`targetSeriesIdx < columnChart.Series.Count`) fallirà, quindi `RemoveAt` non verrà mai chiamato e il grafico rimarrà invariato.

**Q: La rimozione di una serie aggiorna automaticamente la legenda del grafico?**  
A: Sì, dopo `columnChart.Series.RemoveAt` la legenda viene rigenerata per riflettere le serie rimanenti, quindi la voce rimossa scompare dalla legenda.

**Q: Posso usare lo stesso codice per eliminare una serie da un grafico a linee o a torta?**  
A: Il codice funziona per qualsiasi tipo di grafico che supporti una collezione `Series`; basta cambiare `ChartType.Column` nel tipo desiderato quando si inserisce il grafico.

**Q: Se rimuovo l'unica serie in un grafico, il grafico verrà comunque salvato correttamente?**  
A: Un grafico senza serie è comunque una `Shape` valida e verrà salvato, ma apparirà vuoto nel documento risultante.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}