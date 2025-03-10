---
title: Inserisci campo Includi testo senza generatore di documenti
linktitle: Inserisci FieldIncludeText senza Document Builder
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come inserire un FieldIncludeText senza usare DocumentBuilder in Aspose.Words per .NET con la nostra guida dettagliata e passo dopo passo.
weight: 10
url: /it/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci campo Includi testo senza generatore di documenti

## Introduzione

Nel mondo dell'automazione e della manipolazione dei documenti, Aspose.Words per .NET rappresenta uno strumento potente. Oggi, ci immergiamo in una guida dettagliata su come inserire un FieldIncludeText senza usare DocumentBuilder. Questo tutorial ti guiderà passo dopo passo nel processo, assicurandoti di comprendere ogni parte del codice e il suo scopo.

## Prerequisiti

Prima di immergerci nel codice, assicuriamoci di avere tutto ciò di cui hai bisogno:

1.  Aspose.Words per .NET: assicurati di avere installata l'ultima versione. Puoi scaricarla da[Qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo .NET: qualsiasi IDE compatibile con .NET come Visual Studio.
3. Conoscenza di base di C#: la familiarità con la programmazione C# ti aiuterà a seguire il corso.

## Importazione degli spazi dei nomi

Per prima cosa, dobbiamo importare i namespace necessari. Questi namespace forniscono l'accesso alle classi e ai metodi richiesti per manipolare i documenti Word.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Ora, scomponiamo l'esempio in più passaggi. Ogni passaggio sarà spiegato in dettaglio per garantire chiarezza.

## Passaggio 1: impostare il percorso della directory

Il primo passo è definire il percorso per la directory dei tuoi documenti. È qui che i tuoi documenti Word saranno archiviati e accessibili.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Passaggio 2: creare il documento e il paragrafo

Poi, creiamo un nuovo documento e un paragrafo al suo interno. Questo paragrafo conterrà il campo FieldIncludeText.

```csharp
// Creare il documento e il paragrafo.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Passaggio 3: Inserisci il campo FieldIncludeText

Ora, inseriamo il campo FieldIncludeText nel paragrafo. Questo campo consente di includere il testo da un altro documento.

```csharp
// Inserisci il campo FieldIncludeText.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Passaggio 4: impostare le proprietà del campo

Dobbiamo specificare le proprietà per il campo FieldIncludeText. Ciò include l'impostazione del nome del segnalibro e del percorso completo del documento sorgente.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Passaggio 5: aggiungere il paragrafo al documento

Una volta impostato il campo, aggiungiamo il paragrafo al corpo della prima sezione del documento.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Passaggio 6: Aggiorna campo

Prima di salvare il documento, dobbiamo aggiornare FieldIncludeText per garantire che estragga il contenuto corretto dal documento di origine.

```csharp
fieldIncludeText.Update();
```

## Passaggio 7: Salvare il documento

Infine, salviamo il documento nella directory specificata.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi facilmente inserire un FieldIncludeText senza usare DocumentBuilder in Aspose.Words per .NET. Questo approccio fornisce un modo semplificato per includere contenuti da un documento in un altro, rendendo le tue attività di automazione dei documenti molto più semplici.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?  
Aspose.Words per .NET è una potente libreria per lavorare con documenti Word in applicazioni .NET. Consente di creare, modificare e convertire documenti in modo programmatico.

### Perché utilizzare FieldIncludeText?  
FieldIncludeText è utile per includere dinamicamente contenuti da un documento a un altro, consentendo di creare documenti più modulari e gestibili.

### Posso usare questo metodo per includere testo da altri formati di file?  
FieldIncludeText funziona specificamente con i documenti Word. Per altri formati, potresti aver bisogno di metodi o classi diversi forniti da Aspose.Words.

### Aspose.Words per .NET è compatibile con .NET Core?  
Sì, Aspose.Words per .NET supporta .NET Framework, .NET Core e .NET 5/6.

### Come posso ottenere una prova gratuita di Aspose.Words per .NET?  
 Puoi ottenere una prova gratuita da[Qui](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
