---
category: general
date: 2026-08-23
description: Scopri come raggruppare le forme in C# usando Aspose.Words. La guida
  copre anche come inserire una forma rettangolare e aggiungere forme per documenti
  complessi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- insert rectangle shape
- add shapes word
- group multiple shapes
- how to start group
language: it
lastmod: 2026-08-23
og_description: Come raggruppare le forme in C# con Aspose.Words. Segui questo tutorial
  completo per inserire una forma rettangolare, aggiungere forme a Word e raggruppare
  più forme in modo efficiente.
og_image_alt: How to group shapes in C# using Aspose.Words
og_title: Come raggruppare le forme in C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-08-23'
  description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  headline: How to group shapes in C# with Aspose.Words
  type: TechArticle
- description: Learn how to group shapes in C# using Aspose.Words. The guide also
    covers how to insert rectangle shape and add shapes word for complex documents.
  name: How to group shapes in C# with Aspose.Words
  steps:
  - name: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
    text: '**Nested groups** – Aspose.Words allows groups within groups. To create
      a nested group, call `StartGroupShape` again before calling `EndGroupShape`
      for the inner group.'
  - name: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
    text: '**Empty groups** – If you start a group but never insert a shape, `EndGroupShape`
      will still create an empty container. This is harmless but may increase file
      size slightly.'
  - name: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
    text: '**Compatibility** – The generated DOCX works with Word 2010 and later.
      Older versions may ignore grouping metadata, so always test with the target
      Word version.'
  type: HowTo
- questions:
  - answer: Yes. Retrieve the existing `Shape` objects, call `builder.StartGroupShape()`,
      re‑insert them with `builder.InsertShape(existingShape)`, then call `EndGroupShape()`.
    question: Can I group shapes that already exist in the document?
  - answer: Aspose.Words adds a `<w:grpSp>` element that contains each shape’s `<w:sp>`
      node. This is fully compliant with the Office Open XML specification.
    question: Does grouping affect the underlying XML?
  - answer: 'There is no direct “ungroup” API, but you can iterate through the child
      shapes of the group (`group.GroupShape.Children`) and copy them out to the document
      body. ## Next steps Now that you know **how to group shapes**, consider exploring
      these related topics: - **Apply complex formatting to grouped '
    question: What if I need to ungroup later?
  type: FAQPage
tags:
- Aspose.Words
- C#
- shapes
- document automation
title: Come raggruppare le forme in C# con Aspose.Words
url: /it/net/programming-with-shapes/how-to-group-shapes-in-c-with-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in C# con Aspose.Words

Se hai bisogno di **how to group shapes** in un documento Word in modo programmatico, questo tutorial ti mostra i passaggi esatti usando Aspose.Words per .NET. Che tu stia costruendo un generatore di report, un motore di template o uno strumento di diagrammazione, imparerai come avviare un gruppo, inserire una forma rettangolare e aggiungere contenuti a livello di Word all'interno delle forme senza lasciare il tuo codice.

Vedrai anche come **group multiple shapes** insieme, il che è essenziale quando vuoi spostare, ruotare o formattare una collezione di oggetti come un'unica entità. L'esempio qui sotto funziona con l'ultima versione di Aspose.Words 24.x e richiede solo .NET 6 o versioni successive.

## Prerequisiti

- .NET 6 SDK (o qualsiasi versione .NET supportata da Aspose.Words)
- Visual Studio 2022 o VS Code
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)
- Familiarità di base con C# e il modello oggetto di Aspose.Words

> **Consiglio professionale:** Usa la licenza di valutazione gratuita di Aspose per evitare le limitazioni del watermark durante i test.

## Come raggruppare forme con Aspose.Words

