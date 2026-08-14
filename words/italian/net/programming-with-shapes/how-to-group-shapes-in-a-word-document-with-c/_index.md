---
category: general
date: 2026-08-14
description: Come raggruppare le forme in un documento Word usando C#. Impara a creare
  un documento Word, inserire una forma rettangolare, raggruppare le forme in Word
  e salvare il documento come docx.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to group shapes
- create word document
- insert rectangle shape
- group shapes in word
- save document as docx
language: it
lastmod: 2026-08-14
og_description: Come raggruppare le forme in un documento Word usando C#. Segui questo
  tutorial completo per creare un file Word, inserire una forma rettangolare, raggruppare
  le forme in Word e salvare il risultato come docx.
og_image_alt: Screenshot showing how to group shapes in a Word document using C#
og_title: Come raggruppare le forme in un documento Word con C# – guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-08-14'
  description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  headline: How to group shapes in a Word document with C#
  type: TechArticle
- description: How to group shapes in a Word document using C#. Learn to create Word
    document, insert rectangle shape, group shapes in Word, and save document as docx.
  name: How to group shapes in a Word document with C#
  steps:
  - name: Create a new blank document
    text: The first thing you do when you want to **create Word document** programmatically
      is instantiate a `Document` object. This object represents the entire .docx
      file in memory.
  - name: Insert a rectangle shape
    text: To demonstrate **insert rectangle shape**, we use the `InsertShape` method.
      The rectangle will act as the first member of the group.
  - name: Insert an ellipse shape
    text: Next, we **insert ellipse shape** (the API calls it `Ellipse`). This will
      be the second member of the group.
  - name: Group the rectangle and ellipse
    text: Now we answer the central question **how to group shapes** in a Word document.
      Aspose.Words provides `AppendGroupShape` to create a group container, and then
      you call `Group()` on that container.
  - name: Save the document as a DOCX file
    text: The final step is to **save document as docx**. You can choose any path
      you like; the example uses a placeholder `"YOUR_DIRECTORY"` that you should
      replace with a real folder.
  - name: Expected output
    text: When you open `groupedShapes.docx` in Microsoft Word, you will see a light‑blue
      rectangle and a light‑coral ellipse locked together. Clicking either shape selects
      both, allowing you to move or resize them as a single unit.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shapes
title: Come raggruppare le forme in un documento Word con C#
url: /it/net/programming-with-shapes/how-to-group-shapes-in-a-word-document-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in un documento Word con C#

Se hai bisogno di **how to group shapes** in un documento Word, questa guida ti mostra i passaggi esatti usando C# e la libreria Aspose.Words. Vedrai come creare un documento Word, inserire una forma rettangolare, raggruppare forme in Word e infine **save document as docx**—tutto in un unico programma eseguibile.

Creare e manipolare forme è una necessità comune quando si generano report, contratti o brochure di marketing in modo programmatico. Alla fine di questo tutorial avrai uno snippet di codice riutilizzabile da inserire in qualsiasi progetto .NET.

## Prerequisiti

- .NET 6.0 o versioni successive installate  
- Visual Studio 2022 (o qualsiasi IDE che supporta .NET)  
- Una licenza Aspose.Words per .NET (o una prova gratuita)  
- Familiarità di base con la sintassi C#  

Non sono richiesti pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come raggruppare forme in un documento Word

Il cuore della soluzione è un processo in cinque passaggi. Ogni passaggio è spiegato in dettaglio e il codice sorgente completo è fornito alla fine dell’articolo.

### Passo 1: Creare un nuovo documento vuoto

La prima cosa da fare quando vuoi **create Word document** programmaticamente è istanziare un oggetto `Document`. Questo oggetto rappresenta l’intero file .docx in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty document
Document doc = new Document();

// Obtain a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:** `DocumentBuilder` è un helper di alto livello che ti consente di inserire testo, tabelle e forme senza gestire manualmente l’albero dei nodi sottostante.

### Passo 2: Inserire una forma rettangolare

Per dimostrare **insert rectangle shape**, utilizziamo il metodo `InsertShape`. Il rettangolo fungerà da primo membro del gruppo.

```csharp
// Insert a rectangle (100x50 points) at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Optional: set a fill color so the shape is visible
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

**Perché è importante:** Le forme sono posizionate rispetto al punto di inserimento. Impostare un colore di riempimento ti aiuta a vedere la forma quando apri il documento risultante.

### Passo 3: Inserire una forma ellittica

Successivamente, **insert ellipse shape** (l’API la chiama `Ellipse`). Questa sarà il secondo membro del gruppo.

```csharp
// Insert an ellipse (80x40 points) right after the rectangle
Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

**Perché è importante:** Inserendo l’ellisse subito dopo il rettangolo, entrambe le forme finiscono nello stesso paragrafo, il che semplifica il raggruppamento successivo.

### Passo 4: Raggruppare il rettangolo e l'ellisse

Ora rispondiamo alla domanda centrale **how to group shapes** in a Word document. Aspose.Words fornisce `AppendGroupShape` per creare un contenitore di gruppo, quindi chiami `Group()` su quel contenitore.

```csharp
// Get the first paragraph of the document (where the shapes live)
Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;

// Create a group shape that contains the rectangle and ellipse
Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });

// Turn the container into a true group – the shapes will move and scale together
groupedShape.Group();
```

