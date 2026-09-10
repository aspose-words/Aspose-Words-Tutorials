---
category: general
date: 2026-01-14
description: Registra gli avvisi di sostituzione dei font durante il caricamento dei
  documenti Word con Aspose.Words. Impara a rilevare i font mancanti e come catturare
  i font mancanti in C#.
draft: false
keywords:
- log font substitution warnings
- detect missing fonts
- how to capture missing fonts
language: it
og_description: Registra gli avvisi di sostituzione dei font durante il caricamento
  dei documenti Word con Aspose.Words. Scopri come rilevare i font mancanti e catturare
  i font mancanti in C#.
og_title: Registro degli avvisi di sostituzione dei font – Guida completa ad Aspose.Words
tags:
- Aspose.Words
- C#
- Document Processing
title: Avvisi di sostituzione dei font nel registro – Guida completa ad Aspose.Words
url: /it/net/working-with-fonts/log-font-substitution-warnings-complete-aspose-words-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Log Font Substitution Warnings – Guida Completa ad Aspose.Words

Registrare gli avvisi di sostituzione dei font è fondamentale quando è necessario garantire che un documento Word abbia esattamente lo stesso aspetto dopo essere stato caricato da Aspose.Words. Se ti sei mai chiesto come **rilevare i font mancanti** o vuoi sapere **come catturare i font mancanti**, sei nel posto giusto.  

In questo tutorial percorreremo uno scenario reale, mostreremo il codice C# completo e spiegheremo perché ogni riga è importante. Alla fine sarai in grado di registrare ogni evento di sostituzione del font e agire di conseguenza—nessun avviso misterioso rimarrà nascosto.

![Log font substitution warnings example](/images/font-warnings.png "Screenshot showing console output of log font substitution warnings")

## Cosa Imparerai

- Come configurare `LoadOptions` affinché Aspose.Words generi avvisi tipizzati per la sostituzione dei font.  
- I passaggi esatti per **rilevare i font mancanti** durante il caricamento del documento.  
- Un modo pulito per **catturare i font mancanti** e scriverli nel tuo log o sistema di monitoraggio.  
- Gestione dei casi limite (ad esempio, quando un documento contiene un font non installato sul server).  

### Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche con .NET Framework 4.6+).  
- Una licenza valida di Aspose.Words per .NET (o la versione di prova gratuita).  
- Familiarità di base con C# e le applicazioni console.  

Se hai già tutto questo, immergiamoci.

## Passo 1 – Configurare LoadOptions per Generare Avvisi Tipizzati

Il cuore della soluzione risiede in `LoadOptions.FontSubstitutionWarning`. Impostandolo su `RaiseTypedWarnings` si indica ad Aspose.Words di generare un evento **ogni volta** che non riesce a trovare il font esatto richiesto.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;

