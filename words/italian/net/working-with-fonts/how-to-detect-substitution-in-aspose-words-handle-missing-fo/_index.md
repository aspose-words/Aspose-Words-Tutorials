---
category: general
date: 2026-04-24
description: Come rilevare la sostituzione dei caratteri mancanti in Aspose.Words
  usando C#. Questa guida mostra come gestire in modo affidabile i caratteri mancanti
  con gli avvisi di FontSettings.
draft: false
keywords:
- how to detect substitution
- handle missing fonts
- Aspose.Words font warnings
- C# missing font detection
- FontSettings event handling
language: it
og_description: Come rilevare la sostituzione di font mancanti in Aspose.Words con
  C#. Impara a gestire i font mancanti usando gli avvisi di FontSettings.
og_title: Come rilevare la sostituzione in Aspose.Words – Guida completa
tags:
- Aspose.Words
- C#
- Fonts
- .NET
title: Come rilevare la sostituzione in Aspose.Words – Gestire i caratteri mancanti
url: /it/net/working-with-fonts/how-to-detect-substitution-in-aspose-words-handle-missing-fo/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come rilevare la sostituzione in Aspose.Words – Gestire i font mancanti

Ti sei mai chiesto **come rilevare la sostituzione** quando un documento tenta di utilizzare un font che non è installato sul tuo server? È un problema comune, soprattutto quando generi PDF o file Word in una pipeline automatizzata. La buona notizia è che Aspose.Words ti fornisce un hook integrato per individuare esattamente questa situazione, e puoi anche **gestire i font mancanti** in modo elegante.

In questo tutorial percorreremo un esempio reale che mostra **come rilevare la sostituzione** tramite l'evento `FontSettings.Warning`, e spiegheremo come **gestire i font mancanti** senza interrompere il flusso di elaborazione. Alla fine avrai uno snippet pronto all'uso, una chiara comprensione del motivo per cui ogni riga è importante, e alcuni consigli per evitare le insidie più comuni.

## Prerequisiti

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework)
- Aspose.Words per .NET (pacchetto NuGet `Aspose.Words`) – versione 23.11 o più recente
- Un documento di esempio che fa riferimento a un font non installato (ad es., `MissingFont.docx`)
- Visual Studio, VS Code, o qualsiasi IDE C# tu preferisca  

La configurazione aggiuntiva non è necessaria oltre all'aggiunta del pacchetto NuGet.

---

## Come rilevare la sostituzione con FontSettings

Il cuore di **come rilevare la sostituzione** risiede nell'evento `FontSettings.Warning`. Quando Aspose.Words non riesce a trovare un font richiesto, genera un avviso `WarningType.FontSubstitution`. Iscrivendoti a questo evento ottieni una notifica in tempo reale, completa del nome del font originale e del font utilizzato come fallback.

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable a custom FontSettings instance.
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};

// Step 2: Hook into the FontSettings warning event – this is where we detect substitution.
loadOptions.FontSettings.Warning += (sender, e) =>
{
    // We only care about font‑substitution warnings.
    if (e.WarningType == WarningType.FontSubstitution)
    {
        // Output the warning to the console – you could log it or collect it in a list.
        Console.WriteLine($"⚠️ Font substituted: {e.Message}");
    }
};

// Step 3: Load the document using the configured LoadOptions.
Document document = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

**Perché funziona:**  
- `LoadOptions.FontSettings` indica ad Aspose.Words di utilizzare l'oggetto `FontSettings` appena creato.  
- L'iscrizione a `Warning` ti fornisce un unico punto per monitorare *tutti* i problemi relativi ai font, non solo quelli mancanti.  
- Il filtro `WarningType.FontSubstitution` garantisce che tu reagisca solo allo scenario esatto di tuo interesse – l'essenza di **come rilevare la sostituzione**.

### Output previsto

Eseguendo il codice sopra con un documento che fa riferimento a un font inesistente verrà stampato qualcosa di simile:

```
⚠️ Font substituted: Font 'Comic Sans MS' was not found. Substituted with 'Arial'.
```

Se il documento utilizza solo font installati, la console rimane silenziosa – un chiaro segnale che **come rilevare la sostituzione** è riuscito senza falsi allarmi.

---

## Gestire i font mancanti in modo elegante

Rilevare una sostituzione è solo metà della battaglia; hai anche bisogno di una strategia per **gestire i font mancanti** in modo che l'output finale abbia l'aspetto desiderato. Di seguito tre approcci pratici che puoi combinare.

### 1. Fornire una cartella di font di fallback

Aspose.Words può cercare font in directory aggiuntive. Puntandolo a una cartella che contiene i font più comuni che ti aspetti, riduci completamente la possibilità di una sostituzione.

```csharp
// Assume you have a folder "FallbackFonts" with Arial, Times New Roman, etc.
loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", recursive: true);
```

**Perché:** Quando il font originale è mancante, Aspose.Words ha ora un insieme noto di alternative, il che spesso produce un risultato visivo più prevedibile.

### 2. Sostituire i font mancanti programmaticamente

Se desideri il pieno controllo, puoi sostituire il font mancante con uno specifico dopo la rilevazione.

```csharp
loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes("Comic Sans MS", new[] { "Arial", "Helvetica" });
```

**Perché:** Questo indica al motore esattamente quali font provare, permettendoti di applicare il branding aziendale o gli standard di accessibilità.

### 3. Registrare e abortire (quando la sostituzione è inaccettabile)

A volte un font mancante significa che il documento è non valido per il tuo caso d'uso (ad es., moduli legali). In quello scenario puoi lanciare un'eccezione non appena si verifica una sostituzione.

```csharp
loadOptions.FontSettings.Warning += (sender, e) =>
{
    if (e.WarningType == WarningType.FontSubstitution)
        throw new InvalidOperationException($"Critical font missing: {e.Message}");
};
```

**Perché:** Un fallimento immediato previene errori a valle, come tabelle disallineate o firme rotte.

---

## Esempio completo funzionante – Tutti i passaggi combinati

