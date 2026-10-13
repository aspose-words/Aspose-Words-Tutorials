---
title: Formatta l'asse Y secondario come valuta in un grafico Word usando Aspose.Words per .NET
weight: 710
limit:
description: Impara ad aggiungere e formattare un asse Y secondario come valuta in un grafico a linee Word con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, format secondary axis, currency axis formatting, Word line chart secondary series, secondary Y axis .NET, chart axis number format]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara ad aggiungere e formattare un asse Y secondario come valuta
    in un grafico a linee Word con Aspose.Words per .NET.
  headline: Formatta l'asse Y secondario come valuta in un grafico Word usando Aspose.Words
    per .NET
  type: TechArticle
- description: Impara ad aggiungere e formattare un asse Y secondario come valuta
    in un grafico a linee Word con Aspose.Words per .NET.
  name: Formatta l'asse Y secondario come valuta in un grafico Word usando Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
    text: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
  - name: Inserisci un grafico a linee di dimensione 450×250 punti nel documento e
      ottieni il suo oggetto Chart.
    text: Inserisci un grafico a linee di dimensione 450×250 punti nel documento e
      ottieni il suo oggetto Chart.
  - name: Rimuovi la serie segnaposto predefinita che Aspose aggiunge a un nuovo grafico.
    text: Rimuovi la serie segnaposto predefinita che Aspose aggiunge a un nuovo grafico.
  - name: Definisci le etichette dei trimestri e aggiungi una serie di dati primaria
      con valori di esempio al grafico.
    text: Definisci le etichette dei trimestri e aggiungi una serie di dati primaria
      con valori di esempio al grafico.
  - name: Crea un gruppo di serie secondario di tipo Line e assegnalo al gruppo di
      assi secondari.
    text: Crea un gruppo di serie secondario di tipo Line e assegnalo al gruppo di
      assi secondari.
  - name: Nascondi l'asse X secondario in modo che sia visibile solo l'asse Y secondario.
    text: Nascondi l'asse X secondario in modo che sia visibile solo l'asse Y secondario.
  - name: Mostra il titolo dell'asse Y secondario e imposta il suo testo su \"Sales
      (USD)\".
    text: Mostra il titolo dell'asse Y secondario e imposta il suo testo su \"Sales
      (USD)\".
  - name: Imposta il formato numerico dell'asse Y secondario su un modello di valuta
      con due cifre decimali e scollegalo dalla formattazione di origine.
    text: Imposta il formato numerico dell'asse Y secondario su un modello di valuta
      con due cifre decimali e scollegalo dalla formattazione di origine.
  - name: Aggiungi una serie ausiliaria al gruppo secondario, fornendo dati che verranno
      tracciati sull'asse Y secondario.
    text: Aggiungi una serie ausiliaria al gruppo secondario, fornendo dati che verranno
      tracciati sull'asse Y secondario.
  - name: Salva il documento completato in un file chiamato ProfitChart.docx nella
      directory corrente.
    text: Salva il documento completato in un file chiamato ProfitChart.docx nella
      directory corrente.
  type: HowTo
- questions:
  - answer: Il grafico manterrà la serie segnaposto predefinita che Aspose.Words inserisce,
      quindi la tua \"Main Series\" personalizzata apparirà accanto a punti dati indesiderati.
    question: Cosa succede se ometto la chiamata `lineChart.Series.Clear()`?
  - answer: Imposta `secondarySeriesGroup.AxisX.Hidden = false;` (o semplicemente
      ometti la riga che lo imposta a `true`).
    question: Come posso visualizzare l'asse X secondario invece di nasconderlo?
  - answer: Sì – cambia la stringa di formato, ad esempio `secondarySeriesGroup.AxisY.NumberFormat.FormatCode
      = \"\\\"€\\\"#,##0.00\";` per gli euro o adatta il modello al tuo locale.
    question: Posso usare un simbolo di valuta diverso o un formato diverso per l'asse
      Y secondario?
  - answer: Quando `IsLinkedToSource` è true l'asse eredita il formato numerico dalla
      fonte dati sottostante, sovrascrivendo qualsiasi `FormatCode` personalizzato;
      impostarlo a false costringe il grafico a utilizzare il formato specificato.
    question: Perché devo impostare `IsLinkedToSource = false` quando applico un formato
      numerico personalizzato?
  - answer: Sì, assegna `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;`
      (o `Right` per il valore predefinito) per controllare su quale lato viene disegnato
      l'asse.
    question: È possibile spostare l'asse Y secondario sul lato sinistro del grafico?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatta l'asse secondario di un Chart come valuta
og_description: Impara ad aggiungere un asse Y secondario a un grafico a linee Word e a formattarlo come valuta con due decimali.
og_image_alt: Screenshot che mostra un grafico a linee Word con un asse Y secondario formattato come valuta usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatta l'asse Y secondario come valuta in un grafico Word usando Aspose.Words per .NET
In questo tutorial vedrai come creare un documento Word, inserire un grafico a linee, aggiungere un asse Y secondario, formattare quell'asse come valuta con due cifre decimali e collegare una serie di dati secondaria ad esso usando Aspose.Words per .NET. Formattare l'asse secondario come valuta ti consente di presentare chiaramente i dati finanziari accanto alla serie primaria. Segui il codice passo‑passo per vedere il grafico renderizzato direttamente nel documento generato.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/format-secondary-axis" >}}


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

**Q: Cosa succede se ometto la chiamata `lineChart.Series.Clear()`?**  
A: Il grafico manterrà la serie segnaposto predefinita che Aspose.Words inserisce, quindi la tua \"Main Series\" personalizzata apparirà accanto a punti dati indesiderati.

**Q: Come posso visualizzare l'asse X secondario invece di nasconderlo?**  
A: Imposta `secondarySeriesGroup.AxisX.Hidden = false;` (o semplicemente ometti la riga che lo imposta a `true`).

**Q: Posso usare un simbolo di valuta diverso o un formato diverso per l'asse Y secondario?**  
A: Sì – cambia la stringa di formato, ad esempio `secondarySeriesGroup.AxisY.NumberFormat.FormatCode = \"\\\"€\\\"#,##0.00\";` per gli euro o adatta il modello al tuo locale.

**Q: Perché devo impostare `IsLinkedToSource = false` quando applico un formato numerico personalizzato?**  
A: Quando `IsLinkedToSource` è true l'asse eredita il formato numerico dalla fonte dati sottostante, sovrascrivendo qualsiasi `FormatCode` personalizzato; impostarlo a false costringe il grafico a utilizzare il formato specificato.

**Q: È possibile spostare l'asse Y secondario sul lato sinistro del grafico?**  
A: Sì, assegna `secondarySeriesGroup.AxisY.Position = AxisPosition.Left;` (o `Right` per il valore predefinito) per controllare su quale lato viene disegnato l'asse.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}