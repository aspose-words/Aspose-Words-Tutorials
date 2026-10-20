---
category: general
date: 2026-10-20
description: Imposta testo segnaposto in un documento Word usando C#. Scopri come
  aggiungere il controllo e impostare il segnaposto rapidamente con Aspose.Words per
  .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- how to add control
- how to set placeholder
- generate word c#
language: it
lastmod: 2026-10-20
og_description: Imposta testo segnaposto in un documento Word con C#. Questo tutorial
  ti mostra come aggiungere controlli, impostare segnaposto e generare file Word in
  modo programmatico.
og_image_alt: Screenshot of a Word document showing placeholder text created with
  C# code
og_title: Imposta testo segnaposto in un documento Word con C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Set placeholder text in a Word document using C#. Learn how to add
    control and set placeholder quickly with Aspose.Words for .NET.
  headline: Set placeholder text in a Word document using C#
  type: TechArticle
- questions:
  - answer: Yes. Aspose.Words for .NET is compatible with .NET Core, .NET 5, and .NET
      6+. The same code runs unchanged.
    question: Does this work with .NET Core?
  - answer: Use `sdt.SetText("Default value")` after creating the SDT. The placeholder
      disappears once a value is set.
    question: Can I set a default value in addition to the placeholder?
  - answer: 'Load the document, locate the SDT by its `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag,
      true)`) and read `sdt.GetText()`. ## Conclusion You now know how to **set placeholder
      text** in a Word document using C#. By creating a plain‑text `StructuredDocumentTag`,
      assigning a title and place'
    question: What if I need to retrieve the entered value later?
  type: FAQPage
tags:
- C#
- Aspose.Words
- Word automation
- Content control
title: Imposta testo segnaposto in un documento Word usando C#
url: /it/net/programming-with-sdt/set-placeholder-text-in-a-word-document-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta testo segnaposto in un documento Word usando C#

Se hai bisogno di **impostare testo segnaposto** in un file Microsoft Word mentre lo generi con C#, questa guida ti mostra esattamente come. Vedrai una soluzione concisa, end‑to‑end, che aggiunge un controllo di contenuto, definisce il suo segnaposto e salva il documento—tutto con Aspose.Words per .NET.

Molti sviluppatori si chiedono **come aggiungere un controllo** a un documento Word o **come impostare un segnaposto** senza aprire Word manualmente. Questo tutorial risponde a queste domande e dimostra anche un modo pulito per **generare file Word C#** pronti per l'input dell'utente.

## Cosa otterrai

* Creare un documento Word vuoto programmaticamente.
* Inserire un Structured Document Tag (SDT) di testo semplice, che è il nome tecnico di un controllo di contenuto.
* Assegnare un titolo significativo e un testo segnaposto allo SDT.
* Salvare il file `.docx` risultante su disco.

Non sono necessari strumenti aggiuntivi oltre alla libreria Aspose.Words e a un ambiente di sviluppo .NET 6 (o successivo).

## Prerequisiti

* .NET 6 SDK o versione più recente installata.  
* Visual Studio 2022 (o qualsiasi IDE che supporti .NET).  
* Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`).  

> **Suggerimento:** Usa la versione di valutazione gratuita di Aspose.Words se stai solo testando; aggiunge una filigrana ma funziona allo stesso modo della versione con licenza.

## Passo 1: Configura il progetto e importa i namespace

Crea un nuovo progetto console e aggiungi le direttive `using` richieste. Queste importano le classi principali di Aspose.Words e il namespace markup.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // The complete solution starts here.
        }
    }
}
```

*Perché questo passo è importante:* Importare `Aspose.Words.Markup` ti dà accesso a `StructuredDocumentTag`, `SdtType` e `MarkupLevel`—gli oggetti necessari per **aggiungere un controllo** e **impostare un segnaposto**.

## Passo 2: Crea un documento vuoto e un DocumentBuilder

Un `Document` rappresenta l'intero file Word, mentre un `DocumentBuilder` fornisce un cursore comodo per inserire elementi.

```csharp
// Step 2: Initialize a new empty document.
Document doc = new Document();

// DocumentBuilder starts at the beginning of the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché questo passo è importante:* Iniziare con un documento pulito garantisce che il segnaposto impostato appaia esattamente dove desideri, senza interferenze dal contenuto esistente.

## Passo 3: Crea il controllo di contenuto (Structured Document Tag)

Qui creiamo un SDT di testo semplice, gli assegniamo un titolo e impostiamo il testo segnaposto che l'utente vedrà quando il controllo è vuoto.

```csharp
// Step 3: Build a plain‑text Structured Document Tag (SDT).
StructuredDocumentTag sdt = new StructuredDocumentTag(
    doc,                     // Parent document
    SdtType.PlainText,       // Control type – plain text box
    MarkupLevel.Inline);     // Inline placement (behaves like a word)

sdt.Title = "CustomerName";                 // Logical name for the control
sdt.PlaceholderName = "Enter name here";    // Text shown when empty
```

