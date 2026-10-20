---
category: general
date: 2026-09-18
description: Crea un documento Word vuoto e nascondi una forma ellittica usando Aspose.Words.
  Scopri come nascondere una forma in Word, come inserire un'ellisse e creare rapidamente
  una forma nascosta.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to hide shape
- how to insert ellipse
- hide shape in word
- create hidden shape
language: it
lastmod: 2026-09-18
og_description: Crea un documento Word vuoto e nascondi una forma ellittica in Word.
  Questa guida ti mostra passo passo come inserire un'ellisse, nascondere la forma
  in Word e creare una forma nascosta con Aspose.Words.
og_image_alt: Screenshot of a blank Word document containing a hidden ellipse shape
  created with Aspose.Words
og_title: Crea un documento Word vuoto con una forma ellittica nascosta
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  headline: Create a blank Word document with a hidden ellipse shape
  type: TechArticle
- description: Create a blank Word document and hide an ellipse shape using Aspose.Words.
    Learn how to hide shape in Word, how to insert ellipse, and create hidden shape
    quickly.
  name: Create a blank Word document with a hidden ellipse shape
  steps:
  - name: Pro tip
    text: If you later need to make the shape visible again, simply set `ellipse.Hidden
      = false;` and save the document.
  - name: What if the shape still appears?
    text: '* Ensure you are using Aspose.Words 23.9 or later – older versions had
      a bug where `Hidden` was ignored for some shape types. * Verify that you are
      not applying any additional formatting (e.g., `WrapType`) that forces the shape
      to occupy layout space.'
  - name: Can I hide other shape types?
    text: Yes. The same `Hidden` property works for `ShapeType.Rectangle`, `ShapeType.Picture`,
      etc. Just replace `ShapeType.Ellipse` with the desired type.
  - name: How to list hidden shapes later?
    text: '```csharp foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
      { if (shape.Hidden) Console.WriteLine($"Hidden shape: {shape.ShapeType}"); }
      ```'
  - name: Next steps
    text: '* Explore **how to hide shape** conditionally based on document content.
      * Learn **how to unhide shape** when generating a final version of the document.
      * Combine hidden shapes with **custom document properties** to embed machine‑readable
      data.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crea un documento Word vuoto con una forma ellittica nascosta
url: /it/java/images-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto con una forma ellisse nascosta

Se hai bisogno di **create a blank Word document** che contenga una forma che non vuoi che appaia nel layout, questa guida ti mostra esattamente come farlo. Utilizzando Aspose.Words per .NET puoi inserire programmaticamente un'ellisse e poi nascondere la forma in modo che il documento rimanga visivamente vuoto pur contenendo i dati della forma.

In questo tutorial imparerai:

* come **create blank Word document** oggetti,
* come **insert ellipse** usando `DocumentBuilder`,
* come **hide shape in Word** così non influisce sulla pagina,
* come **create hidden shape** oggetti per elaborazioni successive.

I passaggi funzionano con .NET 6+ e l'ultima versione di Aspose.Words (23.9 al momento della stesura). Non è necessaria alcuna installazione aggiuntiva di Office.

## Prerequisites

* Visual Studio 2022 (o qualsiasi IDE C#)
* .NET 6 SDK o successivo
* Pacchetto NuGet Aspose.Words for .NET  
  ```bash
  dotnet add package Aspose.Words
  ```
* Conoscenze di base di C# e dei concetti dei documenti Word

## Step 1: Create a blank Word document

La prima cosa da fare è istanziare un oggetto `Document`. Questo oggetto rappresenta un file `.docx` vuoto ed è la base per tutte le operazioni successive.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document doc = new Document();   // <-- creates a blank Word document in memory
```

Creare un **blank Word document** ti fornisce una tela pulita – nessun paragrafo, nessuna sezione, solo la struttura del pacchetto sottostante. È il punto di partenza ideale quando ti serve solo una forma nascosta e nient'altro.

## Step 2: Initialise a DocumentBuilder

`DocumentBuilder` fornisce un'API comoda per aggiungere contenuti a un `Document`. Funziona come un cursore che si sposta attraverso il documento.

