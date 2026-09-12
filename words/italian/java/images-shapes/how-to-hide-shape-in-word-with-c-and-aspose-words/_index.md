---
category: general
date: 2026-09-11
description: Scopri come nascondere una forma in Word usando C#. Questa guida mostra
  anche come inserire una forma rettangolare e inserire una forma in un documento
  Word con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to hide shape in word
- insert rectangle shape
- insert shape into word document
language: it
lastmod: 2026-09-11
og_description: Come nascondere una forma in Word usando C# e Aspose.Words. Segui
  il tutorial passo‑passo per inserire una forma rettangolare e gestire le forme in
  un documento Word.
og_image_alt: Screenshot showing how to hide shape in Word document using C#
og_title: Come nascondere una forma in Word – guida completa a C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  headline: How to hide shape in Word with C# and Aspose.Words
  type: TechArticle
- description: Learn how to hide shape in Word using C#. This guide also shows how
    to insert rectangle shape and insert shape into Word document with Aspose.Words.
  name: How to hide shape in Word with C# and Aspose.Words
  steps:
  - name: Explanation of each step
    text: 1. **Create a new document** – `Document` represents the Word file in memory.
      `DocumentBuilder` provides a fluent API for inserting content. 2. **Insert rectangle
      shape** – `InsertShape` creates a drawing object of type `Rectangle`. The dimensions
      are expressed in points (1 pt ≈ 1/72 in). This satis
  - name: Expected result
    text: 'Open `output.docx` in Microsoft Word:'
  - name: Manually adding the hidden attribute (fallback)
    text: '```csharp // Fallback for Aspose.Words versions prior to 24.10 Shape shape
      = builder.InsertShape(ShapeType.Rectangle, 100, 50); shape.FillColor = System.Drawing.Color.LightGray;'
  type: HowTo
- questions:
  - answer: No. Hidden shapes are ignored by the layout engine, so they do not consume
      space. This is useful for placeholder content that should not affect page breaks.
    question: Does hiding a shape affect pagination?
  - answer: Yes. The same `Hidden` property works on shapes located anywhere in the
      document tree, including headers, footers, and even inside tables.
    question: Can I hide a shape that is part of a header or footer?
  - answer: Iterate over the `Document.GetChildNodes(NodeType.Shape, true)` collection
      and set `Hidden = true` for each target shape. ```csharp foreach (Shape s in
      doc.GetChildNodes(NodeType.Shape, true)) { if (s.ShapeType == ShapeType.Rectangle)
      s.Hidden = true; } ```
    question: What if I need to hide multiple shapes at once?
  - answer: 'When converting to PDF, hidden shapes are omitted by default, matching
      Word’s rendering behavior. If you need them in the PDF, you must unhide them
      before conversion. ## Tips and pitfalls * **Pro tip:** Set `shape.WrapType =
      WrapType.None` before hiding if you later plan to unhide the shape without '
    question: Is the hidden attribute preserved when converting to PDF?
  type: FAQPage
tags:
- Aspose.Words
- C#
- Word automation
title: Come nascondere una forma in Word con C# e Aspose.Words
url: /it/java/images-shapes/how-to-hide-shape-in-word-with-c-and-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come nascondere una forma in Word con C# e Aspose.Words

Se hai bisogno di nascondere una forma in Word mantenendola nella struttura del documento, questo tutorial ti mostra esattamente come fare. Utilizzando Aspose.Words per .NET puoi inserire una forma rettangolare, nasconderla e conservare comunque la sua posizione per un'elaborazione successiva.

L'automazione di Word richiede spesso un controllo fine sulle forme — che tu stia generando modelli, preparando report o costruendo un servizio di editing di documenti. Alla fine di questa guida sarai in grado di:

* Inserire una forma rettangolare in un documento Word (`insert rectangle shape`).
* Nascondere qualsiasi forma senza eliminarla (`how to hide shape in word`).
* Salvare il risultato e verificare che la forma nascosta non compaia nella visualizzazione renderizzata (`insert shape into word document`).

L'esempio funziona con Aspose.Words 24.10 o versioni successive e mira a .NET 6.0+, ma i concetti si applicano anche a versioni precedenti.

## Prerequisiti

* **Aspose.Words for .NET** ≥ 24.10. Puoi ottenere una licenza temporanea gratuita dal sito di Aspose.
* **.NET SDK** 6.0 o più recente installato sulla tua macchina.
* Un ambiente di sviluppo come Visual Studio 2022, VS Code o Rider.
* Familiarità di base con C# e il concetto di Word Open XML (opzionale ma utile).

## Come nascondere una forma in Word con Aspose.Words

Di seguito trovi un programma completo e eseguibile che dimostra l'intero flusso di lavoro — dalla creazione di un documento all'inserimento di una forma rettangolare e, infine, al suo nascondimento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HideShapeDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Step 2: Insert a rectangle shape (100 × 50 points) at the current cursor position.
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        // Optional: give the shape a visible fill so you can see it before hiding.
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Hide the shape without removing it from the document.
        // The Hidden property is available starting with Aspose.Words 24.10.
        rectangle.Hidden = true;

        // Step 4: Save the document to disk.
        string outputPath = "output.docx";
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}. The rectangle shape is hidden.");
    }
}
```

