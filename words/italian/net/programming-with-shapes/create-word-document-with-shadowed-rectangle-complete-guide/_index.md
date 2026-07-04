---
category: general
date: 2026-04-21
description: Crea un documento Word con un rettangolo stilizzato e ombra. Scopri come
  aggiungere l'ombra, inserire una forma rettangolare, impostare il colore dell'ombra
  e molto altro in C#.
draft: false
keywords:
- create word document
- how to add shadow
- insert rectangle shape
- create rectangle in word
- set shadow color
language: it
og_description: Crea un documento Word e aggiungi una forma rettangolare con ombra
  in C#. Segui questa guida per impostare facilmente il colore dell'ombra, la sfocatura
  e gli offset.
og_title: Crea un documento Word con rettangolo ombreggiato – Passo dopo passo
tags:
- Aspose.Words
- C#
- Document Automation
title: Crea documento Word con rettangolo ombreggiato – Guida completa
url: /it/net/programming-with-shapes/create-word-document-with-shadowed-rectangle-complete-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con rettangolo ombreggiato – Guida completa

Ti è mai capitato di dover **create word document** che abbia un aspetto più curato rispetto a una semplice pagina di testo? Forse stai creando un modello di report o un volantino e un semplice rettangolo con un'ombra delicata farebbe al caso tuo. In questo tutorial ti guideremo passo passo—come inserire una forma rettangolare, attivare l'ombra e personalizzarne colore, sfocatura e spostamenti—tutto con C# e Aspose.Words.

Tratteremo anche **how to add shadow** in modo che funzioni sia per Word 2016, 2019, sia per l'ultima versione di Office 365. Alla fine avrai un file *.docx* pronto da salvare che mostra un rettangolo ben ombreggiato, e comprenderai il “perché” di ogni proprietà impostata.

## Prerequisiti

- .NET 6 (o qualsiasi versione recente di .NET Framework)  
- Pacchetto NuGet Aspose.Words per .NET (`Install-Package Aspose.Words`)  
- Familiarità di base con la sintassi C#  
- Un IDE come Visual Studio (ma qualsiasi editor va bene)

Non sono necessarie librerie aggiuntive; tutto il resto è incluso in Aspose.Words.

## Passo 1 – Inizializza il Document e il Builder (Create Word Document)

Per **create word document** programmaticamente inizi con la classe `Document`. Il `DocumentBuilder` è il tuo pennello; ti permette di aggiungere testo, forme e altri elementi.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;

