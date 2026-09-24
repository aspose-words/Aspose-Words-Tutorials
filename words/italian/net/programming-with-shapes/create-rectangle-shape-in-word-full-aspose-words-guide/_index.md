---
category: general
date: 2026-02-26
description: Crea una forma rettangolare in Word con Aspose.Words e scopri come aggiungere
  la forma a Word, applicare l'ombra e impostare la trasparenza della forma in pochi
  minuti.
draft: false
keywords:
- create rectangle shape
- add shape to word
- apply shadow to shape
- set shape transparency
- rectangle with shadow
language: it
og_description: Crea una forma rettangolare in Word usando Aspose.Words. Impara ad
  aggiungere una forma a Word, applicare un'ombra alla forma e impostare rapidamente
  la trasparenza della forma.
og_title: Crea forma rettangolare in Word – Guida completa ad Aspose.Words
tags:
- Aspose.Words
- C#
- Word Automation
title: Crea forma rettangolare in Word – Guida completa a Aspose.Words
url: /it/net/programming-with-shapes/create-rectangle-shape-in-word-full-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una Forma Rettangolare in Word – Guida Completa ad Aspose.Words

Ti è mai capitato di dover **creare una forma rettangolare** in un documento Word senza sapere da dove cominciare? Non sei solo: molti sviluppatori si trovano di fronte a questo ostacolo quando automatizzano report o fatture. In questo tutorial percorreremo insieme un esempio completo, pronto all'uso, che mostra come **aggiungere una forma a Word**, applicare un'ombra delicata e controllare la trasparenza della forma, il tutto con Aspose.Words per .NET.

Al termine della guida avrai un file `.docx` contenente un rettangolo pulito con un'ombra curata—perfetto per branding, call‑out o semplicemente per rendere il documento un po' più professionale. Nessun tool esterno necessario, solo poche righe di C#.

## Cosa Ti Serve

- **Aspose.Words per .NET** (l'ultima versione disponibile all'inizio del 2026). Puoi ottenerla da NuGet (`Install-Package Aspose.Words`).
- Un ambiente di sviluppo .NET (Visual Studio, Rider o VS Code con l'estensione C#).
- Familiarità di base con la sintassi C#—nulla di complicato, solo le consuete istruzioni `using` e la creazione di oggetti.

Se hai già tutto questo, ottimo—iniziamo.

## Crea una Forma Rettangolare – Passaggi Principali

Di seguito trovi il codice sorgente completo. Copialo in un nuovo progetto console, premi **F5** e vedrai apparire `ShadowDemo.docx` nella cartella che specifichi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;   // Needed for Color

// Step 1: Create a new blank document.
Document document = new Document();

// Step 2: Insert a rectangle shape and define its size.
Shape rectangleShape = new Shape(document, ShapeType.Rectangle)
{
    Width  = 200,   // Width in points (≈2.78 inches)
    Height = 100    // Height in points (≈1.39 inches)
};

// Step 3: Apply a shadow with fine‑grained control over its appearance.
rectangleShape.Shadow = new Shadow
{
    BlurRadius   = 5.0,                     // Softness of the shadow edge
    Distance     = 4.0,                     // How far the shadow is offset
    Direction    = 45,                      // Angle of the offset (degrees)
    Color        = Color.Gray,              // Shadow colour
    Transparency = 0.2,                     // Opacity (0 = opaque, 1 = fully transparent)
    Spread       = 0.3                      // Size of the shadow spread
};

// Step 4: Add the shape to the first paragraph of the document.
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);

