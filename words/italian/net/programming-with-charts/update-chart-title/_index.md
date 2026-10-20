---
title: Aggiorna il titolo del grafico e attiva/disattiva la visibilità della legenda in Word usando Aspose.Words per .NET
weight: 810
limit:
description: Impara a modificare il titolo di un grafico e a controllare la visibilità della legenda in un documento Word con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, update chart title, toggle legend visibility, word chart manipulation, c# chart title, aspose words chart legend]
url: /net/programming-with-charts/update-chart-title/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara a modificare il titolo di un grafico e a controllare la visibilità
    della legenda in un documento Word con Aspose.Words per .NET.
  headline: Aggiorna il titolo del grafico e attiva/disattiva la visibilità della
    legenda in Word usando Aspose.Words per .NET
  type: TechArticle
- description: Impara a modificare il titolo di un grafico e a controllare la visibilità
    della legenda in un documento Word con Aspose.Words per .NET.
  name: Aggiorna il titolo del grafico e attiva/disattiva la visibilità della legenda
    in Word usando Aspose.Words per .NET
  steps:
  - name: Definisci il titolo del grafico fornito dall'utente e se la legenda deve
      essere mostrata.
    text: Definisci il titolo del grafico fornito dall'utente e se la legenda deve
      essere mostrata.
  - name: Crea un nuovo documento Word e un DocumentBuilder per aggiungere contenuti.
    text: Crea un nuovo documento Word e un DocumentBuilder per aggiungere contenuti.
  - name: Inserisci un grafico a colonne di 432 × 252 pt nel documento e verifica
      che la forma contenga effettivamente un grafico.
    text: Inserisci un grafico a colonne di 432 × 252 pt nel documento e verifica
      che la forma contenga effettivamente un grafico.
  - name: Recupera l'oggetto chart, imposta il testo del titolo al valore fornito
      dall'utente e assicurati che il titolo sia visualizzato.
    text: Recupera l'oggetto chart, imposta il testo del titolo al valore fornito
      dall'utente e assicurati che il titolo sia visualizzato.
  - name: 'Configura la legenda: mostrala a destra se richiesto, altrimenti nascondila,
      e consenti che si sovrapponga all''area del grafico.'
    text: 'Configura la legenda: mostrala a destra se richiesto, altrimenti nascondila,
      e consenti che si sovrapponga all''area del grafico.'
  - name: Salva il documento modificato su disco come CustomChart.docx.
    text: Salva il documento modificato su disco come CustomChart.docx.
  type: HowTo
- questions:
  - answer: Quando `displayLegend` è `true`, il codice imposta `chartLegend.Position`
      su `LegendPosition.Right`, rendendo la legenda visibile sul lato destro dell'area
      del grafico; la proprietà `Overlay` rimane `true`, quindi la legenda può sovrapporsi
      al grafico per risparmiare spazio.
    question: Cosa cambia l'impostazione di `displayLegend` su `true` nel grafico
      generato?
  - answer: Imposta `chartTitle.Show = false` (o semplicemente ometti di impostare
      `Show` su `true`) dopo aver assegnato `chartTitle.Text`; il titolo non verrà
      renderizzato nel documento Word.
    question: Come posso nascondere il titolo del grafico se l'utente non ne fornisce
      uno?
  - answer: Sì—`InsertChart` restituisce una `Shape` che dovrebbe contenere un grafico,
      ma verificare `HasChart` garantisce che la forma contenga effettivamente un
      oggetto `Chart`; altrimenti il codice genera un `InvalidOperationException`.
    question: È necessario verificare `chartContainer.HasChart` dopo aver chiamato
      `InsertChart`?
  - answer: Assolutamente; assegna qualsiasi valore dell'enumerazione `LegendPosition`
      (ad esempio `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`)
      a `chartLegend.Position` per riposizionare la legenda secondo necessità.
    question: Posso posizionare la legenda in un punto diverso dal lato destro?
  type: FAQPage
images:
- /net/programming-with-charts/update-chart-title/og-image.png
og_title: Modifica titolo del grafico e legenda in Word
og_description: Impara a impostare un titolo personalizzato per il grafico e a controllare la visualizzazione della legenda in un documento Word con Aspose.Words per .NET.
og_image_alt: Guida che mostra il codice per aggiornare il titolo di un grafico e attivare/disattivare la legenda in un documento Word usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiorna il titolo del grafico e attiva/disattiva la visibilità della legenda in Word usando Aspose.Words per .NET
Questo tutorial mostra come modificare programmaticamente un grafico all'interno di un documento Word con Aspose.Words per .NET. Imparerai a inserire un grafico a colonne, a sostituire il suo titolo con il testo fornito dall'utente e a controllare la visibilità e la sovrapposizione della legenda in base alle preferenze dell'utente. Questi passaggi ti consentono di personalizzare la presentazione del grafico in modo dinamico senza modifiche manuali.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/update-chart-title" >}}


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

**Q: Cosa cambia l'impostazione di `displayLegend` su `true` nel grafico generato?**  
A: Quando `displayLegend` è `true`, il codice imposta `chartLegend.Position` su `LegendPosition.Right`, rendendo la legenda visibile sul lato destro dell'area del grafico; la proprietà `Overlay` rimane `true`, quindi la legenda può sovrapporsi al grafico per risparmiare spazio.

**Q: Come posso nascondere il titolo del grafico se l'utente non ne fornisce uno?**  
A: Imposta `chartTitle.Show = false` (o semplicemente ometti di impostare `Show` su `true`) dopo aver assegnato `chartTitle.Text`; il titolo non verrà renderizzato nel documento Word.

**Q: È necessario verificare `chartContainer.HasChart` dopo aver chiamato `InsertChart`?**  
A: Sì—`InsertChart` restituisce una `Shape` che dovrebbe contenere un grafico, ma verificare `HasChart` garantisce che la forma contenga effettivamente un oggetto `Chart`; altrimenti il codice genera un `InvalidOperationException`.

**Q: Posso posizionare la legenda in un punto diverso dal lato destro?**  
A: Assolutamente; assegna qualsiasi valore dell'enumerazione `LegendPosition` (ad esempio `LegendPosition.Top`, `LegendPosition.Bottom`, `LegendPosition.Left`) a `chartLegend.Position` per riposizionare la legenda secondo necessità.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}