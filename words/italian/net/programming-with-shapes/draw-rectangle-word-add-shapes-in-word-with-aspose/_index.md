---
category: general
date: 2026-07-29
description: Disegna un rettangolo in Word usando Aspose.Words. Scopri come aggiungere
  una forma rettangolare, aggiungere una forma linea e gestire più forme in un unico
  documento.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- draw rectangle word
- add rectangle shape
- add line shape
- how to add shapes
- multiple shapes word
language: it
lastmod: 2026-07-29
og_description: Disegna un rettangolo in Word con Aspose.Words. Segui questa guida
  passo passo per aggiungere una forma rettangolo, una forma linea e lavorare senza
  sforzo con più forme in Word.
og_image_alt: Screenshot showing a Word document with a grouped rectangle and line
  shape – draw rectangle word example
og_title: Disegna un rettangolo in Word – Padroneggia l'aggiunta di forme in Word
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: draw rectangle word using Aspose.Words. Learn how to add rectangle
    shape, add line shape, and manage multiple shapes word in a single document.
  headline: draw rectangle word – Add Shapes in Word with Aspose
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word Automation
title: Disegna un rettangolo in Word – Aggiungi forme in Word con Aspose
url: /it/net/programming-with-shapes/draw-rectangle-word-add-shapes-in-word-with-aspose/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# draw rectangle word – Guida completa per aggiungere forme in Word

Ti sei mai chiesto come **draw rectangle word** documenti senza aprire l'interfaccia ogni volta? Non sei solo. Molti sviluppatori hanno bisogno di generare file Word al volo, e il modo più semplice è lasciare che una libreria faccia il lavoro pesante. In questo tutorial ti mostreremo esattamente **come aggiungere forme**—specificamente un rettangolo e una linea—usando Aspose.Words per .NET, e manterremo l'attenzione sulla frase *draw rectangle word* così non ti perderai.

Pensalo come un mini‑studio d'arte che vive dentro il tuo codice. Alla fine sarai in grado di **add rectangle shape**, **add line shape**, e persino combinarli in gruppi **multiple shapes word**. Nessuna interfaccia, nessuna manipolazione manuale, solo C# pulito e ripetibile.

## Cosa imparerai

- Configurare un nuovo documento Word con Aspose.Words.  
- Creare un **GroupShape** che può contenere diversi oggetti.  
- **Add rectangle shape** e **add line shape** all'interno di quel gruppo.  
- Inserire le forme raggruppate nel corpo del documento.  
- Salvare il file e vedere immediatamente il risultato.  

Se sei a tuo agio con il C# di base e possiedi una copia di Aspose.Words, sei pronto. Non sono necessari pacchetti NuGet aggiuntivi oltre alla libreria principale.

> **Suggerimento professionale:** Aspose.Words funziona con .NET 6, .NET 7 e .NET Framework 4.6+. Scegli il runtime che corrisponde al tuo progetto.

