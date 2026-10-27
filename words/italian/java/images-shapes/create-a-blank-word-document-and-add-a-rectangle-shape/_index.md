---
category: general
date: 2026-10-23
description: Crea un documento Word vuoto, aggiungi una forma rettangolare e nascondi
  la forma in Word usando Aspose.Words. Codice passo‑passo per gli sviluppatori .NET.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- add rectangle shape
- how to insert shape
- hide shape word
language: it
lastmod: 2026-10-23
og_description: Crea un documento Word vuoto, aggiungi una forma rettangolare e nascondi
  la forma in Word con Aspose.Words. Segui l'esempio completo in C#.
og_image_alt: Screenshot of a Word document containing a hidden rectangle shape
og_title: Crea un documento Word vuoto e aggiungi una forma rettangolare nascosta
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create a blank Word document, add a rectangle shape, and hide the shape
    in Word using Aspose.Words. Step‑by‑step code for .NET developers.
  headline: Create a blank Word document and add a rectangle shape
  type: TechArticle
tags:
- Aspose.Words
- .NET
- Word automation
title: Crea un documento Word vuoto e aggiungi una forma rettangolare
url: /it/java/images-shapes/create-a-blank-word-document-and-add-a-rectangle-shape/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e aggiungi una forma rettangolare

Se hai bisogno di **creare un documento Word vuoto**, questa guida ti mostra come farlo con Aspose.Words per .NET. Imparerai anche **come inserire una forma** — in particolare un rettangolo — e **nascondere la forma in Word** in modo che non influisca sul layout.

Il tutorial percorre ogni riga di codice, spiega perché ogni passaggio è importante e copre le insidie comuni, come la visibilità delle forme nascoste in diverse modalità di visualizzazione di Word. Alla fine avrai un file `.docx` completamente funzionante che contiene una forma rettangolare nascosta che potrai successivamente rivelare o manipolare programmaticamente.

## Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.6+)
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)
- Un ambiente di sviluppo come Visual Studio 2022 o VS Code con estensioni C#
- Familiarità di base con la sintassi C# e i concetti dei documenti Word

Non è necessaria alcuna installazione aggiuntiva di Office perché Aspose.Words funziona interamente in memoria.

## Crea un documento Word vuoto

Il primo passo è istanziare un oggetto `Document` vuoto. Questo oggetto rappresenta un file Word che non contiene ancora sezioni, paragrafi o contenuti.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document
Document document = new Document();
```

**Perché è importante:**  
Un `Document` vuoto ti offre una tela pulita. Se parti da un modello esistente, le forme nascoste potrebbero ereditare stili indesiderati. Iniziare da zero garantisce che la forma rettangolare che aggiungerai in seguito sia l'unico contenuto sotto il tuo controllo.

## Aggiungi una forma rettangolare al documento

Successivamente, abbiamo bisogno di un `DocumentBuilder` per inserire contenuti nel documento. Il metodo `InsertShape` del builder è il modo standard **per inserire forme**, come rettangoli, cerchi o disegni personalizzati.

```csharp
// Step 2: Initialize a DocumentBuilder to add content
DocumentBuilder builder = new DocumentBuilder(document);

// Step 3: Insert a rectangle shape of size 200x100 points
Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

**Perché è importante:**  
`InsertShape` restituisce un oggetto `Shape` che puoi configurare ulteriormente (colore, stile della linea, ecc.). Le dimensioni sono espresse in punti (1 punto = 1/72 di pollice), corrispondenti al sistema di misurazione interno di Word.

### Opzionale: stilizzare il rettangolo (opzionale)

Se desideri che il rettangolo abbia un bordo visibile quando lo renderai nuovamente visibile, puoi impostare lo spessore della linea e il colore:

```csharp
rectangleShape.LineWeight = 0.5;               // Thin border
rectangleShape.LineColor = System.Drawing.Color.Blue;
```

Queste righe sono opzionali perché la forma verrà nascosta nel passaggio successivo.

## Nascondi la forma in Word

Word consente di nascondere le forme dal layout mantenendole comunque parte del modello oggetto del documento. Impostare la proprietà `Hidden` a `true` rende la forma invisibile nella visualizzazione normale ma ancora selezionabile tramite l'API.

```csharp
// Step 4: Hide the shape so it does not appear in the layout
rectangleShape.Hidden = true;
```

**Perché è importante:**  
Una forma nascosta è utile per memorizzare metadati, segnaposti per elaborazioni successive o contenuti condizionali che riveli solo in determinate circostanze (ad esempio, durante la generazione di un rapporto finale). La forma rimane nel file, quindi puoi renderla visibile programmaticamente in seguito con `rectangleShape.Hidden = false;`.

## Salva il documento

