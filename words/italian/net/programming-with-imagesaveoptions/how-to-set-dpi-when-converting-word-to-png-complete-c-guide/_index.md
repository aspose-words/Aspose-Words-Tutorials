---
category: general
date: 2025-12-29
description: Scopri come impostare i DPI durante la conversione da Word a PNG con
  Aspose.Words. Questo tutorial passo‑passo copre anche l'esportazione PNG ad alta
  risoluzione e le impostazioni della risoluzione dell'immagine.
draft: false
keywords:
- how to set dpi
- convert word to png
- save word as png
- high resolution png export
- set image resolution png
language: it
og_description: Come impostare i DPI durante la conversione da Word a PNG usando Aspose.Words.
  Segui questa guida per l'esportazione PNG ad alta risoluzione e il controllo della
  risoluzione dell'immagine.
og_title: Come impostare DPI durante la conversione da Word a PNG – Guida completa
  C#
tags:
- Aspose.Words
- C#
- Image Export
title: Come impostare i DPI durante la conversione da Word a PNG – Guida completa
  in C#
url: /it/net/programming-with-imagesaveoptions/how-to-set-dpi-when-converting-word-to-png-complete-c-guide/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Come impostare DPI durante la conversione da Word a PNG – Guida completa C# 

Ti sei mai chiesto **come impostare DPI** mentre converti un documento Word in PNG? Forse ti servono screenshot nitidi per una presentazione, o stai generando risorse stampabili che devono apparire nitide a 300 dpi. In ogni caso, sei nel posto giusto. In questo tutorial vedremo come convertire un `.docx` multipagina in immagini PNG ad alta risoluzione usando Aspose.Words, e ti mostreremo esattamente come impostare la risoluzione dell’immagine affinché l’output non sia sfocato.

Inseriremo anche consigli su **convert word to png**, **save word as png**, e otterrai una **high resolution png export** senza sforzo. Nessun documento esterno, solo un esempio autonomo e eseguibile che puoi copiare‑incollare in Visual Studio.

---

## Cosa ti serve

- **Aspose.Words for .NET** (ultima versione, ad es., 24.9).  
- .NET 6+ (o .NET Framework 4.7.2+) – qualsiasi runtime recente funziona.  
- Un file Word (`MultiPage.docx`) che vuoi trasformare in PNG.  
- Un ambiente di sviluppo – Visual Studio, Rider o VS Code vanno bene.  

Tutto qui. Nessun pacchetto NuGet aggiuntivo oltre a Aspose.Words.

---

## Passo 1: Carica il documento Word

Prima di tutto: abbiamo bisogno di una rappresentazione in memoria del file Word. La classe `Document` lo fa per noi.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;

// Load the multi‑page document from disk
Document multiPageDoc = new Document("YOUR_DIRECTORY/MultiPage.docx");
```

> **Perché è importante:** Caricare il documento ci dà accesso al suo `PageCount`, che ci servirà più tardi quando diremo ad Aspose di esportare **tutte le pagine** come PNG.

---

## Passo 2: Configura ImageSaveOptions con le impostazioni DPI

Ora diciamo ad Aspose che vogliamo un output PNG *e* specifichiamo il DPI. Le proprietà `ImageHorizontalResolution` e `ImageVerticalResolution` sono dove avviene la magia.

```csharp
// Create PNG save options and set the DPI to 300
ImageSaveOptions imageSaveOptions = new ImageSaveOptions(SaveFormat.Png)
{
    // Export every page (0‑based index to PageCount‑1)
    PageSet = new PageSet(0, multiPageDoc.PageCount - 1),

    // Set image resolution – this is the “how to set dpi” part
    ImageHorizontalResolution = 300, // 300 DPI horizontally
    ImageVerticalResolution   = 300, // 300 DPI vertically

    // Give each page a friendly file name
    PageSavingCallback = (sender, args) =>
    {
        args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
    }
};
```

> **Consiglio professionale:** 300 dpi è lo standard de‑facto per grafiche pronte per la stampa. Se ti serve solo la qualità per schermo, 96 dpi ridurrà drasticamente le dimensioni del file.

---

## Passo 3: Salva tutte le pagine come un unico PNG a mosaico (o file separati)

Aspose ti permette di raggruppare tutte le pagine in un unico PNG a mosaico **oppure** scrivere ogni pagina in un file separato. L'esempio qui sotto mostra l'approccio *a mosaico unico*, ma il `PageSavingCallback` che abbiamo aggiunto garantisce già che vengano creati file separati se attivi il flag `ExportImagesAsSeparateFiles`.

```csharp
// Save the whole document as a tiled PNG file
multiPageDoc.Save("YOUR_DIRECTORY/Pages.png", imageSaveOptions);
```

Se preferisci un file per pagina, imposta semplicemente:

```csharp
imageSaveOptions.ExportImagesAsSeparateFiles = true;
```

e il callback si occuperà di nominare ogni `Page_#.png`.

---

## Passo 4: Verifica l'output

Dopo aver eseguito il codice, apri `Pages.png` (o i file `Page_#.png` generati) in qualsiasi visualizzatore di immagini. Dovresti vedere immagini nitide e ad alta risoluzione che corrispondono al layout delle pagine Word originali.

- **Controllo della risoluzione:** Click destro → Proprietà → Dettagli → DPI orizzontale / DPI verticale → dovrebbe indicare **300**.  
- **Controllo delle dimensioni:** A 300 dpi, una tipica pagina A4 (8,27 in × 11,69 in) diventa circa 2481 × 3508 pixel – perfetta per la stampa.

