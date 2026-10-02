---
category: general
date: 2026-01-11
description: Abilita gli avvisi di sostituzione dei caratteri per rilevare i font
  mancanti nei tuoi documenti .NET. Scopri come ottenere il nome del font mancante
  e elencare i font mancanti con Aspose.Words.
draft: false
keywords:
- enable font substitution warnings
- detect missing fonts
- get missing font name
- list missing fonts
language: it
og_description: Abilita gli avvisi di sostituzione dei caratteri in Aspose.Words per
  rilevare i caratteri mancanti, ottenere il nome del carattere mancante e elencare
  i caratteri mancanti nei tuoi documenti.
og_title: Abilita gli avvisi di sostituzione dei font – Tutorial C# passo‑passo
tags:
- Aspose.Words
- C#
- Document Processing
title: Abilita gli avvisi di sostituzione dei font in Aspose.Words – Guida completa
url: /it/net/working-with-fonts/enable-font-substitution-warnings-in-aspose-words-complete-g/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abilita gli avvisi di sostituzione dei caratteri – Guida completa

Ti sei mai chiesto perché un documento Word appare leggermente diverso dopo averlo caricato su un server? Probabilmente un carattere usato dall'autore originale non è disponibile sulla tua macchina, e Aspose.Words lo ha sostituito silenziosamente con quello più vicino. **Abilita gli avvisi di sostituzione dei caratteri** e saprai immediatamente quali caratteri mancano, con cosa sono stati sostituiti e come agire su queste informazioni.

In questo tutorial percorreremo un esempio pratico, end‑to‑end, che mostra come **rilevare i caratteri mancanti**, recuperare il **get missing font name**, e persino **elencare i caratteri mancanti** per la reportistica. Nessuna teoria superflua, solo una soluzione chiara che puoi inserire in qualsiasi progetto .NET oggi.

---

## Cosa imparerai

- Come configurare `LoadOptions` affinché Aspose.Words emetta avvisi dettagliati.
- Il codice esatto necessario per caricare un documento e enumerare gli avvisi relativi ai caratteri.
- Modalità per estrarre il nome del carattere mancante e la sua sostituzione, quindi generare un report ordinato.
- Suggerimenti per gestire casi limite, come documenti con decine di caratteri mancanti o cartelle di caratteri personalizzate.

### Prerequisiti

- .NET 6+ (il codice funziona anche con .NET Framework 4.7+)
- Aspose.Words per .NET 23.10 o versioni successive (puoi scaricarlo da NuGet)
- Un file DOCX di esempio che fa riferimento a un carattere non installato (lo chiameremo `MissingFont.docx`)

Se hai questi prerequisiti, immergiamoci.

---

## Passo 1: Configura LoadOptions per Abilitare gli Avvisi di Sostituzione dei Caratteri  

