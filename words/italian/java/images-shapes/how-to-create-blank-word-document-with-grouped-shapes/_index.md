---
category: general
date: 2026-09-08
description: Impara a creare un documento Word vuoto, inserire una forma rettangolare
  e raggruppare più forme usando C#. Segui questa guida passo‑passo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert rectangle shape
- group multiple shapes
- add shapes to group
language: it
lastmod: 2026-09-08
og_description: Crea un documento Word vuoto, inserisci una forma rettangolare e raggruppa
  più forme in C#. Questo tutorial ti guida attraverso l'intero processo.
og_image_alt: Screenshot showing a blank Word document with a grouped rectangle and
  ellipse shape
og_title: Crea documento Word vuoto con forme raggruppate in C#
schemas:
- author: Aspose
  dateModified: '2026-09-08'
  description: Learn how to create blank Word document, insert rectangle shape and
    group multiple shapes using C#. Follow this step‑by‑step guide.
  headline: How to create blank Word document with grouped shapes
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Come creare un documento Word vuoto con forme raggruppate
url: /it/java/images-shapes/how-to-create-blank-word-document-with-grouped-shapes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto con forme raggruppate

Se hai bisogno di **creare un documento Word vuoto** che contenga grafiche personalizzate, questa guida ti mostra esattamente come fare. Imparerai a **inserire una forma rettangolare**, **raggruppare più forme** e **aggiungere forme al gruppo** usando Aspose.Words per .NET.

Un documento vuoto ti offre una tela pulita, e il raggruppamento delle forme ti consente di spostarle, ridimensionarle o ruotarle come un'unica unità. Questo tutorial copre ogni passaggio—dall'inizializzazione del documento al salvataggio del file finale—così potrai copiare il codice nel tuo progetto e vedere risultati immediati.

## Cosa ti servirà

* .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.6+)
* Una licenza valida di Aspose.Words per .NET (la valutazione gratuita è sufficiente per i test)
* Un IDE come Visual Studio 2022 o Visual Studio Code
* Familiarità di base con la sintassi C#

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come creare un documento Word vuoto

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta un file `.docx` vuoto che puoi modificare con un `DocumentBuilder`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Step 1: Create a new blank document and a builder to edit it.
            Document doc = new Document();               // Blank Word document
            DocumentBuilder builder = new DocumentBuilder(doc);
```

Il costruttore `Document` crea un **documento Word vuoto** in memoria. Il `DocumentBuilder` fornisce un'API fluida per inserire testo, immagini e oggetti di disegno.

## Inserire una forma rettangolare nel documento

Successivamente, aggiungi una forma rettangolare. Il rettangolo sarà il primo figlio del gruppo che creeremo più tardi.

```csharp
            // Step 2: Insert a rectangle shape (100 pt wide, 50 pt high).
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            // Optional: give the rectangle a fill color for visibility.
            rectangle.FillColor = System.Drawing.Color.LightBlue;
```

Chiamare `InsertShape` con `ShapeType.Rectangle` **inserisce una forma rettangolare** nella posizione corrente del cursore. Larghezza e altezza sono espresse in punti (1 pt ≈ 1/72 in).

## Raggruppare più forme insieme

Un `GroupShape` funziona come un contenitore. Tutte le forme figlie all'interno del gruppo si muovono e si trasformano insieme. Prima, crea il gruppo, poi aggiungi il rettangolo appena creato.

```csharp
            // Step 3: Create a group shape that will hold multiple child shapes.
            GroupShape group = builder.InsertGroupShape();
            // Append the rectangle as the first child of the group.
            group.AppendChild(rectangle);
```

Il metodo `InsertGroupShape` posiziona un gruppo vuoto al cursore del builder. Aggiungendo il rettangolo, **raggruppiamo più forme**—il rettangolo diventa parte della collezione interna di nodi del gruppo.

## Aggiungere forme al gruppo e salvare il file

Ora aggiungi una seconda forma—un'ellisse—per dimostrare come più oggetti condividano lo stesso contenitore. Successivamente, salva il documento.

```csharp
            // Step 4: Insert an ellipse shape (80 pt wide, 80 pt high).
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;

            // Append the ellipse to the same group.
            group.AppendChild(ellipse);

            // Step 5: Save the document containing the grouped shapes.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