Di seguito trovi un programma completo e eseguibile che dimostra **how to start group**, aggiunge un rettangolo e finalizza il gruppo. Il codice segue lo stesso flusso logico dello snippet fornito, ma aggiunge contesto, gestione degli errori e commenti per chiarezza.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Create a new blank document.
            Document doc = new Document();

            // 2️⃣ Get a DocumentBuilder to insert content.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3️⃣ Start a group shape – all shapes added after this call belong to the group.
            // This is the “how to start group” step.
            Shape group = builder.StartGroupShape();

            // 4️⃣ Insert individual shapes inside the group.
            //    a) Insert a rectangle shape (demonstrates “insert rectangle shape”).
            builder.InsertShape(ShapeType.Rectangle, 150, 80);
            //    b) Insert a simple ellipse for visual variety.
            builder.InsertShape(ShapeType.Ellipse, 100, 60);
            //    c) Add a WordArt‑style text shape – shows “add shapes word”.
            builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            builder.Writeln("Grouped Text"); // adds text inside the last shape

            // 5️⃣ Close the group shape to finalize the grouping.
            builder.EndGroupShape();

            // Optional: Save the document to verify the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Perché ogni passaggio è importante

| Passo | Scopo | Come si relaziona alle parole chiave |
|------|---------|--------------------------------|
| **Create a new blank document** | Fornisce una tela pulita per le operazioni sulle forme. | Prepara il terreno per **add shapes word** in seguito. |
| **Initialize DocumentBuilder** | Il builder è l'API principale per inserire oggetti. | Necessario prima di poter **how to start group**. |
| **StartGroupShape** | Inizia un contenitore logico; tutte le forme successive diventano membri di questo gruppo. | Risponde direttamente a **how to start group**. |
| **InsertShape** (rectangle, ellipse, text) | Posiziona forme individuali all'interno del gruppo. La chiamata al rettangolo soddisfa **insert rectangle shape**; la forma di testo soddisfa **add shapes word**. | Dimostra **group multiple shapes**. |
| **EndGroupShape** | Finalizza il gruppo così puoi spostarlo o formattarlo come un'unità. | Completa il flusso di lavoro **how to group shapes**. |

## Inserire una forma rettangolare – approfondimento

Il metodo `InsertShape` accetta un enum `ShapeType`, larghezza e altezza. Per **insert rectangle shape** con stile personalizzato, puoi estendere l'esempio:

```csharp
// Insert a styled rectangle
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rect.FillColor = System.Drawing.Color.LightBlue;
rect.StrokeColor = System.Drawing.Color.DarkBlue;
rect.LineWidth = 2.0;
```

> **Perché stilizzarlo?** Lo styling garantisce che il rettangolo risalti quando il gruppo viene riposizionato in seguito. Dimostra anche che le proprietà della forma possono essere impostate *prima* della chiusura del gruppo.

## Aggiungere forme a livello Word (add shapes word)

