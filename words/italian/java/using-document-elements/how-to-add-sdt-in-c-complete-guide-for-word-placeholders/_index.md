---
category: general
date: 2026-08-14
description: Come aggiungere rapidamente SDT con Aspose.Words. Impara a creare un
  segnaposto Word e inserire un controllo di testo semplice in un file .docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to add sdt
- create word placeholder
- insert plain text control
- Aspose.Words SDT
- C# Word automation
language: it
lastmod: 2026-08-14
og_description: Come aggiungere SDT in C# usando Aspose.Words. Segui questo tutorial
  per creare un segnaposto Word e inserire un controllo di testo semplice per documenti
  dinamici.
og_image_alt: Screenshot of a Word document showing a plain‑text Structured Document
  Tag placeholder
og_title: Come aggiungere SDT in C# – guida passo‑passo ai segnaposto di Word
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to add SDT quickly with Aspose.Words. Learn to create word placeholder
    and insert plain text control in a .docx file.
  headline: How to add SDT in C# – complete guide for Word placeholders
  type: TechArticle
tags:
- Word
- C#
- Aspose.Words
- SDT
- Document Automation
title: Come aggiungere SDT in C# – guida completa per i segnaposto di Word
url: /it/java/using-document-elements/how-to-add-sdt-in-c-complete-guide-for-word-placeholders/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere SDT in C# – guida completa per i segnaposto Word

Se hai bisogno di **how to add sdt** in un file Word, questo tutorial ti mostra i passaggi esatti usando Aspose.Words per .NET. Alla fine della guida sarai in grado di **create word placeholder** tag che consentono agli utenti finali di digitare direttamente in un documento, e comprenderai come **insert plain text control** in modo affidabile.

Lavorare con i Structured Document Tags (SDT) elimina la necessità di campi modulo manuali e ti offre un modo pulito e programmatico per creare contratti, report o lettere dinamiche. L'esempio qui sotto copre tutto, dalla configurazione del progetto al salvataggio del file .docx finale, così puoi copiare‑incollare il codice nella tua soluzione senza perdere alcuna dipendenza.

## Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.6+)
- Visual Studio 2022 o qualsiasi IDE C# tu preferisca
- Una licenza Aspose.Words per .NET (una licenza temporanea gratuita funziona per i test)
- Familiarità di base con la sintassi C# e il concetto di SDT

> **Consiglio professionale:** Se prevedi di distribuire i documenti generati, incorpora un file di licenza per evitare la filigrana di valutazione.

## Passo 1: Configura il progetto e importa Aspose.Words

Crea una nuova applicazione console e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet new console -n SdtDemo
cd SdtDemo
dotnet add package Aspose.Words
```

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Queste direttive `using` ti danno accesso alle classi `Document`, `DocumentBuilder` e `StructuredDocumentTag` necessarie per le operazioni di **insert plain text control**.

## Passo 2: Inizializza il documento e il builder

Il primo blocco di codice crea un documento Word vuoto e un `DocumentBuilder` che ti permette di scrivere contenuti al suo interno.

```csharp
// Step 2: Create a new document and a builder to edit it
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

`DocumentBuilder` funziona come un cursore; ogni chiamata successiva aggiunge contenuto nella posizione corrente. Inizializzare il documento è la base per ogni scenario **how to add sdt** perché l'SDT deve appartenere a un'istanza `Document` attiva.

## Passo 3: Inserisci un Structured Document Tag (SDT) di testo semplice

Ora **insert plain text control** che funge da segnaposto dove un utente può digitare un nome, una data o qualsiasi valore personalizzato.

```csharp
// Step 3: Insert a plain‑text Structured Document Tag (SDT)
StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
        StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);
```

- `StructuredDocumentTagType.PlainText` indica ad Aspose.Words di creare un campo di testo semplice.
- `SdtAppearanceTags.Default` assegna al tag lo stile visivo standard di Word (una casella ombreggiata quando il documento viene aperto in Word).

## Passo 4: Configura l'SDT con un titolo e testo segnaposto

Un SDT con un nome chiaro rende il documento auto‑esplicativo per gli utenti finali. Qui **create word placeholder** i metadati e impostiamo il suggerimento che appare all'interno del campo.

```csharp
// Step 4: Give the SDT a meaningful title and placeholder text
plainTextTag.Title = "CustomerName";
plainTextTag.PlaceholderName = "Enter name here";
```

- `Title` è l'identificatore interno che potrai usare in seguito per estrarre o aggiornare il valore programmaticamente.
- `PlaceholderName` è il suggerimento in grigio mostrato in Word, che indica all'utente cosa digitare.

## Passo 5: Aggiungi contenuto circostante

Un documento raramente consiste di un singolo SDT. Di solito hai bisogno di paragrafi regolari prima e dopo il segnaposto. Usa il metodo `WriteLine` del builder per aggiungere testo statico.

