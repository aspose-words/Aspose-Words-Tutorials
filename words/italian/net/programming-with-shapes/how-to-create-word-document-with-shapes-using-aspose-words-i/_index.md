---
category: general
date: 2026-09-11
description: Scopri come creare un documento Word, aggiungere una forma rettangolare
  e impostare le dimensioni della forma con Aspose.Words. Guida passo‑passo in C#
  per dimensionare le forme con precisione.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- add rectangle shape
- set shape size
- create shapes in word
- set shape dimensions
language: it
lastmod: 2026-09-11
og_description: Crea un documento Word con Aspose.Words in C#. Questa guida mostra
  come aggiungere una forma rettangolare, impostare le dimensioni della forma e gestire
  le dimensioni della forma programmaticamente.
og_image_alt: Screenshot of a rectangle shape inside a grouped shape in a newly created
  Word document
og_title: Crea documento Word con forme – tutorial Aspose.Words C#
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document, add rectangle shape, and set shape
    dimensions with Aspose.Words. Step‑by‑step C# guide for precise shape sizing.
  headline: How to create word document with shapes using Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Come creare un documento Word con forme utilizzando Aspose.Words in C#
url: /it/net/programming-with-shapes/how-to-create-word-document-with-shapes-using-aspose-words-i/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word con forme usando Aspose.Words in C#

Se hai bisogno di **create word document** che contiene grafiche personalizzate, puoi farlo interamente con il codice. Questo tutorial ti guida nella creazione di un file Word, nell'aggiunta di una forma rettangolare e nel controllo di ogni dimensione della forma. Alla fine avrai uno snippet riutilizzabile da inserire in qualsiasi progetto .NET.

Imparerai come **add rectangle shape**, **set shape size**, e **set shape dimensions** all'interno di un contenitore raggruppato. L'esempio utilizza Aspose.Words 13.9, ma i concetti si applicano anche alle versioni successive. Non è necessaria alcuna esperienza pregressa con l'API di disegno di Aspose—basta una conoscenza di base di C#.

## Prerequisiti

