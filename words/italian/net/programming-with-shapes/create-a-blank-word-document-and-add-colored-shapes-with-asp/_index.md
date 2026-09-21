---
category: general
date: 2026-09-21
description: Crea un documento Word vuoto con Aspose.Words, imposta la dimensione
  della forma, la posizione della forma, il colore della forma e salva il file docx
  in un unico walkthrough.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- set shape size
- save docx file
- set shape position
- set shape color
language: it
lastmod: 2026-09-21
og_description: Crea un documento Word vuoto, imposta la dimensione della forma, imposta
  la posizione della forma, imposta il colore della forma e salva il file docx con
  Aspose.Words in pochi minuti.
og_image_alt: Screenshot of a blank Word document containing two colored rectangles
  grouped together
og_title: Crea un documento Word vuoto e aggiungi forme colorate – Guida Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Create a blank Word document using Aspose.Words, set shape size, set
    shape position, set shape color, and save the docx file in a single walkthrough.
  headline: Create a blank Word document and add colored shapes with Aspose.Words
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
- shapes
title: Crea un documento Word vuoto e aggiungi forme colorate con Aspose.Words
url: /it/net/programming-with-shapes/create-a-blank-word-document-and-add-colored-shapes-with-asp/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e aggiungi forme colorate con Aspose.Words

Se hai bisogno di **creare un documento Word vuoto** programmaticamente, questa guida ti mostra come fare con Aspose.Words. Imparerai a **impostare la dimensione della forma**, **impostare la posizione della forma**, **impostare il colore della forma**, e infine **salvare il file docx** senza uscire dal tuo IDE.

Lavorare con file Word in C# spesso significa destreggiarsi con chiamate OpenXML a basso livello, ma Aspose.Words astrae la complessità. Alla fine di questo tutorial avrai un `.docx` completamente funzionante che contiene una forma raggruppata composta da due rettangoli colorati—perfetta per report, certificati o modelli personalizzati.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7+)
- Aspose.Words per .NET 23.9 o più recente (installare tramite NuGet: `Install-Package Aspose.Words`)
- Familiarità di base con C# e Visual Studio (o qualsiasi editor C#)

Non è necessario alcun file Word esistente; il tutorial inizia **creando un documento Word vuoto** da zero.

## Crea un documento Word vuoto con Aspose.Words

Il primo passo è istanziare un oggetto `Document`. Questo oggetto rappresenta un file Word vuoto in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Initialize a new, empty document.
Document document = new Document();

// DocumentBuilder gives you a cursor to add content.
DocumentBuilder builder = new DocumentBuilder(document);
```

`Document` inizia vuoto, che è esattamente ciò di cui hai bisogno quando **crei un documento Word vuoto**. Il `builder` sarà poi usato per inserire il gruppo di forme nella posizione corrente del cursore.

## Imposta la dimensione della forma e crea un GroupShape

Un `GroupShape` funziona come un contenitore che può contenere più forme individuali. Prima, definisci le dimensioni complessive del contenitore.

```csharp
// Create a GroupShape that will hold multiple shapes.
// Width = 300 points, Height = 200 points.
GroupShape groupShape = new GroupShape(document, 300, 200);

// Position the group on the page: 100 points from the left, 100 points from the top.
groupShape.Left = 100;
groupShape.Top  = 100;
```

Qui **impostiamo la dimensione della forma** per il gruppo stesso (300 × 200). Gli stessi nomi di proprietà (`Width`, `Height`) sono usati per ogni forma figlia, offrendoti un controllo dettagliato su ogni elemento.

## Aggiungi il primo rettangolo e imposta il colore della forma

Ora aggiungi un rettangolo al gruppo e assegnagli un colore di sfondo.

```csharp
// First rectangle – light blue background.
Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 0,          // Position relative to the group’s left edge.
    Top = 0,           // Position relative to the group’s top edge.
    FillColor = Color.LightBlue
};

// Append the rectangle to the group.
groupShape.AppendChild(rectangle1);
```

La proprietà `FillColor` **imposta il colore della forma**. Usare `System.Drawing.Color` ti permette di scegliere qualsiasi valore ARGB predefinito o personalizzato.

## Aggiungi un secondo rettangolo, imposta la sua dimensione, posizione e colore

Un secondo rettangolo dimostra come **impostare la posizione della forma** rispetto al gruppo e come cambiarne il colore.

```csharp
// Second rectangle – light coral background.
Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
{
    Width = 120,
    Height = 80,
    Left = 150,               // 150 points to the right of the group’s left edge.
    Top = 0,                  // Same vertical alignment as the first rectangle.
    FillColor = Color.LightCoral
};

