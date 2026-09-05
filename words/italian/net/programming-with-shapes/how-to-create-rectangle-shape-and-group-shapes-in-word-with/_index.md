---
category: general
date: 2026-09-05
description: Crea una forma rettangolare in un documento Word usando Aspose.Words,
  poi impara come inserire una forma ellittica e raggruppare le forme in Word per
  layout più ricchi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create rectangle shape
- group shapes in word
- how to insert rectangle word
- how to insert ellipse word
- aspose.words create shapes
language: it
lastmod: 2026-09-05
og_description: Crea una forma rettangolare in un documento Word con Aspose.Words,
  quindi scopri come inserire una forma ellittica e raggruppare le forme in Word per
  layout complessi.
og_image_alt: Screenshot of a Word document showing a grouped rectangle and ellipse
  created with Aspose.Words
og_title: Crea una forma rettangolare e raggruppa le forme in Word – Guida Aspose.Words
schemas:
- author: Aspose
  dateModified: '2026-09-05'
  description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  headline: How to create rectangle shape and group shapes in Word with Aspose.Words
  type: TechArticle
- description: Create rectangle shape in a Word document using Aspose.Words, then
    learn how to insert ellipse word and group shapes in Word for richer layouts.
  name: How to create rectangle shape and group shapes in Word with Aspose.Words
  steps:
  - name: Pro tip
    text: Always add shapes **before** you group them. If you try to group a shape
      that is already part of another group, Aspose.Words throws an `ArgumentException`.
      Building the group in a single method prevents this runtime error.
  - name: Watch out for
    text: '* **Coordinate system** – `Left` and `Top` are measured from the page’s
      left and top margins, not from the document edge. Misunderstanding this can
      place shapes off‑page. * **Licensing** – Without a valid license, the saved
      document will contain a watermark that says “Aspose.Words for .NET Evaluatio'
  - name: What’s next?
    text: '* Explore **aspose.words create shapes** for more complex geometry such
      as `Polygon` or `Freeform`. * Combine grouped shapes with **content controls**
      to build dynamic templates. * Convert the DOCX to PDF or HTML to see how vector
      shapes are rendered across formats.'
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Come creare una forma rettangolare e raggruppare forme in Word con Aspose.Words
url: /it/net/programming-with-shapes/how-to-create-rectangle-shape-and-group-shapes-in-word-with/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare una forma rettangolare e raggruppare forme in Word con Aspose.Words

Se hai bisogno di **creare una forma rettangolare** in un documento Word, questa guida ti mostra i passaggi esatti con Aspose.Words per .NET. Vedrai anche come inserire una forma ellittica, raggruppare forme in Word e salvare il risultato come file DOCX. La soluzione funziona in qualsiasi progetto .NET 6+ e non richiede l'installazione di Microsoft Office sul server.

Il tutorial copre tutto, dalla configurazione del progetto alla gestione dei problemi comuni di layout, così puoi copiare il codice ed eseguirlo immediatamente.

## Prerequisiti

* .NET 6 SDK o versioni successive installato  
* Un IDE compatibile con NuGet (Visual Studio, Rider o VS Code)  
* Una licenza Aspose.Words per .NET (o una chiave di valutazione temporanea)  
* Conoscenze di base di C# e della struttura dei documenti Word  

Questi elementi consentono al codice di compilare e alle forme di essere renderizzate correttamente.

## Passo 1: Configurare il progetto e aggiungere Aspose.Words

Crea un nuovo progetto console e aggiungi il pacchetto Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Il pacchetto fornisce le classi `Document`, `DocumentBuilder`, `Shape` e `GroupShape` utilizzate in tutto questo tutorial.

## Passo 2: Inizializzare un documento vuoto e un builder

L'oggetto `Document` rappresenta l'intero file Word, mentre `DocumentBuilder` ti permette di inserire contenuti programmaticamente.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

Document doc = new Document();                 // creates an empty .docx container
DocumentBuilder builder = new DocumentBuilder(doc);
```

Creare prima il documento garantisce che tutte le operazioni successive sulle forme abbiano un contenitore valido.

## Passo 3: **Creare una forma rettangolare** e impostarne le dimensioni

Un rettangolo è il contenitore più comune per testo o immagini. Definisci la sua dimensione in punti (1 pt ≈ 1/72 pollice).

```csharp
// create a rectangle shape
Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
rectangleShape.Width = 100;      // 100 pt ≈ 1.39 in
rectangleShape.Height = 50;      // 50 pt ≈ 0.69 in

// optional: give the rectangle a light fill and a thin border
rectangleShape.FillColor = System.Drawing.Color.LightGray;
rectangleShape.Line.Width = 0.5;

// insert the rectangle into the document at the current cursor position
builder.InsertNode(rectangleShape);
```

Perché questo passaggio è importante: la classe `Shape` incapsula la geometria, le proprietà di riempimento e di linea. Impostare `Width` e `Height` prima dell'inserimento garantisce che la forma appaia con la dimensione prevista.

## Passo 4: **Come inserire una forma ellittica** – aggiungere una forma ellisse

Un'ellisse può essere usata per icone, marcatori o elementi decorativi. Il codice rispecchia la creazione del rettangolo, solo il `ShapeType` cambia.

```csharp
// create an ellipse shape
Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
ellipseShape.Width = 80;      // 80 pt ≈ 1.11 in
ellipseShape.Height = 80;     // a perfect circle because width = height

// style the ellipse
ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;

