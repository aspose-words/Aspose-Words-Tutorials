---
"description": "Scopri come abilitare o disabilitare la sostituzione dei font nei documenti Word utilizzando Aspose.Words per .NET. Assicurati che i tuoi documenti abbiano un aspetto coerente su tutte le piattaforme."
"linktitle": "Abilita Disabilita Sostituzione Font"
"second_title": "API di elaborazione dei documenti Aspose.Words"
"title": "Abilita Disabilita Sostituzione Font"
"url": "/it/net/working-with-fonts/enable-disable-font-substitution/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Abilita Disabilita Sostituzione Font

## Introduzione

Vi siete mai trovati in una situazione in cui i font scelti con cura in un documento Word vengono sostituiti quando vengono visualizzati su un altro computer? Fastidioso, vero? Questo accade a causa della sostituzione dei font, un processo in cui il sistema sostituisce un font mancante con uno disponibile. Ma non preoccupatevi! Con Aspose.Words per .NET, potete gestire e controllare facilmente la sostituzione dei font. In questo tutorial, vi guideremo attraverso i passaggi per abilitare o disabilitare la sostituzione dei font nei vostri documenti Word, assicurandovi che i vostri documenti abbiano sempre l'aspetto desiderato.

## Prerequisiti

Prima di procedere, assicuriamoci di avere tutto il necessario:

- Aspose.Words per .NET: scarica l'ultima versione [Qui](https://releases.aspose.com/words/net/).
- Visual Studio: qualsiasi versione che supporti .NET.
- Conoscenza di base di C#: ti aiuterà a seguire gli esempi di codifica.

## Importa spazi dei nomi

Per iniziare, assicurati di aver importato gli spazi dei nomi necessari nel tuo progetto. Aggiungili all'inizio del tuo file C#:

```csharp
using Aspose.Words;
using Aspose.Words.Fonts;
```

Ora scomponiamo il processo in passaggi semplici e gestibili.

## Passaggio 1: imposta il tuo progetto

Per prima cosa, crea un nuovo progetto in Visual Studio e aggiungi un riferimento alla libreria Aspose.Words per .NET. Se non l'hai già fatto, scaricala da [Sito web di Aspose](https://releases.aspose.com/words/net/).

## Passaggio 2: carica il documento

Quindi, carica il documento su cui vuoi lavorare. Ecco come fare:

```csharp
// Percorso alla directory dei documenti 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Rendering.docx");
```

Sostituire `"YOUR DOCUMENT DIRECTORY"` Con il percorso effettivo della directory del documento. Questo codice carica il documento in memoria in modo da poterlo manipolare.

## Passaggio 3: configurare le impostazioni del carattere

Ora creiamo un `FontSettings` oggetto per gestire le impostazioni di sostituzione dei font:

```csharp
FontSettings fontSettings = new FontSettings();
```

## Passaggio 4: imposta la sostituzione predefinita del carattere

Imposta la sostituzione predefinita del font con un font a tua scelta. Questo font verrà utilizzato se il font originale non è disponibile:

```csharp
fontSettings.SubstitutionSettings.DefaultFontSubstitution.DefaultFontName = "Arial";
```

In questo esempio utilizziamo Arial come font predefinito.

## Passaggio 5: disabilitare la sostituzione delle informazioni sui caratteri

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

Infine, salva il documento modificato. Puoi salvarlo in qualsiasi formato tu preferisca. In questo tutorial, lo salveremo in formato PDF:

```csharp
doc.Save(dataDir + "WorkingWithFonts.EnableDisableFontSubstitution.pdf");
```

## Conclusione

Ed ecco fatto! Seguendo questi passaggi, puoi facilmente controllare la sostituzione dei font nei tuoi documenti Word utilizzando Aspose.Words per .NET. Questo garantisce che i tuoi documenti mantengano l'aspetto desiderato, indipendentemente da dove vengano visualizzati.

## Domande frequenti

### Posso usare font diversi da Arial per la sostituzione?

Assolutamente! Puoi specificare qualsiasi font disponibile sul tuo sistema modificandone il nome nel `DefaultFontName` proprietà.

### Cosa succede se il font predefinito specificato non è disponibile?

Se il font predefinito non è disponibile, Aspose.Words utilizzerà un meccanismo di fallback del sistema per trovare un sostituto appropriato.

### Posso abilitare nuovamente la sostituzione dei font dopo averla disabilitata?

Sì, puoi attivare/disattivare `Enabled` proprietà di `FontInfoSubstitution` torna a `true` se vuoi abilitare nuovamente la sostituzione dei font.

### C'è un modo per verificare quali font vengono sostituiti?

Sì, Aspose.Words fornisce metodi per registrare e tenere traccia della sostituzione dei font, consentendo di vedere quali font vengono sostituiti.

### Posso usare questo metodo anche per altri formati di documenti oltre al DOCX?

Certamente! Aspose.Words supporta vari formati e puoi applicare queste impostazioni del font a qualsiasi formato supportato.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}