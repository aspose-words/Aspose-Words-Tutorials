---
category: general
date: 2026-09-21
description: Scopri come raggruppare le forme in Word usando Aspose.Words per C#.
  Questa guida passo‑passo copre la creazione, il posizionamento e il salvataggio
  delle forme raggruppate.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- group shapes in Word
- Aspose.Words shape grouping
- C# Word shape manipulation
- DocumentBuilder insert shape
- GroupShape container
language: it
lastmod: 2026-09-21
og_description: Raggruppa forme in Word usando Aspose.Words per C#. Segui questo conciso
  tutorial per creare, posizionare e salvare forme raggruppate programmaticamente.
og_image_alt: Screenshot of grouped shapes in Word document created with Aspose.Words
og_title: Raggruppa forme in Word con Aspose.Words – guida completa C#
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  headline: How to group shapes in Word with Aspose.Words for C#
  type: TechArticle
- description: Learn how to group shapes in Word using Aspose.Words for C#. This step‑by‑step
    guide covers creating, positioning, and saving grouped shapes.
  name: How to group shapes in Word with Aspose.Words for C#
  steps:
  - name: Create a blank document and a `DocumentBuilder`
    text: '```csharp using Aspose.Words; using Aspose.Words.Drawing;'
  - name: Insert the first rectangle shape
    text: '```csharp // Insert a rectangle that is 100 points wide and 50 points tall.
      Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); ```'
  - name: Insert the second rectangle and offset it
    text: '```csharp // Insert the second rectangle with the same dimensions. Shape
      shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);'
  - name: Create a `GroupShape` large enough for both rectangles
    text: '```csharp // The group must be wide enough to contain both shapes (100
      pt + 120 pt + 100 pt = 320 pt). // We give a little extra margin, so the group
      width is set to 300 pt and height to 100 pt. GroupShape group = new GroupShape(doc,
      300, 100); ```'
  - name: Append the individual shapes to the group
    text: '```csharp group.AppendChild(shape1); group.AppendChild(shape2); ```'
  - name: Insert the grouped shape back into the document
    text: '```csharp // Insert the GroupShape at the current builder position. builder.InsertNode(group);
      ```'
  - name: Save the document
    text: '```csharp // Replace YOUR_DIRECTORY with an absolute or relative path where
      you have write permission. doc.Save("YOUR_DIRECTORY/GroupedShapes.docx"); ```'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Come raggruppare le forme in Word con Aspose.Words per C#
url: /it/net/programming-with-shapes/how-to-group-shapes-in-word-with-aspose-words-for-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come raggruppare forme in Word con Aspose.Words per C#

Se devi **raggruppare forme in Word** in modo programmatico, Aspose.Words lo rende semplice. Questo tutorial ti mostra come creare due forme rettangolari, posizionarle una accanto all'altra, combinarle in un `GroupShape` e salvare il risultato come file DOCX.

Vedrai un esempio completo, eseguibile, spiegazioni sul perché ogni passaggio è importante e consigli per gestire casi limite comuni come forme sovrapposte o dimensioni dinamiche. Alla fine di questa guida potrai integrare il raggruppamento di forme in qualsiasi progetto di automazione Word.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 (o successivo) installato – Aspose.Words supporta .NET Standard 2.0+, .NET Core e .NET Framework.  
* Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione temporanea) – la libreria funziona senza licenza ma aggiunge una filigrana.  
* Visual Studio 2022 (o qualsiasi IDE C#) per compilare ed eseguire il campione.

Non sono necessari pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Come raggruppare forme in Word usando Aspose.Words

Il cuore della soluzione è un oggetto **`GroupShape`** che funge da contenitore per le singole forme. Di seguito suddividiamo il processo in passaggi chiari.

### Passo 1: Creare un documento vuoto e un `DocumentBuilder`

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new empty Word document.
Document doc = new Document();

// DocumentBuilder provides convenient methods for inserting content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché questo passaggio?*  
`Document` rappresenta l'intero file DOCX, mentre `DocumentBuilder` fornisce metodi fluenti (ad es., `InsertShape`) che inseriscono automaticamente i nuovi elementi nella posizione corrente del cursore.

### Passo 2: Inserire la prima forma rettangolare

```csharp
// Insert a rectangle that is 100 points wide and 50 points tall.
Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

La chiamata `InsertShape` aggiunge la forma al documento e restituisce un oggetto `Shape` che puoi configurare ulteriormente (colore, bordo, ecc.). La dimensione è espressa in punti (1 pt ≈ 1/72 in).

### Passo 3: Inserire il secondo rettangolo e spostarlo

```csharp
// Insert the second rectangle with the same dimensions.
Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

// Move the second shape 120 points to the right so the two rectangles do not overlap.
shape2.Left = 120; // Horizontal offset from the left edge of the page.
```

Impostare `Left` posiziona la forma rispetto al margine della pagina. L'offset deve essere maggiore della larghezza della prima forma (100 pt) per evitare sovrapposizioni; usiamo 120 pt per lasciare un piccolo spazio.

### Passo 4: Creare un `GroupShape` sufficientemente grande per entrambi i rettangoli

