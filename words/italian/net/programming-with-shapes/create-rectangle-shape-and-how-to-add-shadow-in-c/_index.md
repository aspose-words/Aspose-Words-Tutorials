---
category: general
date: 2026-04-04
description: Crea una forma rettangolare in C# con Aspose.Words e impara come aggiungere
  un'ombra, applicare sfocatura all'ombra e rendere l'ombra trasparente – guida passo
  passo.
draft: false
keywords:
- create rectangle shape
- how to add shadow
- how to create document
- apply blur to shadow
- make shadow transparent
language: it
og_description: Crea una forma rettangolare in C# con Aspose.Words. Scopri come aggiungere
  un'ombra, applicare la sfocatura all'ombra e rendere l'ombra trasparente in un tutorial
  conciso.
og_title: Crea forma rettangolare e come aggiungere l'ombra in C#
tags:
- Aspose.Words
- C#
- Document Automation
title: Crea forma rettangolare e come aggiungere l'ombra in C#
url: /it/net/programming-with-shapes/create-rectangle-shape-and-how-to-add-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea forma rettangolare e come aggiungere l'ombra in C#

Ti è mai capitato di dover **creare una forma rettangolare** in un documento Word ma non sapevi come darle un'ombra leggera? Non sei l'unico. In molti scenari di reporting o branding un semplice rettangolo con un'ombra soffusa e semi‑trasparente può rendere il layout più curato senza molto sforzo.

In questo tutorial vedremo **come creare un documento** usando Aspose.Words, poi mostreremo **come aggiungere l'ombra**, **applicare il blur all'ombra** e persino **rendere l'ombra trasparente**. Alla fine avrai uno snippet C# pronto da eseguire che produce un file *.docx* con un rettangolo elegantemente ombreggiato—tutto in pochi minuti.

## Cosa ti serve

