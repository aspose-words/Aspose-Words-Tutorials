---
category: general
date: 2025-12-29
description: Crea una forma rettangolare in un documento Word usando Aspose.Words
  C#. Impara a impostare la trasparenza della forma, a impostare il colore dell'ombra
  e a salvare il documento Word senza sforzo.
draft: false
keywords:
- create rectangle shape
- set shape transparency
- set shadow color
- save word document
- create word document
language: it
og_description: Crea una forma rettangolare in un documento Word con Aspose.Words
  C#. Questa guida mostra come impostare la trasparenza della forma, impostare il
  colore dell'ombra e salvare il documento Word.
og_title: Crea forma rettangolare in Word – Tutorial completo di Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Crea una forma rettangolare in Word con Aspose.Words – Guida passo passo
url: /it/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare in Word – Tutorial completo di Aspose.Words

Hai mai dovuto **creare una forma rettangolare** in un documento Word ma non sapevi da dove cominciare? Non sei solo; molti sviluppatori incontrano questo ostacolo quando automatizzano report o fatture. In questa guida percorreremo passo passo le operazioni per creare una forma rettangolare, impostare la trasparenza della forma, impostare il colore dell’ombra e infine **salvare il documento Word** usando Aspose.Words per .NET.  

Copriamo tutto, dall’oggetto documento iniziale al file finale `.docx` su disco, così alla fine potrai **creare un documento Word** programmaticamente senza indovinare. Nessun riferimento esterno, solo una soluzione autonoma che puoi copiare‑incollare nel tuo progetto.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.7+)
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)
- Familiarità di base con la sintassi C#
- Un IDE a tua scelta (Visual Studio, Rider, VS Code, ecc.)

> **Pro tip:** Se stai usando una versione di prova gratuita di Aspose.Words, la libreria aggiungerà una filigrana al file di output. Per la produzione avrai bisogno di una licenza valida.

## Passo 1: Inizializzare il documento e il builder

La prima cosa che facciamo è creare un nuovo documento Word vuoto e un `DocumentBuilder` che ci permette di inserire contenuti. Pensa al builder come a una penna virtuale che disegna sulla pagina.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();

// The builder provides methods to add text, tables, shapes, etc.
DocumentBuilder builder = new DocumentBuilder(document);
```

> **Perché è importante:** Senza un `DocumentBuilder` dovresti manipolare direttamente l’albero dei nodi a basso livello, operazione soggetta a errori e più difficile da leggere.

## Passo 2: Creare la forma rettangolare

Ora **creiamo la forma rettangolare**. Il metodo `InsertShape` accetta un enum `ShapeType`, larghezza e altezza (in punti). L’oggetto `Shape` restituito ci consente di regolare le proprietà visive in seguito.

```csharp
// Insert a rectangle 150 pts wide and 80 pts tall
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

A questo punto il rettangolo è un blocco nero solido ancorato al paragrafo corrente. Puoi spostarlo, ridimensionarlo o anche ruotarlo più tardi, se necessario.

![crea forma rettangolare con ombra](/images/rectangle-shadow.png "Un documento Word che mostra una forma rettangolare con un’ombra grigia")

*Testo alternativo immagine: crea forma rettangolare con ombra in un documento Word*

## Passo 3: Impostare la trasparenza della forma

La trasparenza è il livello di “vedibilità” del riempimento della forma. Aspose.Words utilizza una proprietà `Transparency` che varia da `0.0` (opaco) a `1.0` (completamente trasparente). Qui **impostiamo la trasparenza della forma** al 40 % così il testo sottostante rimane leggibile.

```csharp
// Make the rectangle 40 % transparent
rectangleShape.Fill.Transparency = 0.4; // 0.0 = opaque, 1.0 = invisible
```

> **Caso limite:** Se ti serve una forma completamente invisibile ma vuoi comunque che l’ombra sia visibile, imposta `Transparency` a `1.0` e assegna alla forma una larghezza del contorno diversa da zero.

## Passo 4: Configurare l’ombra

Un’ombra leggera aggiunge profondità. **Imposteremo il colore dell’ombra** su un grigio medio, ne regoleremo il raggio di sfocatura e la sposteremo di qualche punto sia orizzontalmente che verticalmente.

```csharp
// Enable the shadow effect
rectangleShape.Shadow.Enabled = true;

// Shadow color – a neutral gray
rectangleShape.Shadow.Color = System.Drawing.Color.Gray;

// 40 % transparent shadow (same as shape's fill)
rectangleShape.Shadow.Transparency = 0.4;

// Blur radius makes the edge softer
rectangleShape.Shadow.Blur = 6;

// Horizontal and vertical offsets (in points)
rectangleShape.Shadow.OffsetX = 5;
rectangleShape.Shadow.OffsetY = 5;
```