// place the ellipse after the rectangle
builder.InsertNode(ellipseShape);
```

Le proprietà `FillColor` e `Line.Color` illustrano come personalizzare l'aspetto senza immagini esterne.

## Passo 5: **Raggruppare forme in Word** – combinare rettangolo ed ellisse

Il raggruppamento ti consente di spostare, ridimensionare o ruotare più forme come un'unica unità. Questo è essenziale quando hai bisogno di un grafico composito (ad esempio, un'icona etichettata).

```csharp
// create a group shape container
GroupShape groupShape = new GroupShape(doc);

// add the previously created shapes to the group
groupShape.AppendChild(rectangleShape);
groupShape.AppendChild(ellipseShape);

// optional: set the group's position on the page
groupShape.Left = 150;   // distance from the left margin in points
groupShape.Top = 100;    // distance from the top margin in points

// insert the grouped shape into the document
builder.InsertNode(groupShape);
```

Quando chiami `AppendChild`, le forme originali vengono rimosse dal flusso principale del documento e diventano figli del `GroupShape`. Il gruppo si comporta come una singola forma, semplificando le successive regolazioni di layout.

## Passo 6: Salvare il documento

Infine, scrivi il documento su disco. Puoi scegliere qualsiasi formato supportato (`.docx`, `.pdf`, `.html`, ecc.). Per questo tutorial manteniamo il formato Word nativo.

```csharp
// replace "YOUR_DIRECTORY" with an absolute or relative path you control
string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Dopo aver eseguito il programma, apri *GroupShape.docx* in Microsoft Word. Vedrai un rettangolo e un'ellisse raggruppati insieme, posizionati alle coordinate specificate.

## Varianti comuni e casi limite

| Situazione | Cosa modificare | Motivo |
|-----------|----------------|--------|
| **Unità di misura diverse** | Usa `ConvertUtil.InchToPoint(2.5)` per pollici o `ConvertUtil.MillimeterToPoint(30)` per millimetri. | Mantiene il codice leggibile quando lavori con misure non in punti. |
| **Aggiungere testo all'interno del rettangolo** | Crea un nodo `Paragraph`, imposta la sua proprietà `Text` e aggiungilo a `rectangleShape` tramite `AppendChild`. | Ti permette di etichettare la forma senza caselle di testo separate. |
| **Ruotare il gruppo** | Imposta `groupShape.Rotation = 45;` (gradi). | Utile per creare distintivi o filigrane diagonali. |
| **Salvare come PDF** | Chiama `doc.Save("GroupShape.pdf");`. | Aspose.Words rasterizza automaticamente le forme vettoriali per l'output PDF. |
| **Gruppi multipli** | Crea ulteriori istanze `GroupShape` e ripeti i passaggi di append/insert. | Consente layout di pagina complessi con diversi compositi indipendenti. |

### Consiglio professionale

Aggiungi sempre le forme **prima** di raggrupparle. Se provi a raggruppare una forma che è già parte di un altro gruppo, Aspose.Words genera un `ArgumentException`. Costruire il gruppo in un unico metodo previene questo errore di runtime.

### Attenzione a

* **Sistema di coordinate** – `Left` e `Top` sono misurati dal margine sinistro e superiore della pagina, non dal bordo del documento. Un'errata interpretazione può posizionare le forme fuori dalla pagina.
* **Licenza** – Senza una licenza valida, il documento salvato conterrà una filigrana che dice “Aspose.Words for .NET Evaluation”. Applica la licenza all'inizio del codice (`License license = new License(); license.SetLicense("Aspose.Words.lic");`) per evitarla.

## Codice sorgente completo (eseguibile)

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize document and builder
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Create rectangle shape
        Shape rectangleShape = new Shape(doc, ShapeType.Rectangle);
        rectangleShape.Width = 100;
        rectangleShape.Height = 50;
        rectangleShape.FillColor = System.Drawing.Color.LightGray;
        rectangleShape.Line.Width = 0.5;
        builder.InsertNode(rectangleShape);

        // 3️⃣ Create ellipse shape
        Shape ellipseShape = new Shape(doc, ShapeType.Ellipse);
        ellipseShape.Width = 80;
        ellipseShape.Height = 80;
        ellipseShape.FillColor = System.Drawing.Color.CornflowerBlue;
        ellipseShape.Line.Color = System.Drawing.Color.DarkBlue;
        builder.InsertNode(ellipseShape);

        // 4️⃣ Group rectangle and ellipse
        GroupShape groupShape = new GroupShape(doc);
        groupShape.AppendChild(rectangleShape);
        groupShape.AppendChild(ellipseShape);
        groupShape.Left = 150;
        groupShape.Top = 100;
        builder.InsertNode(groupShape);

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "GroupShape.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Eseguendo questo programma si genera *GroupShape.docx* con le forme raggruppate esattamente come descritto.

## Conclusione

Ora sai come **creare una forma rettangolare**, **come inserire una forma ellittica** e **raggruppare forme in Word** usando Aspose.Words. L'esempio completo dimostra l'intero flusso di lavoro—dall'inizializzazione di un documento al salvataggio del file finale—così puoi integrare la gestione delle forme in qualsiasi soluzione di reportistica automatizzata o di generazione di documenti.

### Cosa fare dopo?

* Esplora **aspose.words create shapes** per geometrie più complesse come `Polygon` o `Freeform`.  
* Combina le forme raggruppate con **content controls** per creare modelli dinamici.  
* Converti il DOCX in PDF o HTML per vedere come le forme vettoriali vengono renderizzate nei vari formati.  

Sentiti libero di sperimentare con dimensioni, colori e rotazioni diversi. Quando padroneggerai il raggruppamento delle forme, potrai creare diagrammi sofisticati, distintivi e elementi UI personalizzati direttamente nei documenti Word.

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Creare una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserire forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Creare una forma rettangolare in Word usando C# – Guida passo‑per‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}