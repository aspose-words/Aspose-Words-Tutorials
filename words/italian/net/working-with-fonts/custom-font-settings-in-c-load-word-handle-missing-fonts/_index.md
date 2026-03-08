---
category: general
date: 2026-03-08
description: Le impostazioni personalizzate dei caratteri ti consentono di impostare
  le opzioni dei caratteri, caricare in modo sicuro i documenti Word e gestire i caratteri
  mancanti con Aspose.Words.
draft: false
keywords:
- custom font settings
- set font settings
- load word document
- handle missing fonts
language: it
og_description: Le impostazioni personalizzate dei font ti consentono di configurare
  i font, caricare in modo sicuro i documenti Word e gestire i font mancanti con Aspose.Words.
og_title: Impostazioni di Font Personalizzate in C# – Carica Word e Gestisci i Font
  Mancanti
tags:
- Aspose.Words
- C#
- Font Management
title: Impostazioni di Font Personalizzate in C# – Carica Word e Gestisci i Font Mancanti
url: /it/net/working-with-fonts/custom-font-settings-in-c-load-word-handle-missing-fonts/
---

Word & Handle Missing Fonts" => "Impostazioni di Font Personalizzate in C# – Carica Word e Gestisci i Font Mancanti"

Paragraphs accordingly.

Make sure to keep **bold** formatting.

Translate bullet points.

Translate table.

Let's write.

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Impostazioni di Font Personalizzate in C# – Carica Word e Gestisci i Font Mancanti

Ti sei mai chiesto come funzionano le **impostazioni di font personalizzate** quando un file Word fa riferimento a font che non hai installato? È un inconveniente comune: il documento appare corretto su una macchina, poi improvvisamente ogni paragrafo passa a un font di fallback su un'altra.  

La buona notizia? Con Aspose.Words puoi **impostare le impostazioni dei font**, **caricare il contenuto del documento Word** e **gestire i font mancanti** tutto in un unico flusso ordinato. Di seguito trovi un esempio completo, pronto per l'esecuzione, che mostra esattamente come fare, più il “perché” di ogni passaggio.

## What You’ll Learn

In questa guida tratteremo:

* Creare un oggetto `LoadOptions` e collegare un'istanza `FontSettings`.  
* Registrare una callback di avviso in modo da vedere quali font vengono sostituiti.  
* Caricare un file DOCX che potrebbe avere font mancanti e stampare i dettagli della sostituzione sulla console.  

Al termine sarai in grado di distribuire la tua app C# con fiducia, sapendo che ogni scenario di font mancante viene registrato e potrà essere gestito in seguito.

> **Prerequisite:** Aspose.Words for .NET (v23.12 o più recente) installato tramite NuGet, e una conoscenza di base delle app console C#.

---

## Custom Font Settings – Configure LoadOptions

La prima cosa di cui hai bisogno è un oggetto `LoadOptions`. Questo indica ad Aspose.Words come trattare il file in ingresso. Assegnando una nuova istanza `FontSettings` forniamo alla libreria un luogo dove cercare i font personalizzati.

```csharp
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

// Step 1: Create LoadOptions and enable custom font settings.
LoadOptions loadOptions = new LoadOptions
{
    // Attach a new FontSettings object – it starts empty.
    FontSettings = new FontSettings()
};
```

**Perché è importante:**  
Se ometti `FontSettings`, Aspose.Words ricade nella collezione di font predefinita del sistema. Ciò significa che qualsiasi font mancante verrà sostituito silenziosamente, e non saprai quali sono stati scambiati. Creando un contenitore `FontSettings` esplicito ottieni il pieno controllo sul processo di ricerca.

---

## Set Font Settings on LoadOptions

Ora che abbiamo un oggetto `FontSettings`, ti starai chiedendo dove puntarlo. Tipicamente aggiungeresti una cartella che contiene i font che distribuisci con la tua applicazione:

```csharp
// Optional: add a custom folder that holds your private fonts.
string customFontFolder = @"C:\MyApp\Fonts";
loadOptions.FontSettings.SetFontsFolder(customFontFolder, recursive: true);
```

*Se non disponi di una cartella privata, puoi omettere questo blocco—Aspose.Words segnalerà comunque i font mancanti tramite la callback di avviso.*

**Suggerimento professionale:** Usa il flag `recursive: true` se i tuoi font sono sparsi in sottocartelle. Ti evita di dover aggiungere manualmente ogni percorso.

---

## Load Word Document with Custom Font Settings

Con le opzioni pronte, caricare il documento è un gioco da ragazzi. Il costruttore `Document` accetta il percorso del file e il `LoadOptions` che abbiamo appena creato.

```csharp
// Step 2: Attach a warning callback to capture font substitution details.
loadOptions.WarningCallback = new FontWarningHandler();

// Step 3: Load the document that may contain missing fonts using the configured options.
Document doc = new Document(@"C:\MyApp\Docs\input.docx", loadOptions);
```

