---
category: general
date: 2026-11-22
description: Imposta il testo segnaposto in un controllo di contenuto Word con C#.
  Scopri come creare un tag personalizzato, inserire un controllo di testo semplice
  e aggiungere un segnaposto al tag usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set placeholder text
- create custom tag
- how to insert content control
- add placeholder to tag
- insert plain text control
language: it
lastmod: 2026-11-22
og_description: Imposta il testo segnaposto in un controllo contenuto di Word con
  C#. Questo tutorial ti mostra come creare un tag personalizzato, inserire un controllo
  di testo semplice e aggiungere un segnaposto al tag per una migliore interattività
  del documento.
og_image_alt: Screenshot showing a Word document with a content control placeholder
  text set using C#
og_title: Imposta il testo segnaposto in un controllo di contenuto Word – Guida C#
schemas:
- author: Aspose
  dateModified: '2026-11-22'
  description: Set placeholder text in a Word content control with C#. Learn how to
    create a custom tag, insert a plain text control, and add placeholder to tag using
    Aspose.Words.
  headline: Set placeholder text in a Word content control with C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Content Control
- Word Automation
title: Imposta testo segnaposto in un controllo contenuto di Word con C#
url: /it/java/using-document-elements/set-placeholder-text-in-a-word-content-control-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Imposta testo segnaposto in un controllo di contenuto Word con C#

Se hai bisogno di **impostare testo segnaposto** in un documento Word in modo programmatico, questa guida ti mostra esattamente come farlo. Utilizzando Aspose.Words per .NET puoi creare un tag personalizzato, inserire un controllo di testo semplice e aggiungere un segnaposto al tag in modo che il documento sia pronto per l'immissione dell'utente.

In questo tutorial imparerai come **creare un tag personalizzato**, **inserire un controllo di contenuto**, e **aggiungere un segnaposto al tag** mantenendo il codice conciso e pronto per la produzione. Non sono necessari strumenti esterni—solo un progetto .NET e la libreria Aspose.Words.

## Prerequisiti

* SDK .NET 6.0 o successivo installato  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione gratuita)  
* Conoscenza di base di C# e Visual Studio (o qualsiasi IDE preferisci)  

Le sezioni seguenti presumono che tu abbia creato un progetto console chiamato `WordPlaceholderDemo`.

## Passo 1: Installa Aspose.Words

Aggiungi il pacchetto NuGet al tuo progetto:

```bash
dotnet add package Aspose.Words
```

> **Suggerimento:** Usa il flag `--version` per fissare il pacchetto alla versione stabile più recente (ad es., `Aspose.Words.NET 24.9`).

## Passo 2: Carica il documento sorgente e crea un `DocumentBuilder`

La prima cosa da fare è caricare un file `.docx` esistente (o creare un nuovo documento vuoto) e istanziare un `DocumentBuilder`. Il builder ti fornisce un'API fluida per inserire controlli e testo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Load an existing Word file or create a new one
            Document doc = new Document("input.docx");   // <-- replace with your path
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Questo codice **prepara il terreno** per l'inserimento di un controllo di contenuto. Il `DocumentBuilder` lavora direttamente sull'oggetto `doc`, quindi qualsiasi modifica apporti viene riflessa automaticamente.

## Passo 3: Crea un tag personalizzato (StructuredDocumentTag)

Un *tag personalizzato* in Word è chiamato **StructuredDocumentTag (SDT)**. Puoi considerarlo come un controllo di contenuto che porta un identificatore unico. Crearne uno è il fulcro del passo **crea tag personalizzato**.

```csharp
            // Insert a plain‑text StructuredDocumentTag (SDT) with a tag identifier
            StructuredDocumentTag sdt = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
```

Il metodo `InsertStructuredDocumentTag` accetta due argomenti:

1. Il tipo di controllo (`PlainText` in questo caso).  
2. Una stringa che identifica univocamente il tag (`"MyTag"`).  

Utilizzando un **tag personalizzato**, puoi successivamente individuare o manipolare il controllo in modo programmatico.

## Passo 4: Imposta un titolo per l'accessibilità

Un titolo migliora l'accessibilità e rende il controllo più facile da trovare nell'interfaccia di Word.

```csharp
            // Set a descriptive title (used by screen readers)
            sdt.Title = "CustomerName";
```

La proprietà `Title` è opzionale, ma aggiungerla è una buona pratica quando **aggiungi un segnaposto al tag** per migliorare l'esperienza dell'utente.

## Passo 5: Aggiungi testo segnaposto al tag

Ora arriva l'obiettivo principale: **impostare testo segnaposto**. Questo testo appare quando il controllo è vuoto, guidando l'utente su cosa digitare.

