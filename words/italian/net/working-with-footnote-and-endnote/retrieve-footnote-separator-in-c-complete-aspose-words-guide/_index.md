---
category: general
date: 2026-08-07
description: Recupera il separatore delle note a piè di pagina usando Aspose.Words
  per .NET. Scopri come estrarre i separatori delle note a piè di pagina e delle note
  finali, ispezionare i tipi di nodo e modificarli in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- retrieve footnote separator
- Aspose.Words footnote separator
- C# footnote extraction
- endnote separator retrieval
- document node type
language: it
lastmod: 2026-08-07
og_description: Recupera il separatore delle note a piè di pagina con Aspose.Words
  per .NET. Questa guida mostra come estrarre i separatori delle note a piè di pagina
  e delle note finali, verificare i loro tipi di nodo e salvare le modifiche.
og_image_alt: Console output demonstrating retrieve footnote separator results
og_title: Recupera il separatore di nota a piè di pagina in C# – tutorial passo‑passo
  Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: retrieve footnote separator using Aspose.Words for .NET. Learn how
    to extract footnote and endnote separators, inspect node types, and modify them
    in C#.
  headline: retrieve footnote separator in C# – complete Aspose.Words guide
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
title: Recuperare il separatore delle note a piè di pagina in C# – guida completa
  ad Aspose.Words
url: /it/net/working-with-footnote-and-endnote/retrieve-footnote-separator-in-c-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# recuperare il separatore di nota a piè di pagina in C# – guida completa Aspose.Words

Se hai bisogno di **retrieve footnote separator** da un documento Word, questo tutorial ti mostra esattamente come farlo con Aspose.Words per .NET. Che tu stia creando un servizio di elaborazione documenti o pulendo la formattazione delle note a piè di pagina, vedrai un esempio completo e eseguibile che estrae sia i separatori di note a piè di pagina sia quelli di note finali.

In questa guida imparerai come caricare un file `.docx`, chiamare le proprietà `FootnoteSeparator` e `EndnoteSeparator`, ispezionare gli oggetti `Node` restituiti e, facoltativamente, sostituire la linea del separatore. Non è necessaria alcuna documentazione esterna—tutto ciò di cui hai bisogno è incluso di seguito.

## Prerequisiti

* .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.7.2)
* Pacchetto NuGet Aspose.Words per .NET (versione 24.9 o successiva)
* Un documento Word che contiene note a piè di pagina e/o note finali (ad es., `Footnotes.docx`)

Puoi aggiungere il pacchetto Aspose.Words con il seguente comando CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

## Passo 1: Configura il progetto e importa gli spazi dei nomi

Crea un nuovo progetto console o aggiungi il codice a uno esistente. Le direttive `using` richieste sono elencate di seguito.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Questi spazi dei nomi ti danno accesso alla classe `Document`, alla gerarchia `Node` e all'enumerazione `NodeType` necessarie per le operazioni di **retrieve footnote separator**.

## Passo 2: Carica il documento che contiene note a piè di pagina e note finali

La prima operazione in qualsiasi flusso di lavoro Aspose.Words è caricare il file di origine. Sostituisci il percorso segnaposto con la posizione reale del tuo `.docx`.

```csharp
// Load a document that contains footnotes and endnotes
Document doc = new Document(@"C:\Docs\Footnotes.docx");

// Verify that the document was loaded
Console.WriteLine($"Document loaded: {doc.OriginalFileName}");
```

Il caricamento del file prepara l'albero interno dei nodi, fondamentale per **retrieve footnote separator** poiché i nodi separatori vivono all'interno di quell'albero.

## Passo 3: Recupera il nodo separatore di nota a piè di pagina

Ora puoi **retrieve footnote separator** accedendo alla proprietà `FootnoteSeparator` dell'oggetto `Document`. Questo nodo rappresenta la linea che separa le note a piè di pagina dal testo principale.

```csharp
// Retrieve the footnote separator node (the line that separates footnotes from the main text)
Node footnoteSeparator = doc.FootnoteSeparator;

// Output its type for verification
Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");
```

Il `NodeType` sarà `Paragraph` per una linea separatore standard. Conoscere il tipo di nodo ti aiuta a decidere se modificare il separatore o sostituirlo completamente.

## Passo 4: Recupera il nodo separatore di nota finale

Allo stesso modo, puoi **retrieve endnote separator** usando la proprietà `EndnoteSeparator`. Questo nodo separa le note finali dal contenuto principale.

```csharp
// Retrieve the endnote separator node (the line that separates endnotes from the main text)
Node endnoteSeparator = doc.EndnoteSeparator;

// Output its type for verification
Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");
```

Entrambi i nodi separatori condividono lo stesso `NodeType` (`Paragraph`) nella maggior parte dei documenti, ma possono essere personalizzati in modo indipendente.

## Passo 5: Ispeziona o modifica il contenuto del separatore (opzionale)

