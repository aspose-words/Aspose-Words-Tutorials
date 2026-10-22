---
category: general
date: 2026-09-08
description: Imposta il nome del tag e crea un controllo di contenuto (SDT) in un
  documento Word usando C#. Scopri come aggiungere SDT, scrivere testo nel tag e modificare
  il documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set tag name
- how to add sdt
- modify word document
- create content control
- write text to tag
language: it
lastmod: 2026-09-08
og_description: Imposta il nome del tag e crea un controllo contenuto (SDT) in un
  documento Word usando C#. Segui questa guida passo‑passo per aggiungere l'SDT, scrivere
  testo nel tag e modificare il documento.
og_image_alt: Screenshot showing a Word document with a StructuredDocumentTag whose
  tag name is set
og_title: Imposta il nome del tag e aggiungi SDT in un documento Word – guida C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Set tag name and create a content control (SDT) in a Word document
    using C#. Learn how to add SDT, write text to tag, and modify the document.
  headline: How to set tag name and add SDT in a Word document with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Come impostare il nome del tag e aggiungere SDT in un documento Word con C#
url: /it/java/document-manipulation/how-to-set-tag-name-and-add-sdt-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare il nome del tag e aggiungere SDT in un documento Word con C#

Se hai bisogno di **impostare il nome del tag** per uno StructuredDocumentTag (SDT) mentre lavori con file Word, questa guida ti mostra esattamente come fare. Vedrai un esempio completo, eseguibile, che **crea un controllo di contenuto**, scrive testo nel tag e **modifica il documento Word** dall'inizio alla fine.

