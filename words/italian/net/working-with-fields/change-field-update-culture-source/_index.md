---
title: Cambia campo Aggiorna cultura origine
linktitle: Cambia campo Aggiorna cultura origine
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come modificare la sorgente della cultura di aggiornamento del campo in Aspose.Words per .NET con questa guida. Controlla facilmente la formattazione della data in base a culture diverse.
weight: 10
url: /it/net/working-with-fields/change-field-update-culture-source/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Cambia campo Aggiorna cultura origine

## Introduzione

In questo tutorial, ci immergeremo nel mondo di Aspose.Words per .NET ed esploreremo come modificare la sorgente della cultura di aggiornamento dei campi. Se hai a che fare con documenti Word che includono campi data e hai bisogno di controllare come queste date vengono formattate in base a culture diverse, questa guida è per te. Esaminiamo il processo passo dopo passo, assicurandoti di comprendere ogni concetto e di poterlo applicare efficacemente nei tuoi progetti.

## Prerequisiti

Prima di passare al codice, assicurati di avere quanto segue:

-  Aspose.Words per .NET: puoi scaricarlo da[Qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: qualsiasi IDE compatibile con .NET (ad esempio Visual Studio).
- Conoscenza di base di C#: questo tutorial presuppone una conoscenza fondamentale della programmazione in C#.

## Importazione degli spazi dei nomi

Per prima cosa, importiamo i namespace necessari per il nostro progetto. Questo ci assicurerà di avere accesso a tutte le classi e i metodi richiesti forniti da Aspose.Words.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Ora scomponiamo l'esempio in più passaggi per aiutarti a capire come modificare l'origine della cultura di aggiornamento dei campi in Aspose.Words per .NET.

## Passaggio 1: inizializzare il documento

 Il primo passo è creare una nuova istanza di`Document` classe e una`DocumentBuilder`Questo pone le basi per la creazione e la manipolazione del nostro documento Word.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 2: inserire campi con impostazioni locali specifiche

Poi, dobbiamo inserire i campi nel documento. Per questo esempio, inseriremo due campi data. Imposteremo le impostazioni locali del font su German (LocaleId = 1031) per dimostrare come la cultura influisce sul formato della data.

```csharp
builder.Font.LocaleId = 1031; // tedesco
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Passaggio 3: imposta la sorgente della cultura di aggiornamento del campo

 Per controllare la cultura utilizzata durante l'aggiornamento dei campi, impostiamo`FieldUpdateCultureSource` proprietà del`FieldOptions`classe. Questa proprietà determina se la cultura viene presa dal codice di campo o dal documento.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Passaggio 4: eseguire la stampa unione

Ora dobbiamo eseguire una stampa unione per popolare i campi con dati effettivi. In questo esempio, imposteremo il secondo campo data (`Date2`) al 1° gennaio 2011.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Passaggio 5: Salvare il documento

Infine, salviamo il documento nella directory specificata. Questo passaggio completa il processo di modifica della sorgente della cultura di aggiornamento del campo.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Conclusione

Ed ecco fatto! Hai modificato con successo la sorgente della cultura di aggiornamento campo in Aspose.Words per .NET. Seguendo questi passaggi, puoi assicurarti che i tuoi documenti Word visualizzino date e altri valori di campo in base alle impostazioni di cultura specificate. Ciò può essere particolarmente utile quando si generano documenti per un pubblico internazionale.

## Domande frequenti

###  Qual è lo scopo dell'impostazione del`LocaleId`?
 IL`LocaleId` specifica le impostazioni culturali per il testo, che influiscono sul modo in cui vengono formattate le date e altri dati sensibili locali.

### Posso usare una lingua diversa dal tedesco?
 Sì, puoi impostare il`LocaleId` qualsiasi identificatore locale valido. Ad esempio, 1033 per inglese (Stati Uniti).

###  Cosa succede se non imposto il`FieldUpdateCultureSource` property?
Se questa proprietà non è impostata, durante l'aggiornamento dei campi verranno utilizzate le impostazioni cultura predefinite del documento.

### È possibile aggiornare i campi in base alla cultura del documento anziché in base al codice di campo?
 Sì, puoi impostare`FieldUpdateCultureSource` A`FieldUpdateCultureSource.Document` per utilizzare le impostazioni culturali del documento.

### Come posso formattare le date seguendo uno schema diverso?
 È possibile modificare il modello del formato della data in`InsertField` metodo modificando il`\\@` valore di commutazione.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
