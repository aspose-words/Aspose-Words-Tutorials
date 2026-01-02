---
category: general
date: 2026-01-02
description: Crea un documento Word con una forma rettangolare, imposta il colore
  di riempimento della forma e salva il file docx usando Aspose.Words. Scopri come
  creare un rettangolo con ombra in pochi minuti.
draft: false
keywords:
- create word document
- add rectangle shape
- set shape fill color
- save docx file
- how to create rectangle
language: it
og_description: Crea un documento Word con un rettangolo personalizzato, imposta il
  colore di riempimento, aggiungi un'ombra e salva come DOCX. Codice completo e spiegazioni.
og_title: Crea documento Word con forma rettangolare – Passo dopo passo
tags:
- Aspose.Words
- C#
- Document Generation
title: Crea documento Word con forma rettangolare e ombra – Guida completa
url: /it/net/programming-with-shapes/create-word-document-with-rectangle-shape-and-shadow-complet/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con forma rettangolare e ombra – Guida completa

Ti sei mai chiesto come **create word document** che contenga un rettangolo ben stilizzato? Forse ti serve un segnaposto per un logo, un banner colorato, o semplicemente un'indicazione visiva in un report. In questo tutorial **add rectangle shape**, gli assegneremo un colore di riempimento, applicheremo un'ombra sottile e infine **save docx file** – tutto con Aspose.Words per .NET.

Otterrai uno snippet C# pronto all'uso, una chiara spiegazione di ogni riga e una serie di consigli che potrai riutilizzare nei tuoi progetti. Niente superfluo, solo una soluzione pratica da copiare‑incollare.

## Di cosa avrai bisogno

- .NET 6 o successivo (il codice funziona anche su .NET Framework)  
- Visual Studio 2022 (o qualsiasi editor preferisci)  
- **Aspose.Words** pacchetto NuGet (`Install-Package Aspose.Words`)  

Se li hai già, ottimo – tuffiamoci.

## Passo 1 – Inizializzare un nuovo documento (How to create word document)

La prima cosa da fare è **create word document** in memoria. Pensalo come aprire una tela vuota dove disegnerai più tardi il tuo rettangolo.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // for Color struct

// Create a fresh, empty document
Document document = new Document();

// DocumentBuilder helps us add content step‑by‑step
DocumentBuilder builder = new DocumentBuilder(document);

// Write a simple heading so you can see something when you open the file
builder.Writeln("Shadow Demo");
```

> **Perché è importante:** `Document` rappresenta l'intero file DOCX, mentre `DocumentBuilder` è un comodo helper che ti permette di inserire testo, tabelle, immagini e forme senza gestire manualmente l'albero dei nodi sottostante.

## Passo 2 – Inserire una forma rettangolare (Add rectangle shape)

Ora **add rectangle shape** al documento. Il metodo `InsertShape` accetta il tipo di forma e le sue dimensioni in punti (1 punto = 1/72 di pollice).

```csharp
// Insert a rectangle that will later receive a custom shadow
Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);

// Give the rectangle a light‑blue background so it stands out
rect.FillColor = Color.LightBlue;
```

> **Consiglio:** Se mai dovessi creare una geometria diversa (ellisse, triangolo, ecc.), basta cambiare `ShapeType.Rectangle` con il valore enum desiderato.

## Passo 3 – Configurare l'ombra (Set shape fill color & shadow)

Un'ombra può far sembrare una forma piatta più tridimensionale. Qui abilitiamo l'ombra e ne modifichiamo l'aspetto.

```csharp
// Turn the shadow on
rect.ShadowFormat.Enabled = true;

// Choose a subtle gray for the shadow color
rect.ShadowFormat.Color = Color.Gray;

// Blur softens the edge of the shadow – 8 points looks nice
rect.ShadowFormat.BlurRadius = 8;

// Distance controls how far the shadow is offset from the shape
rect.ShadowFormat.Distance = 5;

// Angle determines the direction; 45° gives a bottom‑right offset
rect.ShadowFormat.Angle = 45;

// Transparency makes the shadow partially see‑through (0 = opaque, 1 = invisible)
rect.ShadowFormat.Transparency = 0.3; // 30 % transparent
```

> **Perché questi valori?** Un raggio di sfocatura moderato e una distanza di 5 punti impediscono all'ombra di sovrastare la forma, mentre 45° imita una fonte luminosa proveniente dall'alto‑sinistra – una convenzione UI comune.

## Passo 4 – Salvare il documento (Save docx file)

Infine, **save docx file** su disco. Regola il percorso in base al tuo ambiente.

```csharp
// Replace with the folder you actually want to use
string outputPath = @"C:\Temp\ShadowDemo.docx";

