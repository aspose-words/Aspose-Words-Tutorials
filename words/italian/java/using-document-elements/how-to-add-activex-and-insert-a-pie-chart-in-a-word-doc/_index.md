---
category: general
date: 2026-08-17
description: Come aggiungere controlli ActiveX e inserire un grafico a torta in un
  documento Word usando Aspose.Words. Esplodere una fetta e salvare come DOCX in pochi
  passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add activex
- insert pie chart
- save as docx
- how to insert chart
- explode pie slice
language: it
lastmod: 2026-08-17
og_description: Come aggiungere controlli ActiveX, inserire un grafico a torta, far
  esplodere una fetta e salvare come DOCX con Aspose.Words – guida completa passo
  passo.
og_image_alt: Screenshot of a Word document showing an ActiveX button and a pie chart
  with an exploded slice
og_title: Come aggiungere ActiveX e inserire un grafico a torta in un documento Word
schemas:
- author: Aspose
  dateModified: '2026-08-17'
  description: How to add ActiveX controls and insert a pie chart in a Word doc using
    Aspose.Words. Explode a slice and save as DOCX in a few steps.
  headline: How to add ActiveX and insert a pie chart in a Word doc
  type: TechArticle
tags:
- Aspose.Words
- ActiveX
- Chart
- DOCX
title: Come aggiungere ActiveX e inserire un grafico a torta in un documento Word
url: /it/java/using-document-elements/how-to-add-activex-and-insert-a-pie-chart-in-a-word-doc/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere ActiveX e inserire un grafico a torta in un documento Word

Se hai bisogno di **how to add ActiveX** controlli e incorporare un grafico in un documento Word, questo tutorial ti mostra una soluzione completa e eseguibile. Utilizzando Aspose.Words puoi posizionare un ActiveX CommandButton, creare un grafico a torta, far esplodere una fetta per enfatizzare, e infine **save as DOCX** in poche righe di C#.

Nelle sezioni seguenti vedrai tutti gli import richiesti, un elenco completo di codice e spiegazioni sul perché ogni passaggio è importante. Alla fine sarai in grado di integrare controlli interattivi e dati visivi in qualsiasi file .docx generato programmaticamente.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.7+)
* Pacchetto Aspose.Words per .NET (disponibile via NuGet)
* Un ambiente di sviluppo come Visual Studio 2022 o VS Code
* Familiarità di base con C# e il modello a oggetti di Word

Non sono necessarie librerie di grafico di terze parti aggiuntive—Aspose.Words fornisce la creazione di grafici integrata.

## Come aggiungere controlli ActiveX con Aspose.Words

I controlli ActiveX ti consentono di incorporare elementi UI interattivi direttamente in un file Word. In questa guida aggiungiamo un **CommandButton** che potrà essere collegato successivamente a codice VBA.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

// Step 1: Create a new document and a DocumentBuilder
Document document = new Document();
DocumentBuilder builder = new DocumentBuilder(document);

// Step 2: Insert a group shape to hold the ActiveX control
GroupShape groupShape = builder.InsertGroupShape();

// Step 3: Insert a rectangle shape, hide it, and attach it to the group
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
groupShape.AppendChild(rectangleShape);
rectangleShape.SetHidden(true);

// Step 4: Insert a plain‑text StructuredDocumentTag (optional placeholder)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");

// Step 5: Insert the CommandButton ActiveX control
Forms2OleControl commandButton = builder.InsertForms2OleControl();
commandButton.SetActiveXControlType(Forms2OleControlType.CommandButton);
commandButton.SetCaption("Click Me");

// The CommandButton now appears in the document and can be used in VBA macros.
```

**Perché funziona:**  
`InsertForms2OleControl` crea un contenitore OLE che l'interfaccia di Word riconosce come controllo ActiveX. Impostare il tipo di controllo su `CommandButton` e assegnargli una didascalia lo fa comportare come un pulsante standard quando l'utente apre il file in Word.

## Inserire un grafico a torta e far esplodere una fetta

I grafici sono utili per visualizzare dati senza uscire dal documento. I passaggi seguenti dimostrano **how to insert chart** e specificamente un **pie chart** la cui prima fetta è esplosa.

```csharp
// Step 6: Insert a pie chart (400 × 300 points)
Chart pieChart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);

// Populate the chart with sample data
pieChart.Series.Clear();
ChartSeries series = pieChart.Series.Add("Sales", new[] { "Q1", "Q2", "Q3", "Q4" },
                                          new[] { 12000, 15000, 9000, 13000 });

// Step 7: Explode the first slice for emphasis
series.SetExplode(0, true);

