---
category: general
date: 2026-09-30
description: Aggiungi un controllo ActiveX a un documento Word usando C#. Scopri come
  inserire un pulsante ActiveX, aggiungere un pulsante di comando e renderlo cliccabile.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- activex control word
- how to insert activex
- how to add command button
- insert activex button
- add clickable button word
language: it
lastmod: 2026-09-30
og_description: Aggiungi un controllo ActiveX a un documento Word con C#. Segui questa
  guida completa per inserire un pulsante ActiveX, aggiungere un pulsante di comando
  e renderlo cliccabile.
og_image_alt: Word document displaying an inserted ActiveX command button
og_title: Aggiungi un controllo ActiveX ai documenti Word – guida passo‑passo in C#
schemas:
- author: Aspose
  dateModified: '2026-09-30'
  description: Add an ActiveX control word to a Word document using C#. Learn how
    to insert an ActiveX button, add a command button, and make it clickable.
  headline: How to add an ActiveX control word in Word with C#
  type: TechArticle
tags:
- ActiveX
- Aspose.Words
- C#
- Word automation
title: Come aggiungere un controllo ActiveX in Word con C#
url: /it/net/working-with-oleobjects-and-activex/how-to-add-an-activex-control-word-in-word-with-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come aggiungere una parola di controllo ActiveX in Word con C#

Se hai bisogno di incorporare una **ActiveX control word** all'interno di un file Microsoft Word, questa guida ti mostra esattamente come farlo. Vedrai un esempio completo e eseguibile che inserisce un pulsante cliccabile, salva il documento e funziona con l'ultima versione di Aspose.Words per .NET.

