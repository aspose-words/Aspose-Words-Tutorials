---
category: general
date: 2026-10-23
description: Crea un documento Word vuoto con C# e impara come inserire controlli
  ActiveX, incluso un pulsante, usando Aspose.Words.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create blank word document
- how to insert activex
- create activex control
- word document activex button
language: it
lastmod: 2026-10-23
og_description: Crea un documento Word vuoto con C# e impara come inserire controlli
  ActiveX, incluso un pulsante, usando Aspose.Words.
og_image_alt: Result of creating a blank Word document with an ActiveX Submit button
og_title: Crea un documento Word vuoto e aggiungi un pulsante ActiveX in C#
schemas:
- author: Aspose
  dateModified: '2026-10-23'
  description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  headline: Create a blank Word document and add an ActiveX button in C#
  type: TechArticle
- description: Create blank Word document with C# and learn how to insert ActiveX
    controls, including a button, using Aspose.Words.
  name: Create a blank Word document and add an ActiveX button in C#
  steps:
  - name: Instantiate a `Document`.
    text: Instantiate a `Document`.
  - name: Use `DocumentBuilder` to work with the file.
    text: Use `DocumentBuilder` to work with the file.
  - name: Call `InsertForms2OleControl` to **how to insert activex** controls.
    text: Call `InsertForms2OleControl` to **how to insert activex** controls.
  - name: Configure the control’s properties (**create activex control**).
    text: Configure the control’s properties (**create activex control**).
  - name: Save the file, yielding a **word document activex button** ready for VBA
      integration.
    text: Save the file, yielding a **word document activex button** ready for VBA
      integration.
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
title: Crea un documento Word vuoto e aggiungi un pulsante ActiveX in C#
url: /it/java/document-manipulation/create-a-blank-word-document-and-add-an-activex-button-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea un documento Word vuoto e aggiungi un pulsante ActiveX in C#

Se hai bisogno di **creare un documento Word vuoto** programmaticamente, questa guida ti mostra esattamente come. Vedrai un esempio completo e eseguibile che crea un nuovo documento, inserisce un ActiveX CommandButton e salva il file—tutto con Aspose.Words per .NET.

Aggiungere un **ActiveX button** ti consente di incorporare funzionalità interattive che possono essere utilizzate in modelli abilitati alle macro o soluzioni solo per Windows. Alla fine di questo tutorial sarai in grado di inserire qualsiasi controllo ActiveX, ma ci concentreremo sullo scenario più comune: un **word document activex button** che invia un modulo.

## Prerequisiti

