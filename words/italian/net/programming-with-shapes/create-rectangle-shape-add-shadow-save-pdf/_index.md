---
category: general
date: 2026-02-24
description: Crea una forma rettangolare in C# usando Aspose.Words, aggiungi un'ombra
  alla forma e salva il documento come PDF. Scopri come aggiungere l'ombra e come
  salvare il PDF in pochi minuti.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- save document as pdf
- how to add shadow
- how to save pdf
language: it
og_description: Crea una forma rettangolare in C# con Aspose.Words, quindi aggiungi
  l'ombra alla forma e salva il documento come PDF – una guida completa, passo dopo
  passo.
og_title: Crea forma rettangolare, aggiungi ombra e salva PDF
tags:
- Aspose.Words
- C#
- PDF generation
title: Crea forma rettangolare, aggiungi ombra e salva PDF
url: /it/net/programming-with-shapes/create-rectangle-shape-add-shadow-save-pdf/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare, aggiungi ombra e salva PDF

Mai avuto bisogno di **creare una forma rettangolare** in un documento Word ma desideravi anche una bella ombra e un output PDF? Non sei l'unico. In molti progetti di reporting o generazione di fatture, la rifinitura visiva — come un'ombra sottile — fa la differenza tra “un semplice file” e “un documento di livello professionale.”  

In questo tutorial vedremo esattamente questo: usare **Aspose.Words for .NET** per creare una forma rettangolare, aggiungere un'ombra alla forma e infine **salvare il documento come PDF**. Alla fine avrai un'app console C# pronta all'uso che produce un PDF con un rettangolo ombreggiato, e comprenderai come regolare l'ombra o modificare le opzioni di esportazione.

## Cosa ti serve

- .NET 6 SDK (o qualsiasi versione recente di .NET) – l'API funziona allo stesso modo anche su .NET Framework 4.x.  
- Pacchetto NuGet Aspose.Words for .NET (`Aspose.Words`) – installalo con `dotnet add package Aspose.Words`.  
- Un editor di codice – Visual Studio, VS Code o Rider vanno bene.  

Nessun passaggio di licenza aggiuntivo per questo esempio; la modalità di valutazione gratuita è sufficiente per vedere l'output PDF.

## Passo 1: Configura il progetto e importa i namespace

Prima di tutto, creiamo un progetto console e importiamo le classi di cui avremo bisogno.

```csharp
// Program.cs
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // The rest of the code lives here – see the following steps.
        }
    }
}
```

*Perché è importante:* `Document` e `DocumentBuilder` ci forniscono la tela, mentre `Shape` e `ShadowFormat` ci permettono di disegnare e stilizzare il rettangolo. Importarli in anticipo mantiene il codice successivo ordinato.

## Passo 2: **Crea forma rettangolare** con le dimensioni desiderate

Adesso creiamo effettivamente un documento vuoto e inseriamo un rettangolo. Nota come il metodo `InsertShape` restituisca un oggetto `Shape` che possiamo stilizzare immediatamente.

```csharp
// Inside Main()
Document document = new Document();               // blank Word document
DocumentBuilder builder = new DocumentBuilder(document);

// Insert a rectangle of 200x100 points (≈2.78" × 1.39")
Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
rectangle.FillColor = System.Drawing.Color.LightBlue;
```

*Spiegazione*: La dimensione è espressa in punti (1 pt = 1/72 in). Regola i numeri per adattarli al tuo layout. Assegniamo anche alla forma un riempimento azzurro chiaro per far risaltare l'ombra.

## Passo 3: **Aggiungi ombra alla forma** – perfeziona l'effetto

Un'ombra non è solo “acceso/spento”. Puoi controllare il suo colore, sfocatura, distanza, direzione e persino la trasparenza. Ecco una configurazione pratica che funziona bene per la maggior parte dei report.

```csharp
// Access the shape's shadow format
ShadowFormat shadow = rectangle.ShadowFormat;
shadow.Visible = true;                     // turn the shadow on
shadow.Color = System.Drawing.Color.Gray;  // shadow colour
shadow.BlurRadius = 5.0;                    // soft edges (higher = blurrier)
shadow.Distance = 4.0;                      // how far the shadow is from the shape
shadow.Direction = 45;                     // angle in degrees (45° = down‑right)
shadow.Transparency = 0.3;                  // 30 % transparent for a subtle look
```

*Perché potresti modificare questi valori:*  
- **BlurRadius** – aumentalo per un effetto sognante, diminuiscilo per un bordo nitido.  
- **Direction** – 0° punta a destra, 90° verso il basso, 180° a sinistra, ecc. Ruota per adattarlo al layout della pagina.  
- **Transparency** – impostalo a `0` per un'ombra solida, `0.5` per semi‑trasparente, ecc.

### Come aggiungere ombra – approcci alternativi