Aggiungere una parola di controllo ActiveX ti consente di creare moduli interattivi, finestre di dialogo personalizzate o semplici elementi UI che si comportano come controlli Word nativi. Che tu stia costruendo un modello di contratto che richiede l'interazione dell'utente o un report che necessita di un pulsante “Esegui”, i passaggi seguenti coprono tutto ciò di cui hai bisogno.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* SDK .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.8)
* Visual Studio 2022 (o qualsiasi IDE che supporti C#)
* Aspose.Words per .NET installato (`dotnet add package Aspose.Words`)
* Una conoscenza di base di C# e della struttura dei documenti Word

> **Consiglio professionale:** Il metodo `InsertForms2OleControl` funziona solo con i controlli “Forms 2.0” legacy, che sono i controlli ActiveX che Word utilizza per i campi modulo. Se punti a versioni più recenti di Office, il controllo viene comunque visualizzato correttamente nel client desktop.

## Passo 1: Configura il progetto e importa i namespace

Crea un nuovo progetto console e aggiungi le istruzioni `using` richieste. Questo garantisce che il compilatore trovi le classi `Document`, `DocumentBuilder` e `OleControlType`.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Il namespace `Aspose.Words` fornisce API di alto livello per l'elaborazione di Word, mentre `Aspose.Words.Drawing` contiene l'enumerazione `OleControlType` necessaria per specificare il tipo di controllo ActiveX.

## Passo 2: Carica il documento Word di origine

Devi partire da un file Word che desideri modificare. Il codice seguente carica `input.docx` da una cartella da te specificata.

```csharp
// Step 2: Load the Word document you want to modify
string inputPath = @"C:\Docs\input.docx";
Document doc = new Document(inputPath);
```

Se il file non esiste, Aspose.Words genera una `FileNotFoundException`. Avvolgi la chiamata in un blocco `try/catch` se hai bisogno di una gestione degli errori più delicata.

## Passo 3: Crea un DocumentBuilder per modificare il documento

`DocumentBuilder` è lo strumento principale per inserire testo, immagini e controlli. Mantiene un cursore che punta alla posizione in cui verrà inserito il prossimo elemento.

```csharp
// Step 3: Create a DocumentBuilder to work with the document's content
DocumentBuilder builder = new DocumentBuilder(doc);
```

Per impostazione predefinita, il cursore del builder è posizionato all'inizio della prima sezione. Puoi spostarlo con metodi come `MoveToDocumentEnd()` o `MoveToParagraph(index)` se desideri il pulsante altrove.

## Passo 4: Inserisci un controllo ActiveX CommandButton

Ora arriva il cuore del tutorial: inserire una **ActiveX control word** che appare come pulsante cliccabile. Il metodo `InsertForms2OleControl` accetta due argomenti—il tipo di controllo e una didascalia (o nome) per il controllo.

```csharp
// Step 4: Insert an ActiveX CommandButton control with the caption "ClickMe"
builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");
```

* **Perché usare `OleControlType.CommandButton`?**  
  Indica a Word di creare un classico pulsante CommandButton di Forms 2.0, che visualizza una didascalia e può essere collegato a una macro o script VBA in seguito.

* **Cosa fa la didascalia?**  
  La stringa `"ClickMe"` diventa il testo visibile del pulsante. Puoi cambiarla in qualsiasi cosa si adatti alla tua UI.

### Inserimento del pulsante in una posizione specifica

Se hai bisogno del pulsante dopo un determinato paragrafo, sposta prima il builder:

```csharp
builder.MoveToParagraph(2); // moves to the third paragraph (zero‑based index)
builder.InsertParagraph(); // optional: add a blank line before the button
builder.InsertForms2OleControl(OleControlType.CommandButton, "Submit");
```

## Passo 5: Salva il documento modificato

Dopo aver inserito il controllo, persisti le modifiche in un nuovo file (o sovrascrivi l'originale).

```csharp
// Step 5: Save the modified document
string outputPath = @"C:\Docs\output.docx";
doc.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri `output.docx` nella versione desktop di Word, vedrai il pulsante etichettato **ClickMe** (o **Submit**, a seconda della didascalia usata). Cliccare il pulsante in modalità design non fa nulla per impostazione predefinita; puoi assegnare una macro in seguito tramite la scheda “Developer” di Word.

## Esempio completo e eseguibile

Di seguito trovi un programma autonomo che dimostra l'intero flusso di lavoro. Copialo in `Program.cs` di una nuova app console ed eseguilo.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXControlWordDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // Paths – adjust to your environment
            string inputPath = @"C:\Docs\input.docx";
            string outputPath = @"C:\Docs\output.docx";

            // 1️⃣ Load the source document
            Document doc = new Document(inputPath);

            // 2️⃣ Create a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(doc);

            // Optional: move to the end of the document
            builder.MoveToDocumentEnd();
            builder.Writeln(); // add a blank line before the button

            // 3️⃣ Insert the ActiveX CommandButton (the core of the activex control word)
            builder.InsertForms2OleControl(OleControlType.CommandButton, "ClickMe");

            // 4️⃣ Save the result
            doc.Save(outputPath);
            Console.WriteLine($"Successfully saved the document with an ActiveX button to: {outputPath}");
        }
    }
}
```

### Output previsto

* La console stampa il messaggio di successo con il percorso di output.
* L'apertura di `output.docx` mostra un pulsante **ClickMe** nella posizione in cui il builder lo ha inserito.
* Il pulsante può essere selezionato, ridimensionato o a cui può essere assegnata una macro tramite **Developer → Design Mode** di Word.

## Domande frequenti e gestione di casi limite

| Domanda | Risposta |
|----------|--------|
| **Come inserire un pulsante ActiveX nell'intestazione/piè di pagina?** | Sposta il builder nell'intestazione/piè di pagina con `builder.MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` prima di chiamare `InsertForms2OleControl`. |
| **E se ho bisogno di una casella di controllo invece di un pulsante?** | Usa `OleControlType.CheckBox` e fornisci una didascalia come `"Agree"`. |
| **Il pulsante funzionerà in Word Online?** | No. Word Online non supporta i controlli legacy Forms 2.0 ActiveX. Il pulsante viene visualizzato solo nel client desktop. |
| **Posso impostare la dimensione del pulsante programmaticamente?** | Dopo l'inserimento, recupera l'oggetto `Shape` tramite `builder.CurrentParagraph.Runs[0].GetShape()` e regola `Width`/`Height`. |
| **C'è un modo per assegnare una macro dal codice?** | Aspose.Words non espone la modifica delle macro. Devi aprire il documento in Word e collegare manualmente una macro o utilizzare le API Office Interop. |

## Consigli per l'uso in produzione

* **Evita percorsi hard‑coded** – utilizza `Path.Combine` e file di configurazione.
* **Rilascia il `Document`** – avvolgilo in una dichiarazione `using` se lavori con file di grandi dimensioni per liberare rapidamente la memoria.
* **Convalida l'output** – verifica programmaticamente che il documento contenga una forma di tipo `OleControl` iterando `doc.GetChildNodes(NodeType.Shape, true)`.
* **Nota di sicurezza** – i controlli ActiveX possono eseguire codice sulla macchina client. Distribuisci i documenti solo a utenti fidati e considera l'uso di firme digitali.

## Conclusione

Ora sai come aggiungere una **ActiveX control word** a un documento Word usando C#. Caricando un documento, creando un `DocumentBuilder`, inserendo un pulsante di comando con `InsertForms2OleControl` e salvando il file, puoi automatizzare la creazione di moduli Word interattivi. Sperimenta con altri valori di `OleControlType`, posiziona i controlli in intestazioni o tabelle e combinaci con macro per esperienze utente più ricche.

---

*Passi successivi*: esplora **come inserire controlli ActiveX** di altri tipi, impara **come aggiungere gestori di eventi per pulsanti di comando** tramite VBA e leggi le migliori pratiche per **inserire pulsanti ActiveX** per la compatibilità cross‑platform.

## Cosa dovresti imparare dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Incorporare oggetti OLE e controlli ActiveX nei documenti Word](/words/english/python-net/document-structure-and-content-manipulation/document-ole-objects-active-x/)
- [Aggiungere un campo modulo Combo Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-combo-box/)
- [Aggiungere un campo modulo Check Box a un documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-documentbuilder/insert-check-box/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}