// Optional: Customize colors or labels here if needed
```

**Perché far esplodere la fetta:**  
Chiamare `SetExplode(0, true)` indica ad Aspose.Words di spostare il primo punto dati, attirando l'occhio dello spettatore su quel segmento. Questa è una tecnica comune nelle presentazioni per evidenziare un valore chiave.

## Salva come DOCX

Dopo aver aggiunto il pulsante ActiveX e il grafico, persisti il documento su disco. Questo passaggio dimostra **save as DOCX** usando il metodo standard.

```csharp
// Step 8: Save the document in DOCX format
document.Save("Output.docx", SaveFormat.Docx);
```

Il file `Output.docx` ora contiene un pulsante interattivo, un grafico a torta con una fetta esplosa e può essere aperto in Microsoft Word senza plugin aggiuntivi.

## Esempio completo eseguibile

Mettendo tutto insieme, ecco un programma autonomo che puoi copiare in un'applicazione console e eseguire immediatamente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Charts;

class Program
{
    static void Main()
    {
        // Create document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert group shape and hidden rectangle (required for ActiveX positioning)
        GroupShape group = builder.InsertGroupShape();
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        group.AppendChild(rect);
        rect.SetHidden(true);

        // Optional placeholder tag
        builder.InsertStructuredDocumentTag(StructuredDocumentTagType.PlainText, "MyTag");

        // Insert CommandButton ActiveX control
        Forms2OleControl button = builder.InsertForms2OleControl();
        button.SetActiveXControlType(Forms2OleControlType.CommandButton);
        button.SetCaption("Click Me");

        // Insert pie chart and explode first slice
        Chart chart = (Chart)builder.InsertChart(ChartType.Pie, 400, 300);
        chart.Series.Clear();
        ChartSeries series = chart.Series.Add("Revenue", new[] { "Jan", "Feb", "Mar" },
                                               new[] { 5000, 7000, 3000 });
        series.SetExplode(0, true); // explode pie slice

        // Save the document
        doc.Save("Output.docx", SaveFormat.Docx);

        Console.WriteLine("Document created successfully: Output.docx");
    }
}
```

**Risultato atteso:**  
Aprendo `Output.docx` in Word viene mostrato un pulsante etichettato *Click Me* e un grafico a torta dove la prima fetta (January) è spostata rispetto alle altre. Il pulsante è pronto per la gestione degli eventi VBA, e il grafico può essere modificato usando gli strumenti di grafico integrati di Word.

## Domande comuni e casi particolari

* **Posso aggiungere altri tipi di ActiveX?**  
  Sì. Sostituisci `Forms2OleControlType.CommandButton` con qualsiasi valore dell'enumerazione `Forms2OleControlType` (ad es., `CheckBox`, `OptionButton`). Lo stesso schema di inserimento si applica.

* **E se ho bisogno di un tipo di grafico diverso?**  
  Usa `ChartType.Bar`, `ChartType.Line`, ecc., nella chiamata `InsertChart`. Il passaggio **how to insert chart** rimane identico; cambia solo il valore dell'enumerazione.

* **Come controllare la dimensione della fetta esplosa?**  
  Attualmente Aspose.Words supporta un flag binario di esplosione (true/false). Per un controllo più fine (ad es., distanza di offset) dovresti modificare l'OOXML sottostante dopo il salvataggio.

* **Il documento è compatibile con versioni più vecchie di Word?**  
  Il salvataggio come DOCX garantisce la compatibilità con Word 2007 e successive. Per Word 2003 potresti cambiare in `SaveFormat.Doc`, ma il supporto ActiveX è limitato in quel formato.

* **Devo fare riferimento a `System.Drawing`?**  
  No. Tutti gli oggetti di disegno sono forniti da Aspose.Words, quindi l'unico pacchetto NuGet richiesto è `Aspose.Words`.

## Conclusione

Ora sai **how to add ActiveX**, **insert a pie chart**, **explode a pie slice** e **save as DOCX** usando Aspose.Words per .NET. L'esempio completo copre ogni passaggio dalla creazione del documento alla persistenza finale, spiegando il motivo di ciascuna chiamata API.

Successivamente, potresti esplorare:

* Aggiungere macro VBA che rispondono al click del CommandButton (**how to insert chart** e automatizzano gli aggiornamenti dei dati)
* Personalizzare l'aspetto del grafico (colori, etichette dei dati) per corrispondere al branding aziendale
* Incorporare controlli ActiveX aggiuntivi come **ComboBox** o **ListBox** per moduli più ricchi

Sentiti libero di sperimentare con il codice, sostituire i dati di esempio e integrare la soluzione nei tuoi pipeline di generazione di documenti. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserire un grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-column-chart/)
- [Inserire un semplice grafico a colonne in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-simple-column-chart/)
- [Inserire un grafico a bolle in Word usando Aspose.Words per .NET](/words/english/net/working-with-charts/insert-bubble-chart/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}