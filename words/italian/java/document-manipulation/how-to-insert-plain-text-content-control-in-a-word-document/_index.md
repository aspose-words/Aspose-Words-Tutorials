---
category: general
date: 2026-10-26
description: Impara a inserire un controllo di contenuto di testo semplice usando
  Aspose.Words in C#. Guida passo‑passo che copre StructuredDocumentTag, i titoli
  e gli ID dei tag.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert plain text content control
- structured document tag
- Aspose.Words DocumentBuilder
- C# content control
- SDT appearance
language: it
lastmod: 2026-10-26
og_description: Inserisci un controllo di contenuto di testo semplice usando Aspose.Words
  in C#. Segui questa guida per aggiungere titoli, ID tag e personalizzare l'aspetto.
og_image_alt: Screenshot of a Word document showing an inserted plain text content
  control
og_title: Inserisci un controllo contenuto di testo semplice in Word con C# – guida
  completa
schemas:
- author: Aspose
  dateModified: '2026-10-26'
  description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  headline: How to insert plain text content control in a Word document with C#
  type: TechArticle
- description: Learn to insert plain text content control using Aspose.Words in C#.
    Step‑by‑step guide covering StructuredDocumentTag, titles, and tag IDs.
  name: How to insert plain text content control in a Word document with C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Markup;'
  - name: Insert the plain‑text content control (SDT)
    text: '```csharp // Insert a plain‑text Structured Document Tag (SDT) with the
      default appearance. StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
      SdtType.PlainText, // The control type – plain text. SdtAppearance.Default);
      // Visual style; Default shows a light gray shading. ```'
  - name: Set a title and a tag identifier
    text: '```csharp // Give the SDT a friendly title that appears in the Content
      Controls pane. sdt.Title = "MyTag";'
  - name: Variations you might need
    text: '| Scenario | Code change | |----------|-------------| | **No visual shading**
      (border‑less) | Use `SdtAppearance.Hidden` instead of `Default`. | | **Read‑only
      field** | After insertion, set `sdt.LockContentControl = true`. | | **Pre‑populate
      with data** | Set `sdt.Text = "John Doe";` after creating '
  - name: What’s next?
    text: '- Explore other SDT types such as `RichText` or `ComboBox` for dropdowns.
      - Combine multiple content controls inside tables or repeat them using `RepeatingSection`.
      - Use `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` to read or modify
      control values programmatically.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Come inserire un controllo di contenuto di testo semplice in un documento Word
  con C#
url: /it/java/document-manipulation/how-to-insert-plain-text-content-control-in-a-word-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire un controllo di contenuto di testo semplice in un documento Word con C#

Se hai bisogno di **inserire un controllo di contenuto di testo semplice** in un file Word, questo tutorial ti mostra esattamente come farlo usando Aspose.Words per .NET. Che tu stia creando un servizio di generazione di documenti o automatizzando la creazione di moduli, i passaggi seguenti ti consentono di aggiungere un'area riutilizzabile e modificabile che gli utenti finali possono compilare.

Imparerai a creare un `Document`, usare `DocumentBuilder` per posizionare un Structured Document Tag (SDT) di tipo plain‑text, impostare un titolo descrittivo e assegnare un identificatore di tag univoco. La guida spiega anche le variazioni più comuni — come modificare l’aspetto o annidare i controlli — così da poter adattare la soluzione a qualsiasi progetto.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
- Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione gratuita)
- Visual Studio 2022 o qualsiasi IDE compatibile con C#
- Familiarità di base con la sintassi C#

> **Consiglio professionale:** Se utilizzi la versione di valutazione gratuita, ricorda che il documento di output conterrà una filigrana. Una versione con licenza la rimuove automaticamente.

## Come inserire un controllo di contenuto di testo semplice usando Aspose.Words

Il cuore della soluzione è un processo in tre passaggi:

1. **Creare un `Document` e un `DocumentBuilder`.**  
2. **Inserire un Structured Document Tag (SDT) di tipo plain‑text con aspetto predefinito.**  
3. **Assegnare un titolo e un identificatore di tag allo SDT.**  

