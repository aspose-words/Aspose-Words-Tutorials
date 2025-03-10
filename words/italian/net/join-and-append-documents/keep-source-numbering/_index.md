---
title: Mantieni la numerazione delle fonti
linktitle: Mantieni la numerazione delle fonti
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come importare documenti mantenendo la formattazione utilizzando Aspose.Words per .NET. Guida passo passo con esempi di codice.
weight: 10
url: /it/net/join-and-append-documents/keep-source-numbering/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Mantieni la numerazione delle fonti

## Introduzione

 Quando si lavora con Aspose.Words per .NET, l'importazione di documenti da una fonte all'altra preservando la formattazione può essere gestita in modo efficiente utilizzando`NodeImporter` classe. Questo tutorial ti guiderà passo dopo passo attraverso il processo.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:
- Visual Studio installato sul tuo computer.
-  Aspose.Words per .NET installato. In caso contrario, scaricalo da[Qui](https://releases.aspose.com/words/net/).
- Conoscenza di base della programmazione C# e .NET.

## Importazione degli spazi dei nomi

Per prima cosa, includi gli spazi dei nomi necessari nel tuo progetto:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Passaggio 1: imposta il tuo progetto

Per prima cosa, crea un nuovo progetto C# in Visual Studio e installa Aspose.Words tramite NuGet Package Manager.

## Passaggio 2: inizializzare i documenti
Crea istanze della sorgente (`srcDoc`) e destinazione (`dstDoc`) documenti.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Passaggio 3: configurare le opzioni di importazione
Imposta le opzioni di importazione per mantenere la formattazione originale, inclusi i paragrafi numerati.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Passaggio 4: importare paragrafi
Scorrere i paragrafi del documento di origine e importarli nel documento di destinazione.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Passaggio 5: Salvare il documento
Salvare il documento unito nella posizione desiderata.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Conclusione

 In conclusione, utilizzare Aspose.Words per .NET per importare documenti preservandone la formattazione è semplice con`NodeImporter` classe. Questo metodo assicura che i tuoi documenti mantengano il loro aspetto e la loro struttura originali senza soluzione di continuità.

## Domande frequenti

### Posso importare documenti con stili di formattazione diversi?
 Sì, il`NodeImporter` La classe supporta l'importazione di documenti con stili di formattazione diversi.

### Cosa succede se i miei documenti contengono tabelle e immagini complesse?
Aspose.Words per .NET gestisce strutture complesse come tabelle e immagini durante le operazioni di importazione.

### Aspose.Words è compatibile con tutte le versioni di .NET?
Aspose.Words supporta le versioni .NET Framework e .NET Core per un'integrazione perfetta.

### Come posso gestire gli errori durante l'importazione dei documenti?
Utilizzare blocchi try-catch per gestire le eccezioni che potrebbero verificarsi durante il processo di importazione.

### Dove posso trovare una documentazione più dettagliata su Aspose.Words per .NET?
 Visita il[documentazione](https://reference.aspose.com/words/net/) per guide complete e riferimenti API.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
