---
title: Nascondi il bordo dell'area di tracciamento in un grafico a colonne con Aspose.Words per .NET
weight: 410
limit:
description: Impara a nascondere il bordo dell'area di tracciamento di un grafico mantenendo visibili le linee degli assi in un grafico a colonne Word usando Aspose.Words per .NET.
keywords: [aspose.words for .net, hide plot border, column chart, chart formatting, word document chart, plot area border removal]
url: /net/programming-with-charts/hide-plot-border/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Impara a nascondere il bordo dell'area di tracciamento di un grafico
    mantenendo visibili le linee degli assi in un grafico a colonne Word usando Aspose.Words
    per .NET.
  headline: Nascondi il bordo dell'area di tracciamento in un grafico a colonne con
    Aspose.Words per .NET
  type: TechArticle
- description: Impara a nascondere il bordo dell'area di tracciamento di un grafico
    mantenendo visibili le linee degli assi in un grafico a colonne Word usando Aspose.Words
    per .NET.
  name: Nascondi il bordo dell'area di tracciamento in un grafico a colonne con Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
    text: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
  - name: Inserisci un grafico a colonne 432×252 nel documento e ottieni il relativo
      oggetto Chart.
    text: Inserisci un grafico a colonne 432×252 nel documento e ottieni il relativo
      oggetto Chart.
  - name: Cancella eventuali serie esistenti, definisci tre etichette di categoria
      e aggiungi una serie con valori di esempio al grafico.
    text: Cancella eventuali serie esistenti, definisci tre etichette di categoria
      e aggiungi una serie con valori di esempio al grafico.
  - name: Imposta lo spessore del tratto dell'area di tracciamento a zero, rimuovendo
      il suo bordo ma lasciando visibili le linee degli assi.
    text: Imposta lo spessore del tratto dell'area di tracciamento a zero, rimuovendo
      il suo bordo ma lasciando visibili le linee degli assi.
  - name: Salva il documento modificato in un file .docx.
    text: Salva il documento modificato in un file .docx.
  type: HowTo
- questions:
  - answer: La proprietà `Stroke` appartiene al formato complessivo dell'oggetto `Chart`,
      che disegna il bordo rettangolare attorno all'area di tracciamento; le linee
      degli assi sono oggetti `Axis` separati e non sono influenzate dalle impostazioni
      `Stroke` del grafico.
    question: Perché impostare `columnChart.Format.Stroke.Weight = 0` rimuove il bordo
      dell'area di tracciamento ma lascia visibili le linee degli assi?
  - answer: No, la proprietà `Stroke` controlla l'intero bordo dell'area di tracciamento
      come un unico rettangolo, quindi i bordi parziali non possono essere nascosti
      tramite Aspose.Words; dovresti sovrapporre forme personalizzate o modificare
      manualmente il grafico.
    question: Posso nascondere solo un lato del bordo dell'area di tracciamento (ad
      esempio quello sinistro) mantenendo gli altri tre lati visibili?
  - answer: Sì, la proprietà `Stroke` è indipendente da `ChartType`, quindi impostare
      il suo `Weight` a 0 rimuove il bordo dell'area di tracciamento per Line, Pie
      o qualsiasi altro tipo di grafico supportato.
    question: Se cambio il tipo di grafico in Line o Pie, `columnChart.Format.Stroke.Weight
      = 0` nasconderà comunque il bordo dell'area di tracciamento?
  - answer: Non è necessario alcun aggiornamento aggiuntivo; cancellare le serie e
      aggiungerne una nuova aggiorna il grafico internamente, e `wordDoc.Save(...)`
      scrive lo stato attuale nel file .docx.
    question: Dopo aver chiamato `columnChart.Series.Clear()`, è necessario aggiornare
      il grafico prima di salvare il documento?
  type: FAQPage
images:
- /net/programming-with-charts/hide-plot-border/og-image.png
og_title: Nascondi il bordo dell'area di tracciamento in un grafico a colonne Word
og_description: Rimuovi il bordo dell'area di tracciamento mantenendo visibili le linee degli assi in un grafico a colonne Word usando Aspose.Words per .NET.
og_image_alt: Guida che mostra un documento Word con un grafico a colonne in cui il bordo dell'area di tracciamento è nascosto ma le linee degli assi rimangono visibili, usando Aspose.Words per .NET.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Nascondi il bordo dell'area di tracciamento in un grafico a colonne con Aspose.Words per .NET
In questo tutorial imparerai a generare un documento Word, inserire un grafico a colonne, riempirlo con dati di esempio e poi nascondere il bordo dell'area di tracciamento del grafico mantenendo visibili le linee degli assi. Il codice passo‑passo dimostra ogni operazione e termina con il salvataggio del documento, così potrai vedere subito il risultato.

---

{{< tutorial-widget sourcePath="words/net/programming-with-charts/hide-plot-border" >}}


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

**Q: Perché impostare `columnChart.Format.Stroke.Weight = 0` rimuove il bordo dell'area di tracciamento ma lascia visibili le linee degli assi?**  
A: La proprietà `Stroke` appartiene al formato complessivo dell'oggetto `Chart`, che disegna il bordo rettangolare attorno all'area di tracciamento; le linee degli assi sono oggetti `Axis` separati e non sono influenzate dalle impostazioni `Stroke` del grafico.

**Q: Posso nascondere solo un lato del bordo dell'area di tracciamento (ad esempio quello sinistro) mantenendo gli altri tre lati visibili?**  
A: No, la proprietà `Stroke` controlla l'intero bordo dell'area di tracciamento come un unico rettangolo, quindi i bordi parziali non possono essere nascosti tramite Aspose.Words; dovresti sovrapporre forme personalizzate o modificare manualmente il grafico.

**Q: Se cambio il tipo di grafico in Line o Pie, `columnChart.Format.Stroke.Weight = 0` nasconderà comunque il bordo dell'area di tracciamento?**  
A: Sì, la proprietà `Stroke` è indipendente da `ChartType`, quindi impostare il suo `Weight` a 0 rimuove il bordo dell'area di tracciamento per Line, Pie o qualsiasi altro tipo di grafico supportato.

**Q: Dopo aver chiamato `columnChart.Series.Clear()`, è necessario aggiornare il grafico prima di salvare il documento?**  
A: Non è necessario alcun aggiornamento aggiuntivo; cancellare le serie e aggiungerne una nuova aggiorna il grafico internamente, e `wordDoc.Save(...)` scrive lo stato attuale nel file .docx.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}