Gli sviluppatori chiedono spesso: *“come aggiungere sdt* a un .docx esistente e poi *scrivere testo nel tag*?” – la risposta sta nell'utilizzare l'API Aspose.Words per .NET. Alla fine di questo tutorial sarai in grado di aprire un file Word, inserire un SDT di testo semplice, impostarne il nome del tag, popolarlo con contenuto e salvare le modifiche senza lasciare risorse pendenti.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o successivo installato.
* Una licenza valida di Aspose.Words per .NET (oppure puoi lavorare con la versione di valutazione).
* Visual Studio 2022 (o qualsiasi IDE che supporti C#).
* Un documento Word di input (`input.docx`) posizionato in una cartella a cui puoi fare riferimento dal codice.

## Passo 1: Configurare il progetto e importare i namespace

Crea un nuovo progetto Console App e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet new console -n WordSdtDemo
cd WordSdtDemo
dotnet add package Aspose.Words
```

Quindi, aggiungi le direttive `using` necessarie all'inizio di `Program.cs`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;
```

Questi namespace ti danno accesso a `Document`, `DocumentBuilder` e alla classe `StructuredDocumentTag`, indispensabili per **modificare un documento Word**.

## Passo 2: Caricare il documento Word esistente

La prima operazione è caricare il file che vuoi modificare. Questo passaggio è richiesto in ogni scenario in cui **modifichi il contenuto di un documento Word**.

```csharp
// Load an existing Word document from disk
string inputPath = @"YOUR_DIRECTORY\input.docx";
Document doc = new Document(inputPath);
Console.WriteLine($"Loaded document: {inputPath}");
```

> **Perché carichiamo prima il documento** – L'oggetto `Document` rappresenta l'intero pacchetto .docx in memoria. Solo dopo il caricamento puoi inserire in modo sicuro nuovi nodi, come uno SDT.

## Passo 3: Inserire uno StructuredDocumentTag (SDT) e impostarne il nome del tag

Ora rispondiamo alla domanda centrale: **come aggiungere sdt** e **impostare il nome del tag**. Utilizziamo `DocumentBuilder.InsertStructuredDocumentTag` con `SdtType.PlainText`. Il secondo argomento è il nome del tag, che potrai poi riferire programmaticamente o tramite l'interfaccia di Word.

```csharp
// Create a DocumentBuilder attached to the loaded document
DocumentBuilder builder = new DocumentBuilder(doc);

// Insert a plain‑text StructuredDocumentTag (content control) at the cursor position
// The second parameter ("MyTag") is the tag name we are setting.
StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
    SdtType.PlainText, "MyTag");

// Confirm that the tag name has been set
Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");
```

> **Spiegazione** – `InsertStructuredDocumentTag` restituisce un'istanza di `StructuredDocumentTag`. Passando `"MyTag"` **impostiamo il nome del tag** direttamente al momento della creazione. Se in seguito devi cambiarlo, puoi assegnare un nuovo valore a `sdt.Tag`.

## Passo 4: Scrivere testo nel tag appena creato

Dopo che lo SDT esiste, tipicamente vuoi **scrivere testo nel tag** affinché gli utenti finali vedano un segnaposto o contenuto predefinito. Il metodo `SetText` fa esattamente questo.

```csharp
// Populate the SDT with sample content
sdt.SetText("Sample content");

// Optionally, you can also set the placeholder text that appears when the tag is empty
sdt.PlaceholderName = "Enter your text here";
Console.WriteLine("Text written to the SDT.");
```

> **Perché usare SetText** – Assegnare direttamente alla proprietà `Text` sostituirebbe l'intera gerarchia del nodo. `SetText` aggiorna in modo sicuro il testo interno del controllo di contenuto preservando la sua struttura.

## Passo 5: Salvare il documento modificato

Infine, persisti le modifiche in un nuovo file. Questo completa il flusso di lavoro **modifica documento Word**.

```csharp
// Define the output path
string outputPath = @"YOUR_DIRECTORY\output.docx";

// Save the document with the inserted content control
doc.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Quando apri `output.docx` in Microsoft Word, vedrai un controllo di contenuto di testo semplice etichettato **MyTag** contenente il testo “Sample content”. Il controllo può essere modificato manualmente e il nome del tag rimane accessibile tramite gli strumenti per sviluppatori di Word.

## Codice sorgente completo

Di seguito trovi il programma completo, autonomo. Copialo in `Program.cs` ed eseguilo; non sono necessari snippet aggiuntivi.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Markup;

namespace WordSdtDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Load the existing Word document
            string inputPath = @"YOUR_DIRECTORY\input.docx";
            Document doc = new Document(inputPath);
            Console.WriteLine($"Loaded document: {inputPath}");

            // 2️⃣ Create a DocumentBuilder to work with the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert a plain‑text StructuredDocumentTag (SDT) and set its tag name
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                SdtType.PlainText, "MyTag");
            Console.WriteLine($"Inserted SDT with tag name: {sdt.Tag}");

            // 4️⃣ Write text to the tag (and optionally set a placeholder)
            sdt.SetText("Sample content");
            sdt.PlaceholderName = "Enter your text here";
            Console.WriteLine("Text written to the SDT.");

            // 5️⃣ Save the modified document
            string outputPath = @"YOUR_DIRECTORY\output.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

### Output previsto nella console

```
Loaded document: YOUR_DIRECTORY\input.docx
Inserted SDT with tag name: MyTag
Text written to the SDT.
Document saved to: YOUR_DIRECTORY\output.docx
```

### Come appare il file Word risultante

![Word document showing a content control named MyTag with the text “Sample content”](/images/word-sdt-example.png){: .img-fluid alt="Esempio di impostazione del nome del tag in un documento Word"}

*Lo screenshot illustra lo SDT con il **nome del tag** impostato a *MyTag* e il testo incorporato visibile.*

## Varianti comuni e casi limite

| Situazione | Come gestirla |
|------------|---------------|
| **Creare uno SDT di testo ricco** | Usa `SdtType.RichText` invece di `PlainText`. |
| **Impostare un nome del tag diverso dopo l'inserimento** | `sdt.Tag = "NewTag";` – puoi riassegnare il nome del tag in qualsiasi momento. |
| **Aggiungere lo SDT all'interno di un paragrafo specifico** | Sposta il cursore del builder (`builder.MoveToParagraph(index)`) prima di chiamare `InsertStructuredDocumentTag`. |
| **Più SDT nello stesso documento** | Ripeti i passi 3‑4 per ogni controllo; ognuno può avere un nome del tag unico. |
| **Lavorare con documenti protetti** | Assicurati che il documento sia non protetto (`doc.Unprotect()`) prima di inserire uno SDT. |

## Consigli professionali per un'automazione Word robusta

* **Licenza anticipata** – Chiama `Aspose.Words.License license = new Aspose.Words.License(); license.SetLicense("Aspose.Words.lic");` all'inizio di `Main` per evitare filigrane di valutazione.
* **Rilasciare gli oggetti** – Avvolgi `Document` in un blocco `using` se punti al .NET Framework per garantire il rilascio delle handle dei file.
* **Convalidare l'esistenza del tag** – Quando leggi in seguito un documento, usa `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)` per individuare i tag tramite la proprietà `Tag`.
* **Prestazioni** – Per documenti di grandi dimensioni, carica solo le sezioni necessarie usando `LoadOptions` con `LoadFormat.Docx` e `LoadFormat.Auto`.  

## Conclusione

Ora sai come **impostare il nome del tag**, **creare un controllo di contenuto**, **scrivere testo nel tag** e **modificare un documento Word** usando C#. L'esempio completo dimostra il modello standard per **come aggiungere sdt** e salvare le modifiche in modo sicuro.  

Da qui


## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aggiungere contenuto usando Document Builder in Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/)
- [Documento Word - Come rimuovere contenuto](/words/english/net/remove-content/)
- [Creare documento Word con Aspose.Words – Guida passo‑per‑passo](/words/english/net/enable-opentype-features/create-word-document-with-aspose-words-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}