---
category: general
date: 2026-02-18
description: Crea una forma rettangolare usando Aspose.Words e impara come aggiungere
  l'ombra, impostare le dimensioni della forma e salvare il documento Word in pochi
  minuti.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- save word document
- set shape size
- how to create document
language: it
og_description: Crea una forma rettangolare in un file Word, impara come aggiungere
  l'ombra, imposta le dimensioni della forma e salva il documento con Aspose.Words
  in C#.
og_title: Crea forma rettangolare in Word – Tutorial completo di Aspose.Words
tags:
- Aspose.Words
- C#
- Word automation
title: Crea una forma rettangolare in Word con Aspose.Words – Guida passo passo
url: /it/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare in Word con Aspose.Words – Guida passo‑passo

Hai mai dovuto **creare una forma rettangolare** in un file Word ma non sapevi da dove cominciare? Non sei l’unico—gli sviluppatori chiedono spesso: “come aggiungo un’ombra a una forma mantenendo il documento modificabile?” In questo tutorial risponderemo a questa domanda e ti mostreremo anche **come aggiungere l’ombra**, **impostare le dimensioni della forma** e **salvare il documento Word** tutto in un unico flusso fluido.

Ti guideremo attraverso tutto ciò di cui hai bisogno, dall’inizializzare un nuovo documento (sì, questo è il primo passo per **come creare un documento**) fino a persistere il *.docx* finale su disco. Nessun riferimento esterno, solo un esempio autonomo che puoi copiare‑incollare in Visual Studio e farlo girare subito.

---

## Prerequisiti

- .NET 6+ (o .NET Framework 4.7+). Aspose.Words funziona con qualsiasi runtime .NET recente.
- Una licenza valida di Aspose.Words (o la chiave di valutazione gratuita) – altrimenti vedrai una filigrana.
- Visual Studio, Rider, o qualsiasi editor C# tu preferisca.
- Conoscenze di base di C#—nulla di complicato, solo la capacità di eseguire un’app console.

> **Consiglio professionale:** Se sei su Mac, lo stesso codice gira su .NET 6 con VS Code—basta assicurarsi di aver referenziato il pacchetto NuGet `Aspose.Words`.

---

## Passo 1: Inizializza il documento – la base di **come creare un documento**

Prima di poter disegnare qualcosa, ci serve una tela vuota. Aspose.Words chiama questo un `Document`.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

> **Perché è importante:** L’oggetto `Document` rappresenta l’intero file *.docx*. Tutte le forme, i paragrafi e le sezioni che aggiungi diventano figli di questo oggetto. Partire da un documento pulito garantisce che nessuno stile nascosto interferisca con il tuo rettangolo.

---

## Passo 2: Definisci il rettangolo e **imposta le dimensioni della forma**

Un rettangolo è semplicemente uno `Shape` con `ShapeType.Rectangle`. Gli assegneremo dimensioni esplicite così apparirà esattamente come desiderato.

```csharp
// Step 2: Create a rectangular shape and define its size
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points (≈2.78 inches)
rectangleShape.Height = 100; // height in points (≈1.39 inches)
```

> **Cosa significano i numeri:** Aspose.Words utilizza i punti (1 pt = 1/72 in). Regola i valori per adattarli al tuo layout; per una tipica pagina A4, 200 pt è una larghezza comoda.

---

## Passo 3: **Come aggiungere l’ombra** – far risaltare la forma

Le ombre forniscono un indizio visivo che la forma è “sollevata” dalla pagina. La proprietà `Shadow` ti permette di regolare colore, distanza, trasparenza e sfocatura.

```csharp
// Step 3: Apply a shadow to the shape
rectangleShape.Shadow.Color        = Color.Black; // Shadow color
rectangleShape.Shadow.Distance    = 5;           // Offset distance in points
rectangleShape.Shadow.Transparency = 0.4;        // 40 % transparent
rectangleShape.Shadow.BlurRadius  = 8;           // Soft edge radius
```

> **Perché usare la trasparenza?** Un’ombra completamente opaca può risultare dura. Impostandola a 0.4 l’effetto diventa più sottile e professionale.

---

## Passo 4: Posiziona il rettangolo – flusso inline con il testo circostante

Se vuoi che la forma si comporti come un carattere in un paragrafo, imposta il suo `WrapType` a `Inline`. Questo mantiene il layout prevedibile, soprattutto quando il documento viene modificato in seguito.

```csharp
// Step 4: Set the shape to flow inline with the surrounding text
rectangleShape.WrapType = WrapType.Inline;
```

