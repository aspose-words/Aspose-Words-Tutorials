---
category: general
date: 2026-10-13
description: Scopri come aggiungere un pulsante di comando programmaticamente usando
  Aspose.Words. Questa guida mostra anche come creare un pulsante in un documento
  Word con codice C# completo.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- add command button programmatically
- create word document button
language: it
lastmod: 2026-10-13
og_description: Aggiungi un pulsante di comando programmaticamente a un documento
  Word usando Aspose.Words. Segui questo tutorial completo per creare un pulsante
  in un documento Word con C#.
og_image_alt: Screenshot of a Word document with a command button inserted programmatically
og_title: Aggiungi un pulsante di comando programmaticamente a un documento Word –
  guida passo passo
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  headline: How to add a command button programmatically in a Word document
  type: TechArticle
- description: Learn how to add a command button programmatically using Aspose.Words.
    This guide also shows how to create a Word document button with full C# code.
  name: How to add a command button programmatically in a Word document
  steps:
  - name: 'Create a new console project:'
    text: 'Create a new console project:'
  - name: 'Add the Aspose.Words NuGet package:'
    text: 'Add the Aspose.Words NuGet package:'
  - name: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
    text: Open **Program.cs** and replace its content with the scaffold shown in the
      next steps.
  type: HowTo
tags:
- Aspose.Words
- C#
- Word automation
title: Come aggiungere un pulsante di comando programmaticamente in un documento Word
url: /it/net/working-with-oleobjects-and-activex/how-to-add-a-command-button-programmatically-in-a-word-docum/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere un pulsante di comando programmaticamente in un documento Word  

Se hai bisogno di **aggiungere un pulsante di comando programmaticamente**, Aspose.Words fornisce un'API pulita che ti consente di incorporare controlli modulo OLE direttamente in un file .docx. Questo tutorial ti guida attraverso ogni passaggio necessario per **creare un pulsante in un documento Word** che si comporta come un normale pulsante di modulo quando il documento viene aperto in Microsoft Word.  

Imparerai come configurare l'ambiente di sviluppo, inserire il pulsante, configurare le sue proprietà e verificare il risultato. Non sono richieste utility esterne — basta un progetto .NET e la libreria Aspose.Words per .NET.  

## Prerequisiti  

Prima di iniziare, assicurati di avere:  

* .NET 6.0 SDK o versioni successive installate.  
* Una versione recente di Aspose.Words per .NET (gli esempi usano la 23.12, ma qualsiasi rilascio 22.x+ funziona).  
* Un IDE come Visual Studio 2022 o Visual Studio Code.  

Il codice funziona su Windows, macOS e Linux perché Aspose.Words è indipendente dalla piattaforma.  

## Passo 1: Configurare il progetto e fare riferimento ad Aspose.Words  

1. Crea un nuovo progetto console:  

   ```bash
   dotnet new console -n WordButtonDemo
   cd WordButtonDemo
   ```  

2. Aggiungi il pacchetto NuGet Aspose.Words:  

   ```bash
   dotnet add package Aspose.Words
   ```  

3. Apri **Program.cs** e sostituisci il suo contenuto con lo scheletro mostrato nei passaggi successivi.  

Configurare il progetto in questo modo garantisce che il compilatore possa trovare gli spazi dei nomi `Aspose.Words` e `Aspose.Words.Drawing.Forms` richiesti per i controlli modulo.  

## Passo 2: Inizializzare un documento vuoto e un DocumentBuilder  

La classe `Document` rappresenta l'intero file Word, mentre `DocumentBuilder` fornisce un'API fluida per aggiungere contenuti.  

```csharp
using Aspose.Words;
using Aspose.Words.Drawing.Forms;
using System.Drawing;   // required for RectangleF

// Create an empty document.
Document doc = new Document();

// Create a builder linked to the document.
DocumentBuilder builder = new DocumentBuilder(doc);
```  

*Perché questo passaggio è importante* – Senza un `DocumentBuilder` non è possibile posizionare il pulsante con precisione sulla pagina. Il builder rispetta anche la posizione corrente del cursore, facilitando l'inserimento di più controlli in seguito.  

## Passo 3: Inserire il controllo OLE pulsante di comando  

Aspose.Words tratta un pulsante di comando come un controllo OLE di tipo `ControlType.CommandButton`. Definisci la sua posizione e dimensione con un `RectangleF` misurato in punti (1 punto = 1/72 di pollice).  

```csharp
// Define the button rectangle: X=100, Y=150, Width=120, Height=30 (points)
RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

// Insert the command button at the current cursor position.
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    ControlType.CommandButton,
    buttonRect);
```  

**Punti chiave**  

* L'origine del rettangolo (X, Y) è relativa all'angolo in alto a sinistra della pagina.  
* Modificando `Width` o `Height` si modifica la dimensione visiva del pulsante.  
* `InsertForms2OleControl` restituisce un oggetto `Forms2OleControl` che puoi configurare ulteriormente.  

## Passo 4: Configurare il nome e la didascalia del pulsante  

Il **nome** è usato dal motore macro di Word per identificare il controllo, mentre la **didascalia** è il testo che l'utente vede.  

