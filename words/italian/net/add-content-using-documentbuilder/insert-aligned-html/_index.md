---
title: Inserisci HTML allineato in un documento Word usando Aspose.Words per .NET
weight: 210
limit:
description: Impara a inserire HTML grezzo con allineamento a sinistra, al centro o a destra in un documento Word usando Aspose.Words per .NET.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci HTML allineato in un documento Word usando Aspose.Words per .NET
Questo tutorial interattivo mostra come incorporare HTML grezzo in un documento Word controllandone l'allineamento—sinistra, centro o destra—utilizzando Aspose.Words per .NET. Sfruttando Document e DocumentBuilder, è possibile inserire una stringa HTML e applicare l'allineamento di paragrafo desiderato in poche righe di codice. L'esempio è ideale quando è necessario preservare la formattazione HTML e posizionare il contenuto con precisione all'interno del documento.

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

**Q: Cosa succede se la stringa HTML passata a DocumentBuilder.InsertHtml contiene tag non supportati da Aspose.Words, come <script> o <iframe>?**
A: I tag non supportati vengono ignorati; Aspose.Words analizza solo il sottoinsieme di HTML che può renderizzare, quindi <script>, <iframe> e elementi simili vengono rimossi mentre il resto del contenuto viene inserito.

**Q: Gli stili CSS inline (ad esempio <span style=\"color:red;\">) verranno preservati quando si utilizza InsertHtml?**
A: Sì, InsertHtml rispetta molte proprietà CSS inline come color, font‑size e background, convertendole nella formattazione Word corrispondente.

**Q: InsertHtml crea automaticamente un nuovo paragrafo per gli elementi di livello blocco come <div> o <h1>?**
A: Gli elementi di livello blocco vengono mappati a paragrafi Word, quindi ogni <div>, <p>, <h1>, ecc. diventa un paragrafo separato nel documento.

**Q: Come posso inserire HTML in una posizione specifica di un documento esistente invece che all'inizio?**
A: Sposta il cursore del DocumentBuilder sul nodo desiderato (ad esempio builder.MoveToDocumentEnd() o builder.MoveToParagraph(index)) prima di chiamare InsertHtml; l'HTML verrà inserito nella posizione corrente del cursore.

**Q: Se il documento contiene già del testo, la chiamata a InsertHtml sovrascriverà il contenuto esistente?**
A: No, InsertHtml inserisce l'HTML analizzato nella posizione corrente del builder senza eliminare i nodi esistenti, a meno che non sposti esplicitamente il cursore su di essi o li elimini in anticipo.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}