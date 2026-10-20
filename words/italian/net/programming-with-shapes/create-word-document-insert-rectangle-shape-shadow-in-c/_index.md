---
category: general
date: 2026-05-26
description: Crea un documento Word in C# con Aspose.Words, inserisci una forma rettangolare,
  imposta il colore di riempimento e aggiungi l'effetto ombra – guida passo passo.
draft: false
keywords:
- create word document
- insert rectangle shape
- how to add shadow
- how to insert shape
- how to set fill
language: it
og_description: Crea un documento Word in C# usando Aspose.Words. Scopri come inserire
  una forma rettangolare, impostare il colore di riempimento e aggiungere un effetto
  ombra.
og_title: Crea documento Word – Inserisci forma rettangolare e ombra in C#
schemas:
- author: Aspose
  dateModified: '2026-05-26'
  description: Create Word document in C# with Aspose.Words, insert rectangle shape,
    set fill color, and add shadow effect – step‑by‑step guide.
  headline: Create Word Document – Insert Rectangle Shape & Shadow in C#
  type: TechArticle
tags:
- Aspose.Words
- C#
- Word automation
title: Crea documento Word – Inserisci forma rettangolo e ombra in C#
url: /it/net/programming-with-shapes/create-word-document-insert-rectangle-shape-shadow-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word – Inserisci forma rettangolare e ombra in C#

Ti sei mai chiesto come **creare un documento Word** programmaticamente senza aprire prima Microsoft Word? Non sei l'unico. In molti scenari di automazione—pensiamo a fatture, contratti o generazione di report in massa—hai bisogno di un modo affidabile per generare un file .docx, inserire una forma al suo interno, darle un colore e magari anche un'ombra per un aspetto più curato.

In questo tutorial vedremo esattamente questo: utilizzare Aspose.Words per .NET per **creare un documento Word**, **inserire una forma rettangolare**, applicare un riempimento e **aggiungere un'ombra**. Alla fine avrai un file pronto da salvare che potrai inserire in qualsiasi flusso di lavoro successivo.  

Tratteremo anche **come inserire una forma** in modo flessibile e perché **come impostare il riempimento** è importante per la coerenza visiva. Niente superfluo, solo il codice che puoi copiare‑incollare e far funzionare.

## Prerequisiti

Prima di iniziare, assicurati di avere:

- .NET 6+ (o .NET Framework 4.7+) installato.  
- Una licenza valida di Aspose.Words per .NET (o una chiave di valutazione temporanea).  
- Visual Studio, Rider o qualsiasi IDE C# a tua scelta.  
- Familiarità di base con la sintassi C#—nulla di complicato.

Hai tutto? Ottimo, cominciamo.

## Passo 1 – Crea documento Word

La prima cosa di cui hai bisogno è un oggetto documento vuoto. Questa è la tela su cui vivrà tutto il resto.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

// Step 1: Create a new blank document and a DocumentBuilder.
Document doc = new Document();                 // The document itself.
DocumentBuilder builder = new DocumentBuilder(doc); // Helper to add content.
```

`Document` rappresenta il file .docx in memoria, mentre `DocumentBuilder` fornisce un'API comoda per inserire testo, tabelle e forme. **Creare il documento Word** in questo modo è immediato—senza UI, senza interop COM, solo puro .NET.

## Passo 2 – Inserisci forma rettangolare

Ora che abbiamo un documento, **inseriamo una forma rettangolare**. Il metodo `InsertShape` accetta un enum `ShapeType`, larghezza e altezza (in punti). Useremo un rettangolo di 150 × 80 punti, che corrisponde approssimativamente a 2 × 1 pollice.

```csharp
// Step 2: Insert a rectangle shape of the desired size.
Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);
```

Dietro le quinte, Aspose crea un oggetto `Shape`, lo aggiunge al paragrafo corrente e restituisce un riferimento che puoi stilizzare. Questo è il nucleo di **come inserire una forma**—una sola riga di codice, ma incredibilmente potente.

## Passo 3 – Come impostare il riempimento

Una forma senza riempimento è invisibile su una pagina bianca. Diamo quindi un gradevole sfondo azzurro chiaro.

```csharp
// Step 3: Apply a fill color to make the shape visible.
shape.FillColor = System.Drawing.Color.LightBlue; // Any System.Drawing.Color works.
```

Puoi anche usare gradienti, texture o addirittura un riempimento immagine, ma un colore solido mantiene l'esempio semplice. Questo dimostra **come impostare il riempimento** su qualsiasi forma tu crei, garantendo il segnale visivo che i lettori si aspettano.

## Passo 4 – Come aggiungere l'ombra

Le ombre aggiungono profondità e fanno risaltare la forma. Aspose.Words espone un oggetto `ShadowFormat` dove puoi attivare la visibilità, scegliere un colore e regolare sfocatura, distanza e angolo.

```csharp
// Step 4: Configure the shadow effect – enable it, set color, blur, distance and angle.
shape.ShadowFormat.Visible = true;                     // Turn the shadow on.
shape.ShadowFormat.Color = System.Drawing.Color.Gray; // Shadow color.
shape.ShadowFormat.BlurRadius = 4.0;                  // Softness in pixels.
shape.ShadowFormat.Distance = 3.0;                    // How far the shadow is offset.
shape.ShadowFormat.Angle = 45;                        // Direction of the offset (degrees).
```

Perché questi valori in particolare? Un angolo di 45° fornisce una sorgente luminosa naturale dall'alto‑destra, una sfocatura moderata mantiene l'ombra discreta e una breve distanza impedisce alla forma di apparire staccata. Sentiti libero di sperimentare—cambiando l'angolo a 135° l'ombra cadrà verso il basso‑sinistra, ad esempio.

## Passo 5 – Salva il documento

Il lavoro è finito; ora scriviamo il file su disco. Scegli qualsiasi percorso ti piaccia; assicurati solo che la cartella esista.

```csharp
// Step 5: Save the document with the shaped shadow.
doc.Save("YOUR_DIRECTORY/ShadowShape.docx");
```

Quando apri `ShadowShape.docx` in Microsoft Word, vedrai un rettangolo azzurro chiaro con un'ombra grigia morbida—esattamente ciò che abbiamo programmato.

## Esempio completo funzionante

Mettendo tutto insieme, ecco il programma completo, pronto per il copia‑incolla:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;

class Program
{
    static void Main()
    {
        // 1️⃣ Create a new blank document.
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);

        // 2️⃣ Insert a rectangle shape (150 × 80 points).
        Shape shape = builder.InsertShape(ShapeType.Rectangle, 150, 80);

        // 3️⃣ Set a solid fill color so the shape is visible.
        shape.FillColor = System.Drawing.Color.LightBlue;

        // 4️⃣ Add a subtle shadow for depth.
        shape.ShadowFormat.Visible = true;
        shape.ShadowFormat.Color = System.Drawing.Color.Gray;
        shape.ShadowFormat.BlurRadius = 4.0;   // pixels
        shape.ShadowFormat.Distance = 3.0;     // pixels
        shape.ShadowFormat.Angle = 45;        // degrees

        // 5️⃣ Persist the document.
        doc.Save("ShadowShape.docx");
    }
}
```

