---
title: Aggiungi un campo TC a un documento Word con Aspose.Words per .NET
weight: 310
limit:
description: Impara a inserire un campo TC in un nuovo documento Word con Aspose.Words per .NET usando DocumentBuilder.
keywords: [Aspose.Words for .NET, insert TC field, DocumentBuilder TC field, Word document indexing, add TC field programmatically, TC field tutorial]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi un campo TC a un documento Word con Aspose.Words per .NET
In questo tutorial interattivo imparerai come aggiungere programmaticamente un campo TC — un marcatore nascosto usato dalle funzioni di indicizzazione e indice di Word — a un documento appena creato utilizzando Aspose.Words per .NET. Utilizzando DocumentBuilder puoi posizionare il campo esattamente dove ti serve e poi salvare il file, pronto per ulteriori elaborazioni.

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

**Q: Cosa fa effettivamente il campo "TC" inserito da `builder.InsertField("TC \"Entry Text\" \\f t")` nel documento Word?**
A: Crea un elemento dell'indice con il testo visibile "Entry Text" e lo contrassegna come voce TC (Table of Contents), che Word può successivamente utilizzare durante la generazione dell'indice.

**Q: Qual è lo scopo dell'opzione `\f t` nella stringa del campo TC?**
A: L'opzione `\f t` indica a Word di trattare l'elemento come una voce di testo normale (anziché come intestazione) e di includerlo nell'indice quando viene generato.

**Q: Posso inserire più campi TC con testi di voce diversi utilizzando la stessa istanza di `DocumentBuilder`?**
A: Sì; basta chiamare nuovamente `builder.InsertField` con una stringa diversa, ad esempio `builder.InsertField("TC \"Another Entry\" \\f t")`, e ogni chiamata inserisce un nuovo campo TC nella posizione corrente del cursore.

**Q: Se ho bisogno che il testo della voce sia dinamico (ad esempio, proveniente da una variabile), come devo formattare la chiamata `InsertField`?**
A: Costruisci la stringa del campo con l'interpolazione di stringhe o `String.Format`, ad esempio: `string entry = "Chapter 1"; builder.InsertField($"TC \"{entry}\" \\f t");`.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}