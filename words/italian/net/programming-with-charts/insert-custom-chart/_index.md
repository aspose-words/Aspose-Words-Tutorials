---
title: Inserisci un grafico a colonne personalizzato in un documento Word usando Aspose.Words per .NET
weight: 310
limit:
description: Crea un file Word, inserisci un grafico a colonne, sostituisci i suoi dati con un array personalizzato, aggiungi un titolo e salva—tutto con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, custom chart, column chart, Word document chart, populate chart from array, insert chart Aspose.Words]
url: /net/programming-with-charts/insert-custom-chart/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Crea un file Word, inserisci un grafico a colonne, sostituisci i suoi
    dati con un array personalizzato, aggiungi un titolo e salva—tutto con Aspose.Words
    per .NET.
  headline: Inserisci un grafico a colonne personalizzato in un documento Word usando
    Aspose.Words per .NET
  type: TechArticle
- description: Crea un file Word, inserisci un grafico a colonne, sostituisci i suoi
    dati con un array personalizzato, aggiungi un titolo e salva—tutto con Aspose.Words
    per .NET.
  name: Inserisci un grafico a colonne personalizzato in un documento Word usando
    Aspose.Words per .NET
  steps:
  - name: Crea un nuovo Document e un DocumentBuilder collegato ad esso.
    text: Crea un nuovo Document e un DocumentBuilder collegato ad esso.
  - name: Inserisci un grafico a colonne di dimensioni 432x252 punti nel documento
      e ottieni il suo oggetto Chart.
    text: Inserisci un grafico a colonne di dimensioni 432x252 punti nel documento
      e ottieni il suo oggetto Chart.
  - name: Rimuovi le serie di esempio generate automaticamente dal grafico.
    text: Rimuovi le serie di esempio generate automaticamente dal grafico.
  - name: Definisci le etichette di categoria dell'asse X e le voci della legenda
      per ogni serie.
    text: Definisci le etichette di categoria dell'asse X e le voci della legenda
      per ogni serie.
  - name: Crea un array bidimensionale in cui ogni riga contiene i valori per una
      serie.
    text: Crea un array bidimensionale in cui ogni riga contiene i valori per una
      serie.
  - name: Itera su ogni serie, estrai i valori della riga dalla matrice e aggiungi
      la serie al grafico con la corrispondente voce della legenda e le etichette
      dell'asse X.
    text: Itera su ogni serie, estrai i valori della riga dalla matrice e aggiungi
      la serie al grafico con la corrispondente voce della legenda e le etichette
      dell'asse X.
  - name: Imposta il testo del titolo del grafico su 'Half‑Yearly Revenue' e rendilo
      visibile.
    text: Imposta il testo del titolo del grafico su 'Half‑Yearly Revenue' e rendilo
      visibile.
  - name: Salva il documento contenente il grafico personalizzato in un file .docx.
    text: Salva il documento contenente il grafico personalizzato in un file .docx.
  type: HowTo
- questions:
  - answer: '`Chart.Series.Add` si aspetta che la lunghezza dell''array di valori
      sia uguale al numero di etichette dell''asse X, e devi aggiungere esattamente
      una serie per voce della legenda; una discrepanza genererà un `ArgumentException`
      a runtime.'
    question: Cosa succede se le righe o le colonne in `dataMatrix` non corrispondono
      alle lunghezze di `legendEntries` o `xLabels`?
  - answer: Sì—sostituisci `ChartType.Column` in `docBuilder.InsertChart` con qualsiasi
      altro `ChartType` (ad esempio, `ChartType.Line`) e le successive chiamate a
      `Series.Add` popoleranno il nuovo grafico allo stesso modo.
    question: Posso usare un tipo di grafico diverso, come un grafico a linee, con
      la stessa logica di popolamento dei dati?
  - answer: Regola le proprietà `Width` e `Height` dell'oggetto `Shape` restituito
      da `InsertChart` (ad es., `chartContainer.Width = 500; chartContainer.Height
      = 300;`).
    question: Come posso modificare le dimensioni del grafico dopo che è stato inserito?
  - answer: Imposta `chartObj.Series[i].HasDataLabel = true;` per ogni serie dopo
      averla aggiunta, oppure itera su `chartObj.Series` e abilita `HasDataLabel`
      per visualizzare i valori sul grafico.
    question: Esiste un modo rapido per mostrare le etichette dei dati su ogni colonna
      del grafico?
  type: FAQPage
images:
- /net/programming-with-charts/insert-custom-chart/og-image.png
og_title: Aggiungi un grafico a colonne personalizzato a un documento Word
og_description: Sostituisci i dati predefiniti di un grafico con il tuo array e imposta un titolo in pochi secondi.
og_image_alt: Screenshot che mostra un documento Word con un grafico a colonne personalizzato creato usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci un grafico a colonne personalizzato in un documento Word usando Aspose.Words per .NET
Questo tutorial ti guida nella creazione di un documento Word, nell'inserimento di un grafico a colonne, nella cancellazione dei dati predefiniti e nella popolazione del grafico con valori personalizzati da un array bidimensionale—mappando ogni riga a una serie e ogni colonna a una categoria. Vedrai anche come aggiungere un titolo al grafico prima di salvare il file. Segui i passaggi per ottenere un grafico completamente personalizzato direttamente nel tuo file Word.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/insert-custom-chart" >}}


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

**Q: Cosa succede se le righe o le colonne in `dataMatrix` non corrispondono alle lunghezze di `legendEntries` o `xLabels`?**  
A: `Chart.Series.Add` si aspetta che la lunghezza dell'array di valori sia uguale al numero di etichette dell'asse X, e devi aggiungere esattamente una serie per voce della legenda; una discrepanza genererà un `ArgumentException` a runtime.

**Q: Posso usare un tipo di grafico diverso, come un grafico a linee, con la stessa logica di popolamento dei dati?**  
A: Sì—sostituisci `ChartType.Column` in `docBuilder.InsertChart` con qualsiasi altro `ChartType` (ad esempio, `ChartType.Line`) e le successive chiamate a `Series.Add` popoleranno il nuovo grafico allo stesso modo.

**Q: Come posso modificare le dimensioni del grafico dopo che è stato inserito?**  
A: Regola le proprietà `Width` e `Height` dell'oggetto `Shape` restituito da `InsertChart` (ad es., `chartContainer.Width = 500; chartContainer.Height = 300;`).

**Q: Esiste un modo rapido per mostrare le etichette dei dati su ogni colonna del grafico?**  
A: Imposta `chartObj.Series[i].HasDataLabel = true;` per ogni serie dopo averla aggiunta, oppure itera su `chartObj.Series` e abilita `HasDataLabel` per visualizzare i valori sul grafico.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}