Se ti serve un **ombra a più livelli** (ad esempio, un'ombra esterna più scura più una interna più chiara), puoi creare una seconda forma, spostarla e impostare un `ShadowFormat` diverso. Oppure, per un aspetto rapido “senza sfocatura”, imposta `BlurRadius = 0`.

## Passo 4: **Salva documento come PDF** – l'esportazione finale

Con il rettangolo e la sua ombra pronti, l'ultimo passo è scrivere il file come PDF. Aspose.Words gestisce la conversione internamente; basta chiamare `Save` con il formato desiderato.

```csharp
// Define the output path – adjust to your environment
string outputPath = @"C:\Temp\ShadowRectangle.pdf";

// Save as PDF (the format is inferred from the extension)
document.Save(outputPath);
Console.WriteLine($"PDF saved to {outputPath}");
```

*Suggerimento*: Se devi controllare la conformità PDF (PDF/A, PDF/X) o incorporare i font, usa una overload:

```csharp
PdfSaveOptions options = new PdfSaveOptions
{
    Compliance = PdfCompliance.PdfA1b,
    EmbedFullFonts = true
};
document.Save(outputPath, options);
```

Ecco in breve la parte su **come salvare il PDF**.

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in `Program.cs`. Compila ed esegue così com'è (assicurati solo che la cartella di output esista).

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace RectangleShadowDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create a blank document and a builder
            Document document = new Document();
            DocumentBuilder builder = new DocumentBuilder(document);

            // 2️⃣ Insert a rectangle shape
            Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
            rectangle.FillColor = System.Drawing.Color.LightBlue;

            // 3️⃣ Add a shadow to the shape
            ShadowFormat shadow = rectangle.ShadowFormat;
            shadow.Visible = true;
            shadow.Color = System.Drawing.Color.Gray;
            shadow.BlurRadius = 5.0;
            shadow.Distance = 4.0;
            shadow.Direction = 45;
            shadow.Transparency = 0.3;

            // 4️⃣ Save the document as PDF
            string outputPath = @"C:\Temp\ShadowRectangle.pdf";
            document.Save(outputPath);
            Console.WriteLine($"PDF saved to {outputPath}");
        }
    }
}
```

### Risultato atteso

Apri il file `ShadowRectangle.pdf` generato. Vedrai una singola pagina con un rettangolo azzurro chiaro, un'ombra grigia morbida spostata di 45° in basso‑destra, e bordi puliti. Il PDF dovrebbe essere visualizzabile in qualsiasi lettore moderno (Adobe Acrobat, Edge, Chrome).

![Create rectangle shape with shadow in PDF](/images/shadow-rectangle.png "Create rectangle shape with shadow")

*(Il testo alternativo dell'immagine include la parola chiave principale per SEO.)*

## Domande comuni e gestione dei casi limite

**Cosa succede se l'ombra scompare nel PDF?**  
Assicurati di utilizzare una versione recente di Aspose.Words (≥23.3). Le versioni più vecchie presentavano un bug per cui alcune proprietà dell'ombra venivano ignorate durante la conversione in PDF.

**Posso cambiare il colore dell'ombra per adattarlo al mio brand?**  
Assolutamente—basta sostituire `System.Drawing.Color.Gray` con qualsiasi `Color` desideri, ad esempio `Color.FromArgb(128, 0, 0, 255)` per un blu semi‑trasparente.

**Come aggiungo un'ombra ad altre forme (ellisse, stella, ecc.)?**  
Lo stesso `ShadowFormat` funziona per qualsiasi oggetto `Shape`. Dopo aver creato la forma, accedi al suo `ShadowFormat` e imposta le proprietà.

**Cosa fare per problemi di DPI o scaling?**  
Il rendering PDF rispetta la dimensione in punti della forma. Se ti serve un output ad alta risoluzione (per la stampa), regola le dimensioni della forma di conseguenza o imposta `PdfSaveOptions.ImageResolution`.

**Posso esportare in altri formati, come PNG?**  
Sì—basta chiamare `document.Save("output.png", SaveFormat.Png)`. L'ombra verrà renderizzata allo stesso modo.

## Consigli professionali e best practice

- **Riutilizza il builder**: Se aggiungi più forme, mantieni una singola istanza di `DocumentBuilder`; è più economico che crearne molte.  
- **Salvataggio batch**: Quando generi molti PDF in un ciclo, riutilizza l'oggetto `PdfSaveOptions` per evitare allocazioni ripetute.  
- **Testing**: Apri sempre il PDF dopo il salvataggio per verificare che l'ombra appaia come previsto. Alcuni visualizzatori PDF renderizzano le ombre in modo leggermente diverso; Adobe Acrobat è il riferimento più affidabile.  
- **Performance**: Per documenti di grandi dimensioni, disabilita le interruzioni di pagina automatiche di `DocumentBuilder.InsertShape` impostando `builder.PageSetup.DifferentFirstPageHeaderFooter = false` se non ti servono.  

## Conclusione

Abbiamo coperto tutto ciò che ti serve per **creare una forma rettangolare**, **aggiungere un'ombra alla forma** e **salvare il documento come PDF** usando Aspose.Words per .NET. Il codice è compatto, i concetti sono spiegati, e ora hai una solida base per sperimentare con altre forme, stili di ombra e opzioni di esportazione.  

Prossimi passi? Prova a sostituire il rettangolo con un...

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}