Ogni passaggio è spiegato di seguito, con codice completo e pronto all’esecuzione.

### Passo 1: Inizializzare il documento e il builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Create a new empty document.
        Document doc = new Document();

        // DocumentBuilder lets you insert content into the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta l’intero file Word, mentre `DocumentBuilder` fornisce metodi come `InsertParagraph`, `InsertImage` e, per questo tutorial, `InsertStructuredDocumentTag`. Inizializzarli per primi ti dà una tela su cui posizionare il **controllo di contenuto di testo semplice**.

### Passo 2: Inserire il controllo di contenuto di testo semplice (SDT)

```csharp
        // Insert a plain‑text Structured Document Tag (SDT) with the default appearance.
        StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
            SdtType.PlainText,          // The control type – plain text.
            SdtAppearance.Default);    // Visual style; Default shows a light gray shading.
```

`SdtType.PlainText` indica ad Aspose.Words di creare un **controllo di contenuto di testo semplice**, che si comporta come una casella di testo che gli utenti possono modificare. `SdtAppearance.Default` rende il controllo con uno sfondo delicato, rendendo evidente nel documento che l’area è modificabile.

> **Perché usare `SdtAppearance.Default`?**  
> L’aspetto predefinito è lo stile più universalmente compatibile tra le versioni di Word. Se desideri un aspetto senza bordi, puoi passare a `SdtAppearance.Hidden` in seguito.

### Passo 3: Impostare un titolo e un identificatore di tag

```csharp
        // Give the SDT a friendly title that appears in the Content Controls pane.
        sdt.Title = "MyTag";

        // Assign a unique tag identifier; this is useful for programmatic access later.
        sdt.Tag = "TagId";

        // (Optional) Add placeholder text inside the control.
        sdt.PlaceholderName = "Enter your text here";

        // Save the document to verify the result.
        doc.Save("output.docx");
    }
}
```

