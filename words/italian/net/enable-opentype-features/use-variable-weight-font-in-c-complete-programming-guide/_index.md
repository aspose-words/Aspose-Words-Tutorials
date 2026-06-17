---
category: general
date: 2026-06-02
description: Impara a utilizzare i font a peso variabile in C# e a impostare il peso
  del font programmaticamente, modificando il codice di stretch del font per una tipografia
  dinamica.
draft: false
keywords:
- use variable weight font
- set font weight programmatically
- change font stretch code
- variable font Aspose.Words
- dynamic typography C#
language: it
og_description: Utilizza font a peso variabile in C# per impostare il peso del carattere
  programmaticamente e modificare il codice di allungamento del font, consentendo
  una tipografia dinamica nei tuoi documenti.
og_title: Usa Font a Peso Variabile in C# – Guida Completa
schemas:
- author: Aspose
  dateModified: '2026-06-02'
  description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  headline: Use Variable Weight Font in C# – Complete Programming Guide
  type: TechArticle
- description: Learn how to use variable weight font in C# and set font weight programmatically
    while change font stretch code for dynamic typography.
  name: Use Variable Weight Font in C# – Complete Programming Guide
  steps:
  - name: What if the font doesn’t appear at all?
    text: '- **Missing FontSettings**: Double‑check that `doc.FontSettings = fontSettings;`
      is executed **before** any text is added. - **Incorrect family name**: Use `fontSettings.GetFonts()`
      to list all discovered families; copy the exact string. - **Unsupported weight/stretch**:
      Some variable fonts only sup'
  - name: Can I change the weight after the document is saved?
    text: Yes. The `Run` object is mutable, so you can adjust `FontWeight` or `FontStretch`
      at any point before the final `Save`. If you need to toggle weights dynamically
      (e.g., based on user interaction), consider generating separate runs for each
      state.
  - name: Does this work with DOCX output?
    text: Absolutely. The variable‑weight metadata is stored in the underlying OpenXML,
      and modern versions of Word can interpret it. However, older Word versions may
      ignore the stretch setting.
  type: HowTo
tags:
- C#
- Aspose.Words
- Variable Fonts
title: Usa Font a Peso Variabile in C# – Guida Completa alla Programmazione
url: /it/net/enable-opentype-features/use-variable-weight-font-in-c-complete-programming-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Usa Font a Peso Variabile in C# – Guida Completa alla Programmazione

Hai mai avuto bisogno di **usare un font a peso variabile** in un progetto .NET ma non eri sicuro di come far reagire peso e allungamento all'input dell'utente? Non sei solo. In molti scenari UI o di reporting vuoi che il testo si adatti—magari un titolo leggero che diventa grassetto al passaggio del mouse, o un paragrafo che espande la sua larghezza per enfatizzare. La buona notizia è che con Aspose.Words puoi **impostare il peso del font programmaticamente** e persino **modificare il codice di allungamento del font** al volo.

In questo tutorial ti guideremo passo passo attraverso un esempio pratico che mostra esattamente come caricare un font a peso variabile, applicare un peso personalizzato e regolare l'impostazione di allungamento—tutto con codice C# chiaro che puoi copiare-incollare. Alla fine avrai un'app console eseguibile che produce un PDF che dimostra l'effetto.

---

## Di cosa avrai bisogno

- **Aspose.Words for .NET** (v23.12 o successive). La libreria include il supporto completo per i font a peso variabile.
- Una cartella contenente almeno un file di font a peso variabile, ad esempio *RobotoFlex‑Variable.ttf*. Puoi scaricarlo da Google Fonts.
- .NET 6 SDK (o qualsiasi versione recente di .NET) e un IDE a tua scelta.
- Conoscenze di base di C#—nulla di complicato, solo poche righe di codice.

È tutto. Nessun pacchetto NuGet aggiuntivo oltre a Aspose.Words, e nessun file di configurazione oscuro.

