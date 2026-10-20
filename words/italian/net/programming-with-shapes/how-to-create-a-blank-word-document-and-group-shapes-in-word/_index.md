---
category: general
date: 2026-10-20
description: Scopri come creare un documento Word vuoto, raggruppare le forme in Word,
  impostare il colore di riempimento della forma e utilizzare il tipo di avvolgimento
  inline con un esempio completo in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- group shapes in word
- how to group shapes
- set shape fill color
- wrap type inline
language: it
lastmod: 2026-10-20
og_description: Crea un documento Word vuoto, raggruppa le forme in Word e imposta
  il colore di riempimento della forma con tipo di avvolgimento inline usando Aspose.Words
  e C#. Segui il tutorial completo.
og_image_alt: Screenshot of a blank Word document containing a grouped rectangle and
  text box created with Aspose.Words
og_title: Crea un documento Word vuoto e raggruppa le forme in Word – guida passo
  passo
schemas:
- author: Aspose
  dateModified: '2026-10-20'
  description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  headline: How to create a blank Word document and group shapes in Word using Aspose.Words
  type: TechArticle
- description: Learn how to create a blank Word document, group shapes in Word, set
    shape fill color, and use wrap type inline with a complete C# example.
  name: How to create a blank Word document and group shapes in Word using Aspose.Words
  steps:
  - name: Expected result
    text: '* A .docx file containing a single paragraph. * Inside the paragraph, an
      inline group that looks like a single composite object. * The rectangle is filled
      with light blue, and the text box displays “Grouped text”.'
  - name: What if I need the group to float rather than be inline?
    text: Replace `WrapType.Inline` with `WrapType.TopBottom` (or any other `WrapType`
      enum value). Floating groups can be positioned independently of paragraph flow,
      but they lose the automatic inline alignment.
  - name: Can I add more shapes, such as circles or images?
    text: Yes. Create additional `Shape` objects with `ShapeType.Ellipse` or `ShapeType.Image`,
      configure their properties, and call `group.AppendChild(newShape)`. The group
      will automatically expand to accommodate the new bounds if you update `group.Bounds`
      accordingly.
  - name: How do I change the group’s overall size after adding children?
    text: Adjust `group.Bounds` after all children are appended, or compute the union
      of child bounds programmatically. This ensures the group’s hit‑test area matches
      the visual content.
  - name: What if the output folder does not exist?
    text: 'Aspose.Words throws a `DirectoryNotFoundException`. Create the directory
      first:'
  - name: Does this work with .NET Framework instead of .NET Core?
    text: All APIs used (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) are
      available in the .NET Framework version of Aspose.Words, so the same code works
      unchanged.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Come creare un documento Word vuoto e raggruppare le forme in Word usando Aspose.Words
url: /it/net/programming-with-shapes/how-to-create-a-blank-word-document-and-group-shapes-in-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word vuoto e raggruppare forme in Word

Se hai bisogno di **creare un documento Word vuoto** che contenga più forme che agiscono come un'unica unità, questa guida ti mostra esattamente come fare. Vedrai come **raggruppare forme in Word**, impostare il colore di riempimento di una forma e applicare **wrap type inline** — il tutto con un conciso programma C# eseguibile.

Il tutorial ti guida attraverso ogni riga di codice, spiega perché ogni passaggio è importante e evidenzia le insidie comuni. Alla fine avrai un file .docx che mostra un rettangolo e una casella di testo raggruppati insieme, pronti per ulteriori automazioni.

## Cosa imparerai

* Come inizializzare un file Word vuoto con Aspose.Words.
* Il modo corretto per creare un **GroupShape** e aggiungere forme figlie.
* Tecniche per **set shape fill color** e controllare il posizionamento.
* Utilizzare **wrap type inline** affinché il gruppo si comporti come un unico oggetto inline.
* Come salvare e verificare il risultato.

Non è necessaria alcuna esperienza pregressa con Aspose.Words, ma dovresti sentirti a tuo agio con la sintassi base di C# e avere Visual Studio (o un altro IDE) installato.

