---
category: general
date: 2026-03-27
description: 'Sostituzione dei font Aspose semplificata: impara a configurare le impostazioni
  dei font, catturare gli avvisi e gestire i font mancanti nelle tue app .NET.'
draft: false
keywords:
- aspose font substitution
- configure font settings
- Aspose.Words warning callback
- FontSubstitutionWarningHandler
- LoadOptions example
language: it
og_description: Padroneggia la sostituzione dei font Aspose configurando le impostazioni
  dei font e gestendo i font mancanti con una callback di avviso. Guida completa in
  C#.
og_title: Sostituzione dei Font Aspose – Configura le Impostazioni dei Font in C#
tags:
- Aspose.Words
- C#
- Font Management
title: Sostituzione dei Font Aspose – Come Configurare le Impostazioni dei Font in
  C#
url: /it/net/working-with-fonts/aspose-font-substitution-how-to-configure-font-settings-in-c/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Sostituzione dei Font Aspose – Guida Completa per Configurare le Impostazioni dei Font

Ti è mai capitato di aprire un documento che improvvisamente sostituisce il tuo carattere personalizzato con qualcosa di generico? È la **aspose font substitution** al lavoro—sostituendo i font mancanti con la corrispondenza più vicina che riesce a trovare. È comodo, ma se hai bisogno di sapere *esattamente* quale font è stato sostituito, devi accedere al sistema di avvisi della libreria e configurare le impostazioni dei font da solo.

In questo tutorial percorreremo uno scenario reale: caricare un DOCX che fa riferimento a un font che non possiedi, catturare l'evento di sostituzione e stampare un messaggio amichevole sulla console. Alla fine sarai a tuo agio con **configure font settings**, configurando un **Aspose.Words warning callback**, e potrai estendere l'esempio per adattarlo a qualsiasi flusso di lavoro.

> **Cosa ti servirà**  
> • .NET 6+ (or .NET Framework 4.7.2+)  
> • Aspose.Words for .NET (latest NuGet)  
> • Un DOCX che fa riferimento a un font mancante (lo chiameremo `MissingFont.docx`)  

Iniziamo.

---

## Passo 1: Installa Aspose.Words e Prepara il Progetto

Prima di scrivere qualsiasi codice, assicurati che il pacchetto Aspose.Words sia referenziato:

```bash
dotnet add package Aspose.Words
```

> **Consiglio professionale:** usa l'ultima versione stabile; a partire da marzo 2026 è la 23.11.0. Le versioni più recenti migliorano gli algoritmi di corrispondenza dei font e aggiungono nuovi tipi di avviso.