Di seguito trovi un unico programma pronto per il copia‑incolla che dimostra **come rilevare la sostituzione** *e* diversi modi per **gestire i font mancanti**. Sentiti libero di commentare le sezioni di cui non hai bisogno.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // -------------------------------------------------
        // 1️⃣ Set up LoadOptions with a fresh FontSettings.
        // -------------------------------------------------
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // -------------------------------------------------
        // 2️⃣ OPTIONAL: Add a fallback folder with extra fonts.
        // -------------------------------------------------
        // loadOptions.FontSettings.SetFontsFolder(@"C:\FallbackFonts", true);

        // -------------------------------------------------
        // 3️⃣ OPTIONAL: Define explicit substitution rules.
        // -------------------------------------------------
        // loadOptions.FontSettings.SubstitutionSettings.FontSubstitutes.AddSubstitutes(
        //     "Comic Sans MS", new[] { "Arial", "Helvetica" });

        // -------------------------------------------------
        // 4️⃣ Subscribe to the warning event – the heart of how to detect substitution.
        // -------------------------------------------------
        loadOptions.FontSettings.Warning += (sender, e) =>
        {
            if (e.WarningType == WarningType.FontSubstitution)
            {
                // Log the warning – you could also collect it in a list for later analysis.
                Console.WriteLine($"⚠️ Font substituted: {e.Message}");

                // Uncomment to abort on any substitution.
                // throw new InvalidOperationException($"Missing font detected: {e.Message}");
            }
        };

        // -------------------------------------------------
        // 5️⃣ Load the document; the warning handler fires automatically.
        // -------------------------------------------------
        string docPath = @"YOUR_DIRECTORY/MissingFont.docx";
        Document doc = new Document(docPath, loadOptions);

        // -------------------------------------------------
        // 6️⃣ Save the result – you’ll see the substituted font in the output file.
        // -------------------------------------------------
        string outPath = @"YOUR_DIRECTORY/Processed.docx";
        doc.Save(outPath);
        Console.WriteLine($"Document saved to {outPath}");
    }
}
```

**Cosa aspettarsi:**  
- Se `MissingFont.docx` fa riferimento a un font che non è presente sulla macchina, la console stampa l'avviso di sostituzione.  
- Il `Processed.docx` salvato utilizza il font di fallback configurato (o quello predefinito della libreria).  
- Non compaiono eccezioni non gestite a meno che tu non abortisca deliberatamente alla sostituzione.

---

## Domande comuni e casi limite

| Domanda | Risposta |
|----------|--------|
| *E se il documento contiene molti font mancanti?* | L'evento di avviso si attiva per **ogni** sostituzione, quindi vedrai più righe. Puoi aggregarle in un elenco per un report riepilogativo. |
| *Funziona con la conversione PDF?* | Assolutamente. Gli stessi `FontSettings` vengono rispettati quando chiami `doc.Save("out.pdf")`. L'avviso di sostituzione si attiva comunque, permettendoti di verificare la fedeltà visiva del PDF. |
| *Posso rilevare la sostituzione dopo che il documento è già stato caricato?* | Non direttamente. L'avviso viene generato **durante** il caricamento o il salvataggio. Se hai bisogno di un'analisi post‑caricamento, cattura gli avvisi in una collezione durante la fase di caricamento. |
| *E per i font personalizzati incorporati nel DOCX?* | I font incorporati sono considerati presenti, quindi non avviene alcuna sostituzione. Se il font incorporato è corrotto, Aspose.Words genera comunque un avviso, che puoi catturare allo stesso modo. |
| *C'è un impatto sulle prestazioni?* | Minimo. Il controllo degli avvisi è leggero; il vero costo è il caricamento del documento stesso. Aggiungere una cartella di font può aumentare leggermente il tempo di ricerca, ma solo al primo caricamento. |

---

## Consigli professionali e trappole da evitare

- **Consiglio professionale:** Imposta sempre `recursive: true` quando punti a una cartella con molti font; altrimenti le sottocartelle vengono ignorate.  
- **Attenzione a:** La sensibilità al maiuscolo/minuscolo su Linux. I nomi dei font sono case‑insensitive su Windows ma non su Linux, quindi usa il nome esatto o aggiungi entrambe le varianti.  
- **Ricorda:** Se esegui in un ambiente containerizzato, assicurati che la cartella dei font faccia parte dell'immagine o sia montata a runtime.  
- **Suggerimento:** Conserva gli avvisi in una `List<string>` se devi presentare un riepilogo agli utenti finali o registrarli in un sistema di monitoraggio.  

---

## Conclusione

Abbiamo coperto **come rilevare la sostituzione** dei font mancanti in Aspose.Words, mostrato diversi modi per **gestire i font mancanti**, e fornito un esempio completo e eseguibile che puoi inserire in qualsiasi progetto .NET. Accedendo all'evento `FontSettings.Warning` ottieni visibilità in tempo reale sui problemi dei font, e con cartelle di fallback o regole di sostituzione esplicite mantieni l'output esattamente come ti aspetti.

Pronto per il passo successivo? Prova a estendere la soluzione per incorporare automaticamente il font di fallback nel PDF generato, o collega il gestore degli avvisi a un servizio di logging centralizzato per pipeline di documenti su larga scala. I pattern di cui abbiamo parlato oggi—rilevamento basato su eventi, fallback elegante e gestione esplicita degli errori—si applicano a molte altre API di Aspose, così sei ora pronto ad affrontare le sfide legate ai font in tutti i contesti.

Hai altre domande sulla gestione dei font, la conversione PDF o trucchi di Aspose.Words? Lascia un commento qui sotto, e buona programmazione!

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}