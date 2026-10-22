---
category: general
date: 2026-09-27
description: Crea programmaticamente un documento Word con una forma di gruppo usando
  Aspose.Words in C#. Segui questa guida passo‑passo per generare il file e apprendere
  consigli utili.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- programmatically create word document
- how to create group shape word
- Aspose.Words group shape
- C# Word automation
- StructuredDocumentTag example
language: it
lastmod: 2026-09-27
og_description: Crea programmaticamente un documento Word con una forma di gruppo
  usando Aspose.Words. Questo tutorial ti guida attraverso il codice C# completo,
  spiega ogni passaggio e mostra il risultato finale.
og_image_alt: Screenshot of a Word document containing a group shape with a text placeholder
og_title: Crea programmaticamente un documento Word con una forma di gruppo – Guida
  C#
schemas:
- author: Aspose
  dateModified: '2026-09-27'
  description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  headline: Programmatically create a Word document with a group shape
  type: TechArticle
- description: Programmatically create a Word document with a group shape using Aspose.Words
    in C#. Follow this step‑by‑step guide to generate the file and learn useful tips.
  name: Programmatically create a Word document with a group shape
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works with .NET Framework 4.7+). - Aspose.Words
      for .NET NuGet package (`Install-Package Aspose.Words`). - A C# IDE such as
      Visual Studio 2022 or VS Code with the C# extension.'
  - name: Expected output screenshot (conceptual)
    text: '``` +-----------------------------------------------------------+ | ┌───────────────────────────────────────────────┐
      | | │ [Enter text here] │ | | └───────────────────────────────────────────────┘
      | +-----------------------------------------------------------+ ```'
  - name: Adding more child shapes
    text: 'You can enrich the group by appending additional drawing objects, such
      as pictures or text boxes:'
  - name: Controlling wrapping style
    text: 'If you need the group shape to stay behind text or to have tight wrapping,
      set the `WrapType` property:'
  - name: 'Edge case: Empty group shape'
    text: A `GroupShape` without children renders as an invisible placeholder. Always
      verify that at least one child (e.g., an SDT or a picture) is added; otherwise
      Word may drop the group during saving.
  - name: Compatibility note
    text: Aspose.Words 23.10+ fully supports `GroupShape` and `StructuredDocumentTag`.
      If you target older versions, the `AppendChild` method may behave differently,
      and you might need to call `UpdatePageLayout` after saving.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Creare programmaticamente un documento Word con una forma di gruppo
url: /it/net/programming-with-shapes/programmatically-create-a-word-document-with-a-group-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Creare programmaticamente un documento Word con una forma di gruppo

Se hai bisogno di **creare programmaticamente un documento Word** che contenga un disegno raggruppato, questa guida ti mostra esattamente come farlo con Aspose.Words per .NET. Che tu stia costruendo un generatore di contratti, un costruttore di report o uno strumento di compilazione di moduli, imparerai il codice C# completo, perché ogni chiamata API è importante e come gestire i casi limite comuni.

Creare una forma di gruppo in Word può sembrare complicato perché il modello a oggetti di Word tratta le forme di gruppo come contenitori per altri oggetti di disegno. Questo tutorial non solo risponde a **come creare documenti Word con forme di gruppo**, ma dimostra anche come incorporare un StructuredDocumentTag (SDT) di testo semplice all'interno del gruppo in modo che la forma possa contenere contenuto modificabile.

## Cosa otterrai

- Inizializzare un nuovo documento Word vuoto con `Document` e `DocumentBuilder`.
- Inserire un `GroupShape` nella posizione corrente del cursore.
- Aggiungere un `StructuredDocumentTag` (SDT) di testo semplice alla forma di gruppo.
- Salvare il file come `.docx` apribile in Microsoft Word.
- Comprendere le proprietà chiave di `GroupShape` e `StructuredDocumentTag` per estensioni future.

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7+).
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`).
- Un IDE C# come Visual Studio 2022 o VS Code con l’estensione C#.

---

## Creare programmaticamente un documento Word – configurare il progetto

1. **Crea un nuovo progetto console**  
   ```bash
   dotnet new console -n WordGroupShapeDemo
   cd WordGroupShapeDemo
   dotnet add package Aspose.Words
   ```
2. **Apri il progetto nel tuo IDE** e sostituisci il contenuto di `Program.cs` con il codice mostrato nelle sezioni successive.

> **Suggerimento professionale:** Mantieni la cartella del progetto pulita; Aspose.Words scrive il file di output nella directory di lavoro a meno che non fornisca un percorso assoluto.

## Step 1: Inizializzare il documento e il builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

// Create a new blank document.
Document doc = new Document();

// DocumentBuilder gives you a cursor to insert nodes.
DocumentBuilder builder = new DocumentBuilder(doc);

// Optional: set the page size or margins if your shape must fit a specific area.
builder.PageSetup.PageWidth = 595;   // A4 width in points
builder.PageSetup.PageHeight = 842;  // A4 height in points
```

**Perché è importante:**  
`Document` rappresenta l’intero file Word, mentre `DocumentBuilder` ti consente di posizionare nuovi elementi senza navigare manualmente l’albero dei nodi. Impostare le dimensioni della pagina fin dall’inizio garantisce che la forma di gruppo non trabocchi dalla pagina.

## Step 2: Inserire un GroupShape nella posizione corrente del cursore

```csharp
// Create an empty GroupShape container.
GroupShape groupShape = new GroupShape(doc)
{
    // Give the group a size that comfortably holds its children.
    Width = 300,
    Height = 150,

    // Position the group relative to the page (you can also use RelativeHorizontalPosition).
    Left = 100,
    Top = 100
};

