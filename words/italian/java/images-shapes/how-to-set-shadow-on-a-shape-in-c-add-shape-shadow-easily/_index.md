---
category: general
date: 2026-04-28
description: Come impostare rapidamente l'ombra su una forma. Scopri come aggiungere
  l'ombra alla forma, impostare il colore dell'ombra e personalizzare l'ombra della
  forma con Aspose.Words per .NET.
draft: false
keywords:
- how to set shadow
- add shape shadow
- set shadow color
- how to add shadow
- customize shape shadow
language: it
og_description: Come impostare l'ombra su una forma in C# con Aspose.Words. Guida
  passo passo su come aggiungere l'ombra alla forma, impostare il colore dell'ombra
  e personalizzare l'ombra della forma.
og_title: Come impostare l'ombra su una forma in C# – Guida completa
tags:
- Aspose.Words
- C#
- Document Automation
title: Come impostare l'ombra su una forma in C# – Aggiungi facilmente l'ombra alla
  forma
url: /it/java/images-shapes/how-to-set-shadow-on-a-shape-in-c-add-shape-shadow-easily/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare l'ombra su una forma in C# – Aggiungi facilmente l'ombra alla forma

Ti sei mai chiesto **come impostare l'ombra** su una forma senza scavare tra infinite documentazioni API? Non sei solo. Molti sviluppatori si trovano in difficoltà quando hanno bisogno di un'ombra leggera per far risaltare un diagramma, ma non riescono a trovare un esempio chiaro che mostri *entrambi* il “cosa” e il “perché”.  

In questo tutorial vedremo come aggiungere un'ombra a una forma, cambiare il colore dell'ombra e perfezionare la sfocatura, lo spostamento e la trasparenza—tutto usando Aspose.Words per .NET. Alla fine avrai uno snippet pronto all'uso da inserire in qualsiasi progetto C#, più una serie di consigli per personalizzare l'ombra della forma in scenari più complessi.

> **Nota:** Il codice funziona con Aspose.Words 22.9 o versioni successive e richiede .NET 6+ (o .NET Framework 4.7.2+).  

![Shape with custom shadow](shape-shadow.png "Shape with custom shadow")

## Cosa imparerai

- **Aggiungere l'ombra alla forma** programmaticamente alla prima forma in un documento Word.  
- **Impostare il colore dell'ombra** a qualsiasi `System.Drawing.Color`.  
- **Personalizzare l'ombra della forma** regolando il raggio di sfocatura, gli spostamenti e la trasparenza.  
- Come gestire più forme e ripristinare le impostazioni dell'ombra se necessario.  

Nessuno strumento esterno, nessuna macro Visual Basic—solo puro C#.

---

## Prerequisiti

