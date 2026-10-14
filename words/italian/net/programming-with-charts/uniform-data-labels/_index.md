---
title: Imposta etichette dati uniformi in un grafico a colonne usando Aspose.Words per .NET
weight: 110
limit:
description: Impara a creare un grafico a colonne Word e ad applicare una dimensione e un colore del carattere uniformi alle etichette dei dati per tutte le serie con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, uniform data labels, chart data label formatting, column chart Word SDK, default data label style, Word document chart customization]
url: /net/programming-with-charts/uniform-data-labels/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara a creare un grafico a colonne Word e ad applicare una dimensione
    e un colore del carattere uniformi alle etichette dei dati per tutte le serie
    con Aspose.Words per .NET.
  headline: Imposta etichette dati uniformi in un grafico a colonne usando Aspose.Words
    per .NET
  type: TechArticle
- description: Impara a creare un grafico a colonne Word e ad applicare una dimensione
    e un colore del carattere uniformi alle etichette dei dati per tutte le serie
    con Aspose.Words per .NET.
  name: Imposta etichette dati uniformi in un grafico a colonne usando Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
    text: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
  - name: Inserisci un grafico a colonne 500×300 nel documento e ottieni il suo oggetto
      Chart.
    text: Inserisci un grafico a colonne 500×300 nel documento e ottieni il suo oggetto
      Chart.
  - name: Rimuovi la serie di esempio predefinita che Aspose.Words aggiunge a un nuovo
      grafico.
    text: Rimuovi la serie di esempio predefinita che Aspose.Words aggiunge a un nuovo
      grafico.
  - name: Definisci le etichette di categoria e aggiungi due serie di dati (Item Alpha
      e Item Beta) con i relativi valori al grafico.
    text: Definisci le etichette di categoria e aggiungi due serie di dati (Item Alpha
      e Item Beta) con i relativi valori al grafico.
  - name: Imposta la dimensione e il colore di base del carattere che verranno applicati
      a tutte le etichette dei dati.
    text: Imposta la dimensione e il colore di base del carattere che verranno applicati
      a tutte le etichette dei dati.
  - name: Abilita le etichette dei dati per ogni serie, mostra il valore numerico
      e applica la dimensione e il colore del carattere predefiniti.
    text: Abilita le etichette dei dati per ogni serie, mostra il valore numerico
      e applica la dimensione e il colore del carattere predefiniti.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: '`InsertChart` crea un grafico con una serie di esempio predefinita; cancellandola
      si rimuove quel segnaposto in modo che il grafico mostri solo le serie che aggiungi
      (`Item Alpha` e `Item Beta`).'
    question: Perché devo chiamare `chart.Series.Clear()` prima di aggiungere le mie
      serie?
  - answer: Sostituisci `Color.White` con qualsiasi valore `System.Drawing.Color`,
      ad esempio `Color.Black` o `Color.FromArgb(255, 30, 144, 255)`; il nuovo colore
      viene applicato tramite `series.DataLabels.Font.Color` all'interno del ciclo.
    question: Come posso cambiare il colore dell'etichetta dei dati in qualcosa di
      diverso dal bianco?
  - answer: Le etichette dei dati verranno nascoste, quindi le impostazioni del carattere
      che hai applicato diventano invisibili; devi mantenere `HasDataLabels` impostato
      su `true` affinché le etichette (e il loro stile) vengano visualizzate.
    question: Cosa succede se imposto `series.HasDataLabels = false` dopo aver configurato
      la dimensione e il colore del carattere?
  - answer: Sì—ogni `ChartSeries` ha il proprio oggetto `DataLabels`, quindi qualsiasi
      serie aggiunta dopo il ciclo iniziale deve avere anche `HasDataLabels`, `ShowValue`
      e le proprietà del carattere impostate, sia iterando nuovamente sia estraendo
      lo stile in un metodo di supporto.
    question: Devo iterare nuovamente le serie se aggiungo un'altra serie più tardi
      nel codice?
  type: FAQPage
images:
- /net/programming-with-charts/uniform-data-labels/og-image.png
og_title: Applica etichette dati uniformi a un grafico Word
og_description: Assegna rapidamente a ogni etichetta del grafico la stessa dimensione e colore del carattere con Aspose.Words per .NET.
og_image_alt: Guida che mostra un documento Word con un grafico a colonne in cui tutte le etichette dei dati condividono la stessa dimensione e colore del carattere, creato usando Aspose.Words per .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Imposta etichette dati uniformi in un grafico a colonne usando Aspose.Words per .NET
Questo tutorial mostra come generare un documento Word, inserire un grafico a colonne e aggiungere serie di dati personalizzate con Aspose.Words per .NET. Successivamente dimostra come definire la dimensione e il colore predefiniti del carattere delle etichette dei dati affinché ogni serie del grafico visualizzi etichette identiche. Applicando uno stile unico si garantisce un aspetto visivo coerente in tutto il grafico.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/uniform-data-labels" >}}


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

**Q: Perché devo chiamare `chart.Series.Clear()` prima di aggiungere le mie serie?**  
A: `InsertChart` crea un grafico con una serie di esempio predefinita; cancellandola si rimuove quel segnaposto in modo che il grafico mostri solo le serie che aggiungi (`Item Alpha` e `Item Beta`).

**Q: Come posso cambiare il colore dell'etichetta dei dati in qualcosa di diverso dal bianco?**  
A: Sostituisci `Color.White` con qualsiasi valore `System.Drawing.Color`, ad esempio `Color.Black` o `Color.FromArgb(255, 30, 144, 255)`; il nuovo colore viene applicato tramite `series.DataLabels.Font.Color` all'interno del ciclo.

**Q: Cosa succede se imposto `series.HasDataLabels = false` dopo aver configurato la dimensione e il colore del carattere?**  
A: Le etichette dei dati verranno nascoste, quindi le impostazioni del carattere che hai applicato diventano invisibili; devi mantenere `HasDataLabels` impostato su `true` affinché le etichette (e il loro stile) vengano visualizzate.

**Q: Devo iterare nuovamente le serie se aggiungo un'altra serie più tardi nel codice?**  
A: Sì—ogni `ChartSeries` ha il proprio oggetto `DataLabels`, quindi qualsiasi serie aggiunta dopo il ciclo iniziale deve avere anche `HasDataLabels`, `ShowValue` e le proprietà del carattere impostate, sia iterando nuovamente sia estraendo lo stile in un metodo di supporto.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}