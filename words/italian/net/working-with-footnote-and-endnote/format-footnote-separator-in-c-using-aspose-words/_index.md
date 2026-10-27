---
category: general
date: 2026-08-10
description: Formatta il separatore delle note a piè di pagina in C# con Aspose.Words
  per personalizzare le linee delle note a piè di pagina e delle note di chiusura.
  Impara la formattazione delle note a piè di pagina in C# in pochi minuti.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- format footnote separator
- Aspose.Words footnote separator
- C# footnote formatting
- modify footnote separator
- style footnote separator
- endnote separator formatting
language: it
lastmod: 2026-08-10
og_description: Formatta il separatore delle note a piè di pagina in C# usando Aspose.Words.
  Segui questo tutorial per stilizzare rapidamente e in modo affidabile i separatori
  di note a piè di pagina e di note finali.
og_image_alt: Code editor showing C# snippet that styles a footnote separator
og_title: Formattare il separatore di nota a piè di pagina in C# – guida completa
  ad Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-10'
  description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  headline: Format footnote separator in C# using Aspose.Words
  type: TechArticle
- description: Format footnote separator in C# with Aspose.Words to customize footnote
    and endnote lines. Learn C# footnote formatting in minutes.
  name: Format footnote separator in C# using Aspose.Words
  steps:
  - name: Styling the continuation separator (optional)
    text: 'The continuation separator appears when a footnote spans multiple pages.
      You can style it similarly:'
  - name: Formatting the endnote separator
    text: 'If your document also uses endnotes, you can apply the same logic to the
      `Endnotes` collection:'
  - name: Using a custom string for the separator
    text: 'Sometimes you want the separator to be a series of asterisks (`***`). Replace
      the existing runs with a new run:'
  - name: Handling documents without a separator node
    text: 'A rare edge case is a document that omits the separator node (e.g., when
      the author deleted it). In that scenario `document.Footnotes.Separator` returns
      `null`. Guard against it:'
  type: HowTo
tags:
- Aspose.Words
- C#
- footnotes
- document‑processing
title: Formattare il separatore delle note a piè di pagina in C# con Aspose.Words
url: /it/net/working-with-footnote-and-endnote/format-footnote-separator-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Formattare il separatore di nota a piè di pagina in C# usando Aspose.Words

Se hai bisogno di **formattare il separatore di nota a piè di pagina** in un documento Word, questa guida ti mostra come farlo con Aspose.Words per .NET. Vedrai un esempio completo e eseguibile che modifica l’allineamento e il colore del paragrafo separatore, e imparerai come applicare la stessa tecnica ai separatori di note finali.

Il tutorial copre ogni passaggio—dal caricamento del file sorgente al salvataggio del documento modificato—così potrai copiare‑incollare il codice nel tuo progetto senza ulteriori ricerche.

## Cosa ti serve

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
* Una licenza valida di Aspose.Words per .NET (la versione di prova gratuita è sufficiente per la valutazione)
* Un file Word che contenga almeno una nota a piè di pagina o una nota finale (ad es., `Footnotes.docx`)
* Visual Studio 2022 o qualsiasi IDE C# tu preferisca

Avere questi elementi pronti ti permette di concentrarti sulla **logica di formattazione delle note a piè di pagina in C#** invece che sulla configurazione dell’ambiente.

## Passo 1: Caricare il documento che contiene note a piè di pagina e note finali

La prima operazione è creare un oggetto `Document` che punti al tuo file sorgente. Aspose.Words legge l’intero pacchetto DOCX in memoria, offrendoti pieno accesso ai nodi delle note a piè di pagina e delle note finali.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
using System.Drawing;

