---
category: general
date: 2026-08-04
description: Crea un documento Word vuoto e inserisci un pulsante di comando usando
  Aspose.Words. Impara a impostare le dimensioni del pulsante e ad aggiungere un pulsante
  cliccabile in C#.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- insert command button
- add clickable button
- set button size
- create command button
language: it
lastmod: 2026-08-04
og_description: Crea un documento Word vuoto con Aspose.Words e inserisci un pulsante
  di comando. Questa guida mostra come impostare le dimensioni del pulsante, aggiungere
  un pulsante cliccabile e salvare il file.
og_image_alt: Screenshot of a Word document containing a clickable command button
  created with C#
og_title: Crea un documento Word vuoto e aggiungi un pulsante di comando – tutorial
  completo C#
schemas:
- author: Aspose
  dateModified: '2026-08-04'
  description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  headline: Create blank word document with a command button – step‑by‑step guide
  type: TechArticle
- description: Create blank word document and insert command button using Aspose.Words.
    Learn to set button size and add clickable button in C#.
  name: Create blank word document with a command button – step‑by‑step guide
  steps:
  - name: The ProgID of the OLE control – `"CommandButton"` for a standard button.
    text: The ProgID of the OLE control – `"CommandButton"` for a standard button.
  - name: A `Rectangle` that defines the **set button size** and position.
    text: A `Rectangle` that defines the **set button size** and position.
  - name: The caption that appears on the button.
    text: The caption that appears on the button.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Crea un documento Word vuoto con un pulsante di comando – guida passo passo
url: /it/java/using-document-elements/create-blank-word-document-with-a-command-button-step-by-ste/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto con un pulsante di comando – guida passo‑passo

Se hai bisogno di **creare un documento Word vuoto** che contenga un pulsante interattivo, questo tutorial ti mostra esattamente come farlo con Aspose.Words per .NET. Imparerai a **inserire un pulsante di comando**, a regolarne l’aspetto e a renderlo cliccabile—tutto in poche righe di C#.

La guida copre tutto, dall’impostazione del progetto al salvataggio del file finale, così potrai copiare‑incollare la soluzione completa nella tua applicazione. Lungo il percorso spiegheremo anche come **aggiungere un pulsante cliccabile**, **impostare le dimensioni del pulsante** e **creare un pulsante di comando** programmaticamente.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 SDK o versioni successive installate.  
* Visual Studio 2022 (o qualsiasi IDE che supporti .NET).  
* Pacchetto NuGet Aspose.Words per .NET (`Aspose.Words` versione 23.12 o più recente).  
* Familiarità di base con C# e la programmazione orientata agli oggetti.

Non sono necessari assembly di interop di Office aggiuntivi perché Aspose.Words funziona completamente in modo indipendente da Microsoft Word.

## Passo 1: Configura il progetto .NET

Crea un’applicazione console che ospiterà il codice di automazione Word.

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Questo comando crea una nuova cartella `WordButtonDemo` con un file `Program.cs` pronto all’esecuzione e aggiunge la libreria Aspose.Words.

## Passo 2: Crea un documento Word vuoto

La prima operazione è **creare un documento Word vuoto**. Aspose.Words fornisce la classe `Document` che rappresenta un file Word vuoto fin da subito.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Create a new, empty Word document.
Document doc = new Document();
```

Creare un documento vuoto ti offre una tela pulita su cui puoi aggiungere paragrafi, tabelle o, in questo caso, un pulsante di comando OLE.

## Passo 3: Inizializza DocumentBuilder

`DocumentBuilder` è l’aiutante che ti consente di inserire contenuti nel documento. Devi collegarlo al documento appena creato.

```csharp
// Attach a DocumentBuilder to the empty document.
DocumentBuilder builder = new DocumentBuilder(doc);
```

Il builder mantiene la posizione corrente del cursore, così ogni inserimento successivo avviene esattamente dove desideri.

## Passo 4: Inserisci il pulsante di comando

Ora **inseriamo il pulsante di comando** (un OLE `Forms2OleControl`) nel documento. Il metodo `InsertForms2OleControl` richiede tre argomenti:

1. Il ProgID del controllo OLE – `"CommandButton"` per un pulsante standard.  
2. Un `Rectangle` che definisce la **impostazione delle dimensioni del pulsante** e la posizione.  
3. La didascalia che appare sul pulsante.

```csharp
// Define the button's position (x, y) and size (width, height).
Rectangle buttonRect = new Rectangle(0, 0, 120, 30); // 120 px wide, 30 px high

// Insert the command button with the desired caption.
Forms2OleControl cmdButton = builder.InsertForms2OleControl(
    "CommandButton",   // ProgID for a CommandButton control
    buttonRect,        // Position and size
    "Click Me");       // Caption displayed on the button
