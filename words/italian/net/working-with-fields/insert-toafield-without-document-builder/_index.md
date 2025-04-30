---
"description": "Scopri come inserire un campo TOA senza utilizzare un generatore di documenti in Aspose.Words per .NET. Segui la nostra guida passo passo per gestire in modo efficiente le citazioni legali."
"linktitle": "Inserisci campo TOA senza generatore di documenti"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Inserisci campo TOA senza generatore di documenti"
"url": "/it/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci campo TOA senza generatore di documenti

## Introduzione

Creare un campo TOA (Indice delle fonti) in un documento Word può sembrare un'impresa ardua. Tuttavia, con l'aiuto di Aspose.Words per .NET, il processo diventa semplice e intuitivo. In questo articolo, vi guideremo attraverso i passaggi per inserire un campo TOA senza utilizzare un generatore di documenti, semplificando la gestione di citazioni e riferimenti legali nei vostri documenti Word.

## Prerequisiti

Prima di immergerci nel tutorial, vediamo gli elementi essenziali di cui avrai bisogno:

- Aspose.Words per .NET: assicurati di avere installata la versione più recente. Puoi scaricarla da [Sito web di Aspose](https://releases.aspose.com/words/net/).
- Ambiente di sviluppo: un IDE compatibile con .NET come Visual Studio.
- Conoscenza di base del linguaggio C#: sarà utile comprendere la sintassi e i concetti di base del linguaggio C#.
- Esempio di documento Word: crea o tieni pronto un documento di esempio in cui vuoi inserire il campo TOA.

## Importa spazi dei nomi

Per iniziare, è necessario importare i namespace necessari dalla libreria Aspose.Words. Questa configurazione garantisce l'accesso a tutte le classi e i metodi necessari per la manipolazione dei documenti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Analizziamo il processo in passaggi semplici e facili da seguire. Ti guideremo attraverso ogni fase, spiegandoti cosa fa ogni pezzo di codice e come contribuisce alla creazione del campo TOA.

## Passaggio 1: inizializzare il documento

Per prima cosa, devi creare un'istanza di `Document` classe. Questo oggetto rappresenta il documento Word su cui stai lavorando.

```csharp
// Percorso verso la directory dei documenti.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Questo codice inizializza un nuovo documento Word. Puoi immaginarlo come la creazione di una tela bianca su cui aggiungere i tuoi contenuti.

## Passaggio 2: creare e configurare il campo TA

Successivamente, aggiungeremo un campo TA (Tabella delle fonti). Questo campo contrassegna le voci che appariranno nella TOA.

```csharp
Paragraph para = new Paragraph(doc);

// Vogliamo inserire i campi TA e TOA in questo modo:
// { TA \c 1 \l "Valore 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

Ecco una ripartizione:
- Paragrafo para = new Paragraph(doc);: Crea un nuovo paragrafo all'interno del documento.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Aggiunge un campo TA al paragrafo. IL `FieldType.FieldTOAEntry` specifica che questo è un campo di immissione TOA.
- fieldTA.EntryCategory = "1";: Imposta la categoria della voce. Questo è utile per categorizzare diversi tipi di voci.
- fieldTA.LongCitation = "Valore 0";: Specifica il testo della citazione lunga. Questo è il testo che apparirà nel TOA.
- doc.FirstSection.Body.AppendChild(para);: aggiunge il paragrafo con il campo TA al corpo del documento.

## Passaggio 3: aggiungere il campo TOA

Adesso inseriremo il campo TOA effettivo che compila tutte le voci TA in una tabella.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

In questa fase:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Aggiunge un campo TOA al paragrafo.
- fieldToa.EntryCategory = "1";: filtra le voci per includere solo quelle contrassegnate con la categoria "1".

## Passaggio 4: aggiorna il campo TOA

Dopo aver inserito il campo TOA, è necessario aggiornarlo per assicurarsi che rifletta le voci più recenti.

```csharp
fieldToa.Update();
```

Questo comando aggiorna il campo TOA, assicurando che tutte le voci contrassegnate vengano visualizzate correttamente nella tabella.

## Passaggio 5: salvare il documento

Infine, salva il documento con il campo TOA appena aggiunto.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Questa riga di codice salva il documento nella directory specificata. Assicurati di sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo in cui vuoi salvare il file.

## Conclusione

Ed ecco fatto! Hai aggiunto con successo un campo TOA a un documento Word senza utilizzare un generatore di documenti. Seguendo questi passaggi, puoi gestire in modo efficiente le citazioni e creare indici delle fonti completi nei tuoi documenti legali. Aspose.Words per .NET semplifica questo processo, offrendoti gli strumenti per gestire con facilità attività complesse sui documenti.

## Domande frequenti

### Posso aggiungere più campi TA con categorie diverse?
Sì, puoi aggiungere più campi TA con categorie diverse impostando `EntryCategory` proprietà di conseguenza.

### Come posso personalizzare l'aspetto del TOA?
È possibile personalizzare l'aspetto del TOA modificando le proprietà del campo TOA, come la formattazione delle voci e le etichette delle categorie.

### È possibile aggiornare automaticamente il campo TOA?
Sebbene sia possibile aggiornare manualmente il campo TOA utilizzando `Update` metodo, Aspose.Words attualmente non supporta gli aggiornamenti automatici in caso di modifiche al documento.

### Posso aggiungere campi TA in modo programmatico in parti specifiche del documento?
Sì, puoi aggiungere campi TA in posizioni specifiche inserendoli nei paragrafi o nelle sezioni desiderate.

### Come posso gestire più campi TOA in un singolo documento?
È possibile gestire più campi TOA assegnandone diversi `EntryCategory` valori e assicurando che ogni campo TOA filtri le voci in base alla sua categoria.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}