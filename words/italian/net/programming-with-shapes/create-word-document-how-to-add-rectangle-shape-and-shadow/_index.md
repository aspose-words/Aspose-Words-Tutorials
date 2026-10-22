---
category: general
date: 2026-03-19
description: Crea un documento Word in C# con Aspose.Words, impara come aggiungere
  una forma, aggiungere una forma rettangolare, applicare l'ombra e salvare il documento
  come docx in pochi minuti.
draft: false
keywords:
- create word document
- how to add shape
- add rectangle shape
- save document as docx
- add shadow to shape
language: it
og_description: Crea un documento Word con Aspose.Words, aggiungi una forma rettangolare,
  applica un'ombra esterna e salva il documento in formato docx. Guida passo‑passo.
og_title: Crea documento Word – Aggiungi forma rettangolare e ombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Crea documento Word – Come aggiungere una forma rettangolare e l'ombra
url: /it/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word – Come aggiungere una forma rettangolare e un'ombra

Ti è mai capitato di dover **create word document** programmaticamente e di chiederti da dove cominciare? Non sei solo. Molti sviluppatori incontrano lo stesso ostacolo quando provano per la prima volta a generare un file .docx che contiene grafiche personalizzate. In questo tutorial percorreremo l'intero processo—come aggiungere una forma, nello specifico un **add rectangle shape**, darle un elegante **add shadow to shape**, e infine **save document as docx**.  

Alla fine della guida avrai uno snippet C# pronto all'uso che potrai inserire in qualsiasi progetto .NET. Nessun riferimento vago, solo un esempio completo e eseguibile.  

## Prerequisites

- .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework).  
- Aspose.Words per .NET installato (pacchetto NuGet `Aspose.Words`).  
- Una conoscenza di base della sintassi C#—non è necessario nulla di complesso.  

Se ti manca la libreria, esegui:

```bash
dotnet add package Aspose.Words
```

È tutto—nessun SDK aggiuntivo, nessun interop COM, solo un'unica referenza NuGet.

---

## Passo 1: Crea un documento Word (Obiettivo principale)

La prima cosa di cui abbiamo bisogno è una tela pulita. Pensa alla classe `Document` come a una pagina nuova in Microsoft Word; contiene sezioni, paragrafi e tutto il resto che aggiungerai in seguito.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Step 1: Initialize a new blank document
Document doc = new Document();               // This creates an empty .docx in memory
```

Perché iniziare con un `Document` vuoto? Perché garantisce che nessuna formattazione nascosta si infiltri da un modello. Nella mia esperienza, partire da zero evita spostamenti misteriosi del layout quando inserisci successivamente le forme.

---

## Passo 2: Inserisci una forma rettangolare – Aggiungere l'elemento visivo

Ora che abbiamo un documento, aggiungiamo **add rectangle shape** al primo paragrafo. L'oggetto `Shape` è versatile; puoi scegliere `ShapeType.Rectangle`, `Ellipse` o anche disegni personalizzati. Ecco il codice minimale:

```csharp
// Step 2: Create a rectangle and attach it to the first paragraph
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.78 inches)
    Height = 100,              // Height in points (≈1.39 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};

// Append the shape to the first paragraph (creates one if missing)
Paragraph firstPara = doc.FirstSection.Body.FirstParagraph;
firstPara.AppendChild(rect);
```

**Cosa succede dietro le quinte?**  
- `ShapeType.Rectangle` indica ad Aspose che vogliamo un semplice riquadro.  
- `WrapType.Inline` assicura che il rettangolo si muova con il flusso del testo, che è solitamente ciò che ti aspetti in uno scenario di elaborazione testi.  
- Aggiungendo a `FirstParagraph`, evitiamo la necessità di inserire manualmente un nuovo paragrafo; Aspose ne crea uno per noi se il documento è davvero vuoto.

> **Consiglio professionale:** Se hai bisogno che la forma si trovi *dietro* al testo, cambia `WrapType` in `WrapType.Transparent`. Questa piccola modifica può fare una grande differenza visiva.

---

## Passo 3: Applica un'ombra esterna – Migliorare l'aspetto

Un rettangolo piatto è… beh, piatto. Aggiungere un **add shadow to shape** gli conferisce profondità senza immagini aggiuntive. `ShadowFormat` di Aspose rende tutto questo una singola riga.

```csharp
// Step 3: Configure an outer shadow for the rectangle
rect.ShadowFormat.Type = ShadowType.OuterShadow;
rect.ShadowFormat.Blur = 5.0;           // Softness of the shadow edge
rect.ShadowFormat.Distance = 3.0;      // How far the shadow is offset
rect.ShadowFormat.Angle = 45;          // Direction in degrees (45° = bottom‑right)
rect.ShadowFormat.Color = Color.Gray; // Classic gray shadow
```

Perché preoccuparsi di questi valori specifici?  
- **Blur** di `5.0` fornisce un bordo sfumato sottile che appare professionale sulla maggior parte dei monitor.  
- **Distance** di `3.0` e **Angle** di `45` creano una fonte di luce naturale dall'alto‑sinistra, una convenzione di design comune.  
- **Color.Gray** funziona sia su temi chiari che scuri; puoi sostituirlo con `Color.Black` se ti serve un contrasto più forte.

Se mai avessi bisogno di un'ombra *interna* (pensa a un pulsante incassato), basta cambiare `ShadowType.OuterShadow` in `ShadowType.InnerShadow`. Le stesse proprietà si applicano comunque.

---

## Passo 4: Salva il documento come DOCX – Conservare il tuo lavoro

Tutto questo è divertente, ma alla fine vorrai un file su disco. Il passo **save document as docx** è semplice:

```csharp
// Step 4: Persist the document to a .docx file
string outputPath = @"C:\Temp\ShadowedRectangle.docx";
doc.Save(outputPath, SaveFormat.Docx);
```

Un paio di note:  
- L'enumerazione `SaveFormat.Docx` garantisce il formato moderno Office Open XML, compatibile con Word 2007+.  
- Se hai bisogno di trasmettere il file direttamente a una risposta web, sostituisci il percorso del file con un `MemoryStream` e scrivilo nella risposta HTTP.

Dopo aver eseguito il codice, apri `ShadowedRectangle.docx` in Microsoft Word. Dovresti vedere un rettangolo grigio con un'ombra soffusa, posizionato inline con il primo paragrafo—esattamente quello che volevamo ottenere.

---

## Come aggiungere una forma – Approcci alternativi

L'esempio sopra utilizza l'approccio *inline*, ma a volte vuoi una forma che fluttui sopra il testo. È qui che entra in gioco **how to add shape** con diversi tipi di avvolgimento.

```csharp
Shape floatingRect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 250,
    Height = 120,
    WrapType = WrapType.Square, // Allows text to wrap around the shape
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    HorizontalAlignment = HorizontalAlignment.Center
};

