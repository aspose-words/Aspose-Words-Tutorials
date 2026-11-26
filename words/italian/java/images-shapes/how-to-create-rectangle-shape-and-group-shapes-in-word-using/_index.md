---
category: general
date: 2026-11-18
description: Scopri come creare una forma rettangolare in un documento Word con C#.
  La guida copre anche come impostare le dimensioni della forma, la posizione della
  forma e raggruppare le forme in Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- set shape size
- group shapes in word
- set shape dimensions
- set shape position
language: it
lastmod: 2026-11-18
og_description: Crea una forma rettangolare in un file Word usando C# e impara a impostare
  le dimensioni della forma, la posizione della forma e a raggruppare le forme in
  Word.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  shape created with C#
og_title: Crea forma rettangolare e raggruppa le forme in Word con C#
schemas:
- author: Aspose
  dateModified: '2026-11-18'
  description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  headline: How to create rectangle shape and group shapes in Word using C#
  type: TechArticle
- description: Learn how to create rectangle shape in a Word document with C#. The
    guide also covers set shape size, set shape position, and group shapes in Word.
  name: How to create rectangle shape and group shapes in Word using C#
  steps:
  - name: Initialize the document and builder
    text: '```csharp using System; using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert a group shape
    text: '```csharp // Step 2: Insert a group shape that will hold multiple child
      shapes GroupShape group = builder.InsertGroupShape(); ```'
  - name: Create the rectangle and set its size
    text: '```csharp // Step 3: Create a rectangle shape, set its size, and add it
      to the group Shape rectangle = new Shape(doc, ShapeType.Rectangle); rectangle.Width
      = 100; // set shape size (width) in points rectangle.Height = 50; // set shape
      size (height) in points group.AppendChild(rectangle); ```'
  - name: Create the ellipse, set dimensions, and position it
    text: '```csharp // Step 4: Create an ellipse shape, set its size and position,
      and add it to the group Shape ellipse = new Shape(doc, ShapeType.Ellipse); ellipse.Width
      = 80; // set shape dimensions (width) ellipse.Height = 80; // set shape dimensions
      (height) ellipse.Left = 120; // set shape position rela'
  - name: Save the document
    text: '```csharp // Step 5: Save the document containing the grouped shapes doc.Save("GroupShape.docx");
      Console.WriteLine("Document saved successfully."); } } ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Come creare una forma rettangolare e raggruppare le forme in Word usando C#
url: /it/java/images-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-using/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare una forma rettangolare e raggruppare forme in Word usando C#

Se hai bisogno di **creare una forma rettangolare** in un documento Word, questo tutorial ti mostra una soluzione completa, pronta all'uso. Vedrai come impostare la dimensione della forma, impostare la posizione della forma e raggruppare le forme in Word in modo che si comportino come un unico oggetto.

Lavorare con le forme è una necessità comune quando si generano report, fatture o diagrammi in modo programmatico. Alla fine di questa guida sarai in grado di generare un file `.docx` che contiene un rettangolo, un'ellisse e un contenitore raggruppato—tutto creato con Aspose.Words per .NET.

## Prerequisiti

- .NET 6.0 SDK o versioni successive (il codice funziona anche con .NET Framework 4.7+)
- Pacchetto NuGet Aspose.Words for .NET (`Install-Package Aspose.Words`)
- Un editor di codice o IDE (Visual Studio, VS Code, Rider, ecc.)

Non sono richieste librerie aggiuntive.

## Come creare una forma rettangolare e raggruppare forme in Word

I passaggi fondamentali sono:

1. **Creare un documento vuoto** e un `DocumentBuilder`.
2. **Inserire un `GroupShape`** che conterrà le singole forme.
3. **Creare una forma rettangolare**, impostarne le dimensioni e aggiungerla al gruppo.
4. **Creare una forma ellittica**, impostarne la dimensione e la posizione, e aggiungerla al gruppo.
5. **Salvare** il documento.

Ogni passaggio è spiegato di seguito, e il codice sorgente completo segue la spiegazione.

### Passo 1: Inizializzare il documento e il builder

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

`Document` rappresenta l'intero file Word, mentre `DocumentBuilder` fornisce un'API fluida per inserire contenuti. Inizializzarli è obbligatorio prima di poter aggiungere qualsiasi forma.

### Passo 2: Inserire una forma di gruppo

```csharp
        // Step 2: Insert a group shape that will hold multiple child shapes
        GroupShape group = builder.InsertGroupShape();
```

Un `GroupShape` funziona come un contenitore; tutte le forme figlie si muovono insieme. Questo è il modo consigliato per **raggruppare forme in Word** quando hai bisogno di trasformazioni collettive (ad esempio spostare, ruotare o eliminare).

### Passo 3: Creare il rettangolo e impostarne le dimensioni

```csharp
        // Step 3: Create a rectangle shape, set its size, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle);
```

Qui **creiamo una forma rettangolare** e **impostiamo la dimensione della forma** assegnando `Width` e `Height`. In Aspose.Words, le dimensioni sono espresse in punti (1 pt ≈ 1/72 in). Impostare esplicitamente le dimensioni garantisce che il rettangolo appaia esattamente come previsto.

### Passo 4: Creare l'ellisse, impostare le dimensioni e posizionarla

```csharp
        // Step 4: Create an ellipse shape, set its size and position, and add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position relative to the group
        group.AppendChild(ellipse);
```

Le **dimensioni della forma** per l'ellisse sono identiche per larghezza e altezza, producendo un cerchio perfetto. La proprietà `Left` dimostra **impostare la posizione della forma**: l'ellisse inizia a 120 pt a destra dell'origine del gruppo, così non si sovrappone al rettangolo.

