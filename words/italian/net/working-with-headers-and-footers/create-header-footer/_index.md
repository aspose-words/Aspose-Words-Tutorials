---
"description": "Scopri come aggiungere e personalizzare intestazioni e piè di pagina nei documenti Word utilizzando Aspose.Words per .NET. Questa guida passo passo garantisce una formattazione professionale dei documenti."
"linktitle": "Crea intestazione piè di pagina"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Crea intestazione piè di pagina"
"url": "/it/net/working-with-headers-and-footers/create-header-footer/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Crea intestazione piè di pagina

## Introduzione

Aggiungere intestazioni e piè di pagina ai documenti può migliorarne la professionalità e la leggibilità. Con Aspose.Words per .NET, puoi creare e personalizzare facilmente intestazioni e piè di pagina per i tuoi documenti Word. In questo tutorial, ti guideremo passo dopo passo attraverso il processo, assicurandoti di poter implementare queste funzionalità senza problemi.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

- Aspose.Words per .NET: Scarica e installa da [collegamento per il download](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: come Visual Studio, per scrivere ed eseguire il codice.
- Conoscenza di base di C#: comprensione di C# e del framework .NET.
- Documento di esempio: un documento di esempio a cui applicare intestazioni e piè di pagina oppure per crearne uno nuovo come mostrato nel tutorial.

## Importa spazi dei nomi

Per prima cosa, è necessario importare gli spazi dei nomi necessari per accedere alle classi e ai metodi Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System;
```

## Passaggio 1: definire la directory dei documenti

Definisci la directory in cui verrà salvato il documento. Questo aiuta a gestire il percorso in modo efficace.

```csharp
// Il percorso verso la directory dei documenti
string dataDir = "YOUR_DIRECTORY_OF_DOCUMENTS";
```

## Passaggio 2: creare un nuovo documento

Crea un nuovo documento e un `DocumentBuilder` per facilitare l'aggiunta di contenuti.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 3: configurare l'impostazione della pagina

Configura le impostazioni della pagina, inclusa l'eventuale presenza di intestazione/piè di pagina diversi nella prima pagina.

```csharp
Section currentSection = builder.CurrentSection;
PageSetup pageSetup = currentSection.PageSetup;

pageSetup.DifferentFirstPageHeaderFooter = true;
pageSetup.HeaderDistance = 20;
```

## Passaggio 4: aggiungere un'intestazione alla prima pagina

Passare alla sezione dell'intestazione della prima pagina e configurare il testo dell'intestazione.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderFirst);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;

builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.Font.Size = 14;

builder.Write("Aspose.Words Header/Footer Creation Primer - Title Page.");
```

## Passaggio 5: aggiungere un'intestazione primaria

Passa alla sezione dell'intestazione principale e inserisci un'immagine e un testo.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary);

// Inserisci un'immagine nell'intestazione
builder.InsertImage(dataDir + "Graphics Interchange Format.gif", 
    RelativeHorizontalPosition.Page, 10, RelativeVerticalPosition.Page, 10, 50, 50, WrapType.Through);

builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Aspose.Words Header/Footer Creation Primer.");
```

## Passaggio 6: aggiungere un piè di pagina principale

Passa alla sezione principale del piè di pagina e crea una tabella per formattare il contenuto del piè di pagina.

```csharp
builder.MoveToHeaderFooter(HeaderFooterType.FooterPrimary);

builder.StartTable();
builder.CellFormat.ClearFormatting();
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);

// Aggiungere la numerazione delle pagine
builder.Write("Page ");
builder.InsertField("PAGE", "");
builder.Write(" of ");
builder.InsertField("NUMPAGES", "");

builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Left;
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

builder.Write("(C) 2001 Aspose Pty Ltd. All rights reserved.");
builder.CurrentParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Right;

builder.EndRow();
builder.EndTable();
```

## Passaggio 7: aggiungere contenuto e interruzioni di pagina

Spostati alla fine del documento, aggiungi un'interruzione di pagina e crea una nuova sezione con impostazioni di pagina diverse.

```csharp
builder.MoveToDocumentEnd();
builder.InsertBreak(BreakType.PageBreak);
builder.InsertBreak(BreakType.SectionBreakNewPage);

currentSection = builder.CurrentSection;
pageSetup = currentSection.PageSetup;
pageSetup.Orientation = Orientation.Landscape;
pageSetup.DifferentFirstPageHeaderFooter = false;

currentSection.HeadersFooters.LinkToPrevious(false);
CopyHeadersFootersFromPreviousSection(currentSection);

HeaderFooter primaryFooter = currentSection.HeadersFooters[HeaderFooterType.FooterPrimary];
Row row = primaryFooter.Tables[0].FirstRow;
row.FirstCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 / 3);
row.LastCell.CellFormat.PreferredWidth = PreferredWidth.FromPercent(100 * 2 / 3);

doc.Save(dataDir + "WorkingWithHeadersAndFooters.CreateHeaderFooter.docx");
```

## Passaggio 8: copiare intestazioni e piè di pagina dalla sezione precedente

Se si desidera riutilizzare intestazioni e piè di pagina di una sezione precedente, è sufficiente copiarli e apportare le modifiche necessarie.

```csharp
private static void CopyHeadersFootersFromPreviousSection(Section section)
{
    Section previousSection = (Section)section.PreviousSibling;
    if (previousSection == null) return;

    section.HeadersFooters.Clear();

    foreach (HeaderFooter headerFooter in previousSection.HeadersFooters)
    {
        section.HeadersFooters.Add(headerFooter.Clone(true));
    }
}
```

## Conclusione

Seguendo questi passaggi, puoi aggiungere e personalizzare intestazioni e piè di pagina in modo efficace nei tuoi documenti Word utilizzando Aspose.Words per .NET. Questo migliorerà l'aspetto e la professionalità del tuo documento, rendendolo più leggibile e accattivante.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?

Aspose.Words per .NET è una libreria che consente agli sviluppatori di creare, modificare e convertire documenti Word a livello di programmazione all'interno delle applicazioni .NET.

### Posso aggiungere immagini all'intestazione o al piè di pagina?

Sì, puoi aggiungere facilmente immagini all'intestazione o al piè di pagina utilizzando `DocumentBuilder.InsertImage` metodo.

### Come posso impostare intestazioni e piè di pagina diversi per la prima pagina?

È possibile impostare intestazioni e piè di pagina diversi per la prima pagina utilizzando `DifferentFirstPageHeaderFooter` proprietà del `PageSetup` classe.

### Dove posso trovare ulteriore documentazione su Aspose.Words?

Puoi trovare una documentazione completa su [Pagina di documentazione dell'API Aspose.Words](https://reference.aspose.com/words/net/).

### È disponibile il supporto per Aspose.Words?

Sì, Aspose offre supporto tramite il loro [forum di supporto](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}