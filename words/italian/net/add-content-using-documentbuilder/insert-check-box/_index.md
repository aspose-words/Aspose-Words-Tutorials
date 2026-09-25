---
title: Aggiungi un campo modulo casella di controllo a un documento Word con Aspose.Words for .NET
weight: 210
limit:
description: Scopri come aggiungere programmaticamente un campo modulo casella di controllo a un nuovo documento Word usando Aspose.Words for .NET e salvare il file.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aggiungi un campo modulo casella di controllo a un documento Word con Aspose.Words
Questo tutorial mostra come creare un nuovo documento Word e utilizzare DocumentBuilder di Aspose.Words for .NET per inserire un campo modulo casella di controllo. Seguendo i passaggi, vedrai il codice esatto necessario per aggiungere l'elemento interattivo e poi salvare il documento su un file. È un modo rapido per creare programmaticamente file Word con moduli semplici.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: Cosa rappresenta il quarto argomento (0) in InsertCheckBox?**
A: Specifica la dimensione visiva della casella di controllo in punti; un valore di 0 indica ad Aspose.Words di utilizzare la dimensione predefinita.

**Q: Posso inserire più di una casella di controllo con lo stesso nome?**
A: No – ogni nome di campo modulo deve essere univoco; provare a inserire un'altra casella di controllo chiamata \"CheckBox\" genererà un'ArgumentException.

**Q: Come aggiungere una casella di controllo a un documento esistente invece che a uno nuovo?**
A: Carica prima il documento (ad es., `Document doc = new Document(\"Existing.docx\");`) quindi crea un DocumentBuilder per quel documento e chiama `InsertCheckBox` nella posizione del cursore desiderata.

**Q: Come posso leggere lo stato della casella di controllo inserita dopo che il documento è stato salvato?**
A: Recupera il campo modulo tramite `doc.Range.FormFields[\"CheckBox\"]` e controlla la sua proprietà `Checked` per vedere se era selezionata.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}