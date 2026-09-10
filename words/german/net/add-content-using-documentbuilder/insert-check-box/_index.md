---
title: Ein Check Box Form Field zu einem Word‑Dokument mit Aspose.Words for .NET hinzufügen.
weight: 210
limit:
description: Erfahren Sie, wie Sie programmgesteuert ein Kontrollkästchen‑Formularfeld zu einem neuen Word‑Dokument mit Aspose.Words for .NET hinzufügen und die Datei speichern.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ein Check Box Form Field zu einem Word‑Dokument mit Aspose.Words for .NET hinzufügen.
Dieses Tutorial zeigt, wie man ein neues Word‑Dokument erstellt und den DocumentBuilder von Aspose.Words for .NET verwendet, um ein Kontrollkästchen‑Formularfeld einzufügen. Wenn Sie den Schritten folgen, sehen Sie den genauen Code, der zum Hinzufügen des interaktiven Elements erforderlich ist, und anschließend das Speichern des Dokuments in einer Datei. Es ist ein schneller Weg, um programmgesteuert einfache, formularfähige Word‑Dateien zu erstellen.

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

**Q: Was stellt das vierte Argument (0) in InsertCheckBox dar?**
A: Es gibt die visuelle Größe des Kontrollkästchens in Punkt an; ein Wert von 0 weist Aspose.Words an, die Standardgröße zu verwenden.

**Q: Kann ich mehr als ein Kontrollkästchen mit demselben Namen einfügen?**
A: Nein – jeder Formularfeldname muss eindeutig sein; der Versuch, ein weiteres Kontrollkästchen mit dem Namen \"CheckBox\" einzufügen, löst eine ArgumentException aus.

**Q: Wie füge ich ein Kontrollkästchen zu einem bestehenden Dokument statt zu einem neuen hinzu?**
A: Laden Sie das Dokument zuerst (z. B. `Document doc = new Document(\"Existing.docx\");`), erstellen Sie dann einen DocumentBuilder für dieses Dokument und rufen Sie `InsertCheckBox` an der gewünschten Cursorposition auf.

**Q: Wie kann ich den Zustand des eingefügten Kontrollkästchens nach dem Speichern des Dokuments auslesen?**
A: Rufen Sie das Formularfeld über `doc.Range.FormFields[\"CheckBox\"]` ab und prüfen Sie dessen `Checked`‑Eigenschaft, um zu sehen, ob es markiert war.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}