## Prerequisiti

| Requisito | Motivo |
|-------------|--------|
| .NET 6.0 o successivo | Fornisce il runtime per il progetto C#. |
| Aspose.Words per .NET (ultima versione) | Fornisce le classi `Document`, `DocumentBuilder` e le classi di forma utilizzate nell'esempio. |
| Un percorso di cartella scrivibile | La chiamata `doc.Save` richiede una directory valida per scrivere il file di output. |
| Conoscenza base di C# | Ti consente di seguire il codice e modificarlo per i tuoi scenari. |

Installa Aspose.Words via NuGet:

```bash
dotnet add package Aspose.Words
```

---

## Passo 1: Creare un documento Word vuoto

La prima operazione è **creare un documento Word vuoto**. La classe `Document` di Aspose.Words rappresenta un file Word in memoria, e `DocumentBuilder` fornisce un'API comoda per modificarlo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new empty document.
Document doc = new Document();

// Attach a builder to the document for easy content insertion.
DocumentBuilder builder = new DocumentBuilder(doc);
```

*Perché è importante*: Iniziare con un documento pulito garantisce che la forma di gruppo che aggiungi sarà l'unico contenuto, rendendo la verifica semplice.

## Passo 2: Definire una GroupShape con wrap type inline

Una **GroupShape** funge da contenitore per altre forme. Impostare il suo `WrapType` a `Inline` assicura che il gruppo si comporti come un unico oggetto inline nel flusso del paragrafo.

```csharp
// Create a group shape that will hold the rectangle and text box.
GroupShape group = new GroupShape(doc, WrapType.Inline);

// Define the bounding rectangle of the group (x, y, width, height).
group.Bounds = new System.Drawing.RectangleF(0, 0, 300, 200);
```

*Perché è importante*: Usare **wrap type inline** impedisce al gruppo di galleggiare lontano dal testo circostante, il che è essenziale quando vuoi che il gruppo si muova come un'unità.

## Passo 3: Aggiungere un rettangolo e impostare il colore di riempimento della forma

Un rettangolo è un elemento visivo comune. Il costruttore `Shape` accetta un `ShapeType`; poi specifichiamo le dimensioni e il colore di riempimento.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width = 150,
    Height = 100,
    FillColor = System.Drawing.Color.LightBlue
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

*Perché è importante*: La proprietà `FillColor` dimostra **set shape fill color** in pratica, dando al rettangolo uno sfondo azzurro chiaro che risalta nel documento finale.

## Passo 4: Aggiungere una casella di testo – come raggruppare forme in modo efficace

Una casella di testo fornisce testo modificabile all'interno del gruppo. Posizionala relativamente al sistema di coordinate del gruppo regolando la proprietà `Top`.

```csharp
// Create a text box shape.
Shape textBox = new Shape(doc, ShapeType.TextBox)
{
    Width = 120,
    Height = 60,
    TextBoxText = "Grouped text",
    Top = 110 // Position below the rectangle inside the group.
};

