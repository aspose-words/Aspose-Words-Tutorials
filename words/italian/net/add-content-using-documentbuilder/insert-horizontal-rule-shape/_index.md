---
title: Inserisci una forma di regola orizzontale in un documento Word usando Aspose.Words per .NET
weight: 110
limit:
description: Impara ad aggiungere una forma di regola orizzontale a un documento Word con Aspose.Words per .NET usando DocumentBuilder.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Inserisci una forma di regola orizzontale in un documento Word usando Aspose.Words per .NET
In questo tutorial imparerai come inserire programmaticamente una forma di regola orizzontale in un documento Word con Aspose.Words per .NET. Utilizzando le classi Document e DocumentBuilder creiamo un nuovo documento, aggiungiamo un paragrafo di testo e poi posizioniamo una forma di linea orizzontale nella posizione desiderata. La regola orizzontale fornisce un separatore visivo che può essere utile per interruzioni di sezione o per enfatizzare visivamente.

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

**Q: Dove esattamente `builder.InsertHorizontalRule()` posiziona la linea nel documento?**  
A: `InsertHorizontalRule` inserisce una forma di regola orizzontale nella posizione corrente del cursore del `DocumentBuilder`; se la vuoi su una riga separata, chiama `builder.Writeln()` prima dell'inserimento.

**Q: Posso modificare lo spessore, il colore o la larghezza della regola orizzontale inserita?**  
A: `InsertHorizontalRule` aggiunge una regola con stile predefinito e non espone opzioni di formattazione; per personalizzare tali proprietà è necessario inserire manualmente una `Shape` (ad esempio, `builder.InsertShape(ShapeType.HorizontalLine)`) e poi impostare le sue proprietà `LineFormat`.

**Q: È possibile aggiungere più di una regola orizzontale nello stesso documento?**  
A: Sì—basta chiamare `builder.InsertHorizontalRule()` ogni volta che ti serve una nuova regola; ogni chiamata crea una forma separata nella posizione corrente del builder.

**Q: La regola orizzontale sarà visibile quando il .docx salvato viene aperto in Microsoft Word?**  
A: Assolutamente; la regola viene salvata come forma all'interno del file .docx, quindi Word la visualizza esattamente come appare nel documento generato.

**Q: Cosa succede se la cartella `dataDir` non esiste prima di chiamare `doc.Save(...)`?**  
A: `doc.Save` genererà una `DirectoryNotFoundException`; assicurati che la directory di destinazione esista o creala programmaticamente prima di salvare.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}