La chiamata `InsertShape` **aggiunge forme al gruppo** quando aggiungi lo `Shape` restituito al `GroupShape`. Salvare il `Document` scrive un file `.docx` che puoi aprire con Microsoft Word, LibreOffice o qualsiasi visualizzatore compatibile.

### Risultato atteso

Quando apri *GroupShapeDemo.docx*, vedrai una pagina vuota con un oggetto raggruppato che contiene un rettangolo azzurro chiaro e un'ellisse rosa. Selezionare il gruppo ti permette di spostare entrambe le forme insieme, confermando che **raggruppare più forme** ha funzionato come previsto.

## Perché usare un GroupShape?

* **Trasformazioni atomiche** – Scalare, ruotare o spostare il gruppo influisce su tutti i figli in modo uniforme.
* **Organizzazione logica** – Mantiene le grafiche correlate insieme, rendendo la struttura del documento più facile da gestire.
* **Prestazioni** – Renderizzare un unico contenitore è spesso più veloce rispetto alla gestione di molte forme indipendenti.

Se in seguito devi modificare un singolo figlio, puoi recuperarlo da `group.ChildNodes` tramite indice o tramite la proprietà `Name`.

## Varianti comuni e casi limite

| **Tipi di forma diversi**               | Replace `ShapeType.Rectangle` or `ShapeType.Ellipse` with any other `ShapeType` |
|------------------------------------------|----------------------------------------------------------------------------------|
| **Aggiungere testo all'interno di una forma** | Use `Shape.TextPath.Text = "Hello"` after inserting the shape                    |
| **Impostare un angolo di rotazione**     | `group.Rotation = 45;` (degrees)                                                 |
| **Salvare come PDF invece di DOCX**      | `doc.Save("GroupShapeDemo.pdf");`                                                |
| **Applicare un bordo al gruppo**         | `group.LineStyle = LineStyle.Single;`<br>`group.LineWidth = 1.5;`               |

## Consigli professionali

* **Dai un nome alle tue forme** – `rectangle.Name = "MyRect";` rende più facile individuarle in seguito.
* **Usa il posizionamento relativo** – Imposta `group.RelativeHorizontalPosition` su `RelativeHorizontalPosition.Page` se vuoi che il gruppo rimanga ancorato ai margini della pagina.
* **Rilascia le risorse** – Avvolgi il `Document` in un blocco `using` quando lavori in applicazioni più grandi per liberare rapidamente la memoria non gestita.

## Codice sorgente completo per copia‑incolla veloce

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace GroupShapeDemo
{
    class Program
    {
        static void Main()
        {
            // Create a new blank document and a builder to edit it.
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Insert a rectangle shape (100 pt × 50 pt) and give it a light‑blue fill.
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 100, 50);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // Create a group shape and add the rectangle as its first child.
            GroupShape group = builder.InsertGroupShape();
            group.AppendChild(rectangle);

            // Insert an ellipse shape (80 pt × 80 pt) with a pink fill.
            Shape ellipse = builder.InsertShape(ShapeType.Ellipse, 80, 80);
            ellipse.FillColor = System.Drawing.Color.Pink;
            group.AppendChild(ellipse);

            // Save the document. The file will contain the grouped rectangle and ellipse.
            string outputPath = "GroupShapeDemo.docx";
            doc.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

Copia il codice in un nuovo progetto console, ripristina il pacchetto NuGet `Aspose.Words` e avvia. Il file di output appare nella cartella `bin/Debug/net6.0` del progetto (o equivalente).

## Prossimi passi

Ora che puoi **creare un documento Word vuoto**, **inserire una forma rettangolare** e **raggruppare più forme**, potresti esplorare:

* Aggiungere **caselle di testo** all'interno di un gruppo per creare diagrammi etichettati.
* Esportare la grafica raggruppata in un'immagine con `doc.Save("image.png", SaveFormat.Png)`.
* Combinare gruppi con tabelle per report riccamente formattati.

Sperimenta con diverse proprietà delle forme, gerarchie di gruppi e formati di esportazione per sfruttare appieno le capacità di disegno di Aspose.Words.

--- 

*Ricorda*: raggruppare le forme è un modo potente per mantenere i tuoi documenti Word ordinati e il tuo codice manutenibile. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Creare una forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Inserire forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Creare una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}