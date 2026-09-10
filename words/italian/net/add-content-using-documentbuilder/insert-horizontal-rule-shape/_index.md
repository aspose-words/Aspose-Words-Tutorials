---
title: Inserisci una forma di regola orizzontale in un documento Word usando Aspose.Words per .NET
weight: 110
limit:
description: Guida passo‑passo per inserire una forma di regola orizzontale in un documento Word con Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci una forma di regola orizzontale in un documento Word usando Aspose.Words per .NET
Scopri come utilizzare Aspose.Words per .NET per inserire una forma di regola orizzontale in un documento Word. Questo tutorial ti guida nella creazione di un nuovo documento, nell'aggiunta di una riga di testo, nel posizionamento di una forma di regola orizzontale con DocumentBuilder e nel salvataggio del file. La regola orizzontale fornisce un semplice separatore visivo per il tuo contenuto.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Posso modificare l'aspetto (colore, spessore) della regola orizzontale inserita con DocumentBuilder.InsertHorizontalRule()?**
A: InsertHorizontalRule crea una forma di linea orizzontale incorporata con formattazione predefinita; per modificarne l'aspetto è necessario recuperare l'oggetto Shape inserito (builder.CurrentParagraph.LastChild) e regolare le proprietà LineFormat.

**Q: Cosa succede se chiamo InsertHorizontalRule() dopo un paragrafo che termina già con un'interruzione di riga?**
A: Il metodo inserisce la regola come un paragrafo separato, quindi qualsiasi interruzione di riga precedente crea semplicemente un paragrafo vuoto prima della regola; la regola apparirà comunque sulla sua propria riga.

**Q: È possibile inserire più di una regola orizzontale nello stesso documento usando DocumentBuilder?**
A: Sì, ogni chiamata a builder.InsertHorizontalRule() aggiunge una nuova forma di regola orizzontale nella posizione corrente del cursore, consentendo più regole nel documento.

**Q: InsertHorizontalRule() funziona quando si salva il documento in formati diversi da DOCX, come PDF?**
A: La regola orizzontale è memorizzata come forma nel modello del documento, quindi quando si salva in PDF, XPS o altri formati supportati la regola viene renderizzata correttamente nell'output.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}