// Load the source DOCX file
Document document = new Document(@"C:\Docs\Footnotes.docx");
```

*Perché è importante*: il caricamento del documento è un prerequisito per qualsiasi manipolazione. Se il percorso del file è errato, Aspose.Words genera una `FileNotFoundException`, quindi verifica il percorso prima di procedere.

## Passo 2: Recuperare i nodi separatore e separatore di continuazione

I separatori di note a piè di pagina e di note finali sono memorizzati come nodi speciali all’interno delle collezioni `Footnotes` e `Endnotes`. Ogni collezione espone le proprietà `Separator` e `ContinuationSeparator` che restituiscono un riferimento a un `Node`.

```csharp
// Footnote separator nodes
Node footnoteSeparator          = document.Footnotes.Separator;
Node footnoteContinuationSep    = document.Footnotes.ContinuationSeparator;

// Endnote separator nodes
Node endnoteSeparator           = document.Endnotes.Separator;
Node endnoteContinuationSep     = document.Endnotes.ContinuationSeparator;
```

*Perché è importante*: il nodo `Separator` rappresenta la linea che separa visivamente il testo principale dal blocco della nota a piè di pagina. Ottenendo un riferimento, puoi modificare il formato del paragrafo, il carattere o addirittura sostituire interamente il nodo.

## Passo 3: Modificare lo stile visivo del separatore di nota a piè di pagina

Nella maggior parte dei documenti Word il separatore è un singolo paragrafo che contiene un trattino o un asterisco. Il codice qui sotto verifica se il separatore è un `Paragraph` e, in tal caso, lo centra e ne cambia il colore del testo in grigio.

```csharp
// Ensure the separator is a Paragraph before casting
if (footnoteSeparator is Paragraph separatorParagraph)
{
    // Center the separator paragraph
    separatorParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;

    // Set the separator text color to gray
    if (separatorParagraph.Runs.Count > 0)
    {
        separatorParagraph.Runs[0].Font.Color = Color.Gray;
    }
}
```

### Formattare il separatore di continuazione (opzionale)

Il separatore di continuazione appare quando una nota a piè di pagina si estende su più pagine. Puoi formattarlo in modo simile:

```csharp
if (footnoteContinuationSep is Paragraph contParagraph)
{
    contParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (contParagraph.Runs.Count > 0)
        contParagraph.Runs[0].Font.Color = Color.DarkGray;
}
```

*Perché è importante*: allineare il separatore migliora la leggibilità e cambiare il colore lo distingue dal testo dei paragrafi normali. Puoi sostituire `ParagraphAlignment.Center` con `Left` o `Right` per adeguarlo alle linee guida di design del tuo documento.

## Passo 4: Salvare il documento modificato

Dopo aver applicato lo stile desiderato, scrivi il documento su disco. Puoi sovrascrivere il file originale o crearne una nuova versione.

```csharp
// Save the document with the modified separator
document.Save(@"C:\Docs\Footnotes_Styled.docx");
```

Quando apri `Footnotes_Styled.docx` in Microsoft Word, il separatore di nota a piè di pagina appare centrato e grigio, esattamente come specificato dal codice.

## Varianti avanzate

### Formattare il separatore di nota finale

Se il tuo documento utilizza anche le note finali, puoi applicare la stessa logica alla collezione `Endnotes`:

```csharp
if (endnoteSeparator is Paragraph endSepParagraph)
{
    endSepParagraph.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    if (endSepParagraph.Runs.Count > 0)
        endSepParagraph.Runs[0].Font.Color = Color.SlateGray;
}
```

### Usare una stringa personalizzata per il separatore

A volte vuoi che il separatore sia una serie di asterischi (`***`). Sostituisci le run esistenti con una nuova run:

```csharp
if (footnoteSeparator is Paragraph sepPara)
{
    // Clear existing content
    sepPara.Runs.Clear();

    // Add a custom separator string
    Run newRun = new Run(document, "***");
    newRun.Font.Color = Color.Gray;
    sepPara.Runs.Add(newRun);
}
```

### Gestire documenti senza nodo separatore

Un caso limite raro è un documento che omette il nodo separatore (ad es., quando l’autore lo ha eliminato). In quello scenario `document.Footnotes.Separator` restituisce `null`. Proteggi il tuo codice da questa eventualità:

```csharp
if (footnoteSeparator != null && footnoteSeparator is Paragraph sepPara)
{
    // Apply styling as shown earlier
}
else
{
    // Optionally create a new separator paragraph
    Paragraph newSep = new Paragraph(document);
    newSep.ParagraphFormat.Alignment = ParagraphAlignment.Center;
    Run run = new Run(document, "-");
    run.Font.Color = Color.Gray;
    newSep.Runs.Add(run);
    document.Footnotes.InsertAfter(newSep, document.Footnotes.LastParagraph);
}
```

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| **Il separatore non è un `Paragraph`** | Alcuni modelli Word usano una `Table` o una `Shape` come separatore. | Verifica il tipo di nodo con `is Paragraph` prima del cast. |
| **La collezione `Runs` è vuota** | Il separatore può essere un paragrafo vuoto. | Controlla che `Runs.Count > 0` prima di accedere a `Runs[0]`. |
| **Licenza non applicata** | Senza licenza, Aspose.Words inserisce una filigrana e può limitare l’uso delle API. | Esegui `License license = new License(); license.SetLicense("Aspose.Words.lic");` all’inizio del programma. |
| **Salvataggio in una cartella di sola lettura** | Il metodo `Save` genera un `UnauthorizedAccessException`. | Assicurati che la directory di destinazione abbia permessi di scrittura. |

Affrontare questi problemi fin dall’inizio evita eccezioni a runtime e garantisce un’esperienza fluida nella **modifica del separatore di nota a piè di pagina**.

## Esempio completo e eseguibile

Di seguito trovi un’applicazione console autonoma che dimostra tutti i passaggi discussi. Copia il codice in un nuovo progetto console .NET, sostituisci i percorsi dei file e avvialo.

```csharp
using Aspose.Words;
using System;
using System.Drawing;

