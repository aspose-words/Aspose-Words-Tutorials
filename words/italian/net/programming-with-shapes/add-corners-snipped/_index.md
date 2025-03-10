---
title: Aggiungi angoli tagliati
linktitle: Aggiungi angoli tagliati
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come aggiungere una forma di angoli tagliati ai tuoi documenti Word usando Aspose.Words per .NET. Questa guida passo passo ti assicura di poter migliorare facilmente i tuoi documenti.
weight: 10
url: /it/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi angoli tagliati

## Introduzione

Aggiungere forme personalizzate ai tuoi documenti Word può essere un modo divertente e visivamente accattivante per evidenziare informazioni importanti o aggiungere un tocco di stile al tuo contenuto. In questo tutorial, ci immergeremo in come puoi inserire forme "Corners Snipped" nei tuoi documenti Word usando Aspose.Words per .NET. Questa guida ti guiderà attraverso ogni passaggio, assicurandoti di poter aggiungere senza sforzo queste forme e personalizzare i tuoi documenti come un professionista.

## Prerequisiti

Prima di passare al codice, assicuriamoci di avere tutto il necessario per iniziare:

1.  Aspose.Words per .NET: se non l'hai ancora fatto, scarica l'ultima versione da[Pagina delle release di Aspose](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: imposta il tuo ambiente di sviluppo. Visual Studio è una scelta popolare, ma puoi usare qualsiasi IDE che supporti .NET.
3.  Licenza: se stai solo sperimentando, puoi usare un[prova gratuita](https://releases.aspose.com/) o ottenere un[licenza temporanea](https://purchase.aspose.com/temporary-license/) per sbloccare tutte le funzionalità.
4. Nozioni di base di C#: la familiarità con la programmazione C# ti aiuterà a seguire gli esempi.

## Importazione degli spazi dei nomi

Prima di poter iniziare a lavorare con Aspose.Words per .NET, dobbiamo importare i namespace necessari. Aggiungili in cima al tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Ora, scomponiamo il processo di aggiunta di una forma "Corners Snipped" in più passaggi. Segui attentamente questi passaggi per assicurarti che tutto funzioni senza intoppi.

## Passaggio 1: inizializzare il documento e DocumentBuilder

 La prima cosa che dobbiamo fare è creare un nuovo documento e inizializzarlo`DocumentBuilder` oggetto. Questo costruttore ci aiuterà ad aggiungere contenuti al nostro documento.

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 In questo passaggio, abbiamo impostato il nostro documento e il nostro builder. Pensate al`DocumentBuilder` come penna digitale, pronta per scrivere e disegnare nel tuo documento Word.

## Passaggio 2: inserire la forma degli angoli tagliati

 Successivamente, utilizzeremo il`DocumentBuilder` per inserire una forma "Corners Snipped". Questo tipo di forma è predefinito in Aspose.Words e può essere facilmente inserito con una singola riga di codice.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Qui, stiamo specificando il tipo di forma e le sue dimensioni (50x50). Immagina di posizionare un piccolo adesivo con un angolo perfettamente tagliato sul tuo documento. 

## Passaggio 3: definire le opzioni di salvataggio con conformità

Prima di salvare il nostro documento, dobbiamo definire le opzioni di salvataggio per garantire che il nostro documento sia conforme a standard specifici. Utilizzeremo il`OoxmlSaveOptions` classe per questo.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Queste opzioni di salvataggio garantiscono che il nostro documento rispetti lo standard ISO/IEC 29500:2008, fondamentale per la compatibilità e la longevità del documento.

## Passaggio 4: Salvare il documento

Infine, salviamo il nostro documento nella directory specificata utilizzando le opzioni di salvataggio definite in precedenza.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

E in un attimo il tuo documento conterrà una forma personalizzata "Angoli tagliati", salvata con le opzioni di conformità necessarie.

## Conclusione

Ecco fatto! Aggiungere forme personalizzate ai tuoi documenti Word usando Aspose.Words per .NET è semplice e può migliorare notevolmente l'aspetto visivo dei tuoi documenti. Seguendo questi passaggi, puoi facilmente inserire una forma "Corners Snipped" e assicurarti che il tuo documento soddisfi gli standard richiesti. Buona codifica!

## Domande frequenti

### Posso personalizzare la dimensione della forma "Angoli tagliati"?
Sì, puoi regolare le dimensioni modificando le dimensioni in`InsertShape` metodo.

### È possibile aggiungere altri tipi di forme?
 Assolutamente! Aspose.Words supporta varie forme. Basta cambiare il`ShapeType` nella forma desiderata.

### Ho bisogno di una licenza per utilizzare Aspose.Words?
Sebbene sia possibile utilizzare una prova gratuita o una licenza temporanea, per un utilizzo senza restrizioni è richiesta una licenza completa.

### Come posso personalizzare ulteriormente le forme?
È possibile utilizzare proprietà e metodi aggiuntivi forniti da Aspose.Words per personalizzare l'aspetto e il comportamento delle forme.

### Aspose.Words è compatibile con altri formati?
Sì, Aspose.Words supporta numerosi formati di documenti, tra cui DOCX, PDF, HTML e altri.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