![esempio draw rectangle word](https://example.com/placeholder-image.png "draw rectangle word – forme raggruppate in un file Word")

## draw rectangle word – Configurazione del documento

Prima di poter **draw rectangle word** abbiamo bisogno di una tela pulita. La classe `Document` è quella tela; il `DocumentBuilder` è il nostro pennello.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create an empty Word document.
Document doc = new Document();

// DocumentBuilder lets us insert nodes, paragraphs, tables, etc.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Le due righe sopra ci forniscono un nuovo `.docx` in memoria. Nulla viene scritto su disco ancora, il che significa che possiamo sperimentare senza ingombrare il file system.

## Come aggiungere forme – Creazione di un contenitore GroupShape

Quando vuoi che **multiple shapes word** si comportino come un'unica unità—muoversi insieme, ruotare insieme—le avvolgi in un `GroupShape`. Pensa a un gruppo come a una cartella che contiene altre forme.

```csharp
// Define a GroupShape that will act as a container for other shapes.
// Width = 300 pts, Height = 200 pts (roughly 4.2" x 2.8").
GroupShape group = new GroupShape(doc, 300, 200)
{
    Left = 100,   // Position from the left margin.
    Top  = 100    // Position from the top margin.
};
```

Perché un gruppo? Perché più tardi potresti voler **add rectangle shape** e **add line shape** e poi spostarli insieme. Senza un gruppo, dovresti riposizionare ogni forma singolarmente.

## add rectangle shape – Inserimento di un rettangolo nel gruppo

Ora che il contenitore esiste, **add rectangle shape**. Un rettangolo è una `Shape` il cui `ShapeType` è `Rectangle`.

```csharp
// Create a rectangle shape.
Shape rectangle = new Shape(doc, ShapeType.Rectangle)
{
    Width  = 120,   // 120 points ≈ 1.67 inches.
    Height = 80,    // 80 points ≈ 1.11 inches.
    Left   = 10,    // Offset inside the group.
    Top    = 10
};

// Append the rectangle to the group.
group.AppendChild(rectangle);
```

Nota che i valori `Left` e `Top` sono relativi all'origine del gruppo, non alla pagina. Questo rende facile allineare le forme con precisione. Il rettangolo apparirà vicino all'angolo in alto a sinistra del gruppo.

## add line shape – Aggiunta di una linea allo stesso gruppo

Una linea è semplicemente un'altra `Shape`, ma il suo `ShapeType` è `Line`. La posizioneremo sotto il rettangolo.

```csharp
// Create a line shape.
Shape line = new Shape(doc, ShapeType.Line)
{
    Width  = 150,   // Length of the line.
    Height = 0,     // Height is zero for a straight line.
    Left   = 10,
    Top    = 110    // Position it a bit lower than the rectangle.
};

// Append the line to the group.
group.AppendChild(line);
```

Poiché l'altezza della linea è zero, la proprietà `Top` determina dove la linea si trova verticalmente. La `Width` controlla quanto è lunga la linea orizzontalmente.

## multiple shapes word – Inserimento del gruppo nel corpo del documento

Abbiamo un gruppo che ora contiene **add rectangle shape** e **add line shape**. L'ultimo passo è inserire il tutto nel documento.

```csharp
// Insert the completed group into the document body at the current cursor position.
builder.InsertNode(group);
```

`InsertNode` posiziona il gruppo esattamente dove il `DocumentBuilder` è attualmente posizionato. Se ne hai bisogno in un paragrafo specifico, sposta il builder con `builder.MoveToParagraph(index)` prima.

## Salvataggio del risultato – Visualizzare l'output draw rectangle word

```csharp
// Save the document to disk. Change the path to a location that exists on your machine.
doc.Save("C:/Temp/GroupShape.docx");
```

Apri il file generato in Microsoft Word e vedrai un unico gruppo contenente un rettangolo e una linea. Puoi fare clic sul gruppo, trascinarlo o anche ridimensionarlo—tutte le forme si muovono insieme. Questa è la potenza di **multiple shapes word**.

### Output previsto

- Un file `.docx` chiamato `GroupShape.docx`.  
- Una pagina con un rettangolo raggruppato (120 × 80 pt) vicino all'angolo in alto a sinistra.  
- Una linea orizzontale (150 pt di lunghezza) posizionata appena sotto il rettangolo.  
- Entrambe le forme sono selezionabili come un unico oggetto.

Se fai doppio clic sul gruppo, Word ti permetterà di modificare ogni forma individualmente—perfetto per la messa a punto.

## Domande comuni e casi particolari

**Cosa succede se ho bisogno di più di due forme?**  
Basta continuare a chiamare `group.AppendChild(yourShape)` per ogni oggetto aggiuntivo. Il gruppo può contenere qualsiasi numero di forme, rendendolo ideale per diagrammi complessi.

**Posso cambiare il colore di riempimento del rettangolo?**  
Assolutamente. Dopo aver creato il rettangolo, imposta `rectangle.FillColor = System.Drawing.Color.LightBlue;`. Questo funziona per qualsiasi forma che supporta il riempimento.

**Devo impostare `Height = 0` per una linea?**  
Sì, per una linea orizzontale retta l'altezza dovrebbe essere zero. Per una linea verticale, imposta `Width = 0` e assegna a `Height` un valore positivo.

**Funzionerà con file .doc (Word 97‑2003)?**  
Aspose.Words può salvare nel formato più vecchio `.doc`, ma alcune funzionalità moderne delle forme potrebbero essere limitate. Usa `.docx` per la massima fedeltà.

**Come ruoto l'intero gruppo?**  
Puoi impostare `group.Rotation = 45;` (gradi) prima di inserirlo. La rotazione si applica a ogni forma figlia.

## Riepilogo – Come aggiungere forme in Word programmaticamente

- **draw rectangle word** inizia creando un `Document` e un `DocumentBuilder`.  
- Costruisci un **GroupShape** per contenere **multiple shapes word**.  
- **add rectangle shape** e **add line shape** vengono aggiunti al gruppo.  
- Inserisci il gruppo nel corpo con `builder.InsertNode`.  
- Salva il file e aprilo per verificare il risultato visivo.

Questo è l'intero flusso di lavoro, racchiuso in un unico elenco di codice facile da leggere.

## Prossimi passi e argomenti correlati

Ora che sai **come aggiungere forme**, considera di esplorare:

- **add rectangle shape** con angoli arrotondati (`ShapeType.Rectangle` + `CornerRadius`).  
- Stilizzare le linee con diversi pattern di tratteggio (`line.LineFormat.DashStyle`).  
- Incorporare immagini accanto alle forme per report più ricchi.  
- Usare **multiple shapes word** per costruire diagrammi di flusso o semplici diagrammi UML.  

Ognuno di questi argomenti si basa naturalmente sulle fondamenta che abbiamo delineato qui, e tutti seguono lo stesso schema di creazione delle forme, configurazione e raggruppamento se necessario.

---

Buon coding! Se incontri stranezze o hai un caso d'uso interessante da condividere, lascia un commento qui sotto. Il tuo feedback ci aiuta tutti a padroneggiare l'arte di **draw rectangle word** e oltre.

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea forma rettangolare in Word usando C# – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Crea forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Inserisci forme nei documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}