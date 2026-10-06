---
category: general
date: 2026-03-06
description: Crea una forma rettangolare in Word e aggiungi l'ombra alla forma con
  Aspose.Words. Scopri come inserire un rettangolo in Word e come aggiungere l'ombra
  a una forma in C#.
draft: false
keywords:
- create rectangle shape
- add shape shadow
- how to insert rectangle in word
- how to add shadow to shape
language: it
og_description: Crea una forma rettangolare in Word e aggiungi l'ombra alla forma
  con Aspose.Words. Guida passo‑passo su come inserire un rettangolo in Word e su
  come aggiungere l'ombra alla forma.
og_title: Crea una forma rettangolare con ombra in Word usando Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Crea forma rettangolare con ombra in Word usando Aspose.Words
url: /it/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-word-using-aspose-word/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare con ombra in Word usando Aspose.Words

Ti è mai capitato di dover **creare una forma rettangolare** in un documento Word ma non sapevi come darle un aspetto curato? Non sei solo: la maggior parte degli sviluppatori incontra lo stesso ostacolo quando tenta per la prima volta di aggiungere un tocco visivo ai documenti generati automaticamente. La buona notizia? Con Aspose.Words per .NET puoi sia **creare una forma rettangolare** sia **aggiungere un’ombra alla forma** in poche righe di C#.

In questo tutorial ti mostreremo passo passo **come inserire un rettangolo in Word**, poi vedremo **come aggiungere un’ombra alla forma** in modo che risalti dalla pagina. Alla fine avrai un file `Shadow.docx` pronto da salvare, che potrai aprire in Word e vedere un rettangolo tinta di grigio con una morbida ombra. Nessun file immagine aggiuntivo, nessuna modifica manuale—solo codice.

## Cosa imparerai

- Le istruzioni C# esatte necessarie per **creare una forma rettangolare** con Aspose.Words.  
- Come abilitare e configurare un’ombra usando l’oggetto `Shadow`.  
- Perché ogni proprietà è importante (ad es., `Transparency`, `Blur`, `Angle`).  
- Problemi comuni (unità, compatibilità di versione) e soluzioni rapide.  
- Un programma completo, pronto per il copia‑incolla, che puoi eseguire subito.

### Prerequisiti

- .NET 6+ (o .NET Framework 4.7+).  
- Aspose.Words per .NET 23.10 o successivo (il pacchetto NuGet è `Aspose.Words`).  
- Una conoscenza di base di C# e Visual Studio (o di qualsiasi IDE preferisci).  

Se li hai già, tuffiamoci subito.

---

## Passo 1: Configura il progetto e importa i namespace

Per prima cosa, crea una nuova app console (o riutilizza una esistente) e aggiungi il pacchetto NuGet Aspose.Words:

```bash
dotnet new console -n WordShapeDemo
cd WordShapeDemo
dotnet add package Aspose.Words
```

Ora importa i namespace richiesti nel tuo `Program.cs`:

```csharp
using System.Drawing;               // For Color
using Aspose.Words;                  // Core document classes
using Aspose.Words.Drawing;          // Shape and Shadow types
```

> **Pro tip:** Se stai puntando a .NET 6+, puoi abilitare le direttive `using` globali per evitare di ripetere queste righe in ogni file.

---

## Passo 2: **Crea una forma rettangolare** in un documento Word vuoto

Inizieremo con un nuovo oggetto `Document` e un `DocumentBuilder` per manipolarlo. Il metodo `InsertShape` del builder è dove avviene la magia.

