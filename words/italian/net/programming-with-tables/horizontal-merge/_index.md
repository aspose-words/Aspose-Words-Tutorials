---
title: Unione orizzontale
linktitle: Unione orizzontale
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come unire orizzontalmente le celle in un documento Word utilizzando Aspose.Words per .NET con questo tutorial dettagliato e passo dopo passo.
weight: 10
url: /it/net/programming-with-tables/horizontal-merge/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Unione orizzontale

## Introduzione

Ciao! Pronti a tuffarvi nel mondo di Aspose.Words per .NET? Oggi affronteremo una funzionalità super utile: l'unione orizzontale nelle tabelle. Potrebbe sembrare un po' tecnico, ma non preoccupatevi, ci penso io. Alla fine di questo tutorial, sarete dei professionisti nell'unione di celle nei vostri documenti Word a livello di programmazione. Quindi, rimbocchiamoci le maniche e iniziamo!

## Prerequisiti

Prima di entrare nel vivo della questione, ecco alcune cose che devi sapere:

1. Libreria Aspose.Words per .NET: se non l'hai ancora fatto, scarica la libreria Aspose.Words per .NET. Puoi prenderla[Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: assicurati di aver configurato un ambiente di sviluppo adatto, ad esempio Visual Studio.
3. Conoscenza di base di C#: sarà utile una conoscenza di base della programmazione C#.

Una volta sistemati questi aspetti, sei pronto per partire!

## Importazione degli spazi dei nomi

Prima di immergerci nel codice, assicuriamoci di aver importato i namespace necessari. Nel tuo progetto C#, assicurati di includere:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Bene, analizziamo il processo di unione orizzontale delle celle di una tabella in un documento Word utilizzando Aspose.Words per .NET.

## Passaggio 1: impostazione del documento

 Prima di tutto, dobbiamo creare un nuovo documento Word e inizializzare il`DocumentBuilder`:

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Questo frammento di codice imposta un nuovo documento e prepara il`DocumentBuilder` per l'azione.

## Passaggio 2: inserimento della prima cella

Successivamente, iniziamo inserendo la prima cella e contrassegnandola per l'unione orizzontale:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.First;
builder.Write("Text in merged cells.");
```

 Qui inseriamo una nuova cella e impostiamo la sua`HorizontalMerge`proprietà a`CellMerge.First`, indicando che questa cella è l'inizio di una sequenza di cellule unite.

## Passaggio 3: inserimento della cella unita

Adesso inseriamo la cella che verrà unita alla precedente:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.Previous;
builder.EndRow();
```

 Questa cella è impostata per essere unita alla cella precedente utilizzando`CellMerge.Previous` Nota come concludiamo la riga con`builder.EndRow()`.

## Passaggio 4: inserimento di celle non unite

Per illustrare la differenza, inseriamo un paio di celle non unite:

```csharp
builder.InsertCell();
builder.CellFormat.HorizontalMerge = CellMerge.None;
builder.Write("Text in one cell.");
builder.InsertCell();
builder.Write("Text in another cell.");
builder.EndRow();
```

Qui inseriamo due celle senza unione orizzontale. Questo mostra come si comportano le celle quando non fanno parte di una sequenza unita.

## Fase 5: Completamento della tabella

Infine, chiudiamo la tabella e salviamo il documento:

```csharp
builder.EndTable();
doc.Save(dataDir + "WorkingWithTables.HorizontalMerge.docx");
```

Questo frammento di codice completa la tabella e salva il documento nella directory specificata.

## Conclusione

Ed ecco fatto! Hai appena imparato l'arte di unire orizzontalmente le celle in un documento Word usando Aspose.Words per .NET. Seguendo questi passaggi, puoi creare strutture di tabelle complesse con facilità. Continua a sperimentare ed esplorare le capacità di Aspose.Words per rendere i tuoi documenti dinamici e flessibili come desideri. Buona codifica!

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria che consente agli sviluppatori di creare, modificare e manipolare documenti Word a livello di programmazione nelle applicazioni .NET.

### Posso unire le celle verticalmente con Aspose.Words per .NET?
 Sì, puoi anche unire le celle verticalmente utilizzando`CellFormat.VerticalMerge` proprietà.

### Aspose.Words per .NET è gratuito?
 Aspose.Words per .NET offre una prova gratuita, ma per la piena funzionalità, dovrai acquistare una licenza. Puoi ottenere una licenza temporanea[Qui](https://purchase.aspose.com/temporary-license/).

### Come posso saperne di più su Aspose.Words per .NET?
 Puoi esplorare la documentazione dettagliata[Qui](https://reference.aspose.com/words/net/).

### Dove posso ottenere supporto per Aspose.Words per .NET?
 Per qualsiasi domanda o problema, puoi visitare il forum di supporto di Aspose[Qui](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
