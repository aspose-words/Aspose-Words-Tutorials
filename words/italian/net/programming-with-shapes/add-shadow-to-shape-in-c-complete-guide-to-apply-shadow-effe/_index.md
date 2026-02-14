---
category: general
date: 2026-02-13
description: Aggiungi rapidamente un'ombra alla forma in C#. Scopri come applicare
  l'effetto ombra, cambiare il colore dell'ombra e creare un'ombra a 45 gradi con
  semplici esempi di codice.
draft: false
keywords:
- add shadow to shape
- apply shadow effect
- change shadow color
- 45 degree shadow
- how to add shadow
language: it
og_description: Aggiungi un'ombra alla forma in C# istantaneamente. Questo tutorial
  mostra come applicare l'effetto ombra, cambiare il colore dell'ombra e impostare
  un'ombra a 45 gradi.
og_title: Aggiungi ombra alla forma in C# – Guida passo‑passo all’effetto ombra
tags:
- Aspose.Words
- C#
- Document Automation
title: Aggiungere l'ombra a una forma in C# – Guida completa per applicare l'effetto
  ombra
url: /it/net/programming-with-shapes/add-shadow-to-shape-in-c-complete-guide-to-apply-shadow-effe/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungere ombra a una forma in C# – Guida completa

Ti sei mai chiesto come **aggiungere ombra a una forma** in un documento Word usando C#? Non sei l'unico. Molti sviluppatori si trovano in difficoltà quando hanno bisogno di quella sottile ombra per far risaltare un diagramma, ma non riescono a trovare un esempio conciso e pronto all'uso.  

Buone notizie: questo tutorial ti fornisce il codice esatto di cui hai bisogno per **aggiungere ombra a una forma**, spiega perché ogni riga è importante e ti mostra come modificare l'effetto—che tu voglia una leggera foschia grigia o un'ombra decisa a 45 °. Nel percorso vedremo anche come **applicare l'effetto ombra**, **cambiare il colore dell'ombra** e parleremo dello scenario classico della **ombra a 45 gradi**.

## Cosa imparerai

- Come caricare un DOCX, individuare una forma e abilitare la sua ombra.  
- Il significato di ogni proprietà dell'ombra (visibilità, colore, trasparenza, dimensione, distanza, angolo).  
- Modi per **applicare l'effetto ombra** in modo dinamico, ad esempio iterando su tutte le forme o gestendo oggetti raggruppati.  
- Suggerimenti per **cambiare il colore dell'ombra** in modo sicuro e per gestire documenti privi di forme.  
- Come ottenere una precisa **ombra a 45 gradi** senza indovinare gli angoli.

Nessuna documentazione esterna è necessaria—basta copiare, incollare ed eseguire. Alla fine avrai un programma funzionante che aggiunge un'ombra dall'aspetto professionale a qualsiasi forma.

## Prerequisiti

