---
category: general
date: 2026-09-30
description: Crea un documento vuoto e inserisci una forma rettangolare, un'ellisse
  e raggruppa più forme in C# usando Aspose.Words. Scopri come inserire le forme e
  come creare un gruppo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank document
- insert rectangle shape
- group multiple shapes
- how to insert shapes
- how to create group
language: it
lastmod: 2026-09-30
og_description: Crea un documento vuoto in C# e impara come inserire forme e raggruppare
  più forme con Aspose.Words. Segui il tutorial passo‑passo.
og_image_alt: Screenshot of a C# program that creates a blank document, inserts a
  rectangle and ellipse, and groups them together.
og_title: Crea un documento vuoto e raggruppa le forme in C# – Guida Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Create blank document and insert rectangle shape, ellipse, and group
    multiple shapes in C# using Aspose.Words. Learn how to insert shapes and how to
    create group.
  headline: How to create blank document and add shapes with Aspose.Words in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- document automation
- shapes
title: Come creare un documento vuoto e aggiungere forme con Aspose.Words in C#
url: /it/java/images-shapes/how-to-create-blank-document-and-add-shapes-with-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento vuoto e aggiungere forme con Aspose.Words in C#

Se hai bisogno di **creare un documento vuoto** e popolarlo con elementi grafici, questa guida ti mostra esattamente come fare. Vedrai come **inserire una forma rettangolare**, aggiungere altri oggetti di disegno e poi **raggruppare più forme** affinché si comportino come un’unica unità.

Lavorare con le forme è una necessità comune quando si generano contratti, certificati o report personalizzati. In questo tutorial imparerai l’intero flusso di lavoro, dall’inizializzazione del documento al salvataggio del file finale, utilizzando l’API Aspose.Words per .NET.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* SDK .NET 6.0 (o successivo) installato  
* Una licenza valida di Aspose.Words per .NET (la versione di prova gratuita funziona per questo esempio)  
* Un IDE come Visual Studio 2022 o Visual Studio Code  

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come creare un documento vuoto e lavorare con le forme

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta il file Word in memoria e ti dà accesso al `DocumentBuilder`, lo strumento principale per inserire contenuti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

**Perché è importante:** Un documento vuoto ti offre una tela pulita. Il `DocumentBuilder` mantiene il punto di inserimento corrente, quindi ogni forma che aggiungi viene posizionata automaticamente nella pagina appropriata.

## Inserire una forma rettangolare e altre forme

Successivamente, aggiungiamo un rettangolo e un'ellisse. Entrambe le chiamate utilizzano lo stesso metodo `InsertShape`, che è il modo consigliato **per inserire forme** in Aspose.Words.

```csharp
        // Step 2: Insert a rectangle shape (100 × 50 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;   // optional styling
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // Step 3: Insert an ellipse shape (80 × 80 points)
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;
```

*Il metodo `InsertShape` posiziona automaticamente la forma nella posizione corrente del cursore.* Se hai bisogno di un posizionamento preciso, puoi regolare `Shape.Left` e `Shape.Top` dopo l’inserimento.

## Raggruppare più forme in un unico oggetto

Ora combiniamo il rettangolo e l’ellisse in una singola entità logica. Il raggruppamento è utile quando vuoi spostare o ridimensionare più forme insieme.

```csharp
        // Step 4: Create a group shape that will hold multiple shapes
        GroupShape groupShape = builder.InsertGroupShape();

        // Step 5: Add the rectangle and ellipse to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional: Apply a border to the whole group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;
```

**Come funziona:** `InsertGroupShape` crea un contenitore che si comporta come qualsiasi altra `Shape`. Chiamando `AppendChild`, sposti le forme esistenti nel contenitore, il quale aggiorna automaticamente le loro coordinate relative.

### Consiglio pratico

Se in seguito devi **creare un gruppo** programmaticamente per più di due forme, ripeti semplicemente `AppendChild` per ogni ulteriore istanza di `Shape`. Il gruppo può contenere qualsiasi numero di oggetti di disegno, incluse immagini, caselle di testo o persino altri gruppi.

## Esempio completo – come inserire forme e salvare il documento

Di seguito trovi il programma completo, eseguibile, che dimostra ogni passaggio discusso finora. L’esecuzione del codice produce un file `ShapesDemo.docx` contenente un rettangolo, un’ellisse e una forma raggruppata.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1. Create a blank document
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2. Insert rectangle shape
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        rectangle.StrokeColor = System.Drawing.Color.Blue;
        rectangle.FillColor = System.Drawing.Color.LightBlue;

        // 3. Insert ellipse shape
        Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
        ellipse.StrokeColor = System.Drawing.Color.Green;
        ellipse.FillColor = System.Drawing.Color.LightGreen;

        // 4. Create a group shape
        GroupShape groupShape = builder.InsertGroupShape();

        // 5. Add shapes to the group
        groupShape.AppendChild(rectangle);
        groupShape.AppendChild(ellipse);

        // Optional styling for the group
        groupShape.StrokeColor = System.Drawing.Color.DarkGray;
        groupShape.LineWidth = 1.5;

        // 6. Save the document
        string outputPath = "ShapesDemo.docx";
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output previsto:** Aprendo `ShapesDemo.docx` in Microsoft Word si visualizza una singola pagina con un rettangolo blu, un’ellisse verde e un bordo grigio che circonda il gruppo. Spostare il gruppo muove entrambe le forme insieme, confermando che l’operazione **raggruppare più forme** è riuscita.

## Domande comuni e gestione di casi particolari

| Domanda | Risposta |
|----------|--------|
| *E se ho bisogno delle forme su una pagina specifica?* | Chiama `builder.MoveToDocumentEnd();` prima di inserire le forme, oppure usa `builder.MoveToSection(sectionIndex);` per puntare a una sezione particolare. |
| *Posso aggiungere testo all’interno di una forma raggruppata?* | Sì. Crea una `Shape` di tipo `ShapeType.TextBox`, configura il suo testo e poi `AppendChild` al `GroupShape`. |
| *Le dimensioni delle forme usano punti o pixel?* | Aspose.Words utilizza **punti** (1 pt = 1/72 pollice). Questo garantisce dimensioni coerenti su stampanti e schermi. |
| *Come modificare la rotazione del gruppo?* | Imposta `groupShape.RotationAngle = 45;` (gradi). Tutte le forme figlie ruotano attorno all’origine del gruppo. |

## Conclusione

Ora sai come **creare un documento vuoto**, **inserire una forma rettangolare**, **inserire forme** come le ellissi, e **raggruppare più forme** in un unico oggetto usando Aspose.Words per .NET. L’esempio di codice completo dimostra l’approccio consigliato, e i suggerimenti sopra ti aiutano ad adattare la soluzione a scenari più complessi, come l’aggiunta di caselle di testo o la rotazione di gruppi.

Pronto a esplorare di più? Prova ad aggiungere una forma immagine al gruppo, sperimenta con diversi colori di riempimento o genera un report multipagina in cui ogni pagina contiene il proprio diagramma raggruppato. Gli stessi principi si applicano, così potrai scalare questo modello a qualsiasi progetto di automazione documentale.

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create blank word document with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}