Infine, scrivi il documento su disco. L'estensione del file determina il formato Word; `.docx` è il moderno formato Open XML.

```csharp
// Step 5: Save the document with the hidden shape
string outputPath = @"C:\Temp\HiddenShape.docx";
document.Save(outputPath);
```

**Risultato:**  
Aprendo `HiddenShape.docx` in Microsoft Word si visualizza una pagina altrimenti **vuota**. Il rettangolo non è visibile, ma se vai su **Home → Select → Selection Pane**, vedrai la forma elencata e potrai attivare/disattivare la sua visibilità.

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare, incollare ed eseguire. Include tutte le istruzioni `using` necessarie e i commenti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // Create a new blank document
        Document document = new Document();

        // Initialize a DocumentBuilder for content insertion
        DocumentBuilder builder = new DocumentBuilder(document);

        // Insert a rectangle shape (200x100 points)
        Shape rectangleShape = builder.InsertShape(ShapeType.Rectangle, 200, 100);

        // Optional styling (comment out if not needed)
        rectangleShape.LineWeight = 0.5;
        rectangleShape.LineColor = System.Drawing.Color.Blue;

        // Hide the shape so it does not appear in the layout
        rectangleShape.Hidden = true;

        // Save the document
        string outputPath = @"C:\Temp\HiddenShape.docx";
        document.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output previsto:**  

- La console stampa il percorso di salvataggio.  
- `HiddenShape.docx` si apre come una pagina vuota in Word.  
- La forma rettangolare esiste ma è nascosta; puoi verificarla tramite il *Selection Pane* o impostando programmaticamente `Hidden = false` e riaprendo il file.

## Domande comuni e casi particolari

| Question | Answer |
|----------|--------|
| **Posso nascondere altri tipi di forma?** | Sì. Qualsiasi `Shape` (ad esempio `ShapeType.Ellipse`, `ShapeType.Picture`) supporta la proprietà `Hidden`. |
| **La forma nascosta aumenterà le dimensioni del file?** | L'aumento è trascurabile (pochi kilobyte) perché i dati della forma sono memorizzati come XML nel pacchetto `.docx`. |
| **E se ho bisogno che la forma appaia solo nella visualizzazione di stampa?** | Usa la proprietà `Shape.IsPrint` invece di `Hidden`. Impostare `IsPrint = false` nasconde la forma dall'output stampato ma la mantiene visibile sullo schermo. |
| **Come rivelare la forma in seguito?** | Carica il documento, individua la forma (ad esempio tramite `Shape.Name`), quindi imposta `shape.Hidden = false;` e salva. |
| **Funziona con il formato .doc (binario)?** | Sì, Aspose.Words può salvare in `.doc` usando `document.Save("file.doc");`. Il flag di nascondimento viene preservato. |

## Consigli professionali

- **Assegna un nome alle tue forme**: `rectangleShape.Name = "PlaceholderRectangle";` rende più facile trovarla in seguito tramite `document.GetChildNodes(NodeType.Shape, true).Cast<Shape>().FirstOrDefault(s => s.Name == "PlaceholderRectangle")`.
- **Elaborazione batch**: Se devi aggiungere forme nascoste a molti documenti, avvolgi il codice in un metodo e riutilizza l'istanza `DocumentBuilder`.
- **Prestazioni**: Creare una forma è poco costoso, ma salvare frequentemente documenti di grandi dimensioni può essere limitato da I/O. Considera l'uso di `MemoryStream` per l'elaborazione intermedia.

## Conclusione

Ora sai come **creare un documento Word vuoto**, **aggiungere una forma rettangolare** e **nascondere la forma in Word** usando Aspose.Words per .NET. Questa tecnica ti consente di inserire segnaposti invisibili che puoi rivelare o manipolare in seguito, un modello utile per la generazione dinamica di report, contenuti condizionali e la creazione di template di documenti.

Prossimi passi che potresti esplorare:

- Sostituire il rettangolo con un'immagine o un grafico usando `ShapeType.Picture`.
- Utilizzare **how to insert shape** nelle sezioni intestazione/piè di pagina per segnaposti in stile filigrana.
- Combinare forme nascoste con la convalida dei dati basata su **add rectangle shape** (ad esempio, memorizzare JSON nella proprietà `AlternativeText` di una forma).

Buon coding e sentiti libero di sperimentare con altri tipi di forma e opzioni di visibilità per adattarle alle tue esigenze di automazione dei documenti!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word – Come aggiungere forma rettangolare e ombra](/words/english/net/programming-with-shapes/create-word-document-how-to-add-rectangle-shape-and-shadow/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Crea un documento Word vuoto con una forma ellisse nascosta – Guida completa C#](/words/english/net/programming-with-shapes/create-a-blank-word-document-with-a-hidden-ellipse-shape-ful/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}