- **Title** (`sdt.Title`) appare nel riquadro *Content Controls* di Word, aiutando gli utenti a capire lo scopo del campo.  
- **Tag** (`sdt.Tag`) è un identificatore orientato allo sviluppatore che puoi interrogare successivamente tramite `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.  
- **PlaceholderName** fornisce un testo guida in grigio, migliorando l’esperienza dell’utente.

Il frammento di codice completo sopra forma un programma autonomo che puoi compilare ed eseguire. Dopo l’esecuzione, `output.docx` conterrà un unico controllo di contenuto di testo semplice con il titolo *MyTag* e il tag *TagId*.

![Diagramma che mostra l'inserimento di un controllo di contenuto di testo semplice in un documento Word](image.png){alt="inserire controllo di contenuto di testo semplice"}

## Comprendere StructuredDocumentTag (SDT) e le sue proprietà

Un **Structured Document Tag** (SDT) è il modello di oggetto sottostante ai controlli di contenuto di Word. Le proprietà più rilevanti per inserire un controllo di testo semplice sono:

| Property | Scopo | Valori tipici |
|----------|-------|---------------|
| `SdtType` | Determina il tipo di controllo (plain text, rich text, picture, ecc.) | `PlainText`, `RichText`, `ComboBox`, `DatePicker` |
| `SdtAppearance` | Stile visuale del controllo | `Default`, `Hidden`, `BoundingBox`, `Tags` |
| `Title` | Nome leggibile mostrato nel riquadro *Content Controls* | Qualsiasi stringa breve |
| `Tag` | Identificatore leggibile dalla macchina usato nel codice | Stringa alfanumerica |
| `PlaceholderName` | Testo visualizzato quando il controllo è vuoto | Testo di suggerimento personalizzato |

Quando imposti `SdtType.PlainText`, Word limita il contenuto a caratteri semplici, impedendo formattazioni ricche. Questo rende il controllo ideale per campi di modulo semplici come *Nome*, *Email* o *Numero di telefono*.

### Variazioni che potresti necessitare

| Scenario | Modifica al codice |
|----------|--------------------|
| **Nessuna sfumatura visiva** (senza bordi) | Usa `SdtAppearance.Hidden` invece di `Default`. |
| **Campo di sola lettura** | Dopo l’inserimento, imposta `sdt.LockContentControl = true`. |
| **Pre‑popolare con dati** | Imposta `sdt.Text = "John Doe";` dopo aver creato il tag. |
| **Controlli multipli in una tabella** | Inserisci lo SDT all’interno di una cella di tabella usando `builder.InsertCell();` prima della chiamata `InsertStructuredDocumentTag`. |

## Problemi comuni e come evitarli

1. **Dimenticare di impostare un titolo** – Word creerà comunque il controllo, ma gli utenti non vedranno una descrizione significativa nel riquadro *Content Controls*. Assegna sempre `sdt.Title`.  
2. **Usare il `SdtType` sbagliato** – Se ti serve testo semplice ma scegli accidentalmente `RichText`, il controllo consentirà formattazioni, il che potrebbe rompere l’elaborazione successiva. Controlla il valore dell’enumerazione.  
3. **Salvare in una cartella di sola lettura** – La chiamata `doc.Save` genererà un’`UnauthorizedAccessException`. Assicurati che la directory di destinazione sia scrivibile o usa `Path.GetTempPath()` per i test.  
4. **Licenza non applicata** – Senza una licenza valida, il documento di output contiene una filigrana di valutazione. Applica la licenza all’inizio del programma:  

```csharp
License lic = new License();
lic.SetLicense("Aspose.Words.lic");
```

## Esempio completo, eseguibile

Di seguito trovi l’intero programma, pronto per essere copiato e incollato in un nuovo progetto console.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace InsertPlainTextContentControl
{
    class Program
    {
        static void Main()
        {
            // Apply license (optional for evaluation)
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // 1️⃣ Create a new document and a builder to edit it
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert a plain‑text Structured Document Tag (SDT) with default appearance
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText,          // Plain text control
                SdtAppearance.Default);    // Light gray shading

            // 3️⃣ Assign a title and a tag identifier to the SDT
            sdt.Title = "MyTag";          // Human‑readable title
            sdt.Tag = "TagId";            // Unique machine identifier
            sdt.PlaceholderName = "Enter your text here";

            // (Optional) Add some introductory text before the control
            builder.MoveToDocumentStart();
            builder.Writeln("Please fill in the following field:");

            // 4️⃣ Save the document
            string outputPath = "output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output previsto:** Aprendo `output.docx` in Microsoft Word vedrai una riga di testo *“Please fill in the following field:”* seguita da un’area delimitata in grigio chiaro etichettata *MyTag*. Il segnaposto *Enter your text here* appare in grigio chiaro finché l’utente non digita.

## Conclusione

Ora sai come **inserire un controllo di contenuto di testo semplice** in un documento Word usando Aspose.Words per .NET. Il tutorial ha coperto l’inizializzazione di un `Document`, l’inserimento di uno `StructuredDocumentTag` di tipo `PlainText` e la personalizzazione di titolo, tag e segnaposto. Comprendendo le opzioni di `SdtAppearance` e i problemi più comuni, potrai creare con fiducia moduli, modelli e report automatizzati che si basano su controlli di contenuto modificabili.

### Cosa fare dopo?

- Esplora altri tipi di SDT come `RichText` o `ComboBox` per menu a discesa.  
- Combina più controlli di contenuto all’interno di tabelle o ripetili usando `RepeatingSection`.  
- Usa `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` per leggere o modificare i valori dei controlli programmaticamente.

Sperimenta con le variazioni illustrate in precedenza e integra il modello nei tuoi flussi di generazione di documenti più ampi. Buon coding!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Come creare un controllo di contenuto in C# con Aspose.Words](/words/english/net/programming-with-sdt/how-to-create-content-control-in-c-with-aspose-words/)
- [Creare un nuovo documento Word e inserire un controllo di contenuto in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)
- [Aggiungere contenuto usando Document Builder in Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}