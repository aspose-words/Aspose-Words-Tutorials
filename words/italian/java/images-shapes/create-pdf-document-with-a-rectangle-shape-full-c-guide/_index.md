---
category: general
date: 2026-03-25
description: Crea un documento PDF in C# e scopri come aggiungere una forma rettangolare,
  impostare il colore di riempimento, regolare le dimensioni della forma e impostare
  la trasparenza della forma in pochi passaggi.
draft: false
keywords:
- create pdf document
- set shape transparency
- add rectangle shape
- set fill color
- set shape size
language: it
og_description: Crea un documento PDF in C# e scopri come aggiungere un rettangolo,
  impostare il colore di riempimento, le dimensioni e la trasparenza per un output
  PDF rifinito.
og_title: Crea documento PDF con una forma rettangolare – Tutorial C#
tags:
- C#
- PDF
- Aspose.Words
title: Crea documento PDF con una forma rettangolare – Guida completa C#
url: /it/java/images-shapes/create-pdf-document-with-a-rectangle-shape-full-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento PDF con una forma rettangolare – Guida completa C#

Hai mai avuto bisogno di **creare un documento PDF** che contenga una forma con stile personalizzato, ma non sapevi da dove cominciare? Non sei solo. Che tu stia costruendo un generatore di report o un volantino di marketing, la possibilità di disegnare programmaticamente un rettangolo, impostare il suo colore di riempimento, regolare le sue dimensioni e persino modificare la sua trasparenza può rendere i tuoi PDF molto più professionali.

> **Suggerimento:** Lo stesso approccio funziona con altri tipi di forma (ellisse, linea, ecc.) — basta sostituire `ShapeType.RECTANGLE` con quello di cui hai bisogno.

---

## Cosa ti serve

| Prerequisito | Perché è importante |
|--------------|---------------------|
| **.NET 6+** (or .NET Framework 4.6+) | La libreria Aspose.Words è destinata a runtime moderni. |
| **Aspose.Words for .NET** Pacchetto NuGet | Fornisce `Document`, `Shape`, `ShadowEffect` e classi correlate. |
| **Un IDE C#** (Visual Studio, Rider, VS Code) | Rende il debug e l'esecuzione del campione indolori. |
| **Conoscenza di base di C#** | Capirai la sintassi senza dover approfondire. |

Puoi installare la libreria tramite la riga di comando:

```bash
dotnet add package Aspose.Words
```

È tutto—nessun DLL aggiuntivo, nessuna dipendenza nativa. Una volta che il pacchetto è al suo posto, il codice qui sotto verrà compilato ed eseguito.

---

## Implementazione passo‑passo

Di seguito suddividiamo il processo in cinque passaggi logici. Ogni passaggio ha un'intestazione chiara (così i modelli AI possono indicizzarlo) e un breve blocco di codice che puoi copiare‑incollare direttamente.

### ## 1. Crea documento PDF e prepara la tela

La prima cosa che facciamo è istanziare un `Document`. Pensalo come una tela vuota che diventerà il tuo file PDF.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new empty document – this is the PDF document we will build.
        Document document = new Document();

        // The rest of the steps follow inside this method.
```

> **Perché?** `Document` contiene tutte le sezioni, i paragrafi e le forme. Iniziare con un oggetto pulito garantisce l'assenza di artefatti nascosti da esecuzioni precedenti.

### ## 2. Aggiungi forma rettangolare – Imposta colore di riempimento e dimensioni della forma

Ora creiamo un rettangolo, gli diamo un riempimento giallo brillante e definiamo le sue dimensioni. Questo copre sia **add rectangle shape** che **set fill color** così come **set shape size**.

```csharp
        // Step 2: Create a rectangle shape.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);

        // Set the width and height – this is where we set the shape size.
        rectangle.Width = 200;   // 200 points (≈2.78 inches)
        rectangle.Height = 100;  // 100 points (≈1.39 inches)

        // Apply a fill color – here we use a vivid yellow.
        rectangle.FillColor = Color.Yellow;
```

> **Nota:** Larghezza/altezza sono misurate in punti (1 punto = 1/72 di pollice). Regola questi numeri per adattarli al tuo layout.

### ## 3. Applica un'ombra esterna e imposta la trasparenza della forma

Le ombre aggiungono profondità, e controllare la loro opacità è l'essenza di **set shape transparency**. Di seguito configuriamo un'ombra esterna grigia con trasparenza del 30 %.

```csharp
        // Step 3: Configure the outer shadow effect.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;          // Shadow hue
        shadow.BlurRadius = 5.0;            // How fuzzy the shadow appears
        shadow.DistanceX = 4;               // Horizontal offset
        shadow.DistanceY = 4;               // Vertical offset
        shadow.Transparency = 0.3;          // 0 = opaque, 1 = fully transparent
        shadow.Style = ShadowStyle.Outer;   // Make it an outer shadow
