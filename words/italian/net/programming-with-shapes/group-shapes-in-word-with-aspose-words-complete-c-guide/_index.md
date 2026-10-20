---
category: general
date: 2026-07-19
description: Raggruppa le forme in Word usando Aspose.Words. Scopri come aggiungere
  una forma rettangolare, definire una forma ellittica e inserire forme nei documenti
  Word.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in word
- add rectangle shape
- how to group shapes
- insert shape into word
- define ellipse shape
language: it
lastmod: 2026-07-19
og_description: Raggruppa forme in Word con Aspose.Words. Master aggiunge una forma
  rettangolare, definisce una forma ellittica e inserisce la forma nei documenti Word.
og_image_alt: Screenshot of grouped shapes in a Word document created with Aspose.Words
og_title: Raggruppare le forme in Word – Tutorial passo‑passo C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  headline: Group Shapes in Word with Aspose.Words – Complete C# Guide
  type: TechArticle
- description: Group shapes in Word using Aspose.Words. Learn how to add rectangle
    shape, define ellipse shape, and insert shape into Word documents.
  name: Group Shapes in Word with Aspose.Words – Complete C# Guide
  steps:
  - name: Set Up the Document and Builder
    text: We start by creating an empty `Document` and a `DocumentBuilder`. The builder
      is our “pen” that lets us insert content wherever we need it.
  - name: Add Rectangle Shape (add rectangle shape)
    text: Now we **add rectangle shape** to the document. We set its size, position,
      and fill colour to make it stand out.
  - name: Define Ellipse Shape (define ellipse shape)
    text: Next, we **define ellipse shape**. Notice the different `ShapeType` and
      the offset (`Left = 120`) so the ellipse sits beside the rectangle.
  - name: (Optional) Insert Individual Shapes for Preview
    text: If you want to see each shape before grouping, you can **insert shape into
      Word** individually. This step is optional but handy for debugging.
  - name: How to Group Shapes – Create a GroupShape
    text: 'Here’s the core of the tutorial: **how to group shapes**. We create a `GroupShape`,
      attach our rectangle and ellipse, and decide how the group behaves with surrounding
      text.'
  - name: Insert the Grouped Shape into the Document (insert shape into word)
    text: Now we **insert shape into Word**—but this time it’s the grouped container,
      not the individual pieces.
  - name: Save the Document
    text: Finally, write the file to disk. You can change the path to suit your project
      layout.
  - name: What if I need more than two shapes?
    text: Just keep calling `groupShape.AppendChild(yourNewShape);` before inserting
      the group. The API imposes no limit on the number of child shapes.
  - name: Can I rotate or resize the whole group?
    text: Absolutely. `GroupShape` inherits from `Shape`, so you can set properties
      like `RotationAngle`, `Width`, or `Height` on the group itself, and all child
      shapes will follow.
  - name: How do I change the group’s background colour?
    text: Use `groupShape.FillColor`. This fills the invisible bounding box; it can
      be handy for highlighting.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
title: Forme raggruppate in Word con Aspose.Words – Guida completa C#
url: /it/net/programming-with-shapes/group-shapes-in-word-with-aspose-words-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Raggruppare forme in Word – Guida completa in C#

Ti sei mai chiesto come **raggruppare forme in Word** senza impazzire con l'interfaccia? Non sei solo. Che tu stia generando contratti, volantini o diagrammi in modo programmatico, poter **aggiungere una forma rettangolare**, **definire una forma ellittica** e poi **raggruppare forme in Word** può farti risparmiare ore di lavoro manuale.

In questo tutorial percorreremo un esempio reale usando **Aspose.Words per .NET**. Alla fine saprai esattamente come **inserire una forma in Word**, combinarle e produrre un documento rifinito da distribuire a clienti o colleghi.

---

## Cosa ti serve

Prima di iniziare, assicurati di avere:

- **Aspose.Words per .NET** (ultima versione, ad es. 24.9). Puoi ottenerlo da NuGet con `Install-Package Aspose.Words`.
- Un ambiente di sviluppo .NET (Visual Studio 2022 o VS Code con l’estensione C# vanno benissimo).
- Familiarità di base con la sintassi C#—nulla di complicato, solo le consuete istruzioni `using` e la creazione di oggetti.

Tutto qui. Nessuna libreria aggiuntiva, nessun interop COM, solo codice gestito puro.

---

## Come raggruppare forme in Word usando Aspose.Words

Di seguito trovi una descrizione passo‑passo che rispecchia il codice che hai già. Ogni passaggio spiega **perché** lo facciamo, non solo **cosa** fa la riga, così potrai adattare lo schema a qualsiasi forma ti serva.

### Passo 1: Configurare il documento e il builder

Iniziamo creando un `Document` vuoto e un `DocumentBuilder`. Il builder è la nostra “penna” che ci permette di inserire contenuti dove vogliamo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
// The builder will help us place shapes and text
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Perché?** L'oggetto `Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` fornisce un'API comoda per inserire nodi (come le forme) senza doversi occupare dell'albero dei nodi sottostante.

### Passo 2: Aggiungere forma rettangolare (add rectangle shape)

Ora **aggiungiamo una forma rettangolare** al documento. Impostiamo dimensioni, posizione e colore di riempimento per farla risaltare.

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 100;                     // Width in points
rectangleShape.Height = 50;                      // Height in points
rectangleShape.Left   = 0;                       // X‑coordinate
rectangleShape.Top    = 0;                       // Y‑coordinate
rectangleShape.FillColor = System.Drawing.Color.LightBlue;
```

> **Suggerimento:** Puoi cambiare `FillColor` con qualsiasi `System.Drawing.Color` preferisci. È utile quando hai bisogno di sezioni codificate a colori in un report.

### Passo 3: Definire forma ellittica (define ellipse shape)

Successivamente, **definiamo una forma ellittica**. Nota il diverso `ShapeType` e lo spostamento (`Left = 120`) così l'ellisse si posiziona accanto al rettangolo.

```csharp
// Create an ellipse shape
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width  = 80;
ellipseShape.Height = 40;
ellipseShape.Left   = 120;   // Position it to the right of the rectangle
ellipseShape.Top    = 0;
ellipseShape.FillColor = System.Drawing.Color.LightCoral;
```

> **Perché è importante:** Posizionando le forme in modo esplicito, controlli come appaiono prima di raggrupparle. Se ti affidi al layout automatico, il raggruppamento potrebbe risultare disallineato.

### Passo 4: (Opzionale) Inserire forme individuali per l'anteprima

Se vuoi vedere ogni forma prima del raggruppamento, puoi **inserire forma in Word** singolarmente. Questo passaggio è opzionale ma comodo per il debug.

```csharp
// Insert the rectangle and ellipse separately (useful for preview)
builder.InsertNode(rectangleShape);
builder.InsertNode(ellipseShape);
```

> **Consiglio da esperto:** Commenta queste due righe una volta che sei sicuro che le forme siano corrette; altrimenti otterrai visualizzazioni duplicate dopo il raggruppamento.

### Passo 5: Come raggruppare forme – Creare un GroupShape

Ecco il cuore del tutorial: **come raggruppare forme**. Creiamo un `GroupShape`, aggiungiamo il rettangolo e l'ellisse, e decidiamo come il gruppo si comporta rispetto al testo circostante.

```csharp
// Create a container for the group
GroupShape groupShape = new GroupShape(document);

// Add the rectangle and ellipse to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// Set wrapping – Inline makes the group act like a character in the text flow
groupShape.WrapType = WrapType.Inline;
```

> **Spiegazione:** `GroupShape` è essenzialmente una mini‑canvas che contiene altre forme. Impostando `WrapType` su `Inline`, l'intero gruppo si muove come un'unica unità quando aggiungi o rimuovi testo.

### Passo 6: Inserire la forma raggruppata nel documento (insert shape into word)

Ora **inseriamo forma in Word**—ma questa volta è il contenitore raggruppato, non i singoli pezzi.

```csharp
// Insert the grouped shape at the current cursor position
builder.InsertNode(groupShape);
```

> **Cosa succede dietro le quinte?** La chiamata `InsertNode` aggiunge il `GroupShape` alla collezione di nodi del documento. Poiché il gruppo contiene già rettangolo ed ellisse, appaiono insieme come un unico oggetto.

### Passo 7: Salvare il documento

Infine, scrivi il file su disco. Puoi modificare il percorso per adattarlo alla struttura del tuo progetto.

```csharp
// Save the resulting .docx file
document.Save("YOUR_DIRECTORY/GroupShape.docx");
```

> **Risultato:** Apri `GroupShape.docx` in Microsoft Word e vedrai un rettangolo azzurro chiaro e un'ellisse corallo unite. Trascinando una, l'altra si muove insieme—esattamente ciò che promette “raggruppare forme in Word”.

---

## Conferma visiva

Di seguito trovi un mock‑up di come appaiono le forme raggruppate all'interno del file Word.  

![Screenshot delle forme raggruppate in un documento Word creato con Aspose.Words](grouped_shapes_placeholder.png "raggruppare forme in Word")

*Il testo alternativo dell'immagine contiene la parola chiave principale per accessibilità e SEO.*

---

## Domande frequenti e casi particolari

### E se avessi bisogno di più di due forme?

Basta continuare a chiamare `groupShape.AppendChild(tuaNuovaForma);` prima di inserire il gruppo. L'API non impone limiti al numero di forme figlie.

### Posso ruotare o ridimensionare l'intero gruppo?

Assolutamente. `GroupShape` eredita da `Shape`, quindi puoi impostare proprietà come `RotationAngle`, `Width` o `Height` sul gruppo stesso, e tutte le forme figlie seguiranno.

```csharp
groupShape.RotationAngle = 15;   // Rotate the entire group 15 degrees
groupShape.Width = 250;          // Stretch the group uniformly
```

### Come cambio il colore di sfondo del gruppo?

Usa `groupShape.FillColor`. Questo riempie il riquadro invisibile di delimitazione; può essere utile per evidenziare.

```csharp
groupShape.FillColor = System.Drawing.Color.LightGray;
```

### Funziona con formati Word più vecchi (.doc)?

`Aspose.Words` può salvare anche in `.doc`—basta cambiare l'estensione del file in `Save`. Tuttavia, alcune funzionalità avanzate di forma (come il raggruppamento) sono pienamente supportate solo nel formato OOXML `.docx`.

---

## Esempio completo funzionante

Copia‑incolla il blocco seguente in una nuova console app per vedere l'intero processo in azione. Nessun pezzo è mancante; è un **esempio completo e eseguibile**.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Add rectangle shape
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 100;
        rectangleShape.Height = 50;
        rectangleShape.Left   = 0;
        rectangleShape.Top    = 0;
        rectangleShape.FillColor = Color.LightBlue;

        // 3️⃣ Define ellipse shape
        Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
        ellipseShape.Width  = 80;
        ellipseShape.Height = 40;
        ellipseShape.Left   = 120;
        ellipseShape.Top    = 0;
        ellipseShape.FillColor = Color.LightCoral;

        // 4️⃣ (Optional) Preview individual shapes
        // builder.InsertNode(rectangleShape);
        // builder.InsertNode(ellipseShape);

        // 5️⃣ Group the shapes together
        GroupShape groupShape = new GroupShape(document);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.WrapType = WrapType.Inline;

        // 6️⃣ Insert the grouped shape into the document
        builder.InsertNode(groupShape);

        // 7️⃣ Save the file
        document.Save("GroupShape.docx");

        System.Console.WriteLine("Document created successfully!");
    }
}
```

**Output previsto:** Quando apri `GroupShape.docx`, vedrai un unico oggetto raggruppato composto da un rettangolo azzurro chiaro e un'ellisse corallo chiaro, perfettamente allineati fianco a fianco.

---

## Riepilogo

Abbiamo appena coperto tutto ciò che ti serve per **raggruppare forme in Word** con Aspose.Words:

1. Crea un documento e un builder.  
2. **Aggiungi forma rettangolare** e **definisci forma ellittica** con dimensioni esplicite.  
3. (Facoltativo) **inserisci forma in Word** per un'anteprima rapida.  
4. Usa `GroupShape` per **come raggruppare forme**—aggiungi ogni figlio, imposta il wrapping e inserisci.  
5. Salva il file e verifica il risultato.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci alternativi nei tuoi progetti.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑step guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}