> **Caso limite:** Se ti serve che il rettangolo galleggi sopra il testo (ad esempio, una filigrana), cambia `WrapType` in `Square` o `BehindText`.

---

## Passo 5: Inserisci la forma nel corpo del documento

Ora inseriamo effettivamente il rettangolo nel primo paragrafo. Se il documento non ha ancora contenuto, `FirstParagraph` viene creato automaticamente.

```csharp
// Step 5: Insert the shape into the first paragraph of the document
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

> **Suggerimento:** Puoi anche creare un nuovo paragrafo prima e poi aggiungere la forma—utile quando hai bisogno di testo circostante.

---

## Passo 6: **Salva il documento Word** – l’ultimo passo

Con tutto al suo posto, persistere il file è una singola riga di codice. Scegli qualsiasi percorso ti piaccia; l’esempio usa un segnaposto che dovrai sostituire con la tua directory.

```csharp
// Step 6: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowShape.docx");
```

> **Risultato:** Apri il *.docx* generato in Microsoft Word. Vedrai un rettangolo con ombra nera, largo 200 pt e alto 100 pt, inserito inline con il primo paragrafo.

---

## Output previsto

Quando apri **ShadowShape.docx**, il documento mostra:

- Un singolo paragrafo contenente una forma rettangolare.
- Il rettangolo ha una leggera ombra nera spostata di 5 pt.
- Le dimensioni della forma corrispondono a quelle impostate nel Passo 2.
- Nessun testo extra appare a meno che non lo aggiungi manualmente.

Se la forma non appare, verifica di aver referenziato la versione corretta di Aspose.Words e che la tua licenza (o prova) sia attiva.

---

## Domande frequenti & Varianti

| Domanda | Risposta |
|----------|----------|
| *Posso cambiare il colore dell’ombra in qualcosa di diverso dal nero?* | Assolutamente—imposta `rectangleShape.Shadow.Color = Color.Blue;` o qualsiasi `System.Drawing.Color`. |
| *E se ho bisogno di un rettangolo più grande?* | Regola i valori di `Width` e `Height`. Ricorda che sono in punti; 72 pt = 1 in. |
| *È possibile posizionare la forma in una posizione assoluta?* | Sì—usa `WrapType = WrapType.Absolute` e imposta le proprietà `Top`/`Left`. |
| *Funziona con .NET Core?* | Sì. Aspose.Words è cross‑platform; basta installare il pacchetto NuGet per .NET Standard. |
| *Posso aggiungere testo all’interno del rettangolo?* | Non direttamente; dovresti inserire una forma `TextBox` invece di un semplice rettangolo. |

---

## Esempio completo (pronto per il copia‑incolla)

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialize a new document
        Document document = new Document();

        // 2️⃣ Create rectangle and set its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width  = 200;
        rectangleShape.Height = 100;

        // 3️⃣ Add a subtle black shadow
        rectangleShape.Shadow.Color         = Color.Black;
        rectangleShape.Shadow.Distance     = 5;
        rectangleShape.Shadow.Transparency = 0.4;
        rectangleShape.Shadow.BlurRadius   = 8;

        // 4️⃣ Make the shape flow inline with text
        rectangleShape.WrapType = WrapType.Inline;

        // 5️⃣ Insert the shape into the first paragraph
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // 6️⃣ Persist the file
        document.Save(@"C:\Temp\ShadowShape.docx");

        System.Console.WriteLine("Document saved successfully!");
    }
}
```

Esegui il programma, vai su `C:\Temp\ShadowShape.docx` e vedrai il rettangolo con ombra esattamente come descritto.

---

## Conclusione

Ora sai **come creare una forma rettangolare** in un file Word usando Aspose.Words, **impostare le dimensioni della forma**, **aggiungere l’ombra** e infine **salvare il documento Word** con le modifiche. L’intero processo—da **come creare un documento** alla persistenza del risultato—si riduce a poche righe di C# e può essere esteso per layout più complessi.

Pronto per la prossima sfida? Prova a sostituire il rettangolo con una forma ad angoli arrotondati, sperimenta diversi colori di ombra, o incorpora la forma dentro una cella di tabella. Ogni variazione rafforza gli stessi concetti fondamentali trattati qui.

Se questa guida ti è stata utile, condividila, lascia un commento con le tue varianti, o esplora gli altri tutorial sulla automazione di Word, come inserire immagini o generare tabelle con Aspose.Words. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}