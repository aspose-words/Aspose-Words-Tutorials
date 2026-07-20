---
category: general
date: 2026-07-19
description: Crea un documento Word usando Aspose.Words C# e impara come aggiungere
  un pulsante di comando ActiveX, impostare le dimensioni del pulsante e inserire
  il pulsante programmaticamente.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- create word document
- how to add activex
- insert command button
- set button size
- how to insert button
language: it
lastmod: 2026-07-19
og_description: Crea un documento Word con Aspose.Words C# e incorpora un pulsante
  di comando ActiveX in pochi secondi. Segui la guida passo‑passo per impostare le
  dimensioni del pulsante e inserirlo facilmente.
og_image_alt: Screenshot of a Word document showing an ActiveX command button inserted
  via C#
og_title: Crea documento Word con pulsante ActiveX – Tutorial C#
schemas:
- author: Aspose
  dateModified: '2026-07-19'
  description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  headline: Create Word Document with ActiveX Button – C# Guide
  type: TechArticle
- description: Create Word Document using Aspose.Words C# and learn how to add ActiveX
    command button, set button size, and insert button programmatically.
  name: Create Word Document with ActiveX Button – C# Guide
  steps:
  - name: Prerequisites
    text: '- .NET 6.0 or later (the code also works on .NET Framework 4.7+). - A valid
      Aspose.Words for .NET license (or a free evaluation key). - Visual Studio 2022
      (or any IDE you like). - Basic familiarity with C# and object‑oriented programming.'
  - name: Platform Limitations
    text: '- ActiveX controls only run on the Windows version of Word. If your audience
      includes macOS or Word Online users, the button will appear as a static image.
      - Some corporate environments disable ActiveX for security; you may need to
      sign the document or inform users to enable content.'
  - name: VBA Interaction (Optional)
    text: If you want the button to execute a macro, you’ll have to add a VBA project
      to the document after saving. Aspose.Words does not generate VBA code automatically,
      but you can use the `Document.VbaProject` API to inject it.
  - name: Naming Collisions
    text: Always give each control a unique `Name`. Re‑using the same name can cause
      runtime errors when Word tries to resolve the control.
  - name: Performance Tip
    text: When inserting many controls, reuse a single `DocumentBuilder` instance
      and avoid calling `doc.Save` inside a loop. Batch the inserts and save once
      at the end.
  - name: What’s Next?
    text: '- **Style the button** – change fonts, colors, or add an image background.
      - **Attach VBA macros** – make the button perform calculations or launch external
      programs. - **Combine with other controls** – checkboxes, list boxes, or even
      embedded Excel sheets.'
  type: HowTo
tags:
- Aspose.Words
- C#
- ActiveX
- Word automation
title: Creare un documento Word con pulsante ActiveX – Guida C#
url: /it/net/working-with-oleobjects-and-activex/create-word-document-with-activex-button-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con pulsante ActiveX – Guida completa C#

Ti sei mai chiesto come **creare documento Word** che contenga un pulsante ActiveX funzionante? Forse stai automatizzando un report e hai bisogno di un controllo “Approve” cliccabile direttamente nel file. In questo tutorial ti guideremo passo passo—usando Aspose.Words per .NET per aggiungere un pulsante di comando ActiveX, impostarne le dimensioni e inserirlo dove ti serve.  

Se ti sei mai chiesto *come aggiungere activex* controlli senza aprire Word manualmente, sei nel posto giusto. Alla fine avrai un esempio eseguibile, una chiara spiegazione di ogni passaggio e consigli per gestire le difficoltà comuni.

## Cosa imparerai

- Come configurare Aspose.Words in un progetto C#  
- Il codice esatto per **creare documento Word** e incorporare un pulsante di comando ActiveX  
- Modi per **impostare la dimensione del pulsante** e personalizzare la sua didascalia e nome  
- Il metodo corretto per **inserire pulsante di comando** e **come inserire pulsante** in qualsiasi posizione del documento  
- Considerazioni sui casi limite (versione di Word, limiti della piattaforma, avvisi di sicurezza)

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.7+).  
- Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione gratuita).  
- Visual Studio 2022 (o qualsiasi IDE tu preferisca).  
- Familiarità di base con C# e la programmazione orientata agli oggetti.

