---
title: Personalizza le linee della griglia dell'asse X in un grafico a colonne utilizzando Aspose.Words per .NET
weight: 610
limit:
description: Impara ad aggiungere e personalizzare il colore delle linee della griglia principale dell'asse X in un grafico a colonne Word con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, column chart, customize x axis gridlines, word chart gridlines, primary x axis gridlines, chart formatting .NET]
url: /net/programming-with-charts/customize-x-axis-gridlines/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara ad aggiungere e personalizzare il colore delle linee della griglia
    principale dell'asse X in un grafico a colonne Word con Aspose.Words per .NET.
  headline: Personalizza le linee della griglia dell'asse X in un grafico a colonne
    utilizzando Aspose.Words per .NET
  type: TechArticle
- description: Impara ad aggiungere e personalizzare il colore delle linee della griglia
    principale dell'asse X in un grafico a colonne Word con Aspose.Words per .NET.
  name: Personalizza le linee della griglia dell'asse X in un grafico a colonne utilizzando
    Aspose.Words per .NET
  steps:
  - name: Crea un nuovo documento Word e un DocumentBuilder per modificarlo.
    text: Crea un nuovo documento Word e un DocumentBuilder per modificarlo.
  - name: Inserisci un grafico a colonne 432×252 nel documento e ottieni il suo oggetto
      Chart.
    text: Inserisci un grafico a colonne 432×252 nel documento e ottieni il suo oggetto
      Chart.
  - name: Rimuovi la serie predefinita e aggiungi una serie personalizzata con tre
      gruppi e valori.
    text: Rimuovi la serie predefinita e aggiungi una serie personalizzata con tre
      gruppi e valori.
  - name: Ottieni un riferimento all'asse orizzontale (X) primario del grafico.
    text: Ottieni un riferimento all'asse orizzontale (X) primario del grafico.
  - name: Abilita la visualizzazione delle linee della griglia principale sull'asse
      X primario.
    text: Abilita la visualizzazione delle linee della griglia principale sull'asse
      X primario.
  - name: Imposta il colore delle linee della griglia su blu e il loro spessore a
      2 punti.
    text: Imposta il colore delle linee della griglia su blu e il loro spessore a
      2 punti.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: 'Imposta la stessa proprietà dell''asse su false: `horizontalAxis.HasMajorGridlines
      = false;` attiva/disattiva la visibilità delle linee della griglia principale
      dell''asse X.'
    question: Come nascondere nuovamente le linee della griglia principale dopo averle
      abilitate?
  - answer: No, le impostazioni `Format.Stroke` si applicano solo all'asse modificato;
      per stilizzare le linee della griglia dell'asse Y devi regolare separatamente
      `chart.AxisY.Format.Stroke`.
    question: La modifica di `horizontalAxis.Format.Stroke.Color` influenzerà anche
      le linee della griglia dell'asse Y?
  - answer: Usa `horizontalAxis.Format.Stroke.Weight` e assegna un valore double (ad
      es., `0.5`) per rendere le linee della griglia più sottili.
    question: Quale proprietà controlla lo spessore delle linee della griglia principale
      dell'asse X?
  - answer: Sì, imposta `horizontalAxis.Format.Stroke.DashStyle` su un valore enum
      `DashStyle` come `DashStyle.Dash` o `DashStyle.Dot`.
    question: Posso cambiare il modello di tratteggio delle linee della griglia principale
      dell'asse X?
  type: FAQPage
images:
- /net/programming-with-charts/customize-x-axis-gridlines/og-image.png
og_title: Stilizza le linee della griglia dell'asse X in un grafico a colonne Word
og_description: Attiva e personalizza il colore delle linee della griglia dell'asse X primario di un grafico Word con Aspose.Words per .NET.
og_image_alt: Guida che mostra un documento Word con un grafico a colonne in cui le linee della griglia principale dell'asse X primario sono evidenziate con un colore personalizzato usando Aspose.Words per .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Personalizza le linee della griglia dell'asse X in un grafico a colonne utilizzando Aspose.Words per .NET
In questo tutorial imparerai come creare un documento Word, inserire un grafico a colonne, sostituire i dati predefiniti e quindi abilitare le linee della griglia principale sull'asse X primario. Vedrai anche come cambiare il colore delle linee della griglia per adattarlo al tuo design. Segui il codice passo‑passo per ottenere un controllo preciso sulla visibilità e lo stile delle linee della griglia dell'asse X.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/customize-x-axis-gridlines" >}}


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

**Q: Come nascondere nuovamente le linee della griglia principale dopo averle abilitate?**  
A: Imposta la stessa proprietà dell'asse su false: `horizontalAxis.HasMajorGridlines = false;` attiva/disattiva la visibilità delle linee della griglia principale dell'asse X.

**Q: La modifica di `horizontalAxis.Format.Stroke.Color` influenzerà anche le linee della griglia dell'asse Y?**  
A: No, le impostazioni `Format.Stroke` si applicano solo all'asse modificato; per stilizzare le linee della griglia dell'asse Y devi regolare separatamente `chart.AxisY.Format.Stroke`.

**Q: Quale proprietà controlla lo spessore delle linee della griglia principale dell'asse X?**  
A: Usa `horizontalAxis.Format.Stroke.Weight` e assegna un valore double (ad es., `0.5`) per rendere le linee della griglia più sottili.

**Q: Posso cambiare il modello di tratteggio delle linee della griglia principale dell'asse X?**  
A: Sì, imposta `horizontalAxis.Format.Stroke.DashStyle` su un valore enum `DashStyle` come `DashStyle.Dash` o `DashStyle.Dot`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}