Crea una nuova applicazione console (o inserisci il codice in un progetto esistente) e aggiungi le consuete direttive `using`:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;
```

Questi namespace ci danno accesso a `Document`, `LoadOptions` e alle classi correlate ai font di cui avremo bisogno.

## Passo 2: Configura le Impostazioni dei Font con LoadOptions

Il cuore del controllo **aspose font substitution** risiede in `LoadOptions.FontSettings`. Fornendo un oggetto `FontSettings` vuoto, diciamo ad Aspose di usare i percorsi di ricerca predefiniti *e* di segnalare qualsiasi sostituzione tramite un callback di avviso.

```csharp
// Step 2: Prepare LoadOptions with a fresh FontSettings instance
LoadOptions loadOptions = new LoadOptions
{
    FontSettings = new FontSettings()
};
```

Perché non affidarsi semplicemente alle impostazioni predefinite? Perché collegare un callback di avviso (passo successivo) funziona solo quando la proprietà `FontSettings` non è null. Questa piccola riga ci fornisce un hook nel processo di sostituzione senza modificare il comportamento di ricerca dei font.

## Passo 3: Collega un Callback di Avviso per Catturare le Sostituzioni

Aspose.Words implementa l'interfaccia `IWarningCallback`. Ogni volta che accade qualcosa di degno di nota—come un font mancante—chiama il nostro metodo `Warning`. Implementeremo un piccolo gestore che filtra per `WarningType.FontSubstitution` e stampa la descrizione.

```csharp
// Step 3: Register the warning handler
loadOptions.WarningCallback = new FontSubstitutionWarningHandler();
```

Ecco il gestore stesso:

```csharp
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        // Filter only font‑substitution warnings
        if (info.WarningType == WarningType.FontSubstitution)
        {
            // Step 4: Output information about the substituted font
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

> **Perché è importante** – Senza il callback, Aspose sostituisce i font silenziosamente e non sai mai quale è stato usato. Il callback rende il processo trasparente, il che è essenziale per la segnalazione di conformità o per il debug di problemi di layout.

## Passo 4: Carica il Documento Usando le Opzioni Configurate

Ora carichiamo finalmente il documento, passando le `loadOptions` appena preparate. Se il file di origine fa riferimento a un font non installato, il nostro gestore verrà attivato.

```csharp
// Step 4: Load the document with the custom LoadOptions
Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);
```

Sostituisci `YOUR_DIRECTORY` con il percorso reale dove si trova `MissingFont.docx`. Quando esegui il programma, dovresti vedere un output simile a:

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
```

Quella riga ti dice esattamente quale font mancava e quale fallback ha scelto Aspose.

## Passo 5: (Opzionale) Ottimizza i Percorsi di Ricerca dei Font

Se hai una cartella privata con font aziendali, puoi indicare ad Aspose dove cercare prima di ricorrere ai font di sistema. Questo è un uso avanzato di **configure font settings**:

```csharp
// Optional: Add a custom folder to the font search collection
loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", recursive: true);
```

Impostare `recursive: true` fa sì che Aspose scandisca anche le sottocartelle. Ora la libreria proverà prima i tuoi font privati, riducendo la probabilità di sostituzioni indesiderate.

## Esempio Completo Funzionante

Mettendo tutto insieme, ecco il programma completo, pronto per l'esecuzione:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fonts;

class Program
{
    static void Main()
    {
        // 1️⃣ Prepare FontSettings inside LoadOptions
        LoadOptions loadOptions = new LoadOptions
        {
            FontSettings = new FontSettings()
        };

        // 2️⃣ Hook our warning handler
        loadOptions.WarningCallback = new FontSubstitutionWarningHandler();

        // 3️⃣ (Optional) Add a custom font folder
        // loadOptions.FontSettings.SetFontsFolder(@"C:\Company\Fonts", true);

        // 4️⃣ Load the document – triggers warnings if needed
        Document doc = new Document("YOUR_DIRECTORY/MissingFont.docx", loadOptions);

        // 5️⃣ Do something with the document – e.g., save as PDF
        doc.Save("Output.pdf");
        Console.WriteLine("Document processed and saved as Output.pdf");
    }
}

// Warning handler that prints substitution details
class FontSubstitutionWarningHandler : IWarningCallback
{
    public void Warning(WarningInfo info)
    {
        if (info.WarningType == WarningType.FontSubstitution)
        {
            Console.WriteLine($"Font substitution detected: {info.Description}");
        }
    }
}
```

**Output previsto** (quando si incontra un font mancante):

```
Font substitution detected: Font "MyCustomFont" was not found. Substituted with "Arial".
Document processed and saved as Output.pdf
```

Se tutti i font sono presenti, il programma gira silenziosamente (senza avvisi) e produce comunque il PDF.

## Domande Frequenti & Casi Limite

### Cosa succede se devo *impedire* la sostituzione del tutto?

Imposta `FontSettings.SubstitutionSettings` a `null` o usa `FontSettings.FontSubstitutionSettings` per controllare il comportamento. Per esempio:

```csharp
loadOptions.FontSettings.SubstitutionSettings.DefaultFontSubstitution = false;
```

Ora Aspose lancerà un'eccezione invece di sostituire silenziosamente, che può essere catturata e gestita.

### Funziona con altri formati di file (ad es., .doc, .rtf)?

Assolutamente. Lo stesso oggetto `LoadOptions` può essere passato a qualsiasi costruttore `Document` che accetta un percorso di file. Il callback di avviso verrà attivato per tutti i formati che dipendono dai font.

### Posso catturare il nome *esatto* del font di fallback?

Sì. La stringa `info.Description` contiene sia il font mancante sia il sostituto. Se ti serve il nome programmaticamente, puoi analizzarla o usare l'oggetto `FontInfo` (disponibile nelle versioni più recenti).

### Come si comporta in un ambiente multi‑thread?

`FontSettings` **non** è thread‑safe. Crea un `LoadOptions` separato (con il proprio `FontSettings`) per ogni thread, o proteggi l'accesso con un lock.

## Conclusione

Abbiamo coperto tutto ciò di cui hai bisogno per padroneggiare **aspose font substitution** e **configure font settings** in un'applicazione C#:

1. Installa Aspose.Words e aggiungi le dichiarazioni `using` necessarie.  
2. Crea un oggetto `LoadOptions` con un nuovo `FontSettings`.  
3. Collega un `IWarningCallback` personalizzato per evidenziare gli eventi di sostituzione.  
4. Carica il documento, lasciando che il callback segnali eventuali font mancanti.  
5. (Opzionale) Estendi il percorso di ricerca o disabilita completamente la sostituzione.

Con questo modello puoi registrare i font mancanti per la conformità, avvisare gli utenti in un'interfaccia UI, o incorporare automaticamente font di fallback prima della pubblicazione. Successivamente, potresti esplorare le **politiche di sostituzione dei font di Aspose.Words** o integrare il flusso di lavoro in una pipeline di elaborazione documenti più ampia.

Buona programmazione, e che i tuoi documenti vengano sempre visualizzati con il carattere corretto!  

---  

![Diagramma che mostra Aspose.Words caricare un documento, invocare FontSettings, attivare un callback di avviso e visualizzare le informazioni di sostituzione](image-placeholder.png "flusso di lavoro della sostituzione dei font Aspose")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}