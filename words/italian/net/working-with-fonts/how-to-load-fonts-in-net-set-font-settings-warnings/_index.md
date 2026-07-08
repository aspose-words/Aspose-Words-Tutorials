---
category: general
date: 2026-06-30
description: Impara come caricare i font in .NET usando LoadOptions, impostare le
  impostazioni dei font, abilitare i font personalizzati e rilevare i font mancanti
  con callback di avviso.
draft: false
keywords:
- how to load fonts
- set font settings
- how to handle warnings
- enable custom fonts
- detect missing fonts
language: it
og_description: Come caricare i font in .NET? Questa guida ti mostra come impostare
  le impostazioni dei font, abilitare i font personalizzati e rilevare i font mancanti
  con callback di avviso.
og_title: Come caricare i font in .NET – Impostare le impostazioni dei font e gli
  avvisi
schemas:
- author: Aspose
  dateModified: '2026-06-30'
  description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  headline: How to Load Fonts in .NET – Set Font Settings & Warnings
  type: TechArticle
- description: Learn how to load fonts in .NET using LoadOptions, set font settings,
    enable custom fonts and detect missing fonts with warning callbacks.
  name: How to Load Fonts in .NET – Set Font Settings & Warnings
  steps:
  - name: Creating `LoadOptions` and configuring **set font settings**.
    text: Creating `LoadOptions` and configuring **set font settings**.
  - name: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
    text: '**Enable custom fonts** by pointing to a folder of extra typefaces.'
  - name: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
    text: '**How to handle warnings** with a `WarningCallback` that prints font substitution
      messages.'
  - name: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
    text: '**Detect missing fonts** by filtering `WarningType.FontSubstitution`.'
  - name: Saving the document, confirming that the fallback
    text: Saving the document, confirming that the fallback
  type: HowTo
tags:
- Aspose.Words
- .NET
- Font Management
title: Come caricare i font in .NET – Impostare le impostazioni dei font e gli avvisi
url: /it/net/working-with-fonts/how-to-load-fonts-in-net-set-font-settings-warnings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come Caricare i Font in .NET – Impostare le Impostazioni dei Font e gli Avvisi

Ti sei mai chiesto **come caricare i font** in un documento .NET senza impazzire? Non sei l'unico. Glyph mancanti, fallback silenziosi e avvisi criptici possono trasformare un semplice generatore di report in un incubo.  

In questo tutorial percorreremo un esempio completo, pronto‑da‑eseguire, che mostra **come caricare i font**, configurare le **impostazioni dei font**, **abilitare i font personalizzati** e **rilevare i font mancanti** gestendo gli avvisi. Alla fine avrai uno schema solido da inserire in qualsiasi progetto Aspose.Words o libreria simile.

> **Sguardo rapido:** creeremo un oggetto `LoadOptions`, collegheremo un callback per gli avvisi e caricheremo un DOCX che fa riferimento deliberatamente a un tipo di carattere mancante. La console stamperà un messaggio chiaro ogni volta che il motore sostituirà un font.

## Cosa Ti Serve

- .NET 6.0 o successivo (il codice funziona anche su .NET Framework 4.6+)  
- Aspose.Words per .NET (va bene il pacchetto NuGet di prova)  
- Un file DOCX che fa riferimento a un font che *non* hai installato (ad es., `MissingFont.docx`)  

Tutto qui—nessun servizio aggiuntivo, nessun file di configurazione oscuro. Se hai questi tre elementi, sei pronto a seguire.

![how to load fonts example diagram](https://example.com/how-to-load-fonts-diagram.png)

*Testo alternativo immagine: diagramma di esempio su come caricare i font*

## Passo 1: Creare le Opzioni di Caricamento e Abilitare le Impostazioni dei Font Personalizzati  

La prima cosa da fare quando vuoi **impostare le impostazioni dei font** è istanziare un oggetto `LoadOptions`. All’interno di esso inserisci un’istanza di `FontSettings` che punta a una cartella contenente tutti i file .ttf o .otf personalizzati di cui potresti aver bisogno.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // Step 1: Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // Point to a folder that holds extra fonts (optional but useful)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);
```

**Perché è importante:** Per impostazione predefinita Aspose.Words guarda solo i font installati nel sistema. Se il tuo documento utilizza un font aziendale che risiede su una condivisione di rete, devi indicare alla libreria dove trovarlo. Questo è il nocciolo di **abilitare i font personalizzati**.

## Passo 2: Collegare un Handler per gli Avvisi per Rilevare i Font Mancanti  

Se ometti la gestione degli avvisi, i glyph mancanti vengono silenziosamente sostituiti con un font di fallback—spesso Times New Roman. Questo può compromettere il brand o addirittura causare spostamenti di layout. Per **gestire gli avvisi**, collega un callback che ispeziona `WarningType.FontSubstitution`.

```csharp
        // Step 2: Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution detected: {args.Description}");
        };
```

**Consiglio professionale:** Il `WarningCallback` si attiva per *qualsiasi* avviso, non solo per i font mancanti. Filtrare per `WarningType.FontSubstitution` mantiene l’output pulito e risponde direttamente alla domanda **rilevare i font mancanti**.

## Passo 3: Caricare il Documento Utilizzando le Opzioni Configurate  

Ora che abbiamo preparato le opzioni, possiamo finalmente **caricare i font** nel documento. Il costruttore `Document` accetta il percorso del file più le `LoadOptions` appena create.

```csharp
        // Step 3: Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);