class Program
{
    static void Main()
    {
        // Step 1: Create a LoadOptions instance that will raise warnings.
        var loadOptions = new LoadOptions
        {
            // This flag makes Aspose.Words emit detailed warnings instead of silently substituting.
            FontSubstitutionWarning = LoadOptions.FontSubstitutionWarningOption.RaiseTypedWarnings
        };
```

> **Perché è importante:**  
> Il comportamento predefinito sostituisce silenziosamente un font mancante con il più simile, il che può provocare difetti di layout inattesi. Generare avvisi tipizzati ti offre piena visibilità.

## Passo 2 – Sottoscrivere l'Evento di Avviso

Ora ci colleghiamo a `loadOptions.FontSubstitutionWarning`. La lambda riceve un oggetto `e` che indica esattamente quale font era mancante e quale è stato usato al suo posto.

```csharp
        // Step 2: Attach an event handler to capture each substitution.
        loadOptions.FontSubstitutionWarning += (sender, e) =>
        {
            // Log to console – replace with your own logger if needed.
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

> **Consiglio professionale:** Se esegui questo su un server web, sostituisci `Console.WriteLine` con un logger strutturato (Serilog, NLog, ecc.) così da poter interrogare i dati in seguito.

## Passo 3 – Caricare il Documento Utilizzando le Opzioni Configurate

Con il meccanismo di avviso attivo, basta caricare il documento come faresti normalmente. L'evento viene generato automaticamente per ogni font mancante.

```csharp
        // Step 3: Load the target document while the warning handler is active.
        string inputPath = @"YOUR_DIRECTORY\input.docx";
        Document doc = new Document(inputPath, loadOptions);

        // Optional: do something with the document – e.g., save as PDF.
        // doc.Save(@"YOUR_DIRECTORY\output.pdf");
    }
}
```

### Output Console Atteso

Se `input.docx` fa riferimento a un font chiamato *MyFancyFont* che non è installato, vedrai:

```
Missing font: MyFancyFont – substituted with Arial
Missing font: AnotherMissingFont – substituted with Times New Roman
```

Ogni riga corrisponde a un evento di **detect missing fonts**, fornendo una traccia completa.

## Passo 4 – Gestire i Casi Limite e Scenari Avanzati

### 4.1 Quando Nessuna Sostituzione Avviene

A volte un documento utilizza solo font di sistema già presenti. In tal caso l'evento di avviso non viene mai generato e otterrai una console pulita senza output. È un segnale positivo—l'ambiente dispone già di tutti i font richiesti.

### 4.2 Catturare gli Avvisi per Analisi Successive

Se devi memorizzare gli avvisi per un report notturno, raccoglili in una lista:

```csharp
        var missingFonts = new List<(string Original, string Substituted)>();
        loadOptions.FontSubstitutionWarning += (s, e) =>
        {
            missingFonts.Add((e.FontName, e.SubstitutedFontName));
            Console.WriteLine($"Missing font: {e.FontName} – substituted with {e.SubstitutedFontName}");
        };
```

Dopo il caricamento, puoi serializzare `missingFonts` in JSON, scriverlo in un database o inviare un riepilogo via email.

### 4.3 Lavorare con PDF o Altri Formati

Lo stesso approccio con `LoadOptions` funziona per le chiamate `Load` su PDF, RTF e persino file HTML. Basta passare la stessa istanza di opzioni e Aspose.Words genererà avvisi per qualsiasi font non trovabile.

## Passo 5 – Verificare il Risultato Programmaticamente

Se preferisci un test automatizzato invece di controllare manualmente la console, verifica che la lista contenga le voci attese:

```csharp
        // Simple verification (use a testing framework in real projects)
        if (missingFonts.Count == 0)
        {
            Console.WriteLine("All fonts were available – no substitution warnings.");
        }
        else
        {
            Console.WriteLine($"Total missing fonts detected: {missingFonts.Count}");
        }
```

Questo frammento dimostra **come catturare i font mancanti** nel codice, non solo nei log.

## Problemi Comuni & Come Evitarli

| Problema | Perché accade | Soluzione |
|----------|----------------|-----------|
| Dimenticare di impostare `RaiseTypedWarnings` | Il valore predefinito è `DoNotRaise`, quindi nessun evento viene generato. | Imposta esplicitamente `FontSubstitutionWarning` come mostrato al Passo 1. |
| Usare `Console.WriteLine` in un'app web | L'output della console scompare in IIS/ASP.NET Core. | Passa a un logger persistente (es. Serilog). |
| Caricare un documento con percorso relativo | La directory di lavoro può differire a runtime. | Usa percorsi assoluti o `Path.Combine(AppContext.BaseDirectory, "input.docx")`. |
| Ignorare `SubstitutedFontName` | Perdi informazioni su quale fallback è stato scelto. | Registra sempre sia `FontName` che `SubstitutedFontName`. |

## Bonus: Automatizzare l'Installazione dei Font

Se controlli l'ambiente di distribuzione, puoi pre‑installare i font mancanti con uno script PowerShell:

```powershell
$fonts = @("MyFancyFont.ttf", "AnotherMissingFont.otf")
foreach ($font in $fonts) {
    $dest = "$env:SystemRoot\Fonts\$font"
    Copy-Item -Path ".\fonts\$font" -Destination $dest -Force
}
```

Eseguire questo script prima dell'avvio dell'applicazione elimina la maggior parte degli avvisi di **detect missing fonts**.

## Conclusione

Abbiamo coperto tutto ciò che serve per **log font substitution warnings** durante il caricamento di documenti Word con Aspose.Words. Configurando `LoadOptions`, sottoscrivendo l'evento di avviso e, facoltativamente, persistendo i risultati, puoi rilevare in modo affidabile i font mancanti e capire **come catturare i font mancanti** per qualsiasi progetto .NET.

Prendi il codice, adatta il logger al tuo stack e non sarai più sorpreso da uno scambio di font silenzioso. I prossimi passi potrebbero includere:

- Integrare la lista di avvisi nel tuo pipeline CI/CD per far fallire le build quando mancano font critici.  
- Estendere l'approccio per monitorare l'uso dei font su un'intera flotta di documenti.  
- Esplorare l'API `FontSettings` di Aspose.Words per fornire fallback personalizzati.

Hai domande o uno scenario complesso? Lascia un commento e risolviamo insieme. Buon coding!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}