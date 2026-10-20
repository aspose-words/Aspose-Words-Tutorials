---
category: general
date: 2026-08-04
description: Modifica il separatore delle note a piè di pagina in C# con Aspose.Words
  – impara a modificare il separatore delle note a piè di pagina e a cambiare il separatore
  delle note finali nei documenti Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- change footnote separator
- edit footnote separator
- how to change footnote separator
- change endnote separator
language: it
lastmod: 2026-08-04
og_description: Modifica il separatore delle note a piè di pagina in C# con Aspose.Words.
  Questa guida ti mostra come modificare il separatore delle note a piè di pagina,
  personalizzare il separatore delle note di chiusura e salvare il documento aggiornato.
og_image_alt: Screenshot showing the changed footnote separator in a Word document
og_title: Modifica il separatore delle note a piè di pagina in C# – guida completa
  ad Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Change footnote separator in C# using Aspose.Words – learn how to edit
    footnote separator and change endnote separator in Word documents.
  headline: Change footnote separator in C# using Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Footnotes
- Document processing
title: Modifica il separatore delle note a piè di pagina in C# usando Aspose.Words
url: /it/net/working-with-footnote-and-endnote/change-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Modifica il separatore delle note a piè di pagina in C# usando Aspose.Words

Se hai bisogno di **cambiare il separatore delle note a piè di pagina** in un documento Word, questo tutorial ti guida passo passo con Aspose.Words per .NET. Che tu voglia sostituire la linea predefinita con un simbolo, o applicare uno stile diverso ai separatori delle note a fine documento, il codice qui sotto copre l'intero flusso di lavoro.

Imparerai anche come **modificare il separatore delle note a piè di pagina** e l'operazione correlata **cambiare il separatore delle note a fine documento**, così lo stesso file potrà avere uno stile coerente sia per le note a piè di pagina sia per le note a fine documento. Non sono necessari strumenti esterni—bastano poche righe di C#.

## Cosa otterrai

* Caricare un file *.docx* esistente che contiene note a piè di pagina e note a fine documento.  
* Accedere ai nodi separatore per le note a piè di pagina, le continuazioni delle note a piè di pagina e le note a fine documento.  
* Sostituire il carattere del separatore (ad esempio, cambiare la linea predefinita in un asterisco).  
* Salvare il documento modificato senza perdere alcun altro contenuto.  

Il tutorial presuppone che tu abbia una conoscenza di base di C# e che abbia installato il pacchetto NuGet **Aspose.Words** (versione 24.9 o successiva).  

---

## Prerequisiti

| Requisito | Motivo |
|-------------|--------|
| .NET 6.0+ o .NET Framework 4.7.2+ | Runtime richiesto per Aspose.Words |
| Aspose.Words for .NET library | Fornisce le API `Document` e `FootnoteOptions` |
| Un file Word di input (`input.docx`) con almeno una nota a piè di pagina o nota a fine documento | Dimostra il cambiamento del separatore |

Puoi aggiungere Aspose.Words al tuo progetto con il seguente comando CLI:

```bash
dotnet add package Aspose.Words --version 24.9.0
```

---

## Passo 1: Carica il documento contenente le note a piè di pagina

La prima operazione è leggere il file sorgente in un oggetto `Document`. Questo oggetto rappresenta l'intero file Word in memoria e ti dà accesso a tutti i suoi nodi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;

// Load the .docx file that contains footnotes and endnotes.
Document document = new Document(@"C:\Docs\input.docx");
```

**Perché è importante:** Caricare il documento è il punto di ingresso per qualsiasi manipolazione. Se il file non viene trovato, Aspose.Words genera una `FileNotFoundException`, quindi assicurati che il percorso sia corretto prima di procedere.

---

## Passo 2: Accedi ai nodi separatore delle note a piè di pagina e delle note a fine documento

`Document.FootnoteOptions` espone tre nodi separatore:

* `Separator` – la linea che appare dopo la raccolta di note a piè di pagina nella prima pagina.  
* `ContinuationSeparator` – la linea usata quando le note a piè di pagina continuano nella pagina successiva.  
* `EndnoteSeparator` – la linea che separa il testo principale dall'elenco delle note a fine documento.

Recuperi questi nodi come oggetti generici `Node`, poi li casti a `Run` per modificare il testo.

```csharp
// Retrieve the three separator nodes.
Node footnoteSeparator = document.FootnoteOptions.Separator;
Node footnoteContinuation = document.FootnoteOptions.ContinuationSeparator;
Node endnoteSeparator = document.FootnoteOptions.EndnoteSeparator;
```

**Perché è importante:** Questi nodi sono gli unici luoghi in cui vive il carattere visivo del separatore. Modificare qualsiasi altro nodo (ad esempio, un paragrafo normale) non influenzerà la formattazione delle note a piè di pagina.

---

## Passo 3: Cambia il carattere del separatore delle note a piè di pagina

Il requisito più comune è sostituire la linea predefinita con un simbolo come un asterisco (`*`). Poiché il separatore è memorizzato come un `Run`, puoi modificare in sicurezza la sua proprietà `Text`.

```csharp
// Change the primary footnote separator to an asterisk.
if (footnoteSeparator is Run footnoteRun)
{
    footnoteRun.Text = "*";
}

