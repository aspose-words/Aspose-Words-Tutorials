---
category: general
date: 2026-07-23
description: Crea un documento Word vuoto e aggiungi una forma rettangolare in C#.
  Scopri come inserire forme e raggruppare forme in Word usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- group shapes word
- how to insert shapes
- how to group shapes
language: it
lastmod: 2026-07-23
og_description: Crea un documento Word vuoto in C# e impara come inserire forme, aggiungere
  una forma rettangolare e raggruppare le forme in Word con Aspose.Words.
og_image_alt: Screenshot showing a blank Word document with two rectangle shapes grouped
  together
og_title: Crea un documento Word vuoto con rettangoli raggruppati – tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-23'
  description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  headline: Create blank word document with grouped rectangles – C# guide
  type: TechArticle
- description: Create blank word document and add rectangle shape in C#. Learn how
    to insert shapes and group shapes word using Aspose.Words.
  name: Create blank word document with grouped rectangles – C# guide
  steps:
  - name: What if I need more than two shapes?
    text: Just keep calling `builder.InsertShape(...)` and `group.AppendChild(...)`
      for each new shape. The group can hold any number of children.
  - name: Can I set fill colour or border on the rectangles?
    text: 'Absolutely. After creating a rectangle you can tweak its `FillColor`, `OutlineColor`,
      and `LineWidth`:'
  - name: How do I move the whole group after it’s been created?
    text: 'Use the group''s `Left` and `Top` properties, measured in points:'
  - name: What about scaling the group?
    text: Set `group.Width` and `group.Height` or use `group.ScaleX` / `group.ScaleY`.
      The child rectangles retain their proportions relative to the group.
  - name: Does this work with older .doc files?
    text: Aspose.Words abstracts the file format, so the same code works for `.doc`
      and `.docx`. The only limitation is that some newer shape features may be down‑sampled
      when saving to the older binary format.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crea un documento Word vuoto con rettangoli raggruppati – Guida C#
url: /it/java/images-shapes/create-blank-word-document-with-grouped-rectangles-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word vuoto con rettangoli raggruppati – Guida C#

Ti è mai capitato di dover **creare un documento Word vuoto** che contenga già un insieme di forme, ma non sapevi come raggrupparle in modo ordinato? Non sei l'unico. In molti scenari di reporting o generazione di template vuoi una tela pulita con un paio di rettangoli che fungano da segnaposto, e ti piacerebbe che si muovessero insieme come un’unica unità.

In questo tutorial vedremo passo passo come **creare un documento Word vuoto**, **aggiungere una forma rettangolare**, e poi **raggruppare le forme in Word** usando la libreria Aspose.Words. Alla fine avrai un file `.docx` pronto all’uso in cui i due rettangoli fanno parte di un gruppo, così qualsiasi spostamento o ridimensionamento successivo li influenzerà entrambi contemporaneamente.  

Risponderemo anche alle domande più comuni “**come inserire forme**” e “**come raggruppare forme**” che compaiono su forum e Stack Overflow. Nessuna documentazione esterna necessaria—tutto quello che ti serve è qui.

---

## Prerequisiti

- .NET 6 o successivo (il codice compila anche con .NET Core)  
- Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`)  
- Una conoscenza di base della sintassi C# (se hai scritto un “Hello World”, sei a posto)  

Se non hai ancora installato Aspose.Words, esegui:

```bash
dotnet add package Aspose.Words
```

Questo è tutto—nessun DLL aggiuntivo, nessun COM interop, solo un riferimento NuGet pulito.

---

## Passo 1: Crea documento Word vuoto e inizializza il builder

La prima cosa che facciamo è istanziare un oggetto `Document` vuoto. Pensalo come un foglio di carta fresco. Poi colleghiamo un `DocumentBuilder`, lo strumento pratico che Aspose fornisce per inserire contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document doc = new Document();               // <-- create blank word document
        DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Perché è importante:** Senza un `DocumentBuilder` dovresti manipolare manualmente l’albero dei nodi a basso livello, il che è soggetto a errori. Il builder astrae le complessità XML di un file `.docx`.

---

## Passo 2: Come inserire forme – aggiungi prima un contenitore di gruppo

Aspose ti permette di inserire una *group shape* che può contenere altre forme in seguito. Questa è la base per **group shapes word**.  

```csharp
        // Step 2: Insert a group shape that will act as a container
        Shape group = builder.InsertGroupShape();
```

> **Consiglio:** Il gruppo è invisibile finché non aggiungi forme figlie, quindi non vedrai alcun artefatto nel documento risultante fino al passo successivo.

---

## Passo 3: Aggiungi forma rettangolare – gli oggetti visibili

Ora **aggiungeremo la forma rettangolare** due volte, ciascuna con le proprie dimensioni. Il metodo `InsertShape` accetta un `ShapeType` e le dimensioni in punti (1 pt ≈ 1/72 inch).

```csharp
        // Step 3: Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50); // 100 pt × 50 pt
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);  // 80 pt × 40 pt
```

> **Perché i rettangoli?** Sono la forma geometrica più semplice, perfetta per segnaposto, mockup di interfacce tipo pulsanti o semplici elementi grafici.

---

## Passo 4: Come raggruppare forme – collega i rettangoli al gruppo

Con i rettangoli creati, ora **raggruppiamo le forme** aggiungendoli come figli della group shape inserita in precedenza.

```csharp
        // Step 4: Append the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);
