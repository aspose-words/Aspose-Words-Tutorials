---
category: general
date: 2026-09-18
description: Crea una forma rettangolare in un documento Word usando C#. Scopri come
  aggiungere più forme, aggiungere forme a un gruppo e inserire un gruppo di forme
  con Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- add multiple shapes
- add shapes to group
- insert group shape
language: it
lastmod: 2026-09-18
og_description: Crea una forma rettangolare in un file Word con C#. Questa guida mostra
  come aggiungere più forme, aggiungere forme a un gruppo e inserire una forma di
  gruppo utilizzando Aspose.Words.
og_image_alt: Grouped rectangle and ellipse shapes displayed in a Word document
og_title: Crea forma rettangolare e raggruppa forme in C#
schemas:
- author: Aspose
  dateModified: '2026-09-18'
  description: Create rectangle shape in a Word document using C#. Learn how to add
    multiple shapes, add shapes to a group, and insert group shape with Aspose.Words.
  headline: Create rectangle shape and group multiple shapes in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Shape
- GroupShape
title: Crea forma rettangolare e raggruppa più forme in C#
url: /it/net/programming-with-shapes/create-rectangle-shape-and-group-multiple-shapes-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare e raggruppa più forme in C#

Se hai bisogno di **create rectangle shape** in un documento Word, questo tutorial mostra una soluzione completa. Vedrai come **add multiple shapes**, **add shapes to a group** e **insert group shape** usando l'Aspose.Words API per .NET.

Lavorare con le forme è una necessità comune quando si generano report, contratti o materiali di marketing in modo programmatico. Alla fine di questa guida avrai un'applicazione console C# eseguibile che produce un file `.docx` contenente un rettangolo, un'ellisse e un gruppo che contiene entrambe le forme.

I soli prerequisiti sono un SDK .NET recente (6.0 o successivo) e una copia con licenza di Aspose.Words per .NET. Non sono richiesti strumenti aggiuntivi.

## Prerequisiti

- .NET 6.0 SDK o più recente  
- Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`)  
- Familiarità di base con la sintassi C#  

Puoi installare il pacchetto con il seguente comando:

```bash
dotnet add package Aspose.Words
```

## Passo 1: Crea forma rettangolare con Aspose.Words

Il primo passo è creare un oggetto `Shape` di tipo `Rectangle`. Questo oggetto rappresenta il rettangolo visivo che apparirà nel documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty document
Document doc = new Document();

// Initialize a DocumentBuilder for editing the document
DocumentBuilder builder = new DocumentBuilder(doc);

// Create a rectangle shape: width = 100 points, height = 50 points
Shape rectangle = new Shape(doc, ShapeType.Rectangle);
rectangle.Width = 100;
rectangle.Height = 50;

// Optional: give the rectangle a fill color and a border
rectangle.FillColor = System.Drawing.Color.LightBlue;
rectangle.StrokeColor = System.Drawing.Color.DarkBlue;
rectangle.StrokeWeight = 1.0;

// Insert the rectangle at the current builder position
builder.InsertNode(rectangle);
```

**Perché è importante:** `ShapeType.Rectangle` indica ad Aspose.Words di renderizzare un rettangolo geometrico. Impostare `Width` e `Height` definisce le sue dimensioni in punti (1 punto = 1/72 di pollice). Aggiungere colori di riempimento e contorno rende la forma visibile senza necessità di styling aggiuntivo.

## Passo 2: Aggiungi più forme al documento

Dopo il rettangolo, puoi creare un numero qualsiasi di forme aggiuntive. In questo esempio aggiungiamo un'ellisse per dimostrare come funziona **add multiple shapes**.

```csharp
// Create an ellipse shape: width = 80 points, height = 80 points
Shape ellipse = new Shape(doc, ShapeType.Ellipse);
ellipse.Width = 80;
ellipse.Height = 80;

// Style the ellipse
ellipse.FillColor = System.Drawing.Color.LightCoral;
ellipse.StrokeColor = System.Drawing.Color.Maroon;
ellipse.StrokeWeight = 1.0;

// Insert the ellipse after the rectangle
builder.InsertNode(ellipse);
```

**Perché è importante:** Ogni chiamata a `new Shape` crea un oggetto di disegno indipendente. Inserendoli in sequenza costruisci una collezione di forme che in seguito possono essere raggruppate o posizionate individualmente.

## Passo 3: Aggiungi forme al gruppo

Raggruppare le forme semplifica la gestione del layout perché il gruppo si comporta come un unico nodo. Questo passo mostra come **add shapes to group** usando `GroupShape`.