Se devi incorporare testo direttamente all'interno di una forma — comunemente chiamata “WordArt” o “casella di testo” — usa `ShapeType.TextPlainText`. Dopo l'inserimento, puoi scrivere testo nella forma con `DocumentBuilder.Writeln` o accedendo alla proprietà `TextBox` della forma:

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextPlainText, 250, 50);
textBox.TextBox.Text = "Hello, grouped world!";
```

Ciò soddisfa la parola chiave **add shapes word** e mostra come il testo possa viaggiare con il gruppo.

## Raggruppare più forme – scenari pratici

Quando **group multiple shapes**, puoi trattarle come un unico oggetto per posizionamento, rotazione o ridimensionamento. Ad esempio, dopo che il gruppo è chiuso, puoi spostare l'intero gruppo:

```csharp
// Move the entire group 100 points to the right and 50 points down.
group.Left += 100;
group.Top += 50;
```

Oppure ruotare il gruppo:

```csharp
group.Rotation = 45; // degrees
```

Queste operazioni sono possibili solo perché le forme condividono lo stesso gruppo genitore.

## Gestione dei casi limite

1. **Nested groups** – Aspose.Words consente gruppi all'interno di gruppi. Per creare un gruppo annidato, chiama nuovamente `StartGroupShape` prima di chiamare `EndGroupShape` per il gruppo interno.  
2. **Empty groups** – Se avvii un gruppo ma non inserisci mai una forma, `EndGroupShape` creerà comunque un contenitore vuoto. Questo è innocuo ma può aumentare leggermente la dimensione del file.  
3. **Compatibility** – Il DOCX generato funziona con Word 2010 e versioni successive. Le versioni più vecchie potrebbero ignorare i metadati di raggruppamento, quindi testa sempre con la versione di Word di destinazione.

## File sorgente completo per riferimento

Salva quanto segue come `Program.cs` in un progetto console .NET. Il codice compila ed esegue senza modifiche.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document.
            Document doc = new Document();

            // Step 2: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Start the group – “how to start group”.
            Shape group = builder.StartGroupShape();

            // Step 4a: Insert a rectangle – “insert rectangle shape”.
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 150, 80);
            rect.FillColor = System.Drawing.Color.LightCoral;
            rect.StrokeColor = System.Drawing.Color.DarkRed;
            rect.LineWidth = 1.5;

            // Step 4b: Insert an ellipse (additional shape for grouping).
            builder.InsertShape(ShapeType.Ellipse, 100, 60);

            // Step 4c: Add a text box – “add shapes word”.
            Shape txt = builder.InsertShape(ShapeType.TextPlainText, 200, 40);
            txt.TextBox.Text = "Grouped Text";

            // Step 5: End the group – completes “how to group shapes”.
            builder.EndGroupShape();

            // Optional: Adjust group position.
            group.Left += 50;
            group.Top += 30;

            // Save the result.
            string outPath = "GroupedShapes.docx";
            doc.Save(outPath);
            Console.WriteLine($"Document saved to {outPath}");
        }
    }
}
```

### Output previsto

Aprendo `GroupedShapes.docx` in Microsoft Word vedrai:

- Un rettangolo color corallo chiaro, un'ellisse e una casella di testo—tutti visivamente legati insieme.  
- Selezionando qualsiasi parte del gruppo si seleziona anche l'intero gruppo (compare un unico riquadro di delimitazione).  
- Spostare o ruotare il gruppo sposta tutte e tre le forme insieme.

## Domande frequenti

**D: Posso raggruppare forme che esistono già nel documento?**  
R: Sì. Recupera gli oggetti `Shape` esistenti, chiama `builder.StartGroupShape()`, reinseriscili con `builder.InsertShape(existingShape)`, quindi chiama `EndGroupShape()`.

**D: Il raggruppamento influisce sull'XML sottostante?**  
R: Aspose.Words aggiunge un elemento `<w:grpSp>` che contiene il nodo `<w:sp>` di ogni forma. Questo è pienamente conforme alla specifica Office Open XML.

**D: E se devo separare il gruppo in seguito?**  
R: Non esiste un'API “ungroup” diretta, ma puoi iterare le forme figlie del gruppo (`group.GroupShape.Children`) e copiarle nel corpo del documento.

## Prossimi passi

Ora che conosci **how to group shapes**, considera di esplorare questi argomenti correlati:

- **Apply complex formatting to grouped shapes** – impara a impostare riempimenti a gradiente, effetti ombra e stili di linea.  
- **Export grouped shapes as images** – usa `Shape.GetShapeRenderer().Save(...)` per rasterizzare un gruppo.  
- **Create dynamic diagrams** – combina il posizionamento guidato dai dati con il raggruppamento per generare automaticamente diagrammi di flusso.

Ognuno di questi si basa sulle basi trattate qui e ti aiuterà a creare documenti Word più ricchi e interattivi.

---

*Buon coding! Se hai trovato utile questa guida, condividila con i colleghi o metti una stella al repository che contiene il progetto di esempio.*

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserire forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Creare forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Creare forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}