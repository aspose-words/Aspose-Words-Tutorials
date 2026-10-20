---
category: general
date: 2026-03-19
description: Crea un documento Word utilizzando Aspose.Words e un font variabile.
  Scopri come modificare il peso del font, impostare la larghezza del font e definire
  la variazione del font in C#.
draft: false
keywords:
- create word document
- change font weight
- set font width
- load variable font
- define font variation
language: it
og_description: Crea un documento Word con un font variabile usando Aspose.Words.
  Questo tutorial ti mostra come caricare il font, modificare il peso del font, impostare
  la larghezza del font e definire la variazione del font.
og_title: Crea un documento Word con font variabile – Guida completa
tags:
- Aspose.Words
- C#
- Variable Font
title: Crea documento Word con font variabile – Guida
url: /it/net/enable-opentype-features/create-word-document-with-variable-font-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Crea documento Word con font variabile – Guida

Ti è mai capitato di **creare un documento Word** che utilizza un font variabile moderno, ma non sapevi da dove iniziare? Non sei solo. In molti progetti—pensiamo a report dinamici o brochure coerenti con il brand—poter **cambiare il peso del font** al volo è davvero un punto di svolta.  

In questo tutorial percorreremo l’intero processo: dal caricamento di un font variabile in Aspose.Words, all’impostazione del suo peso e della sua larghezza, fino al salvataggio di un DOCX che appare esattamente come lo hai progettato. Nessun riferimento vago, solo codice concreto che puoi inserire subito nel tuo progetto C#.

## Cosa imparerai

- Come **caricare file di font variabile** in Aspose.Words usando `FontSettings`.
- La sintassi per **definire gli assi di variazione del font** come `wght` (peso) e `wdth` (larghezza).
- Modi per **impostare la larghezza del font** e **cambiare il peso del font** su un singolo `Run`.
- Suggerimenti per risolvere problemi comuni (glifi mancanti, percorsi di cartelle errati, ecc.).
- Un esempio completo, eseguibile, che puoi copiare‑incollare e testare subito.

> **Prerequisiti**: .NET 6+ (o .NET Framework 4.6+), Aspose.Words per .NET installato via NuGet, e un file di font variabile come *RobotoFlex.ttf* collocato in una cartella locale *Fonts*.

---

## Passo 1 – Carica il font variabile in Aspose.Words

Per prima cosa, dobbiamo indicare ad Aspose.Words dove cercare i nostri font personalizzati. La classe `FontSettings` si occupa di tutto.  

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Configure Aspose.Words to use the folder that contains the variable font
FontSettings fontSettings = new FontSettings();
fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);

// Apply the settings globally (optional but convenient)
FontSettings.DefaultInstance = fontSettings;
```

**Perché è importante**: senza registrare la cartella, Aspose.Words ricade sui font di sistema e ignorerà qualsiasi dato di variazione OpenType che proverai ad applicare in seguito. Puntando a una directory specifica garantisci che *RobotoFlex* (o qualsiasi altro font variabile) venga trovato ogni volta che il codice viene eseguito.

> **Consiglio esperto**: imposta il secondo parametro di `SetFontsFolder` a `true` se vuoi che Aspose cerchi anche nelle sottocartelle. Questo è utile quando organizzi i font per stile o peso.

---

## Passo 2 – Crea un nuovo documento e aggiungi testo di esempio

Ora che il motore dei font sa dove guardare, creiamo un `Document` vuoto e inseriamo un paragrafo con un `Run`.  

```csharp
// Create a fresh, empty document
Document document = new Document();

// Add a new paragraph to the first section
Paragraph paragraph = new Paragraph(document);
Run variableRun = new Run(document, "Variable‑weight text");