```csharp
// Create a GroupShape with a bounding box of 200x200 points
GroupShape group = new GroupShape(doc, 200, 200);

// Move the builder's cursor back to the start of the document
builder.MoveToDocumentStart();

// Insert the empty group into the document
builder.InsertNode(group);

// Append the previously created rectangle and ellipse to the group
group.AppendChild(rectangle);
group.AppendChild(ellipse);
```

**Perché è importante:** `GroupShape` agisce come un contenitore. Quando sposti, ruoti o ridimensioni il gruppo, tutte le forme figlie seguono automaticamente. Il riquadro di delimitazione (200 × 200 punti) definisce lo spazio di coordinate per le forme figlie.

## Passo 4: Inserisci forma di gruppo nel documento

Ora che il gruppo contiene il rettangolo e l'ellisse, devi **insert group shape** nella posizione desiderata. Il builder ha già posizionato il gruppo vuoto, ma puoi anche inserirlo altrove se necessario.

```csharp
// Position the group at a specific location (optional)
group.Left = 50;   // 50 points from the left margin
group.Top = 100;   // 100 points from the top margin

// Save the document with the grouped shapes
doc.Save("GroupShapeExample.docx");
```

**Perché è importante:** Regolare `Left` e `Top` sposta l'intero gruppo all'interno della pagina. Salvare il documento scrive la gerarchia delle forme in un file `.docx` che può essere aperto in Microsoft Word, LibreOffice o qualsiasi visualizzatore compatibile.

## Esempio completo eseguibile

Di seguito trovi il programma completo che combina tutti i passaggi. Copia il codice in un nuovo progetto console e eseguilo per generare `GroupShapeExample.docx`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new empty document
            Document doc = new Document();

            // Step 2: Initialize a DocumentBuilder for editing the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 3: Create a rectangle shape
            Shape rectangle = new Shape(doc, ShapeType.Rectangle);
            rectangle.Width = 100;
            rectangle.Height = 50;
            rectangle.FillColor = Color.LightBlue;
            rectangle.StrokeColor = Color.DarkBlue;
            rectangle.StrokeWeight = 1.0;

            // Step 4: Create an ellipse shape
            Shape ellipse = new Shape(doc, ShapeType.Ellipse);
            ellipse.Width = 80;
            ellipse.Height = 80;
            ellipse.FillColor = Color.LightCoral;
            ellipse.StrokeColor = Color.Maroon;
            ellipse.StrokeWeight = 1.0;

            // Step 5: Create a GroupShape that will hold both shapes
            GroupShape group = new GroupShape(doc, 200, 200);
            group.Left = 50;   // optional positioning
            group.Top = 100;   // optional positioning

            // Add the rectangle and ellipse to the group
            group.AppendChild(rectangle);
            group.AppendChild(ellipse);

            // Insert the group into the document at the current builder position
            builder.InsertNode(group);

            // Step 6: Save the document containing the grouped shapes
            doc.Save("GroupShapeExample.docx");

            Console.WriteLine("Document saved successfully.");
        }
    }
}
```

**Output previsto:**  
Aprendo `GroupShapeExample.docx` si vede un unico gruppo contenente un rettangolo azzurro chiaro e un'ellisse corallo chiaro, entrambi posizionati all'interno di un contenitore di 200 × 200 punti. Il gruppo può essere selezionato come un unico oggetto in Word, confermando che **add shapes to group** è riuscito.

## Varianti comuni e casi limite

| Situazione | Regolazione consigliata |
|------------|--------------------------|
| Tipi di forma diversi (es., `ShapeType.Line`) | Crea la forma con il `ShapeType` desiderato e imposta la sua geometria di conseguenza. |
| Necessità di ruotare una forma | Usa `shape.Rotation = 45;` (gradi) prima di aggiungerla al gruppo. |
| Documenti di grandi dimensioni con molti gruppi | Riutilizza una singola istanza di `DocumentBuilder`; evita di creare un nuovo builder per ogni gruppo per ridurre l'overhead di memoria. |
| Salvataggio in PDF invece di DOCX | Chiama `doc.Save("output.pdf", SaveFormat.Pdf);` dopo aver inserito il gruppo. |

**Suggerimento professionale:** Imposta sempre valori espliciti di `Left` e `Top` per il gruppo quando hai bisogno di un posizionamento preciso. Se li ometti, il gruppo eredita la posizione corrente del cursore del builder, il che può portare a risultati di layout inaspettati.

## Conclusione

Ora sai come **create rectangle shape**, **add multiple shapes**, **add shapes to group** e **insert group shape** in un documento Word usando C#. L'esempio completo dimostra l'intero flusso di lavoro dalla creazione del documento al salvataggio del file finale.  

Successivamente, esplora argomenti correlati come **positioning shapes relative to text**, **applying text wrapping**, e **exporting grouped shapes to PDF**. queste estensioni ti permettono di creare layout di documenti sofisticati e programmatici con Aspose.Words.

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}