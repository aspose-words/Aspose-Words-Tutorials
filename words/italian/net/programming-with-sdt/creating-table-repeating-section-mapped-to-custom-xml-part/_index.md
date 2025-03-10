---
title: Creazione di una sezione ripetuta della tabella mappata alla parte XML personalizzata
linktitle: Creazione di una sezione ripetuta della tabella mappata alla parte XML personalizzata
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come creare una tabella con una sezione ripetuta mappata a una CustomXmlPart in un documento Word utilizzando Aspose.Words per .NET.
weight: 10
url: /it/net/programming-with-sdt/creating-table-repeating-section-mapped-to-custom-xml-part/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creazione di una sezione ripetuta della tabella mappata alla parte XML personalizzata

## Introduzione

In questo tutorial, illustreremo il processo di creazione di una tabella con una sezione ripetuta che è mappata a una parte XML personalizzata usando Aspose.Words per .NET. Ciò è particolarmente utile per generare dinamicamente documenti basati su dati strutturati.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:
1.  Aspose.Words per la libreria .NET installata. Puoi scaricarla da[Sito web di Aspose](https://releases.aspose.com/words/net/).
2. Conoscenza di base di C# e XML.

## Importazione degli spazi dei nomi

Assicurati di includere gli spazi dei nomi necessari nel tuo progetto:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
using Aspose.Words.Tables;
```

## Passaggio 1: inizializzare Document e DocumentBuilder

 Per prima cosa, crea un nuovo documento e inizializza un`DocumentBuilder`:

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 2: aggiungere la parte XML personalizzata

Aggiungi una parte XML personalizzata al documento. Questo XML contiene i dati che vogliamo mappare alla nostra tabella:

```csharp
CustomXmlPart xmlPart = doc.CustomXmlParts.Add("Books",
    "<books><book><title>Everyday Italian</title><author>Giada De Laurentiis</author></book>" +
    "<book><title>Harry Potter</title><author>J K. Rowling</author></book>" +
    "<book><title>Learning XML</title><author>Erik T. Ray</author></book></books>");
```

## Passaggio 3: creare la struttura della tabella

 Quindi, utilizzare il`DocumentBuilder` per creare l'intestazione della tabella:

```csharp
Table table = builder.StartTable();
builder.InsertCell();
builder.Write("Title");
builder.InsertCell();
builder.Write("Author");
builder.EndRow();
builder.EndTable();
```

## Passaggio 4: creare una sezione ripetuta

 Crea un`StructuredDocumentTag` (SDT) per la sezione ripetuta e mapparla nei dati XML:

```csharp
StructuredDocumentTag repeatingSectionSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSection, MarkupLevel.Row);
repeatingSectionSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book", "");
table.AppendChild(repeatingSectionSdt);
```

## Passaggio 5: creare un elemento di sezione ripetuto

Crea un SDT per l'elemento della sezione ripetuta e aggiungilo alla sezione ripetuta:

```csharp
StructuredDocumentTag repeatingSectionItemSdt = new StructuredDocumentTag(doc, SdtType.RepeatingSectionItem, MarkupLevel.Row);
repeatingSectionSdt.AppendChild(repeatingSectionItemSdt);
Row row = new Row(doc);
repeatingSectionItemSdt.AppendChild(row);
```

## Passaggio 6: mappare i dati XML alle celle della tabella

Crea SDT per il titolo e l'autore, associali ai dati XML e aggiungili alla riga:

```csharp
StructuredDocumentTag titleSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
titleSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/title[1]", "");
row.AppendChild(titleSdt);

StructuredDocumentTag authorSdt = new StructuredDocumentTag(doc, SdtType.PlainText, MarkupLevel.Cell);
authorSdt.XmlMapping.SetMapping(xmlPart, "/books[1]/book[1]/author[1]", "");
row.AppendChild(authorSdt);
```

## Passaggio 7: Salvare il documento

Infine, salva il documento nella directory specificata:

```csharp
doc.Save(dataDir + "WorkingWithSdt.CreatingTableRepeatingSectionMappedToCustomXmlPart.docx");
```

## Conclusione

Seguendo questi passaggi, hai creato con successo una tabella con una sezione ripetuta mappata a una parte XML personalizzata utilizzando Aspose.Words per .NET. Ciò consente la generazione di contenuti dinamici basati su dati strutturati, rendendo la creazione di documenti più flessibile e potente.

## Domande frequenti

### Che cos'è uno StructuredDocumentTag (SDT)?
Un SDT, noto anche come controllo del contenuto, è un'area delimitata in un documento utilizzata per contenere dati strutturati.

### Posso utilizzare altri tipi di dati nella parte XML personalizzata?
Sì, puoi strutturare la tua parte XML personalizzata con qualsiasi tipo di dati e mapparli di conseguenza.

### Come posso aggiungere più righe alla sezione ripetuta?
La sezione ripetuta replica automaticamente la struttura delle righe per ciascun elemento nel percorso XML mappato.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