```csharp
// Step 5: Add regular content before and after the SDT
builder.Writeln("Dear ");
builder.InsertNode(plainTextTag);   // Re‑insert the tag at the current cursor position
builder.Writeln(",");
builder.Writeln("After the SDT");
```

La chiamata a `InsertNode` posiziona l'SDT creato in precedenza esattamente dove ti serve, preservando il flusso di testo circostante.

## Passo 6: Salva il documento in un file .docx

Infine, salva il documento su disco. Il percorso può essere assoluto o relativo alla cartella del progetto.

```csharp
// Step 6: Save the document to a file
string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Aprendo `SDT.docx` in Microsoft Word viene mostrato un segnaposto grigio che recita **Enter name here**. Gli utenti possono cliccare sul campo, digitare un valore, e il documento manterrà quel valore al successivo salvataggio.

## Esempio completo, eseguibile

Unendo tutti i pezzi ottieni un programma autonomo che puoi eseguire immediatamente:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a plain‑text SDT
        StructuredDocumentTag plainTextTag = builder.InsertStructuredDocumentTag(
            StructuredDocumentTagType.PlainText, SdtAppearanceTags.Default);

        // Configure the SDT
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // Add surrounding content
        builder.Writeln("Dear ");
        builder.InsertNode(plainTextTag);
        builder.Writeln(",");
        builder.Writeln("After the SDT");

        // Save the file
        string outputPath = Path.Combine(Environment.CurrentDirectory, "SDT.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output previsto** quando esegui il programma:

```
Document saved to C:\YourProject\bin\Debug\net6.0\SDT.docx
```

Aprendo il `SDT.docx` generato viene mostrato:

```
Dear [Enter name here],
After the SDT
```

Il testo tra parentesi è il segnaposto **insert plain text control** che gli utenti possono sostituire.

## Variazioni comuni e casi limite

| Situazione | Come adattare il codice |
|------------|--------------------------|
| **Segnaposti multipli** | Chiama `InsertStructuredDocumentTag` più volte e assegna a ciascun tag un `Title` unico. |
| **SDT di testo ricco** | Usa `StructuredDocumentTagType.RichText` al posto di `PlainText`. |
| **Blocca il segnaposto** | Imposta `plainTextTag.LockContentControl = true;` per impedire agli utenti di eliminare il campo. |
| **Pre‑popola con un valore** | Assegna `plainTextTag.Text = "John Doe";` prima del salvataggio. |
| **Aspetto condizionale** | Usa `plainTextTag.SdtType = StructuredDocumentTagType.CheckBox;` per un controllo casella di spunta. |

Queste variazioni ti permettono di **create word placeholder** strutture che corrispondono a quasi qualsiasi scenario simile a un modulo.

## Suggerimenti per la risoluzione dei problemi

- **Placeholder non visibile** – Assicurati di aprire il file in Microsoft Word (o in un visualizzatore compatibile). Alcuni editor leggeri nascondono gli SDT.
- **Avviso di licenza** – Se vedi una filigrana di valutazione, verifica che il tuo file di licenza sia caricato correttamente (`License license = new License(); license.SetLicense("Aspose.Words.lic");`).
- **Posizione del cursore errata** – Dopo aver inserito un SDT, il cursore del builder rimane *dopo* il tag. Se devi aggiungere testo *all'interno* del tag, usa `builder.MoveTo(plainTextTag);` prima di scrivere.

## Conclusione

Ora sai **how to add sdt** a un documento Word usando Aspose.Words per .NET, come **create word placeholder** tag, e come **insert plain text control** che gli utenti possono modificare direttamente in Word. L'esempio completo dimostra l'inizializzazione, l'inserimento del tag, la configurazione, il contenuto circostante e il salvataggio—tutto in un unico programma eseguibile.

Successivamente, esplora argomenti correlati come **insert rich text control**, **populate SDTs from a database**, o **convert the final document to PDF**. Tutti questi si basano sugli stessi fondamenti trattati qui, così potrai estendere la tua pipeline di automazione con fiducia.

Buon coding, e sentiti libero di sperimentare diversi tipi di SDT per soddisfare le tue esigenze di automazione dei documenti!

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come creare campi modulo e aggiungere contenuto usando DocumentBuilder in Aspose.Words per Java](/words/english/java/document-manipulation/adding-content-using-documentbuilder/)
- [Come creare intervalli modificabili in documenti di sola lettura usando Aspose.Words per Java](/words/english/java/security-protection/editable-ranges-aspose-words-java/)
- [Aggiungere segnalibri Word con Aspose.Words per Java – Inserire, aggiornare, eliminare](/words/english/java/content-management/aspose-words-java-manage-bookmarks/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}