```csharp
// Step 2: Initialise a DocumentBuilder to work with the document
DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder crea automaticamente una prima sezione e un paragrafo predefiniti, così puoi iniziare a inserire forme senza dover aggiungere sezioni manualmente.

## Step 3: Insert an ellipse shape

Ora **insert ellipse** usando il metodo `InsertShape`. Il metodo accetta un enumeratore `ShapeType`, la larghezza e l'altezza (in punti).

```csharp
// Step 3: Insert an ellipse shape with a width of 100 points and a height of 50 points
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
```

Perché un'ellisse? Un'ellisse è una forma vettoriale che può essere nascosta senza influire sul flusso di testo circostante. La larghezza di 100 pt e l'altezza di 50 pt sono arbitrarie; puoi modificarle in base alle esigenze di elaborazione successive.

## Step 4: Hide the shape so it does not appear in the layout

Per **hide shape in Word**, imposta la proprietà `Hidden` sull'oggetto `Shape` a `true`. Quando il documento viene aperto in Microsoft Word, la forma sarà invisibile e non occuperà spazio nel layout.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
ellipse.Hidden = true;   // <-- this hides the shape in Word
```

Il flag `Hidden` è memorizzato nell'XML della forma (`<w:hidden/>`). Word rispetta questo attributo durante il rendering, motivo per cui il documento appare completamente vuoto anche se la forma esiste.

### Pro tip

Se in seguito devi rendere nuovamente visibile la forma, imposta semplicemente `ellipse.Hidden = false;` e salva il documento.

## Step 5: Save the document with the hidden shape

Infine, persisti il documento su disco. Il file sarà un normale `.docx` apribile da qualsiasi elaboratore di testi Word.

```csharp
// Step 5: Save the document with the hidden shape
doc.Save(@"C:\Temp\HiddenEllipse.docx");
```

Il file salvato, `HiddenEllipse.docx`, è un **create blank word document** che contiene un'ellisse nascosta. Aprendolo in Microsoft Word si visualizza una pagina vuota, ma la forma è ancora presente nella struttura Open XML.

## Full working example

Di seguito trovi il programma completo e autonomo che puoi copiare, incollare ed eseguire.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace HiddenShapeDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a blank Word document
            Document doc = new Document();

            // 2️⃣ Initialise DocumentBuilder
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse shape (width: 100pt, height: 50pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the shape so it does not affect layout
            ellipse.Hidden = true;

            // 5️⃣ Save the result
            string outputPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Expected output**

* Un file chiamato `HiddenEllipse.docx` appare in `C:\Temp`.
* Aprendo il file in Microsoft Word viene mostrata una pagina completamente vuota.
* Se ispezioni il documento con l'Open XML SDK o un visualizzatore zip, troverai l'elemento `<w:shape>` con `<w:hidden/>` all'interno della parte del documento.

## Common questions and edge cases

### What if the shape still appears?

* Assicurati di utilizzare Aspose.Words 23.9 o successivo – le versioni precedenti presentavano un bug per cui `Hidden` veniva ignorato per alcuni tipi di forma.
* Verifica di non applicare formattazioni aggiuntive (ad es., `WrapType`) che forzano la forma a occupare spazio nel layout.

### Can I hide other shape types?

Sì. La stessa proprietà `Hidden` funziona per `ShapeType.Rectangle`, `ShapeType.Picture`, ecc. Basta sostituire `ShapeType.Ellipse` con il tipo desiderato.

### How to list hidden shapes later?

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.Hidden)
        Console.WriteLine($"Hidden shape: {shape.ShapeType}");
}
```

Questo snippet itera su tutte le forme e stampa quelle nascoste, utile per i flussi di lavoro **create hidden shape** dove in seguito è necessario elaborarle o renderle visibili.

## Conclusion

Ora sai come **create a blank Word document**, **insert ellipse**, e **hide shape in Word** per produrre un **create hidden shape** che rimane invisibile al lettore. Questa tecnica è utile per memorizzare metadati, segnalibri o XML personalizzato all'interno di un documento senza alterarne l'aspetto visivo.

### Next steps

* Esplora **how to hide shape** in modo condizionale in base al contenuto del documento.
* Impara **how to unhide shape** quando generi una versione finale del documento.
* Combina forme nascoste con **custom document properties** per incorporare dati leggibili da macchine.

Sentiti libero di sperimentare con diversi tipi di forma, dimensioni e logiche di stato nascosto per adattarle al tuo scenario di automazione. Happy coding!

## What Should You Learn Next?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}