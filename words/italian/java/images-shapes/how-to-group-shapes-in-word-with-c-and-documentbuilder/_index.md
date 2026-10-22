---
category: general
date: 2026-10-04
description: Scopri come raggruppare le forme in Word usando C#. Questa guida mostra
  come inserire una forma rettangolare, raggruppare più forme e creare un file Word
  vuoto programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- insert rectangle shape
- group multiple shapes
- append child to group
- create blank word file
language: it
lastmod: 2026-10-04
og_description: Raggruppa le forme in Word usando C#. Segui questa guida passo‑passo
  per inserire una forma rettangolare, raggruppare più forme e creare un file Word
  vuoto con DocumentBuilder.
og_image_alt: Screenshot of grouped rectangle and ellipse shapes inside a Word document
og_title: Raggruppa forme in Word con C# – tutorial completo su DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-10-04'
  description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  headline: How to group shapes in Word with C# and DocumentBuilder
  type: TechArticle
- description: Learn how to group shapes in Word using C#. This guide shows how to
    insert rectangle shape, group multiple shapes, and create a blank Word file programmatically.
  name: How to group shapes in Word with C# and DocumentBuilder
  steps:
  - name: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
    text: '**Create a blank Word file** – Starting with a clean document guarantees
      that no hidden formatting interferes with shape positioning.'
  - name: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
    text: '**Initialize DocumentBuilder** – `DocumentBuilder` abstracts low‑level
      node manipulation, letting you focus on layout.'
  - name: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
    text: '**Insert individual shapes** – You first need separate objects (`insert
      rectangle shape` and an ellipse) before you can group them. Adjusting `Left`
      and `Top` ensures they appear side‑by‑side.'
  - name: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
    text: '**Group multiple shapes** – By creating a `GroupShape` and using **append
      child to group**, you turn two independent drawings into a single logical unit.
      Moving or resizing the group will affect both children simultaneously.'
  - name: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
    text: '**Save the document** – The final file, `GroupedShapes.docx`, can be opened
      in Microsoft Word to verify that the rectangle and ellipse are indeed grouped
      (select one, and both move together).'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- Shape handling
- DocumentBuilder
title: Come raggruppare le forme in Word con C# e DocumentBuilder
url: /it/java/images-shapes/how-to-group-shapes-in-word-with-c-and-documentbuilder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word con C# e DocumentBuilder

Se hai bisogno di **raggruppare forme in Word** da un'applicazione C#, questo tutorial ti mostra esattamente come farlo. Vedrai come *inserire una forma rettangolare*, combinare diversi disegni in un unico gruppo e, infine, **creare un file Word vuoto** che contiene gli oggetti raggruppati.

Lavorare con le forme è una necessità comune quando si generano report, fatture o modelli personalizzati in modo programmatico. Alla fine di questa guida avrai uno snippet di codice riutilizzabile da inserire in qualsiasi progetto .NET che fa riferimento ad Aspose.Words.

## Cosa imparerai

- Creare un documento Word vuoto da zero.  
- Inserire una forma rettangolare e un'ellisse usando `DocumentBuilder`.  
- **Raggruppare più forme** in un `GroupShape`.  
- Utilizzare **append child to group** per costruire la gerarchia.  
- Salvare il file su disco e verificare il risultato.

Non è necessaria alcuna esperienza preliminare con Aspose.Words, ma dovresti avere una conoscenza di base di C# e dello sviluppo .NET.

## Prerequisiti

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| .NET 6.0 or later | Fornisce il runtime per il codice C#. |
| Aspose.Words for .NET (latest version) | Fornisce `Document`, `DocumentBuilder` e le classi delle forme. |
| An IDE such as Visual Studio 2022 (or VS Code) | Rende facile compilare ed eseguire il campione. |
| Write permission to a folder on your machine | Necessario per la chiamata `doc.save`. |

Installa Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Raggruppare forme in Word – guida passo‑passo

Di seguito trovi il programma completo e eseguibile. Ogni sezione è spiegata in dettaglio così capirai **perché** il codice è scritto in questo modo, non solo **cosa** fa.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Shapes;

namespace WordShapeGroupingDemo
{
    class Program
    {
        static void Main()
        {
            // -------------------------------------------------
            // Step 1: create a blank Word file
            // -------------------------------------------------
            // The Document constructor creates an empty .docx container.
            Document doc = new Document();

            // -------------------------------------------------
            // Step 2: initialize DocumentBuilder to add content
            // -------------------------------------------------
            // DocumentBuilder is the high‑level API for inserting text,
            // images, tables, and shapes into the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // -------------------------------------------------
            // Step 3: insert individual shapes
            // -------------------------------------------------
            // Insert a rectangle shape – this demonstrates the
            // "insert rectangle shape" keyword in practice.
            Shape rectangle = builder.InsertShape(
                ShapeType.Rectangle,   // shape type
                100,                  // width in points
                50);                  // height in points

            // Position the rectangle a little away from the left margin.
            rectangle.Left = 100;   // points from the left edge
            rectangle.Top = 100;    // points from the top of the page

            // Insert an ellipse shape to accompany the rectangle.
            Shape ellipse = builder.InsertShape(
                ShapeType.Ellipse,
                80,
                80);
            ellipse.Left = rectangle.Left + rectangle.Width + 20; // place right of rectangle
            ellipse.Top = rectangle.Top; // align tops

            // -------------------------------------------------
            // Step 4: create a GroupShape and append children
            // -------------------------------------------------
            // A GroupShape acts like a container; any shape added to it
            // moves together with the group. This fulfills the
            // "group multiple shapes" requirement.
            GroupShape group = builder.InsertGroupShape();

            // The "append child to group" operation builds the hierarchy.
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Optional: give the group a name for later reference.
            group.Name = "MyShapeGroup";

            // -------------------------------------------------
            // Step 5: save the document containing the grouped shapes
            // -------------------------------------------------
            string outputPath = @"GroupedShapes.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Perché ogni passaggio è importante

1. **Creare un file Word vuoto** – Iniziare con un documento pulito garantisce che nessuna formattazione nascosta interferisca con il posizionamento delle forme.  
2. **Inizializzare DocumentBuilder** – `DocumentBuilder` astrae la manipolazione a basso livello dei nodi, permettendoti di concentrarti sul layout.  
3. **Inserire forme individuali** – Hai prima bisogno di oggetti separati (`insert rectangle shape` e un'ellisse) prima di poterli raggruppare. Regolare `Left` e `Top` garantisce che appaiano fianco a fianco.  
4. **Raggruppare più forme** – Creando un `GroupShape` e usando **append child to group**, trasformi due disegni indipendenti in un'unica unità logica. Spostare o ridimensionare il gruppo influenzerà entrambi i figli simultaneamente.  
5. **Salvare il documento** – Il file finale, `GroupedShapes.docx`, può essere aperto in Microsoft Word per verificare che il rettangolo e l'ellisse siano effettivamente raggruppati (seleziona uno, e entrambi si muovono insieme).

### Output previsto

Apri `GroupedShapes.docx` in Microsoft Word:

- Vedrai un rettangolo e un'ellisse posizionati uno accanto all'altro.  
- Selezionando una delle due forme, entrambe vengono evidenziate, confermando che appartengono allo stesso gruppo.  
- Il gruppo può essere trascinato, ridimensionato o formattato come un unico oggetto.

![Diagramma del rettangolo e dell'ellisse raggruppati all'interno di un documento Word](https://example.com/grouped-shapes.png){: .center-image alt="Diagramma del rettangolo e dell'ellisse raggruppati all'interno di un documento Word"}

*Lo screenshot illustra le forme raggruppate finali.*

---

## Inserire forma rettangolare – personalizzare dimensione e stile

Se ti serve un rettangolo con un colore di riempimento o un bordo specifici, modifica l'oggetto `Shape` dopo l'inserimento:

```csharp
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.LineWidth = 2.0; // points
```

Queste proprietà fanno parte della classe `Shape` e funzionano per qualsiasi tipo di forma, non solo per i rettangoli. Regolare lo stile prima di **append child to group** garantisce che il gruppo erediti le proprietà visive impostate.

---

## Raggruppare più forme – gestire più di due oggetti

L'esempio raggruppa un rettangolo e un'ellisse, ma è possibile aggiungere qualsiasi numero di forme:

```csharp
// Create additional shapes as needed
Shape triangle = builder.InsertShape(ShapeType.Triangle, 60, 60);
triangle.Left = ellipse.Left + ellipse.Width + 20;
triangle.Top = ellipse.Top;