// Persist the document as a .docx file
document.Save(outputPath);
```

Quando apri `ShadowDemo.docx` in Word, dovresti vedere un rettangolo azzurro chiaro con un'ombra grigia morbida, proprio come nella schermata qui sotto.

![Crea documento Word con forma rettangolare e ombra](https://example.com/images/rectangle-shadow.png "Crea documento Word con forma rettangolare e ombra")

*Testo alternativo dell'immagine:* **Crea documento Word** che mostra una forma rettangolare con un'ombra.

## Esempio completo, pronto all'esecuzione (How to create rectangle and save)

Mettendo tutto insieme, ecco il programma completo che puoi copiare in un'app console:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 1: Initialize the document
            Document doc = new Document();
            DocumentBuilder builder = new DocumentBuilder(doc);
            builder.Writeln("Shadow Demo");

            // Step 2: Insert the rectangle
            Shape rect = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rect.FillColor = Color.LightBlue;   // set shape fill color

            // Step 3: Apply shadow formatting
            rect.ShadowFormat.Enabled = true;
            rect.ShadowFormat.Color = Color.Gray;
            rect.ShadowFormat.BlurRadius = 8;
            rect.ShadowFormat.Distance = 5;
            rect.ShadowFormat.Angle = 45;
            rect.ShadowFormat.Transparency = 0.3;

            // Step 4: Save the file
            string output = @"C:\Temp\ShadowDemo.docx";
            doc.Save(output);

            System.Console.WriteLine($"Document saved to {output}");
        }
    }
}
```

### Risultato atteso

- Un file chiamato **ShadowDemo.docx** appare nella cartella di destinazione.  
- Aprendolo in Microsoft Word mostra una singola pagina con il testo “Shadow Demo” seguito da un rettangolo azzurro chiaro.  
- Il rettangolo proietta un'ombra grigia morbida a 45°, conferendogli una leggera sensazione 3‑D.

## Domande comuni e casi particolari

### E se avessi bisogno di una dimensione diversa?

Basta modificare gli argomenti `200, 100` in `InsertShape`. Quei numeri rappresentano larghezza e altezza in punti. Per un quadrato, usa valori identici.

### Posso rendere l'ombra più marcata?

Aumenta `BlurRadius` per un bordo più morbido, alza `Distance` per uno spostamento maggiore, o diminuisci `Transparency` (es., `0.1`) per renderla più scura.

### Come aggiungere un bordo attorno al rettangolo?

```csharp
rect.LineColor = Color.DarkBlue;   // border color
rect.LineWidth = 2;                // thickness in points
```

### È compatibile con versioni precedenti di Aspose.Words?

Sì. La classe `ShadowFormat` esiste fin dalle versioni iniziali del 2020. Se utilizzi una versione molto vecchia, potresti dover aggiornare per accedere a tutte le proprietà.

## Consigli e insidie

- **Consiglio:** Disporre sempre di documenti di grandi dimensioni (`doc.Dispose()`) quando hai finito, specialmente nelle applicazioni web, per liberare le risorse native.  
- **Attenzione:** Usare un percorso relativo senza le corrette autorizzazioni può causare `UnauthorizedAccessException`. Preferisci percorsi assoluti o assicurati che il pool dell'app abbia i permessi di scrittura.  
- **Ricorda:** La proprietà `FillColor` accetta qualsiasi `System.Drawing.Color`. Sentiti libero di usare `Color.FromArgb(255, 173, 216, 230)` per una tonalità pastello personalizzata.

## Prossimi passi

Ora che sai come **create word document**, **add rectangle shape**, **set shape fill color** e **save docx file**, puoi sperimentare ulteriormente:

- Inserisci più forme e disponile con `RelativeHorizontalPosition` e `RelativeVerticalPosition`.  
- Combina il rettangolo con testo usando `Shape.TextBox` per le didascalie.  
- Esporta lo stesso documento in PDF (`doc.Save("output.pdf")`) per la distribuzione.

Se sei curioso di grafica più avanzata, dai un'occhiata al supporto di Aspose.Words per **WordArt**, **charts** e **inline images**. Ognuno segue lo stesso schema: crea un nodo, configura le sue proprietà e salva.

---

### TL;DR

- Usa `Document` e `DocumentBuilder` per **create word document**.  
- Chiama `InsertShape(ShapeType.Rectangle, …)` per **add rectangle shape**.  
- Imposta `FillColor` per lo sfondo desiderato.  
- Abilita `ShadowFormat` e regola le sue proprietà per un aspetto curato.  
- Concludi con `document.Save("yourPath.docx")` per **save docx file**.

Buon coding e divertiti a rendere i tuoi file Word un po' più eleganti!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}