- .NET 6 o successivo (l'API funziona anche con .NET Framework 4.6+)
- Aspose.Words per .NET (la versione di prova gratuita è sufficiente per questo esempio)
- Un editor di codice – Visual Studio, VS Code, Rider, o quello che preferisci
- Conoscenze di base di C# – niente di complicato, solo la capacità di eseguire un'app console

Se hai tutto questo, possiamo passare subito alla soluzione.

## Passo 1 – Come creare il documento e inizializzare la tela

Prima di tutto: ti serve un oggetto `Document` vuoto. Pensalo come un foglio di carta bianco che Aspose.Words trasformerà in un file Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // For Color

// Create a new blank document
Document doc = new Document();
```

Perché istanziamo `Document` invece di caricare un modello? Partire da zero garantisce che nessuno stile o sezione nascosta interferisca con il nostro rettangolo. Inoltre mantiene le dimensioni del file ridotte – una buona abitudine quando si generano molti documenti in un ciclo.

## Passo 2 – Crea forma rettangolare (il nucleo della nostra parola chiave principale)

Ora **creiamo la forma rettangolare**. La classe `Shape` è flessibile; le indichi il tipo (Rectangle), le dimensioni e come deve avvolgere il testo circostante.

```csharp
// Define a rectangular shape
Shape rect = new Shape(doc, ShapeType.Rectangle)
{
    Width = 200,               // Width in points (≈2.8 inches)
    Height = 100,              // Height in points (≈1.4 inches)
    WrapType = WrapType.Inline // Makes the shape behave like a character
};
```

Nota l'uso della sintassi di inizializzatore di oggetti – è concisa e riduce la possibilità di dimenticare di impostare una proprietà in seguito. Il rettangolo verrà inserito all'interno del primo paragrafo, che aggiungeremo nel passo successivo.

## Passo 3 – Come aggiungere l'ombra e personalizzarne l'aspetto

Aggiungere un'ombra non è solo una riga di codice; hai diverse proprietà da regolare. È qui che entrano in gioco le parole chiave secondarie **applicare blur all'ombra** e **rendere l'ombra trasparente**.

```csharp
// Configure the shadow
rect.Shadow.Format.Color = Color.DarkGray;   // Shadow colour
rect.Shadow.Format.BlurRadius = 5.0;         // Apply blur to shadow (points)
rect.Shadow.Format.OffsetX = 3;              // Horizontal offset
rect.Shadow.Format.OffsetY = 3;              // Vertical offset
rect.Shadow.Format.Transparency = 0.3;       // 30 % transparent (make shadow transparent)
```

Una rapida nota sui numeri: `BlurRadius` pari a 5 fornisce una sfumatura delicata; aumentalo a 10 per un effetto più morbido, o riducilo a 2 per un bordo più netto. Il valore di `Transparency` varia da 0 (opaco) a 1 (invisibile). Regola in base ai requisiti di contrasto del tuo brand.

### Consiglio professionale

Se ti serve un'ombra colorata (ad esempio un blu aziendale), sostituisci semplicemente `Color.DarkGray` con `Color.FromArgb(80, 0, 120, 215)`. Il primo argomento è il canale alfa – mantienilo basso per una maggiore sobrietà.

## Passo 4 – Inserisci la forma nel documento

Con il rettangolo e la sua ombra pronti, lo inseriamo nel primo paragrafo del documento. Questo passaggio garantisce che la forma appaia in cima al file.

```csharp
// Append the shape to the first paragraph of the first section
doc.FirstSection.Body.FirstParagraph.AppendChild(rect);
```

Perché il primo paragrafo? È un valore predefinito sicuro che funziona anche quando il documento è completamente vuoto. Se hai una posizione specifica (ad esempio dopo un'intestazione), dovrai individuare quel nodo e inserire la forma lì.

## Passo 5 – Salva il file e verifica il risultato

Infine, persisti il documento su disco. Puoi scegliere qualsiasi percorso ti piaccia; assicurati solo che la cartella esista.

```csharp
// Save the document
doc.Save(@"C:\Temp\ShadowRectangle.docx");
```

Quando apri *ShadowRectangle.docx* in Microsoft Word, dovresti vedere un rettangolo di 200 × 100 punti con un'ombra grigio scuro, leggermente sfocata, al 30 % di trasparenza e spostata di tre punti verso destra e verso il basso. L'effetto è sottile ma aggiunge profondità a layout altrimenti piatti.

![crea forma rettangolare con ombra in Aspose.Words](https://example.com/placeholder-image.png "crea forma rettangolare con ombra in Aspose.Words")

*Testo alternativo immagine:* **crea forma rettangolare con ombra in Aspose.Words** – l'immagine mostra il documento finale con il rettangolo ombreggiato.

## Variazioni comuni e casi limite

### Cambiare dinamicamente il colore dell'ombra

Se la tua applicazione supporta temi, potresti prelevare il colore dell'ombra da un file di configurazione:

```csharp
Color themeShadow = ColorTranslator.FromHtml(ConfigurationManager.AppSettings["ShadowColor"]);
rect.Shadow.Format.Color = themeShadow;
```

### Rendere la forma non inline

A volte vuoi che il rettangolo fluttui sopra il testo. Cambia `WrapType` in `WrapType.Square` e imposta `RelativeHorizontalPosition` su `RelativeHorizontalPosition.Margin` per avere più controllo.

```csharp
rect.WrapType = WrapType.Square;
rect.RelativeHorizontalPosition = RelativeHorizontalPosition.Margin;
rect.Left = 72; // 1 inch from the left margin
```

### Gestire più pagine

Se ti serve un rettangolo su ogni pagina, cicla attraverso `doc.Sections` e aggiungi una forma clonata al primo paragrafo di ciascuna sezione. Ricorda di chiamare `rect.Clone(true)` per duplicare anche le impostazioni dell'ombra.

## Riepilogo – Cosa abbiamo realizzato

- **Creato forma rettangolare** usando Aspose.Words
- **Come aggiungere l'ombra** con colore, offset, blur e trasparenza
- Dimostrato **applicare blur all'ombra** e **rendere l'ombra trasparente**
- Salvato un file Word apribile immediatamente

Tutto questo è stato ottenuto con poche righe di codice, dimostrando che modifiche visive sofisticate non richiedono sempre librerie grafiche pesanti.

## Cosa fare dopo?

- Sperimenta con altri `ShapeType` (Ellipse, Cloud, ecc.) e osserva come si comportano le ombre.
- Combina il rettangolo con caselle di testo per creare call‑out etichettati.
- Approfondisci **come creare documenti** modello che contengono già segnaposto per le forme, poi popolali programmaticamente.

Sentiti libero di modificare il raggio del blur, il colore o la trasparenza finché l'ombra non appare perfetta per il tuo linguaggio di design. L'API è indulgente e le modifiche sono visibili subito quando riesegui l'app console.

Buona programmazione, e che i tuoi documenti abbiano sempre quel tocco extra di profondità!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}