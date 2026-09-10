---
title: Inserisci HTML allineato in un documento Word usando Aspose.Words per .NET
weight: 210
limit:
description: Scopri come inserire HTML con allineamento specifico in un documento Word usando Aspose.Words per .NET.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci HTML allineato in un documento Word usando Aspose.Words per .NET
Questo tutorial dimostra come utilizzare DocumentBuilder di Aspose.Words per .NET per incorporare markup HTML in un documento Word e controllarne l'allineamento. Vedrai come inserire l'HTML, impostare l'allineamento del paragrafo (sinistra, centro o destra) e quindi salvare il documento risultante. L'esempio è ideale per gli sviluppatori che devono preservare la formattazione in stile web durante la generazione programmatica di file Word.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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

**Q: È possibile utilizzare InsertHtml per aggiungere HTML in un documento Word esistente anziché in uno nuovo?**
A: Sì. Crea un Document dal file esistente, posiziona il cursore di DocumentBuilder dove desideri inserire l'HTML (ad es., usando builder.MoveToDocumentEnd()), e poi chiama builder.InsertHtml con il tuo markup.

**Q: Quali attributi HTML sono rispettati da InsertHtml per l'allineamento?**
A: InsertHtml rispetta l'attributo "align" sugli elementi di livello blocco come <p>, <div> e i tag di intestazione, applicando l'allineamento del paragrafo corrispondente nel documento Word risultante.

**Q: Cosa succede se la stringa HTML contiene tag o CSS non supportati?**
A: I tag non supportati vengono ignorati e il loro testo interno viene inserito come testo semplice; gli stili CSS inline che Aspose.Words non riconosce sono anch'essi ignorati, quindi viene renderizzata solo la sottoinsieme di HTML supportato.

**Q: Devo chiudere il DocumentBuilder prima di salvare il documento?**
A: Non è necessario chiudere esplicitamente; dopo aver inserito l'HTML puoi chiamare direttamente doc.Save con il nome file e il formato desiderati, e le risorse del builder vengono rilasciate automaticamente.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}