---
category: general
date: 2026-07-29
description: Crea un documento Word vuoto e impara come nascondere una forma, creare
  un oggetto nascosto e creare una forma ellittica utilizzando Aspose.Words in C#.
  Codice passo‑passo incluso.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- blank word document
- how to hide shape
- create hidden object
- create ellipse shape
language: it
lastmod: 2026-07-29
og_description: Crea un documento Word vuoto e nascondi la forma istantaneamente.
  Impara a creare un oggetto nascosto e a disegnare una forma ellittica usando Aspose.Words
  in C#.
og_image_alt: Hidden ellipse shape inserted into a blank Word document
og_title: Crea un documento Word vuoto con una forma ellisse nascosta – Tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-29'
  description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  headline: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  type: TechArticle
- description: Create a blank word document and learn how to hide shape, create hidden
    object, and create ellipse shape using Aspose.Words in C#. Step‑by‑step code included.
  name: Create a Blank Word Document with a Hidden Ellipse Shape – Full C# Guide
  steps:
  - name: What if the target Word version doesn’t support hidden shapes?
    text: The `Hidden` flag is part of the Office Open XML spec and is respected by
      Word 2007+ and LibreOffice. Older formats (e.g., `.doc`) ignore the flag, so
      always save as `.docx` when you need reliable hiding.
  - name: Can I hide other types of objects (pictures, tables)?
    text: Yes. Any node derived from `Shape`—including pictures, text boxes, and even
      SmartArt—exposes the `Hidden` property. Just set it to `true` before insertion.
  - name: Does hiding a shape affect document performance?
    text: Negligibly. The shape is stored as XML markup, and Word skips rendering
      hidden objects during layout. If you embed many hidden objects, the file size
      grows, but rendering stays fast.
  - name: How does this differ from using a bookmark or comment as a marker?
    text: Bookmarks are invisible by design, but they’re meant for navigation, not
      visual placeholders. Comments appear in the margin. A hidden shape gives you
      a visual object (size, position) that you can later reveal or manipulate, which
      is handy for templating scenarios.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word Automation
- Shapes
title: Crea un documento Word vuoto con una forma ellittica nascosta – Guida completa
  C#
url: /it/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto con una forma ellittica nascosta – Guida completa C#

Ti è mai capitato di dover creare un **documento Word vuoto** e poi nascondere una forma al suo interno? Forse stai generando un modello in cui alcuni marcatori devono rimanere invisibili fino a un passaggio successivo. In questo tutorial ti mostreremo esattamente **come nascondere una forma**, come **creare un oggetto nascosto**, e persino come **creare una forma ellittica** usando Aspose.Words per .NET. Alla fine avrai uno snippet C# pronto all'uso che produce un file DOCX contenente un'ellisse invisibile.

## Cosa imparerai

- Inizializzare un nuovo documento Word vuoto con Aspose.Words.  
- Costruire una forma ellittica, impostarne le dimensioni e posizionarla nella pagina.  
- Contrassegnare la forma come nascosta in modo che non compaia né sullo schermo né in stampa.  
- Salvare il risultato su disco e verificare che l'oggetto nascosto sia davvero invisibile.  

Non sono necessarie librerie esterne oltre a Aspose.Words, e il codice funziona con la versione 24.10 o successive (la proprietà `Hidden` è stata introdotta in quella release). Iniziamo.