Nessuna altra libreria di terze parti è necessaria.

---

## Passo 1: Crea documento Word – Configurazione del progetto

Prima di poter **inserire pulsante di comando**, abbiamo bisogno di un file Word vuoto su cui lavorare. Questo passaggio mostra anche il classico modello “creare documento Word” usando Aspose.Words.

```csharp
// Add the Aspose.Words NuGet package first:
//   dotnet add package Aspose.Words
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

// 1️⃣  Initialize a new blank document.
Document doc = new Document();

// 1️⃣  Create a DocumentBuilder – it lets us place content.
DocumentBuilder builder = new DocumentBuilder(doc);
```

> **Perché è importante:** `Document` rappresenta l'intero file .docx, mentre `DocumentBuilder` traccia la posizione corrente del cursore. Tutti gli inserimenti successivi (incluso il nostro controllo ActiveX) avvengono in relazione a questo builder.

---

## Passo 2: Come aggiungere ActiveX – Costruire il controllo CommandButton

Ora che il documento esiste, affrontiamo la parte **come aggiungere activex**. Aspose.Words espone la classe `Forms2OleControl` per gli oggetti ActiveX. Qui creeremo un pulsante di comando e ne configureremo le proprietà, includendo il requisito **impostare la dimensione del pulsante**.

```csharp
// 2️⃣  Create the ActiveX command button.
Forms2OleControl commandButton = new Forms2OleControl(
    doc,                     // Parent document
    Forms2OleControlType.CommandButton); // Control type

// Configure appearance – this is where we **set button size**.
commandButton.Width = 120;          // Width in points (≈1.67 inches)
commandButton.Height = 30;          // Height in points (≈0.42 inches)

// Set the text the user sees.
commandButton.Caption = "Click Me";

// Give the control a unique name for later reference.
commandButton.Name = "cmdButton1";
```

> **Consiglio professionale:** La dimensione è misurata in punti (1 punto = 1/72 di pollice). Regola i valori per adattarli al tuo layout; per un tipico pulsante della barra degli strumenti, 120 × 30 funziona bene.

---

## Passo 3: Inserire pulsante di comando – Il nucleo di **Inserire pulsante di comando**

Con il controllo pronto, ora **inseriamo pulsante di comando** nel documento nella posizione corrente del builder. Puoi spostare il builder ovunque (ad esempio, dopo un paragrafo) prima di chiamare questo metodo.

```csharp
// 3️⃣  Insert the prepared ActiveX control into the document.
builder.InsertForms2OleControl(commandButton);
```

Se devi **come inserire pulsante** in un segnalibro specifico, sposta prima il builder:

```csharp
builder.MoveToBookmark("MyPlace"); // Ensure a bookmark named 'MyPlace' exists
builder.InsertForms2OleControl(commandButton);
```

> **Cosa succede dietro le quinte?** Aspose.Words scrive i flussi di oggetti OLE necessari nel pacchetto .docx, così Word può renderizzare il pulsante senza macro aggiuntive.

---

## Passo 4: Salva il documento – Concludere il ciclo di **creare documento Word**

L'ultimo passaggio è semplice: persistere il file su disco. Questo completa il ciclo di **creare documento Word**, incorporare l'ActiveX e salvare.

```csharp
// 4️⃣  Save the document where you want it.
string outputPath = @"C:\Temp\CommandButton.docx";
doc.Save(outputPath);
```

Apri il file risultante in Microsoft Word (solo Windows). Dovresti vedere un pulsante cliccabile etichettato “Click Me”. Cliccandolo si attiverà l'azione predefinita per un CommandButton—non succede nulla a meno che non colleghi del codice VBA, ma il controllo è pienamente funzionante.