// Optionally, change the continuation separator as well.
if (footnoteContinuation is Run continuationRun)
{
    continuationRun.Text = "*";
}
```

**Perché è importante:** Modificando direttamente `Run.Text` aggiorni la rappresentazione visiva nel documento finale senza influire sul resto del contenuto delle note a piè di pagina. Lo stesso schema può essere usato per applicare qualsiasi stringa, inclusi simboli Unicode.

---

## Passo 4: Cambia il separatore delle note a fine documento (opzionale)

Se hai anche bisogno di **cambiare il separatore delle note a fine documento**, il processo è analogo a quello per le note a piè di pagina. Sostituisci il testo di `endnoteSeparator` con il carattere desiderato.

```csharp
// Change the endnote separator to a dash.
if (endnoteSeparator is Run endnoteRun)
{
    endnoteRun.Text = "-";
}
```

**Perché è importante:** Le note a fine documento sono spesso formattate diversamente dalle note a piè di pagina. Fornire un separatore separato ti consente di mantenere la coerenza visiva con le linee guida di design del documento.

---

## Passo 5: Salva il documento modificato

Dopo tutte le modifiche, persisti le modifiche usando `Document.Save`. Puoi sovrascrivere il file originale o scrivere in una nuova posizione.

```csharp
// Save the updated document.
document.Save(@"C:\Docs\ModifiedSeparators.docx");
```

**Perché è importante:** `Save` scrive la rappresentazione in memoria su disco, preservando tutti gli altri elementi (stili, immagini, tabelle) invariati.

---

## Esempio completo, eseguibile

Unendo tutti i pezzi, ecco un'applicazione console autonoma che dimostra l'intero flusso di lavoro:

```csharp
using System;
using Aspose.Words;

namespace FootnoteSeparatorDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Load the source document.
            string inputPath = @"C:\Docs\input.docx";
            Document doc = new Document(inputPath);

            // 2️⃣ Access separator nodes.
            Node footnoteSep = doc.FootnoteOptions.Separator;
            Node footnoteCont = doc.FootnoteOptions.ContinuationSeparator;
            Node endnoteSep = doc.FootnoteOptions.EndnoteSeparator;

            // 3️⃣ Change footnote separator to an asterisk.
            if (footnoteSep is Run footnoteRun)
                footnoteRun.Text = "*";

            // Optional: also change the continuation separator.
            if (footnoteCont is Run contRun)
                contRun.Text = "*";

            // 4️⃣ Change endnote separator to a dash.
            if (endnoteSep is Run endnoteRun)
                endnoteRun.Text = "-";

            // 5️⃣ Save the result.
            string outputPath = @"C:\Docs\ModifiedSeparators.docx";
            doc.Save(outputPath);

            Console.WriteLine("Document saved to " + outputPath);
        }
    }
}
```

**Risultato atteso:** Apri *ModifiedSeparators.docx* in Microsoft Word. La linea del separatore delle note a piè di pagina nella parte inferiore della prima pagina di note sarà ora un singolo asterisco (`*`). Se il documento contiene note a fine documento, la linea che separa il testo principale dall'elenco delle note a fine documento apparirà come un trattino (`-`). Tutto il resto del contenuto (testo, immagini, tabelle) rimane intatto.

---

## Domande comuni e gestione dei casi limite

| Domanda | Risposta |
|----------|--------|
| **E se il documento non contiene note a piè di pagina?** | `FootnoteOptions.Separator` restituisce comunque un nodo `Run`, ma il suo testo potrebbe essere vuoto. Il codice verifica in modo sicuro il tipo di nodo prima di modificarlo. |
| **Posso usare una stringa multicarattere (ad es., "***")?** | Sì. La proprietà `Run.Text` accetta qualsiasi stringa, inclusi caratteri Unicode. |
| **La modifica del separatore influirà sulla numerazione esistente delle note a piè di pagina?** | No. Il separatore è indipendente dallo schema di numerazione. |
| **Devo rilasciare l'oggetto `Document`?** | `Document` implementa implicitamente `IDisposable` tramite `Node`. In un'app console a breve vita è opzionale, ma per servizi a lunga esecuzione puoi avvolgerlo in un blocco `using`. |
| **Come funziona questo con .NET Core vs .NET Framework?** | L'API è identica su tutti i runtime; conta solo la versione del framework di destinazione (deve essere supportata dal pacchetto Aspose.Words). |

**Suggerimento professionale:** Se devi applicare separatori diversi per sezioni differenti, puoi iterare su `doc.GetChildNodes(NodeType.Footnote, true)` e regolare individualmente la proprietà `Separator` di ciascuna nota. È più avanzato ma utile per documenti complessi.

---

## Conclusione

Ora sai come **cambiare il separatore delle note a piè di pagina** e **cambiare il separatore delle note a fine documento** in un file Word usando Aspose.Words per C#. La guida ha coperto il caricamento del documento, l'accesso ai nodi separatore pertinenti, la modifica del loro testo e il salvataggio del risultato—tutto in un unico programma autonomo.

Da qui puoi esplorare argomenti correlati come **modificare lo stile del separatore delle note a piè di pagina**, personalizzare la numerazione delle note o applicare formattazioni condizionali in base al layout della pagina. Lo stesso schema (recuperare un nodo, castarlo a `Run`, modificare `Text`) funziona per molte altre situazioni di elaborazione di Word.

Buona programmazione, e sentiti libero di sperimentare con simboli diversi o persino inserire immagini come separatori per un layout di documento davvero unico!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Get Paragraph Style Separator In Word Document](/words/english/net/document-formatting/get-paragraph-style-separator/)
- [Insert Document Style Separator in Word](/words/english/net/programming-with-styles-and-themes/insert-style-separator/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}