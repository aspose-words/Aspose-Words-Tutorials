---
category: general
date: 2026-09-11
description: Impara a creare un documento Word in C# e ad aggiungere programmaticamente
  un pulsante di comando usando Aspose.Words in pochi semplici passaggi.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document c#
- programmatically add command button
language: it
lastmod: 2026-09-11
og_description: Crea un documento Word in C# e aggiungi programmaticamente un pulsante
  di comando con Aspose.Words. Segui questa guida completa per una soluzione funzionante.
og_image_alt: Screenshot of a Word document containing a Submit command button created
  with C#
og_title: Crea documento Word in C# – aggiungi un pulsante di comando programmaticamente
schemas:
- author: Aspose
  dateModified: '2026-09-11'
  description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  headline: How to create word document c# and programmatically add a command button
  type: TechArticle
- description: Learn how to create word document c# and programmatically add a command
    button using Aspose.Words in a few simple steps.
  name: How to create word document c# and programmatically add a command button
  steps:
  - name: Launch Word and open `CommandButton.docx`.
    text: Launch Word and open `CommandButton.docx`.
  - name: You should see a button labeled **Submit** in the document body.
    text: You should see a button labeled **Submit** in the document body.
  - name: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
    text: Hovering over the button reveals the name `btnSubmit` in the **Properties**
      pane (Developer tab → Properties).
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
- ActiveX
title: How to create word document c# and programmatically add a command button
url: /it/net/working-with-oleobjects-and-activex/how-to-create-word-document-c-and-programmatically-add-a-com/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come creare un documento Word c# e aggiungere programmaticamente un pulsante di comando

Se hai bisogno di **create word document c#** e incorporare un pulsante interattivo, questa guida ti mostra esattamente come farlo. Usando Aspose.Words puoi aggiungere programmaticamente un pulsante di comando in poche righe di codice, eliminando la necessità di lavoro manuale sull'interfaccia in Word.

In questo tutorial imparerai a:

* Inizializzare un file Word vuoto con C#.
* Inserire un controllo ActiveX **CommandButton**.
* Impostare le proprietà del pulsante, come nome e didascalia.
* Salvare il documento in modo che il pulsante appaia quando il file viene aperto in Microsoft Word.

Non sono necessari strumenti esterni oltre alla libreria Aspose.Words per .NET, e i passaggi funzionano con .NET 6+ o .NET Framework 4.6.2 e versioni successive.

## Prerequisiti