```

> **Cosa succede dietro le quinte?** La group shape diventa il nodo padre nell’albero XML del documento. Spostare il gruppo sposta entrambi i rettangoli insieme, mantenendo le loro posizioni relative.

---

## Passo 5: Salva il documento – ora hai un file Word con forme raggruppate

Infine, persisti il documento su disco. Modifica il percorso con una cartella esistente sul tuo computer.

```csharp
        // Step 5: Save the document with the grouped shapes
        doc.Save("GroupShape.docx");   // Creates a blank word document with grouped rectangles
    }
}
```

Questo è l’intero programma. Eseguilo, apri `GroupShape.docx` e vedrai due rettangoli affiancati. Se ne selezioni uno, l’intero gruppo viene evidenziato—esattamente quello che **group shapes word** dovrebbe fare.

---

## Codice completo in un unico posto

Per comodità, ecco l’esempio completo, pronto da copiare e incollare:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert a group shape that will contain other shapes
        Shape group = builder.InsertGroupShape();

        // Insert two rectangle shapes with desired dimensions
        Shape rect1 = builder.InsertShape(ShapeType.Rectangle, 100, 50);
        Shape rect2 = builder.InsertShape(ShapeType.Rectangle, 80, 40);

        // Add the rectangles to the group shape
        group.AppendChild(rect1);
        group.AppendChild(rect2);

        // Save the document
        doc.Save("GroupShape.docx");
    }
}
```

**Output previsto:** Aprendo `GroupShape.docx` si visualizza una pagina vuota con due rettangoli raggruppati. Selezionando un rettangolo, l’altro viene selezionato automaticamente, confermando che il raggruppamento è riuscito.

---

## Domande frequenti e gestione dei casi limite

### E se avessi bisogno di più di due forme?

Basta continuare a chiamare `builder.InsertShape(...)` e `group.AppendChild(...)` per ogni nuova forma. Il gruppo può contenere un numero illimitato di figli.

### Posso impostare colore di riempimento o bordo sui rettangoli?

Assolutamente. Dopo aver creato un rettangolo puoi modificare le sue proprietà `FillColor`, `OutlineColor` e `LineWidth`:

```csharp
rect1.FillColor = System.Drawing.Color.LightBlue;
rect1.OutlineColor = System.Drawing.Color.DarkBlue;
rect1.LineWidth = 1.5;
```

### Come sposto l’intero gruppo dopo averlo creato?

Usa le proprietà `Left` e `Top` del gruppo, misurate in punti:

```csharp
group.Left = 150;   // move 150 pt from the left margin
group.Top  = 200;   // move 200 pt from the top of the page
```

### E per scalare il gruppo?

Imposta `group.Width` e `group.Height` oppure usa `group.ScaleX` / `group.ScaleY`. I rettangoli figli mantengono le loro proporzioni rispetto al gruppo.

### Funziona con file .doc più vecchi?

Aspose.Words astrae il formato del file, quindi lo stesso codice funziona per `.doc` e `.docx`. L’unica limitazione è che alcune funzionalità di forma più recenti potrebbero essere ridotte quando si salva nel formato binario più vecchio.

---

## Consigli professionali per codice pronto alla produzione

- **Rilascia le risorse** – Avvolgi `Document` in un blocco `using` se lavori con file di grandi dimensioni per liberare la memoria tempestivamente.  
- **Gestione degli errori** – Cattura `Aspose.Words.Fonts.FontSettingsException` se prevedi di incorporare font personalizzati.  
- **Performance** – Quando inserisci molte forme, disabilita temporaneamente gli aggiornamenti del layout con `doc.LayoutOptions = new LayoutOptions { UpdateFields = false };` e riattivalo successivamente.

---

## Conclusione

Ora sai **come creare un documento Word vuoto**, **aggiungere una forma rettangolare**, e **raggruppare le forme in Word** usando Aspose.Words in C#. L’esempio copre i passaggi essenziali “**come inserire forme**” e “**come raggruppare forme**”, spiega il motivo di ogni riga e tocca anche personalizzazioni, casi limite e best practice.

Successivamente potresti esplorare **come inserire immagini**, **aggiungere testo all’interno di forme raggruppate**, o **esportare il documento in PDF**—tutte operazioni che seguono lo stesso schema di utilizzo di `DocumentBuilder` e manipolazione delle forme. Continua a sperimentare; l’API Aspose è sufficientemente ricca da gestire quasi qualsiasi scenario di automazione Word che tu possa immaginare.

Buona programmazione, e sentiti libero di lasciare un commento se incontri difficoltà!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi nei tuoi progetti.

- [Insert Shapes in Word Documents Using Aspose.Words for .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}