- .NET 6.0 o versioni successive (il codice funziona anche su .NET Framework 4.7+).  
- Aspose.Words per .NET (versione di prova gratuita o licenziata). Installa via NuGet: `dotnet add package Aspose.Words`.  
- Un file Word di base (`input.docx`) che contenga già almeno una forma (ad esempio un rettangolo o un'immagine).

> **Pro tip:** Se non hai una forma, inseriscine una manualmente in Word prima; il tutorial assume che la prima forma sia il bersaglio.

---

## Passo 1: Configura il progetto e carica il documento

Per prima cosa, crea un'app console (o qualsiasi progetto C#) e aggiungi il riferimento ad Aspose.Words. Quindi carica il DOCX che contiene la forma che desideri migliorare.

```csharp
using System;
using System.Drawing;               // For Color
using Aspose.Words;
using Aspose.Words.Drawing;          // For Shape and ShadowFormat

class Program
{
    static void Main()
    {
        // Load the Word document that contains the shape.
        Document doc = new Document("YOUR_DIRECTORY/input.docx");
```

**Perché è importante:** `Document` è il punto di ingresso per tutte le operazioni di elaborazione di Word. Caricando il file all'inizio, garantisci che ogni operazione successiva lavori sulla corretta rappresentazione in memoria.

---

## Passo 2: Recupera la forma target

Successivamente, individua la forma che intendi modificare. L'esempio prende la prima forma, ma puoi regolare l'indice o filtrare per tipo di forma.

```csharp
        // Retrieve the first shape in the document (adjust the index if needed).
        Shape targetShape = (Shape)doc.GetChild(NodeType.Shape, 0, true);
        if (targetShape == null)
        {
            Console.WriteLine("No shape found. Add a shape to input.docx and try again.");
            return;
        }
```

**Spiegazione:**  
- `GetChild(NodeType.Shape, 0, true)` attraversa l'albero del documento in profondità e restituisce la prima forma che incontra.  
- Il controllo sul valore null evita una `NullReferenceException` quando il documento non contiene forme—un caso limite comune per i principianti.

---

## Passo 3: Attiva l'ombra

L'ombra di una forma è disabilitata per impostazione predefinita. Attivarla è semplice come impostare un flag booleano.

```csharp
        // Turn on the shadow effect for the shape.
        targetShape.ShadowFormat.Visible = true;
```

**Cosa succede:** Impostare `Visible` a `true` indica a Word di renderizzare un'ombra. Senza questa riga, qualsiasi altra impostazione dell'ombra verrebbe ignorata.

---

## Passo 4: Configura l'aspetto dell'ombra

Ora definiamo l'aspetto dell'ombra. Il codice qui sotto corrisponde allo stile tipico “nero, 30 % trasparente, sfocatura 5 pt, offset 3 pt, angolo 45°”.

```csharp
        // Configure the shadow's appearance.
        // • Black color
        // • 30 % transparent
        // • 5 pt blur radius (size)
        // • 3 pt offset distance
        // • 45° direction (angle)
        targetShape.ShadowFormat.Color = Color.Black;          // change shadow color
        targetShape.ShadowFormat.Transparency = 0.3;           // 30 % transparent
        targetShape.ShadowFormat.Size = 5;                     // blur radius
        targetShape.ShadowFormat.Distance = 3;                 // offset distance
        targetShape.ShadowFormat.Angle = 45;                   // 45 degree shadow
```

**Perché ogni proprietà è importante:**

| Proprietà | Effetto | Uso tipico |
|----------|--------|-------------|
| `Visible` | Attiva/disattiva l'ombra | Fondamentale per **applicare l'effetto ombra** |
| `Color` | Determina la tonalità dell'ombra | Cambia in grigio per discrezione, rosso per enfasi |
| `Transparency` | 0 = opaco, 1 = totalmente trasparente | 0.3 offre un aspetto morbido e realistico |
| `Size` | Controlla il raggio di sfocatura (in punti) | Valori più alti creano un effetto “sfumato” |
| `Distance` | Distanza dell'ombra dalla forma | Distanze ridotte mantengono la forma ancorata |
| `Angle` | Direzione in gradi (0 = destra, 90 = su) | 45 produce la classica ombra diagonale |

Sentiti libero di sperimentare—ad esempio, imposta `Color = Color.Gray` per **cambiare il colore dell'ombra** a una tonalità più chiara, oppure usa `Angle = 135` per un'ombra che cade verso il basso‑sinistra.

---

## Passo 5: Salva il documento modificato

Infine, scrivi le modifiche su disco. Puoi sovrascrivere l'originale o creare un nuovo file.

```csharp
        // Save the document with the new shadow.
        doc.Save("YOUR_DIRECTORY/output_with_shadow.docx");
        Console.WriteLine("Shadow added successfully! Check output_with_shadow.docx");
    }
}
```

**Risultato:** Apri `output_with_shadow.docx` in Word, seleziona la forma e vedrai un'ombra nera nitida a 45 ° di angolo, 30 % trasparente, con una morbida sfocatura. Il risultato visivo è identico a quello che otterresti applicando manualmente un'ombra tramite l'interfaccia di Word.

---

## Bonus: Applica l'ombra a tutte le forme del documento

Se devi **applicare l'effetto ombra** a ogni forma, itera sulla collezione invece di puntare a un singolo nodo.

```csharp
        // Loop through every shape and add the same shadow.
        NodeCollection shapes = doc.GetChildNodes(NodeType.Shape, true);
        foreach (Shape shp in shapes)
        {
            shp.ShadowFormat.Visible = true;
            shp.ShadowFormat.Color = Color.Black;
            shp.ShadowFormat.Transparency = 0.3;
            shp.ShadowFormat.Size = 5;
            shp.ShadowFormat.Distance = 3;
            shp.ShadowFormat.Angle = 45;
        }
```

**Gestione dei casi limite:** Alcune forme (ad esempio WordArt) potrebbero ignorare certe proprietà. Testa sempre su un campione rappresentativo.

---

## Conferma visiva

Di seguito è mostrato uno screenshot della forma dopo l'applicazione dell'ombra. Nota l'offset pulito di 45 ° e la leggera trasparenza.

![esempio di aggiunta ombra alla forma](add-shadow-to-shape.png){: .img alt="esempio di aggiunta ombra alla forma"}

---

## Domande frequenti

**D: Posso usare un gradiente di colore personalizzato per l'ombra?**  
R: Aspose.Words supporta solo colori solidi per `ShadowFormat.Color`. Per i gradienti, dovresti esportare la forma come immagine e applicare un effetto grafico.

**D: Cosa succede se il documento contiene forme raggruppate?**  
R: Ogni membro di un gruppo è un nodo `Shape` separato. Il ciclo mostrato nella sezione “Bonus” li gestirà automaticamente.

**D: Funziona con file Word 2007‑2019?**  
R: Sì. Aspose.Words astrae il formato del file, quindi lo stesso codice funziona per `.doc`, `.docx` e anche `.rtf`.

**D: Come rendo nuovamente invisibile l'ombra?**  
R: Imposta `targetShape.ShadowFormat.Visible = false;` e salva nuovamente il documento.

---

## Conclusione

Ora sai esattamente come **aggiungere ombra a una forma** in C#. Attivando `ShadowFormat.Visible` e regolando colore, trasparenza, dimensione, distanza e angolo, puoi **applicare l'effetto ombra** che corrisponde a qualsiasi specifica di design—including una precisa **ombra a 45 gradi**.  

Che tu stia automatizzando la generazione di report, costruendo un motore di template o semplicemente rifinendo un singolo diagramma, questo approccio ti offre il pieno controllo programmatico sulla profondità visiva di una forma. Prova ora a **cambiare il colore dell'ombra** in base a un tema, o combina questa logica con il riempimento della forma per creare visualizzazioni dinamiche guidate dai dati.

Buona programmazione, e non esitare a sperimentare—le ombre sono facili da aggiungere ma possono migliorare drasticamente la leggibilità. Se questa guida ti è stata utile, condividila con i colleghi o lascia un commento con le tue personalizzazioni!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}