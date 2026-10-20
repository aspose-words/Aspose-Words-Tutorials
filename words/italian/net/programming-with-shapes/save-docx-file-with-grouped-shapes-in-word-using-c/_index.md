---
category: general
date: 2026-08-04
description: Salva un file docx programmaticamente aggiungendo una forma rettangolare
  e raggruppando forme in Word. Impara a impostare le dimensioni della forma e a creare
  una casella di testo programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- save docx file
- add rectangle shape
- group shapes word
- set shape dimensions
- create textbox programmatically
language: it
lastmod: 2026-08-04
og_description: Salva un file docx usando C# aggiungendo una forma rettangolare, raggruppando
  le forme in Word, impostando le dimensioni della forma e creando una casella di
  testo programmaticamente.
og_image_alt: Screenshot of a saved docx file that contains a grouped rectangle and
  textbox
og_title: Salva file docx con forme raggruppate in Word – Guida passo‑passo C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  headline: Save docx file with grouped shapes in Word using C#
  type: TechArticle
- description: Save docx file programmatically while add rectangle shape and group
    shapes in Word. Learn to set shape dimensions and create textbox programmatically.
  name: Save docx file with grouped shapes in Word using C#
  steps:
  - name: 1. Create a new document and a builder
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing; using Aspose.Words.Drawing.Shapes;'
  - name: 2. Add rectangle shape to a group
    text: '```csharp // Create a group container that will hold all shapes. GroupShape
      group = new GroupShape(doc) { Width = 400, // Set shape dimensions for the group.
      Height = 200 };'
  - name: 3. Group shapes in Word document
    text: The `GroupShape` class aggregates multiple drawing objects. Grouping is
      useful when you want to treat several objects as a single unit (e.g., moving,
      rotating, or copying them together).
  - name: 4. Set shape dimensions for precise layout
    text: Both the group and its child shapes need explicit dimensions; otherwise
      Word applies default sizes that may not match your design.
  - name: 5. Create textbox programmatically inside the group
    text: '```csharp // Add a textbox shape with custom text. Shape textBox = new
      Shape(doc, ShapeType.TextBox) { Width = 180, Height = 100, Left = 210, // Position
      relative to the group’s coordinate system. Top = 10 };'
  - name: 6. Insert group shape and **save docx file**
    text: '```csharp // Insert the completed group into the document at the current
      cursor position. builder.InsertNode(group);'
  - name: Expected output
    text: '* A file named **GroupShape.docx** appears in the output directory. * Opening
      the file shows a rectangular shape on the left and a textbox containing “Grouped
      text” on the right, both locked together. * Selecting either shape moves the
      entire group, confirming that **group shapes word** functionalit'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Salva file docx con forme raggruppate in Word usando C#
url: /it/net/programming-with-shapes/save-docx-file-with-grouped-shapes-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Salva file docx con forme raggruppate in Word usando C#

Se hai bisogno di **save docx file** che contiene diverse forme disposte insieme, questa guida ti mostra come farlo con C#. Imparerai come **add rectangle shape**, raggruppare più forme in un documento Word, **set shape dimensions**, e **create textbox programmatically**. La soluzione funziona con l'ultima versione di Aspose.Words per .NET e gira su .NET 6 o versioni successive.

Il tutorial percorre ogni passaggio, dalla configurazione del progetto alla chiamata finale `doc.Save`. Alla fine avrai uno snippet di codice riutilizzabile che potrai incollare in qualsiasi progetto console o ASP.NET. Non sono necessari script esterni né modifiche manuali del file DOCX.

## Prerequisiti

* .NET 6 SDK (o più recente) installato.
* Una licenza valida per **Aspose.Words for .NET** (la versione di prova gratuita funziona per i test).
* Visual Studio 2022, VS Code, o qualsiasi IDE in grado di compilare progetti .NET.

Il codice utilizza solo lo spazio dei nomi Aspose.Words, quindi non sono necessari pacchetti NuGet aggiuntivi.

## Salva file docx con forme raggruppate in Word

Il cuore della soluzione consiste nel creare un `GroupShape` che contiene un rettangolo e una casella di testo, quindi inserire il gruppo nel documento e chiamare `doc.Save`. Le sezioni seguenti suddividono il processo in parti gestibili.

### 1. Crea un nuovo documento e un builder

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // Initialize a blank document.
        Document doc = new Document();

        // DocumentBuilder provides convenient methods for editing the document.
        DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché questo passaggio è importante* – Un nuovo oggetto `Document` rappresenta un file *.docx* vuoto. `DocumentBuilder` fornisce metodi di alto livello come `InsertNode`, che utilizzeremo per posizionare la forma di gruppo.

### 2. Aggiungi forma rettangolare a un gruppo

```csharp
        // Create a group container that will hold all shapes.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,   // Set shape dimensions for the group.
            Height = 200
        };

        // Add a rectangle shape that will be part of the group.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,   // Set shape dimensions for the rectangle.
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);
```

*Perché questo passaggio è importante* – L'operazione **add rectangle shape** dimostra come definire un elemento visivo con dimensioni e posizione precise. Il rettangolo vive all'interno di `group`, quindi spostare il gruppo in seguito sposta automaticamente il rettangolo.

### 3. Raggruppa forme in un documento Word

La classe `GroupShape` aggrega più oggetti di disegno. Il raggruppamento è utile quando si desidera trattare diversi oggetti come un'unica unità (ad esempio, spostarli, ruotarli o copiarli insieme).