**Perché è importante:** Una volta raggruppate, qualsiasi trasformazione (spostamento, ridimensionamento, rotazione) applicata a `groupedShape` influisce automaticamente sia sul rettangolo sia sull’ellisse. Questo è essenziale per mantenere la coerenza del layout nei documenti generati.

### Passo 5: Salvare il documento come file DOCX

L’ultimo passaggio è **save document as docx**. Puoi scegliere qualsiasi percorso ti piaccia; l’esempio utilizza il segnaposto `"YOUR_DIRECTORY"` che dovrai sostituire con una cartella reale.

```csharp
// Define the output path (ensure the directory exists)
string outputPath = @"C:\Temp\groupedShapes.docx";

// Save the document in DOCX format
doc.Save(outputPath, SaveFormat.Docx);

Console.WriteLine($"Document saved successfully to {outputPath}");
```

**Perché è importante:** Il salvataggio come DOCX preserva i metadati del raggruppamento, così quando apri il file in Microsoft Word vedrai il rettangolo e l’ellisse comportarsi come un unico oggetto.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che combina tutti e cinque i passaggi. Copialo in un nuovo progetto console, ripristina il pacchetto NuGet Aspose.Words e avvialo.

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
            // Step 1: Create a new blank document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 2: Insert a rectangle shape (100x50 points)
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangleShape.FillColor = System.Drawing.Color.LightBlue;

            // Step 3: Insert an ellipse shape (80x40 points)
            Shape ellipseShape = builder.InsertShape(ShapeType.Ellipse, 80, 40);
            ellipseShape.FillColor = System.Drawing.Color.LightCoral;

            // Step 4: Group the rectangle and ellipse
            Paragraph firstParagraph = doc.FirstSection.Body.FirstParagraph;
            Shape groupedShape = firstParagraph.AppendGroupShape(new[] { rectangleShape, ellipseShape });
            groupedShape.Group();

            // Step 5: Save the document as DOCX
            string outputPath = @"C:\Temp\groupedShapes.docx";
            doc.Save(outputPath, SaveFormat.Docx);

            Console.WriteLine($"Document saved successfully to {outputPath}");
        }
    }
}
```

### Output previsto

Quando apri `groupedShapes.docx` in Microsoft Word, vedrai un rettangolo azzurro chiaro e un’ellisse corallo chiaro bloccati insieme. Cliccando su una delle due forme, entrambe vengono selezionate, permettendoti di spostarle o ridimensionarle come un’unica unità.

## Domande comuni e casi particolari

| Domanda | Risposta |
|----------|--------|
| **Posso raggruppare più di due forme?** | Sì. Passa qualsiasi numero di oggetti `Shape` a `AppendGroupShape`. Il metodo accetta un array, quindi puoi costruire dinamicamente una collezione. |
| **E se ho bisogno che il gruppo sia ancorato a una cella di tabella?** | Inserisci le forme all’interno del paragrafo della cella, quindi chiama `AppendGroupShape` su quel paragrafo. Il gruppo eredita l’ancoraggio della cella. |
| **Il raggruppamento influisce sull’XML sottostante?** | Aspose.Words scrive un elemento `<w:grpSp>` che contiene le forme figlie. Word lo riconosce come un gruppo, preservando il posizionamento relativo. |
| **Come posso separare il gruppo in seguito?** | Chiama `groupedShape.Ungroup()`; il metodo restituisce le forme individuali così da poterle manipolare separatamente. |
| **Ci sono impatti sulle prestazioni quando si raggruppano molte forme?** | Il raggruppamento stesso è poco costoso, ma il rendering di gruppi molto grandi (centinaia di forme) può aumentare la dimensione del file. Considera di rasterizzare le immagini se la dimensione diventa un problema. |

## Consigli professionali

- **Imposta posizioni esplicite** (`Left`, `Top`) se hai bisogno di un allineamento preciso prima del raggruppamento.  
- **Usa `Shape.WrapType = WrapType.Inline`** quando vuoi che il gruppo si comporti come un elemento di paragrafo anziché come un oggetto fluttuante.  
- **Applica uno stile di linea** al gruppo (`groupedShape.LineFormat`) per dare all’intera collezione un bordo.  
- **Riutilizza il gruppo**: dopo aver chiamato `Group()`, puoi clonare `groupedShape` e inserire il clone altrove nel documento.

## Prossimi passi

Ora che sai **how to group shapes** in un documento Word, puoi approfondire argomenti correlati come:

- **Insert rectangle shape** con testo o immagini personalizzate all’interno della forma.  
- **Create complex diagrams** nidificando gruppi (group a group).  
- **Export the document as PDF** mantenendo il raggruppamento delle forme (`doc.Save("output.pdf", SaveFormat.Pdf)`).  

Ognuno di questi si basa sugli stessi fondamenti trattati qui, quindi sei pronto a espandere il tuo toolkit di automazione Word.

## Conclusione

Questo tutorial ha dimostrato **how to group shapes** in un documento Word usando C#. Hai imparato a **create Word document**, **insert rectangle shape**, **group shapes in Word** e infine **save document as docx**. Con l’esempio completo e i consigli pratici forniti, puoi integrare il raggruppamento di forme in qualsiasi flusso di lavoro di generazione documenti. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑per‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserire forme in documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Creare forma rettangolare in Word usando C# – Guida passo‑per‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}