// Append the text box to the group.
group.AppendChild(textBox);
```

*Perché è importante*: Questo passaggio risponde a **how to group shapes** — aggiungendo ogni forma figlia alla stessa istanza di `GroupShape`. L'offset `Top` assicura che la casella di testo appaia sotto il rettangolo, dimostrando un controllo preciso del layout.

## Passo 5: Inserire la GroupShape completata nel documento

Ora che il gruppo contiene entrambe le forme figlie, inseriscilo nella posizione corrente del builder.

```csharp
// Insert the group shape at the builder’s cursor location.
builder.InsertNode(group);
```

*Perché è importante*: Inserire il gruppo come un unico nodo garantisce che Word tratti il rettangolo e la casella di testo come un unico oggetto logico, preservando le loro posizioni relative durante la modifica.

## Passo 6: Salvare il documento e verificare l'output

Infine, scrivi il documento su disco. Sostituisci `YOUR_DIRECTORY` con un percorso reale sulla tua macchina.

```csharp
// Save the document to the specified folder.
doc.Save("YOUR_DIRECTORY/GroupShape.docx");
```

Quando apri `GroupShape.docx` in Microsoft Word, dovresti vedere un rettangolo azzurro chiaro con una casella di testo etichettata “Grouped text” posizionata direttamente sotto di esso. Selezionando una delle forme, verrà selezionato l'intero gruppo, confermando che **group shapes in Word** funziona come previsto.

### Risultato atteso

* Un file .docx contenente un singolo paragrafo.
* All'interno del paragrafo, un gruppo inline che appare come un unico oggetto composito.
* Il rettangolo è riempito di azzurro chiaro, e la casella di testo mostra “Grouped text”.

![Screenshot del documento Word generato](grouped_shapes.png){.center width=600 alt="Screenshot di un documento Word vuoto con rettangolo raggruppato e casella di testo creati con Aspose.Words"}

## Domande comuni e gestione dei casi limite

### Cosa succede se ho bisogno che il gruppo fluttui invece di essere inline?

Sostituisci `WrapType.Inline` con `WrapType.TopBottom` (o qualsiasi altro valore dell'enumerazione `WrapType`). I gruppi fluttuanti possono essere posizionati indipendentemente dal flusso del paragrafo, ma perdono l'allineamento inline automatico.

### Posso aggiungere altre forme, come cerchi o immagini?

Sì. Crea ulteriori oggetti `Shape` con `ShapeType.Ellipse` o `ShapeType.Image`, configura le loro proprietà e chiama `group.AppendChild(newShape)`. Il gruppo si espanderà automaticamente per contenere i nuovi limiti se aggiorni `group.Bounds` di conseguenza.

### Come modificare la dimensione complessiva del gruppo dopo aver aggiunto le forme figlie?

Regola `group.Bounds` dopo aver aggiunto tutte le forme figlie, oppure calcola l'unione dei limiti delle forme figlie programmaticamente. Questo garantisce che l'area di hit‑test del gruppo corrisponda al contenuto visivo.

### Cosa succede se la cartella di output non esiste?

Aspose.Words lancia una `DirectoryNotFoundException`. Crea prima la directory:

```csharp
string outputPath = "YOUR_DIRECTORY";
Directory.CreateDirectory(outputPath);
doc.Save(Path.Combine(outputPath, "GroupShape.docx"));
```

### Funziona con .NET Framework invece di .NET Core?

Tutte le API utilizzate (`Document`, `DocumentBuilder`, `GroupShape`, `Shape`) sono disponibili nella versione .NET Framework di Aspose.Words, quindi lo stesso codice funziona senza modifiche.

## Consigli professionali

* **Consiglio di performance** – Riutilizza un'unica istanza di `DocumentBuilder` quando inserisci molti gruppi; creare un nuovo builder per ogni gruppo aggiunge overhead.
* **Coerenza visiva** – Imposta `rectangle.StrokeColor` per corrispondere a `FillColor` per un aspetto uniforme, oppure imposta `rectangle.LineWidth = 0` per nascondere il bordo.
* **Debugging** – Chiama `doc.UpdatePageLayout()` prima di salvare se modifichi molte forme; questo costringe Word a ricalcolare il layout e può prevenire ritagli inaspettati.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **raggruppare forme in Word**, **impostare il colore di riempimento della forma**, e applicare **wrap type inline** usando Aspose.Words per .NET. L'esempio completo dimostra l'approccio standard per costruire grafiche composite che si comportano come un unico oggetto in Word.

Da qui puoi esplorare:

* Aggiungere forme aggiuntive come immagini o grafici.
* Sperimentare con diversi valori di `WrapType` per gruppi fluttuanti.
* Automatizzare la generazione batch di diagrammi raggruppati su più documenti.

Sentiti libero di adattare il codice ai tuoi scenari di automazione e condividi i tuoi risultati nei commenti!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea Group Shape in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea un documento Word vuoto con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)
- [Come salvare PDF da Word con forme inline – Guida completa](/words/english/java/document-conversion-and-export/how-to-save-pdf-from-word-with-inline-shapes-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}