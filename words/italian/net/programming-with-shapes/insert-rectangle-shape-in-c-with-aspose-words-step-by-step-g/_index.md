---
category: general
date: 2026-08-07
description: Inserisci una forma rettangolare in C# usando Aspose.Words e scopri come
  nascondere la forma, impostare il colore di riempimento e aggiungere la forma rettangolare
  a un documento Word in modo efficiente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- insert rectangle shape
- how to hide shape
- how to insert shape
- how to set fill color
- add rectangle shape
language: it
lastmod: 2026-08-07
og_description: Inserisci una forma rettangolare in un documento Word con C#. Scopri
  come nascondere la forma, impostare il colore di riempimento e aggiungere una forma
  rettangolare usando Aspose.Words.
og_image_alt: Screenshot showing a hidden yellow rectangle shape inserted into a Word
  document
og_title: Inserisci forma rettangolare in C# – tutorial completo di Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-08-07'
  description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  headline: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  type: TechArticle
- description: Insert rectangle shape in C# using Aspose.Words and learn how to hide
    shape, set fill color, and add rectangle shape to a Word document efficiently.
  name: Insert rectangle shape in C# with Aspose.Words – step‑by‑step guide
  steps:
  - name: What each step does
    text: '| Step | Reason | |------|--------| | **Create a new document** | Provides
      a clean canvas; you can also load an existing .docx by passing a file path to
      `new Document(path)`. | | **Initialize DocumentBuilder** | `DocumentBuilder`
      is the high‑level helper that lets you insert text, tables, and shapes'
  - name: 1. Making the shape visible again
    text: 'If a later part of your workflow needs to reveal the hidden rectangle,
      you can toggle the flag:'
  - name: 2. Adding a border (stroke)
    text: 'A hidden shape can still have a visible border when you decide to show
      it. Set the `LineColor` and `LineWidth` properties:'
  - name: 3. Positioning the rectangle absolutely
    text: 'For precise layout control, switch the shape’s `WrapType` to `WrapType.Inline`
      (default) or `WrapType.TopBottom` and adjust `Left`/`Top` properties:'
  - name: 4. Using a different measurement unit
    text: 'Aspose.Words works in points (1 pt = 1/72 inch). If you prefer centimeters,
      convert first:'
  - name: Next steps
    text: '* Explore **how to insert shape** inside tables or headers/footers for
      watermarks. * Combine **add rectangle shape** with content controls to create
      dynamic placeholders. * Review Aspose.Words’ **shape manipulation** API for
      advanced features like rotation, gradient fills, and SVG import.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- shapes
- document generation
title: Inserisci una forma rettangolare in C# con Aspose.Words – guida passo passo
url: /it/net/programming-with-shapes/insert-rectangle-shape-in-c-with-aspose-words-step-by-step-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Inserire forma rettangolare in C# con Aspose.Words – guida passo‑passo

Se hai bisogno di **inserire forma rettangolare** in un documento Word da C#, questa guida ti mostra esattamente come farlo. Vedrai come impostare il colore di riempimento, nascondere la forma in modo che non appaia nel layout finale e salvare il file—tutto con poche righe di codice.

Nelle sezioni seguenti copriamo tutto ciò che devi sapere: prerequisiti, l'elenco completo del codice, spiegazioni per ogni passaggio e consigli per variazioni comuni come rendere nuovamente visibile la forma o utilizzare un colore diverso. Alla fine sarai in grado di **aggiungere forma rettangolare** a qualsiasi file .docx in modo programmatico.

## Prerequisiti

* **Aspose.Words for .NET** (versione 23.10 o successiva). Puoi installarlo tramite NuGet:

  ```bash
  dotnet add package Aspose.Words
  ```

* .NET 6.0 SDK o successivo installato sulla tua macchina.
* Una conoscenza di base di C# e Visual Studio (o di qualsiasi IDE tu preferisca).

Non sono richieste librerie aggiuntive—le API relative alle forme fanno parte del pacchetto core di Aspose.Words.

## Inserire forma rettangolare con Aspose.Words

