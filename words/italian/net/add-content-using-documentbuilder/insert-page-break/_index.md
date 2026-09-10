---
title: Inserisci un'interruzione di pagina in un documento Word con Aspose.Words per .NET
weight: 110
limit:
description: Impara ad aggiungere interruzioni di pagina a un file Word con Aspose.Words per .NET usando Document e DocumentBuilder.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci un'interruzione di pagina in un documento Word con Aspose.Words per .NET
In questo tutorial interattivo imparerai come aggiungere programmaticamente interruzioni di pagina a un documento Word utilizzando Aspose.Words per .NET. Creando un oggetto Document e usando DocumentBuilder, puoi controllare dove iniziano le nuove pagine, cosa essenziale per formattare report, fatture o qualsiasi documento a più sezioni. Segui l'esempio passo‑passo per vedere il codice in azione e visualizzare il file risultante.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: Posso usare InsertBreak per aggiungere un'interruzione di riga o un'interruzione di sezione invece di un'interruzione di pagina?**
A: Sì, InsertBreak accetta qualsiasi valore dell'enumerazione BreakType, come BreakType.LineBreak o BreakType.SectionBreakContinuous, per inserire l'interruzione corrispondente.

**Q: Devo chiamare InsertBreak prima o dopo aver scritto il testo per la nuova pagina?**
A: InsertBreak dovrebbe essere chiamato dopo il contenuto che desideri sulla pagina corrente; il successivo Writeln inizierà quindi sulla nuova pagina creata dall'interruzione.

**Q: Cosa succede se il percorso dataDir non termina con un separatore di directory?**
A: Se dataDir manca della barra finale, il nome del file verrà concatenato direttamente (ad es., "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), il che può generare un percorso non valido; assicurati che il percorso termini con "\\" o usa Path.Combine.

**Q: Posso riutilizzare la stessa istanza di DocumentBuilder per inserire più interruzioni in tutto il documento?**
A: Sì, lo stesso DocumentBuilder può essere usato ripetutamente; ogni chiamata a InsertBreak inserisce un'interruzione nella posizione corrente del cursore del builder.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}