```csharp
        // The group now contains the rectangle; we will add more shapes next.
```

*Perché raggruppiamo* – Il raggruppamento riduce la complessità del layout. Invece di posizionare ogni forma singolarmente sulla pagina, si regola una sola volta `Left`, `Top`, `Width` e `Height` del gruppo.

### 4. Imposta le dimensioni della forma per un layout preciso

Sia il gruppo sia le sue forme figlie necessitano di dimensioni esplicite; altrimenti Word applica dimensioni predefinite che potrebbero non corrispondere al tuo design.

```csharp
        // Example of adjusting the group’s overall size.
        group.Width = 400;   // Overall width of the grouped area.
        group.Height = 200;  // Overall height of the grouped area.
```

*Perché impostiamo le dimensioni* – Una misurazione precisa garantisce che il rettangolo e la casella di testo non si sovrappongano involontariamente e che il risultato finale **save docx file** corrisponda al layout previsto.

### 5. Crea casella di testo programmaticamente all'interno del gruppo

```csharp
        // Add a textbox shape with custom text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,   // Position relative to the group’s coordinate system.
            Top = 10
        };

        // Populate the textbox with a paragraph containing a run.
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);

        // Append the textbox to the same group.
        group.AppendChild(textBox);
```

*Perché questo passaggio è importante* – Il segmento **create textbox programmatically** mostra come incorporare testo formattato all'interno di una forma. L'uso di `Paragraph` e `Run` ti dà pieno controllo sulla formattazione in seguito.

### 6. Inserisci forma di gruppo e **save docx file**

```csharp
        // Insert the completed group into the document at the current cursor position.
        builder.InsertNode(group);

        // Save the document to the file system.
        doc.Save("GroupShape.docx");   // The file now contains a rectangle and a textbox grouped together.
    }
}
```

*Perché questo passaggio finale è importante* – La chiamata `InsertNode` posiziona le forme raggruppate esattamente dove si trova il cursore del builder. Il metodo `doc.Save` esegue l'operazione **save docx file**, scrivendo su disco un documento Word completo.

> **Risultato:** Aprendo *GroupShape.docx* in Microsoft Word viene visualizzato un rettangolo a sinistra e una casella di testo a destra, entrambi bloccati insieme all'interno di un unico gruppo. Puoi spostare il gruppo come un'unità, ridimensionarlo o applicare formattazioni aggiuntive.

## Esempio completo, eseguibile

Copia il codice qui sotto in un nuovo progetto console (`dotnet new console`) ed esegui `dotnet run`. Il programma crea `GroupShape.docx` nella cartella di output del progetto.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

class Program
{
    static void Main()
    {
        // 1. Initialize document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Create a group shape container.
        GroupShape group = new GroupShape(doc)
        {
            Width = 400,
            Height = 200
        };

        // 3. Add rectangle shape.
        Shape rectangle = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 180,
            Height = 100,
            Left = 10,
            Top = 10
        };
        group.AppendChild(rectangle);

        // 4. Add textbox shape with text.
        Shape textBox = new Shape(doc, ShapeType.TextBox)
        {
            Width = 180,
            Height = 100,
            Left = 210,
            Top = 10
        };
        Paragraph paragraph = new Paragraph(doc);
        Run run = new Run(doc, "Grouped text");
        paragraph.AppendChild(run);
        textBox.AppendChild(paragraph);
        group.AppendChild(textBox);

        // 5. Insert the group into the document.
        builder.InsertNode(group);

        // 6. Save the document.
        doc.Save("GroupShape.docx");
    }
}
```

### Output previsto

* Un file chiamato **GroupShape.docx** appare nella directory di output.
* Aprendo il file si vede una forma rettangolare a sinistra e una casella di testo contenente “Grouped text” a destra, entrambi bloccati insieme.
* Selezionando una delle forme si sposta l'intero gruppo, confermando che la funzionalità **group shapes word** funziona come previsto.

## Varianti comuni e casi limite

| Situazione | Raccomandazione |
|-----------|----------------|
| Need more than two shapes | Append additional `Shape` objects to `group` before calling `builder.InsertNode`. |
| Want the group to appear on a specific page | Move the builder’s cursor with `builder.MoveToDocumentEnd()` or `builder.MoveToPage(pageNumber)`. |
| Require different units (e.g., centimeters) | Use `ConvertUtil.InchToPoint(1.0)` to convert inches to points, the unit Word expects. |
| Want the textbox to wrap text | Set `textBox.TextBoxWrap = TextBoxWrapType.Square` after creating the textbox. |
| Working with older .NET Framework versions | The same API works with .NET Framework 4.7+, but ensure you reference the correct Aspose.Words version. |

**Suggerimento:** Imposta sempre la `Width` e l'`Height` del gruppo *dopo* aver aggiunto tutte le forme figlie. Questo garantisce che il gruppo racchiuda completamente i suoi contenuti, evitando il ritaglio quando il documento viene aperto in Word.

## Conclusione

Ora sai come **save docx file** mentre **add rectangle shape**, **group shapes word**, **set shape dimensions**, e **create textbox programmatically** usando Aspose.Words per .NET. L'esempio completo dimostra un modello pulito e ripetibile che puoi adattare a layout più complessi, come grafici, immagini,

## Cosa dovresti imparare dopo?

I tutorial seguenti coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crea Group Shape in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Tutorial ombra forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}