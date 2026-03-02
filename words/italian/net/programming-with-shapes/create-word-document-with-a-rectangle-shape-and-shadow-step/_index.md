---
category: general
date: 2026-03-01
description: Crea un documento Word usando Aspose.Words e impara come aggiungere una
  forma rettangolare, come aggiungere l'ombra, come impostare la trasparenza e come
  creare una forma—tutto in C#.
draft: false
keywords:
- create word document
- add rectangle shape
- how to add shadow
- how to create shape
- how to set transparency
language: it
og_description: Crea un documento Word con Aspose.Words in C#. Scopri come aggiungere
  una forma rettangolare, applicare un'ombra esterna e impostare la trasparenza in
  pochi passaggi.
og_title: Crea documento Word con una forma rettangolare e ombra – Guida
tags:
- Aspose.Words
- C#
- Document Generation
title: Crea un documento Word con una forma rettangolare e ombra – Guida passo‑passo
url: /it/net/programming-with-shapes/create-word-document-with-a-rectangle-shape-and-shadow-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word con una forma rettangolare e ombra – Guida passo‑passo

Hai mai dovuto **creare un documento Word** che contenga un rettangolo con stile personalizzato? Forse stai costruendo un modello di report e vuoi un’ombra leggera per far risaltare il layout. Non sei l’unico—gli sviluppatori chiedono continuamente: “Come aggiungo una forma rettangolare e un’ombra programmaticamente?” La buona notizia è che con Aspose.Words puoi farlo in poche righe.

In questo tutorial percorreremo l’intero processo: dalla creazione di un file Word vuoto, all’aggiunta di una forma rettangolare, alla configurazione di un’ombra esterna con trasparenza. Alla fine avrai un file `Shadow.docx` pronto all’uso, che potrai aprire in Word e vedere l’effetto immediatamente. Nessun tool esterno, nessun XML complicato—solo codice C# pulito e spiegazioni chiare.

## Cosa imparerai

- **Come creare oggetti shape** in un documento Word usando Aspose.Words.  
- **Come aggiungere una forma rettangolare** a un paragrafo senza disturbare il contenuto esistente.  
- **Come aggiungere un’ombra** (ombra esterna) e controllarne colore, offset, sfocatura e trasparenza.  
- **Come impostare la trasparenza** sull’ombra per un aspetto professionale.  
- Suggerimenti, insidie e varianti utili nei progetti reali.

### Prerequisiti

- .NET 6.0 o successivo (l’API funziona anche con .NET Framework 4.6+).  
- Aspose.Words per .NET installato via NuGet (`Install-Package Aspose.Words`).  
- Una conoscenza di base della sintassi C#—nulla di complesso, solo le consuete istruzioni `using` e la creazione di oggetti.

> **Pro tip:** Se usi Visual Studio, abilita i “nullable reference types” per intercettare eventuali bug di riferimento nullo in anticipo.

## Passo 1 – Crea un documento Word vuoto

Per **creare un documento Word** iniziamo con la classe `Document`. Pensala come una tela vuota; potrai aggiungere sezioni, paragrafi, tabelle o forme in seguito.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Initialize a new blank document
Document document = new Document();
```

Perché abbiamo bisogno di una nuova istanza di `Document`? Perché ogni forma, paragrafo o stile vive all’interno di un modello a oggetti del documento (DOM). Partire da un documento pulito garantisce che il rettangolo che aggiungi non interferisca con contenuti preesistenti.

## Passo 2 – Definisci la forma rettangolare

Ora vediamo **come creare una shape** rettangolare. Il costruttore `Shape` richiede il documento proprietario e il tipo di forma. Impostiamo anche larghezza e altezza in punti (1 pt ≈ 1/72 in).

```csharp
// Create a rectangle shape
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width = 200;   // 200 pt ≈ 2.78 in
rectangleShape.Height = 100; // 100 pt ≈ 1.39 in
```

Ti potresti chiedere: “Posso usare i centimetri invece dei punti?” L’API accetta solo punti, ma puoi convertire: `points = centimeters * 28.35`. Questa piccola conversione è utile quando allinei le forme ai margini della pagina.

## Passo 3 – Aggiungi un’ombra esterna e imposta la trasparenza

Qui avviene la magia: **come aggiungere un’ombra** e **come impostare la trasparenza** su quell’ombra. La proprietà `ShadowFormat` ti dà il pieno controllo.

```csharp
// Enable shadow visibility
rectangleShape.ShadowFormat.Visible = true;

// Choose a shadow color
rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;

// Set transparency (0 = opaque, 1 = fully transparent)
rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent

// Position the shadow relative to the shape
rectangleShape.ShadowFormat.OffsetX = 5; // horizontal offset in points
rectangleShape.ShadowFormat.OffsetY = 5; // vertical offset in points

// Blur makes the shadow look softer
rectangleShape.ShadowFormat.BlurRadius = 4;

// Specify that this is an outer shadow (instead of inner)
rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;
```

**Perché queste impostazioni?**  
- **Transparency** permette alla trama della pagina sottostante di intravedersi, evitando che l’ombra appaia troppo pesante.  
- **OffsetX/Y** creano l’illusione che la forma sia sollevata dalla pagina.  
- **BlurRadius** ammorbidisce i bordi—senza di esso l’ombra sarebbe un rettangolo netto, poco naturale.  

Se desideri un effetto più drammatico, aumenta `OffsetX/Y` a 10 e `BlurRadius` a 8. Al contrario, per un accenno delicato, mantienili a 2 e 2 rispettivamente.

## Passo 4 – Inserisci la forma nel documento

Ora **aggiungiamo la forma rettangolare** al primo paragrafo del documento. Se il documento non contiene contenuti, `FirstParagraph` viene creato automaticamente per te.

```csharp
// Append the rectangle to the first paragraph
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

