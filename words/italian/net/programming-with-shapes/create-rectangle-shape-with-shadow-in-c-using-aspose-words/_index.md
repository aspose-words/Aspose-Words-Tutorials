---
category: general
date: 2026-03-22
description: Crea una forma rettangolare in C# e aggiungi un'ombra alla forma con
  Aspose.Words. Scopri come aggiungere l'ombra, come creare un rettangolo e come impostare
  le proprietà dell'ombra.
draft: false
keywords:
- create rectangle shape
- add shadow to shape
- how to add shadow
- how to create rectangle
- how to set shadow
language: it
og_description: Crea una forma rettangolare in C# e aggiungi un'ombra alla forma usando
  Aspose.Words. Guida passo‑passo che copre come aggiungere l'ombra, come creare il
  rettangolo e come impostare l'ombra.
og_title: Crea una forma rettangolare con ombra in C# – Guida completa
tags:
- Aspose.Words
- C#
- Document Automation
title: Crea una forma rettangolare con ombra in C# usando Aspose.Words
url: /it/net/programming-with-shapes/create-rectangle-shape-with-shadow-in-c-using-aspose-words/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea una forma rettangolare con ombra in C# usando Aspose.Words

Ti è mai capitato di dover **create rectangle shape** in un documento Word ma non sapevi come dargli una leggera ombra? Non sei solo—molti sviluppatori incontrano questo ostacolo quando si avvicinano per la prima volta all'automazione dei documenti. In questa guida ti mostreremo passo passo come **add shadow to shape** usando Aspose.Words, e risponderemo anche a “**how to add shadow**”, “**how to create rectangle**” e “**how to set shadow**” lungo il percorso.

Inizieremo con un `Document` vuoto, disegneremo un rettangolo, attiveremo la sua ombra, regoleremo sfocatura, distanza, angolo e colore, e infine salveremo il file. Alla fine avrai un `.docx` pronto all'uso che mostra un rettangolo di tono grigio che fluttua appena sopra la pagina. Nessun mistero, solo codice semplice da copiare‑incollare in qualsiasi progetto .NET.

## Prerequisiti