**Cosa succede dietro le quinte?**  
Aspose.Words analizza il DOCX, controlla ogni riferimento `<w:font>` e consulta le `FontSettings` fornite. Se un font non viene trovato, genera un avviso di tipo `FontSubstitution`. Il nostro gestore personalizzato (mostrato di seguito) catturerà quegli avvisi.

---

## Handle Missing Fonts with Warning Callback

L'interfaccia `IWarningCallback` ti consente di reagire a qualsiasi problema che si verifichi durante il caricamento. Implementarla è semplice:

```csharp
public class FontWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Step 4: When a font substitution occurs, output the substituted font name.
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substituted: {info.Description}");
        }
    }
}
```

Quando il documento viene caricato, ogni font mancante genererà una riga del tipo:

```
Font substituted: Arial -> Liberation Sans
```

**Perché dovresti registrare questo:**  
In produzione puoi reindirizzare questi messaggi a un file o a un sistema di telemetria, rendendo facile individuare quali font devi includere o licenziare.

---

## Full Working Example

Di seguito trovi un programma console autonomo che unisce tutti i pezzi. Copialo e incollalo in un nuovo progetto console .NET Core e premi **Run**.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.LoadOptions;
using Aspose.Words.Fonts;

namespace FontDemo
{
    class Program
    {
        static void Main(string[] args)
        {
            // 1️⃣ Create LoadOptions with a fresh FontSettings instance.
            LoadOptions loadOptions = new LoadOptions
            {
                FontSettings = new FontSettings()
            };

            // OPTIONAL: Point to a folder that contains your private fonts.
            // Uncomment and adjust the path if you have custom fonts.
            // loadOptions.FontSettings.SetFontsFolder(@"C:\MyApp\Fonts", true);

            // 2️⃣ Register a warning callback to capture missing‑font events.
            loadOptions.WarningCallback = new FontWarningHandler();

            // 3️⃣ Load the Word document using the custom options.
            string docPath = @"C:\MyApp\Docs\input.docx";
            Document doc = new Document(docPath, loadOptions);

            // 4️⃣ (Optional) Save the document to another format to verify it loaded correctly.
            doc.Save(@"C:\MyApp\Docs\output.pdf");
            Console.WriteLine("Document loaded and saved as PDF successfully.");
        }
    }

    // 5️⃣ Warning handler that prints font substitution details.
    public class FontWarningHandler : IWarningCallback
    {
        public void Warning(WarningInfo info)
        {
            if (info.WarningType == WarningType.FontSubstitution)
            {
                Console.WriteLine($"Font substituted: {info.Description}");
            }
        }
    }
}
```

**Output previsto** (supponendo che `input.docx` utilizzi un font che non possiedi):

```
Font substituted: Times New Roman -> Liberation Serif
Font substituted: Calibri -> Arial
Document loaded and saved as PDF successfully.
```

Se tutti i font sono presenti, vedrai solo la riga di conferma finale.

---

## Common Questions & Edge Cases

| Question | Answer |
|----------|--------|
| **What if I need to embed the missing fonts into the PDF?** | After loading, call `doc.FontSettings.SubstitutionSettings.FontSubstitutionRule.DefaultFontName = "YourFallback";` and then enable embedding with `doc.FontSettings.EmbeddingMode = FontEmbeddingMode.Embedding;`. |
| **Can I suppress the warnings instead of logging them?** | Yes—set `loadOptions.WarningCallback = null;` or implement the callback to ignore non‑font warnings. |
| **Does this work with `.doc` and `.rtf` files?** | Absolutely. The same `LoadOptions` object applies to any format supported by Aspose.Words. |
| **Is the callback thread‑safe?** | The callback runs on the same thread that loads the document, so you can safely write to the console. For multi‑threaded scenarios, use a concurrent collection or logging framework. |

---

## Pro Tips & Pitfalls

* **Pro tip:** Se distribuisci un font che non è installato sulla macchina di destinazione, aggiungilo alla cartella che passi a `SetFontsFolder`. Questo garantisce un rendering deterministico.
* **Attenzione alle licenze:** Alcuni font richiedono licenze commerciali per l'incorporamento. Verifica sempre l'EULA del font prima di includerlo.
* **Nota sulle prestazioni:** Caricare grandi librerie di font può rallentare l'analisi del documento. Mantieni la cartella snella—incluse solo i font realmente necessari.
* **Caso limite:** Quando un documento fa riferimento a un font tramite il suo *nome PostScript* anziché il nome della famiglia, Aspose.Words lo risolve comunque purché il file del font sia presente nel percorso di ricerca.

---

## Conclusion

Ora disponi di un modello completo, pronto per la produzione, per utilizzare **impostazioni di font personalizzate** in C#. Configurando `LoadOptions`, registrando una callback di avviso e, facoltativamente, puntando a una cartella privata di font, puoi **impostare le impostazioni dei font**, **caricare il contenuto del documento Word** in modo affidabile.

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}