### Spiegazione di ogni passaggio

1. **Crea un nuovo documento** – `Document` rappresenta il file Word in memoria. `DocumentBuilder` fornisce un'API fluida per inserire contenuti.
2. **Inserisci una forma rettangolare** – `InsertShape` crea un oggetto di disegno di tipo `Rectangle`. Le dimensioni sono espresse in punti (1 pt ≈ 1/72 in). Questo soddisfa il requisito `insert rectangle shape`.
3. **Nascondi la forma** – Impostare `Shape.Hidden = true` segna la forma come nascosta nel markup Word (`<w:hidden/>`). La forma rimane parte dell'albero del documento, così potrai successivamente renderla visibile o fare riferimento ad essa programmaticamente. Questo è il fulcro di `how to hide shape in word`.
4. **Salva il file** – Il documento viene scritto in `output.docx`. Quando aperto in Microsoft Word, il rettangolo non sarà visibile, ma esiste ancora nell'XML e può essere ispezionato con un visualizzatore ZIP o con l'Open XML SDK.

### Risultato atteso

Apri `output.docx` in Microsoft Word:

* Il documento appare vuoto — nessuna forma visibile.
* Se ispezioni l'XML sottostante (`word/document.xml`) troverai un elemento `<w:pict>` con un attributo `<w:hidden/>`, a conferma che la forma è presente ma nascosta.

```xml
<w:pict>
  <v:shape id="Shape0" style="position:absolute; ...">
    <v:fillcolor>#ADD8E6</v:fillcolor>
    <w:hidden/>
  </v:shape>
</w:pict>
```

La forma nascosta può essere resa nuovamente visibile impostando `Hidden = false` e salvando nuovamente il documento.

## Inserire una forma rettangolare in un documento Word

Mentre l'obiettivo principale è nascondere una forma, molti scenari iniziano con l'inserimento di una forma. Il metodo `InsertShape` supporta numerosi valori di `ShapeType`, tra cui `Rectangle`, `Ellipse`, `Line` e immagini personalizzate.

```csharp
// Example: Insert an ellipse shape and keep it visible.
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
ellipse.FillColor = System.Drawing.Color.Pink;
```

**Perché usare un rettangolo?**  
Un rettangolo fornisce un contenitore pulito, allineato agli assi, che può contenere testo, immagini o altre forme nidificate. È spesso usato come segnaposto per contenuti dinamici come tabelle o grafici. Inserendo prima il rettangolo, mantieni la coerenza del layout anche dopo averlo nascosto.

## Inserire una forma in un documento Word – best practices

Quando `insert shape into word document`, considera quanto segue:

* **Imposta dimensioni esplicite** – Evita di fare affidamento sul ridimensionamento automatico; specifica larghezza e altezza in punti per garantire un layout coerente su tutte le piattaforme.
* **Definisci il posizionamento** – Per impostazione predefinita la forma è ancorata al paragrafo corrente. Usa `builder.MoveTo` o `builder.StartBookmark` per posizionarla con precisione.
* **Applica lo stile in anticipo** – Il colore di riempimento, lo stile della linea e il text wrapping influenzano l'aspetto finale. Anche le forme nascoste beneficiano di uno stile corretto perché il markup rimane invariato.
* **Compatibilità di versione** – La proprietà `Hidden` è disponibile solo da Aspose.Words 24.10 in poi. Se punti a una versione più vecchia, puoi aggiungere manualmente l'attributo `<w:hidden/>` usando l'API `Node`.

