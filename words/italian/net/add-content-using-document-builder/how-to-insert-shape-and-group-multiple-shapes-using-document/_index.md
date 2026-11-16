---
category: general
date: 2026-11-15
description: Scopri come inserire una forma in un documento Word e raggruppare più
  forme con Aspose.Words DocumentBuilder. Include esempi di inserimento di una forma
  rettangolare e di inserimento di più forme.
draft: false
images:
- PLACEHOLDER_URL/og-image.png
keywords:
- how to insert shape
- group multiple shapes
- insert multiple shapes
- insert rectangle shape
language: it
lastmod: 2026-11-15
og_description: Come inserire una forma in un file Word usando Aspose.Words. Questa
  guida copre il raggruppamento di più forme, l'inserimento di una forma rettangolare
  e l'aggiunta efficiente di più forme.
og_image_alt: Screenshot showing how to insert shape and group multiple shapes in
  a Word document using DocumentBuilder
og_title: Come inserire una forma e raggruppare più forme con DocumentBuilder
schemas:
- author: Aspose
  dateModified: '2026-11-15'
  description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  headline: How to insert shape and group multiple shapes using DocumentBuilder in
    C#
  type: TechArticle
- description: Learn how to insert shape in a Word document and group multiple shapes
    with Aspose.Words DocumentBuilder. Includes insert rectangle shape and insert
    multiple shapes examples.
  name: How to insert shape and group multiple shapes using DocumentBuilder in C#
  steps:
  - name: Why use a group?
    text: '* **Single‑point transformation** – rotate or resize the whole group with
      one call. * **Logical organization** – the Word document tree reflects the grouping,
      making later edits easier. * **Consistent layout** – moving the group keeps
      the relative positions of its children intact.'
  - name: Adding more shapes – extending **insert multiple shapes** inside the group
    text: 'You can keep calling `InsertShape` while the cursor remains inside the
      `GroupShape`. For example, to add a triangle:'
  - name: Expected output
    text: '* **First two shapes** – a rectangle and an ellipse placed independently
      on the page. * **Grouped block** – a rectangle, an ellipse, and a triangle that
      move together when you click any of them in Word.'
  type: HowTo
tags:
- Aspose.Words
- C#
- DocumentBuilder
- Shape handling
title: Come inserire una forma e raggruppare più forme usando DocumentBuilder in C#
url: /it/net/add-content-using-document-builder/how-to-insert-shape-and-group-multiple-shapes-using-document/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come inserire forme e raggruppare più forme usando DocumentBuilder in C#

Se hai bisogno di sapere **come inserire forme** in un documento Word con Aspose.Words, questa guida ti mostra i passaggi esatti. Imparerai anche come **raggruppare più forme** in modo che si comportino come un unico oggetto, e come **inserire una forma rettangolare** insieme ad altre grafiche.

L'automazione dei documenti spesso richiede l'aggiunta di diverse grafiche—grafici, loghi, call‑out—mantendole organizzate. Alla fine di questo tutorial sarai in grado di **inserire più forme**, posizionarle all'interno di un gruppo e salvare un layout pulito e riutilizzabile.

## Prerequisiti

Prima di iniziare, assicurati di avere:

* .NET 6.0 o versioni successive installato  
* Visual Studio 2022 (o qualsiasi IDE C#)  
* Una licenza Aspose.Words per .NET o una chiave di valutazione gratuita  
* Familiarità di base con C# e la classe Aspose.Words `DocumentBuilder`  

Non hai **bisogno** di altre librerie di terze parti; tutto il necessario è incluso in Aspose.Words.

## Passo 1: Installa Aspose.Words via NuGet

Apri il tuo progetto in Visual Studio ed esegui il seguente comando nella Console di Gestione Pacchetti:

```powershell
Install-Package Aspose.Words
```

Il pacchetto include le classi `DocumentBuilder`, `Shape` e `GroupShape` utilizzate in tutta questa guida.

## Passo 2: Crea un'istanza di DocumentBuilder – la base per **come inserire forme**

La prima riga di codice operativa è la creazione di un `DocumentBuilder`. Questo oggetto ti dà accesso diretto all'albero del documento, consentendoti di posizionare le forme esattamente dove desideri.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class ShapeDemo
{
    static void Main()
    {
        // Initialise a new blank document
        Document doc = new Document();
        // Create a DocumentBuilder for the document
        DocumentBuilder builder = new DocumentBuilder(doc);

        // The rest of the tutorial inserts and groups shapes here …
    }
}
```

*Perché è importante*: `DocumentBuilder` mantiene un cursore (il “punto di inserimento”). Ogni successiva chiamata `Insert...` utilizza quel cursore, ed è per questo che più tardi lo spostiamo in un `GroupShape` per tenere tutte le forme insieme.

## Passo 3: **Inserire una forma rettangolare** – la prima grafica che aggiungerai

Un rettangolo è un segnaposto comune per tabelle, immagini o call‑out. Usa `InsertShape` con `ShapeType.Rectangle` e specifica larghezza e altezza in punti (1 pt ≈ 1/72 in).

```csharp
// Insert a rectangle shape (width: 100 pt, height: 50 pt)
builder.InsertShape(ShapeType.Rectangle, 100, 50);
```

Il rettangolo appare nella posizione corrente del cursore. Puoi personalizzare il riempimento, lo stile della linea o il testo in seguito, se necessario.

## Passo 4: Inserisci un'altra forma – un'ellisse per varietà visiva

Aggiungere più di una forma dimostra **inserire più forme**. L'ellisse verrà posizionata dopo il rettangolo nel flusso del documento.

```csharp
// Insert an ellipse shape (width: 80 pt, height: 40 pt)
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

A questo punto il documento contiene due forme indipendenti. Se sposti il cursore o aggiungi testo, le forme rimangono dove sono state inserite.

## Passo 5: **Raggruppare più forme** in modo che agiscano come un'unica unità

Il raggruppamento è essenziale quando devi spostare, ruotare o formattare più grafiche insieme. Il codice seguente crea un `GroupShape`, sposta il cursore del builder all'interno di esso, e poi inserisce nuovamente le stesse forme—questa volta diventano figli del gruppo.

```csharp
// 1️⃣ Create a GroupShape and add it to the document tree
GroupShape group = new GroupShape(builder.Document);
builder.InsertNode(group);

// 2️⃣ Position the cursor inside the group so new inserts go into it
builder.MoveTo(group);

// 3️⃣ Insert a rectangle shape inside the group
builder.InsertShape(ShapeType.Rectangle, 100, 50);

// 4️⃣ Insert an ellipse shape inside the same group
builder.InsertShape(ShapeType.Ellipse, 80, 40);
```

### Perché usare un gruppo?

* **Trasformazione a punto singolo** – ruota o ridimensiona l'intero gruppo con una sola chiamata.  
* **Organizzazione logica** – l'albero del documento Word riflette il raggruppamento, rendendo le modifiche successive più facili.  
* **Layout coerente** – spostare il gruppo mantiene intatte le posizioni relative dei suoi figli.

### Aggiungere più forme – estendere **inserire più forme** all'interno del gruppo

Puoi continuare a chiamare `InsertShape` mentre il cursore rimane all'interno del `GroupShape`. Ad esempio, per aggiungere un triangolo:

```csharp
builder.InsertShape(ShapeType.Triangle, 60, 60);
```

Ogni chiamata rispetta il contesto del gruppo, quindi il triangolo diventa automaticamente parte dello stesso insieme raggruppato.

## Passo 6: Salva il documento e verifica il risultato

Dopo che tutte le forme sono state posizionate, salva il documento in un file `.docx`. Aprendo il file in Microsoft Word (o in qualsiasi visualizzatore compatibile) dovrebbero comparire due forme separate seguite da un insieme raggruppato contenente lo stesso rettangolo, ellisse e triangolo.

```csharp
// Save the document
doc.Save("GroupedShapesDemo.docx");
```

### Output previsto

* **Prime due forme** – un rettangolo e un'ellisse posizionati in modo indipendente sulla pagina.  
* **Blocco raggruppato** – un rettangolo, un'ellisse e un triangolo che si muovono insieme quando clicchi su uno di essi in Word.

Puoi testare il raggruppamento selezionando qualsiasi forma all'interno del gruppo; Word evidenzierà l'intera collezione, confermando che l'operazione **raggruppare più forme** è riuscita.

## Problemi comuni e consigli professionali

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| Le forme appaiono fuori dalla pagina prevista | Il cursore del builder non è stato spostato nel `GroupShape` prima dell'inserimento. | Chiama sempre `builder.MoveTo(group)` **prima** di qualsiasi chiamata `InsertShape` che appartiene al gruppo. |
| Il gruppo scompare dopo il salvataggio | Il gruppo è stato inserito senza essere aggiunto alla collezione di nodi del documento. | Usa `builder.InsertNode(group)` subito dopo aver creato il `GroupShape`. |
| Dimensione inattesa a causa della DPI del documento | Aspose.Words utilizza i punti; se pensi in pixel potresti ottenere dimensioni non corrispondenti. | Converti i pixel in punti (`points = pixels * 72 / 96`) o lavora direttamente in punti. |
| Le forme si sovrappongono involontariamente | Non è stata impostata una posizione esplicita; Word le posiziona in sequenza. | Imposta `Shape.Left` e `Shape.Top` dopo l'inserimento per controllare la posizione esatta. |

**Consiglio professionale:** Dopo il raggruppamento, puoi recuperare la collezione `Shapes` del gruppo (`group.Shapes`) per iterare, rinominare o applicare formattazioni di massa.

## Passo 7: Estendere l'esempio – cosa segue?

Ora che conosci **come inserire forme**, **inserire una forma rettangolare** e **raggruppare più forme**, puoi esplorare:

* **Animare forme raggruppate** – impostare proprietà di rotazione o capovolgimento sul gruppo.  
* **Applicare stili** – usa `Shape.FillColor`, `Shape.LineFormat` o `Shape.TextBox` per aggiungere etichette.  
* **Esportare in PDF** – lo stesso layout raggruppato viene renderizzato correttamente quando chiami `doc.Save("output.pdf")`.  

Tutte queste estensioni riutilizzano lo stesso flusso di lavoro `DocumentBuilder`, mantenendo il codice pulito e manutenibile.

## Conclusione

Questo tutorial ha dimostrato **come inserire forme** in un documento Word con Aspose.Words, come **inserire una forma rettangolare** e come **raggruppare più forme** in modo che si comportino come un unico oggetto. Seguendo il codice passo‑passo, puoi inserire in modo affidabile **più forme**, organizzarle in gruppi e produrre documenti di livello professionale in modo programmatico.

Sentiti libero di sperimentare con diversi tipi di forme, colori e trasformazioni di gruppo. Quando sei pronto, integra il modello in soluzioni di reporting o templating più ampie per automatizzare layout di documenti complessi. Buona programmazione!

## Cosa dovresti imparare dopo?

I seguenti tutorial coprono argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi e funzionanti con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive ed esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Inserire forme in documenti Word usando Aspose.Words per .NET](/words/english/net/working-with-shapes/insert-shape/)
- [Come creare e inserire forme ellisse e rettangolo all'interno di un gruppo in un documento Word usando Aspose.Words](/words/english/java/images-shapes/how-to-insert-ellipse-and-rectangle-shapes-inside-a-group-sh/)
- [Come raggruppare forme in un documento Word usando Aspose.Words](/words/english/java/images-shapes/how-to-group-shapes-in-a-word-document-using-aspose-words/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}