Il cuore della soluzione è un breve programma autonomo che crea un documento vuoto, inserisce un rettangolo, lo colora, lo nasconde e poi salva il file. Di seguito trovi il codice sorgente completo con commenti in linea che spiegano il *perché* di ogni riga.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Required for Color struct

// 1️⃣ Create a new, empty Word document.
Document document = new Document();

// 2️⃣ Obtain a DocumentBuilder – the primary API for editing the document.
DocumentBuilder builder = new DocumentBuilder(document);

// 3️⃣ Insert a rectangle shape of 100 × 50 points.
//    ShapeType.Rectangle tells Aspose.Words to create a simple rectangular drawing object.
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Set the shape's fill color to yellow.
//    The FillColor property accepts a System.Drawing.Color value.
rectangleShape.FillColor = Color.Yellow;

// 5️⃣ Hide the shape so it does not appear in the rendered document.
//    When Hidden = true, the shape is stored in the file but omitted from layout.
//    This is useful for placeholders, bookmarks, or metadata.
rectangleShape.Hidden = true;

// 6️⃣ Save the document to disk.
//    Change the path to a folder you have write access to.
document.Save(@"C:\Temp\HiddenRectangleShape.docx");
```

### Cosa fa ogni passaggio

| Passo | Motivo |
|------|--------|
| **Create a new document** | Fornisce una tela pulita; è anche possibile caricare un .docx esistente passando un percorso file a `new Document(path)`. |
| **Initialize DocumentBuilder** | `DocumentBuilder` è l'helper di alto livello che consente di inserire testo, tabelle e forme senza occuparsi degli alberi di nodi a basso livello. |
| **Insert rectangle shape** | Il metodo `InsertShape` restituisce un oggetto `Shape` che può essere ulteriormente personalizzato (dimensioni, posizione, bordi, ecc.). |
| **Set fill color** | La proprietà `FillColor` controlla il colore interno; è possibile usare qualsiasi valore `Color` (`Color.Red`, `Color.FromArgb(255, 0, 255, 0)`, ecc.). |
| **Hide the shape** | `Hidden = true` indica a Word di ignorare la forma durante il layout mantenendola comunque nel XML del documento. Questo è il modo standard per memorizzare oggetti invisibili. |
| **Save the document** | Salva le modifiche in un file .docx. Il file salvato conterrà la forma rettangolare nascosta. |

## Come impostare il colore di riempimento per una forma

Cambiare il colore di riempimento è semplice come assegnare un `System.Drawing.Color` alla proprietà `FillColor`. Se ti serve una tonalità personalizzata, usa `Color.FromArgb`:

```csharp
// Example: set a semi‑transparent teal fill
rectangleShape.FillColor = Color.FromArgb(128, 0, 128, 128);
```

*Perché è importante*: Il colore di riempimento è memorizzato nell'XML della forma (`<w:fill>` attribute). Quando la forma è nascosta, il colore rimane, il che può essere utile per l'elaborazione successiva (ad esempio, estrarre metadati basati sui codici colore).

## Come nascondere la forma nel documento finale

Il flag `Hidden` è una proprietà booleana della classe `Shape`. Impostandola su `true` garantisce che la forma venga ignorata dal motore di layout di Word.

```csharp
rectangleShape.Hidden = true;
```

**Errori comuni**

* **Hidden vs. Visible** – Se in seguito hai bisogno che la forma appaia, imposta semplicemente `Hidden = false`.
* **Compatibility** – Le versioni più vecchie di Word (pre‑2007) potrebbero trattare gli oggetti di disegno nascosti in modo diverso. Aspose.Words mantiene la compatibilità memorizzando il flag nell'elemento OOXML appropriato.

## Come inserire una forma programmaticamente

Sebbene l'esempio utilizzi un rettangolo, lo stesso metodo `InsertShape` funziona per molte altre forme (ellisse, triangolo, linea, ecc.). Il primo argomento è un valore enum `ShapeType`:

```csharp
// Insert an ellipse with the same dimensions
Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 100, 50);
ellipse.FillColor = Color.LightBlue;
```

**Suggerimento**: Se devi posizionare la forma in una posizione specifica della pagina, usa `builder.MoveTo` per impostare il punto di inserimento prima di chiamare `InsertShape`.

## Aggiungere forma rettangolare a un documento esistente

Spesso potresti voler migliorare un modello anziché partire da zero. Sostituisci il passo 1 con:

```csharp
// Load an existing .docx file
Document document = new Document(@"C:\Templates\ReportTemplate.docx");
```

Tutti i passaggi successivi rimangono identici, e il rettangolo verrà aggiunto ovunque il cursore del builder sia posizionato (di solito alla fine del documento per impostazione predefinita).

## Gestione di casi limite e variazioni

### 1. Rendere nuovamente visibile la forma

Se una fase successiva del tuo flusso di lavoro deve rivelare il rettangolo nascosto, puoi commutare il flag:

```csharp
rectangleShape.Hidden = false;   // Shape will now be rendered
```

### 2. Aggiungere un bordo (stroke)

Una forma nascosta può comunque avere un bordo visibile quando decidi di mostrarla. Imposta le proprietà `LineColor` e `LineWidth`:

```csharp
rectangleShape.LineColor = Color.Black;
rectangleShape.LineWeight = 1.5; // points
```

### 3. Posizionare il rettangolo in modo assoluto

Per un controllo preciso del layout, imposta il `WrapType` della forma su `WrapType.Inline` (predefinito) o `WrapType.TopBottom` e regola le proprietà `Left`/`Top`:

```csharp
rectangleShape.WrapType = WrapType.TopBottom;
rectangleShape.Left = 72;   // 1 inch from the left margin
rectangleShape.Top = 144;   // 2 inches from the top margin
```

### 4. Utilizzare un'unità di misura diversa

Aspose.Words lavora in punti (1 pt = 1/72 pollice). Se preferisci i centimetri, converti prima:

```csharp
float cmToPoints = 28.3465f; // 1 cm ≈ 28.3465 pt
float width = 5 * cmToPoints;   // 5 cm wide
float height = 2 * cmToPoints;  // 2 cm tall
Shape cmRectangle = builder.InsertShape(ShapeType.Rectangle, width, height);
```

## Esempio completo eseguibile

Di seguito trovi il programma *completo* che puoi copiare, incollare ed eseguire. Include tutte le direttive `using` necessarie e utilizza percorsi assoluti che dovrai adattare al tuo ambiente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class InsertRectangleShapeDemo
{
    static void Main()
    {
        // Create a blank document.
        Document doc = new Document();

        // Use DocumentBuilder to edit the document.
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a 100 × 50 pt rectangle.
        Shape rect = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // Set the fill color to yellow.
        rect.FillColor = Color.Yellow;

        // Hide the shape so it does not affect layout.
        rect.Hidden = true;

        // Save the result.
        string outputPath = @"C:\Temp\HiddenRectangleShape.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Risultato atteso**: Il file `HiddenRectangleShape.docx` si apre in Microsoft Word senza *alcuna forma visibile*, ma il rettangolo nascosto è presente nell'XML del documento. Puoi verificarne l'esistenza aprendo il .docx come archivio zip e ispezionando `word/document.xml` per un elemento `<w:shape>` con gli attributi `w:fill="yellow"` e `w:hidden="true"`.

## Conclusione

Ora sai come **inserire forma rettangolare** in un documento Word usando C# e Aspose.Words, come **impostare il colore di riempimento** e come **nascondere la forma** in modo che rimanga invisibile nel layout finale. Lo stesso schema funziona per altri tipi di forma, colori personalizzati e modelli esistenti. Sperimenta con i bordi, il posizionamento assoluto e diverse unità di misura per adattare la forma alle tue esigenze precise.

### Prossimi passi

* Esplora **come inserire forma** all'interno di tabelle o intestazioni/piè di pagina per filigrane.
* Combina **aggiungere forma rettangolare** con i controlli di contenuto per creare segnaposti dinamici.
* Consulta l'API di **manipolazione forme** di Aspose.Words per funzionalità avanzate come rotazione, riempimenti a gradiente e importazione SVG.

Sentiti libero di adattare il codice al tuo progetto e facci sapere nei commenti quale sfida legata alle forme hai risolto successivamente!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Ombra Forma Aspose.Words – Aggiungi un'ombra alla forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Crea Forma di Gruppo in Documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}