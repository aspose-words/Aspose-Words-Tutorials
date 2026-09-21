---
category: general
date: 2026-09-21
description: Scopri come creare un pulsante di comando ActiveX in un documento Word
  con Aspose.Words e C#. La guida passo‑passo copre l'inserimento, il posizionamento
  e il salvataggio.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create activex command button
- aspose.words activex
- c# documentbuilder
- insertforms2olecontrol
- activeX control in word
- programmatically add button
language: it
lastmod: 2026-09-21
og_description: Crea un pulsante di comando ActiveX in un documento Word usando C#
  e Aspose.Words. Segui questo tutorial completo per inserire, posizionare e salvare
  il pulsante programmaticamente.
og_image_alt: Screenshot showing an ActiveX command button inserted in a Word document
  using C#
og_title: Crea un pulsante di comando ActiveX in Word con C# – guida completa
schemas:
- author: Aspose
  dateModified: '2026-09-21'
  description: Learn how to create ActiveX command button in a Word document with
    Aspose.Words and C#. Step‑by‑step guide covers insertion, positioning, and saving.
  headline: How to create ActiveX command button in Word using C#
  type: TechArticle
tags:
- ActiveX
- C#
- Aspose.Words
- Word automation
- DocumentBuilder
title: Come creare un pulsante di comando ActiveX in Word usando C#
url: /it/net/working-with-oleobjects-and-activex/how-to-create-activex-command-button-in-word-using-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un pulsante di comando ActiveX in Word usando C#

Se devi **creare un pulsante di comando ActiveX** all'interno di un file Word, questa guida ti mostra i passaggi esatti. Utilizzando Aspose.Words per .NET puoi aggiungere, posizionare e configurare il pulsante interamente dal codice C#.

L'inserimento programmatico di un pulsante ActiveX elimina il lavoro manuale sull'interfaccia utente e consente la generazione automatizzata di documenti per moduli, report o template interattivi. In questo tutorial imparerai a usare **DocumentBuilder**, il metodo **InsertForms2OleControl** e le proprietà correlate per ottenere un pulsante pienamente funzionale.

## Cosa ti serve

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o successivo (il codice funziona anche con .NET Framework 4.7+)
* Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`)
* Un IDE come Visual Studio 2022 o VS Code
* Conoscenze di base di C# e dei concetti dei documenti Word

Non è necessaria alcuna installazione aggiuntiva di Office perché Aspose.Words funziona in modo indipendente da Microsoft Word.

## Passo 1: Configura il progetto C#

Crea un nuovo progetto console e aggiungi il pacchetto Aspose.Words.

```bash
dotnet new console -n WordActiveXDemo
cd WordActiveXDemo
dotnet add package Aspose.Words
```

La libreria `Aspose.Words` fornisce la classe **DocumentBuilder** che utilizzeremo per manipolare il documento.

## Passo 2: Inizializza il documento e il builder

Il primo blocco di codice crea un documento vuoto e un'istanza di `DocumentBuilder`. Questo oggetto è il punto di ingresso per tutte le operazioni di elaborazione di Word.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

// Create a new blank document.
Document doc = new Document();

// Create a builder to edit the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:** `DocumentBuilder` mantiene la posizione corrente del cursore, quindi qualsiasi inserimento successivo apparirà esattamente dove posizioni il cursore.

## Passo 3: Inserisci il pulsante di comando ActiveX

Il metodo **InsertForms2OleControl** crea un controllo ActiveX del tipo richiesto. Qui richiediamo un `CommandButton` e specifichiamo le sue dimensioni in punti (200 × 30 pt).

```csharp
// Insert an ActiveX CommandButton control (200 × 30 pt).
Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
    OleControlType.CommandButton, 200, 30);
```

**Spiegazione:**  
* `OleControlType.CommandButton` indica ad Aspose.Words di creare un pulsante anziché un altro tipo di controllo.  
* Il metodo restituisce un oggetto `Forms2OleControl`, che espone i campi di posizionamento e delle proprietà.

## Passo 4: Posiziona il pulsante e imposta le sue proprietà

Dopo l'inserimento puoi spostare il pulsante in qualsiasi punto della pagina e assegnargli un nome programmatico e una didascalia visibile.

```csharp
// Position the button (coordinates are in points).
cmdBtn.Left = 100;          // X‑coordinate
cmdBtn.Top = 150;           // Y‑coordinate

