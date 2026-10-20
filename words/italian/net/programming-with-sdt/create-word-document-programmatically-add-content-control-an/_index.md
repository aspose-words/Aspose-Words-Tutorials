---
category: general
date: 2026-08-04
description: Crea un documento Word programmaticamente usando C#. Scopri come aggiungere
  un controllo di contenuto a Word e impostare il testo segnaposto per modelli dinamici.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document programmatically
- add content control to word
- set placeholder text word
- Aspose.Words content control
- dynamic Word template C#
language: it
lastmod: 2026-08-04
og_description: Crea un documento Word programmaticamente con C#. Questa guida mostra
  come aggiungere un controllo di contenuto a Word e impostare il testo segnaposto
  per modelli riutilizzabili.
og_image_alt: Screenshot of a Word document with a highlighted content control placeholder
og_title: Crea un documento Word programmaticamente – aggiungi controllo del contenuto
  e segnaposto
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create word document programmatically using C#. Learn how to add content
    control to word and set placeholder text word for dynamic templates.
  headline: Create word document programmatically – add content control and placeholder
  type: TechArticle
tags:
- C#
- Aspose.Words
- Word automation
title: Crea documento Word programmaticamente – aggiungi controllo del contenuto e
  segnaposto
url: /it/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word programmaticamente – aggiungi controllo contenuto e segnaposto

Se hai bisogno di **creare documenti Word programmaticamente**, questo tutorial ti mostra una soluzione completa, pronta all'uso. Vedrai come **aggiungere un controllo contenuto a Word**, assegnargli un titolo significativo e **impostare il testo segnaposto in Word** così gli utenti finali potranno inserire i dati in seguito.

La guida analizza ogni riga di codice, spiega perché ogni passaggio è importante e mette in evidenza le insidie comuni. Alla fine avrai un file .docx riutilizzabile che può fungere da modello per fatture, contratti o qualsiasi documento basato su moduli.

## Prerequisiti

* .NET 6.0 (o successivo) installato – il codice utilizza le ultime funzionalità del linguaggio C#.
* Una licenza Aspose.Words per .NET (la versione di prova gratuita funziona per lo sviluppo).
* Visual Studio 2022 o qualsiasi IDE in grado di compilare progetti .NET.
* Familiarità di base con C# e il concetto di Structured Document Tags (SDT).

> **Consiglio:** Se esegui il campione senza licenza, Aspose.Words aggiunge una piccola filigrana al file salvato. Applica la tua licenza all'inizio del programma per evitarla.

## Passo 1: Configura il progetto e importa i namespace

Crea un nuovo progetto console e aggiungi il pacchetto NuGet Aspose.Words.

```bash
dotnet new console -n WordTemplateDemo
cd WordTemplateDemo
dotnet add package Aspose.Words
```

Ora importa i namespace richiesti in `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
```

Questi namespace ti danno accesso alle classi `Document`, `DocumentBuilder` e `StructuredDocumentTag`, essenziali per **creare documenti Word programmaticamente**.

## Passo 2: Inizializza un documento vuoto e un builder

La classe `Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` ti consente di posizionare contenuti in una posizione specifica del cursore.

```csharp
// Step 2: Create an empty Word document
Document document = new Document();

// Step 2b: Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché è importante*: Iniziare con un `Document` vuoto garantisce il pieno controllo su ogni elemento inserito. Il `DocumentBuilder` mantiene un cursore interno, così puoi inserire nodi esattamente dove ti serve.

## Passo 3: Crea un Structured Document Tag (SDT) di testo semplice

Uno Structured Document Tag è il nome tecnico per un **controllo contenuto** in Word. Creeremo un tag di testo semplice inline che si comporta come un campo segnaposto.

```csharp
// Step 3: Create a plain‑text Structured Document Tag (content control)
StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
    document,
    StructuredDocumentTagType.PlainText,   // plain‑text content control
    MarkupLevel.Inline);                    // appears inside a paragraph