E se vuoi la forma all’interno di una cella di tabella specifica o in un paragrafo successivo? Basta individuare quel nodo (`doc.GetChild(NodeType.Paragraph, index, true)`) e chiamare `AppendChild` su di esso. Lo stesso oggetto shape può essere clonato se ti servono più copie.

## Passo 5 – Salva il documento

Infine, **creiamo il file word document** su disco. Usa un percorso adatto al tuo ambiente; l’esempio utilizza un segnaposto.

```csharp
// Save the document as a .docx file
document.Save(@"YOUR_DIRECTORY/Shadow.docx");
```

Quando apri `Shadow.docx` in Microsoft Word, vedrai un rettangolo grigio chiaro con un’ombra esterna morbida spostata verso il basso‑destra. La trasparenza del 30 % dell’ombra assicura che non domini la pagina.

---

![Create word document with a shadowed rectangle shape](image.png "Create word document with a shadowed rectangle shape")

*Testo alternativo immagine: crea un documento Word con una forma rettangolare ombreggiata*

## Codice completo, pronto all’esecuzione

Di seguito trovi il programma completo che puoi copiare‑incollare in un’app console. Nessun pezzo mancante, nessun “vedi la documentazione per ulteriori dettagli”.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Step 1: Create a new blank document
        Document document = new Document();

        // Step 2: Add a rectangular shape and define its size
        Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
        rectangleShape.Width = 200;   // width in points
        rectangleShape.Height = 100;  // height in points

        // Step 3: Configure an outer shadow for the shape
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = System.Drawing.Color.DarkGray;
        rectangleShape.ShadowFormat.Transparency = 0.3;   // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;          // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;          // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;
        rectangleShape.ShadowFormat.Style = ShadowStyle.OuterShadow;

        // Step 4: Insert the shape into the first paragraph of the document
        document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

        // Step 5: Save the document with the shadowed shape
        document.Save(@"YOUR_DIRECTORY/Shadow.docx");

        Console.WriteLine("Word document created successfully at YOUR_DIRECTORY/Shadow.docx");
    }
}
```

### Risultato atteso

- Un file chiamato **Shadow.docx** appare nella cartella di destinazione.  
- Aprendolo in Word si vede un rettangolo (200 × 100 pt) con un’ombra esterna grigio scuro.  
- L’ombra è spostata di 5 pt in orizzontale e verticale, sfocata e con trasparenza del 30 %.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|----------|
| **Posso cambiare il colore dell’ombra per adattarlo al mio brand?** | Assolutamente—basta sostituire `System.Drawing.Color.DarkGray` con qualsiasi `Color` preferisci, ad es. `Color.FromArgb(255, 0, 120, 215)` per un accento blu. |
| **E se mi serve un’ombra interna invece di quella esterna?** | Imposta `ShadowFormat.Style = ShadowStyle.InnerShadow`. Le altre proprietà funzionano allo stesso modo. |
| **La trasparenza è supportata nelle versioni più vecchie di Word?** | Sì. Aspose.Words scrive l’XML appropriato che Word 2007+ interpreta. Le versioni più vecchie potrebbero ignorare il valore di trasparenza ma mostreranno comunque l’ombra. |
| **Posso aggiungere più forme con ombre diverse?** | Certo—basta creare nuove istanze di `Shape`, configurare ogni ombra in modo indipendente e aggiungerle ai nodi desiderati. |
| **Che cosa succede alle prestazioni con centinaia di forme?** | Creare molte forme può aumentare l’uso di memoria. Riutilizza una singola istanza di `Document` e aggiungi le forme in un ciclo; rilascia gli oggetti temporanei se incontri problemi di memoria. |

## Suggerimenti per progetti reali

- **Generazione batch:** Quando generi report per molti utenti, istanzia un unico modello `Document` e clonalo per ogni iterazione. Sostituisci i segnaposto prima di aggiungere le forme.  
- **Dimensionamento dinamico:** Usa le dimensioni della pagina (`document.FirstSection.PageSetup.PageWidth`) per calcolare la dimensione della forma in relazione alla pagina, garantendo layout coerenti su diversi formati di carta.  
- **Testing:** Apri sempre il `.docx` generato in Word dopo aver modificato i parametri dell’ombra. Il feedback visivo è più veloce di un’ipotesi numerica.

## Prossimi passi

Ora che sai **come aggiungere una forma rettangolare**, **come aggiungere un’ombra** e **come impostare la trasparenza**, considera di approfondire:

- Aggiungere **riempimenti a gradiente** alle forme (`Shape.FillFormat`).  
- Incorporare **immagini** all’interno delle forme per effetti di filigrana.  
- Usare **tabelle** per allineare più forme ombreggiate in una griglia.  
- Esportare lo stesso documento in PDF (`document.Save("output.pdf")`) mantenendo le ombre.

Ognuna di queste estensioni si basa sugli stessi concetti di base, così ti sentirai a tuo agio nell’espandere il codice.

---

### Riepilogo

Abbiamo iniziato **creando un documento Word** con Aspose.Words, poi **creato una shape** rettangolare, applicato **un’ombra**, regolato **la trasparenza**, e salvato il risultato. L’intero processo è racchiuso in un modello compatto e riutilizzabile che puoi adattare a qualsiasi scenario di automazione.

Sentiti libero di sperimentare—cambia colori, gioca con gli offset o impila più forme insieme. Se incontri un ostacolo, torna alle sezioni sopra; sono pensate come riferimento rapido. Buona programmazione, e che i tuoi documenti siano sempre impeccabili!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}