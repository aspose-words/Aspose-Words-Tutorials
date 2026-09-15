---
category: general
date: 2026-01-13
description: Crea un documento Word usando Aspose.Words e impara come inserire una
  forma rettangolare, come aggiungere l'ombra e come aggiungere l'ombra alla forma
  in C#. Esempio completo incluso.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- add shape shadow
language: it
og_description: Crea un documento Word con Aspose.Words, scopri come inserire una
  forma rettangolare e come aggiungere l'ombra. Segui l'esempio completo in C#.
og_title: Crea documento Word con un rettangolo ombreggiato – tutorial completo
tags:
- Aspose.Words
- C#
- Document Automation
title: Crea documento Word con un rettangolo ombreggiato – Guida passo passo
url: /it/net/programming-with-shapes/create-word-document-with-a-shadowed-rectangle-step-by-step/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word con un rettangolo ombreggiato – Guida passo‑passo

Hai mai dovuto **creare un documento Word** che contenesse un rettangolo ben ombreggiato, ma non sapevi da dove cominciare? Non sei l’unico: molti sviluppatori si trovano nella stessa situazione quando si avvicinano per la prima volta ad Aspose.Words.  

In questo tutorial vedremo tutto ciò che ti serve per **creare un documento Word** programmaticamente, **inserire una forma rettangolare** e mostrare **come aggiungere l’ombra** affinché la forma risalti davvero. Alla fine avrai a disposizione uno snippet C# pronto da inserire in qualsiasi progetto .NET.

## Cosa imparerai

- Il codice esatto per **come inserire una forma** (un rettangolo) in un file Word.  
- Le proprietà da modificare per **aggiungere l’ombra alla forma** e controllarne l’aspetto.  
- Come salvare il risultato e verificare che l’ombra sia visibile.  
- Alcuni consigli pratici e note su casi limite che ti faranno risparmiare mal di testa in seguito.

Nessuna documentazione esterna necessaria—tutto è qui.

## Prerequisiti

Prima di iniziare, assicurati di avere:

1. **.NET 6.0** (o qualsiasi versione recente di .NET) installato.  
2. Una **licenza** per Aspose.Words for .NET, oppure puoi usare la modalità di valutazione gratuita per i test.  
3. Un ambiente di sviluppo—Visual Studio 2022 funziona benissimo, ma qualsiasi editor in grado di compilare C# è sufficiente.

Questo è tutto. Non servono pacchetti NuGet aggiuntivi oltre a `Aspose.Words`.

## Passo 1 – Configura il progetto e aggiungi il riferimento ad Aspose.Words

Per prima cosa, crea una nuova console app e aggiungi il pacchetto Aspose.Words:

```bash
dotnet new console -n ShadowRectangleDemo
cd ShadowRectangleDemo
dotnet add package Aspose.Words
```

> **Suggerimento:** Se usi la versione di prova gratuita, ricorda di chiamare `License.SetLicense` con il tuo file di licenza; altrimenti la libreria aggiungerà una filigrana.

## Passo 2 – Inizializza il Document Builder

Ora iniziamo il vero processo di **creare un documento Word**. La classe `Document` ci fornisce una tela vuota, e `DocumentBuilder` ci permette di dipingere su di essa.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing; // For Color

// Initialise a new blank document
Document document = new Document();

// Initialise a builder to start adding content
DocumentBuilder builder = new DocumentBuilder(document);
```

Perché abbiamo bisogno di un builder? Astrae i dettagli a basso livello di OpenXML, così puoi concentrarti su *cosa* vuoi piuttosto che su *come* il file è strutturato. Questo è il cuore di **come inserire una forma** rapidamente.

## Passo 3 – Inserisci la forma rettangolare

Ecco dove **inseriamo la forma rettangolare**. Il rettangolo sarà di 150 × 100 punti (circa 2 pollici × 1,3 pollici).

```csharp
// Insert a rectangle shape at the current cursor position
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);
```

Il metodo `InsertShape` restituisce un oggetto `Shape`, che possiamo personalizzare ulteriormente. A questo punto, il rettangolo è solo una scatola bianca solida—senza ombra.

## Passo 4 – Come aggiungere l’ombra (Add Shape Shadow)

Aggiungere un’ombra è sorprendentemente semplice una volta saputi quali proprietà modificare. L’oggetto `ShadowFormat` controlla visibilità, colore, sfocatura, offset e dimensione.

```csharp
// Make the shadow visible
rectangleShape.ShadowFormat.Visible = true;

// Choose a subtle gray tone
rectangleShape.ShadowFormat.Color = Color.Gray;

// Set 30 % transparency – the shadow will be faint but noticeable
rectangleShape.ShadowFormat.Transparency = 0.3;

// Offset the shadow 5 points right and 5 points down
rectangleShape.ShadowFormat.OffsetX = 5;
rectangleShape.ShadowFormat.OffsetY = 5;

// Soften the edges with a blur radius of 4 points
rectangleShape.ShadowFormat.BlurRadius = 4;

