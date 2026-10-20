---
category: general
date: 2026-08-20
description: Scopri come impostare la proprietà nascosta di una forma in Aspose.Words
  per C#. Questa guida mostra come inserire un'immagine e nascondere la forma in modo
  che non compaia mai nell'interfaccia utente o nell'output di stampa.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- set shape hidden property
- insert image into document
- hide shape in Aspose.Words
- C# shape hidden property
- Aspose.Words DocumentBuilder
- prevent shape from printing
language: it
lastmod: 2026-08-20
og_description: Imposta la proprietà nascosta della forma in Aspose.Words con C#.
  Inserisci un'immagine, nascondi la forma e assicurati che non venga mai visualizzata
  nell'interfaccia utente né nell'output di stampa.
og_image_alt: Diagram illustrating set shape hidden property on a Word document shape
og_title: Imposta la proprietà nascosta della forma in Aspose.Words – guida completa
  C#
schemas:
- author: Aspose
  dateModified: '2026-08-20'
  description: Learn how to set shape hidden property in Aspose.Words for C#. This
    guide shows inserting an image and hiding the shape so it never appears in the
    UI or print output.
  headline: How to set shape hidden property in Aspose.Words for C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Document Automation
- Shape Handling
title: Come impostare la proprietà nascosta della forma in Aspose.Words per C#
url: /it/java/images-shapes/how-to-set-shape-hidden-property-in-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare la proprietà hidden della forma in Aspose.Words per C#

Se hai bisogno di **impostare la proprietà hidden della forma** in un documento Word, questo tutorial ti mostra i passaggi esatti usando Aspose.Words per .NET. Che tu stia creando un motore di template, generando report o incorporando un logo che deve rimanere invisibile, imparerai come inserire un'immagine e nascondere la forma in modo che non appaia mai nell'interfaccia utente o nell'output di stampa.

In questa guida copriamo anche **insert image into document**, spieghiamo perché nascondere una forma è importante per la stampa e ti guidiamo attraverso il codice completo e eseguibile. Non sono necessari riferimenti esterni—basta copiare, incollare ed eseguire.

## Prerequisiti