Se hai bisogno di cambiare l'aspetto visivo del separatore—ad esempio sostituendo una linea di trattini con una regola sottile—puoi modificare direttamente il nodo `Paragraph`. Di seguito è riportato un esempio che sostituisce il testo predefinito del separatore con una stringa personalizzata.

```csharp
// Cast to Paragraph to access its text
Paragraph footnotePara = (Paragraph)footnoteSeparator;
footnotePara.Clear(); // Remove existing runs
footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

// Do the same for the endnote separator
Paragraph endnotePara = (Paragraph)endnoteSeparator;
endnotePara.Clear();
endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));
```

Dopo aver modificato i nodi, puoi salvare il documento per vedere le modifiche riflesse in Word.

```csharp
// Save the updated document
string outputPath = @"C:\Docs\Footnotes_Updated.docx";
doc.Save(outputPath);
Console.WriteLine($"Updated document saved to: {outputPath}");
```

## Output previsto della console

Quando esegui il programma con il `Footnotes.docx` originale, dovresti vedere qualcosa di simile a:

```
Document loaded: Footnotes.docx
Footnote separator node type: Paragraph
Endnote separator node type: Paragraph
Updated document saved to: C:\Docs\Footnotes_Updated.docx
```

Se apri `Footnotes_Updated.docx` in Microsoft Word, i separatori di note a piè di pagina e note finali mostreranno il testo personalizzato che hai inserito.

## Domande comuni e casi particolari

**Cosa succede se il documento non ha note a piè di pagina?**  
La proprietà `FootnoteSeparator` restituisce comunque un nodo `Paragraph` perché Word include sempre un segnaposto per il separatore. Il nodo sarà vuoto, quindi puoi aggiungere contenuto in modo sicuro o lasciarlo così com'è.

**Posso recuperare il separatore per una sezione specifica?**  
I separatori di note a piè di pagina e note finali sono a livello di documento, non specifici per sezione. Se hai bisogno di un controllo a livello di sezione, devi lavorare con `Section.FootnoteOptions` e `Section.EndnoteOptions` invece dei nodi separatori globali.

**Funziona con .NET Core?**  
Sì. Aspose.Words per .NET è cross‑platform e lo stesso codice funziona su Windows, Linux e macOS con .NET 6+.

**Quale tipo di nodo dovrei aspettarmi?**  
Sia `FootnoteSeparator` che `EndnoteSeparator` restituiscono un nodo `Paragraph` (`NodeType.Paragraph`). Se incontri un tipo diverso, il documento potrebbe essere corrotto e dovresti ricaricare o convalidare il file di origine.

## Codice sorgente completo per copia‑incolla veloce

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace RetrieveFootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // Load the document containing footnotes and endnotes
            Document doc = new Document(@"C:\Docs\Footnotes.docx");
            Console.WriteLine($"Document loaded: {doc.OriginalFileName}");

            // Retrieve footnote separator
            Node footnoteSeparator = doc.FootnoteSeparator;
            Console.WriteLine($"Footnote separator node type: {footnoteSeparator.NodeType}");

            // Retrieve endnote separator
            Node endnoteSeparator = doc.EndnoteSeparator;
            Console.WriteLine($"Endnote separator node type: {endnoteSeparator.NodeType}");

            // OPTIONAL: Customize separator text
            Paragraph footnotePara = (Paragraph)footnoteSeparator;
            footnotePara.Clear();
            footnotePara.AppendChild(new Run(doc, "— Custom Footnote Separator —"));

            Paragraph endnotePara = (Paragraph)endnoteSeparator;
            endnotePara.Clear();
            endnotePara.AppendChild(new Run(doc, "— Custom Endnote Separator —"));

            // Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Updated.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Updated document saved to: {outputPath}");
        }
    }
}
```

Copia il codice in un file `Program.cs`, regola i percorsi dei file e esegui `dotnet run`. Il programma dimostra l'intero flusso di lavoro **retrieve footnote separator**, dal caricamento del documento al salvataggio delle modifiche.

## Conclusione

Ora sai come **retrieve footnote separator** e **endnote separator retrieval** usando Aspose.Words per .NET, ispezionare il loro `document node type` e, facoltativamente, sostituire il loro contenuto. Questa tecnica ti consente di automatizzare la formattazione delle note a piè di pagina, generare linee separatore personalizzate o convalidare la struttura del documento in qualsiasi applicazione C#.

Successivamente, potresti esplorare argomenti correlati come **C# footnote extraction** per testi di note a piè di pagina individuali, o imparare come **modify footnote reference marks** usando `FootnoteOptions`. Entrambi i concetti si basano direttamente sui fondamenti dell'albero dei nodi trattati qui.

Buon coding, e sentiti libero di sperimentare con diversi stili di separatore per adattarli al branding del tuo progetto!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Add Content Using Document Builder in Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/)
- [Working With Footnote And Endnote](/words/hindi/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}