### Risultato atteso

- Un file chiamato **ShadowShape.docx** appare nella cartella di destinazione.  
- Aprendolo in Word, viene mostrato un rettangolo azzurro chiaro centrato nella prima pagina.  
- Il rettangolo proietta un'ombra grigia a 45°, creando un sottile effetto 3‑D.

## Domande frequenti & casi particolari

**E se avessi bisogno di una forma diversa?**  
Sostituisci `ShapeType.Rectangle` con qualsiasi altro valore enum (`Ellipse`, `Star`, `Arrow`, ecc.). Il resto del codice rimane invariato.

**Posso aggiungere testo all'interno della forma?**  
Sì—dopo aver creato la forma, chiama `shape.AppendChild(new Paragraph(doc))` e poi inserisci un `Run` con il tuo testo. Ricorda di impostare le proprietà `shape.TextBox` se desideri il wrapping.

**Cosa riguarda DPI o unità di misura?**  
Aspose lavora in punti (1 pt = 1/72 pollice). Se preferisci i centimetri, moltiplica per 28,35 (poiché 1 cm ≈ 28,35 pt).

**È necessaria una licenza per far funzionare tutto?**  
La versione di valutazione aggiunge una filigrana nella prima pagina. Una licenza valida la rimuove e sblocca l'intera API.

## Suggerimenti & avvertenze

- **Pro tip:** Chiama `builder.MoveToDocumentEnd()` prima di inserire una forma se vuoi posizionarla alla fine del documento.  
- **Attenzione a:** Salvare in una cartella di sola lettura genererà un `UnauthorizedAccessException`. Assicurati che l'app abbia i permessi di scrittura.  
- **Nota sulle prestazioni:** Per generazione di massa (centinaia di documenti), riutilizza un'unica istanza `Document` come modello e clona con `doc.Clone(true)` per evitare l'overhead di inizializzazioni ripetute.

## Conclusione

Ora sai come **creare un documento Word**, **inserire una forma rettangolare**, **impostare il riempimento** e **aggiungere un'ombra** usando Aspose.Words per .NET. Lo snippet sopra è una soluzione autonoma che puoi inserire in qualsiasi progetto C#, sia esso un'app console, un'API web o un servizio in background.

Da qui potresti esplorare:

- Aggiungere più forme con colori diversi.  
- Usare gradienti o riempimenti immagine (`shape.FillColor = ...` → `shape.FillPattern`).  
- Combinare forme con tabelle per layout di report complessi.

Provalo, modifica i parametri e guarda i tuoi file Word automatizzati diventare più professionali con poche righe di codice. Buon coding!

## Tutorial correlati

- [Create rectangle shape in Word using C# – Step‑by‑Step Guide](/words/english/net/programming-with-shapes/create-rectangle-shape-in-word-using-c-step-by-step-guide/)
- [Aspose.Words Shape Shadow Tutorial – Add a Shadow to Word Shape in C#](/words/english/net/programming-with-shapes/aspose-words-shape-shadow-tutorial-add-a-shadow-to-word-shap/)
- [Create Group Shape in Word Document Using Aspose.Words for .NET](/words/english/net/working-with-shapes/add-group-shape/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}