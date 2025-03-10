---
title: Disposizione nella cella
linktitle: Disposizione nella cella
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come impostare il layout in cella usando Aspose.Words per .NET con questa guida completa. Perfetta per gli sviluppatori che vogliono personalizzare i documenti Word.
weight: 10
url: /it/net/programming-with-shapes/layout-in-cell/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Disposizione nella cella

## Introduzione

Se hai mai voluto mettere a punto il layout delle celle della tua tabella nei documenti Word in modo programmatico, sei nel posto giusto. Oggi, ci immergeremo in come impostare il layout in cella usando Aspose.Words per .NET. Ti guideremo attraverso un esempio pratico, suddividendolo passo dopo passo in modo che tu possa seguire con facilità.

## Prerequisiti

Prima di passare al codice, assicuriamoci di avere tutto ciò di cui hai bisogno:

1.  Aspose.Words per .NET: assicurati di avere la libreria Aspose.Words per .NET installata. Se non l'hai ancora fatto, puoi[scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: avrai bisogno di un ambiente di sviluppo configurato con .NET. Visual Studio è un'ottima scelta se stai cercando consigli.
3. Conoscenza di base di C#: anche se spiegherò ogni passaggio, una conoscenza di base di C# ti aiuterà a seguire più facilmente.
4.  Directory dei documenti: prepara un percorso di directory in cui salverai i tuoi documenti. Ci riferiremo a questo come`YOUR DOCUMENT DIRECTORY`.

## Importazione degli spazi dei nomi

Per iniziare, assicurati di importare gli spazi dei nomi necessari nel tuo progetto:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Scomponiamo il processo in passaggi gestibili.

## Passaggio 1: creare un nuovo documento

 Per prima cosa, creeremo un nuovo documento Word e inizializzeremo un`DocumentBuilder` oggetto per aiutarci a costruire i nostri contenuti.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 2: avviare una tabella e impostare il formato di riga

Inizieremo costruendo una tabella e specificheremo l'altezza e la regola dell'altezza per le righe.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Passaggio 3: inserire le celle e compilarle con il contenuto

Poi, facciamo un ciclo per inserire celle nella tabella. Per ogni 7 celle, termineremo la riga per crearne una nuova.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Passaggio 4: aggiungere una forma di filigrana

 Ora, aggiungiamo una filigrana al nostro documento. Creeremo un`Shape` oggetto e impostarne le proprietà.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Visualizza la forma all'esterno della cella della tabella se verrà inserita in una cella.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Passaggio 5: personalizzare l'aspetto della filigrana

Personalizzeremo ulteriormente l'aspetto della filigrana impostandone le proprietà del colore e del testo.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Passaggio 6: Inserisci la filigrana nel documento

Troveremo l'ultima esecuzione nel documento e inseriremo la filigrana in quella posizione.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Passaggio 7: Ottimizzare il documento per Word 2010

Per garantire la compatibilità, ottimizzeremo il documento per Word 2010.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Passaggio 8: Salvare il documento

Infine, salveremo il nostro documento nella directory specificata.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Conclusione

Ed ecco fatto! Hai creato con successo un documento Word con un layout di tabella personalizzato e aggiunto una filigrana usando Aspose.Words per .NET. Questo tutorial mirava a fornire una guida chiara e passo dopo passo per aiutarti a comprendere ogni parte del processo. Con queste competenze, ora puoi creare documenti Word più sofisticati e personalizzati a livello di programmazione.

## Domande frequenti

### Posso usare un font diverso per il testo della filigrana?
 Sì, puoi cambiare il font impostando`watermark.TextPath.FontFamily` proprietà al font desiderato.

### Come faccio a regolare la posizione della filigrana?
 Puoi modificare il`RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment` , E`VerticalAlignment` proprietà per regolare la posizione della filigrana.

### È possibile utilizzare un'immagine al posto del testo per la filigrana?
 Assolutamente! Puoi creare un`Shape` con il tipo`ShapeType.Image` e imposta la sua immagine usando`ImageData.SetImage` metodo.

### Posso creare tabelle con altezze di riga diverse?
Sì, puoi impostare altezze diverse per ogni riga modificando il`RowFormat.Height` proprietà prima di inserire le celle in quella riga.

### Come faccio a rimuovere una filigrana dal documento?
 È possibile rimuovere la filigrana individuandola nella raccolta di forme del documento e chiamando il comando`Remove` metodo.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
