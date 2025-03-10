---
title: Ottimizza le dimensioni del PDF con Salta i caratteri Arial e Times Roman incorporati
linktitle: Ottimizza le dimensioni del PDF con Salta i caratteri Arial e Times Roman incorporati
second_title: API di elaborazione dei documenti Aspose.Words
description: Ottimizza le dimensioni del PDF saltando i font Arial e Times Roman incorporati usando Aspose.Words per .NET. Segui questa guida passo passo per semplificare i tuoi file PDF.
weight: 10
url: /it/net/programming-with-pdfsaveoptions/skip-embedded-arial-and-times-roman-fonts/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ottimizza le dimensioni del PDF con Salta i caratteri Arial e Times Roman incorporati

## Introduzione

Ti sei mai trovato in una situazione in cui le dimensioni del tuo file PDF sono semplicemente troppo grandi? È come fare i bagagli per una vacanza e accorgersi che la valigia sta scoppiando. Sai che devi perdere un po' di peso, ma a cosa lasci andare? Quando lavori con file PDF, in particolare quelli convertiti da documenti Word, i font incorporati possono gonfiare le dimensioni del file. Fortunatamente, Aspose.Words per .NET fornisce una soluzione elegante per mantenere i tuoi PDF snelli e snelli. In questo tutorial, approfondiremo come ottimizzare le dimensioni del tuo PDF saltando i font incorporati Arial e Times Roman. Cominciamo!

## Prerequisiti

Prima di entrare nei dettagli, ecco alcune cose di cui avrai bisogno:
-  Aspose.Words per .NET: assicurati di avere installata questa potente libreria. In caso contrario, puoi scaricarla da[Qui](https://releases.aspose.com/words/net/).
- Una conoscenza di base di C#: ti aiuterà a seguire i frammenti di codice.
- Un documento Word: utilizzeremo un documento di esempio per illustrare il processo. 

## Importazione degli spazi dei nomi

Per prima cosa, assicurati di aver importato i namespace necessari. Questo prepara il terreno per accedere alle funzionalità di Aspose.Words.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bene, analizziamo il processo passo dopo passo.

## Passaggio 1: configura il tuo ambiente

Per iniziare, devi impostare il tuo ambiente di sviluppo. Apri il tuo IDE C# preferito (come Visual Studio) e crea un nuovo progetto.

## Passaggio 2: caricare il documento Word

Il passo successivo è caricare il documento Word che vuoi convertire in PDF. Assicurati che il tuo documento sia nella directory corretta.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

 In questo frammento, sostituisci`"YOUR DOCUMENT DIRECTORY"` con il percorso alla directory dei documenti.

## Passaggio 3: configurare le opzioni di salvataggio PDF

Ora, dobbiamo configurare le opzioni di salvataggio PDF per controllare come i font sono incorporati. Di default, tutti i font sono incorporati, il che può aumentare le dimensioni del file. Cambieremo questa impostazione.

```csharp
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedAll
};
```

## Passaggio 4: Salvare il documento come PDF

Infine, salva il documento come PDF con le opzioni di salvataggio specificate. È qui che avviene la magia.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.SkipEmbeddedArialAndTimesRomanFonts.pdf", saveOptions);
```

Questo comando salva il documento come PDF denominato "OptimizedPDF.pdf" nella directory specificata.

## Conclusione

Ed ecco fatto! Hai appena imparato come ottimizzare le dimensioni del tuo file PDF saltando l'incorporamento dei font Arial e Times Roman usando Aspose.Words per .NET. Questa semplice modifica può ridurre significativamente le dimensioni dei tuoi file, rendendoli più facili da condividere e archiviare. È come andare in palestra per i tuoi PDF, perdere peso inutile mantenendo intatti tutti gli elementi essenziali.

## Domande frequenti

### Perché dovrei evitare di incorporare i font Arial e Times Roman?
Saltando questi font comuni è possibile ridurre le dimensioni del file PDF, poiché la maggior parte dei sistemi li ha già installati.

### Ciò influirà sull'aspetto del mio PDF?
No, non lo farà. Poiché Arial e Times Roman sono font standard, l'aspetto rimane coerente nei diversi sistemi.

### Posso evitare di incorporare anche altri font?
Sì, puoi configurare le opzioni di salvataggio per saltare l'incorporamento di altri font, se necessario.

### Aspose.Words per .NET è gratuito?
 Aspose.Words per .NET offre una prova gratuita che puoi scaricare[Qui](https://releases.aspose.com/) , ma per l'accesso completo, è necessario acquistare una licenza[Qui](https://purchase.aspose.com/buy).

### Dove posso trovare altri tutorial su Aspose.Words per .NET?
Puoi trovare documentazione e tutorial completi[Qui](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