---

## Problemi comuni e come evitarli

| Problema | Perché accade | Soluzione |
|-------|----------------|-----|
| **Output sfocato** | DPI lasciato al valore predefinito (96) | Impostare esplicitamente `ImageHorizontalResolution` **e** `ImageVerticalResolution`. |
| **Pagine mancanti** | `PageSet` copre solo un sottoinsieme | Usare `new PageSet(0, multiPageDoc.PageCount - 1)` per includere tutte le pagine. |
| **Collisioni di nome file** | Callback non impostato | Fornire un `PageSavingCallback` che genera nomi unici. |
| **Dimensioni file grandi** | 600 dpi o superiore senza necessità | Scegliere il DPI più basso che soddisfi comunque i requisiti di qualità. |
| **Errori di out‑of‑memory** per documenti enormi | Esportazione di un PNG a mosaico massiccio | Passare a `ExportImagesAsSeparateFiles = true` per scrivere ogni pagina singolarmente. |

---

## Avanzato: Esporta in varianti PNG diverse

A volte hai bisogno di uno **sfondo trasparente** o di una **profondità di colore diversa**. Aspose.Words supporta queste modifiche tramite `PngOptions` all'interno di `ImageSaveOptions`.

```csharp
imageSaveOptions.PngOptions = new PngOptions
{
    // Enable transparency
    Transparency = true,

    // 8‑bit color depth (smaller file) or 24‑bit for full color
    BitDepth = 24
};
```

Puoi anche combinare questo con le impostazioni DPI sopra per ottenere una **high resolution png export** pronta sia per il web che per la stampa.

---

## Esempio completo funzionante

Di seguito trovi il programma completo, pronto per il copia‑incolla. Sostituisci semplicemente `YOUR_DIRECTORY` con il percorso reale sul tuo computer.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;

class Program
{
    static void Main()
    {
        // 1️⃣ Load the Word document
        Document doc = new Document("YOUR_DIRECTORY/MultiPage.docx");

        // 2️⃣ Configure PNG export with 300 DPI
        ImageSaveOptions options = new ImageSaveOptions(SaveFormat.Png)
        {
            PageSet = new PageSet(0, doc.PageCount - 1),
            ImageHorizontalResolution = 300,
            ImageVerticalResolution = 300,
            // Optional: separate files per page
            // ExportImagesAsSeparateFiles = true,

            // 3️⃣ Friendly file names for each page
            PageSavingCallback = (sender, args) =>
            {
                args.ImageFileName = $"Page_{args.PageIndex + 1}.png";
            },

            // 4️⃣ High‑resolution PNG tweaks (transparent background, 24‑bit)
            PngOptions = new PngOptions
            {
                Transparency = true,
                BitDepth = 24
            }
        };

        // 5️⃣ Save – either a tiled PNG or separate files
        doc.Save("YOUR_DIRECTORY/Pages.png", options);

        Console.WriteLine("Conversion complete! Check YOUR_DIRECTORY for the PNG files.");
    }
}
```

Esegui il programma e otterrai una **high resolution PNG export** di ogni pagina, ciascuna con il DPI esatto impostato.

---

## Domande frequenti

**D: Questo funziona con file `.doc` più vecchi?**  
R: Assolutamente. Aspose.Words astrae il formato, quindi lo stesso codice gestisce `.doc`, `.docx`, `.rtf` e anche `.odt`.

**D: Posso esportare in JPEG invece di PNG?**  
R: Sì – basta cambiare `SaveFormat.Png` in `SaveFormat.Jpeg` e, se necessario, regolare `JpegOptions`.

**D: Cosa succede se ho bisogno di 600 dpi per un grande poster?**  
R: Imposta `ImageHorizontalResolution = 600` e `ImageVerticalResolution = 600`. Tieni d'occhio l'uso della memoria; valori DPI elevati aumentano rapidamente le dimensioni in pixel.

**D: Esiste un modo per elaborare in batch molti file Word?**  
R: Avvolgi la logica sopra in un ciclo `foreach (var file in Directory.GetFiles(folder, "*.docx"))`. Ricorda di eliminare ogni istanza di `Document` o di riutilizzare un unico oggetto `ImageSaveOptions` per efficienza.

---

## Conclusione

Abbiamo coperto **come impostare DPI** quando **converti Word in PNG** usando Aspose.Words, affrontato le sfumature di **high resolution PNG export**, e fornito un esempio di codice pronto all'uso che **save word as png** con controllo preciso della risoluzione dell'immagine. Modificando `ImageHorizontalResolution`, `ImageVerticalResolution` e opzionalmente `PngOptions`, puoi generare grafiche pronte per la stampa o risorse web leggere con sicurezza.

Prossimi passi? Prova a sperimentare con valori DPI diversi, passa all'esportazione in file separati, o combina questo flusso di lavoro con una pipeline PDF‑to‑PNG per una gestione dei documenti ancora più ampia. Gli stessi principi si applicano quando **set image resolution png** per altri formati, così sei ora pronto a gestire una vasta gamma di scenari di esportazione delle immagini.

Buona programmazione, e che i tuoi PNG siano sempre affilati come rasoi! 

![Come impostare DPI durante la conversione da Word a PNG – esempio di output](/images/how-to-set-dpi-word-to-png.png "come impostare dpi")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}