```

Se il file sorgente fa riferimento a un font che non è nella cartella di sistema *o* nella cartella personalizzata impostata prima, il callback di avviso del Passo 2 stamperà una riga utile sulla console.

## Passo 4: Verificare il Set di Font Caricato (Facoltativo ma Istruttivo)  

A volte vuoi ricontrollare quali font sono stati effettivamente risolti. Aspose.Words espone le `FontSettings` che hai passato, così puoi enumerare le font source risolte.

```csharp
        // Step 4: (Optional) List all font sources that were used
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");
```

Eseguire questo snippet dopo il caricamento stamperà qualcosa del genere:

```
⚠️ Font substitution detected: Font 'Comic Sans MS' was substituted with 'Arial'.
Loaded font sources:
- FolderFontSource
- SystemFontSource
```

La riga di avviso conferma che abbiamo **rilevato i font mancanti**, mentre l’elenco mostra che sia le cartelle di sistema sia quelle personalizzate sono state consultate.

## Passo 5: Salvare o Renderizzare il Documento  

Una volta che il documento è caricato e hai verificato i font, puoi continuare con qualsiasi elaborazione—salvare come PDF, renderizzare in immagini o manipolare il DOM. Per completezza, ecco una riga di codice che salva il risultato come PDF:

```csharp
        // Step 5: Save the document as PDF (fonts now embedded where possible)
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ Document saved as PDF.");
    }
}
```

Quando il PDF viene aperto, eventuali glyph mancanti saranno stati sostituiti dal fallback mostrato nell’output della console. Se aggiungi il font mancante in `C:\MyCustomFonts`, riesegui il programma e l’avviso scompare—prova che **abilitare i font personalizzati** funziona davvero.

---

## Esempio Completo Funzionante

Copia l’intero blocco qui sotto in un nuovo progetto console, aggiungi il pacchetto NuGet Aspose.Words e premi **Run**. Regola i percorsi dei file in base al tuo ambiente.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Create load options and enable custom font settings
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };
        // Point to a folder with extra fonts (if you have any)
        loadOptions.FontSettings.SetFontsFolder(@"C:\MyCustomFonts", false);

        // 2️⃣ Attach a warning handler to capture font substitution warnings
        loadOptions.WarningCallback = (sender, args) =>
        {
            if (args.WarningType == WarningType.FontSubstitution)
                Console.WriteLine($"⚠️ Font substitution: {args.Description}");
        };

        // 3️⃣ Load the document using the configured options
        Document doc = new Document(@"C:\Docs\DocWithMissingFont.docx", loadOptions);

        // 4️⃣ (Optional) List loaded font sources for debugging
        FontSourcesCollection sources = loadOptions.FontSettings.GetFontSources();
        Console.WriteLine("\nLoaded font sources:");
        foreach (var source in sources)
            Console.WriteLine($"- {source.GetType().Name}");

        // 5️⃣ Save as PDF – you’ll see the same warnings if fonts were missing
        doc.Save(@"C:\Docs\Result.pdf");
        Console.WriteLine("\n✅ PDF saved successfully.");
    }
}
```

### Output Atteso

```
⚠️ Font substitution: Font 'Papyrus' was substituted with 'Arial'.

Loaded font sources:
- FolderFontSource
- SystemFontSource

✅ PDF saved successfully.
```

Se posizioni il file `Papyrus.ttf` mancante in `C:\MyCustomFonts` e riesegui il programma, la riga di avviso scompare, confermando che la cartella personalizzata è stata consultata correttamente.

---

## Domande Frequenti & Trappole

| Domanda | Risposta |
|----------|----------|
| **E se non ho un callback per gli avvisi?** | Il documento viene comunque caricato, ma non saprai quando avviene una sostituzione. Aggiungere il callback è il modo più semplice per **gestire gli avvisi**. |
| **Posso caricare i font da un file zip?** | Sì—usa `new FolderFontSource(zipPath, true)` o implementa un `IFontSource` personalizzato. Questo rientra comunque in **abilitare i font personalizzati**. |
| **Devo incorporare i font nel PDF?** | Imposta `doc.SaveOptions.PdfSaveOptions.EmbedFullFonts = true;` prima di salvare. L’incorporamento garantisce che il PDF abbia lo stesso aspetto su qualsiasi macchina. |
| **E se il documento usa un font con licenza che non può essere ridistribuito?** | Puoi comunque *rilevare* il font mancante tramite gli avvisi, ma non dovresti incorporarlo a meno che non possiedi i diritti. Considera di sostituirlo con un font open‑source simile. |

---

## Riepilogo

Abbiamo coperto **come caricare i font** in .NET:

1. Creare `LoadOptions` e configurare **impostare le impostazioni dei font**.  
2. **Abilitare i font personalizzati** puntando a una cartella di typeface aggiuntivi.  
3. **Gestire gli avvisi** con un `WarningCallback` che stampa messaggi di sostituzione dei font.  
4. **Rilevare i font mancanti** filtrando `WarningType.FontSubstitution`.  
5. Salvare il documento, confermando che il fallback è stato gestito correttamente.

## Cosa Dovresti Imparare Dopo?


I tutorial seguenti trattano argomenti strettamente correlati che si basano sulle tecniche dimostrate in questa guida. Ogni risorsa include esempi di codice completi con spiegazioni passo‑passo per aiutarti a padroneggiare funzionalità aggiuntive dell’API e a esplorare approcci alternativi di implementazione nei tuoi progetti.

- [Impostare le Cartelle dei Font di Sistema e Personalizzate](/words/english/net/working-with-fonts/set-fonts-folders-system-and-custom-folder/)
- [Come Rilevare i Font in Aspose.Words – Gestire Avvisi e Impostazioni](/words/english/net/working-with-fonts/how-to-detect-fonts-in-aspose-words-handle-warnings-settings/)
- [Come Catturare i Font in Aspose.Words – Guida Completa](/words/english/net/working-with-fonts/how-to-capture-fonts-in-aspose-words-complete-guide/)

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}