// Set the button's programmatic name and displayed text.
cmdBtn.Name = "btnSubmit";
cmdBtn.Caption = "Submit";
```

**Consiglio professionale:** Il sistema di coordinate parte dall'angolo in alto a sinistra della pagina. Regola `Left` e `Top` per allineare il pulsante con gli altri campi del modulo.

## Passo 5: Salva il documento

Infine, scrivi il documento su disco. Il file conterrà il pulsante ActiveX, pronto per essere aperto in Microsoft Word dove il pulsante diventa interattivo.

```csharp
// Save the document that now contains the ActiveX button.
doc.Save("ActiveXCommandButton.docx");
```

Quando apri `ActiveXCommandButton.docx` in Word, vedrai un pulsante etichettato **Submit** nella posizione specificata. Cliccandolo in Word verrà attivato il comportamento predefinito del pulsante (che potrai personalizzare successivamente con VBA o componenti aggiuntivi di Word).

## Esempio completo, eseguibile

Unendo tutti i pezzi ottieni un programma autonomo che puoi copiare, incollare ed eseguire.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // 1. Create a new document and builder.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2. Insert an ActiveX CommandButton (200 × 30 pt).
        Forms2OleControl cmdBtn = builder.InsertForms2OleControl(
            OleControlType.CommandButton, 200, 30);

        // 3. Position and configure the button.
        cmdBtn.Left = 100;          // X‑coordinate (points)
        cmdBtn.Top = 150;           // Y‑coordinate (points)
        cmdBtn.Name = "btnSubmit";
        cmdBtn.Caption = "Submit";

        // 4. Save the document.
        doc.Save("ActiveXCommandButton.docx");

        Console.WriteLine("Document created successfully.");
    }
}
```

**Output previsto:** la console stampa *“Document created successfully.”* e la cartella contiene ora `ActiveXCommandButton.docx`. Aprendo il file in Microsoft Word appare un pulsante **Submit** cliccabile posizionato a 100 pt dal margine sinistro e a 150 pt dall'alto della pagina.

## Problemi comuni e come evitarli

| Problema | Perché succede | Soluzione |
|----------|----------------|-----------|
| Il pulsante appare fuori dalla pagina | I valori `Left`/`Top` superano le dimensioni della pagina | Usa `doc.FirstSection.PageSetup.PageWidth` e `PageHeight` per calcolare coordinate sicure |
| Il pulsante non è visibile in Word | Il documento è stato salvato in un formato che rimuove i controlli ActiveX (es. `.txt`) | Salva sempre come `.docx` o `.doc` |
| Errore di runtime `ArgumentOutOfRangeException` | Larghezza o altezza impostate a zero o valori negativi | Assicurati che gli argomenti di dimensione passati a `InsertForms2OleControl` siano numeri positivi |

## Estendere la soluzione

Puoi personalizzare ulteriormente il pulsante impostando proprietà aggiuntive come `Enabled`, `Visible` o collegando una macro tramite VBA. La classe **Forms2OleControl** consente anche di inserire altri controlli ActiveX come caselle di controllo (`OleControlType.CheckBox`) o caselle combinate (`OleControlType.ComboBox`).

Se devi generare più pulsanti in un ciclo, incapsula la logica di inserimento in un metodo di supporto:

```csharp
static Forms2OleControl AddCommandButton(DocumentBuilder builder,
    string name, string caption, double left, double top)
{
    var btn = builder.InsertForms2OleControl(OleControlType.CommandButton, 200, 30);
    btn.Name = name;
    btn.Caption = caption;
    btn.Left = left;
    btn.Top = top;
    return btn;
}
```

## Conclusione

Ora sai come **creare un pulsante di comando ActiveX** in un documento Word usando C# e Aspose.Words. Il tutorial ha coperto la configurazione del progetto, l'inserimento del pulsante con `InsertForms2OleControl`, il suo posizionamento e il salvataggio del file finale. Con queste basi potrai automatizzare moduli complessi, incorporare controlli interattivi e integrare documenti Word in soluzioni .NET più ampie.

Successivamente, esplora argomenti correlati come **Aspose.Words ActiveX** form fields, **C# DocumentBuilder** styling avanzato, o l'aggiunta programmatica di **ActiveX control in Word** per caselle di controllo e liste a discesa. Sperimenta con coordinate e dimensioni diverse per adattarle ai requisiti del tuo layout. Buona programmazione!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci alternativi nei tuoi progetti.

- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Create rectangle shape in Word with Aspose.Words – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-with-aspose-words-step-by-ste/)
- [Create a Word Document with Table Using Aspose.Words](/words/english/net/add-content-using-document-builder/build-table/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}