doc.FirstSection.Body.FirstParagraph.AppendChild(floatingRect);
```

Qui abbiamo cambiato `WrapType` in `Square` e centrato la forma sulla pagina. Questo schema è utile per copertine o banner decorativi. Ricorda: le forme fluttuanti aumentano leggermente la dimensione del file perché Word memorizza dati di posizionamento aggiuntivi.

---

## Output previsto e verifica

Quando apri il file generato, dovresti vedere:

- Un singolo paragrafo contenente un rettangolo grigio.  
- Il rettangolo misura approssimativamente 2,8 × 1,4 pollici.  
- Un'ombra esterna sottile spostata verso il basso‑destra.  

Se la forma appare *fuori* dal paragrafo, ricontrolla il `WrapType`. Se l'ombra sembra troppo dura, riduci il valore `Blur` o cambia il `Color` in una tonalità più chiara.

---

## Problemi comuni e come evitarli

| Problema | Perché succede | Soluzione |
|----------|----------------|-----------|
| La forma scompare dopo il salvataggio | `WrapType` impostato su `Inline` ma il paragrafo è stato rimosso | Assicurati che il paragrafo esista; usa `doc.FirstSection.Body.FirstParagraph` per garantirlo. |
| L'ombra appare pixelata | Uso di un valore `Blur` molto basso | Aumenta `Blur` ad almeno `3.0` per bordi lisci. |
| La dimensione del file aumenta notevolmente | Aggiunta di molte immagini ad alta risoluzione insieme alle forme | Usa `doc.RemoveUnusedResources()` prima del salvataggio se hai aggiunto immagini. |
| Il colore non è visibile in modalità scura | Uso di un `Color` scuro per la forma stessa | Scegli un colore contrastante (ad es., `Color.White`) per una migliore visibilità. |

---

## Esempio completo funzionante

Di seguito trovi il codice completo, pronto per il copia‑incolla, che incorpora tutto ciò di cui abbiamo parlato. Sentiti libero di eseguirlo come applicazione console.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank Word document
        Document doc = new Document();

        // 2️⃣ Add a rectangle shape to the first paragraph
        Shape rect = new Shape(doc, ShapeType.Rectangle)
        {
            Width = 200,
            Height = 100,
            WrapType = WrapType.Inline
        };
        doc.FirstSection.Body.FirstParagraph.AppendChild(rect);

        // 3️⃣ Apply an outer shadow to the rectangle
        rect.ShadowFormat.Type = ShadowType.OuterShadow;
        rect.ShadowFormat.Blur = 5.0;
        rect.ShadowFormat.Distance = 3.0;
        rect.ShadowFormat.Angle = 45;
        rect.ShadowFormat.Color = Color.Gray;

        // 4️⃣ Save the document as a .docx file
        string outPath = @"C:\Temp\ShadowShape.docx";
        doc.Save(outPath, SaveFormat.Docx);

        // Optional: Let the user know we’re done
        System.Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**La spiegazione di ogni blocco** è inline come commenti, soddisfacendo sia i lettori SEO sia gli assistenti AI che amano risposte auto‑contenute.

---

## Conclusione

Abbiamo appena **create word document** da zero, imparato **how to add shape**, nello specifico un **add rectangle shape**, gli abbiamo aggiunto un **add shadow to shape**, e infine **save document as docx**. I passaggi sono semplici, il codice è compatto e il risultato appare rifinito.  

Se sei pronto a fare di più, prova a sostituire il rettangolo con un'immagine personalizzata, sperimenta con diversi colori di ombra, o genera un intero report con più sezioni con forme. L'API Aspose.Words è sufficientemente flessibile da gestire tutto, dalle fatture ai depliant di marketing.  

Hai domande su altri tipi di forma o hai bisogno di aiuto per integrare questo in un servizio ASP.NET Core? Lascia un commento qui sotto, e buona programmazione! 

![crea documento word con forma rettangolare e ombra](placeholder-image.png "crea documento word con forma rettangolare e ombra"

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}