```csharp
// Step 2: Initialize a new document and builder
Document document = new Document();                     // Blank Word file
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle – 200 × 100 points (≈2.78 × 1.39 inches)
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

Perché 200 × 100 punti? In Word, un punto corrisponde a 1/72 di pollice, quindi il rettangolo risulta circa 2,8 × 1,4 pollici—sufficiente per essere notato ma non eccessivo. Puoi modificare questi valori per adattarli al tuo layout; ricorda solo che sono misurati in **punti**, non in pixel.

---

## Passo 3: **Aggiungi un’ombra alla forma** – configurare l’aspetto

Ora che abbiamo un rettangolo, diamo una leggera ombra grigia. L’oggetto `Shadow` è associato al `Shape` e espone diverse proprietà utili.

```csharp
// Step 3: Turn on the shadow and tweak its appearance
rectangle.Shadow.Enabled = true;               // Switch the shadow on
rectangle.Shadow.Color = Color.Gray;           // Shadow hue
rectangle.Shadow.Transparency = 0.3;           // 30 % transparent – looks softer
rectangle.Shadow.Blur = 5;                     // Blur radius (points)
rectangle.Shadow.Distance = 4;                 // How far the shadow sits from the shape
rectangle.Shadow.Angle = 45;                   // Direction in degrees (45° = down‑right)
rectangle.Shadow.Size = 100;                   // 100 % of the original shape size
```

### Cosa fa ogni proprietà

| Property | Effect | Typical values |
|----------|--------|----------------|
| **Enabled** | Attiva o disattiva l'ombra | `true` or `false` |
| **Color** | Colore di base dell'ombra | Any `System.Drawing.Color` |
| **Transparency** | Opacità (0 = solido, 1 = invisibile) | 0.0 – 1.0 |
| **Blur** | Morbidezza del bordo | 0 – 10 (higher = softer) |
| **Distance** | Distanza tra forma e ombra | 0 – 20 points |
| **Angle** | Direzione da cui sembra provenire la luce | 0 – 360 degrees |
| **Size** | Scala dell'ombra rispetto alla forma | 0 – 200 % |

> **Perché preoccuparsi di queste impostazioni?**  
> Regolare finemente l'ombra ti permette di rispettare le linee guida del brand aziendale (ad esempio, una trasparenza sottile del 20 % per un aspetto professionale) senza ricorrere a editor di immagini esterni.

---

## Passo 4: Salva il documento e verifica il risultato

Infine, scrivi il file su disco. Puoi scegliere qualsiasi cartella; basta sostituire `YOUR_DIRECTORY` con un percorso reale.

```csharp
// Step 4: Persist the document
string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
document.Save(outputPath);
Console.WriteLine($"Document saved to: {outputPath}");
```

Apri `Shadow.docx` in Microsoft Word e dovresti vedere un rettangolo grigio con una leggera ombra offset di 45° . Questo indizio visivo fa sembrare la forma “sollevata” dalla pagina—esattamente ciò che ti aspetti da un report o una fattura ben curati.

---

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in `Program.cs`. Nessuna parte è mancante; compila ed esegue così com'è.

```csharp
using System;
using System.Drawing;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document and a builder
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);

        // 2️⃣ Insert a rectangle shape (200 × 100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // 3️⃣ Enable the shape's shadow and configure its appearance
        rectangle.Shadow.Enabled = true;               // Turn the shadow on
        rectangle.Shadow.Color = Color.Gray;           // Shadow colour
        rectangle.Shadow.Transparency = 0.3;           // 30 % transparent
        rectangle.Shadow.Blur = 5;                     // Blur radius
        rectangle.Shadow.Distance = 4;                 // Offset from the shape
        rectangle.Shadow.Angle = 45;                   // Direction in degrees
        rectangle.Shadow.Size = 100;                   // Shadow size as a percentage

        // 4️⃣ Save the document with the shadowed shape
        string outputPath = Path.Combine(Environment.CurrentDirectory, "Shadow.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to: {outputPath}");
    }
}
```

### Output previsto

- **File:** `Shadow.docx` posizionato nella cartella di esecuzione del progetto.  
- **Visuale:** Un unico rettangolo centrato nella pagina, riempito di bianco predefinito, e un'ombra grigia spostata di 4 punti verso il basso‑destra, leggermente sfocata per un aspetto naturale.

---

## Domande comuni e casi limite

### 1. E se avessi bisogno di un'unità diversa (ad esempio, centimetri)?

Aspose.Words lavora in punti, ma puoi convertire i centimetri in punti con la semplice formula:  
`points = centimeters * 28.3465`.  

```csharp
double cmWidth = 5.0; // 5 cm
double cmHeight = 2.5; // 2.5 cm
Shape rectCm = builder.InsertShape(ShapeType.Rectangle,
                                   (float)(cmWidth * 28.3465),
                                   (float)(cmHeight * 28.3465));
```

### 2. Funziona con versioni più vecchie di Aspose.Words?

L'API `Shadow` è stata introdotta nella versione 14.0. Se utilizzi una versione più vecchia, dovrai aggiornare tramite NuGet. Il resto del codice (creazione di forme) è stabile da molti anni, quindi non incontrerai cambiamenti incompatibili.

### 3. Posso aggiungere un'ombra ad altre forme (ad esempio, cerchi)?

Assolutamente—qualsiasi oggetto `Shape` espone una proprietà `Shadow`. Basta sostituire `ShapeType.Rectangle` con `ShapeType.Ellipse` o `ShapeType.Cloud`, poi applicare le stesse impostazioni dell'ombra.

### 4. E se avessi bisogno di un'ombra colorata (ad esempio, blu per un brand)?

Sostituisci `Color.Gray` con qualsiasi `Color` desideri:

```csharp
rectangle.Shadow.Color = Color.FromArgb(30, 0, 120); // Dark blue
```

Ricorda di regolare `Transparency` affinché il colore non diventi troppo dominante.

---

## 🎨 Riepilogo visivo

![crea una forma rettangolare con ombra in Word usando Aspose.Words](image-placeholder.png "crea una forma rettangolare con ombra in Word usando Aspose.Words")

*Testo alternativo: crea una forma rettangolare con ombra in Word usando Aspose.Words*

Lo screenshot (segnaposto) mostra il documento finale—solo il rettangolo e la sua morbida ombra grigia.

---

## Conclusione

Ora sai come **creare una forma rettangolare** in un file Word, **aggiungere un’ombra alla forma**, e perfezionare ogni aspetto visivo usando Aspose.Words per .NET. Il breve programma che abbiamo costruito copre l'intero flusso di lavoro—dalla

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}