*Perché questo passo è importante:* La proprietà `Title` ti consente di fare riferimento al controllo in seguito (ad esempio, per il data binding). `PlaceholderName` è esattamente il **testo segnaposto impostato** che vuoi far apparire, guidando l'utente finale.

## Passo 4: Inserisci il controllo nella posizione corrente del cursore

Usando il `DocumentBuilder`, inserisci lo SDT nel documento dove il builder è attualmente posizionato.

```csharp
// Step 4: Insert the SDT into the document.
builder.InsertNode(sdt);
```

*Perché questo passo è importante:* Inserire il nodo collega il controllo al DOM del documento. Se hai bisogno di aggiungere più segnaposti, puoi spostare il cursore del builder e ripetere questo passo.

## Passo 5: Salva il documento

Infine, scrivi il documento su disco. Sostituisci `YOUR_DIRECTORY` con un percorso reale sulla tua macchina.

```csharp
// Step 5: Save the .docx file.
string outputPath = @"C:\Temp\SDT.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri `SDT.docx` in Microsoft Word, vedrai una casella di testo in linea con sfondo grigio che contiene **Enter name here**. Cliccando all'interno della casella il segnaposto scompare, permettendo all'utente di digitare un nome cliente.

### Output previsto

| Posizione file | Anteprima contenuto |
|----------------|---------------------|
| `C:\Temp\SDT.docx` | Segnaposto in linea **Enter name here** all'interno di un controllo di contenuto di testo semplice intitolato *CustomerName*. |

## Casi limite e variazioni

| Situazione | Regolazione consigliata |
|------------|--------------------------|
| **Multiple placeholders** | Crea ulteriori oggetti `StructuredDocumentTag` con valori diversi di `Title` e `PlaceholderName`, quindi inserisci ciascuno dove necessario. |
| **Rich‑text placeholder** | Usa `SdtType.RichText` invece di `PlainText` per consentire la formattazione all'interno del segnaposto. |
| **Block‑level control** | Modifica `MarkupLevel.Inline` in `MarkupLevel.Block` per far sì che il controllo si comporti come un paragrafo intero. |
| **Placeholder not visible** | Assicurati che le impostazioni di visualizzazione del documento in Word non nascondano i controlli di contenuto (`File → Options → Advanced → Show content controls`). |
| **Saving to a stream** | Chiama `doc.Save(stream, SaveFormat.Docx)` se devi inviare il file via HTTP invece di scriverlo su disco. |

## Esempio completo e eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Include tutti i passaggi sopra in un unico metodo `Main`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Position a builder at the start of the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Define a plain‑text content control (SDT) with placeholder text.
            StructuredDocumentTag sdt = new StructuredDocumentTag(
                doc,
                SdtType.PlainText,
                MarkupLevel.Inline);

            sdt.Title = "CustomerName";                 // Logical identifier
            sdt.PlaceholderName = "Enter name here";    // The placeholder you see in Word

            // 4️⃣ Insert the SDT into the document.
            builder.InsertNode(sdt);

            // 5️⃣ Save the document to disk.
            string outputPath = @"C:\Temp\SDT.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document successfully saved to {outputPath}");
        }
    }
}
```

Esegui il programma, apri il file generato e vedrai il testo segnaposto pronto per l'input dell'utente.

## Domande frequenti

**Q: Funziona con .NET Core?**  
A: Sì. Aspose.Words per .NET è compatibile con .NET Core, .NET 5 e .NET 6+. Lo stesso codice funziona senza modifiche.

**Q: Posso impostare un valore predefinito oltre al segnaposto?**  
A: Usa `sdt.SetText("Default value")` dopo aver creato lo SDT. Il segnaposto scompare una volta impostato un valore.

**Q: E se devo recuperare il valore inserito in seguito?**  
A: Carica il documento, individua lo SDT tramite il suo `Title` (`doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`) e leggi `sdt.GetText()`.

## Conclusione

Ora sai come **impostare testo segnaposto** in un documento Word usando C#. Creando un `StructuredDocumentTag` di testo semplice, assegnando un titolo e un segnaposto, inserendolo con un `DocumentBuilder` e salvando il file, puoi **aggiungere un controllo** e **generare file Word C#** programmaticamente.  

Da qui potresti esplorare:

* Aggiungere controlli di testo ricco o liste a discesa (`SdtType.RichText`, `SdtType.DropDownList`).  
* Popolare più segnaposti da un database.  
* Convertire il `.docx` generato in PDF con Aspose.Words.

Sperimenta con diversi tipi di controllo e stili di segnaposto per adattarli alle esigenze della tua applicazione. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Imposta testo segnaposto in Aspose.Words – Guida completa C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Crea documento Word programmaticamente – aggiungi controllo di contenuto e segnaposto](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Come aggiungere un controllo di contenuto e creare un documento Word con Aspose – Completo](/words/english/net/programming-with-sdt/how-to-add-content-control-and-create-word-document-with-asp/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}