```

*Perché è importante*: L'utilizzo di `StructuredDocumentTagType.PlainText` indica a Word che il controllo accetterà solo testo semplice. `MarkupLevel.Inline` fa sì che il controllo si comporti come una parola normale all'interno di un paragrafo, ideale per i campi modulo.

## Passo 4: Assegna un titolo e un testo segnaposto

Il **titolo** è l'identificatore interno che la tua applicazione può interrogare in seguito. Il **segnaposto** è il suggerimento in grigio mostrato all'utente prima che inizi a digitare.

```csharp
// Step 4: Set a title and placeholder text for the content control
plainTextTag.Title = "CustomerName";          // internal name used by code
plainTextTag.PlaceholderName = "Enter name here"; // visible hint in the UI
```

Qui **impostiamo il testo segnaposto in Word** a “Enter name here”. Quando il documento viene aperto in Microsoft Word, il segnaposto appare in grigio chiaro finché l'utente non inserisce un valore.

## Passo 5: Inserisci il controllo contenuto nella posizione corrente del cursore

`DocumentBuilder.InsertNode` posiziona l'SDT esattamente dove si trova il cursore del builder. Per impostazione predefinita, il cursore è all'inizio del primo paragrafo.

```csharp
// Step 5: Insert the content control into the document at the builder's current position
builder.InsertNode(plainTextTag);
```

Se hai bisogno del controllo all'interno di un paragrafo specifico, sposta prima il cursore:

```csharp
builder.Writeln("Please provide the customer name:");
builder.InsertNode(plainTextTag);
```

Questo esempio dimostra come **aggiungere un controllo contenuto a Word** preservando il testo circostante.

## Passo 6: Salva il documento

Infine, salva il file su disco. Puoi scegliere qualsiasi cartella; assicurati solo che l'applicazione abbia i permessi di scrittura.

```csharp
// Step 6: Save the document with the content control
string outputPath = @"YOUR_DIRECTORY\SDT.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri `SDT.docx` in Microsoft Word, vedrai il segnaposto “Enter name here” all'interno di una casella grigio chiaro. Gli utenti possono fare clic sulla casella e sostituire il suggerimento con il nome reale del cliente.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire senza modifiche (ad eccezione del percorso di output).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

class Program
{
    static void Main()
    {
        // Optional: apply your Aspose.Words license here
        // var license = new License();
        // license.SetLicense("Aspose.Words.lic");

        // 1. Create a new empty document
        Document document = new Document();

        // 2. Initialize a DocumentBuilder for editing the document
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3. Write a brief instruction line (optional)
        builder.Writeln("Please enter the customer's name below:");

        // 4. Create a plain‑text Structured Document Tag (content control)
        StructuredDocumentTag plainTextTag = new StructuredDocumentTag(
            document,
            StructuredDocumentTagType.PlainText,
            MarkupLevel.Inline);

        // 5. Set a title and placeholder text for the content control
        plainTextTag.Title = "CustomerName";
        plainTextTag.PlaceholderName = "Enter name here";

        // 6. Insert the content control at the current cursor position
        builder.InsertNode(plainTextTag);

        // 7. Save the document
        string outputPath = @"C:\Temp\SDT.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output previsto** – Quando esegui il programma, la console stampa il percorso del file e il file Word generato contiene una singola riga di testo seguita da un segnaposto grigio che recita “Enter name here”.

## Variazioni comuni e casi limite

| Scenario | Come adattare il codice |
|----------|-----------------------|
| **Multi‑line placeholder** | Usa `StructuredDocumentTagType.RichText` al posto di `PlainText` e imposta `plainTextTag.MultipleLines = true;`. |
| **Repeating the same control** | Clona il tag con `plainTextTag.Clone(true)` e inserisci il clone dove necessario. |
| **Binding to data source** | Dopo che l'utente ha compilato il documento, recupera il valore con `document.GetChildNodes(NodeType.StructuredDocumentTag, true).Cast<StructuredDocumentTag>().First(t => t.Title == "CustomerName").GetText();`. |
| **Locking the control** | Imposta `plainTextTag.LockContentControl = true;` per impedire agli utenti di eliminare il controllo. |
| **Changing placeholder color** | Word non espone lo stile del segnaposto tramite l'SDK; è necessario modificare manualmente il modello o usare una macro Word. |

## Best practice e risoluzione dei problemi

* **Imposta sempre un titolo** – Senza un titolo, trovare il controllo in seguito diventa difficile.
* **Evita segnaposti vuoti** – Word nasconde un segnaposto vuoto se la proprietà `ShowPlaceholderText` del controllo è false. Mantienila true per una migliore esperienza utente.
* **Convalida il percorso di output** – Se `document.Save` genera un `UnauthorizedAccessException`, verifica che la cartella esista e che il tuo processo abbia i permessi di scrittura.
* **Licenza precoce** – Inserisci il codice della licenza prima che vengano istanziati gli oggetti Aspose.Words per evitare la filigrana di prova.

## Conclusione

Ora sai come **creare documenti Word programmaticamente**, **aggiungere un controllo contenuto a Word** e **impostare il testo segnaposto in Word** usando Aspose.Words per .NET. L'esempio completo dimostra ogni passaggio necessario, dall'inizializzazione del documento alla persistenza di un modello che gli utenti finali possono compilare.

Successivamente, potresti esplorare:

* Aggiungere **controlli contenuto ripetibili** per tabelle (parola chiave secondaria: add content control to word).
* Popolare i segnaposti con dati provenienti da un database (parola chiave secondaria: set placeholder text word).
* Convertire il .docx generato in PDF o HTML per l'elaborazione successiva.

Sentiti libero di sperimentare con diversi tipi di tag, stili e tecniche di binding dei dati. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea nuovo documento Word](/words/english/net/add-content-using-documentbuilder/create-new-document/)
- [Crea documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Crea un documento Word con tabella usando Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}