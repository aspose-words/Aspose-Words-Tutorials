---
"description": "Scopri come riavviare i numeri di elenco nei documenti Word utilizzando Aspose.Words per .NET. Questa guida dettagliata di 2000 parole copre tutto ciò che devi sapere, dalla configurazione alla personalizzazione avanzata."
"linktitle": "Numero elenco di riavvio"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Numero elenco di riavvio"
"url": "/it/net/working-with-list/restart-list-number/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Numero elenco di riavvio

## Introduzione

Vuoi padroneggiare l'arte della manipolazione degli elenchi nei tuoi documenti Word usando Aspose.Words per .NET? Beh, sei nel posto giusto! In questo tutorial, approfondiremo il riavvio dei numeri degli elenchi, una funzionalità ingegnosa che porterà le tue competenze di automazione dei documenti a un livello superiore. Allacciati le cinture e iniziamo!

## Prerequisiti

Prima di passare al codice, assicuriamoci di avere tutto il necessario:

1. Aspose.Words per .NET: è necessario aver installato Aspose.Words per .NET. Se non l'hai ancora installato, puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: assicurati di disporre di un ambiente di sviluppo adatto, come Visual Studio.
3. Conoscenza di base di C#: una conoscenza di base di C# ti aiuterà a seguire il tutorial.

## Importa spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Sono fondamentali per accedere alle funzionalità di Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Lists;
using System.Drawing;
```

Ora, scomponiamo il processo in passaggi semplici da seguire. Parleremo di tutto, dalla creazione di un elenco alla riattivazione della numerazione.

## Passaggio 1: imposta il documento e il generatore

Prima di poter iniziare a manipolare gli elenchi, hai bisogno di un documento e di un DocumentBuilder. DocumentBuilder è lo strumento ideale per aggiungere contenuti al tuo documento.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Passaggio 2: crea e personalizza il tuo primo elenco

Successivamente, creeremo un elenco basato su un modello e ne personalizzeremo l'aspetto. In questo esempio, utilizziamo il formato numerico arabo con parentesi.

```csharp
List list1 = doc.Lists.Add(ListTemplate.NumberArabicParenthesis);
list1.ListLevels[0].Font.Color = Color.Red;
list1.ListLevels[0].Alignment = ListLevelAlignment.Right;
```

Qui abbiamo impostato il colore del carattere su rosso e allineato il testo a destra.

## Passaggio 3: aggiungi elementi al tuo primo elenco

Con la tua lista pronta, è il momento di aggiungere alcuni elementi. Il DocumentBuilder `ListFormat.List` La proprietà aiuta ad applicare il formato elenco al testo.

```csharp
builder.Writeln("List 1 starts below:");
builder.ListFormat.List = list1;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Passaggio 4: riavviare la numerazione degli elenchi

Per riutilizzare l'elenco e riavviarne la numerazione, è necessario creare una copia dell'elenco originale. Ciò consente di modificare il nuovo elenco in modo indipendente.

```csharp
List list2 = doc.Lists.AddCopy(list1);
list2.ListLevels[0].StartAt = 10;
```

In questo esempio, il nuovo elenco inizia dal numero 10.

## Passaggio 5: aggiungere elementi al nuovo elenco

Proprio come prima, aggiungi elementi alla tua nuova lista. Questo dimostra che la lista riparte dal numero specificato.

```csharp
builder.Writeln("List 2 starts below:");
builder.ListFormat.List = list2;
builder.Writeln("Item 1");
builder.Writeln("Item 2");
builder.ListFormat.RemoveNumbers();
```

## Passaggio 6: salva il documento

Infine, salva il documento nella directory specificata.

```csharp
builder.Document.Save(dataDir + "WorkingWithList.RestartListNumber.docx");
```

## Conclusione

Riavviare i numeri di elenco nei documenti Word utilizzando Aspose.Words per .NET è semplice e incredibilmente utile. Che tu stia generando report, creando documenti strutturati o semplicemente abbia bisogno di un maggiore controllo sui tuoi elenchi, questa tecnica fa al caso tuo.

## Domande frequenti

### Posso utilizzare altri modelli di elenco oltre a NumberArabicParenthesis?

Assolutamente! Aspose.Words offre diversi modelli di elenco, come elenchi puntati, lettere, numeri romani e altro ancora. Puoi scegliere quello più adatto alle tue esigenze.

### Come posso modificare il livello dell'elenco?

È possibile modificare il livello dell'elenco modificando `ListLevels` proprietà. Ad esempio, `list1.ListLevels[1]` si riferirebbe al secondo livello dell'elenco.

### Posso ricominciare la numerazione da qualsiasi numero?

Sì, puoi impostare il numero iniziale su qualsiasi valore intero utilizzando `StartAt` proprietà del livello di elenco.

### È possibile avere formattazioni diverse per diversi livelli di elenco?

Esatto! Ogni livello di elenco può avere le proprie impostazioni di formattazione, come carattere, allineamento e stile di numerazione.

### Cosa succede se voglio continuare la numerazione da un elenco precedente invece di ricominciare?

Se vuoi continuare a numerare, non è necessario creare una copia dell'elenco. Continua semplicemente ad aggiungere elementi all'elenco originale.





{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}