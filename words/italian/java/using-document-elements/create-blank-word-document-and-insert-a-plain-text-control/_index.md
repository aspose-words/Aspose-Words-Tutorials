---
category: general
date: 2026-09-18
description: Crea un documento Word vuoto usando C# e imposta il testo segnaposto,
  quindi salva il documento come docx. Impara a inserire un controllo di testo semplice
  e aggiungere il nome del segnaposto.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set placeholder text
- save document as docx
- insert plain text control
- add placeholder name
language: it
lastmod: 2026-09-18
og_description: Crea un documento Word vuoto usando C#. Imposta il testo segnaposto,
  inserisci un controllo di testo semplice, aggiungi il nome del segnaposto e salva
  il documento come docx.
og_image_alt: Screenshot of a Word document showing a plain‑text content control with
  placeholder text
og_title: Crea un documento Word vuoto con testo segnaposto – Guida C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  headline: Create blank Word document and insert a plain‑text control
  type: TechArticle
- description: Create blank Word document using C# and set placeholder text, then
    save document as docx. Learn to insert plain text control and add placeholder
    name.
  name: Create blank Word document and insert a plain‑text control
  steps:
  - name: An empty Word file (the **blank Word document** you created)
    text: An empty Word file (the **blank Word document** you created)
  - name: A plain‑text content control (the **insert plain text control** step)
    text: A plain‑text content control (the **insert plain text control** step)
  - name: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
    text: Placeholder text that appears inside the control until the user types something
      (the **set placeholder text** step)
  - name: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
    text: A placeholder name that can be used for programmatic access later (the **add
      placeholder name** step)
  - name: A line of regular text after the control, demonstrating that normal content
      can follow
    text: A line of regular text after the control, demonstrating that normal content
      can follow
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crea un documento Word vuoto e inserisci un controllo di testo semplice
url: /it/java/using-document-elements/create-blank-word-document-and-insert-a-plain-text-control/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e inserisci un controllo di testo semplice

Se hai bisogno di **creare un documento Word vuoto** programmaticamente, questa guida ti mostra come farlo con C#. Imparerai a **inserire un controllo di testo semplice**, **impostare il testo segnaposto**, **aggiungere un nome segnaposto** e infine **salvare il documento come docx**. I passaggi sono completamente autonomi, quindi puoi copiare il codice in qualsiasi progetto .NET e eseguirlo subito.

Lavorare con i file Word spesso richiede un punto di partenza pulito: un documento vuoto che contiene già i controlli che gli utenti dovranno compilare. Alla fine di questo tutorial avrai un file `.docx` che contiene un controllo di contenuto di testo semplice con un utile segnaposto, seguito da contenuto normale.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+)
- Un riferimento alla libreria **Aspose.Words for .NET** (disponibile via NuGet `Install-Package Aspose.Words`)
- Familiarità di base con le applicazioni console C#
- Permessi di scrittura sulla cartella di output che specifichi in `doc.save(...)`

## Cosa costruirai

Il documento finale (`SDT.docx`) contiene:

1. Un file Word vuoto (il **documento Word vuoto** che hai creato)
2. Un controllo di contenuto di testo semplice (il passaggio **inserisci controllo di testo semplice**)
3. Testo segnaposto che appare all'interno del controllo finché l'utente non digita qualcosa (il passaggio **imposta testo segnaposto**)
4. Un nome segnaposto che può essere usato per l'accesso programmatico successivo (il passaggio **aggiungi nome segnaposto**)
5. Una riga di testo normale dopo il controllo, a dimostrazione che il contenuto standard può seguirlo

## Passo 1: Crea un documento Word vuoto

La prima operazione è istanziare un oggetto `Document` vuoto. Questo oggetto rappresenta un **documento Word vuoto** completamente nuovo in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

// Step 1: Create a new blank document
Document doc = new Document();
```

*Perché è importante:* Un `Document` vuoto ti dà il pieno controllo su ogni elemento che aggiungi, assicurando che nessuno stile o sezione nascosta interferisca con il controllo di contenuto che inserirai in seguito.

## Passo 2: Inizializza un DocumentBuilder

`DocumentBuilder` è la classe di supporto che ti permette di scrivere nel `Document`. Tiene traccia della posizione corrente del cursore e fornisce metodi per inserire tutti i tipi di oggetti Word.

```csharp
// Step 2: Initialize a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante:* Usare un `DocumentBuilder` semplifica il processo di aggiunta di un **controllo di testo semplice** perché il builder conosce il punto di inserimento esatto.

## Passo 3: Inserisci il controllo di testo semplice

Ora aggiungiamo un **controllo di contenuto di testo semplice** (noto anche come Structured Document Tag, o SDT). Il tipo di controllo `StructuredDocumentTagType.PLAIN_TEXT` indica a Word di trattare il contenuto come testo semplice, non formattato.

```csharp
// Step 3: Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    StructuredDocumentTagType.PlainText, "MyTag");
```

*Perché è importante:* Il metodo `InsertStructuredDocumentTag` crea il controllo e restituisce un riferimento (`sdt`) che puoi configurare ulteriormente, ad esempio aggiungendo testo segnaposto o un nome personalizzato.