groupShape.AppendChild(rectangle2);
```

Poiché la larghezza del gruppo è di 300 punti, i due rettangoli da 120 punti si adattano comodamente con uno spazio di 30 punti. Regola `Left` e `Top` se hai bisogno di un layout diverso.

## Inserisci il GroupShape nel documento

Con il gruppo completamente configurato, posizionalo nella posizione corrente del cursore.

```csharp
// Insert the completed group shape at the builder’s current location.
builder.InsertNode(groupShape);
```

`InsertNode` scrive la forma direttamente nel corpo del documento, preservando l'esatta **posizione della forma impostata** che hai definito in precedenza.

## Salva il file docx

L'ultimo passo è salvare il documento su disco. Questo dimostra l'operazione di **salvataggio del file docx**.

```csharp
// Define the output path (ensure the directory exists).
string outputPath = @"C:\Temp\GroupShape.docx";

// Save the document in DOCX format.
document.Save(outputPath);
```

Dopo aver eseguito il programma, apri `GroupShape.docx` in Microsoft Word. Dovresti vedere una pagina vuota con una forma raggruppata contenente due rettangoli colorati posizionati fianco a fianco.

### Output previsto

- Un file `.docx` a pagina singola.
- La pagina contiene una forma di gruppo posizionata a 100 pt dal margine sinistro e superiore.
- All'interno del gruppo, un rettangolo azzurro chiaro è a sinistra, e un rettangolo corallo chiaro è a destra, entrambi di 120 × 80 pt.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in un'applicazione console. Non sono richiesti file aggiuntivi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a blank Word document.
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Define a GroupShape and set its size and position.
        GroupShape groupShape = new GroupShape(document, 300, 200)
        {
            Left = 100,
            Top = 100
        };

        // 3️⃣ First rectangle – set size, position, and color.
        Shape rectangle1 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 0,
            Top = 0,
            FillColor = Color.LightBlue
        };
        groupShape.AppendChild(rectangle1);

        // 4️⃣ Second rectangle – set size, position, and color.
        Shape rectangle2 = new Shape(document, ShapeType.Rectangle)
        {
            Width = 120,
            Height = 80,
            Left = 150,
            Top = 0,
            FillColor = Color.LightCoral
        };
        groupShape.AppendChild(rectangle2);

        // 5️⃣ Insert the grouped shape into the document.
        builder.InsertNode(groupShape);

        // 6️⃣ Save the docx file.
        string outputPath = @"C:\Temp\GroupShape.docx";
        document.Save(outputPath);

        System.Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Eseguendo questo programma si crea il documento esattamente come descritto in precedenza, soddisfacendo tutti e quattro gli obiettivi: **creare un documento Word vuoto**, **impostare la dimensione della forma**, **impostare la posizione della forma**, **impostare il colore della forma**, e **salvare il file docx**.

## Varianti comuni e casi limite

| Scenario | Cosa cambiare | Perché è importante |
|----------|----------------|----------------------|
| **Tipi di forma diversi** | Sostituire `ShapeType.Rectangle` con `ShapeType.Ellipse`, `ShapeType.Triangle`, ecc. | Consente di creare grafiche più complesse senza immagini esterne. |
| **Dimensioni dinamiche** | Calcolare `Width` e `Height` dall'input dell'utente o da file di configurazione. | Rende la soluzione riutilizzabile su più modelli di documento. |
| **Salvataggio come PDF** | Call `document.Save("output.pdf", SaveFormat.Pdf);` | Se i destinatari hanno bisogno di un formato non modificabile, il PDF è una scelta sicura. |
| **Aggiungere testo all'interno di una forma** | Creare una forma `TextBox` e impostare `TextBox.Text`. | Utile per creare badge o annotazioni etichettate. |
| **Gruppi multipli su una pagina** | Ripetere i passaggi 2‑5 con valori diversi di `Left`/`Top`. | Consente di creare dashboard o layout a più sezioni. |

### Consiglio professionale

Quando hai bisogno di allineare le forme con precisione, usa la proprietà `ShapeBase.WrapType = WrapType.Inline` prima di inserire il gruppo. Questo costringe il gruppo a comportarsi come un paragrafo, evitando flussi di testo inaspettati attorno ad esso.

## Conclusione

Ora sai come **creare un documento Word vuoto** con Aspose.Words, **impostare la dimensione della forma**, **impostare la posizione della forma**, **impostare il colore della forma**, e **salvare il file docx**. L'esempio completo dimostra un modello pulito e riutilizzabile per aggiungere grafiche raggruppate a qualsiasi progetto di automazione Word.

Da qui puoi approfondire:

- Aggiungere più forme o immagini allo stesso `GroupShape` (variazioni di **impostare la dimensione della forma**, **impostare il colore della forma**).
- Usare `ShapeBase.Rotation` per ruotare i rettangoli per effetti decorativi.
- Esportare lo stesso documento come PDF o HTML per ampliare la distribuzione (alternativa **salvare il file docx**).

Sentiti libero di sperimentare con colori, dimensioni e logiche di layout diversi per soddisfare le tue specifiche esigenze di reporting o di creazione di modelli. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea Group Shape in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Tutorial Ombra Forma Aspose.Words – Aggiungi un'ombra a una forma Word in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}