| Requisito | Perché è importante |
|-------------|----------------|
| **Aspose.Words for .NET** (pacchetto NuGet `Aspose.Words`) | Fornisce le classi `Document`, `Shape` e `ShadowFormat` utilizzate nell'esempio. |
| **.NET 6 SDK** (o .NET Framework 4.7.2) | Garantisce la compatibilità con l'ultima superficie API. |
| **Un file .docx** con almeno una forma (ad es. un rettangolo o un'immagine) | Il tutorial manipola la *prima* forma; puoi crearne una in Word se non ne hai già una. |

Installa la libreria con:

```bash
dotnet add package Aspose.Words
```

---

## Passo‑per‑passo: Come impostare l'ombra su una forma

### 1. Carica il documento Word

Iniziamo aprendo il file `.docx`. Il costruttore `Document` legge il file in memoria, offrendoci pieno accesso ai suoi nodi.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

// Load the source document
Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

> **Perché?** Caricare il documento è la base—senza di esso non puoi attraversare l'albero delle forme.

### 2. Recupera la prima forma (o qualsiasi forma ti serva)

Aspose.Words memorizza le forme come nodi di tipo `NodeType.SHAPE`. Il metodo `GetChild` consente di ottenere la forma *n‑esima*; qui prendiamo l'indice 0, cioè la prima forma.

```csharp
// Grab the first shape in the document (depth‑first search)
Shape firstShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
if (firstShape == null)
{
    throw new InvalidOperationException("No shape found in the document.");
}
```

> **Suggerimento professionale:** Se devi **aggiungere l'ombra alla forma** a una forma specifica, sostituisci l'indice con il valore appropriato o itera attraverso `doc.GetChildNodes(NodeType.Shape, true)`.

### 3. Accedi all'oggetto di formattazione dell'ombra

Ogni `Shape` ha una proprietà `ShadowFormat` che espone tutte le impostazioni relative all'ombra.

```csharp
ShadowFormat shadow = firstShape.ShadowFormat;
```

Ora possiamo iniziare a modificare l'ombra.

### 4. Imposta il raggio di sfocatura – ammorbidire i bordi

Un raggio di sfocatura più grande rende l'ombra più diffusa. Il valore è espresso in punti (1 pt ≈ 1/72 pollice).

```csharp
shadow.BlurRadius = 5.0; // 5 pt blur – looks nicely soft
```

> **Quando regolare?** Se la tua forma è piccola, una sfocatura di 2–3 pt può bastare; per banner grandi, aumentala a 8–10 pt.

### 5. Definisci gli spostamenti orizzontale e verticale

Gli offset controllano quanto l'ombra è spostata dalla forma. Valori positivi spostano l'ombra a destra/giù; valori negativi la spostano a sinistra/su.

```csharp
shadow.DistanceX = 3.0; // 3 pt to the right
shadow.DistanceY = 3.0; // 3 pt downwards
```

### 6. Regola la trasparenza (opacità)

`Transparency` varia da `0.0` (completamente opaco) a `1.0` (completamente invisibile). Un valore intorno a `0.3` offre un aspetto sottile e semi‑trasparente.

```csharp
shadow.Transparency = 0.3; // 30 % transparent
```

### 7. Scegli un colore per l'ombra – **imposta il colore dell'ombra** a qualsiasi `System.Drawing.Color`

Puoi scegliere qualsiasi colore predefinito o crearne uno personalizzato con valori RGB.

```csharp
shadow.Color = Color.FromArgb(0, 120, 215); // A calm blue shade
```

Se preferisci un'ombra nera classica, usa semplicemente `Color.Black`.

### 8. Salva il documento modificato

Infine, persisti le modifiche. Puoi sovrascrivere il file originale o scrivere in una nuova posizione.

```csharp
doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
```

---

## Esempio completo funzionante (tutti i passaggi in un unico blocco)

Copia‑incolla il seguente codice nel metodo `Main` di un'app console. Compila così com'è, a patto che il pacchetto NuGet sia installato.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using System.Drawing;

class Program
{
    static void Main()
    {
        // 1. Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/input.docx");

        // 2. Retrieve the first shape (add shape shadow)
        Shape shape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (shape == null)
        {
            System.Console.WriteLine("No shape found – aborting.");
            return;
        }

        // 3. Get the shadow formatting object
        ShadowFormat shadow = shape.ShadowFormat;

        // 4. Set blur radius
        shadow.BlurRadius = 5.0;

        // 5. Define offsets
        shadow.DistanceX = 3.0;
        shadow.DistanceY = 3.0;

        // 6. Adjust transparency (0 = opaque, 1 = fully transparent)
        shadow.Transparency = 0.3;

        // 7. Set shadow color (set shadow color)
        shadow.Color = Color.GetBlue(); // or any custom color

        // 8. Save the result
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");

        System.Console.WriteLine("Shadow applied successfully!");
    }
}
```

**Risultato atteso:** Apri `output_with_shadow.docx` in Word; la prima forma ora mostra un'ombra blu soffusa, spostata di 3 pt, con una leggera sfocatura e il 30 % di trasparenza.

---

## Varianti comuni e casi particolari

### Aggiungere ombre a *tutte* le forme

Se il tuo documento contiene diversi diagrammi, potresti voler iterare su ogni forma:

```csharp
NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
foreach (Shape s in shapes)
{
    ShadowFormat sf = s.ShadowFormat;
    sf.BlurRadius = 4.0;
    sf.DistanceX = 2.0;
    sf.DistanceY = 2.0;
    sf.Transparency = 0.25;
    sf.Color = Color.Gray;
}
```

### Ripristinare un'ombra

A volte una forma ha già un'ombra che devi rimuovere. Imposta `ShadowFormat.Visible` su `false`:

```csharp
shape.ShadowFormat.Visible = false;
```

### Usare un colore personalizzato con alfa (semi‑trasparente)

```csharp
shadow.Color = Color.FromArgb(128, 255, 0, 0); // 50 % transparent red
```

### Nota di compatibilità

L'API `ShadowFormat` è stabile tra le versioni di Aspose.Words, ma le versioni più vecchie (< 19.1) usavano campi `ShadowFormat` con convenzioni di denominazione leggermente diverse. Punta sempre all'ultimo pacchetto NuGet per i migliori risultati.

---

## Consigli professionali per un'ombra perfetta

- **Equilibra sfocatura e offset:** Una sfocatura intensa con un offset minimo può apparire “luminoso” anziché una vera ombra a caduta. Sperimenta con `BlurRadius` × `DistanceX/Y`.
- **Abbina il tema del documento:** Se il file Word utilizza un tema scuro, un'ombra chiara (`Color.White`) può creare un effetto di lieve sollevamento.
- **Prestazioni:** Modificare le ombre su centinaia di forme può aggiungere qualche millisecondo per forma. Raggruppa l'operazione se elabori report di grandi dimensioni.
- **Test:** Apri il `.docx` risultante sia in Word desktop sia in Word Online per assicurarti che l'ombra venga resa in modo coerente.

---

## Conclusione

Abbiamo appena coperto **come impostare l'ombra** su una forma usando C#. Seguendo gli otto passaggi sopra potrai **aggiungere l'ombra alla forma**, **impostare il colore dell'ombra** e **personalizzare completamente l'ombra della forma** per adattarla a qualsiasi linguaggio di design. L'esempio è autonomo, funziona subito e ti fornisce una solida base per estendere la logica a più forme, colori dinamici o parametri definiti dall'utente.

Pronto per la prossima sfida? Prova a combinare questa tecnica con la **rotazione della forma**, o genera un intero report dove ogni grafico ottiene la propria ombra brandizzata. Le possibilità sono infinite, e il codice che hai appena appreso è un ottimo trampolino di lancio.

Se questa guida ti è stata utile, sentiti libero di mettere una stella al repository, lasciare un commento o condividere i tuoi trucchi per la regolazione delle ombre qui sotto. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}