## Passo 4: Imposta il testo segnaposto e aggiungi il nome segnaposto

Il testo segnaposto fornisce agli utenti un'indicazione visiva su cosa digitare. Il passaggio **aggiungi nome segnaposto** assegna un identificatore programmatico che potrai interrogare in seguito con `doc.GetChildNodes` o API simili.

```csharp
// Step 4a: Set a placeholder text that appears when the SDT is empty
sdt.SetPlaceholderName("Enter text…");

// Step 4b: Add a placeholder name (tag ID) for later retrieval
sdt.Tag = "MyTag";
```

*Perché è importante:* `SetPlaceholderName` controlla il testo grigio mostrato all'interno del controllo di contenuto. Impostare `Tag` (l'azione **aggiungi nome segnaposto**) ti permette di individuare il controllo nell'albero del documento senza dover scansionare l'intero file.

## Passo 5: Aggiungi contenuto normale dopo il controllo

Per dimostrare che il documento continua normalmente dopo il controllo, scriviamo una semplice riga di testo.

```csharp
// Step 5: Add regular content after the SDT
builder.Writeln("After the tag.");
```

## Passo 6: Salva il documento come docx

Infine, persisti il documento in memoria su disco. Questa è l'operazione **salva documento come docx** che produce il file apribile con Microsoft Word.

```csharp
// Step 6: Save the document as a .docx file
string outputPath = @"YOUR_DIRECTORY/SDT.docx";
doc.Save(outputPath);
```

*Perché è importante:* Usare il formato `.docx` garantisce la massima compatibilità con le versioni moderne di Word, Google Docs e altri strumenti compatibili con Office.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare in un progetto console‑app. Sostituisci `YOUR_DIRECTORY` con un percorso di cartella reale sul tuo computer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.BuildingBlocks;

namespace WordSdtExample
{
    class Program
    {
        static void Main()
        {
            // Create a new blank Word document
            Document doc = new Document();

            // Initialize a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag ID
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");

            // Set a placeholder text that appears when the SDT is empty
            sdt.SetPlaceholderName("Enter text…");

            // Add a placeholder name (tag) for later retrieval
            sdt.Tag = "MyTag";

            // Add regular content after the SDT
            builder.Writeln("After the tag.");

            // Save the document as a .docx file
            string outputPath = @"C:\Temp\SDT.docx"; // change to your folder
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Risultato atteso

- Aprendo `SDT.docx` in Word vedrai una casella grigia vuota con il testo **Enter text…** al suo interno.
- La casella è un controllo di contenuto di testo semplice; puoi digitare direttamente al suo interno.
- Sotto la casella, la riga **After the tag.** appare come testo di paragrafo normale.

Se il segnaposto non compare, verifica di stare usando una versione recente di Aspose.Words (v23.1 o successiva) e che il documento sia aperto in una versione di Word che supporta i controlli di contenuto (Word 2007+).

## Varianti comuni e casi particolari

| Scenario | Come adattare il codice |
|----------|--------------------------|
| **Più segnaposti** | Chiama nuovamente `InsertStructuredDocumentTag` con un ID tag diverso e un nome segnaposto differente. |
| **Controllo rich‑text** | Usa `StructuredDocumentTagType.RichText` al posto di `PlainText`. |
| **Impostare testo predefinito** | Dopo l'inserimento, assegna `sdt.Text = "Default value";` – questo testo sostituisce il segnaposto quando il documento viene caricato. |
| **Salvare su stream** | Sostituisci `doc.Save(outputPath);` con `doc.Save(stream, SaveFormat.Docx);` per inviare il file via HTTP. |
| **Cambiare colore del segnaposto** | Usa `sdt.PlaceholderTextColor = System.Drawing.Color.Gray;` (richiede `using System.Drawing`). |

## Consigli professionali

- **Riutilizza l'ID tag**: mantenere il tag (`MyTag`) coerente tra i documenti ti consente di automatizzare il popolamento dei dati in seguito con `doc.Range.Replace` o la `StructuredDocumentTagCollection`.
- **Evita percorsi hard‑coded**: usa `Path.Combine(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments), "SDT.docx")` per una destinazione di output portabile.
- **Prestazioni**: se devi generare migliaia di documenti, crea un unico modello `Document` con lo SDT già presente, poi clonalo con `doc.Clone()` per ogni iterazione.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **inserire un controllo di testo semplice**, **impostare il testo segnaposto**, **aggiungere un nome segnaposto** e **salvare il documento come docx** usando Aspose.Words per .NET. Questo modello costituisce la base per costruire modelli Word compilabili, report automatizzati o qualsiasi soluzione che richieda segnaposti modificabili dall'utente.

Sentiti libero di sperimentare con altri tipi di controllo, combinare più segnaposti o integrare questo codice in una Web API che restituisce direttamente il file `.docx` generato agli chiamanti. Come passo successivo, esplora **popolare un controllo di contenuto con dati programmaticamente** o **convertire il file Word generato in PDF** usando le funzionalità di conversione integrate di Aspose.Words. Buon coding!

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Insert Text Input Form Field In Word Document](/words/english/net/add-content-using-documentbuilder/insert-text-input-form-field/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)
- [Create Word Document with Header and Footer Using Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}