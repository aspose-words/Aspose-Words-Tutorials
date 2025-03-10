---
title: Abilita Disabilita Sostituzione Font
linktitle: Abilita Disabilita Sostituzione Font
second_title: API di elaborazione dei documenti Aspose.Words
description: Scopri come abilitare o disabilitare la sostituzione dei font nei documenti Word usando Aspose.Words per .NET. Assicurati che i tuoi documenti abbiano un aspetto coerente su tutte le piattaforme.
weight: 10
url: /it/net/working-with-fonts/enable-disable-font-substitution/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Abilita Disabilita Sostituzione Font

## Introduzione

Ti sei mai trovato in una situazione in cui i tuoi font scelti meticolosamente in un documento Word vengono sostituiti quando vengono visualizzati su un altro computer? Fastidioso, vero? Ciò accade a causa della sostituzione dei font, un processo in cui il sistema sostituisce un font mancante con uno disponibile. Ma non preoccuparti! Con Aspose.Words per .NET, puoi facilmente gestire e controllare la sostituzione dei font. In questo tutorial, ti guideremo attraverso i passaggi per abilitare o disabilitare la sostituzione dei font nei tuoi documenti Word, assicurandoti che i tuoi documenti abbiano sempre l'aspetto che desideri.

## Prerequisiti

Prima di procedere, assicuriamoci di avere tutto ciò di cui hai bisogno:

-  Aspose.Words per .NET: Scarica l'ultima versione[Qui](https://releases.aspose.com/words/net/).
- Visual Studio: qualsiasi versione che supporti .NET.
- Conoscenza di base di C#: ti aiuterà a seguire gli esempi di codifica.

## Importazione degli spazi dei nomi

Per iniziare, assicurati di aver importato i namespace necessari nel tuo progetto. Aggiungili in cima al tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ora scomponiamo il processo in passaggi semplici e gestibili.

## Passaggio 1: imposta il tuo progetto

Per prima cosa, imposta un nuovo progetto in Visual Studio e aggiungi un riferimento alla libreria Aspose.Words per .NET. Se non l'hai già fatto, scaricalo da[Sito web di Aspose](https://releases.aspose.com/words/net/).

## Passaggio 2: carica il documento

Poi, carica il documento con cui vuoi lavorare. Ecco come fare:

```csharp
// Percorso alla directory del documento
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

 Sostituire`"YOUR DOCUMENT DIRECTORY"` con il percorso effettivo della directory del tuo documento. Questo codice carica il documento in memoria in modo che tu possa manipolarlo.

## Passaggio 3: configurare le impostazioni del carattere

 Ora creiamo un`FontSettings` oggetto per gestire le impostazioni di sostituzione dei font:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Passaggio 4: imposta la sostituzione predefinita del carattere

Imposta la sostituzione del font predefinito su un font a tua scelta. Questo font verrà utilizzato se il font originale non è disponibile:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

In questo esempio utilizziamo Arial come font predefinito.

## Passaggio 5: Disattiva la sostituzione delle informazioni sui caratteri

Per disattivare la sostituzione delle informazioni sui font, che impedisce al sistema di sostituire i font mancanti con quelli disponibili, utilizzare il seguente codice:

```csharp
fontSettings.SubstitutionSettings.FontInfoSubstitution.Enabled = false;
```

## Passaggio 6: applicare le impostazioni del carattere al documento

Ora applica queste impostazioni al tuo documento:

```csharp
doc.FontSettings = fontSettings;
```

## Passaggio 7: salva il documento

Infine, salva il documento modificato. Puoi salvarlo in qualsiasi formato tu voglia. Per questo tutorial, lo salveremo come PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi facilmente controllare la sostituzione dei font nei tuoi documenti Word usando Aspose.Words per .NET. Ciò assicura che i tuoi documenti mantengano l'aspetto e la sensazione desiderati, indipendentemente da dove vengono visualizzati.

## Domande frequenti

### Posso usare font diversi da Arial per la sostituzione?

 Assolutamente! Puoi specificare qualsiasi font disponibile sul tuo sistema modificando il nome del font in`DefaultFontName` proprietà.

### Cosa succede se il font predefinito specificato non è disponibile?

Se il font predefinito non è disponibile, Aspose.Words utilizzerà un meccanismo di fallback del sistema per trovare un sostituto appropriato.

### Posso abilitare nuovamente la sostituzione dei font dopo averla disabilitata?

 Sì, puoi attivare/disattivare`Enabled` proprietà di`FontInfoSubstitution` torna a`true` se vuoi abilitare nuovamente la sostituzione dei caratteri.

### C'è un modo per verificare quali font vengono sostituiti?

Sì, Aspose.Words fornisce metodi per registrare e tenere traccia della sostituzione dei font, consentendo di vedere quali font vengono sostituiti.

### Posso usare questo metodo anche per altri formati di documento oltre al DOCX?

Certamente! Aspose.Words supporta vari formati e puoi applicare queste impostazioni di font a qualsiasi formato supportato.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