La prima cosa da fare è dire ad Aspose.Words che ti interessano i caratteri mancanti. Per impostazione predefinita la libreria registra solo gli avvisi internamente. Impostare `SubstitutionWarningLevel` su `Typical` (o `All` per l'output più dettagliato) attiva la funzionalità.

```csharp
using Aspose.Words;
using Aspose.Words.Loading;

// Create a new LoadOptions instance
LoadOptions loadOptions = new LoadOptions();

// Attach a FontSettings object so we can tweak font‑related behavior
loadOptions.FontSettings = new FontSettings();

// Enable warnings for typical font substitutions (covers most real‑world cases)
loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;
```

**Perché è importante:**  
Quando `SubstitutionWarningLevel` è impostato, ogni volta che Aspose.Words non riesce a trovare un carattere di riferimento aggiunge un `FontSubstitutionWarning` alla collezione `Warnings` del documento. Questa collezione è l'unico modo affidabile per **rilevare i caratteri mancanti** senza analizzare manualmente il documento.

> **Suggerimento professionale:** Se stai gestendo un batch di documenti e vuoi essere assolutamente certo di catturare ogni sostituzione, usa `FontSubstitutionWarningLevel.All`. È un po' più rumoroso ma garantisce che nessun avviso sfugga.

---

## Passo 2: Carica il Documento Utilizzando le Opzioni Configurate  

Ora che il sistema di avvisi è pronto, carica il tuo DOCX con le `LoadOptions` appena configurate. Il percorso può essere assoluto o relativo; assicurati solo che il file esista.

```csharp
// Path to the DOCX that references a font you don’t have
string docPath = @"C:\Docs\MissingFont.docx";

// Load the document while respecting our warning configuration
Document document = new Document(docPath, loadOptions);
```

**Cosa succede dietro le quinte?**  
Aspose.Words analizza l'XML del documento, risolve ogni elemento `<w:font>` e controlla il catalogo dei caratteri del sistema (oltre a eventuali cartelle personalizzate aggiunte a `FontSettings`). Quando non riesce a trovare un carattere, registra un avviso—esattamente ciò di cui abbiamo bisogno per **elencare i caratteri mancanti** in seguito.

---

## Passo 3: Itera sugli Avvisi ed Estrai i Dettagli del Carattere Mancante  

Con il documento in memoria, la collezione `Warnings` contiene ogni `FontSubstitutionWarning`. La percorreremo, filtreremo per il tipo corretto e stamperemo un report leggibile.

```csharp
Console.WriteLine("=== Missing Font Report ===");
foreach (WarningInfo warning in document.Warnings)
{
    // Only interested in font substitution warnings
    if (warning is FontSubstitutionWarning fontWarning)
    {
        // The name of the font that was missing
        string missingFont = fontWarning.FontName;

        // The font Aspose.Words used instead
        string substitutedFont = fontWarning.SubstitutedFontName;

        Console.WriteLine($"Missing font: {missingFont}");
        Console.WriteLine($"Substituted with: {substitutedFont}");
        Console.WriteLine(new string('-', 30));
    }
}
```

**Output previsto** (supponendo che il documento di origine faccia riferimento a `MyCustomFont` che non è installato):

```
=== Missing Font Report ===
Missing font: MyCustomFont
Substituted with: Arial
------------------------------
Missing font: FancyScript
Substituted with: Times New Roman
------------------------------
```

Nota come ogni voce fornisce sia il **get missing font name** (`MyCustomFont`) sia il carattere di fallback (`Arial`). Queste sono esattamente le informazioni necessarie per decidere se incorporare il carattere originale, chiedere all'autore una sostituzione, o semplicemente accettare la sostituzione.

---

## Passo 4: Facoltativo – Raccogli i Dati in una Lista per Ulteriori Elaborazioni  

Se devi esportare il report in CSV, inviarlo tramite API, o semplicemente conservarlo in memoria per dopo, puoi archiviare gli avvisi in una lista tipizzata.

```csharp
// Define a simple DTO to hold the warning details
public class MissingFontInfo
{
    public string MissingFont { get; set; }
    public string SubstitutedFont { get; set; }
}

// Build the list
List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();

foreach (WarningInfo warning in document.Warnings)
{
    if (warning is FontSubstitutionWarning fsw)
    {
        missingFonts.Add(new MissingFontInfo
        {
            MissingFont = fsw.FontName,
            SubstitutedFont = fsw.SubstitutedFontName
        });
    }
}

// Example: write to a CSV (requires System.IO)
var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);
```

Ora hai **list missing fonts** in un formato che qualsiasi sistema a valle può consumare. Che tu stia alimentando una dashboard o generando un registro di audit, i dati sono pronti.

---

## Passo 5: Gestione dei Casi Limite e delle Insidie Comuni  

### Molti Caratteri Mancanti in un Unico Esecuzione  

I grandi modelli aziendali spesso fanno riferimento a decine di caratteri personalizzati. La collezione di avvisi può diventare notevole, ma il pattern di iterazione mostrato sopra scala linearmente, quindi le prestazioni non sono un problema. Ricorda solo di mantenere l'output leggibile—raggruppare per pagina o stile può essere utile se necessiti di un'analisi più approfondita.

### Cartelle di Caratteri Personalizzate  

Se memorizzi i caratteri in una directory non standard (ad esempio una condivisione di rete), indica ad Aspose.Words dove cercare:

```csharp
loadOptions.FontSettings.SetFontsFolder(@"\\fileserver\SharedFonts", recursive: true);
```

Impostare questo *prima* di caricare il documento dà alla libreria la possibilità di trovare i caratteri, il che può eliminare del tutto alcuni avvisi.

### Soppressione di Avvisi Specifici  

A volte sai che una determinata sostituzione è accettabile (ad esempio un carattere decorativo che non ti dispiace sostituire). Puoi filtrare questi avvisi dopo il fatto:

```csharp
missingFonts = missingFonts
    .Where(f => f.MissingFont != "DecorativeFont")
    .ToList();
```

### Compatibilità di Versione  

L'enumerazione `FontSubstitutionWarningLevel` è stabile sin da Aspose.Words 20.12. Se utilizzi una versione più vecchia, potresti dover aggiornare per accedere alla funzionalità di livello di avviso.

---

## Esempio Completo Funzionante  

Di seguito trovi il programma completo, pronto per l'esecuzione, che incorpora tutti i passaggi sopra. Incollalo in un nuovo progetto console, aggiungi il pacchetto NuGet Aspose.Words, e imposta `docPath` su un documento che fa riferimento a un carattere mancante.

```csharp
using System;
using System.Collections.Generic;
using System.IO;
using System.Linq;
using Aspose.Words;
using Aspose.Words.Loading;

namespace FontWarningDemo
{
    // DTO for storing missing font info
    public class MissingFontInfo
    {
        public string MissingFont { get; set; }
        public string SubstitutedFont { get; set; }
    }

    class Program
    {
        static void Main()
        {
            // 1️⃣ Configure LoadOptions to enable font substitution warnings
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };
            loadOptions.FontSettings.SubstitutionWarningLevel = FontSubstitutionWarningLevel.Typical;

            // Optional: add a custom fonts folder
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", true);

            // 2️⃣ Load the document with the above options
            string docPath = @"C:\Docs\MissingFont.docx";
            Document doc = new Document(docPath, loadOptions);

            // 3️⃣ Gather warnings into a list
            List<MissingFontInfo> missingFonts = new List<MissingFontInfo>();
            foreach (WarningInfo warning in doc.Warnings)
            {
                if (warning is FontSubstitutionWarning fsw)
                {
                    missingFonts.Add(new MissingFontInfo
                    {
                        MissingFont = fsw.FontName,
                        SubstitutedFont = fsw.SubstitutedFontName
                    });
                }
            }

            // 4️⃣ Output a human‑readable report
            Console.WriteLine("=== Missing Font Report ===");
            foreach (var info in missingFonts)
            {
                Console.WriteLine($"Missing font: {info.MissingFont}");
                Console.WriteLine($"Substituted with: {info.SubstitutedFont}");
                Console.WriteLine(new string('-', 30));
            }

            // 5️⃣ (Optional) Export to CSV for further analysis
            var csvLines = missingFonts.Select(f => $"{f.MissingFont},{f.SubstitutedFont}");
            File.WriteAllLines(@"C:\Docs\MissingFontsReport.csv", csvLines);

            Console.WriteLine("Report saved to C:\\Docs\\MissingFontsReport.csv");
        }
    }
}
```

Eseguendo questo programma **abiliterà gli avvisi di sostituzione dei caratteri**, **rileverà i caratteri mancanti**, **get missing font name**, e **elencherà i caratteri mancanti** sia nella console che in un file CSV.

---

## Conclusione  

Abbiamo appena coperto tutto ciò di cui hai bisogno per **abilitare gli avvisi di sostituzione dei caratteri** in Aspose.Words, dalla configurazione iniziale all'estrazione di un elenco pulito di caratteri mancanti. Seguendo i passaggi sopra potrai auditare i tuoi documenti, garantire la fedeltà visiva e evitare spiacevoli sorprese durante il rendering su un server.

Successivamente, potresti voler approfondire:

- **Incorporare i caratteri mancanti** direttamente nel PDF o DOCX di output (usa `FontSettings.EmbeddedFonts`).
- **Automatizzare l'installazione dei caratteri** sugli agenti di build basandosi sul report generato.
- **Integrare con pipeline CI** per far fallire le build quando i caratteri critici sono assenti.

Provali, e trasformerai un semplice sistema di avvisi in un flusso di lavoro completo di gestione dei caratteri.

Buon coding, e che tutti i tuoi caratteri vengano trovati!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}