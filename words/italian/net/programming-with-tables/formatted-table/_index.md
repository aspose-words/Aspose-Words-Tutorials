---
title: Tabella formattata
linktitle: Tabella formattata
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come creare e formattare tabelle nei documenti Word utilizzando Aspose.Words per .NET con questa guida dettagliata passo dopo passo.
weight: 10
url: /it/net/programming-with-tables/formatted-table/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tabella formattata

## Introduzione

Creare e formattare tabelle nei documenti Word a livello di programmazione può sembrare un compito arduo, ma con Aspose.Words per .NET diventa semplice e gestibile. In questo tutorial, ti guideremo attraverso la creazione di una tabella formattata in un documento Word utilizzando Aspose.Words per .NET. Tratteremo tutto, dall'impostazione dell'ambiente al salvataggio del documento con una tabella splendidamente formattata.

## Prerequisiti

Prima di immergerci nel codice, assicuriamoci di avere tutto ciò di cui hai bisogno:

1. Aspose.Words per la libreria .NET: scaricala da[Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: un IDE come Visual Studio.
3. .NET Framework: assicurati che .NET Framework sia installato sul tuo computer.

## Importazione degli spazi dei nomi

Prima di scrivere il codice effettivo, è necessario importare gli spazi dei nomi necessari:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

## Passaggio 1: imposta la directory dei documenti

Per prima cosa devi definire il percorso in cui verrà salvato il documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo in cui si desidera salvare il documento.

## Passaggio 2: inizializzare il documento e DocumentBuilder

Ora inizializziamo un nuovo documento e un oggetto DocumentBuilder.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 IL`DocumentBuilder` è una classe helper che semplifica il processo di creazione dei documenti.

## Passaggio 3: avviare la tabella

 Quindi, inizia a creare la tabella utilizzando`StartTable` metodo.

```csharp
Table table = builder.StartTable();
builder.InsertCell();
```

Per iniziare la tabella è necessario inserire una cella.

## Passaggio 4: applicare la formattazione a livello di tabella

Puoi applicare una formattazione che influenzi l'intera tabella. Ad esempio, impostando il rientro a sinistra:

```csharp
table.LeftIndent = 20.0;
```

## Passaggio 5: formattare la riga dell'intestazione

Imposta l'altezza, l'allineamento e altre proprietà per la riga dell'intestazione.

```csharp
builder.RowFormat.Height = 40.0;
builder.RowFormat.HeightRule = HeightRule.AtLeast;
builder.CellFormat.Shading.BackgroundPatternColor = Color.FromArgb(198, 217, 241);
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Font.Size = 16;
builder.Font.Name = "Arial";
builder.Font.Bold = true;
builder.CellFormat.Width = 100.0;
builder.Write("Header Row,\n Cell 1");
```

In questa fase, rendiamo visibile la riga dell'intestazione impostando un colore di sfondo, una dimensione del carattere e un allineamento.

## Passaggio 6: inserire celle di intestazione aggiuntive

Inserisci più celle per la riga di intestazione:

```csharp
builder.InsertCell();
builder.Write("Header Row,\n Cell 2");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Header Row,\n Cell 3");
builder.EndRow();
```

## Passaggio 7: formattare le righe del corpo

Dopo aver impostato l'intestazione, formattare il corpo della tabella:

```csharp
builder.CellFormat.Shading.BackgroundPatternColor = Color.White;
builder.CellFormat.Width = 100.0;
builder.CellFormat.VerticalAlignment = CellVerticalAlignment.Center;
builder.RowFormat.Height = 30.0;
builder.RowFormat.HeightRule = HeightRule.Auto;
```

## Passaggio 8: Inserisci le righe del corpo

Inserire le righe del corpo con il contenuto:

```csharp
builder.InsertCell();
builder.Font.Size = 12;
builder.Font.Bold = false;
builder.Write("Row 1, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 1, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 1, Cell 3 Content");
builder.EndRow();
```

Ripetere per le righe aggiuntive:

```csharp
builder.InsertCell();
builder.CellFormat.Width = 100.0;
builder.Write("Row 2, Cell 1 Content");
builder.InsertCell();
builder.Write("Row 2, Cell 2 Content");
builder.InsertCell();
builder.CellFormat.Width = 200.0;
builder.Write("Row 2, Cell 3 Content.");
builder.EndRow();
builder.EndTable();
```

## Passaggio 9: Salvare il documento

Infine, salva il documento nella directory specificata:

```csharp
doc.Save(dataDir + "WorkingWithTables.FormattedTable.docx");
```

Verrà creato e salvato un documento Word con la tabella formattata.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi creare una tabella ben formattata in un documento Word usando Aspose.Words per .NET. Questa potente libreria semplifica la manipolazione programmatica dei documenti Word, risparmiando tempo e fatica.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per creare, modificare e convertire documenti Word a livello di programmazione.

### Posso usare colori diversi per righe diverse?
Sì, puoi applicare formattazioni diverse, compresi i colori, a righe o celle diverse.

### Aspose.Words per .NET è gratuito?
 Aspose.Words per .NET è una libreria a pagamento, ma è possibile ottenerne una[prova gratuita](https://releases.aspose.com/).

### Come posso ottenere supporto per Aspose.Words per .NET?
 Puoi ottenere supporto da[Forum della comunità Aspose](https://forum.aspose.com/c/words/8).

### Posso creare altri tipi di documenti con Aspose.Words per .NET?
Sì, Aspose.Words per .NET supporta vari formati di documento, tra cui PDF, HTML e TXT.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