// Insert the group shape into the document where the builder is currently positioned.
builder.InsertNode(groupShape);
```

**Spiegazione:**  
Un `GroupShape` è un oggetto di disegno che può contenere altre forme, immagini o caselle di testo. Impostando `Width`, `Height`, `Left` e `Top`, controlli il posizionamento esatto sulla pagina. Il metodo `InsertNode` inserisce la forma nel flusso principale del documento, comportandosi come un oggetto fluttuante.

## Step 3: Aggiungere un StructuredDocumentTag (SDT) di testo semplice all’interno del gruppo

```csharp
// Create a plain‑text SDT that will act as a content placeholder.
StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
{
    // Provide a helpful tag title that appears as a tooltip in Word.
    Title = "GroupShapeText",
    // Set default placeholder text.
    PlaceholderName = "Enter text here"
};

// Append the SDT to the group shape's child collection.
groupShape.AppendChild(sdtTag);
```

**Perché usare un SDT?**  
Gli StructuredDocumentTag sono i controlli di contenuto nativi di Word. Permettono agli utenti di modificare il testo direttamente nel documento salvato e possono essere accessibili programmaticamente in seguito per l’estrazione dei dati. Inserire un SDT all’interno di una forma di gruppo ti consente di combinare il raggruppamento visivo con contenuto modificabile.

## Step 4: Salvare il documento

```csharp
// Define the output path – replace with your desired directory.
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShapeDemo.docx");

// Save the document in DOCX format.
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved to: {outputPath}");
```

**Risultato:**  
Aprendo `GroupShapeDemo.docx` in Microsoft Word si vede un rettangolo fluttuante (la forma di gruppo) contenente un segnaposto di testo che recita “Enter text here”. Gli utenti possono fare clic all’interno della forma e digitare direttamente.

### Screenshot di output previsto (concettuale)

```
+-----------------------------------------------------------+
|   ┌───────────────────────────────────────────────┐   |
|   │  [Enter text here]                               │   |
|   └───────────────────────────────────────────────┘   |
+-----------------------------------------------------------+
```

Il riquadro esterno è il `GroupShape`; l’area grigia interna è il `StructuredDocumentTag`.

---

## Come creare forme di gruppo in Word – considerazioni aggiuntive

### Aggiungere altre forme figlio

Puoi arricchire il gruppo aggiungendo ulteriori oggetti di disegno, come immagini o caselle di testo:

```csharp
// Example: add a picture inside the same group.
Shape picture = new Shape(doc, ShapeType.Image)
{
    ImageData = ImageData.FromFile("logo.png"),
    Width = 100,
    Height = 50,
    Left = 10,
    Top = 80
};
groupShape.AppendChild(picture);
```

### Controllare lo stile di avvolgimento

Se hai bisogno che la forma di gruppo rimanga dietro il testo o abbia un avvolgimento stretto, imposta la proprietà `WrapType`:

```csharp
groupShape.WrapType = WrapType.Inline; // Makes the shape behave like a paragraph.
```

### Caso limite: Forma di gruppo vuota

Un `GroupShape` senza figli viene renderizzato come un segnaposto invisibile. Verifica sempre che venga aggiunto almeno un figlio (ad esempio un SDT o un’immagine); altrimenti Word potrebbe eliminare il gruppo durante il salvataggio.

### Nota di compatibilità

Aspose.Words 23.10+ supporta pienamente `GroupShape` e `StructuredDocumentTag`. Se utilizzi versioni precedenti, il metodo `AppendChild` potrebbe comportarsi diversamente e potresti dover chiamare `UpdatePageLayout` dopo il salvataggio.

---

## Esempio completo eseguibile

Copia l’intero frammento qui sotto in `Program.cs` ed esegui il progetto. Il codice include tutti i passaggi sopra in un unico programma autonomo.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.PageSetup.PageWidth = 595;
        builder.PageSetup.PageHeight = 842;

        // 2️⃣ Create and insert a GroupShape.
        GroupShape groupShape = new GroupShape(doc)
        {
            Width = 300,
            Height = 150,
            Left = 100,
            Top = 100
        };
        builder.InsertNode(groupShape);

        // 3️⃣ Add a plain‑text StructuredDocumentTag (SDT) inside the group.
        StructuredDocumentTag sdtTag = new StructuredDocumentTag(doc, SdtType.PlainText, true)
        {
            Title = "GroupShapeText",
            PlaceholderName = "Enter text here"
        };
        groupShape.AppendChild(sdtTag);

        // 4️⃣ Optional: add a picture to demonstrate multiple children.
        // Uncomment and adjust the path if you want to test this.
        /*
        Shape picture = new Shape(doc, ShapeType.Image)
        {
            ImageData = ImageData.FromFile("logo.png"),
            Width = 100,
            Height = 50,
            Left


## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}