// Attach the run to the paragraph, then the paragraph to the document body
paragraph.AppendChild(variableRun);
document.FirstSection.Body.AppendChild(paragraph);
```

**Cosa succede**: `Run` rappresenta una porzione contigua di testo con formattazione uniforme. Creandolo per primo, manteniamo la logica di formattazione isolata—perfetta per applicare in seguito assi di variazione diversi a run separati, se necessario.

---

## Passo 3 – Definisci gli assi di variazione desiderati (Peso & Larghezza)

I font variabili espongono *assi* che puoi modificare a runtime. I due più comuni sono `wght` (peso del font) e `wdth` (larghezza del font). Aspose.Words modella questo con la collezione `OpenTypeFontVariation`.

```csharp
// Build a collection of variation axes
OpenTypeFontVariation variationAxes = new OpenTypeFontVariation
{
    // Change the weight to 700 (roughly Bold) and width to 100 (normal width)
    { "wght", 700 },
    { "wdth", 100 }
};
```

**Perché questi numeri**: nella specifica OpenType, `wght` varia dal peso minimo al massimo del font (spesso 100–900). Un valore di **700** corrisponde a un aspetto grassetto. `wdth` funziona in modo analogo; **100** indica la larghezza predefinita (normale), mentre valori inferiori a 100 comprimono i glifi.

> **Caso limite**: alcuni font variabili non supportano un determinato asse. Se fornisci un tag non supportato, Aspose lo ignorerà silenziosamente. Controlla sempre la specifica del font (di solito presente nei metadati del file `.ttf` o `.otf`).

---

## Passo 4 – Applica la variazione al Run usando il nome del font

Ora colleghiamo i dati di variazione al testo reale. La classe `FontInfo` contiene il nome della famiglia del font e la collezione di assi.

```csharp
// Assign the variable font and its axes to the run's FontInfo
variableRun.Font.FontInfo = new FontInfo("RobotoFlex", variationAxes);
```

**Spiegazione**: impostando `FontInfo`, bypassiamo la consueta proprietà `Font.Name` e forniamo al motore una configurazione completa del font. Questo è l’unico modo per dire ad Aspose.Words di usare un font variabile con assi personalizzati.

> **Errore comune**: dimenticare di corrispondere esattamente al nome della famiglia all’interno del file del font (`RobotoFlex` in questo esempio). Un errore di battitura farà ricadere Aspose su un font predefinito, e la tua variazione andrà persa.

---

## Passo 5 – Salva il documento e verifica il risultato

Infine, scrivi il documento su disco. Il DOCX generato conterrà le istruzioni del font variabile, che Microsoft Word (2016+) può renderizzare correttamente.

```csharp
// Save the document; Word will render the variable font with the specified weight and width
document.Save(@"C:\MyProject\Output\VariableFont.docx");
```

Apri il file risultante in Word, seleziona il testo e guarda la finestra di dialogo **Font**. Dovresti vedere *Roboto Flex* elencato, e il testo apparirà più spesso rispetto al contenuto circostante—esattamente quello richiesto dall’impostazione `wght = 700`.

> **Suggerimento di verifica**: se il testo sembra invariato, ricontrolla che il file del font supporti davvero l’asse `wght`. Alcuni “font variabili” espongono solo `ital` (italic) o `opsz` (dimensione ottica).

---

## Opzionale: Aggiungi più variazioni – Cambiare la larghezza dinamicamente

Se vuoi *impostare la larghezza del font* diversamente per un altro paragrafo, ripeti i passi 3‑4 con una nuova collezione `OpenTypeFontVariation`.

```csharp
// Example: widen the text to 115% (condensed vs expanded)
OpenTypeFontVariation wideAxes = new OpenTypeFontVariation
{
    { "wght", 500 },   // regular weight
    { "wdth", 115 }    // slightly expanded width
};