// Scale the shadow to 75 % of the shape size (percentage)
rectangleShape.ShadowFormat.Size = 75;
```

Questo blocco risponde a **come aggiungere l’ombra** in termini semplici: attivalo, scegli un colore, regola la trasparenza, l’offset, la sfocatura e la dimensione. Puoi sperimentare con questi valori per ottenere un’ombra pesante o una più leggera.

### Varianti comuni

- **Colori diversi:** Usa `Color.Black` per un’ombra classica, o `Color.BlueViolet` per un effetto stilizzato.  
- **Nessuna sfocatura:** Imposta `BlurRadius = 0` per un bordo nitido.  
- **Offset più grandi:** Aumenta `OffsetX`/`OffsetY` per spostare l’ombra più lontano dalla forma.

## Passo 5 – Salva il documento e verifica

Infine, scrivi il documento su disco. Il file sarà un normale `.docx` apribile da qualsiasi elaboratore di testi moderno.

```csharp
// Save the document to the desired folder
string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
document.Save(outputPath);

Console.WriteLine($"Document saved to {outputPath}");
```

Apri il risultato *ShadowRectangle.docx* in Microsoft Word. Dovresti vedere un rettangolo con un’ombra grigia soffusa spostata verso il basso‑destra—esattamente come specificato dal codice.

> **Output atteso:** Un file Word di una sola pagina contenente un rettangolo di 150 × 100 punti con un’ombra grigia al 30 % di trasparenza, offset di 5 pt, sfocatura di 4 pt e dimensione al 75 % della forma.

## Esempio completo funzionante

Mettendo tutto insieme, ecco il programma completo, pronto da eseguire:

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Initialise a new blank document
        Document document = new Document();

        // 2️⃣ Create a DocumentBuilder to add content
        DocumentBuilder builder = new DocumentBuilder(document);

        // 3️⃣ Insert a rectangle shape (150 × 100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 150, 100);

        // 4️⃣ How to add shadow – configure the ShadowFormat
        rectangleShape.ShadowFormat.Visible = true;
        rectangleShape.ShadowFormat.Color = Color.Gray;
        rectangleShape.ShadowFormat.Transparency = 0.3; // 30 % transparent
        rectangleShape.ShadowFormat.OffsetX = 5;        // horizontal offset
        rectangleShape.ShadowFormat.OffsetY = 5;        // vertical offset
        rectangleShape.ShadowFormat.BlurRadius = 4;    // softer edge
        rectangleShape.ShadowFormat.Size = 75;         // size as a percentage

        // 5️⃣ Save the document
        string outputPath = Path.Combine(Environment.CurrentDirectory, "ShadowRectangle.docx");
        document.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Esegui il programma (`dotnet run`) e otterrai un nuovo file Word con un rettangolo elegantemente ombreggiato—perfetto per report, certificati o qualsiasi indicatore visivo di cui hai bisogno.

## Domande frequenti (FAQ)

**D: Posso inserire altre forme (ellisse, stella) e usare lo stesso codice per l’ombra?**  
R: Assolutamente. Il metodo `InsertShape` accetta qualsiasi valore dell’enum `ShapeType`. Una volta ottenuta l’istanza `Shape`, le proprietà di `ShadowFormat` funzionano allo stesso modo, quindi **come aggiungere l’ombra** è indipendente dalla forma.

**D: E se volessi l’ombra su entrambi i lati della forma?**  
R: Aspose.Words supporta una sola ombra per forma. Per simulare un effetto a doppio lato, duplica la forma, sposta ciascuna copia diversamente e imposta `ShadowFormat.Visible` a `false` per una mentre mantieni l’ombra visibile per l’altra.

**D: Funziona su .NET Framework 4.8?**  
R: Sì. L’API è indipendente dalla versione; basta referenziare il DLL Aspose.Words appropriato per il tuo framework di destinazione.

## Consigli e trappole

- **Non dimenticare di impostare `Visible = true`**—altrimenti le proprietà dell’ombra vengono ignorate.  
- **I valori di trasparenza vanno da 0.0 (opaco) a 1.0 (completamente trasparente).** Un errore comune è usare `30` invece di `0.3`.  
- **Salvare in una cartella di sola lettura genera un’eccezione.** Assicurati che la directory di output sia scrivibile.

## Prossimi passi

Ora che sai **come inserire una forma**, **aggiungere l’ombra alla forma** e **creare un documento Word** con Aspose.Words, potresti voler approfondire:

- Aggiungere **testo all’interno del rettangolo** usando `builder.InsertParagraph()` prima di inserire la forma.  
- Applicare **riempimenti a gradiente** o **bordi a trama** per uno stile visivo più ricco.  
- Automatizzare la generazione di più pagine, ognuna con una forma ombreggiata diversa, per creare report dinamici.

Sperimenta liberamente—cambiare colore, sfocatura o dimensione dell’ombra può trasformare radicalmente l’aspetto del tuo documento.

---

*Pronto a mettere tutto in produzione? Prendi il codice, modifica i parametri e guarda i tuoi file Word guadagnare una finitura professionale in pochi secondi.*

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}