- .NET 6.0 o versioni successive installate  
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)  
- Un IDE come Visual Studio 2022 (qualsiasi editor che supporta C# funziona)  

Avere questi strumenti pronti ti consente di eseguire il codice immediatamente senza configurazioni aggiuntive.

## Passo 1: Initialize the document and builder – create word document basics

La prima operazione è istanziare un oggetto `Document` e un `DocumentBuilder`. Il `Document` rappresenta il file stesso, mentre il `DocumentBuilder` fornisce un'API fluida per inserire contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Create a new, empty Word document
        Document doc = new Document();

        // DocumentBuilder gives us a cursor to insert nodes
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:**  
Creare il documento in anticipo ti fornisce una tela pulita. Il cursore del builder inizia al primo paragrafo, che è dove più tardi **create shapes in word**.

## Passo 2: Build a GroupShape to hold multiple graphics

Un `GroupShape` funziona come un contenitore; puoi spostare, ruotare o ridimensionare l'intero gruppo come un'unica unità. Qui definiamo la larghezza e l'altezza del contenitore in punti (1 pt ≈ 1/72 in).

```csharp
        // Define a group that is 300 pt wide and 200 pt high
        GroupShape group = new GroupShape(doc, 300, 200);

        // Position the group 50 pt from the left and top margins
        group.Left = 50;
        group.Top  = 50;
```

**Perché è importante:**  
Raggruppare le forme semplifica la gestione del layout. Se più tardi dovrai aggiungere altre forme (ad es., cerchi o caselle di testo), erediteranno la posizione e la scala del gruppo.

## Passo 3: Create a rectangle shape and configure its dimensions

Ora aggiungiamo il rettangolo effettivo. Il costruttore `Shape` richiede il riferimento al documento e il tipo di forma. Dopo la creazione impostiamo esplicitamente **set shape size** e **set shape dimensions**.

```csharp
        // Create a rectangle shape
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);

        // Set the rectangle’s width to 100 pt and height to 50 pt
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height

        // Position the rectangle 10 pt from the group’s left/top edges
        rectangle.Left = 10;
        rectangle.Top  = 10;
```

**Perché è importante:**  
Specificare larghezza, altezza, sinistra e alto ti dà un controllo pixel‑perfect sulla forma. Questo è essenziale quando il documento deve corrispondere a una specifica di design o a un modulo stampato.

## Passo 4: Assemble the group by appending the rectangle

Aggiungere il rettangolo al `GroupShape` lo rende un nodo figlio. Puoi aggiungere quanti figli desideri prima di inserire il gruppo nel documento.

```csharp
        // Add the rectangle to the group
        group.AppendChild(rectangle);
```

**Suggerimento:** Se prevedi di aggiungere una seconda forma, creala allo stesso modo e chiama `group.AppendChild(secondShape)`. Tutti i figli condividono il sistema di coordinate del gruppo.

## Passo 5: Insert the grouped shape into the document and save

Con il gruppo completamente costruito, lo inseriamo nel paragrafo corrente. La proprietà `CurrentParagraph` del builder fornisce accesso diretto all'albero dei nodi sottostante.

```csharp
        // Insert the group into the first paragraph of the document
        builder.CurrentParagraph.AppendChild(group);

        // Save the document to disk (adjust the path as needed)
        doc.Save("GroupShape.docx");

        // Optional: open the file automatically (Windows only)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Perché è importante:**  
Aggiungere il gruppo a un paragrafo garantisce che la forma appaia in linea con il flusso del testo. Salvare il documento finalizza l'operazione **create word document**.

## Variazioni comuni e casi limite

| Scenario | Adjustment |
|----------|------------|
| **Different page orientation** | Imposta `doc.FirstSection.PageSetup.Orientation = Orientation.Landscape;` prima di creare il gruppo. |
| **Multiple rectangles** | Crea ulteriori oggetti `Shape` e chiama `group.AppendChild(newRect)` per ciascuno. |
| **Dynamic size based on content** | Calcola larghezza/altezza dalle dimensioni dell'immagine o dalle metriche del testo, quindi assegna a `rectangle.Width` / `rectangle.Height`. |
| **Export to PDF** | Dopo `doc.Save`, chiama `doc.Save("GroupShape.pdf", SaveFormat.Pdf);`. |
| **Compatibility with older Word versions** | Salva usando `SaveFormat.Doc` invece di `Docx` per la compatibilità con Word 97‑2003. |

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Include tutte le direttive `using`, un punto di ingresso `Main` e commenti che spiegano ogni riga.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new document and a builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Define a group shape (300 pt × 200 pt) positioned at (50, 50)
        GroupShape group = new GroupShape(doc, 300, 200);
        group.Left = 50;
        group.Top  = 50;

        // 3️⃣ Create a rectangle (100 pt × 50 pt) positioned at (10, 10) inside the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width  = 100;   // set shape width
        rectangle.Height = 50;    // set shape height
        rectangle.Left = 10;
        rectangle.Top  = 10;

        // 4️⃣ Add the rectangle to the group
        group.AppendChild(rectangle);

        // 5️⃣ Insert the group into the first paragraph and save the file
        builder.CurrentParagraph.AppendChild(group);
        doc.Save("GroupShape.docx");

        // Open the resulting file automatically (optional)
        System.Diagnostics.Process.Start(new System.Diagnostics.ProcessStartInfo
        {
            FileName = "GroupShape.docx",
            UseShellExecute = true
        });
    }
}
```

**Output previsto:**  
Quando apri *GroupShape.docx*, la prima pagina mostra un rettangolo con bordo grigio posizionato a 50 pt dal margine sinistro/superiore, con il rettangolo stesso spostato di 10 pt all'interno del gruppo. Le dimensioni corrispondono ai valori impostati nel codice.

## Conclusione

Ora sai come **create word document**, **add rectangle shape**, e impostare con precisione **set shape size** e **set shape dimensions** usando Aspose.Words. L'approccio a forma raggruppata mantiene il tuo layout flessibile e pronto per future estensioni come grafiche aggiuntive o caselle di testo.

Successivamente, esplora argomenti correlati come **create shapes in word** per cerchi, frecce o percorsi SVG personalizzati, e impara a **set shape fill color** o **apply rotation**. Sperimenta con diverse misurazioni per vedere come Word rende i punti rispetto ai centimetri, e integra il codice in pipeline più ampie di generazione di documenti.

Buon coding, e sentiti libero di adattare questo modello a qualsiasi scenario di reportistica automatizzata o compilazione di moduli!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crea documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Tutorial ombra forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}