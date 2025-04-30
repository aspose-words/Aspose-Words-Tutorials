---
"description": "Scopri come inserire un campo modulo con casella combinata in un documento Word utilizzando Aspose.Words per .NET. Segui questa guida passo passo per una perfetta integrazione dei contenuti HTML."
"linktitle": "Tipo di controllo preferito nel documento Word"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Tipo di controllo preferito nel documento Word"
"url": "/it/net/programming-with-htmlloadoptions/preferred-control-type/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Tipo di controllo preferito nel documento Word

## Introduzione

Ci stiamo immergendo in un entusiasmante tutorial su come utilizzare le opzioni di caricamento HTML in Aspose.Words per .NET, concentrandoci in particolare sull'impostazione del tipo di controllo preferito quando si inserisce un campo modulo di tipo casella combinata in un documento Word. Questa guida passo passo vi aiuterà a capire come manipolare e visualizzare efficacemente il contenuto HTML nei vostri documenti Word utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di passare al codice, ecco alcune cose che devi sapere:

1. Aspose.Words per .NET: assicurati di aver installato la libreria Aspose.Words per .NET. Puoi scaricarla da [sito web](https://releases.aspose.com/words/net/).
2. Ambiente di sviluppo: dovresti disporre di un ambiente di sviluppo configurato, come Visual Studio.
3. Conoscenza di base di C#: per seguire il tutorial è necessaria una conoscenza fondamentale della programmazione C#.
4. Contenuto HTML: è utile avere una conoscenza di base dell'HTML poiché in questo esempio lavoreremo con contenuti HTML.

## Importa spazi dei nomi

Per prima cosa, importiamo gli spazi dei nomi necessari per iniziare:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Ora, scomponiamo l'esempio in più passaggi per garantire chiarezza e comprensione.

## Passaggio 1: imposta il contenuto HTML

Per prima cosa, dobbiamo definire il contenuto HTML che vogliamo inserire nel documento Word. Ecco il frammento HTML che useremo:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

Questo codice HTML contiene una semplice casella combinata con due opzioni. Caricheremo questo codice HTML in un documento Word e specificheremo come visualizzarlo.

## Passaggio 2: definire la directory dei documenti

Successivamente, specifica la directory in cui verrà salvato il documento Word. Questo ti aiuterà a organizzare i file e a mantenere pulita la gestione dei percorsi.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo in cui desideri salvare il documento Word.

## Passaggio 3: configurare le opzioni di caricamento HTML

Qui configuriamo le opzioni di caricamento HTML, concentrandoci in particolare su `PreferredControlType` proprietà. Determina come deve essere visualizzata la casella combinata nel documento Word.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

Impostando `PreferredControlType` A `HtmlControlType.StructuredDocumentTag`, ci assicuriamo che la casella combinata venga visualizzata come tag di documento strutturato (SDT) nel documento Word.

## Passaggio 4: caricare il contenuto HTML nel documento

Utilizzando le opzioni di caricamento configurate, carichiamo il contenuto HTML in un nuovo documento Word.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Qui convertiamo la stringa HTML in un array di byte e la carichiamo nel documento utilizzando un flusso di memoria. Questo garantisce che il contenuto HTML venga interpretato e renderizzato correttamente da Aspose.Words.

## Passaggio 5: salvare il documento

Infine, salva il documento nella directory specificata in formato DOCX.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

In questo modo il documento Word con il controllo casella combinata renderizzato viene salvato nella posizione specificata.

## Conclusione

Ed ecco fatto! Abbiamo inserito con successo un campo modulo di tipo casella combinata in un documento Word utilizzando Aspose.Words per .NET, sfruttando le opzioni di caricamento HTML. Questa guida passo passo ti aiuterà a comprendere il processo e ad applicarlo ai tuoi progetti. Che tu stia automatizzando la creazione di documenti o manipolando contenuti HTML, Aspose.Words per .NET offre potenti strumenti per raggiungere i tuoi obiettivi.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per la manipolazione di documenti che consente agli sviluppatori di creare, modificare, convertire ed eseguire il rendering di documenti Word a livello di programmazione.

### Posso utilizzare altri tipi di controllo HTML con Aspose.Words per .NET?
Sì, Aspose.Words per .NET supporta vari tipi di controlli HTML. È possibile personalizzare il rendering dei diversi controlli nel documento Word.

### Come gestire contenuti HTML complessi in Aspose.Words per .NET?
Aspose.Words per .NET offre un supporto completo per HTML, inclusi gli elementi complessi. Assicurati di configurare `HtmlLoadOptions` in modo appropriato per gestire i tuoi specifici contenuti HTML.

### Dove posso trovare altri esempi e documentazione?
Puoi trovare documentazione dettagliata ed esempi su [Pagina di documentazione di Aspose.Words per .NET](https://reference.aspose.com/words/net/).

### È disponibile una versione di prova gratuita di Aspose.Words per .NET?
Sì, puoi scaricare una versione di prova gratuita da [Sito web di Aspose](https://releases.aspose.com/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}