| Requisito | Motivo |
|------------|--------|
| .NET 6 SDK (or .NET Framework 4.6.2+) | Fornisce l'ambiente di esecuzione per il progetto C#. |
| Visual Studio 2022 (or any C# IDE) | Rende più semplice scrivere, compilare ed eseguire il codice. |
| Aspose.Words for .NET NuGet package | Fornisce le classi `Document`, `DocumentBuilder` e `Forms2OleControl` utilizzate nell'esempio. |
| Basic knowledge of C# syntax | Ti consente di seguire il codice senza ulteriori curve di apprendimento. |

Puoi aggiungere il pacchetto Aspose.Words tramite la console NuGet:

```powershell
Install-Package Aspose.Words
```

## Passo 1: Configurare un nuovo progetto console C#

Crea un'applicazione console che genererà il file Word. Apri un terminale ed esegui:

```bash
dotnet new console -n WordButtonDemo
cd WordButtonDemo
dotnet add package Aspose.Words
```

Il file `Program.cs` generato conterrà il codice mostrato nei passaggi successivi.

## Passo 2: Creare un documento vuoto e un DocumentBuilder

La prima operazione è istanziare un oggetto `Document`, che rappresenta un file `.docx` vuoto, e un `DocumentBuilder` che ti permette di modificare il contenuto del documento.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Step 2: Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
```

**Perché è importante:**  
`Document` è il contenitore di tutti gli elementi Word (paragrafi, tabelle, controlli). `DocumentBuilder` fornisce un'API fluida per inserire oggetti nella posizione corrente del cursore senza dover gestire collezioni di nodi a basso livello.

## Passo 3: Inserire un controllo ActiveX CommandButton

Aspose.Words supporta l'inserimento di controlli ActiveX legacy tramite il metodo `InsertForms2OleControl`. Il metodo richiede il tipo di controllo e le dimensioni desiderate in punti.

```csharp
        // Step 3: Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);
```

**Cosa succede dietro le quinte:**  
Word tratta un controllo ActiveX come un oggetto OLE (Object Linking and Embedding). La classe `Forms2OleControl` avvolge i dati OLE ed espone proprietà come `Name` e `Caption`.

## Passo 4: Configurare nome e didascalia del pulsante

Dopo aver posizionato il controllo, puoi personalizzare le sue proprietà di runtime. Impostare un `Name` significativo ti aiuta a identificare il pulsante in seguito, mentre `Caption` definisce il testo visualizzato sul pulsante.

```csharp
        // Step 4: Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";
```

**Consiglio professionale:**  
Se prevedi di gestire l'evento click del pulsante con VBA, il `Name` diventa il nome della macro a cui fai riferimento, ad esempio `Sub btnSubmit_Click()`.

## Passo 5: Salvare il documento su disco

Infine, scrivi il documento in un file `.docx`. Scegli una cartella a cui hai accesso in scrittura; l'esempio utilizza un percorso relativo, che si risolve nella directory di output del progetto.

```csharp
        // Step 5: Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

L'esecuzione del programma produce `CommandButton.docx`. Aprendo il file in Microsoft Word vedrai un pulsante **Submit** cliccabile:

![Documento Word con un pulsante di comando Submit](/images/command-button.png "Screenshot di un documento Word contenente un pulsante di comando Submit creato con C#")

*Testo alternativo dell'immagine (og_image_alt):* `Screenshot di un documento Word contenente un pulsante di comando Submit creato con C#`

## Verifica del risultato

1. Avvia Word e apri `CommandButton.docx`.  
2. Dovresti vedere un pulsante con l'etichetta **Submit** nel corpo del documento.  
3. Passando il mouse sul pulsante verrà mostrato il nome `btnSubmit` nel riquadro **Properties** (scheda Sviluppatore → Proprietà).  

Se il pulsante non appare, assicurati che la scheda **Developer** sia abilitata in Word (File → Opzioni → Personalizza barra multifunzione → spunta *Developer*). I controlli ActiveX sono nascosti quando la scheda è disabilitata.

## Gestione di variazioni comuni e casi limite

| Situazione | Regolazione consigliata |
|-----------|------------------------|
| **Dimensione pulsante diversa** | Modifica gli argomenti di larghezza e altezza in `InsertForms2OleControl`. Ad esempio, `150, 40` crea un pulsante più grande. |
| **Pulsanti multipli** | Chiama `InsertForms2OleControl` più volte, spostando il cursore del builder tra le chiamate (`builder.Writeln();`). |
| **Pulsante senza ActiveX** | Usa `InsertFormField` per aggiungere un campo modulo legacy (ad esempio, una casella di controllo) se hai bisogno di compatibilità con versioni più vecchie di Word che bloccano ActiveX. |
| **Uso cross‑platform** | I controlli ActiveX funzionano solo nelle versioni Windows di Word. Per Mac o visualizzatori web, considera l'inserimento di un collegamento ipertestuale stilizzato come pulsante. |
| **Avvisi di sicurezza** | Word può mostrare un prompt di sicurezza quando si apre un documento contenente controlli ActiveX. Firmare il documento con un certificato attendibile riduce questo attrito. |

## Esempio completo, eseguibile

Di seguito trovi il programma completo che puoi copiare‑incollare in `Program.cs`. Compila ed esegue senza modifiche dopo aver aggiunto il pacchetto NuGet Aspose.Words.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

class Program
{
    static void Main()
    {
        // Create a new blank document and a DocumentBuilder to edit it
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Insert an ActiveX CommandButton control (size: 100x30 points)
        Forms2OleControl commandButton = builder.InsertForms2OleControl(
            ControlType.CommandButton, 100, 30);

        // Set the button's name and displayed caption
        commandButton.Name = "btnSubmit";
        commandButton.Caption = "Submit";

        // Save the document containing the button
        string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButton.docx");
        doc.Save(outputPath);
        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

**Output previsto nella console:**  

```
Document saved to C:\Path\To\WordButtonDemo\bin\Debug\net6.0\CommandButton.docx
```

Aprendo il file generato vedrai il pulsante **Submit** pronto per l'interazione.

## Conclusione

Ora sai come **create word document c#** e **programmatically add command button** controlli usando Aspose.Words. Il processo si riduce a inizializzare un `Document`, inserire un `Forms2OleControl`, configurare le sue proprietà e salvare il file. Da qui puoi:

* Aggiungere più controlli (ad esempio, caselle di controllo, campi di testo) modificando `ControlType`.
* Allegare macro VBA al pulsante per logica personalizzata.
* Combinare questa tecnica con altre funzionalità di Aspose.Words come la stampa unione o il riempimento di template.

Sperimenta con diverse dimensioni, didascalie e pulsanti multipli per adattarli al tuo scenario di automazione. Buon coding!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con intestazione e piè di pagina usando Aspose.Words](/words/english/net/header-footer-formatting/create-header-footer/)
- [Crea documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}