class ShadowRectangleDemo
{
    static void Main()
    {
        // Step 1: Create a new blank document and a builder to edit it
        Document document = new Document();
        DocumentBuilder builder = new DocumentBuilder(document);
```

*Perché è importante:* L'oggetto `Document` rappresenta l'intero file .docx. Senza di esso non hai dove collegare il rettangolo o la sua ombra.

## Passo 2 – Inserisci una forma rettangolare (Insert Rectangle Shape)

Ora inseriamo effettivamente **insert rectangle shape**. Il metodo `InsertShape` accetta un enum `ShapeType`, oltre alla larghezza e all'altezza in punti.

```csharp
        // Step 2: Insert a rectangle shape of the desired size (200x100 points)
        Shape rectangle = builder.InsertShape(ShapeType.Rectangle, 200, 100);
```

*Consiglio:* 1 punto ≈ 1/72 pollice, quindi 200 pts corrispondono a circa 2,78 pollici di larghezza. Regola questi valori per adattarli al tuo layout.

## Passo 3 – Abilita l'ombra (How to Add Shadow)

Le ombre sono disabilitate per impostazione predefinita. Imposta il flag `Visible` su true per attivarla.

```csharp
        // Step 3: Turn on the shadow for the shape
        rectangle.ShadowFormat.Visible = true;
```

*Cosa succede?* Quando `Visible` è true, Word renderà un'ombra a caduta basata sulle altre proprietà che imposterai successivamente.

## Passo 4 – Personalizza l'aspetto dell'ombra (Set Shadow Color, Blur, Offsets)

Qui è dove **set shadow color**, il raggio di sfocatura e gli offset X/Y. Sentiti libero di sperimentare—valori diversi ti daranno un bagliore morbido, una caduta profonda o persino un effetto “fluttuante”.

```csharp
        // Step 4: Define the shadow appearance – colour, blur radius and offsets
        rectangle.ShadowFormat.Color = Color.Gray;   // shadow colour
        rectangle.ShadowFormat.Blur = 5.0;           // blur radius (points)
        rectangle.ShadowFormat.OffsetX = 4.0;        // horizontal offset (points)
        rectangle.ShadowFormat.OffsetY = 4.0;        // vertical offset (points)
```

*Perché questi numeri?* Una sfocatura di 5 pts fornisce un bordo delicato, mentre un offset di 4 pts sposta l'ombra verso il basso‑destra, simulando una fonte luminosa in alto‑sinistra. Cambia `Color` in `Color.Black` per un contrasto più forte, oppure usa `Color.FromArgb(128, 0, 0, 0)` per un nero semitrasparente.

### Casi limite e variazioni

- **No blur:** Imposta `Blur = 0` per un'ombra nitida e a bordi netti.  
- **Negative offsets:** Usa `OffsetX = -4` per spostare l'ombra a sinistra.  
- **Different shapes:** Le stesse proprietà dell'ombra funzionano per cerchi, triangoli o forme disegnate a mano—basta cambiare `ShapeType` nel Passo 2.  
- **Compatibility:** Aspose.Words scrive i dati dell'ombra nel formato Office Open XML, che funziona su Word 2010‑2021 e Office 365.

## Passo 5 – Salva il documento (Create Word Document)

Infine, salva il file su disco. Puoi scegliere qualsiasi formato supportato (`.docx`, `.pdf`, `.odt`, …) ma per questa guida useremo il classico formato Word.

```csharp
        // Step 5: Save the document with the shaped shadow
        document.Save("ShadowRectangle.docx");
    }
}
```

Quando apri **ShadowRectangle.docx** in Microsoft Word vedrai un rettangolo grigio con un'ombra sottile e sfocata spostata verso il basso‑destra—esattamente ciò che abbiamo programmato.

### Output previsto

- Un file *.docx* di una sola pagina.  
- Un rettangolo 200 pt × 100 pt centrato dove si trovava il cursore al momento della chiamata a `InsertShape`.  
- Un'ombra grigia che appare 4 pts a destra e 4 pts in basso, con una sfocatura di 5 pt.

Se la forma appare fuori centro, puoi spostare il cursore con `builder.MoveTo` prima dell'inserimento, oppure regolare le proprietà `Left` e `Top` della forma dopo l'inserimento.

## Domande comuni e risoluzione dei problemi

**Q: L'ombra non appare in Word.**  
A: Assicurati che `ShadowFormat.Visible` sia `true`. Verifica anche di utilizzare una versione recente di Aspose.Words (la funzionalità ombra è stata aggiunta nella versione 20.3).  

**Q: Posso applicare un gradiente all'ombra?**  
A: Non direttamente tramite `ShadowFormat`. L'interfaccia di Word supporta ombre sfumate, ma lo schema Open XML (che Aspose.Words segue) espone solo ombre a colore solido. Dovresti modificare manualmente l'XML sottostante—uno scenario più avanzato.  

**Q: E se ho bisogno di un rettangolo trasparente con solo l'ombra?**  
A: Imposta `rectangle.FillColor = Color.Transparent;` dopo l'inserimento. L'ombra verrà comunque renderizzata perché è indipendente dal riempimento.

## Consigli professionali per il codice di produzione

- **Riutilizza il builder:** Se aggiungi più forme, mantieni la stessa istanza di `DocumentBuilder`—crearne una nuova per ogni forma aggiunge overhead inutile.  
- **Salvataggi batch:** Salva una sola volta dopo tutte le modifiche; I/O frequente rallenta la generazione di documenti di grandi dimensioni.  
- **Gestione degli errori:** Avvolgi l'intero blocco in un `try / catch` e registra le eccezioni `Aspose.Words`; spesso contengono numeri di riga utili se il modello di documento è corrotto.

## Prossimi passi (Argomenti correlati)

- **How to add shadow** a immagini o caselle di testo (uso simile di `ShadowFormat`).  
- **Insert rectangle shape** all'interno di una cella di tabella per una formattazione personalizzata.  
- **Create rectangle in Word** usando l'XML nativo di Word (per chi preferisce l'Open XML grezzo).  
- **Set shadow color** in modo dinamico in base all'input dell'utente o ai colori del tema.

Sperimenta con diversi colori, raggi di sfocatura e offset—magari un bagliore blu tenue per un report aziendale, o un'ombra nera profonda per un volantino drammatico. Le possibilità sono infinite, e le modifiche al codice sono minime.

---

### Riepilogo veloce

- Abbiamo **created a word document** da zero.  
- Abbiamo **inserted a rectangle shape** e attivato la sua ombra.  
- Abbiamo **set shadow color**, la sfocatura e gli offset per ottenere un aspetto professionale.  
- Abbiamo salvato il file, pronto per la distribuzione.

Ora hai una solida base per aggiungere elementi visivi a qualsiasi progetto di automazione Word. Hai altre idee? Lascia un commento e continuiamo la conversazione. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}