### Aggiunta manuale dell'attributo hidden (fallback)

```csharp
// Fallback for Aspose.Words versions prior to 24.10
Shape shape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
shape.FillColor = System.Drawing.Color.LightGray;

// Access the underlying OpenXml node.
var shapeNode = shape.GetChildNodes(NodeType.Any, true)[0];
shapeNode.GetAttributes().Add("w:hidden", "true");
```

## Esempio completo end‑to‑end

Mettendo tutto insieme, ecco un unico programma che:

1. Inserisce una forma rettangolare.
2. Nasconde la forma.
3. Inserisce un'ellisse visibile per contrasto.
4. Salva il documento.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class FullDemo
{
    static void Main()
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert and hide a rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 120, 60);
        rect.FillColor = System.Drawing.Color.LightGreen;
        rect.Hidden = true; // core of how to hide shape in word

        // Insert a visible ellipse to show the difference.
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.FillColor = System.Drawing.Color.Coral;

        // Save the output.
        string filePath = "demo_output.docx";
        doc.Save(filePath);
        Console.WriteLine($"Demo document saved to {filePath}");
    }
}
```

L'esecuzione del programma produce `demo_output.docx`. Quando aperto, vedrai solo l'ellisse corallo; il rettangolo verde è presente nell'XML ma nascosto dalla visualizzazione.

## Domande comuni e casi limite

**D: Nascondere una forma influisce sulla paginazione?**  
R: No. Le forme nascoste sono ignorate dal motore di layout, quindi non consumano spazio. Questo è utile per contenuti segnaposto che non devono influenzare le interruzioni di pagina.

**D: Posso nascondere una forma che fa parte di intestazione o piè di pagina?**  
R: Sì. La stessa proprietà `Hidden` funziona su forme situate ovunque nell'albero del documento, comprese intestazioni, piè di pagina e persino all'interno di tabelle.

**D: E se devo nascondere più forme contemporaneamente?**  
R: Itera sulla collezione `Document.GetChildNodes(NodeType.Shape, true)` e imposta `Hidden = true` per ogni forma target.

```csharp
foreach (Shape s in doc.GetChildNodes(NodeType.Shape, true))
{
    if (s.ShapeType == ShapeType.Rectangle)
        s.Hidden = true;
}
```

**D: L'attributo hidden viene preservato durante la conversione in PDF?**  
R: Durante la conversione in PDF, le forme nascoste vengono omesse per impostazione predefinita, corrispondendo al comportamento di rendering di Word. Se hai bisogno che siano presenti nel PDF, devi renderle visibili prima della conversione.

## Suggerimenti e insidie

* **Pro tip:** Imposta `shape.WrapType = WrapType.None` prima di nascondere se prevedi di renderla visibile in seguito senza disturbare il testo circostante.
* **Attenzione alle versioni più vecchie di Aspose.Words:** La proprietà `Hidden` genera `NotSupportedException` prima della 24.10. Usa l'approccio XML manuale in quel caso.
* **Test:** Apri sempre il `.docx` generato in Word e utilizza “Show XML markup” (scheda Sviluppatore) per verificare che l'attributo `<w:hidden/>` sia presente.

## Conclusione

Ora sai come nascondere una forma in Word usando C# e Aspose.Words, oltre a come inserire una forma rettangolare e inserire forme in un documento Word con pieno controllo sulla visibilità. Sfruttando la proprietà `Hidden` puoi mantenere le forme nel modello del documento per elaborazioni successive, presentando al contempo una vista pulita agli utenti finali.

Successivamente, esplora argomenti correlati come **aggiornare le proprietà delle forme a runtime**, **convertire forme nascoste in immagini**, o **usare l'Open XML SDK per manipolare direttamente gli elementi nascosti**. Queste estensioni approfondiranno le tue competenze.

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑a‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserire forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Creare una forma rettangolare in Word usando C# – Guida passo‑a‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Creare una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}