```csharp
            // Provide placeholder text that shows when the tag is empty
            sdt.PlaceholderText = "Enter name…";
```

La proprietà `PlaceholderText` è esattamente ciò di cui hai bisogno per **aggiungere un segnaposto al tag**. Si comporta come il suggerimento grigio che vedi nei campi di modulo moderni.

## Passo 6: Salva il documento modificato

Dopo aver configurato il controllo, scrivi il documento nuovamente su disco.

```csharp
            // Save the document with the new content control
            doc.Save("output.docx");   // <-- replace with your desired path
        }
    }
}
```

Quando apri `output.docx` in Microsoft Word, vedrai un controllo di contenuto di testo semplice etichettato “CustomerName” con il segnaposto “Enter name…”. Cliccando all'interno del controllo il segnaposto scompare, permettendo all'utente di digitare.

### Output previsto

* Un file Word (`output.docx`) contenente un singolo controllo di contenuto di testo semplice.  
* Il controllo visualizza il segnaposto “Enter name…” finché l'utente non digita qualcosa.  
* L'identificatore del tag del controllo è `MyTag`, che puoi interrogare in seguito con `doc.GetChildNodes(NodeType.StructuredDocumentTag, true)`.

## Passo 7: Come inserire un controllo di contenuto altrove (avanzato)

Se hai bisogno di **inserire un controllo di contenuto** in una posizione specifica—ad esempio, dopo un determinato paragrafo—usa il metodo `MoveTo` prima di inserire il tag:

```csharp
            // Move the cursor to the end of the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            // Insert another plain‑text control with a different tag
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";
```

Questo frammento dimostra **l'inserimento di un controllo di testo semplice** più volte nello stesso documento.

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| Segnaposto non visibile | Il controllo contiene già del testo (anche uno spazio) | Assicurati che `sdt.Text` sia vuoto prima di impostare `PlaceholderText`. |
| Collisione dell'identificatore del tag | Riutilizzo dello stesso nome tag (`MyTag`) nello stesso documento | Usa identificatori unici per ogni `StructuredDocumentTag`. |
| Eccezione di licenza | Esecuzione senza una licenza valida di Aspose.Words | Applica un file di licenza (`license.SetLicense("Aspose.Words.lic")`) all'inizio di `Main`. |
| Documento non salvato | Dimenticare di chiamare `doc.Save` o usare un percorso di sola lettura | Verifica che il percorso di output sia scrivibile e chiama `doc.Save`. |

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in `Program.cs`. Include tutti i passaggi—**crea tag personalizzato**, **come inserire un controllo di contenuto**, **aggiungi segnaposto al tag**, e **inserisci un controllo di testo semplice**—in un unico flusso coerente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Building;
using Aspose.Words.Markup;

namespace WordPlaceholderDemo
{
    class Program
    {
        static void Main()
        {
            // Optional: apply your Aspose.Words license here
            // var license = new License();
            // license.SetLicense("Aspose.Words.lic");

            // Load the source document (or create a new one)
            Document doc = new Document("input.docx");
            DocumentBuilder builder = new DocumentBuilder(doc);

            // --------- Create custom tag ----------
            StructuredDocumentTag nameTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "MyTag");
            nameTag.Title = "CustomerName";
            nameTag.PlaceholderText = "Enter name…";

            // Insert a second control after the first paragraph
            builder.MoveTo(doc.FirstSection.Body.Paragraphs[0].End);
            StructuredDocumentTag addressTag = builder.InsertStructuredDocumentTag(
                StructuredDocumentTagType.PlainText, "AddressTag");
            addressTag.Title = "CustomerAddress";
            addressTag.PlaceholderText = "Enter address…";

            // Save the result
            doc.Save("output.docx");
            Console.WriteLine("Document saved with placeholder text set.");
        }
    }
}
```

Esegui il programma con `dotnet run`. Dopo l'esecuzione, apri `output.docx` per verificare che entrambi i controlli mostrino i rispettivi segnaposti.

## Prossimi passi

* **Personalizza l'aspetto** – Usa `sdt.Font` per cambiare dimensione, colore o stile del carattere all'interno del controllo.  
* **Associa a dati XML** – Esplora `sdt.XmlMapping` se hai bisogno che il controllo si mappi

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word programmaticamente – aggiungi controllo di contenuto e segnaposto](/words/english/net/programming-with-sdt/create-word-document-programmatically-add-content-control-an/)
- [Imposta testo segnaposto in Aspose.Words – Guida completa C#](/words/english/net/programming-with-sdt/set-placeholder-text-in-aspose-words-complete-c-guide/)
- [Crea nuovo documento Word e inserisci controllo di contenuto in C#](/words/english/net/programming-with-sdt/create-new-word-document-and-insert-content-control-in-c/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}