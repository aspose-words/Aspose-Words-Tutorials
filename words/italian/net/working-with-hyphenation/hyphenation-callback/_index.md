---
"description": "Scopri come implementare il callback di sillabazione in Aspose.Words per .NET per migliorare la formattazione dei documenti con questa guida completa passo dopo passo."
"linktitle": "Callback di sillabazione"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Callback di sillabazione"
"url": "/it/net/working-with-hyphenation/hyphenation-callback/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Callback di sillabazione


## Introduzione

Ciao! Ti sei mai trovato invischiato nelle complessità della formattazione del testo, soprattutto quando hai a che fare con linguaggi che richiedono la sillabazione? Non sei il solo. La sillabazione, sebbene fondamentale per un corretto layout del testo, può essere un po' un grattacapo. Ma indovina un po'? Aspose.Words per .NET ti aiuta. Questa potente libreria ti permette di gestire la formattazione del testo in modo impeccabile, inclusa la gestione della sillabazione tramite un meccanismo di callback. Ti ha incuriosito? Approfondiamo i dettagli di come implementare una callback per la sillabazione utilizzando Aspose.Words per .NET.

## Prerequisiti

Prima di sporcarci le mani con il codice, assicuriamoci di avere tutto ciò che ti serve:

1. Aspose.Words per .NET: assicurati di avere la libreria. Puoi [scaricalo qui](https://releases.aspose.com/words/net/).
2. IDE: ambiente di sviluppo come Visual Studio.
3. Conoscenza di base di C#: comprensione di C# e del framework .NET.
4. Dizionari di sillabazione: dizionari di sillabazione per le lingue che intendi utilizzare.
5. Licenza Aspose: una licenza Aspose valida. Puoi ottenere una [licenza temporanea](https://purchase.aspose.com/temporary-license/) se non ne hai uno.

## Importa spazi dei nomi

Per prima cosa, importiamo i namespace necessari. Questo garantisce che il nostro codice abbia accesso a tutte le classi e i metodi di cui abbiamo bisogno da Aspose.Words.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Passaggio 1: registrare il callback di sillabazione

Per iniziare, dobbiamo registrare il nostro callback di sillabazione. È qui che diciamo ad Aspose.Words di utilizzare la nostra logica di sillabazione personalizzata.

```csharp
try
{
    // Registra il callback di sillabazione.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

Qui, stiamo creando un'istanza del nostro callback personalizzato e assegnandolo a `Hyphenation.Callback`.

## Passaggio 2: definire il percorso del documento

Successivamente, dobbiamo definire la directory in cui sono archiviati i nostri documenti. Questo è fondamentale perché caricheremo e salveremo i documenti da questo percorso.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo per arrivare ai tuoi documenti.

## Passaggio 3: caricare il documento

Carichiamo ora il documento che richiede la sillabazione.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Qui stiamo caricando un documento di testo in tedesco. Puoi sostituirlo `"German text.docx"` con il nome file del tuo documento.

## Passaggio 4: salvare il documento

Dopo aver caricato il documento, lo salviamo in un nuovo file, applicando nel processo il callback di sillabazione.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Questa riga salva il documento come PDF con la sillabazione applicata.

## Passaggio 5: gestire l'eccezione del dizionario di sillabazione mancante

A volte, potresti riscontrare un problema dovuto alla mancanza del dizionario di sillabazione. Cerchiamo di risolvere il problema.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

In questo blocco, catturiamo l'eccezione specifica relativa ai dizionari mancanti e stampiamo il messaggio.

## Passaggio 6: implementare la classe di callback di sillabazione personalizzata

Ora, implementiamo il `CustomHyphenationCallback` classe che gestisce la richiesta di dizionari di sillabazione.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // Registra il dizionario per la lingua richiesta.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

In questa classe, il `RequestDictionary` Il metodo viene chiamato ogni volta che è necessario un dizionario di sillabazione. Controlla la lingua e registra il dizionario appropriato.

## Conclusione

Ed ecco fatto! Hai appena imparato a implementare una callback per la sillabazione in Aspose.Words per .NET. Seguendo questi passaggi, puoi garantire che i tuoi documenti siano formattati in modo impeccabile, indipendentemente dalla lingua. Che tu abbia a che fare con inglese, tedesco o qualsiasi altra lingua, questo metodo ti permette di gestire la sillabazione senza sforzo.

## Domande frequenti

### Che cos'è Aspose.Words per .NET?
Aspose.Words per .NET è una potente libreria per la manipolazione di documenti che consente agli sviluppatori di creare, modificare e convertire documenti a livello di programmazione.

### Perché la sillabazione è importante nella formattazione dei documenti?
La sillabazione migliora l'impaginazione del testo dividendo le parole nei punti appropriati, garantendo così un documento più leggibile e visivamente più accattivante.

### Posso usare Aspose.Words gratuitamente?
Aspose.Words offre una prova gratuita. Puoi ottenerla [Qui](https://releases.aspose.com/).

### Come posso ottenere un dizionario di sillabazione?
È possibile scaricare dizionari di sillabazione da varie risorse online o crearne di propri, se necessario.

### Cosa succede se manca un dizionario di sillabazione?
Se manca un dizionario, il `RequestDictionary` Il metodo genera un'eccezione, che puoi gestire per informare l'utente o fornire una soluzione di fallback.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}