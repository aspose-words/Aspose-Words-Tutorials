---
category: general
date: 2026-10-13
description: Crea un nuovo documento Word in C# e inserisci un controllo di contenuto
  con testo segnaposto. Scopri come impostare il testo segnaposto e salvare il documento
  Word in modo efficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create new word document
- insert content control
- set placeholder text
- how to create sdt
- save word document c#
language: it
lastmod: 2026-10-13
og_description: Crea un nuovo documento Word in C# con Aspose.Words, inserisci un
  controllo contenuto, imposta il testo segnaposto e salva il documento Word—tutto
  in una singola guida.
og_image_alt: Screenshot of a Word document showing a content control placeholder
og_title: Crea un nuovo documento Word e inserisci un controllo di contenuto in C#
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  headline: Create new Word document and insert content control in C#
  type: TechArticle
- description: Create new Word document in C# and insert a content control with placeholder
    text. Learn how to set placeholder text and save the Word document efficiently.
  name: Create new Word document and insert content control in C#
  steps:
  - name: Run the console app.
    text: Run the console app.
  - name: Open `output.docx` in Microsoft Word.
    text: Open `output.docx` in Microsoft Word.
  - name: Verify that the placeholder text appears inside a gray‑shaded box.
    text: Verify that the placeholder text appears inside a gray‑shaded box.
  - name: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
    text: Click the box, type a name, and save the file. The entered text replaces
      the placeholder.
  type: HowTo
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Crea un nuovo documento Word e inserisci un controllo di contenuto in C#
url: /it/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un nuovo documento Word e inserisci un controllo di contenuto in C#

Se hai bisogno di **creare un nuovo documento Word** programmaticamente, questa guida ti mostra come farlo con Aspose.Words per .NET. Imparerai a **inserire un controllo di contenuto**, assegnare **testo segnaposto**, e infine **salvare il documento Word C#** codice che puoi copiare nel tuo progetto.

Il tutorial percorre ogni passaggio, spiega perché ogni chiamata API è importante e copre variazioni comuni come aggiungere un SDT rich‑text o gestire documenti esistenti. Alla fine avrai un esempio completo e eseguibile che potrai adattare a fatture, contratti o qualsiasi output Word basato su template.

## Prerequisiti

* .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.7+)
* Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)
* Un IDE come Visual Studio 2022 o Visual Studio Code

Non sono richieste librerie aggiuntive.

## Crea un nuovo documento Word con Aspose.Words

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta un file Word vuoto in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Markup;

// Step 1: Create a new, empty document
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` ti fornisce un'API fluida per inserire elementi nella posizione corrente del cursore. Poiché il documento è vuoto, il cursore inizia all'inizio della prima (e unica) sezione.

## Inserisci un controllo di contenuto (StructuredDocumentTag)

Un **controllo di contenuto** in Word è chiamato Structured Document Tag (SDT). Il codice seguente crea un SDT plain‑text, imposta il suo titolo e definisce il testo segnaposto che appare quando l'utente apre il file.

```csharp
// Step 2: Create a plain‑text StructuredDocumentTag (SDT)
StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Title is used for identification in the document outline
    Title = "CustomerName",
    // Placeholder text is visible until the user types a value
    PlaceholderName = "Enter name here"
};

// Step 3: Insert the SDT at the builder's current insertion point
builder.InsertNode(sdt);
```

**Perché è importante:**  
* `SdtType.PlainText` limita il contenuto a una singola riga di testo semplice, ideale per campi semplici come nome o email.  
* Impostare `PlaceholderName` fornisce un'indicazione visiva (`Enter name here`) che guida l'utente finale.

Se ti serve un campo più ricco (ad esempio testo multilinea o un selettore di data), sostituisci `SdtType.PlainText` con `SdtType.RichText` o `SdtType.Date`.

## Aggiungi testo opzionale circostante

La maggior parte dei template include un'etichetta prima del controllo di contenuto. Puoi aggiungerla con la stessa istanza di `DocumentBuilder`:

```csharp
// Optional: add a label before the content control
builder.Writeln("Customer Name:");
builder.InsertNode(sdt);   // Re‑insert the SDT after the label
```

Il file Word risultante mostra:

```
Customer Name: [Enter name here]
```

## Salva il documento Word in stile C#

Infine, scrivi il documento su disco. Aspose.Words determina automaticamente il formato dall'estensione del file.

```csharp
// Step 4: Save the document to verify the result
string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri `output.docx` in Microsoft Word, vedrai il testo segnaposto all'interno di un controllo di contenuto con sfondo grigio. Gli utenti possono fare clic sul controllo e sostituire il segnaposto con il proprio valore.