```

> **Perché impostare la trasparenza?** Un'ombra trasparente al 30 % appare sottile, evitando che il rettangolo sembri “piatto” sulla pagina.

### ## 4. Inserisci la forma nel corpo del documento

Ora inseriamo il rettangolo nel primo paragrafo della prima sezione del documento. Questo passaggio lega tutto insieme.

```csharp
        // Step 4: Insert the rectangle into the first paragraph.
        // If the document has no paragraphs yet, Aspose creates one automatically.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);
```

> **Caso limite:** Se hai bisogno della forma su una nuova pagina, anteponi `document.Sections[0].PageSetup.SectionStart = SectionStart.NewPage;` prima di aggiungere la forma.

### ## 5. Salva il documento come file PDF

Infine, salviamo la struttura in memoria in un file PDF fisico. Il file verrà scritto nella cartella che specifichi.

```csharp
        // Step 5: Save the document as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF saved successfully to {outputPath}");
    }
}
```

Quando esegui il programma, appare un file chiamato `shadow.pdf`. Aprendolo vedrai un rettangolo giallo con un'ombra grigia morbida spostata di 4 punti—esattamente ciò che il nostro codice descrive.

> **Output previsto:** Un PDF a pagina singola dove il rettangolo si trova vicino all'angolo in alto a sinistra della pagina, riempito di giallo, dimensioni 200 × 100 punti, e con un'ombra esterna semi‑trasparente.

## Esempio completo funzionante (pronto per copia‑incolla)

Di seguito trovi l'intero file sorgente, pronto per essere inserito in un nuovo progetto console.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new empty document – this will become the PDF.
        Document document = new Document();

        // 2️⃣ Add a rectangle shape, set its size and fill color.
        Shape rectangle = new Shape(document, ShapeType.RECTANGLE);
        rectangle.Width = 200;          // shape size – width
        rectangle.Height = 100;         // shape size – height
        rectangle.FillColor = Color.Yellow; // set fill color

        // 3️⃣ Apply an outer shadow and adjust transparency.
        ShadowEffect shadow = rectangle.ShadowEffect;
        shadow.Color = Color.Gray;
        shadow.BlurRadius = 5.0;
        shadow.DistanceX = 4;
        shadow.DistanceY = 4;
        shadow.Transparency = 0.3;      // set shape transparency
        shadow.Style = ShadowStyle.Outer;

        // 4️⃣ Insert the shape into the first paragraph of the document.
        Paragraph firstParagraph = document.FirstSection.Body.FirstParagraph;
        firstParagraph.AppendChild(rectangle);

        // 5️⃣ Save everything as a PDF.
        string outputPath = @"YOUR_DIRECTORY\shadow.pdf";
        document.Save(outputPath, SaveFormat.Pdf);

        Console.WriteLine($"PDF created at: {outputPath}");
    }
}
```

> **Suggerimento:** Sostituisci `YOUR_DIRECTORY` con un percorso assoluto come `C:\Temp` o un percorso relativo come `.\output`. Il programma creerà la cartella se non esiste già.

## Domande frequenti (FAQ)

**Q: Posso cambiare la posizione del rettangolo sulla pagina?**  
A: Assolutamente. Imposta `rectangle.Left` e `rectangle.Top` (entrambi misurati in punti) prima di aggiungerlo al paragrafo.

**Q: E se ho bisogno di un riempimento trasparente invece di un'ombra trasparente?**  
A: Usa `rectangle.FillColor = Color.FromArgb(128, Color.Yellow);` – il primo argomento è il canale alfa (0‑255), dove 128 produce circa il 50 % di trasparenza.

**Q: Funziona con .NET Core?**  
A: Sì. Aspose.Words supporta .NET Standard 2.0+, quindi puoi eseguire lo stesso codice su .NET 6, .NET 7 o .NET Framework 4.6+.

**Q: Come posso aggiungere più forme?**  
A: Basta ripetere i passaggi 2‑4 per ogni forma, inserendole eventualmente in paragrafi o sezioni diversi.

## Conclusione

Abbiamo appena **creato un documento PDF** da zero, **aggiunto una forma rettangolare**, **impostato il suo colore di riempimento**, **definito le sue dimensioni**, e **regolato la trasparenza della forma** per ottenere un effetto ombra raffinato. Il codice di esempio è autonomo, si esegue in meno di un minuto, e dimostra i concetti fondamentali di cui avrai bisogno per layout PDF più elaborati.

Pronto per la prossima sfida? Prova a sostituire il rettangolo con una forma con angoli arrotondati, inserisci un'immagine all'interno della forma, o genera automaticamente un indice. La stessa API ti consente di sovrapporre testo, immagini e vettori—il cielo è il limite.

Se hai trovato utile questa guida, metti una stella su GitHub, condividila con un collega, o lascia un commento con le tue variazioni. Buon coding! 

---

![esempio di creazione documento pdf con forma rettangolare](/images/rectangle-shadow.png "Screenshot che mostra il PDF creato con un rettangolo giallo e un'ombra esterna grigia")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}