---
title: Ridimensiona il grafico proporzionalmente cambiando il formato della pagina in Word con Aspose.Words per .NET
weight: 210
limit:
description: Impara a ridimensionare automaticamente un grafico a colonne di Word quando si cambia il documento in A4 usando Aspose.Words per .NET.
keywords: [chart resizing, Aspose.Words for .NET, Word column chart, automatic chart scaling, A4 page size, resize chart in Word]
url: /net/programming-with-charts/resize-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara a ridimensionare automaticamente un grafico a colonne di Word
    quando si cambia il documento in A4 usando Aspose.Words per .NET.
  headline: Ridimensiona il grafico proporzionalmente cambiando il formato della pagina
    in Word con Aspose.Words per .NET
  type: TechArticle
- description: Impara a ridimensionare automaticamente un grafico a colonne di Word
    quando si cambia il documento in A4 usando Aspose.Words per .NET.
  name: Ridimensiona il grafico proporzionalmente cambiando il formato della pagina
    in Word con Aspose.Words per .NET
  steps:
  - name: Crea un nuovo oggetto Document e un DocumentBuilder per modificarlo.
    text: Crea un nuovo oggetto Document e un DocumentBuilder per modificarlo.
  - name: Inserisci un grafico a colonne di dimensione 432×252 punti e ottieni il
      suo oggetto Chart.
    text: Inserisci un grafico a colonne di dimensione 432×252 punti e ottieni il
      suo oggetto Chart.
  - name: Imposta il testo del titolo del grafico su "Quarterly Revenue" e rendilo
      visibile.
    text: Imposta il testo del titolo del grafico su "Quarterly Revenue" e rendilo
      visibile.
  - name: Salva il documento in un file mostrando le dimensioni originali del grafico.
    text: Salva il documento in un file mostrando le dimensioni originali del grafico.
  - name: Cambia il formato della carta del documento in A4 e aggiorna il layout.
    text: Cambia il formato della carta del documento in A4 e aggiorna il layout.
  - name: Calcola una nuova larghezza del grafico pari all'80 % della larghezza della
      pagina mantenendo il rapporto d'aspetto originale.
    text: Calcola una nuova larghezza del grafico pari all'80 % della larghezza della
      pagina mantenendo il rapporto d'aspetto originale.
  - name: Se la forma contiene un grafico, applica la larghezza e l'altezza calcolate
      per ridimensionarla.
    text: Se la forma contiene un grafico, applica la larghezza e l'altezza calcolate
      per ridimensionarla.
  - name: Salva il documento dopo che il grafico è stato ridimensionato per riflettere
      il nuovo formato della pagina.
    text: Salva il documento dopo che il grafico è stato ridimensionato per riflettere
      il nuovo formato della pagina.
  type: HowTo
- questions:
  - answer: Sì. Cambiare `docBuilder.PageSetup.PaperSize` non regola automaticamente
      le forme esistenti, quindi devi ricalcolare e assegnare `chartContainer.Width`
      e `Height` manualmente come mostrato.
    question: Devo ridimensionare manualmente il grafico dopo aver cambiato il formato
      della carta del documento?
  - answer: Memorizza `originalAspectRatio = chartContainer.Height / chartContainer.Width`
      e poi calcola `newChartHeight = newChartWidth * originalAspectRatio` dopo aver
      determinato la nuova larghezza.
    question: Come fa il codice a mantenere il rapporto originale larghezza‑altezza
      del grafico durante il ridimensionamento?
  - answer: '`UpdatePageLayout()` forza il motore di layout a rivalutare le dimensioni
      della pagina, assicurando che `docBuilder.PageSetup.PageWidth` rifletta la nuova
      larghezza A4 prima che le dimensioni del grafico vengano ricalcolate.'
    question: Perché `myDoc.UpdatePageLayout()` viene chiamato dopo aver impostato
      il formato della carta su A4?
  - answer: Il controllo `if (chartContainer.HasChart)` impedisce al codice di assegnare
      `Width` e `Height` quando non è presente alcun grafico, evitando un'eccezione
      a runtime.
    question: Cosa succede se la forma inserita non contiene effettivamente un grafico?
  - answer: Assolutamente—sostituisci il moltiplicatore `0.8` con qualsiasi proporzione
      tu preferisca; il resto della logica di ridimensionamento manterrà comunque
      il rapporto d'aspetto originale.
    question: Posso cambiare il fattore di scala dell'80 % con un valore diverso?
  type: FAQPage
images:
- /net/programming-with-charts/resize-chart/og-image.png
og_title: Ridimensiona un grafico Word passando a A4
og_description: Mantieni il tuo grafico proporzionale ridimensionandolo automaticamente dopo aver cambiato il documento in A4.
og_image_alt: Screenshot che mostra un grafico a colonne ridimensionato automaticamente per adattarsi a un documento Word formato A4 usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ridimensiona il grafico proporzionalmente cambiando il formato della pagina in Word con Aspose.Words per .NET
Questo tutorial mostra come inserire un grafico a colonne in un documento Word, cambiare il formato della pagina del documento in A4 e far ridimensionare automaticamente il grafico in modo che rimanga proporzionale alla nuova larghezza della pagina. Seguendo i passaggi, vedrai il grafico adattare le sue dimensioni senza ridimensionamento manuale, garantendo un layout coerente su diversi formati di pagina.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/resize-chart" >}}


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

**Q: Devo ridimensionare manualmente il grafico dopo aver cambiato il formato della carta del documento?**  
A: Sì. Cambiare `docBuilder.PageSetup.PaperSize` non regola automaticamente le forme esistenti, quindi devi ricalcolare e assegnare `chartContainer.Width` e `Height` manualmente come mostrato.

**Q: Come fa il codice a mantenere il rapporto originale larghezza‑altezza del grafico durante il ridimensionamento?**  
A: Memorizza `originalAspectRatio = chartContainer.Height / chartContainer.Width` e poi calcola `newChartHeight = newChartWidth * originalAspectRatio` dopo aver determinato la nuova larghezza.

**Q: Perché `myDoc.UpdatePageLayout()` viene chiamato dopo aver impostato il formato della carta su A4?**  
A: `UpdatePageLayout()` forza il motore di layout a rivalutare le dimensioni della pagina, assicurando che `docBuilder.PageSetup.PageWidth` rifletta la nuova larghezza A4 prima che le dimensioni del grafico vengano ricalcolate.

**Q: Cosa succede se la forma inserita non contiene effettivamente un grafico?**  
A: Il controllo `if (chartContainer.HasChart)` impedisce al codice di assegnare `Width` e `Height` quando non è presente alcun grafico, evitando un'eccezione a runtime.

**Q: Posso cambiare il fattore di scala dell'80 % con un valore diverso?**  
A: Assolutamente—sostituisci il moltiplicatore `0.8` con qualsiasi proporzione tu preferisca; il resto della logica di ridimensionamento manterrà comunque il rapporto d'aspetto originale.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}