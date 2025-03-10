---
title: Aggiungi prefisso nome classe CSS
linktitle: Aggiungi prefisso nome classe CSS
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come aggiungere un prefisso al nome della classe CSS quando salvi documenti Word come HTML utilizzando Aspose.Words per .NET. Guida dettagliata, frammenti di codice e FAQ incluse.
weight: 10
url: /it/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi prefisso nome classe CSS

## Introduzione

Benvenuti! Se vi state tuffando nel mondo di Aspose.Words per .NET, vi aspetta una sorpresa. Oggi esploreremo come aggiungere un prefisso del nome di classe CSS quando si salva un documento Word come HTML usando Aspose.Words per .NET. Questa funzionalità è molto utile quando si vogliono evitare conflitti di nomi di classe nei file HTML.

## Prerequisiti

Prima di iniziare, assicurati di avere quanto segue:

-  Aspose.Words per .NET: se non lo hai ancora installato,[scaricalo qui](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: Visual Studio o qualsiasi altro IDE C#.
-  Un documento Word: utilizzeremo un documento denominato`Rendering.docx`Inseriscilo nella directory del tuo progetto.

## Importazione degli spazi dei nomi

Per prima cosa, assicurati di aver importato i namespace necessari nel tuo progetto C#. Aggiungili in cima al tuo file di codice:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Ora, entriamo nel vivo della guida passo dopo passo!

## Passaggio 1: imposta il tuo progetto

Prima di poter iniziare ad aggiungere un prefisso al nome della classe CSS, impostiamo il nostro progetto.

### Passaggio 1.1: creare un nuovo progetto

 Avvia Visual Studio e crea un nuovo progetto Console App. Chiamalo con un nome accattivante come`AsposeCssPrefixExample`.

### Passaggio 1.2: aggiungere Aspose.Words per .NET

Se non l'hai già fatto, aggiungi Aspose.Words for .NET al tuo progetto tramite NuGet. Apri semplicemente la NuGet Package Manager Console ed esegui:

```bash
Install-Package Aspose.Words
```

Ottimo! Ora siamo pronti per iniziare a programmare.

## Passaggio 2: carica il documento

La prima cosa che dobbiamo fare è caricare il documento Word che vogliamo convertire in HTML.

### Passaggio 2.1: definire il percorso del documento

 Imposta il percorso per la directory del tuo documento. Per il bene di questo tutorial, supponiamo che il tuo documento sia in una cartella denominata`Documents` all'interno della directory del progetto.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Passaggio 2.2: Caricare il documento

Ora carichiamo il documento utilizzando Aspose.Words:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Passaggio 3: configurare le opzioni di salvataggio HTML

Successivamente, dobbiamo configurare le opzioni di salvataggio HTML per includere un prefisso per il nome della classe CSS.

### Passaggio 3.1: creare opzioni di salvataggio HTML

 Istanziare il`HtmlSaveOptions` oggetto e imposta il tipo di foglio di stile CSS su`External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Passaggio 3.2: Imposta il prefisso del nome della classe CSS

 Ora, impostiamo il`CssClassNamePrefix` proprietà al prefisso desiderato. Per questo esempio, useremo`"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Passaggio 4: Salvare il documento come HTML

Infine, salviamo il documento come file HTML con le opzioni configurate.


Specificare il percorso del file HTML di output e salvare il documento.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Passaggio 5: verificare l'output

 Dopo aver eseguito il progetto, vai al tuo`Documents` cartella. Dovresti trovare un file HTML denominato`WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html` . Apri questo file in un editor di testo o in un browser per verificare che le classi CSS abbiano il prefisso`pfx_`.

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, hai aggiunto con successo un prefisso del nome di classe CSS al tuo output HTML usando Aspose.Words per .NET. Questa semplice ma potente funzionalità può aiutarti a mantenere stili puliti e senza conflitti nei tuoi documenti HTML.

## Domande frequenti

### Posso usare un prefisso diverso per ogni operazione di salvataggio?
 Sì, puoi personalizzare il prefisso ogni volta che salvi un documento modificando il`CssClassNamePrefix` proprietà.

### Questo metodo supporta CSS in linea?
 IL`CssClassNamePrefix`proprietà funziona con CSS esterno. Per CSS inline, avrai bisogno di un approccio diverso.

### Come posso includere altre opzioni di salvataggio HTML?
 È possibile configurare varie proprietà di`HtmlSaveOptions` per personalizzare l'output HTML. Controlla il[documentazione](https://reference.aspose.com/words/net/) per maggiori dettagli.

### È possibile salvare l'HTML in un flusso?
 Assolutamente! Puoi salvare il documento in un flusso passando l'oggetto flusso al`Save` metodo.

### Come posso ottenere supporto se riscontro dei problemi?
 Puoi ottenere supporto da[Forum di Aspose](https://forum.aspose.com/c/words/8).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
