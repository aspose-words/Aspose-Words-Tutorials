---
title: Inserisci campo TC in documento Word usando Aspose.Words per .NET
weight: 110
limit:
description: Scopri come inserire un campo TC con testo personalizzato in un documento Word usando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci campo TC in documento Word usando Aspose.Words per .NET
Questo tutorial mostra come utilizzare Aspose.Words per .NET per inserire un campo TC (Table of Contents) in un documento Word appena creato. Utilizzando DocumentBuilder è possibile aggiungere un campo TC con testo di voce personalizzato, utile per creare un indice ricercabile per un sommario. L'esempio dimostra anche come salvare il documento su disco.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-tc-field" >}}


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

**Q: Cosa significa l'opzione "\\f t" nel codice del campo TC?**
A: L'opzione "\\f t" indica a Word di trattare la voce come una voce di tabella, facendola apparire in un indice generato con l'opzione \\f.

**Q: Come posso modificare il testo che appare nel campo TC?**
A: Sostituisci "Entry Text" nella chiamata InsertField con qualsiasi stringa desideri, ad esempio, builder.InsertField(\"TC \\"Chapter 1\" \\f t\");

**Q: Posso inserire più campi TC nello stesso documento?**
A: Sì; basta chiamare builder.InsertField con testi di voce diversi nelle posizioni desiderate prima di salvare il documento.

**Q: Questo codice funziona per formati diversi da .docx, come .pdf?**
A: Il documento viene salvato come .docx nell'esempio, ma Aspose.Words può salvare in altri formati (ad esempio, .pdf) modificando l'estensione del file in doc.Save e assicurandosi che il formato di output appropriato sia supportato.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}