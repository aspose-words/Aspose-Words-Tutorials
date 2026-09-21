---
category: general
date: 2026-09-21
description: Crea un documento Word vuoto con un'ellisse nascosta usando C#. Scopri
  come nascondere una forma in Word e generare una forma nascosta programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to create ellipse
- hide shape in word
- create hidden shape
language: it
lastmod: 2026-09-21
og_description: Crea un documento Word vuoto con un'ellisse nascosta usando C#. Questa
  guida mostra come nascondere una forma in Word e creare forme nascoste programmaticamente.
og_image_alt: Screenshot of a blank Word document that contains a hidden ellipse shape
  created with C#
og_title: Crea un documento Word vuoto con una forma ellittica nascosta in C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create blank Word document with a hidden ellipse using C#. Learn how
    to hide shape in Word and generate a hidden shape programmatically.
  headline: How to create blank Word document and add a hidden ellipse shape in C#
  type: TechArticle
- questions:
  - answer: The shape’s XML adds a few hundred bytes, which is negligible for most
      use cases. The file remains essentially the same size as a truly empty document.
    question: Does hiding a shape affect document size?
  - answer: Yes. Load the document, locate the shape (`doc.GetChildNodes(NodeType.Shape,
      true)`), and set `shape.Hidden = false`.
    question: Can I unhide the shape later programmatically?
  - answer: No. Hidden objects are excluded from the print layout, so the printed
      page stays blank.
    question: Will the hidden shape appear when printing?
  - answer: 'The `Hidden` property is part of the OOXML spec, so any Word processor
      that fully implements OOXML (Word, LibreOffice, Google Docs) will respect the
      hidden flag. --- ## Conclusion You now know how to **create blank Word document**,
      **how to create ellipse**, **hide shape in Word**, and **create hidd'
    question: Is this approach compatible with Office Open XML (OOXML) only?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Come creare un documento Word vuoto e aggiungere una forma ellisse nascosta
  in C#
url: /it/java/images-shapes/how-to-create-blank-word-document-and-add-a-hidden-ellipse-s/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e aggiungere una forma ellittica nascosta in C#

Se hai bisogno di **create blank Word document** che contenga una grafica invisibile, questa guida ti mostra esattamente come fare. Alla fine del tutorial avrai un file .docx che sembra vuoto ma che in realtà contiene una forma ellittica nascosta dal layout.

Utilizzeremo Aspose.Words per .NET per costruire il documento, inserire un'ellisse, nasconderla e salvare il file. I passaggi coprono anche **how to create ellipse** objects, il modo corretto per **hide shape in Word**, e come **create hidden shape** codice che funziona con qualsiasi progetto .NET.

## Prerequisiti