namespace FootnoteSeparatorStyler
{
    class Program
    {
        static void Main()
        {
            // OPTIONAL: Apply your Aspose.Words license
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1. Load the source document
            string inputPath = @"C:\Docs\Footnotes.docx";
            Document doc = new Document(inputPath);

            // 2. Retrieve separator nodes
            Node footnoteSeparator = doc.Footnotes.Separator;
            Node footnoteContinuationSep = doc.Footnotes.ContinuationSeparator;
            Node endnoteSeparator = doc.Endnotes.Separator;
            Node endnoteContinuationSep = doc.Endnotes.ContinuationSeparator;

            // 3. Style footnote separator
            if (footnoteSeparator is Paragraph footSepPara)
            {
                footSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footSepPara.Runs.Count > 0)
                    footSepPara.Runs[0].Font.Color = Color.Gray;
            }

            // 3a. (Optional) Style footnote continuation separator
            if (footnoteContinuationSep is Paragraph footContPara)
            {
                footContPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (footContPara.Runs.Count > 0)
                    footContPara.Runs[0].Font.Color = Color.DarkGray;
            }

            // 4. Style endnote separator (optional)
            if (endnoteSeparator is Paragraph endSepPara)
            {
                endSepPara.ParagraphFormat.Alignment = ParagraphAlignment.Center;
                if (endSepPara.Runs.Count > 0)
                    endSepPara.Runs[0].Font.Color = Color.SlateGray;
            }

            // 5. Save the modified document
            string outputPath = @"C:\Docs\Footnotes_Styled.docx";
            doc.Save(outputPath);

            Console.WriteLine("Footnote separator formatted successfully.");
            Console.WriteLine($"Saved to: {outputPath}");
        }
    }
}
```

**Risultato atteso**  

Quando apri `Footnotes_Styled.docx`:

* La linea del separatore di nota a piè di pagina è centrata sotto il testo principale.
* Il suo colore è un grigio chiaro, rendendolo visivamente distinto.
* Se il documento contiene note finali, anche i loro separatori sono centrati e colorati in grigio (o ardesia).

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Words Processing with Footnote and Endnote](/words/english/net/working-with-footnote-and-endnote/)
- [Set Footnote And Endnote Position](/words/english/net/working-with-footnote-and-endnote/set-footnote-and-end-note-position/)
- [Working With Footnote And Endnote](/words/german/net/working-with-footnote-and-endnote/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}