// Step 5: Save the document with the shadowed shape.
document.Save("ShadowDemo.docx");
```

### Perché Funziona

- **`Document`** è il punto di ingresso; rappresenta l'intero file Word.
- **`Shape`** con `ShapeType.Rectangle` indica ad Aspose che vogliamo un oggetto di disegno rettangolare.
- Impostare **`Width`** e **`Height`** assegna alla forma una dimensione deterministica; altrimenti usa un segnaposto molto piccolo.
- L'oggetto **`Shadow`** consente di regolare ogni aspetto visivo: sfocatura, distanza, direzione, colore, trasparenza e diffusione. È il cuore di *apply shadow to shape*.
- Infine, **`AppendChild`** inserisce la forma nel primo paragrafo del documento, il modo più semplice per *add shape to Word* senza dover gestire tabelle o intestazioni.

Quando apri `ShadowDemo.docx`, vedrai un rettangolo grigio posizionato comodamente nel documento, con un'ombra inclinata verso il basso‑destra a 45°. L'ombra non è un blocco solido; il raggio di sfocatura ammorbidisce i bordi e la trasparenza la fa apparire come un'ombra naturale piuttosto che un overlay duro.

![crea forma rettangolare esempio](image.png "crea forma rettangolare con ombra in Word usando Aspose.Words")

*(L'immagine sopra mostra il risultato finale dello snippet di codice.)*

## Aggiungi una Forma a un Documento Word – Opzioni di Posizionamento

L'esempio utilizza il **primo paragrafo** perché è il modo più rapido per vedere qualcosa a schermo. In scenari reali potresti voler:

- Inserire la forma in una **sezione** o in un **header/footer** specifici.
- Posizionarla all'interno di una **cella di tabella** per allinearla a dati tabulari.
- Avvolgerla con opzioni di **text wrapping** (ad es., `WrapType.Square`) così che il testo circostante fluisca attorno al rettangolo.

Ecco una variazione rapida che mette la forma in un nuovo paragrafo con uno stile personalizzato:

```csharp
Paragraph para = new Paragraph(document);
para.ParagraphFormat.StyleIdentifier = StyleIdentifier.Heading2;
para.AppendChild(rectangleShape);
document.FirstSection.Body.AppendChild(para);
```

*Consiglio professionale:* Aggiungi sempre la forma **dopo** aver configurato le sue proprietà; altrimenti potresti dover chiamare `UpdateLayout` per aggiornare l'aspetto visivo.

## Applica Ombra alla Forma – Rifinire l'Aspetto

Le ombre possono cambiare drasticamente l'estetica di un documento. La classe `Shadow` espone diverse proprietà:

| Property      | Cosa Controlla                                      | Valori Tipici |
|---------------|-----------------------------------------------------|---------------|
| `BlurRadius`  | Morbidezza dei bordi dell'ombra                     | 2.0 – 10.0    |
| `Distance`    | Distanza dell'ombra dalla forma                     | 1.0 – 8.0     |
| `Direction`   | Angolo in gradi (0 = sinistra, 90 = in alto)       | 0 – 360       |
| `Color`       | Colore dell'ombra (qualsiasi `System.Drawing.Color`) | Gray, Black, Custom |
| `Transparency`| Opacità (0 = completamente opaco, 1 = invisibile)  | 0.0 – 0.5     |
| `Spread`      | Espansione dell'ombra prima dell'applicazione della sfocatura | 0.0 – 1.0 |

Se desideri un **aspetto sottile e professionale**, mantieni `BlurRadius` intorno a 4‑6 e `Transparency` vicino a 0.2, proprio come nel codice sopra. Per un **effetto drammatico**, aumenta `Distance` a 6, imposta `Direction` a 135° e riduci `Transparency` a 0.05.

## Imposta Trasparenza della Forma e Diffusione dell'Ombra

La trasparenza non riguarda solo l'ombra; puoi anche rendere il rettangolo stesso parzialmente trasparente:

```csharp
rectangleShape.FillColor = Color.LightBlue;
rectangleShape.Transparency = 0.3; // 30% transparent fill
```

Combinare un riempimento semi‑trasparente con un'ombra morbida genera spesso una sensazione di UI moderna—ideale per dashboard o mock‑up di design inseriti nei report.

### Casi Limite da Tenere d'Occhio

1. **Versioni Word più vecchie** (pre‑2007) non supportano alcune proprietà dell'ombra. Se punti a file `.doc`, considera di semplificare l'ombra (ad es., impostare `BlurRadius` a 0).
2. **Display ad alta DPI** potrebbero renderizzare l'ombra in modo leggermente diverso. Testa nell'ambiente di destinazione se la fedeltà visiva è critica.
3. **Forme sovrapposte**—Aspose rende le ombre nell'ordine in cui vengono aggiunte. Inserisci le forme dal retro al davanti per evitare occlusioni indesiderate.

## Salva e Verifica il Risultato

Il metodo `Document.Save` rileva automaticamente il formato di output dall'estensione del file. Per un file **`.docx`** ottieni il formato Open XML, compreso dalla maggior parte dei moderni editor Word. Se ti serve una versione **PDF** con lo stesso stile visivo, basta cambiare l'estensione:

```csharp
document.Save("ShadowDemo.pdf");
```

Aprendo il `ShadowDemo.docx` (o `ShadowDemo.pdf`) dovresti vedere un **rettangolo con ombra** pulito, confermando che hai creato correttamente *create rectangle shape* e *apply shadow to shape* usando Aspose.Words.

## Domande Frequenti

**D: Posso usare una forma diversa, come un'ellisse?**  
R: Assolutamente. Sostituisci `ShapeType.Rectangle` con `ShapeType.Ellipse` (o qualsiasi altro valore dell'enum `ShapeType`). Le proprietà dell'ombra rimangono invariate.

**D: E se voglio che il rettangolo sia cliccabile?**  
R: Puoi assegnare un hyperlink alla forma:

```csharp
rectangleShape.Href = "https://example.com";
```

**D: Funziona su .NET 6+?**  
R: Sì. Aspose.Words 23.11 e successive supportano pienamente .NET 6, .NET 7 e .NET 8. Basta referenziare il pacchetto NuGet appropriato.

**D: Come cambio il colore dell'ombra per allinearlo al mio brand?**  
R: Usa qualsiasi `System.Drawing.Color` desideri:

```csharp
rectangleShape.Shadow.Color = Color.FromArgb(255, 30, 144, 255); // DodgerBlue
```

## Conclusione

Abbiamo coperto tutto ciò che ti serve per **creare una forma rettangolare** in un documento Word, **aggiungere la forma a Word**, **applicare un'ombra alla forma** e **impostare la trasparenza della forma**. Il codice completo, eseguibile, si trova all'inizio di questa pagina, e le spiegazioni dovrebbero darti la sicurezza necessaria per modificare dimensioni, colori e parametri dell'ombra per qualsiasi progetto.

Pronto per il passo successivo? Prova a sperimentare con:

- Molteplici forme sovrapposte per un effetto badge.
- Dimensionamento dinamico basato sul contenuto del documento (ad es., calcolare la larghezza da una colonna di tabella).
- Esportare il documento in PDF o HTML mantenendo l'ombra.

Sentiti libero di lasciare un commento se incontri difficoltà, o di condividere le tue varianti sul tema “rettangolo con ombra”.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}