* .NET 6.0 o successivo (l'ultima versione di Aspose.Words supporta .NET 6+)
* Una licenza valida di Aspose.Words per .NET (o utilizza la modalità di valutazione gratuita)
* Visual Studio 2022 o qualsiasi IDE C# che preferisci
* Un file immagine (ad esempio `logo.png`) posizionato in una cartella a cui puoi fare riferimento dal codice

## Passo 1: Creare un nuovo Document e DocumentBuilder

La classe `DocumentBuilder` è il punto di ingresso per creare contenuti Word in modo programmatico. Consente di inserire paragrafi, tabelle e forme come le immagini.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Initialize a new blank document
        Document doc = new Document();
        // DocumentBuilder provides methods to add content
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché questo passo?*  
Creare un `Document` ti fornisce una rappresentazione in memoria di un file .docx, mentre il `DocumentBuilder` fornisce l'API fluente che inserisce gli oggetti. Senza questi oggetti non è possibile posizionare una forma nel documento.

## Passo 2: Inserire l'immagine come forma

Aspose.Words tratta ogni immagine come una `Shape`. Il metodo `InsertImage` restituisce quell'istanza di `Shape`, che puoi manipolare successivamente.

```csharp
        // Step 2: Insert an image into the document
        // The returned Shape object lets us modify properties like size, rotation, and visibility.
        Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");
```

*Perché questo passo?*  
Usare `InsertImage` non solo aggiunge l'immagine al flusso di testo, ma ti fornisce anche un riferimento (`picture`) che puoi configurare. Questo è essenziale per la **C# shape hidden property** che imposteremo successivamente.

## Passo 3: Impostare la proprietà hidden della forma

La proprietà `Hidden` controlla se la forma partecipa all'interfaccia utente e alla stampa. Impostandola su `true` la forma diventa invisibile nell'interfaccia di Word e garantisce che non venga stampata.

```csharp
        // Step 3: Hide the inserted shape so it won't appear in the UI or print output
        picture.Hidden = true;
```

*Perché questo passo?*  
Quando una forma è contrassegnata come hidden, Word la tratta come un commento—presente nella struttura del documento ma mai renderizzata. Questo è il fulcro di **set shape hidden property**.

## Passo 4: Salvare il documento

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi formato supportato da Aspose.Words (`.docx`, `.pdf`, `.html`, ecc.).

```csharp
        // Step 4: Save the document to a .docx file
        doc.Save(@"OUTPUT\HiddenImageDocument.docx");
        // Optional: Save as PDF to verify the shape really stays hidden when printed
        doc.Save(@"OUTPUT\HiddenImageDocument.pdf");
    }
}
```

*Perché questo passo?*  
Il salvataggio finalizza le modifiche in memoria. Aprire il `.docx` risultante in Microsoft Word non mostra alcuna immagine visibile, e l'esportazione in PDF conferma che la forma non appare mai nell'output di stampa.

## Esempio completo, eseguibile

Mettendo tutto insieme, ecco il programma completo che puoi compilare ed eseguire:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeHiddenDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize a blank document and a builder
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 2️⃣ Insert an image as a shape
            // Replace YOUR_DIRECTORY with the actual folder that contains logo.png
            Shape picture = builder.InsertImage(@"YOUR_DIRECTORY\logo.png");

            // 3️⃣ Set the shape hidden property
            picture.Hidden = true; // This hides the shape in UI and when printing

            // 4️⃣ Save the document in both DOCX and PDF formats
            doc.Save(@"OUTPUT\HiddenImageDocument.docx");
            doc.Save(@"OUTPUT\HiddenImageDocument.pdf");

            Console.WriteLine("Document created successfully. The image is hidden.");
        }
    }
}
```

**Output previsto**

* Aprendo `HiddenImageDocument.docx` in Microsoft Word non viene mostrata alcuna immagine visibile.
* Esportando o stampando il documento (o aprendo il PDF) non viene mostrata alcuna immagine.
* La forma nascosta esiste ancora nell'XML del documento, che puoi verificare aprendo il `.docx` come zip e ispezionando `word/document.xml` – vedrai un elemento `<w:pict>` con `w:hidden="true"`.

## Variazioni comuni e casi limite

| Situation | What to do | Why it matters |
|-----------|------------|----------------|
| **File immagine mancante** | Avvolgi `InsertImage` in un `try/catch` e gestisci `FileNotFoundException`. | Previene il crash dell'applicazione e consente di registrare un errore chiaro. |
| **Forme nascoste multiple** | Chiama `picture.Hidden = true` per ogni `Shape` inserita, oppure itera su `doc.GetChildNodes(NodeType.Shape, true)`. | Garantisce che ogni elemento visivo indesiderato rimanga invisibile. |
| **Necessità della forma visibile solo in modalità di modifica** | Imposta `picture.Hidden = false` dopo la modifica, poi riattiva il flag prima di salvare. | Ti permette di lavorare con la forma nell'interfaccia utente mantenendo pulito l'output finale. |
| **Stampa su versioni Word più vecchie** | Verifica il documento con Word 2010 o versioni successive; il flag hidden è supportato in tutte le versioni moderne. | Assicura la compatibilità per tutta la tua base utenti. |
| **Uso di un formato file diverso (ad esempio PDF direttamente)** | Il flag `Hidden` funziona allo stesso modo; Aspose.Words lo rispetta durante la conversione in PDF. | Conferma che **prevent shape from printing** funzioni per tutti i target di esportazione. |

## Suggerimento professionale: Verificare il flag hidden programmaticamente

Se hai bisogno di confermare che una forma sia hidden prima di salvare, puoi ispezionare la proprietà:

```csharp
bool isHidden = picture.Hidden;
Console.WriteLine($"Shape hidden? {isHidden}");
```

Questo semplice controllo è utile in pipeline automatizzate dove devi garantire la conformità alle politiche di generazione dei documenti.

## Conclusione

Ora sai come **set shape hidden property** in Aspose.Words per C#. Inserendo un'immagine, applicando `picture.Hidden = true` e salvando il documento, la forma rimane fuori dall'interfaccia utente e non appare mai nell'output stampato. Questa tecnica è essenziale quando hai bisogno di segnaposti, filigrane o elementi di branding che devono rimanere invisibili agli utenti finali.

### Cosa c'è dopo?

* Esplora altre proprietà della forma come `picture.WrapType`, `picture.Rotation` e `picture.RelativeHorizontalPosition`.
* Impara come **hide shape in Aspose.Words** in modo condizionale basato su input dell'utente o configurazione.
* Combina forme nascoste con cicli **insert image into document** per generare marcatori dinamici e invisibili per elaborazioni successive (ad esempio campi di stampa unione).

Sentiti libero di sperimentare con diversi formati immagine, layout di documento e target di esportazione. Nascondere le forme ti dà un controllo dettagliato su ciò che i lettori vedono realmente—e su ciò che rimane dietro le quinte. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserisci immagine inline in documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}