![Diagramma di un'ellisse nascosta all'interno di un documento Word vuoto](https://example.com/hidden-ellipse.png "Forma ellittica nascosta inserita in un documento Word vuoto")

## Crea un documento Word vuoto e inserisci una forma ellittica nascosta

Il primo passo è creare un documento completamente nuovo. Pensa a `Document` come a una tela vuota; `DocumentBuilder` è il tuo pennello.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder to edit it.
Document document = new Document();               // This is your blank word document.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Perché iniziare con un documento vuoto?**  
> Una pagina pulita garantisce che nessun contenuto preesistente interferisca con la forma nascosta che stai per aggiungere. Inoltre rende l'esempio più facile da copiare‑incollare in qualsiasi progetto.

## Come nascondere una forma: impostare la proprietà Hidden

Aspose.Words 24.10 ha introdotto il flag `Hidden` su `Shape`. Quando impostato su `true`, Word tratta la forma come un commento—completamente invisibile nell'interfaccia e in stampa.

```csharp
// Step 2: Create an ellipse shape and set its size and position.
Shape ellipseShape = new Shape(document, ShapeType.Ellipse);
ellipseShape.Width = 100;   // Width in points
ellipseShape.Height = 80;   // Height in points
ellipseShape.Left = 150;    // Horizontal offset from the left margin
ellipseShape.Top = 150;     // Vertical offset from the top margin

// Step 3: Hide the shape so it does not appear when the document is viewed or printed.
ellipseShape.Hidden = true;   // This is the key to "how to hide shape"
```

> **Consiglio professionale:** Se in seguito devi rivelare la forma programmaticamente, basta impostare `ellipseShape.Hidden = false;` e risalvare il documento.

## Crea oggetto nascosto: inserire la forma nel documento

Ora che l'ellisse è pronta e nascosta, la inseriamo nella posizione corrente del cursore del builder. La posizione del builder di default è l'inizio del primo paragrafo, il che è perfetto per un documento vuoto.

```csharp
// Step 4: Insert the hidden shape into the document at the current builder position.
builder.InsertNode(ellipseShape);
```

> **E se ti serve la forma su una pagina specifica?**  
> Sposta prima il builder alla pagina desiderata (`builder.MoveToDocumentEnd();` o `builder.MoveToPage(pageNumber);`) prima di chiamare `InsertNode`.

## Salva il documento contenente la forma nascosta

Infine, scrivi il file su disco. L'output sarà un DOCX standard che qualsiasi elaboratore di testi può aprire—eccetto che l'ellisse rimarrà invisibile.

```csharp
// Step 5: Save the document containing the hidden shape.
document.Save("YOUR_DIRECTORY/HiddenShape.docx");
```

> **Output previsto:** Apri `HiddenShape.docx` in Microsoft Word. Non vedrai alcuna grafica, ma la dimensione del file sarà leggermente più grande rispetto a un documento realmente vuoto perché l'ellisse nascosta è memorizzata nell'XML.

## Verifica l'ellisse nascosta programmaticamente (opzionale)

Se vuoi ricontrollare che la forma sia effettivamente nascosta, puoi caricare il file salvato e ispezionare la proprietà `Hidden` della forma:

```csharp
Document loaded = new Document("YOUR_DIRECTORY/HiddenShape.docx");
Shape loadedShape = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
Console.WriteLine($"Is shape hidden? {loadedShape.Hidden}"); // Should print True
```

Eseguendo questo snippet stampa `True`, confermando che l'oggetto nascosto è sopravvissuto al ciclo di salvataggio‑caricamento.

## Casi limite e domande frequenti

### E se la versione di Word di destinazione non supporta le forme nascoste?

Il flag `Hidden` fa parte della specifica Office Open XML ed è rispettato da Word 2007+ e LibreOffice. Formati più vecchi (ad esempio `.doc`) ignorano il flag, quindi salva sempre come `.docx` quando hai bisogno di nascondere in modo affidabile.

### Posso nascondere altri tipi di oggetti (immagini, tabelle)?

Sì. Qualsiasi nodo derivato da `Shape`—incluse immagini, caselle di testo e persino SmartArt—esporta la proprietà `Hidden`. Basta impostarla su `true` prima dell'inserimento.

### Nascondere una forma influisce sulle prestazioni del documento?

In modo trascurabile. La forma è memorizzata come markup XML, e Word salta il rendering degli oggetti nascosti durante il layout. Se inserisci molte forme nascoste, la dimensione del file aumenta, ma il rendering rimane veloce.

### In che modo questo differisce dall'uso di un segnalibro o di un commento come marcatore?

I segnalibri sono invisibili per design, ma sono pensati per la navigazione, non per segnaposti visivi. I commenti appaiono a margine. Una forma nascosta ti fornisce un oggetto visivo (dimensione, posizione) che puoi rivelare o manipolare in seguito, utile per scenari di templating.

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per il copia‑incolla. Include tutte le direttive `using`, la creazione dell'ellisse nascosta e un passaggio di verifica.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class HiddenEllipseDemo
{
    static void Main()
    {
        // 1️⃣ Create a blank word document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Build the ellipse shape.
        Shape ellipse = new Shape(doc, ShapeType.Ellipse)
        {
            Width = 100,
            Height = 80,
            Left = 150,
            Top = 150,
            Hidden = true               // ← how to hide shape
        };

        // 3️⃣ Insert the hidden shape.
        builder.InsertNode(ellipse);

        // 4️⃣ Save the file.
        string outPath = "HiddenEllipse.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");

        // 5️⃣ Optional: Verify that the shape is hidden.
        Document loaded = new Document(outPath);
        Shape loadedEllipse = (Shape)loaded.GetChild(NodeType.Shape, 0, true);
        Console.WriteLine($"Is the ellipse hidden? {loadedEllipse.Hidden}");
    }
}
```

Eseguendo il programma viene creato `HiddenEllipse.docx` nella cartella di esecuzione. Aprilo—vedrai una pagina bianca perfettamente normale, ma l'ellisse nascosta vive silenziosamente al suo interno.

## Riepilogo

Abbiamo coperto come **creare un documento Word vuoto**, **nascondere una forma**, **creare un oggetto nascosto** e **creare una forma ellittica**, il tutto con poche righe di C#. Il punto chiave è la proprietà `Hidden` su `Shape`, che trasforma qualsiasi elemento visivo in un marcatore invisibile senza compromettere la compatibilità con Word.

## Prossimi passi

- **Stilizza la forma nascosta** (colore di riempimento, stile della linea) così quando la rivelerai in seguito avrà esattamente l'aspetto desiderato.  
- **Combina forme nascoste con segnalibri** per costruire modelli dinamici che possono essere attivati o disattivati.  
- **Esplora altri tipi di forma**—rettangoli, frecce o persino percorsi SVG personalizzati—sostituendo `ShapeType.Ellipse`.  

Sentiti libero di sperimentare: modifica le dimensioni, sposta la posizione o inserisci più ellissi nascoste. Lo stesso schema funziona per qualsiasi forma Aspose.Words che devi tenere fuori dalla vista.

Se incontri difficoltà o hai idee per estendere questo modello, lascia un commento qui sotto. Buon coding!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea un documento Word vuoto con forma rettangolare ombreggiata – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Crea una forma di gruppo in un documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea una forma rettangolare in Word con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}