```csharp
// The group must be wide enough to contain both shapes (100 pt + 120 pt + 100 pt = 320 pt).
// We give a little extra margin, so the group width is set to 300 pt and height to 100 pt.
GroupShape group = new GroupShape(doc, 300, 100);
```

`GroupShape` richiede il `Document` proprietario e le dimensioni del contenitore. La larghezza del contenitore deve superare il bordo destro della forma più distante; altrimenti, la seconda forma verrebbe ritagliata.

### Passo 5: Aggiungere le singole forme al gruppo

```csharp
group.AppendChild(shape1);
group.AppendChild(shape2);
```

L'operazione di append sposta le forme nella collezione interna del gruppo. Dopo questa chiamata le forme non sono più oggetti indipendenti nell'albero del documento: appartengono al gruppo.

### Passo 6: Inserire la forma raggruppata nuovamente nel documento

```csharp
// Insert the GroupShape at the current builder position.
builder.InsertNode(group);
```

`InsertNode` posiziona l'intero `GroupShape` dove il cursore si trova attualmente. Se hai bisogno del gruppo in un paragrafo specifico, sposta prima il builder su quel paragrafo.

### Passo 7: Salvare il documento

```csharp
// Replace YOUR_DIRECTORY with an absolute or relative path where you have write permission.
doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
```

Il file risultante contiene due rettangoli che si comportano come un unico oggetto—puoi spostarli, ridimensionarli o eliminarli insieme in Microsoft Word.

## Codice sorgente completo

Unendo tutti i passaggi otteniamo un programma autonomo:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a DocumentBuilder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert the first rectangle (100 pt × 50 pt).
        Shape shape1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);

        // 3️⃣ Insert the second rectangle and offset it horizontally.
        Shape shape2 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        shape2.Left = 120; // Prevent overlap.

        // 4️⃣ Create a GroupShape container large enough for both.
        GroupShape group = new GroupShape(doc, 300, 100);

        // 5️⃣ Add both rectangles to the group.
        group.AppendChild(shape1);
        group.AppendChild(shape2);

        // 6️⃣ Insert the grouped shape back into the document.
        builder.InsertNode(group);

        // 7️⃣ Save the document.
        doc.Save("YOUR_DIRECTORY/GroupedShapes.docx");
    }
}
```

**Output previsto:** L'apertura di *GroupedShapes.docx* in Microsoft Word mostra due rettangoli affiancati, trattati come un unico oggetto selezionabile. Trascinando il gruppo, entrambi i rettangoli si muovono insieme.

## Varianti comuni e casi limite

| Situazione | Regolazione consigliata |
|------------|--------------------------|
| **Più di due forme** | Crea oggetti `Shape` aggiuntivi, posizionali di conseguenza e aggiungili tutti allo stesso `GroupShape`. |
| **Dimensione dinamica** | Calcola la larghezza/altezza del gruppo in base ai valori massimi di `Right` e `Bottom` delle forme figlie. |
| **Tipi di forma diversi** | `ShapeType.Ellipse`, `ShapeType.Triangle`, ecc., possono essere inseriti allo stesso modo; il contenitore del gruppo non si preoccupa del tipo. |
| **Forme ruotate** | Imposta `shape.Rotation = 45;` prima di aggiungere; la rotazione viene preservata all'interno del gruppo. |
| **Salvataggio come PDF** | Chiama `doc.Save("GroupedShapes.pdf");` – il gruppo viene mantenuto nella resa PDF. |

**Consiglio professionale:** Dopo aver raggruppato, puoi comunque modificare le singole forme accedendo a `group.GetChildNodes(NodeType.Shape, true)`. Questo è utile quando devi cambiare il colore di riempimento di un rettangolo senza rompere il gruppo.

## Come verificare il raggruppamento programmaticamente

Se devi confermare che le forme siano state raggruppate correttamente (ad es., nei test unitari), esamina la gerarchia dei nodi del documento:

```csharp
NodeCollection groups = doc.GetChildNodes(NodeType.GroupShape, true);
Console.WriteLine($"Number of groups: {groups.Count}");
Console.WriteLine($"Children in first group: {groups[0].GetChildNodes(NodeType.Shape, true).Count}");
```

L'output dovrebbe essere:

```
Number of groups: 1
Children in first group: 2
```

Ciò conferma che le **forme di gruppo in Word** sono state create come previsto.

## Conclusione

Ora sai come **raggruppare forme in Word** con Aspose.Words per C#. Il processo prevede la creazione di forme individuali, il loro posizionamento, l'incapsulamento in un `GroupShape` e l'inserimento del gruppo nel documento. Con l'esempio completo sopra puoi estendere la tecnica a qualsiasi numero di forme, a tipi diversi o persino combinarla con caselle di testo e immagini.

Successivamente, esplora argomenti correlati come **raggruppamento di forme Aspose.Words**, **manipolazione di forme Word in C#** e **DocumentBuilder insert shape** per scenari di automazione documentale più avanzati. Sperimenta con dimensioni dinamiche, raggruppamento condizionale ed esportazione in PDF per sfruttare appieno la potenza di Aspose.Words.

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserisci forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Crea forma rettangolare in Word con Aspose.Words – Guida passo‑per‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Tutorial ombra forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}