> **Perché è importante:** Un’ombra troppo netta o troppo scura può sembrare un artefatto di stampa. Regola `Blur` e `Transparency` finché non sembra naturale.

## Passo 5: Salvare il documento Word

Infine **salviamo il documento Word** su disco. Il metodo `Save` determina automaticamente il formato del file dall’estensione; `.docx` è il formato OpenXML moderno.

```csharp
// Save the document to the desired folder
document.Save(@"C:\Temp\ShadowRectangle.docx");
```

Se la cartella non esiste, Aspose.Words solleverà un `ArgumentException`. Assicurati che il percorso sia valido o crea la directory in anticipo.

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per l’esecuzione, che combina tutti i passaggi. Copialo in un nuovo progetto console e premi **F5**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace AsposeRectangleDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Initialize document and builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert rectangle shape
            Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

            // 3️⃣ Set shape transparency (40 % transparent)
            rectangleShape.Fill.Transparency = 0.4;

            // 4️⃣ Configure shadow (color, blur, offset, transparency)
            rectangleShape.Shadow.Enabled = true;
            rectangleShape.Shadow.Color = System.Drawing.Color.Gray;
            rectangleShape.Shadow.Transparency = 0.4;
            rectangleShape.Shadow.Blur = 6;
            rectangleShape.Shadow.OffsetX = 5;
            rectangleShape.Shadow.OffsetY = 5;

            // 5️⃣ Save the document
            string outputPath = @"C:\Temp\ShadowRectangle.docx";
            document.Save(outputPath);

            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

### Risultato atteso

Apri `ShadowRectangle.docx` in Microsoft Word. Dovresti vedere un rettangolo grigio chiaro con un’ombra soffice, leggermente spostata, entrambi renderizzati al 40 % di trasparenza. La forma si trova su una pagina vuota, pronta per contenuti aggiuntivi.

## Domande frequenti e varianti

**E se avessi bisogno di una forma diversa?**  
Sostituisci `ShapeType.Rectangle` con qualsiasi altro valore enum (`Ellipse`, `Triangle`, `Star`, ecc.). Il resto del codice rimane invariato.

**Posso cambiare il colore del contorno?**  
Sì—usa `rectangleShape.StrokeColor = System.Drawing.Color.Blue;` e, opzionalmente, imposta `rectangleShape.StrokeWeight = 1.5;`.

**Come posizionare la forma in una posizione specifica nella pagina?**  
Imposta `rectangleShape.WrapType = WrapType.None;` e poi regola le proprietà `rectangleShape.Left` e `rectangleShape.Top` (i valori sono in punti).

**È possibile aggiungere testo all’interno del rettangolo?**  
Assolutamente. Dopo aver creato la forma, puoi chiamare `rectangleShape.AppendChild(new Paragraph(document))` e poi aggiungere un `Run` con il tuo testo. Ricorda di impostare le proprietà `rectangleShape.TextBox` se desideri una formattazione più ricca.

## Pro Tips & Pitfalls

- **Licenza anticipata:** Se dimentichi di applicare una licenza, Aspose.Words inserirà una filigrana nella prima pagina, il che può creare confusione durante i test.
- **Suggerimento sulle prestazioni:** Quando generi molti documenti in un ciclo, riutilizza un’unica istanza di `Document` e chiama `document.RemoveAllChildren();` dopo ogni salvataggio per evitare un eccessivo carico sul GC.
- **Visibilità dell’ombra:** Su schermi a bassa risoluzione un’ombra sottile può apparire invisibile. Aumenta `Blur` o `OffsetX/Y` per il debug, poi riduci per la produzione.

## Prossimi passi

Ora che sai **creare una forma rettangolare**, **impostare la trasparenza della forma**, **impostare il colore dell’ombra** e **salvare il documento Word**, considera di estendere il tutorial:

- Aggiungere più forme e raggrupparle.
- Inserire il rettangolo all’interno di una cella di tabella per un layout di report.
- Combinare la forma con `DocumentBuilder.InsertHtml` per sovrapporre contenuti HTML stilizzati.
- Esplorare altri effetti visivi come `Glow` o `Reflection` per documenti più ricchi, simili a UI.

Sperimenta, rompi le cose, e poi perfeziona—la generazione programmatica di documenti è un playground dove il design visivo incontra il codice.

---

*Buona programmazione! Se hai incontrato difficoltà, lascia un commento qui sotto e risolveremo insieme.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}