---
title: Formatta l'asse X secondario e imposta le unità di visualizzazione su migliaia nei grafici a linee di Word utilizzando Aspose.Words per .NET
weight: 710
limit:
description: Crea un grafico a linee Word, aggiungi un asse X secondario, imposta la sua unità di visualizzazione su migliaia e applica un formato numerico personalizzato con Aspose.Words per .NET.
keywords: [secondary axis formatting, Aspose.Words for .NET, line chart axis units, display units thousands, custom numeric format axis, Word chart secondary X axis]
url: /net/programming-with-charts/format-secondary-axis/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Crea un grafico a linee Word, aggiungi un asse X secondario, imposta
    la sua unità di visualizzazione su migliaia e applica un formato numerico personalizzato
    con Aspose.Words per .NET.
  headline: Formatta l'asse X secondario e imposta le unità di visualizzazione su
    migliaia nei grafici a linee di Word utilizzando Aspose.Words per .NET
  type: TechArticle
- description: Crea un grafico a linee Word, aggiungi un asse X secondario, imposta
    la sua unità di visualizzazione su migliaia e applica un formato numerico personalizzato
    con Aspose.Words per .NET.
  name: Formatta l'asse X secondario e imposta le unità di visualizzazione su migliaia
    nei grafici a linee di Word utilizzando Aspose.Words per .NET
  steps:
  - name: Crea un nuovo Document e un DocumentBuilder per iniziare a costruire il
      file Word.
    text: Crea un nuovo Document e un DocumentBuilder per iniziare a costruire il
      file Word.
  - name: Inserisci un grafico a linee di dimensioni 500×300 nel documento e ottieni
      l'oggetto Chart.
    text: Inserisci un grafico a linee di dimensioni 500×300 nel documento e ottieni
      l'oggetto Chart.
  - name: Rimuovi la serie demo predefinita che Aspose.Words aggiunge automaticamente.
    text: Rimuovi la serie demo predefinita che Aspose.Words aggiunge automaticamente.
  - name: Definisci un array di etichette di categoria che verrà utilizzato per l'asse
      X.
    text: Definisci un array di etichette di categoria che verrà utilizzato per l'asse
      X.
  - name: Aggiungi la serie di dati primaria denominata "Main Data" utilizzando le
      etichette e i valori.
    text: Aggiungi la serie di dati primaria denominata "Main Data" utilizzando le
      etichette e i valori.
  - name: Crea un gruppo di serie secondario di tipo Line e assegnalo al gruppo di
      assi secondario.
    text: Crea un gruppo di serie secondario di tipo Line e assegnalo al gruppo di
      assi secondario.
  - name: Imposta l'unità di visualizzazione dell'asse X secondario su migliaia in
      modo che i valori siano mostrati in K.
    text: Imposta l'unità di visualizzazione dell'asse X secondario su migliaia in
      modo che i valori siano mostrati in K.
  - name: Applica un formato numerico personalizzato "#,##0.0" alle etichette dei
      tick dell'asse X secondario.
    text: Applica un formato numerico personalizzato "#,##0.0" alle etichette dei
      tick dell'asse X secondario.
  - name: Facoltativamente aggiungi una serie di dati ausiliaria al gruppo secondario.
    text: Facoltativamente aggiungi una serie di dati ausiliaria al gruppo secondario.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: No – le impostazioni `AxisX` appartengono al `ChartSeriesGroup`, quindi
      puoi impostare `secondaryGroup.AxisX.DisplayUnit.Unit` e `secondaryGroup.AxisX.NumberFormat.FormatCode`
      prima o dopo aver aggiunto le serie; la configurazione verrà applicata all'asse
      del gruppo in entrambi i casi.
    question: Devo aggiungere la serie secondaria prima di impostare l'unità di visualizzazione
      e il formato numerico sull'asse X secondario?
  - answer: Sì – assegna qualsiasi valore `AxisBuiltInUnit`, ad esempio `secondaryGroup.AxisX.DisplayUnit.Unit
      = AxisBuiltInUnit.Millions;` per mostrare i valori dell'asse in milioni invece
      che in migliaia.
    question: Posso usare un'unità predefinita diversa, ad esempio milioni, per l'asse
      X secondario?
  - answer: No – il codice di formato viene applicato solo all'asse che modifichi
      (`secondaryGroup.AxisX.NumberFormat.FormatCode`), quindi l'asse X primario mantiene
      la formattazione predefinita.
    question: Il formato personalizzato `"#,##0.0"` influenzerà le etichette dell'asse
      X primario?
  - answer: Il grafico conterrà la serie demo predefinita oltre a quelle che aggiungi,
      il che può portare a linee extra e categorie non corrispondenti; cancellare
      la collezione garantisce che compaiano solo i dati desiderati.
    question: Cosa succede se dimentico di cancellare la serie demo con `lineChart.Series.Clear();`?
  type: FAQPage
images:
- /net/programming-with-charts/format-secondary-axis/og-image.png
og_title: Formatta l'asse X secondario e imposta le unità su migliaia
og_description: Aggiungi un asse X secondario a un grafico a linee Word e formatta le sue etichette in migliaia con un modello personalizzato.
og_image_alt: Guida che mostra come aggiungere un asse X secondario a un grafico a linee Word e formattare le sue etichette per visualizzare le unità in migliaia usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Formatta l'asse X secondario e imposta le unità di visualizzazione su migliaia nei grafici a linee di Word utilizzando Aspose.Words per .NET
Questo tutorial ti guida nella creazione di un documento Word che contiene un grafico a linee, nell'aggiunta di un asse X secondario e nella configurazione di tale asse per mostrare i valori in migliaia. Imparerai anche come applicare un formato numerico personalizzato alle etichette dell'asse secondario, offrendoti un controllo preciso su come i dati vengono presentati. Segui i passaggi per migliorare la leggibilità dei grafici multi‑asse nei tuoi report Word.

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

**Q: Devo aggiungere la serie secondaria prima di impostare l'unità di visualizzazione e il formato numerico sull'asse X secondario?**  
A: No – le impostazioni `AxisX` appartengono al `ChartSeriesGroup`, quindi puoi impostare `secondaryGroup.AxisX.DisplayUnit.Unit` e `secondaryGroup.AxisX.NumberFormat.FormatCode` prima o dopo aver aggiunto le serie; la configurazione verrà applicata all'asse del gruppo in entrambi i casi.

**Q: Posso usare un'unità predefinita diversa, ad esempio milioni, per l'asse X secondario?**  
A: Sì – assegna qualsiasi valore `AxisBuiltInUnit`, ad esempio `secondaryGroup.AxisX.DisplayUnit.Unit = AxisBuiltInUnit.Millions;` per mostrare i valori dell'asse in milioni invece che in migliaia.

**Q: Il formato personalizzato `"#,##0.0"` influenzerà le etichette dell'asse X primario?**  
A: No – il codice di formato viene applicato solo all'asse che modifichi (`secondaryGroup.AxisX.NumberFormat.FormatCode`), quindi l'asse X primario mantiene la formattazione predefinita.

**Q: Cosa succede se dimentico di cancellare la serie demo con `lineChart.Series.Clear();`?**  
A: Il grafico conterrà la serie demo predefinita oltre a quelle che aggiungi, il che può portare a linee extra e categorie non corrispondenti; cancellare la collezione garantisce che compaiano solo i dati desiderati.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}