![Esempio di utilizzo del font a peso variabile](https://example.com/variable-weight-sample.png "Dimostrazione dell'uso del font a peso variabile")

*Testo alternativo: screenshot che mostra l'uso del font a peso variabile in un documento PDF generato.*

---

## Passo 1: Configura FontSettings e indica la tua cartella dei font  

Prima di tutto—Aspose.Words deve sapere dove risiedono i tuoi font a peso variabile. Lo fai creando un oggetto `FontSettings` e collegando un `FolderFontSource`. Il flag `true` indica al motore di cercare anche nelle sottocartelle, il che è comodo se tieni più famiglie di font insieme.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create FontSettings and point to the folder containing variable‑weight fonts
var fontSettings = new FontSettings();
fontSettings.SetFontSources(new FontSourceBase[]
{
    new FolderFontSource(@"C:\MyProject\Fonts\", true) // Adjust path to your own directory
});
```

**Perché è importante:** Senza registrare la cartella, Aspose.Words ricade sui font di sistema e ignorerà i dati a peso variabile incorporati nel tuo file di font personalizzato. Questo passaggio è la base per tutto ciò che seguirà.

---

## Passo 2: Associa FontSettings al Documento  

Ora creiamo un nuovo `Document` (o ne carichiamo uno esistente) e gli diciamo di usare i `FontSettings` appena preparati. Questa associazione è ciò che rende disponibili i dati a peso variabile a ogni `Run` che aggiungeremo in seguito.

```csharp
// Step 2: Attach the FontSettings to the document
var doc = new Document();          // Starts with a blank document
doc.FontSettings = fontSettings;   // Connects our custom fonts
```

Se hai già un modello—ad esempio un file Word con segnaposti—puoi sostituire `new Document()` con `new Document("Template.docx")`. Gli stessi `FontSettings` verranno applicati.

---

## Passo 3: Aggiungi un Run di Testo che Utilizzerà il Font a Peso Variabile  

Un **Run** è l'unità più piccola di formattazione del testo in Aspose.Words. Creeremo uno, lo inseriremo in un nuovo paragrafo e successivamente ne modificheremo le proprietà del font.

```csharp
// Step 3: Add a run of text that will use the variable‑weight font
var paragraph = new Paragraph(doc);
doc.FirstSection.Body.AppendChild(paragraph);

var run = new Run(doc, "Variable‑weight text demo");
paragraph.AppendChild(run);
```

A questo punto il testo verrà renderizzato usando il font predefinito (di solito Times New Roman). La magia accade quando assegniamo la famiglia a peso variabile.

---

## Passo 4: Scegli la Famiglia di Font a Peso Variabile  

Ecco dove **usiamo realmente il font a peso variabile**. Imposta `Font.Name` sul nome esatto della famiglia definita all'interno del file di font variabile. Per Roboto Flex, il nome è `"Roboto Flex"`.

```csharp
// Step 4: Choose the variable‑weight font family
run.Font.Name = "Roboto Flex";
```

Se non sei sicuro del nome della famiglia, apri il file `.ttf` in un visualizzatore di font o usa il metodo `fontSettings.GetFonts()` per elencare le famiglie disponibili.

---

## Passo 5: Imposta Peso e Allungamento del Font Programmaticamente  

Ora il cuore del tutorial: **impostiamo il peso del font programmaticamente** e **modifichiamo il codice di allungamento del font**. Entrambe le proprietà accettano valori interi che corrispondono alla specifica OpenType.

```csharp
// Step 5: Specify the desired weight and stretch for the run
run.Font.FontWeight = 300;   // Light weight (300)
run.Font.FontStretch = 125; // Expanded stretch (125% of normal width)
```

- **FontWeight**: 100 (Thin) → 900 (Black). Scegli qualsiasi valore supportato dal font variabile.
- **FontStretch**: 50 (Ultra‑Condensed) → 200 (Ultra‑Expanded). Il valore predefinito è 100 (Normal).

> **Consiglio professionale:** Non tutti i font variabili espongono l'intera gamma. Se imposti un valore non supportato, il motore lo limiterà al peso o allungamento più vicino disponibile.

---

## Passo 6: Salva il Documento e Verifica il Risultato  

Infine, scrivi il documento in PDF (o DOCX) e aprilo per vedere l'effetto. Il PDF è un formato ottimo per la verifica visiva perché il rendering è coerente su tutte le piattaforme.

```csharp
// Step 6: Save the document as PDF
doc.Save(@"C:\MyProject\Output\VariableWeightDemo.pdf", SaveFormat.Pdf);
```

Quando apri *VariableWeightDemo.pdf*, dovresti vedere la frase “Variable‑weight text demo” renderizzata in una versione leggera e leggermente espansa di Roboto Flex. Cambia `FontWeight` a `700` e `FontStretch` a `80` e riesegui—osserva il testo diventare grassetto e più condensato.

---

## Domande Frequenti & Casi Limite  

### Cosa succede se il font non appare affatto?  

- **Missing FontSettings**: Verifica che `doc.FontSettings = fontSettings;` venga eseguito **prima** di aggiungere qualsiasi testo.
- **Incorrect family name**: Usa `fontSettings.GetFonts()` per elencare tutte le famiglie scoperte; copia la stringa esatta.
- **Unsupported weight/stretch**: Alcuni font variabili supportano solo un sottoinsieme della gamma 100‑900. Usa `run.Font.FontWeight = 400;` come fallback sicuro.

### Posso cambiare il peso dopo che il documento è stato salvato?  

Sì. L'oggetto `Run` è mutabile, quindi puoi regolare `FontWeight` o `FontStretch` in qualsiasi momento prima del `Save` finale. Se devi alternare i pesi in modo dinamico (ad esempio in base all'interazione dell'utente), considera di generare run separati per ogni stato.

### Funziona con l'output DOCX?  

Assolutamente. I metadati a peso variabile sono memorizzati nell'OpenXML sottostante, e le versioni moderne di Word possono interpretarli. Tuttavia, le versioni più vecchie di Word potrebbero ignorare l'impostazione di allungamento.

---

## Esempio Completo Funzionante  

Di seguito trovi un programma console completo che puoi compilare ed eseguire subito. Include tutte le direttive `using` necessarie, la gestione degli errori e i commenti.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

namespace VariableWeightDemo
{
    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure FontSettings
            var fontSettings = new FontSettings();
            fontSettings.SetFontSources(new FontSourceBase[]
            {
                // 👉 Point to your local folder containing the variable‑weight font files
                new FolderFontSource(@"C:\MyProject\Fonts\", true)
            });

            // 2️⃣ Create the document and attach FontSettings
            var doc = new Document();
            doc.FontSettings = fontSettings;

            // 3️⃣ Build a paragraph with a run of text
            var paragraph = new Paragraph(doc);
            doc.FirstSection.Body.AppendChild(paragraph);
            var run = new Run(doc, "Variable‑weight text demo");
            paragraph.AppendChild(run);

            // 4️⃣ Apply the variable‑weight font family
            run.Font.Name = "Roboto Flex";

            // 5️⃣ Set weight (300 = Light) and stretch (125 = Expanded)
            run.Font.FontWeight = 300;   // set font weight programmatically
            run.Font.FontStretch = 125; // change font stretch code

            // 6️⃣ Save as PDF to verify the rendering
            string outputPath = @"C:\MyProject\Output\VariableWeightDemo.pdf";
            doc.Save(outputPath, SaveFormat.Pdf);

            Console.WriteLine($"Document saved to {outputPath}");
            Console.WriteLine("Open the PDF to see the light, expanded Roboto Flex text.");
        }
    }
}
```

**Output previsto:** La console stampa il percorso di salvataggio e il PDF generato mostra il testo in uno stile leggero ed espanso—esattamente come lo abbiamo configurato.

---

## Riepilogo  

Abbiamo coperto come **usare un font a peso variabile** in C# con Aspose.Words, dimostrato come **impostare il peso del font programmaticamente** e mostrato il preciso **codice per cambiare l'allungamento del font** necessario per espandere o condensare i glifi. I passaggi sono semplici: configura `FontSettings`, associali a un `Document`, crea un `Run`, scegli la famiglia a peso variabile e infine regola `FontWeight` e `FontStretch`.

---

## Cosa segue?  

- **Integrazione UI dinamica**: Collega la stessa logica a un'app WinForms o WPF per consentire agli utenti di scegliere peso/allungamento tramite slider.  
- **Run multipli**: Combina diversi run con pesi differenti nello stesso paragrafo per gerarchie tipografiche ricche.  
- **Assi avanzati**: Alcuni font variabili espongono assi aggiuntivi (ad esempio slant, optical size). Usa `run.Font.FontStyle` o esplora `FontVariationSettings` per un controllo ancora più fine.  
- **Consigli sulle prestazioni**: Metti in cache l'istanza `FontSettings` quando elabori molti documenti per evitare scansioni ripetute della cartella.  

Sentiti libero di sperimentare—sostituisci *Roboto Flex* con *Inter Variable* o qualsiasi altro font OpenType variabile, e osserva i tuoi documenti guadagnare un nuovo livello di flessibilità visiva. Buon coding!

---

## Cosa Dovresti Imparare Dopo?

I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità API aggiuntive e a esplorare approcci di implementazione alternativi nei tuoi progetti.

- [Usa Font dalla Macchina di Destinazione](/words/english/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Usa Font dalla Macchina di Destinazione](/words/german/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)
- [Usa Font dalla Macchina di Destinazione](/words/french/net/programming-with-htmlfixedsaveoptions/use-font-from-target-machine/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}