// Append the new shape to the existing group
group.AppendChild(triangle);
```

**Consiglio professionale:** Dopo aver costruito un gruppo complesso, puoi bloccare il suo layout per evitare modifiche accidentali:

```csharp
group.LockAspectRatio = true;
group.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
group.RelativeVerticalPosition = RelativeVerticalPosition.Margin;
```

---

## Append child to group – l'ordine è importante

L'ordine in cui chiami `AppendChild` definisce lo Z‑order (quale forma appare sopra). Nell'esempio, il rettangolo è aggiunto per primo, poi l'ellisse, così l'ellisse sovrappone il rettangolo se si intersecano. Riordinare è semplice come chiamare `RemoveChild` e ri‑aggiungere:

```csharp
group.RemoveChild(ellipse);
group.AppendChild(ellipse); // now ellipse is on top
```

---

## Creare file Word vuoto – metodo helper riutilizzabile

Se la tua applicazione richiede frequentemente un documento nuovo, incapsula la logica di creazione:

```csharp
/// <summary>
/// Returns a new empty Document with a single section.
/// </summary>
static Document CreateBlankWordFile()
{
    Document emptyDoc = new Document();
    // Optionally set default page size, margins, etc.
    emptyDoc.FirstSection.PageSetup.PageWidth = 595;  // A4 width in points
    emptyDoc.FirstSection.PageSetup.PageHeight = 842; // A4 height in points
    return emptyDoc;
}
```

Puoi quindi sostituire la riga `new Document()` nel programma principale con `CreateBlankWordFile()`. Questo dimostra il concetto di **creare file Word vuoto** in modo riutilizzabile.

---

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| Le forme appaiono fuori pagina | I valori predefiniti di `Left`/`Top` sono 0, il che posiziona la forma al margine. | Imposta esplicitamente `Left` e `Top` dopo l'inserimento. |
| Il gruppo perde la formattazione | Modificare una forma figlia dopo che è stata aggiunta a un gruppo può rompere il layout del gruppo. | Applica tutte le proprietà visive **prima** di chiamare `AppendChild`. |
| Il file salvato è vuoto | `DocumentBuilder` non è mai stato usato per aggiungere un nodo, o `doc.Save` è stato chiamato su un'istanza `Document` diversa. | Verifica di salvare lo stesso `Document` che hai costruito. |
| Avvisi di compatibilità in Word | Utilizzare funzionalità di forma più recenti non supportate |  |

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea Group Shape in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserisci forme in documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}