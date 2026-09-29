---
title: Sostituisci i dati del codice a barre nei documenti Word usando Aspose.Words per .NET
weight: 110
limit:
description: Scopri come inserire un campo DISPLAYBARCODE e sostituire la sua stringa di dati con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, barcode field, replace barcode data, Document.Range.Replace, DISPLAYBARCODE, Word barcode update]
url: /net/working-with-fields/replace-barcode-data/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Scopri come inserire un campo DISPLAYBARCODE e sostituire la sua stringa
    di dati con Aspose.Words per .NET.
  headline: Sostituisci i dati del codice a barre nei documenti Word usando Aspose.Words
    per .NET
  type: TechArticle
- description: Scopri come inserire un campo DISPLAYBARCODE e sostituire la sua stringa
    di dati con Aspose.Words per .NET.
  name: Sostituisci i dati del codice a barre nei documenti Word usando Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo oggetto Document e un DocumentBuilder per costruirne il contenuto.
    text: Crea un nuovo oggetto Document e un DocumentBuilder per costruirne il contenuto.
  - name: Inserisci un campo DISPLAYBARCODE e imposta il suo tipo, valore iniziale
      e i caratteri di inizio/fine, quindi aggiungi un'interruzione di riga.
    text: Inserisci un campo DISPLAYBARCODE e imposta il suo tipo, valore iniziale
      e i caratteri di inizio/fine, quindi aggiungi un'interruzione di riga.
  - name: Chiama UpdateFields per renderizzare il campo codice a barre appena inserito.
    text: Chiama UpdateFields per renderizzare il campo codice a barre appena inserito.
  - name: Utilizza il motore Trova/Sostituisci per modificare la stringa di dati del
      codice a barre da INIT123 a NEWVAL.
    text: Utilizza il motore Trova/Sostituisci per modificare la stringa di dati del
      codice a barre da INIT123 a NEWVAL.
  - name: Aggiorna nuovamente i campi affinché DISPLAYBARCODE rifletta la nuova stringa
      di dati.
    text: Aggiorna nuovamente i campi affinché DISPLAYBARCODE rifletta la nuova stringa
      di dati.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: '`Range.Replace` modifica solo il testo sottostante; il risultato visivo
      del campo DISPLAYBARCODE viene rigenerato solo quando viene chiamato `UpdateFields()`,
      così il nuovo codice a barre appare nel documento salvato.'
    question: Perché devo chiamare `myDocument.UpdateFields()` dopo aver eseguito
      `Range.Replace`?
  - answer: Sì, `Document.Range.Replace` opera sull'intero intervallo del documento,
      quindi qualsiasi testo corrispondente altrove verrà sostituito a meno che non
      limiti la ricerca usando `FindReplaceOptions` (ad esempio impostando un `Range`
      specifico o usando `.MatchWholeWord`).
    question: La chiamata `Replace(\"INIT123\", \"NEWVAL\", ...)` influenzerà altre
      occorrenze di "INIT123" al di fuori del campo codice a barre?
  - answer: Puoi assegnare un nuovo valore a `displayBarcode.BarcodeType` in qualsiasi
      momento, ma devi chiamare `myDocument.UpdateFields()` successivamente affinché
      la modifica sia riflessa nel codice a barre renderizzato.
    question: Posso cambiare il tipo di codice a barre (ad esempio da CODE39 a QR)
      dopo che il campo è stato inserito?
  - answer: Quando `AddStartStopChar` è true, Aspose.Words aggiunge automaticamente
      i caratteri di inizio/fine richiesti (`*`) attorno al valore del codice a barre,
      come richiesto da CODE39; impostalo a false se la tua simbologia non li necessita.
    question: Cosa fa la proprietà `AddStartStopChar = true` per i codici a barre
      CODE39?
  - answer: Non sono necessarie impostazioni speciali per una corrispondenza esatta
      semplice, ma puoi abilitare `.MatchCase` o `.MatchWholeWord` in `FindReplaceOptions`
      per evitare sostituzioni parziali accidentali.
    question: Devo configurare opzioni speciali in `FindReplaceOptions` per sostituire
      in modo sicuro il valore del codice a barre?
  type: FAQPage
images:
- /net/working-with-fields/replace-barcode-data/og-image.png
og_title: Aggiorna un campo codice a barre in Word con Aspose.Words
og_description: Scambia la stringa di dati di un codice a barre e aggiornala istantaneamente in un file Word.
og_image_alt: Screenshot che mostra un documento Word con un campo DISPLAYBARCODE prima e dopo la sostituzione dei dati usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Sostituisci i dati del codice a barre nei documenti Word usando Aspose.Words per .NET
Questo tutorial dimostra come inserire un campo DISPLAYBARCODE in un documento Word e poi utilizzare il metodo Document.Range.Replace per modificare la stringa di dati del codice a barre. Dopo la sostituzione, il campo viene aggiornato in modo che il codice a barre aggiornato compaia nel file salvato. Segui i passaggi per vedere l'aggiornamento del codice a barre istantaneamente senza ricreare il campo.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/replace-barcode-data" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Perché devo chiamare `myDocument.UpdateFields()` dopo aver eseguito `Range.Replace`?**  
A: `Range.Replace` modifica solo il testo sottostante; il risultato visivo del campo DISPLAYBARCODE viene rigenerato solo quando viene chiamato `UpdateFields()`, così il nuovo codice a barre appare nel documento salvato.

**Q: La chiamata `Replace(\"INIT123\", \"NEWVAL\", ...)` influenzerà altre occorrenze di "INIT123" al di fuori del campo codice a barre?**  
A: Sì, `Document.Range.Replace` opera sull'intero intervallo del documento, quindi qualsiasi testo corrispondente altrove verrà sostituito a meno che non limiti la ricerca usando `FindReplaceOptions` (ad esempio impostando un `Range` specifico o usando `.MatchWholeWord`).

**Q: Posso cambiare il tipo di codice a barre (ad esempio da CODE39 a QR) dopo che il campo è stato inserito?**  
A: Puoi assegnare un nuovo valore a `displayBarcode.BarcodeType` in qualsiasi momento, ma devi chiamare `myDocument.UpdateFields()` successivamente affinché la modifica sia riflessa nel codice a barre renderizzato.

**Q: Cosa fa la proprietà `AddStartStopChar = true` per i codici a barre CODE39?**  
A: Quando `AddStartStopChar` è true, Aspose.Words aggiunge automaticamente i caratteri di inizio/fine richiesti (`*`) attorno al valore del codice a barre, come richiesto da CODE39; impostalo a false se la tua simbologia non li necessita.

**Q: Devo configurare opzioni speciali in `FindReplaceOptions` per sostituire in modo sicuro il valore del codice a barre?**  
A: Non sono necessarie impostazioni speciali per una corrispondenza esatta semplice, ma puoi abilitare `.MatchCase` o `.MatchWholeWord` in `FindReplaceOptions` per evitare sostituzioni parziali accidentali.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}