---
title: Aggiungi un campo modulo a casella combinata a un documento Word con Aspose.Words for .NET
weight: 310
limit:
description: Scopri come aggiungere un campo modulo a casella combinata con elementi predefiniti a un documento Word usando Aspose.Words for .NET.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi un campo modulo a casella combinata a un documento Word con Aspose.Words
Questo tutorial dimostra come utilizzare DocumentBuilder di Aspose.Words for .NET per creare un nuovo documento Word e inserire un campo modulo a casella combinata popolato con elementi predefiniti. Seguendo il codice passo‑passo, vedrai come configurare le opzioni della casella combinata e poi salvare il documento per l'uso in moduli interattivi.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: Cosa rappresenta l'array `items` passato a `InsertComboBox`?**
A: Definisce l'elenco di stringhe che appaiono come opzioni selezionabili nel menu a discesa della casella combinata.

**Q: Come posso cambiare quale elemento è selezionato per impostazione predefinita quando il documento viene aperto?**
A: Imposta il terzo argomento (`selectedIndex`) di `InsertComboBox` sull'indice basato su zero dell'elemento predefinito desiderato (ad esempio, `2` per "Three").

**Q: È possibile posizionare la casella combinata in una posizione specifica nel documento?**
A: Sì—sposta il cursore di `DocumentBuilder` nel punto desiderato usando metodi come `MoveToParagraph`, `InsertParagraph` o `Write` prima di chiamare `InsertComboBox`.

**Q: Quale formato di file viene creato da questo codice e può essere aperto nelle versioni precedenti di Word?**
A: Il codice salva un file `.docx`, che può essere aperto da Word 2007 e versioni successive, nonché da qualsiasi applicazione che supporta il formato OpenXML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}