### Passo 5: Salvare il documento

```csharp
        // Step 5: Save the document containing the grouped shapes
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document saved successfully.");
    }
}
```

Il salvataggio scrive il file Word su disco. Puoi aprire `GroupShape.docx` in Microsoft Word per verificare che il rettangolo e l'ellisse siano raggruppati e posizionati correttamente.

## Impostare le dimensioni e la grandezza della forma – approfondimento

- **Punti vs. pollici**: 72 pt = 1 in. Se preferisci i pollici, moltiplica per 72 (ad es. `2.5 * 72` per 2,5 in).
- **Scaling automatico**: Se ometti `Width` o `Height`, la forma utilizza la sua dimensione predefinita. Imposta esplicitamente **la dimensione della forma** per evitare sorprese di layout.
- **Rapporto d'aspetto**: Per forme come `Ellipse`, mantenere `Width` e `Height` uguali preserva un aspetto circolare.

## Posizionare una forma in Word

Le proprietà `Left` e `Top` controllano lo spostamento della forma all'interno del suo contenitore (il gruppo o la pagina). Valori positivi spostano la forma a destra/giù; valori negativi la spostano a sinistra/alto. Quando le forme sono raggruppate, le posizioni sono relative all'origine del gruppo, il che semplifica i calcoli di layout.

## Raggruppare forme in Word usando Aspose.Words

Il raggruppamento è essenziale quando vuoi che più forme agiscano come un'unica unità. L'oggetto `GroupShape`:

- Supporta `AppendChild` per aggiungere qualsiasi `Shape` (rettangolo, ellisse, immagine, ecc.).
- Consente di spostare, ruotare o eliminare l'intero gruppo con una sola chiamata.
- Mantiene le posizioni delle forme figlie relative al gruppo, rendendo più semplice gestire diagrammi complessi.

**Suggerimento professionale:** Dopo aver aggiunto tutte le forme figlie, puoi regolare `Width`, `Height`, `Left` e `Top` del gruppo per riposizionare l'intera collezione in un unico passaggio.

## Esempio completo eseguibile

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Include tutte le direttive `using`, un metodo `Main` e commenti che spiegano ogni riga.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a GroupShape to hold child shapes
        GroupShape group = builder.InsertGroupShape();

        // 3️⃣ Create a rectangle, set its dimensions, and add it to the group
        Shape rectangle = new Shape(doc, ShapeType.Rectangle);
        rectangle.Width = 100;   // set shape size (width) in points
        rectangle.Height = 50;   // set shape size (height) in points
        group.AppendChild(rectangle); // add rectangle to the group

        // 4️⃣ Create an ellipse, set size and position, then add it to the group
        Shape ellipse = new Shape(doc, ShapeType.Ellipse);
        ellipse.Width = 80;      // set shape dimensions (width)
        ellipse.Height = 80;     // set shape dimensions (height)
        ellipse.Left = 120;      // set shape position inside the group
        group.AppendChild(ellipse); // add ellipse to the group

        // 5️⃣ Save the document
        doc.Save("GroupShape.docx");
        Console.WriteLine("Document 'GroupShape.docx' created with a rectangle and an ellipse grouped together.");
    }
}
```

**Output previsto:** Dopo aver eseguito il programma, `GroupShape.docx` appare nella cartella di esecuzione. Aprendolo in Word vedrai un rettangolo (100 pt × 50 pt) a sinistra e un'ellisse (80 pt × 80 pt) posizionata a 120 pt a destra, entrambe all'interno di un unico oggetto raggruppato.

![Word document with grouped rectangle and ellipse](grouped_shapes.png){: .center alt="Screenshot di un documento Word che mostra un rettangolo e un'ellisse raggruppati creati con C#" }

*L'immagine sopra illustra il risultato finale; il rettangolo e l'ellisse sono selezionabili come un unico gruppo.*

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|----------|
| **Posso aggiungere più di due forme?** | Sì. Chiama `group.AppendChild(yourShape)` per ogni forma aggiuntiva. |
| **E se devo ruotare il gruppo?** | Usa `group.RotationAngle = 45;` (gradi) dopo aver aggiunto tutti i figli. |
| **Come cambio il colore di sfondo del gruppo?** | Imposta `group.FillColor = System.Drawing.Color.LightGray;`. |
| **Funziona con file .doc?** | Aspose.Words supporta `.doc` e `.docx`. Lo stesso codice funziona; basta cambiare l'estensione del file in `Save`. |
| **C'è un impatto sulla memoria quando si raggruppano molte forme?** | Il raggruppamento aggiunge un overhead minimo. La principale preoccupazione è il numero totale di forme; mantienilo ragionevole per documenti di grandi dimensioni. |

## Conclusione

In questo tutorial hai imparato come **creare una forma rettangolare** in un file Word usando C#, come **impostare la dimensione della forma**, **impostare le dimensioni della forma**, **impostare la posizione della forma**, e infine come **raggruppare forme in Word** con Aspose.Words. L'esempio completo dimostra un approccio pulito e manutenibile che puoi estendere a diagrammi, grafici o grafiche personalizzate più complesse.

Prossimi passi consigliati:

- Aggiungere testo all'interno delle forme (`Shape.TextPath.Text = "Hello"`).
- Inserire immagini in un `GroupShape`.
- Esportare le forme raggruppate in PDF con `doc.Save("output.pdf")`.

Sentiti libero di sperimentare con diverse dimensioni, posizioni e tipi di forma aggiuntivi per soddisfare le esigenze del tuo progetto. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche illustrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Come creare una forma rettangolare e raggruppare forme in Word con Aspose.Words](/words/english/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/)
- [Creare una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}