## Esempio completo e eseguibile

Di seguito trovi un programma console autonomo che mette tutto insieme. Copia il codice in un nuovo progetto console e eseguilo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Add a descriptive label
            builder.Writeln("Customer Name:");

            // Create and configure a plain‑text content control (SDT)
            StructuredDocumentTag sdt = new StructuredDocumentTag(doc, SdtType.PlainText, true)
            {
                Title = "CustomerName",
                PlaceholderName = "Enter name here"
            };

            // Insert the SDT after the label
            builder.InsertNode(sdt);

            // Save the document
            string outputPath = Path.Combine(Environment.CurrentDirectory, "output.docx");
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output previsto** (console):

```
Document saved to C:\YourProject\bin\Debug\net6.0\output.docx
```

Aprendo `output.docx` si vede una singola riga con l'etichetta *Customer Name:* seguita da un controllo di contenuto che visualizza *Enter name here*.

## Variazioni comuni e casi limite

| Scenario | Modifica del codice | Motivo |
|----------|---------------------|--------|
| **Campo rich‑text** | `new StructuredDocumentTag(doc, SdtType.RichText, true)` | Consente input multilinea e formattazione di base. |
| **Controllo di sola lettura** | `sdt.LockContentControl = true;` | Impedisce agli utenti di modificare il contenuto del controllo. |
| **Pre‑popola con dati** | `sdt.AppendChild(new Run(doc, "John Doe"));` | Inserisce un valore predefinito che sovrascrive il segnaposto. |
| **Aggiungi a un documento esistente** | Load with `new Document("template.docx")` instead of an empty `Document` | Abilita scenari di templating in cui il controllo è posizionato in un layout predefinito. |
| **Controlli multipli** | Repeat the creation block with different titles and placeholders | Utile per moduli che raccolgono diverse informazioni. |

### Consiglio professionale

Quando generi documenti di grandi dimensioni, riutilizza una singola istanza di `DocumentBuilder` invece di crearne una nuova per ogni controllo. Questo riduce l'overhead di memoria e migliora le prestazioni.

## Testare il risultato

1. Esegui l'app console.  
2. Apri `output.docx` in Microsoft Word.  
3. Verifica che il testo segnaposto appaia all'interno di una casella con sfondo grigio.  
4. Fai clic sulla casella, digita un nome e salva il file. Il testo inserito sostituisce il segnaposto.

Se il segnaposto non appare, verifica di utilizzare Aspose.Words versione 23.9 o successiva, poiché le versioni precedenti presentavano un bug con `PlaceholderName` su SDT plain‑text.

## Conclusione

Ora sai come **creare un nuovo documento Word**, **inserire un controllo di contenuto**, **impostare il testo segnaposto** e **salvare il documento Word C#** usando Aspose.Words. L'esempio completo dimostra lo schema standard, e la tabella delle variazioni mostra come adattare la soluzione a scenari più ricchi.

Successivamente, potresti esplorare:

* **Insert content control for dates** – usa l'enumerazione `SdtType.Date`.  
* **Populate a template with data** – combina `StructuredDocumentTag` con i campi di stampa unione.  
* **Export to PDF** – chiama `doc.Save("output.pdf")` dopo aver aggiunto i controlli.

Sentiti libero di sperimentare con diversi tipi di SDT, impostazioni di blocco e stili per soddisfare i requisiti del tuo progetto. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea nuovo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Inserisci campo modulo di input testo in documento Word](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Crea documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}