> **Output previsto:** Un file .docx con una singola pagina, un pulsante centrato nel punto di inserimento, dimensionato 120 × 30 pt, etichettato “Click Me”.  
> ![ActiveX button inserted into a Word document](placeholder-image.png)  
> *Testo alternativo dell'immagine:* **Pulsante ActiveX inserito in un documento Word usando C#** (matches `og_image_alt`).

---

## Passo 5: Casi limite, sicurezza e migliori pratiche

### Limitazioni della piattaforma
- I controlli ActiveX funzionano solo nella versione Windows di Word. Se il tuo pubblico include utenti macOS o Word Online, il pulsante apparirà come un'immagine statica.
- Alcuni ambienti aziendali disabilitano ActiveX per motivi di sicurezza; potresti dover firmare il documento o informare gli utenti di abilitare il contenuto.

### Interazione VBA (Opzionale)
Se vuoi che il pulsante esegua una macro, dovrai aggiungere un progetto VBA al documento dopo il salvataggio. Aspose.Words non genera codice VBA automaticamente, ma puoi usare l'API `Document.VbaProject` per iniettarlo.

### Collisioni di nomi
Assegna sempre a ogni controllo un `Name` unico. Riutilizzare lo stesso nome può causare errori di runtime quando Word tenta di risolvere il controllo.

### Suggerimento sulle prestazioni
Quando inserisci molti controlli, riutilizza una singola istanza di `DocumentBuilder` ed evita di chiamare `doc.Save` all'interno di un ciclo. Raggruppa gli inserimenti e salva una sola volta alla fine.

---

## Esempio completo funzionante

Mettendo tutto insieme, ecco un programma completo, pronto per il copia‑incolla:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Drawing.Ole;

class Program
{
    static void Main()
    {
        // Initialize a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // Create and configure the ActiveX command button.
        Forms2OleControl commandButton = new Forms2OleControl(
            doc, Forms2OleControlType.CommandButton);
        commandButton.Width = 120;          // Set button size – width
        commandButton.Height = 30;          // Set button size – height
        commandButton.Caption = "Click Me";
        commandButton.Name = "cmdButton1";

        // Insert the button at the current cursor position.
        builder.InsertForms2OleControl(commandButton);

        // Save the document.
        string outputPath = @"C:\Temp\CommandButton.docx";
        doc.Save(outputPath);

        Console.WriteLine($"Document saved to {outputPath}");
    }
}
```

Esegui il programma, apri il file salvato e vedrai il pulsante esattamente dove il builder era posizionato.

---

## Conclusione

Abbiamo appena **creato documento Word** da zero, imparato **come aggiungere activex** configurando un `Forms2OleControl`, padroneggiato le proprietà **impostare la dimensione del pulsante**, e dimostrato il modo corretto per **inserire pulsante di comando** e **come inserire pulsante** in qualsiasi punto del file.  

Da un unico esempio di codice ora hai una solida base per un'automazione Word più avanzata—che tu stia creando modelli con moduli interattivi, generando contratti che richiedono l'approvazione dell'utente, o semplicemente aggiungendo qualche comodo controllo in un report.

### Cosa c'è dopo?

- **Stilizza il pulsante** – cambia font, colori o aggiungi uno sfondo immagine.  
- **Allega macro VBA** – fai eseguire al pulsante calcoli o avviare programmi esterni.  
- **Combina con altri controlli** – caselle di controllo, elenchi a discesa o anche fogli Excel incorporati.  

Sentiti libero di sperimentare, e se incontri un problema, lascia un commento qui sotto. Buona programmazione e divertiti ad automatizzare Word con Aspose.Words!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell'API ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Crea documento Word con Aspose.Words per .NET](/words/english/net/add-content-using-document-builder/insert-paragraph/)
- [Crea forma di gruppo in documento Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/add-group-shape/)
- [Inserisci immagine inline in documento Word usando Aspose.Words](/words/english/net/add-content-using-document-builder/insert-inline-image/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}