* .NET 6.0 o versioni successive (il codice funziona anche con .NET Framework 4.7+)
* Visual Studio 2022 (o qualsiasi IDE C#)
* **Aspose.Words for .NET** Pacchetto NuGet  
  ```bash
  dotnet add package Aspose.Words
  ```
* Familiarità di base con la sintassi C#

> **Consiglio professionale:** Aspose.Words è una libreria commerciale, ma offre una licenza temporanea gratuita per i test. Installa la licenza subito per evitare la filigrana di valutazione.

## Passo 1: Crea un documento Word vuoto con Aspose.Words

Il primo passo è istanziare un oggetto `Document`. Questo rappresenta un file `.docx` vuoto in memoria.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Create a new blank document
Document document = new Document();
```

`Document` inizia senza sezioni, pagine o contenuti. È la tela pulita di cui hai bisogno per scenari di **creare un documento Word vuoto** come la generazione di report da zero.

## Passo 2: Ottieni un DocumentBuilder per modificare il documento

`DocumentBuilder` fornisce un'API comoda per aggiungere testo, immagini e controlli. Lo utilizzeremo per posizionare il controllo ActiveX.

```csharp
// Obtain a DocumentBuilder tied to the blank document
DocumentBuilder builder = new DocumentBuilder(document);
```

Il builder aggiunge automaticamente una sezione predefinita e una prima pagina, così puoi iniziare a inserire oggetti subito.

## Passo 3: Come inserire controlli ActiveX nel documento

Aspose.Words espone `InsertForms2OleControl` per incorporare oggetti OLE/ActiveX. Il metodo richiede il tipo di controllo, larghezza e altezza (in punti). Di seguito inseriamo un **CommandButton**—il classico pulsante di modulo che trovi nei modelli Word legacy.

```csharp
// Insert an ActiveX CommandButton control (100 × 30 points)
Forms2OleControl commandButton = builder.InsertForms2OleControl(
    Forms2OleControlType.COMMANDBUTTON, 100, 30);
```

> **Perché funziona:** `Forms2OleControlType.COMMANDBUTTON` indica a Word di creare un pulsante che può rispondere agli eventi di click quando il documento è aperto in un ambiente Windows che supporta ActiveX.

## Passo 4: Crea un controllo ActiveX – imposta le sue proprietà

Ora diamo al pulsante un nome programmatico e una didascalia visibile. Questa è la parte di **creare un controllo activex** che gli sviluppatori spesso trascurano.

```csharp
// Set the button's name (used in VBA) and the text shown to users
commandButton.Name = "btnSubmit";
commandButton.Caption = "Submit";
```

* `Name` è l'identificatore che utilizzerai nei macro VBA (`ActiveDocument.InlineShapes("btnSubmit")`).
* `Caption` è l'etichetta visualizzata sul pulsante stesso.

## Passo 5: Salva il documento Word con il pulsante ActiveX

Infine, scrivi il documento su disco. L'estensione del file deve essere `.docx` (o `.docm` se prevedi di aggiungere macro in seguito). L'esempio salva in una cartella segnaposto—sostituiscila con il tuo percorso.

```csharp
// Save the document containing the ActiveX button
string outputPath = @"C:\Temp\ActiveXButton.docx";
document.Save(outputPath);
Console.WriteLine($"Document saved to {outputPath}");
```

Quando apri il file risultante in Microsoft Word (solo Windows), vedrai un **word document activex button** funzionale che può essere collegato al codice VBA.

## Esempio completo funzionante

Di seguito trovi il programma completo che puoi copiare‑incollare in un nuovo progetto console.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing;

namespace ActiveXButtonDemo
{
    class Program
    {
        static void Main()
        {
            // 1. Create a blank Word document
            Document document = new Document();

            // 2. Get a builder to edit the document
            DocumentBuilder builder = new DocumentBuilder(document);

            // 3. Insert an ActiveX CommandButton (100 × 30 points)
            Forms2OleControl commandButton = builder.InsertForms2OleControl(
                Forms2OleControlType.COMMANDBUTTON, 100, 30);

            // 4. Configure the button
            commandButton.Name = "btnSubmit";
            commandButton.Caption = "Submit";

            // 5. Save the file
            string outputPath = @"C:\Temp\ActiveXButton.docx";
            document.Save(outputPath);
            Console.WriteLine($"Document saved to {outputPath}");
        }
    }
}
```

**Output previsto quando esegui il programma**

```
Document saved to C:\Temp\ActiveXButton.docx
```

Apri il file generato `ActiveXButton.docx` in Word e vedrai un pulsante etichettato **Submit** posizionato in cima alla prima pagina.

## Casi limite e problemi comuni

| Situazione | Cosa controllare | Raccomandazione |
|------------|-------------------|-----------------|
| Esecuzione su macOS o Linux | ActiveX è una tecnologia solo per Windows, quindi il pulsante apparirà come segnaposto. | Usa il tutorial solo per modelli destinati a Windows. |
| Documento aperto in Word Online | I controlli ActiveX non sono supportati nella visualizzazione del browser. | Fornisci un'interfaccia di riserva o istruisci gli utenti ad aprire il file nel client desktop. |
| Necessità di un file abilitato alle macro | I file `.docx` non possono contenere codice VBA. | Salva come `.docm` (`document.Save("MyFile.docm", SaveFormat.Docm)`) e aggiungi la macro separatamente. |
| Discrepanza nelle dimensioni del controllo | I valori di larghezza/altezza sono in punti (1 pt ≈ 1/72 in). | Regola i valori numerici per ottenere la dimensione visiva desiderata. |

## Domande frequenti

**Come inserire controlli ActiveX diversi da un pulsante?**  
Usa lo stesso metodo `InsertForms2OleControl` ma passa un valore diverso dell'enumerazione `Forms2OleControlType`, come `COMBOBOX` o `LISTBOX`.

**Posso cambiare il font o il colore del pulsante?**  
L'aspetto del pulsante ActiveX è determinato dall'applicazione host (Word) e dal tema Windows sottostante. Puoi modificare proprietà come `ForeColor` e `BackColor` tramite VBA dopo l'apertura del documento.

**Esiste un modo per aggiungere un gestore di click direttamente da C#?**  
No. L'evento click deve essere gestito da VBA o da un add‑in Word perché il pulsante viene eseguito all'interno del processo di Word, non della tua applicazione .NET.

## Conclusione

Ora sai come **creare un documento Word vuoto** programmaticamente e incorporare un **ActiveX button** usando Aspose.Words per .NET. I passaggi coperti:

1. Istanziare un `Document`.
2. Usare `DocumentBuilder` per lavorare con il file.
3. Chiamare `InsertForms2OleControl` per **come inserire controlli activex**.
4. Configurare le proprietà del controllo (**creare un controllo activex**).
5. Salvare il file, ottenendo un **word document activex button** pronto per l'integrazione VBA.

Da qui puoi esplorare l'aggiunta di altri tipi di controlli, collegare macro VBA o convertire il documento in PDF mantenendo il pulsante (come immagine statica). Sperimenta con diverse dimensioni, didascalie e nomi.

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare ulteriori funzionalità dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Come aggiungere un pulsante ActiveX in un documento Word con Aspose.Words](/words/english/net/working-with-oleobjects-and-activex/how-to-add-activex-button-in-a-word-document-with-aspose-wor/)
- [Crea documento Word con pulsante ActiveX – Guida C#](/words/english/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}