Run wideRun = new Run(document, "Expanded width text");
wideRun.Font.FontInfo = new FontInfo("RobotoFlex", wideAxes);
Paragraph wideParagraph = new Paragraph(document);
wideParagraph.AppendChild(wideRun);
document.FirstSection.Body.AppendChild(wideParagraph);
```

Ora hai due run—uno in grassetto, l’altro leggermente più largo—che dimostrano sia **cambiare il peso del font** sia **impostare la larghezza del font** nello stesso documento.

---

## Esempio completo funzionante

Copia lo snippet qui sotto in una nuova console app (`Program.cs`) ed eseguilo. Assicurati che la cartella `Fonts` contenga `RobotoFlex.ttf` (o qualsiasi font variabile tu preferisca).

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the variable font
        FontSettings fontSettings = new FontSettings();
        fontSettings.SetFontsFolder(@"C:\MyProject\Fonts", false);
        FontSettings.DefaultInstance = fontSettings;

        // 2️⃣ Create a document and a run
        Document doc = new Document();
        Paragraph para = new Paragraph(doc);
        Run run = new Run(doc, "Variable‑weight text");
        para.AppendChild(run);
        doc.FirstSection.Body.AppendChild(para);

        // 3️⃣ Define variation axes (weight = 700, width = 100)
        OpenTypeFontVariation axes = new OpenTypeFontVariation
        {
            { "wght", 700 },
            { "wdth", 100 }
        };

        // 4️⃣ Apply the variation using the font name
        run.Font.FontInfo = new FontInfo("RobotoFlex", axes);

        // 5️⃣ Save the result
        doc.Save(@"C:\MyProject\Output\VariableFont.docx");
    }
}
```

**Output previsto**: un file `VariableFont.docx` in cui la frase “Variable‑weight text” appare in grassetto, grazie all’asse `wght = 700`, mantenendo la larghezza predefinita.

---

## Domande frequenti & casi limite

| Domanda | Risposta |
|----------|----------|
| *E se il font non viene trovato?* | Verifica il percorso della cartella, assicurati che il nome del file corrisponda e che il processo abbia i permessi di lettura. Puoi anche chiamare `fontSettings.GetFonts()` per elencare i font rilevati. |
| *Posso combinare più run con variazioni diverse?* | Assolutamente. Ogni `Run` può avere il proprio `FontInfo`. Basta ripetere i passi 3‑4 per ogni run. |
| *Le versioni più vecchie di Word supportano i font variabili?* | Word 2016 (Build 16.0.8001) ha introdotto il supporto di base. Se punti a versioni precedenti, il documento tornerà a una versione statica più vicina del font. |
| *C’è un limite al numero di assi che posso impostare?* | Puoi impostare tutti gli assi definiti dal font. I tag più comuni sono `wght`, `wdth`, `ital`, `opsz`, `GRAD`. Fornire un tag non supportato non ha alcun effetto. |
| *Come debuggo i glifi mancanti?* | Usa `FontSettings.GetFontSources()` per ispezionare i font caricati, e `FontInfo.HasGlyph(char)` per testare i singoli caratteri. |

---

## Conclusione

In pochi passaggi abbiamo mostrato **come creare documenti Word** che sfruttano la potenza dei font variabili, permettendoti di **cambiare il peso del font**, **impostare la larghezza del font**, **caricare file di font variabile** e **definire gli assi di variazione del font**—tutto con Aspose.Words per .NET.  

L’idea di base è semplice: registra la cartella dei font, descrivi gli assi desiderati, allegali a un `Run` e salva. Da qui puoi estendere la tecnica a intere sezioni, tabelle o persino generare report brandizzati in modo programmatico.

**Passi successivi**: prova a sostituire `RobotoFlex` con un altro font variabile, sperimenta l’asse `ital` (italic) o genera una versione PDF dello stesso documento usando Aspose.PDF. Lo stesso schema si applica—carica, definisci, applica, salva.

Buon coding e goditi la flessibilità che i font variabili portano ai tuoi progetti di automazione Word!  

<img src="variable-font-demo.png" alt="Create word document with variable font example">

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}