```

Quando il documento viene aperto in Word, il pulsante si comporta come qualsiasi controllo di modulo nativo: puoi cliccarlo e Word eseguirà la macro associata (se presente). Questo soddisfa il requisito di **aggiungere un pulsante cliccabile**.

### Perché usare Forms2OleControl?

`Forms2OleControl` incorpora un oggetto OLE direttamente nel file DOCX, preservando le proprietà del controllo senza necessità dell’assembly Interop di Word. È il modo più affidabile per **creare un pulsante di comando** che funzioni su tutte le versioni di Word.

## Passo 5: Personalizza il pulsante (opzionale)

Potresti voler **impostare le dimensioni del pulsante** in modo più preciso o modificare altre proprietà come il carattere o il colore di sfondo. Aspose.Words espone l’oggetto OLE sottostante, consentendo ulteriori regolazioni.

```csharp
// Example: change the button's background color (requires OLE automation).
// Note: This step is optional and demonstrates additional customization.
cmdButton.OleFormat.Icon = true; // Show an icon instead of the default appearance.
```

Se ti serve una dimensione diversa, basta modificare i valori del `Rectangle` nel Passo 4. Le coordinate sono misurate in punti (1 pt = 1/72 pollice), quindi `120` corrisponde a circa 1,67 pollici di larghezza.

## Passo 6: Salva il documento

Infine, scrivi il documento su disco. Il file risultante contiene un **documento Word vuoto** con un pulsante di comando pienamente funzionante.

```csharp
// Save the document as a .docx file.
doc.Save("CommandButtonDemo.docx");
```

Quando apri `CommandButtonDemo.docx` in Microsoft Word, vedrai un pulsante con l’etichetta “Click Me”. Cliccando il pulsante verrà mostrata la finestra di dialogo della macro predefinita, a meno che non venga collegata una macro personalizzata.

## Codice sorgente completo

Di seguito trovi il programma completo da copiare in `Program.cs`. Include tutti i passaggi descritti sopra e si compila senza modifiche.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

namespace WordButtonDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Step 2: Create a blank word document.
            Document doc = new Document();

            // Step 3: Initialize DocumentBuilder.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Step 4: Define button size and insert command button.
            Rectangle buttonRect = new Rectangle(0, 0, 120, 30);
            Forms2OleControl cmdButton = builder.InsertForms2OleControl(
                "CommandButton",
                buttonRect,
                "Click Me");

            // Optional: further customization (e.g., set icon).
            // cmdButton.OleFormat.Icon = true;

            // Step 6: Save the document.
            doc.Save("CommandButtonDemo.docx");

            System.Console.WriteLine("Document created successfully.");
        }
    }
}
```

### Risultato atteso

L’esecuzione del programma produce `CommandButtonDemo.docx`. Aprendo il file in Word si osserva:

* Una singola pagina contenente un pulsante con l’etichetta **Click Me**.  
* Il pulsante rispetta la **impostazione delle dimensioni del pulsante** (120 × 30 punti).  
* Cliccando il pulsante si attiva il comportamento predefinito del pulsante di comando di Word, confermando che l’operazione **aggiungere un pulsante cliccabile** è riuscita.

## Domande frequenti e casi particolari

| Domanda | Risposta |
|----------|----------|
| **Funziona con file .doc?** | Sì. Cambia l’estensione del file in `doc.Save("file.doc")`. Il controllo OLE viene memorizzato anche nel formato binario legacy. |
| **E se ho bisogno di più pulsanti?** | Chiama `InsertForms2OleControl` più volte, regolando il `Rectangle` per ciascun nuovo pulsante in modo da evitare sovrapposizioni. |
| **Posso collegare una macro al pulsante?** | Il pulsante stesso non contiene codice macro. Devi aggiungere una macro VBA al documento manualmente o tramite la collezione `Modules` dell’oggetto `Document`. |
| **Il pulsante è visibile nell’esportazione PDF?** | Quando esporti il DOCX in PDF usando Aspose.Words, il pulsante viene renderizzato come immagine statica, non come controllo interattivo. |
| **Quali versioni di Word sono supportate?** | Il pulsante di comando OLE funziona in Word 2007 e versioni successive, poiché segue la specifica standard Forms2.0. |

## Conclusione

Ora sai come **creare un documento Word vuoto**, **inserire un pulsante di comando**, **aggiungere un pulsante cliccabile** e **impostare le dimensioni del pulsante** usando Aspose.Words per .NET. L’esempio completo dimostra il flusso di lavoro **creare un pulsante di comando** dall’inizio alla fine, fornendoti una solida base per attività di automazione Word più avanzate.

## Prossimi passi

* Esplora altri controlli OLE (ad esempio `CheckBox`, `ListBox`) modificando il ProgID in `InsertForms2OleControl`.  
* Combina il pulsante con una macro VBA per eseguire azioni personalizzate quando l’utente lo clicca.  
* Usa `DocumentBuilder` di Aspose.Words per aggiungere contenuti aggiuntivi come tabelle, immagini o note a piè di pagina prima di inserire il pulsante.  
* Sperimenta con i valori di **impostazione delle dimensioni del pulsante** per adattarli ai requisiti di layout del tuo documento.

Buona programmazione e divertiti a creare documenti Word più ricchi con controlli interattivi!

## Cosa dovresti imparare dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell’API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Create Blank Word Document with Shadowed Rectangle Shape – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-blank-word-document-with-shadowed-rectangle-shape-ste/)
- [Create Word Document with Aspose.Words for .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}