```csharp
// Set a unique identifier for the button.
commandButton.Name = "cmdSubmit";

// Set the text displayed on the button.
commandButton.Caption = "Submit";
```  

Se prevedi di aggiungere macro VBA in seguito, utilizza un nome descrittivo perché il registratore di macro di Word fa riferimento a questa proprietà.  

## Passo 5: (Opzionale) Salvare il documento e verificare il risultato  

Salvare il file ti consente di aprirlo in Microsoft Word per confermare che il pulsante appare e funziona.  

```csharp
// Save the document to the output folder.
string outputPath = Path.Combine(Environment.CurrentDirectory, "CommandButtonDemo.docx");
doc.Save(outputPath);

Console.WriteLine($"Document saved to: {outputPath}");
```  

Quando apri *CommandButtonDemo.docx* in Word, dovresti vedere un pulsante etichettato **Submit** posizionato approssimativamente a 1,4 pollici dal margine sinistro e 2,1 pollici dalla parte superiore della pagina. Cliccare il pulsante non fa nulla per impostazione predefinita perché non è associata alcuna macro, ma il controllo visivo è pienamente funzionale.  

## Passo 6: Casi limite e problemi comuni  

| Situazione | Cosa controllare | Correzione consigliata |
|------------|------------------|------------------------|
| **Il pulsante si sovrappone al testo esistente** | Il rettangolo può intersecarsi con un paragrafo, causando problemi di layout. | Inserisci il pulsante dopo aver chiamato `builder.Writeln()` per spostare il cursore su una nuova riga, oppure regola la coordinata `Y`. |
| **Il documento si apre con un avviso** | Alcune versioni di Word segnalano i controlli OLE che non hanno un programma collegato. | Assicurati che il tipo di controllo sia `CommandButton`; Word lo tratta come un elemento di modulo standard e non richiede un programma esterno. |
| **Esecuzione su Linux con ambiente headless** | Word non può essere avviato per testare l'interfaccia, ma il file rimane valido. | Utilizza un test unitario che legge le proprietà del controllo (`commandButton.Name`, `commandButton.Caption`) per verificare che siano state impostate correttamente. |
| **Necessità di più pulsanti** | Riutilizzare lo stesso `DocumentBuilder` senza spostare il cursore aggiunge il pulsante sopra quello precedente. | Chiama `builder.MoveToDocumentEnd()` o regola il valore `Y` del rettangolo prima di ogni inserimento. |

Affrontare questi casi limite in anticipo fa risparmiare tempo quando si scala la soluzione a moduli completi con decine di controlli.  

## Passo 7: Esempio completo e eseguibile  

Di seguito è riportato un programma autonomo che puoi copiare, incollare ed eseguire senza modifiche (a parte il ripristino del pacchetto NuGet).  

```csharp
using System;
using System.IO;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing.Forms;

namespace WordButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a new empty document.
            Document doc = new Document();

            // 2. Create a DocumentBuilder to work with the document.
            DocumentBuilder builder = new DocumentBuilder(doc);

            // 3. Define the button rectangle (position + size).
            RectangleF buttonRect = new RectangleF(100, 150, 120, 30);

            // 4. Insert the command button OLE control.
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                ControlType.CommandButton,
                buttonRect);

            // 5. Set identifying properties.
            commandButton.Name = "cmdSubmit";
            commandButton.Caption = "Submit";

            // 6. Save the document.
            string outputPath = Path.Combine(
                Environment.CurrentDirectory,
                "CommandButtonDemo.docx");
            doc.Save(outputPath);

            Console.WriteLine($"Document saved to: {outputPath}");
        }
    }
}
```

**Output previsto**  

L'esecuzione del programma stampa un percorso simile a:  

```
Document saved to: C:\Path\To\WordButtonDemo\CommandButtonDemo.docx
```  

Aprire il *CommandButtonDemo.docx* generato mostra un unico pulsante **Submit** posizionato alle coordinate definite nel codice. Non compaiono altri elementi UI, confermando che il flusso di lavoro **add command button programmatically** è riuscito.  

## Conclusione  

Ora sai come **add a command button programmatically** a un documento Word usando Aspose.Words, e comprendi anche come **create a Word document button** che può essere collegato in seguito a macro VBA o a strumenti di automazione esterni. Il processo consiste nell'inizializzare un documento, inserire un controllo OLE `CommandButton`, configurare le sue proprietà e salvare il file.  

Da qui potresti:  

* Aggiungere più controlli (caselle di controllo, campi di testo) ripetendo il passo 3 con valori `ControlType` diversi.  
* Collegare macro VBA al pulsante per eseguire azioni come salvare un modulo o inviare un'email.  
* Generare interi moduli dinamicamente iterando su una collezione di definizioni di campi basata sui dati.  

Sperimenta con le coordinate del rettangolo e la didascalia del pulsante per adattarle al tuo design UI. Buon coding!  

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Aggiungere un campo modulo Combo Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aggiungere un campo modulo Check Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)
- [Creare un documento Word vuoto con Aspose.Words – Guida passo‑passo](/words/english/net/programming-with-shapes/create-blank-word-document-with-aspose-words-step-by-step-gu/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}