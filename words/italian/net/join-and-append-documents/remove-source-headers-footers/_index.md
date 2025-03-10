---
title: Rimuovi intestazioni e piè di pagina della fonte
linktitle: Rimuovi intestazioni e piè di pagina della fonte
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come rimuovere intestazioni e piè di pagina nei documenti Word usando Aspose.Words per .NET. Semplifica la gestione dei tuoi documenti con la nostra guida passo passo.
weight: 10
url: /it/net/join-and-append-documents/remove-source-headers-footers/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Rimuovi intestazioni e piè di pagina della fonte

## Introduzione

In questa guida completa, approfondiremo come rimuovere efficacemente intestazioni e piè di pagina da un documento Word utilizzando Aspose.Words per .NET. Intestazioni e piè di pagina sono comunemente utilizzati per la numerazione delle pagine, i titoli dei documenti o altri contenuti ripetuti nei documenti Word. Che tu stia unendo documenti o pulendo la formattazione, padroneggiare questo processo può semplificare le tue attività di gestione dei documenti. Esploriamo il processo passo dopo passo per ottenere questo risultato utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di immergerti nel tutorial, assicurati di aver impostato i seguenti prerequisiti:

1. Ambiente di sviluppo: avere installato Visual Studio o qualsiasi altro ambiente di sviluppo .NET.
2.  Aspose.Words per .NET: assicurati di aver scaricato e installato Aspose.Words per .NET. In caso contrario, puoi ottenerlo da[Qui](https://releases.aspose.com/words/net/).
3. Conoscenze di base: familiarità con la programmazione C# e con i fondamenti del framework .NET.

## Importazione degli spazi dei nomi

Prima di iniziare a scrivere il codice, assicurati di importare gli spazi dei nomi necessari nel tuo file C#:

```csharp
using Aspose.Words;
```

## Passaggio 1: caricare il documento sorgente

 Innanzitutto, devi caricare il documento sorgente da cui vuoi rimuovere intestazioni e piè di pagina. Sostituisci`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo alla directory del documento in cui si trova il documento sorgente.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Passaggio 2: creare o caricare il documento di destinazione

 Se non hai ancora creato un documento di destinazione in cui desideri posizionare il contenuto modificato, puoi crearne uno nuovo`Document` oggetto o caricarne uno esistente.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Passaggio 3: cancellare intestazioni e piè di pagina dalle sezioni

Eseguire l'iterazione attraverso ciascuna sezione nel documento sorgente (`srcDoc`) e cancellarne intestazioni e piè di pagina.

```csharp
foreach (Section section in srcDoc.Sections)
{
    section.ClearHeadersFooters();
}
```

## Passaggio 4: Gestisci l'impostazione LinkToPrevious

Per evitare che intestazioni e piè di pagina continuino nel documento di destinazione (`dstDoc` ), assicurarsi che il`LinkToPrevious` l'impostazione per intestazioni e piè di pagina è impostata su`false`.

```csharp
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Passaggio 5: aggiungere il documento modificato al documento di destinazione

Infine, aggiungi il contenuto modificato dal documento sorgente (`srcDoc`) al documento di destinazione (`dstDoc`) mantenendo la formattazione originale.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Passaggio 6: Salvare il documento risultante

Salva il documento finale con le intestazioni e i piè di pagina rimossi nella directory specificata.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.RemoveSourceHeadersFooters.docx");
```

## Conclusione

La rimozione di intestazioni e piè di pagina da un documento Word tramite Aspose.Words per .NET è un processo semplice che può migliorare notevolmente le attività di gestione dei documenti. Seguendo i passaggi descritti sopra, puoi ripulire in modo efficiente i documenti per un aspetto professionale e raffinato.

## Domande frequenti

### Posso rimuovere intestazioni e piè di pagina solo da sezioni specifiche?
Sì, puoi scorrere le sezioni e cancellare selettivamente intestazioni e piè di pagina in base alle tue esigenze.

### Aspose.Words per .NET supporta la rimozione di intestazioni e piè di pagina in più documenti?
Certamente, puoi manipolare intestazioni e piè di pagina in più documenti utilizzando Aspose.Words per .NET.

###  Cosa succede se dimentico di impostare`LinkToPrevious` to `false`?
Le intestazioni e i piè di pagina del documento di origine possono continuare nel documento di destinazione.

### Posso rimuovere intestazioni e piè di pagina a livello di codice senza influire su altre formattazioni?
Sì, Aspose.Words per .NET consente di rimuovere intestazioni e piè di pagina mantenendo inalterata la formattazione del resto del documento.

### Dove posso trovare ulteriori risorse e supporto per Aspose.Words per .NET?
 Visita il[Documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/) per riferimenti API dettagliati ed esempi.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