* **Aspose.Words for .NET** (l'ultima versione a marzo 2026). Puoi ottenerlo da NuGet con `Install-Package Aspose.Words`.
* Un ambiente di sviluppo .NET – Visual Studio, Rider, o anche VS Code con l'estensione C# funziona bene.
* Conoscenze di base di C# – niente di complicato, solo la capacità di creare un'app console o WinForms.

È tutto. Nessuna libreria aggiuntiva, nessun passaggio nascosto. Pronto? Iniziamo.

## Passo 1: Inizializza un nuovo documento vuoto

Per **create rectangle shape**, abbiamo prima bisogno di un contenitore – un oggetto `Document` – che rappresenta il file Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new empty document
Document document = new Document();
```

La classe `Document` è il punto di ingresso per tutto ciò che fa Aspose.Words. Pensala come una tela vuota; senza di essa non puoi aggiungere forme, tabelle o testo.

## Passo 2: Crea il rettangolo che conterrà l'ombra

Ora mostreremo **how to create rectangle** istanziando un `Shape` di tipo `Rectangle`. Impostiamo anche le sue dimensioni in punti (1 punto ≈ 1/72 di pollice).

```csharp
// Step 2: Create a rectangular shape that will hold the shadow
Shape rectangleShape = new Shape(document, ShapeType.Rectangle);
rectangleShape.Width  = 200; // width in points
rectangleShape.Height = 100; // height in points
```

Perché scegliere 200 × 100 punti? È una dimensione adeguata per una demo – abbastanza grande da vedere chiaramente l'ombra, ma non così enorme da sovraccaricare la pagina. Sentiti libero di modificare questi valori per adattarli al tuo layout.

## Passo 3: Abilita l'effetto ombra e configura il suo aspetto

Ecco il cuore del tutorial: **how to add shadow** e **how to set shadow** proprietà. Aspose.Words espone un oggetto `Shadow` su ogni forma, permettendoti di attivare l'effetto e regolare i parametri visivi.

```csharp
// Step 3: Enable the shadow effect and configure its appearance
rectangleShape.Shadow.Enabled    = true;                     // turn the shadow on
rectangleShape.Shadow.BlurRadius = 5;                       // blur radius in pixels
rectangleShape.Shadow.Distance   = 8;                       // distance from the shape in pixels
rectangleShape.Shadow.Angle      = 45;                      // direction of the light source (degrees)
rectangleShape.Shadow.Color      = System.Drawing.Color.Gray; // shadow color
```

* **BlurRadius** ammorbidisce i bordi – un valore più alto rende l'ombra più diffusa.
* **Distance** spinge l'ombra più lontano dal rettangolo.
* **Angle** determina da dove sembra provenire la luce; 45° fornisce un aspetto diagonale e naturale.
* **Color** ti consente di scegliere qualsiasi `System.Drawing.Color`. Il grigio è un valore predefinito sicuro, ma puoi optare per il coraggioso `Color.Black` o il delicato `Color.LightGray`.

Consiglio: se imposti `Enabled = false`, tutte le altre impostazioni dell'ombra vengono ignorate, quindi controlla sempre quel flag.

## Passo 4: Inserisci la forma nel corpo del documento

Con il rettangolo pronto e la sua ombra configurata, dobbiamo inserirlo nel documento. Il modo più semplice è aggiungerlo al primo paragrafo della prima sezione.

```csharp
// Step 4: Insert the shape into the first paragraph of the document body
document.FirstSection.Body.FirstParagraph.AppendChild(rectangleShape);
```

Se il tuo documento contiene già del testo, potresti individuare un `Paragraph` specifico o anche una cella di `Table` e inserire la forma lì. Il metodo `AppendChild` è versatile – funziona con qualsiasi tipo di `Node`.

## Passo 5: Salva il documento e verifica il risultato

Infine, scriviamo il file su disco. Cambia il percorso dove preferisci; la cartella deve esistere, altrimenti otterrai un'eccezione.

```csharp
// Step 5: Save the document with the shadowed shape
document.Save(@"C:\Temp\ShadowedRectangle.docx");
```

Apri il risultato `ShadowedRectangle.docx` in Microsoft Word (o LibreOffice) e dovresti vedere un rettangolo grigio con un'ombra nitida e diagonale che si sposta verso il basso a destra. Se l'ombra sembra troppo tenue, aumenta `BlurRadius` o `Distance` e riesegui il codice – sperimentare è parte del divertimento.

![Create rectangle shape with shadow example](rectangle-shadow.png){alt="Esempio di forma rettangolare con ombra"}

### Output previsto

* Un documento Word a pagina singola.
* Un rettangolo grigio di 200 × 100 punti posizionato in alto a sinistra della pagina.
* Un'ombra grigia delicata spostata di 8 pixel a un angolo di 45°, sfocata di 5 pixel.

## Come aggiungere ombra a una forma – approfondimento

Potresti chiederti, *“Posso animare l'ombra o farla cambiare in base all'input dell'utente?”* Sebbene Aspose.Words non supporti l'animazione, puoi regolare programmaticamente le proprietà dell'ombra prima di salvare, creando efficacemente più versioni dello stesso documento con aspetti diversi. Ad esempio, iterando su una collezione di colori:

```csharp
Color[] shadowColors = { Color.Gray, Color.Black, Color.DarkSlateGray };
foreach (var col in shadowColors)
{
    rectangleShape.Shadow.Color = col;
    document.Save($@"C:\Temp\Shadow_{col.Name}.docx");
}
```

Questa piccola porzione dimostra **how to set shadow** in modo dinamico—ottimo per generare report tematici.

## Come creare un rettangolo – forme alternative

Se ti serve un rettangolo arrotondato, basta cambiare il `ShapeType`:

```csharp
Shape rounded = new Shape(document, ShapeType.RoundRectangle);
rounded.Width  = 200;
rounded.Height = 100;
rounded.Shadow.Enabled = true; // shadow works the same way
```

Oppure, per un quadrato perfetto, imposta `Width` uguale a `Height`. Le stesse proprietà dell'ombra si applicano, quindi sei già coperto su **how to add shadow** per qualsiasi forma tu scelga.

## Problemi comuni e risoluzione

| Sintomo | Probabile causa | Correzione |
|---------|----------------|------------|
| L'ombra non appare | `Shadow.Enabled` lasciato a `false` | Imposta `rectangleShape.Shadow.Enabled = true;` |
| L'ombra sembra troppo netta | `BlurRadius` impostato a 0 | Aumenta `BlurRadius` ad almeno 3 |
| Il documento genera `FileNotFoundException` durante il salvataggio | La cartella di destinazione non esiste | Crea prima la cartella o usa un percorso valido |
| La forma è invisibile | Larghezza/Altezza impostate a 0 | Assicurati che entrambe le dimensioni siano > 0 |

Tenere d'occhio questi problemi ti salva dal classico momento “perché la mia forma non viene visualizzata?”.

## Riepilogo – cosa abbiamo realizzato

* **Create rectangle shape** in un nuovo documento Word usando Aspose.Words.  
* **Add shadow to shape** attivando il flag `Shadow.Enabled` e regolando sfocatura, distanza, angolo e colore.  
* Dimostrato **how to add shadow**, **how to create rectangle**, e **how to set shadow** in uno snippet di codice pulito e riutilizzabile.  
* Fornito un esempio completo, pronto all'uso, che puoi incollare in qualsiasi progetto C#.

## Cosa fare dopo?

Ora che hai padroneggiato le basi, considera di esplorare:

* **How to add shadow to images** – la stessa API `Shadow` funziona per `ShapeType.Image`.
* **Combining multiple shapes** – crea diagrammi di flusso o infografiche direttamente in Word.
* **Exporting to PDF** – chiama `document.Save("output.pdf")` dopo aver aggiunto le ombre per una versione stampabile.

Sentiti libero di sperimentare con colori diversi, angoli o anche riempimenti a gradiente. L'API è sufficientemente flessibile da permetterti di creare documenti dall'aspetto professionale senza mai aprire Word manualmente.

---

Buona programmazione! Se incontri problemi, lascia un commento qui sotto o controlla i forum di Aspose.Words – la community è pronta ad aiutare.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}