* .NET 6.0 SDK o versioni successive installato  
* Visual Studio 2022 (o qualsiasi editor C#)  
* Una licenza Aspose.Words per .NET o una copia di valutazione gratuita  
* Familiarità di base con la sintassi C#  

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Creare un documento Word vuoto con Aspose.Words

Il primo passo è generare un file Word vuoto. Questo ci fornisce una tela pulita dove poter inserire successivamente grafiche nascoste.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();

        // The document is currently empty – it contains no paragraphs or shapes.
        // This is the foundation for all further operations.
```

**Why we start with a blank document** – Partire da un file vuoto garantisce che nessun contenuto indesiderato interferisca con la forma nascosta. Inoltre mantiene la dimensione del file al minimo, il che è utile quando il documento viene successivamente usato come modello.

## Come creare un'ellisse all'interno del documento vuoto

Successivamente abbiamo bisogno di un `DocumentBuilder` per aggiungere contenuti. Il builder ci permette di posizionare le forme esattamente dove desideriamo.

```csharp
        // Step 2: Initialize a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 3: Insert an ellipse shape (width: 100 points, height: 50 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

        // The ellipse now exists on the page, but it is visible by default.
```

**Explanation** – `ShapeType.Ellipse` indica ad Aspose.Words di disegnare una figura approssimativamente circolare. La larghezza e l'altezza sono misurate in punti (1 pt ≈ 1/72 pollice). È possibile regolare questi valori per adattarli alle esigenze del design.

## Nascondere la forma in Word in modo che non appaia nel layout

Una forma nascosta rimane comunque presente nell'XML del documento, il che può essere utile per metadati, formattazione condizionale o modifiche programmatiche successive. Per nasconderla, impostiamo la proprietà `Hidden` su `true`.

```csharp
        // Step 4: Hide the shape so it does not appear in the layout
        ellipse.Hidden = true;

        // When Hidden = true, Word treats the shape as if it were not there.
        // The shape remains in the document’s DOM, allowing you to retrieve or modify it later.
```

**Why hide the shape** – Le forme nascoste sono ignorate dal motore di layout, quindi la pagina appare completamente vuota. Tuttavia, i dati della forma persistono, il che può essere utile per memorizzare marcatori, segnalibri o XML personalizzato che i processi successivi possono leggere.

## Salvare il documento con la forma nascosta

Infine scriviamo il file su disco. Il `.docx` salvato si aprirà in Microsoft Word senza contenuti visibili, ma l'ellisse nascosta sarà ancora presente.

```csharp
        // Step 5: Save the document with the hidden shape
        doc.Save(@"C:\Temp\HiddenEllipse.docx");

        // The file now contains a hidden ellipse and appears empty when opened.
    }
}
```

**Verification** – Apri il file generato in Word, poi premi `Alt+F9` per attivare/disattivare i codici campo e `Ctrl+A` → `Ctrl+Shift+F9` per visualizzare gli oggetti nascosti. Vedrai l'ellisse nell'XML del documento (`word/document.xml`) ma nulla nella pagina.

---

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in un nuovo progetto console. Include tutte le direttive `using` e il metodo `Main` in modo da poterlo eseguire senza ulteriori scaffolding.

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
            // 1️⃣ Create a new blank Word document
            Document doc = new Document();

            // 2️⃣ Prepare a builder to insert content
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Insert an ellipse (100 pt × 50 pt)
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);

            // 4️⃣ Hide the ellipse so the page stays empty
            ellipse.Hidden = true;

            // 5️⃣ Save the file
            string outPath = @"C:\Temp\HiddenEllipse.docx";
            doc.Save(outPath);

            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

**Expected output** – Quando esegui il programma, la console stampa il percorso del file e il file Word risultante non contiene oggetti visibili. Se ispezioni il documento con uno strumento zip (`.docx` è un archivio zip), troverai l'elemento `<w:pict>` che descrive l'ellisse all'interno di `word/document.xml`.

---

## Variazioni comuni e casi limite

| Scenario | Cosa cambiare | Perché è importante |
|----------|----------------|----------------|
| **Different shape** | Sostituire `ShapeType.Ellipse` con `ShapeType.Rectangle`, `ShapeType.Line`, ecc. | Consente di nascondere altre grafiche mantenendo lo stesso flusso di lavoro. |
| **Multiple hidden shapes** | Chiamare `InsertShape` più volte e impostare `Hidden = true` su ciascuna. | Utile per incorporare una collezione di marcatori o segnaposti. |
| **Conditional visibility** | Usare `shape.Visible = false` insieme a `shape.Hidden = true` per una maggiore sicurezza. | Alcune versioni più vecchie di Word gestiscono `Visible` in modo diverso; impostare entrambi copre tutti i casi. |
| **Saving to a stream** | Sostituire `doc.Save(path)` con `doc.Save(stream, SaveFormat.Docx)`. | Consente di inviare il documento direttamente via HTTP o di memorizzarlo in un database. |
| **Applying a style** | Dopo l'inserimento, modificare `ellipse.FillColor`, `ellipse.LineWeight`, ecc. prima di nascondere. | Lo stile della forma è conservato nell'XML, il che può essere utile per successivi un‑hide. |

**Pro tip:** Testare sempre la forma nascosta sulla versione di Word di destinazione (ad es., Word 2019, Word 365) perché occasionalmente possono emergere problemi di rendering quando gli oggetti nascosti interagiscono con layout di pagina complessi.

---

## Domande frequenti

**Q: Nascondere una forma influisce sulla dimensione del documento?**  
A: L'XML della forma aggiunge qualche centinaio di byte, il che è trascurabile per la maggior parte dei casi d'uso. Il file rimane sostanzialmente della stessa dimensione di un documento veramente vuoto.

**Q: Posso rendere visibile la forma in seguito in modo programmatico?**  
A: Sì. Carica il documento, individua la forma (`doc.GetChildNodes(NodeType.Shape, true)`) e imposta `shape.Hidden = false`.

**Q: La forma nascosta appare durante la stampa?**  
A: No. Gli oggetti nascosti sono esclusi dal layout di stampa, quindi la pagina stampata rimane vuota.

**Q: Questo approccio è compatibile solo con Office Open XML (OOXML)?**  
A: La proprietà `Hidden` fa parte della specifica OOXML, quindi qualsiasi elaboratore di testi che implementa completamente OOXML (Word, LibreOffice, Google Docs) rispetterà il flag nascosto.

## Conclusione

Ora sai come **create blank Word document**, **how to create ellipse**, **hide shape in Word** e **create hidden shape** usando Aspose.Words per .NET. Il tutorial ha coperto l'intero ciclo di vita — dall'inizializzazione di un file vuoto all'inserimento, nascondere e salvare la forma — includendo i passaggi di verifica e le variazioni comuni.

Successivamente, potresti esplorare:

* Aggiungere caselle di testo nascoste per metadati (tecnica `hide shape in word` applicata al testo)  
* Usare parti XML personalizzate per memorizzare dati strutturati accanto a forme nascoste  
* Convertire il documento con forma nascosta in PDF mantenendo gli elementi nascosti  

Sperimenta con diverse forme e impostazioni di visibilità per vedere come i contenuti nascosti possono fungere da archivio dati leggero all'interno dei file Word.

Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Word Document with a Shadowed Rectangle – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}