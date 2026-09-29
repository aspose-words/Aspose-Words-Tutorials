---
title: Inserisci un codice a barre DataMatrix in un documento Word usando Aspose.Words per .NET
weight: 210
limit:
description: Aggiungi programmaticamente un codice a barre DataMatrix a un documento Word con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, datamatrix barcode, displaybarcode field, documentbuilder barcode, word document barcode, insert barcode .net]
url: /net/working-with-fields/insert-datamatrix-barcode/
date: '2026-09-29'
lastmod: '2026-09-29'
schemas:
- author: Aspose
  dateModified: '2026-09-29'
  description: Aggiungi programmaticamente un codice a barre DataMatrix a un documento
    Word con Aspose.Words per .NET.
  headline: Inserisci un codice a barre DataMatrix in un documento Word usando Aspose.Words
    per .NET
  type: TechArticle
- description: Aggiungi programmaticamente un codice a barre DataMatrix a un documento
    Word con Aspose.Words per .NET.
  name: Inserisci un codice a barre DataMatrix in un documento Word usando Aspose.Words
    per .NET
  steps:
  - name: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
    text: Crea un nuovo documento Word vuoto e un DocumentBuilder per modificarlo.
  - name: Inserisci un campo DISPLAYBARCODE nella posizione corrente del cursore,
      che aggiunge un segnaposto di campo al documento.
    text: Inserisci un campo DISPLAYBARCODE nella posizione corrente del cursore,
      che aggiunge un segnaposto di campo al documento.
  - name: Imposta la proprietà BarcodeType del campo su DataMatrix e fornisci la stringa
      di dati da codificare.
    text: Imposta la proprietà BarcodeType del campo su DataMatrix e fornisci la stringa
      di dati da codificare.
  - name: Facoltativamente definisci i colori di sfondo e di primo piano del codice
      a barre.
    text: Facoltativamente definisci i colori di sfondo e di primo piano del codice
      a barre.
  - name: Chiama UpdateFields sul documento per generare l'immagine del codice a barre
      all'interno del campo.
    text: Chiama UpdateFields sul documento per generare l'immagine del codice a barre
      all'interno del campo.
  - name: Salva il documento in un file .docx.
    text: Salva il documento in un file .docx.
  type: HowTo
- questions:
  - answer: Il campo verrà inserito, ma `document.UpdateFields()` lascerà il codice
      a barre vuoto e Aspose.Words genererà una `FieldException` che indica un tipo
      di codice a barre non valido.
    question: Cosa succede se assegno un valore non supportato a `displayBarcodeField.BarcodeType`?
  - answer: '`UpdateFields()` genera le immagini dei codici a barre, quindi puoi inserire
      più oggetti `FieldDisplayBarcode` e chiamare `document.UpdateFields()` una sola
      volta alla fine per generarli tutti.'
    question: Devo chiamare `document.UpdateFields()` dopo ogni inserimento di codice
      a barre, o posso aggiornare una sola volta dopo aver aggiunto tutti i campi?
  - answer: Entrambe le proprietà si aspettano una stringa RGB esadecimale preceduta
      da `0x` (ad esempio, \"0xFF0000\" per il rosso); qualsiasi altro formato verrà
      ignorato e verranno usati i colori predefiniti.
    question: Quale formato devono avere le stringhe di colore per `BackgroundColor`
      e `ForegroundColor`?
  - answer: Sì—basta impostare `displayBarcodeField.BarcodeValue` su una nuova stringa
      e chiamare nuovamente `document.UpdateFields()` per aggiornare l'immagine generata.
    question: Posso modificare il contenuto del codice a barre dopo che il campo è
      stato inserito?
  type: FAQPage
images:
- /net/working-with-fields/insert-datamatrix-barcode/og-image.png
og_title: Inserisci un codice a barre DataMatrix con Aspose.Words
og_description: Scopri come aggiungere un codice a barre DataMatrix a un file Word in poche righe di codice .NET.
og_image_alt: Guida che mostra come inserire e generare un codice a barre DataMatrix in un documento Word usando Aspose.Words per .NET
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci un codice a barre DataMatrix in un documento Word usando Aspose.Words per .NET
Con Aspose.Words per .NET puoi aggiungere programmaticamente un codice a barre DataMatrix a un documento Word. Questo tutorial mostra come creare un nuovo documento, inserire un campo DISPLAYBARCODE, impostare il suo tipo su DataMatrix e generare l'immagine del codice a barre utilizzando le classi Document e DocumentBuilder. Segui i passaggi per generare un codice a barre stampabile direttamente nel tuo file .docx.

---

{{< tutorial-widget sourcePath="words/net/working-with-fields/insert-datamatrix-barcode" >}}


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

**Q: Cosa succede se assegno un valore non supportato a `displayBarcodeField.BarcodeType`?**  
A: Il campo verrà inserito, ma `document.UpdateFields()` lascerà il codice a barre vuoto e Aspose.Words genererà una `FieldException` che indica un tipo di codice a barre non valido.

**Q: Devo chiamare `document.UpdateFields()` dopo ogni inserimento di codice a barre, o posso aggiornare una sola volta dopo aver aggiunto tutti i campi?**  
A: `UpdateFields()` genera le immagini dei codici a barre, quindi puoi inserire più oggetti `FieldDisplayBarcode` e chiamare `document.UpdateFields()` una sola volta alla fine per generarli tutti.

**Q: Quale formato devono avere le stringhe di colore per `BackgroundColor` e `ForegroundColor`?**  
A: Entrambe le proprietà si aspettano una stringa RGB esadecimale preceduta da `0x` (ad esempio, \"0xFF0000\" per il rosso); qualsiasi altro formato verrà ignorato e verranno usati i colori predefiniti.

**Q: Posso modificare il contenuto del codice a barre dopo che il campo è stato inserito?**  
A: Sì—basta impostare `displayBarcodeField.BarcodeValue` su una nuova stringa e chiamare nuovamente `document.UpdateFields()` per aggiornare l'immagine generata.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}