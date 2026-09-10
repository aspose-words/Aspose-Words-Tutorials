---
title: TC‑Feld in Word-Dokument einfügen mit Aspose.Words für .NET
weight: 110
limit:
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET ein TC‑Feld mit benutzerdefiniertem Text in ein Word‑Dokument einfügen.
keywords: [Aspose.Words for .NET, insert TC field, TC field Word, DocumentBuilder TC field, Word document index, table of contents field]
url: /net/add-content-using-documentbuilder/insert-tc-field/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# TC‑Feld in Word-Dokument einfügen mit Aspose.Words für .NET
Dieses Tutorial zeigt, wie man Aspose.Words für .NET verwendet, um ein TC‑Feld (Table of Contents) in ein neu erstelltes Word‑Dokument einzufügen. Mit DocumentBuilder können Sie ein TC‑Feld mit benutzerdefiniertem Eintragstext hinzufügen, was nützlich ist, um einen durchsuchbaren Index für ein Inhaltsverzeichnis zu erstellen. Das Beispiel demonstriert außerdem das Speichern des Dokuments auf dem Datenträger.

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

**Q: Was bedeutet der Schalter "\f t" im TC‑Feldcode?**
A: Der Schalter "\f t" weist Word an, den Eintrag als Tabelleneintrag zu behandeln, wodurch er in einem mit dem \f‑Schalter erzeugten Inhaltsverzeichnis erscheint.

**Q: Wie kann ich den Text ändern, der im TC‑Feld angezeigt wird?**
A: Ersetzen Sie "Entry Text" im InsertField‑Aufruf durch eine beliebige Zeichenkette, z. B. builder.InsertField("TC \"Chapter 1\" \f t");

**Q: Kann ich mehrere TC‑Felder im selben Dokument einfügen?**
A: Ja; rufen Sie einfach builder.InsertField mit unterschiedlichen Eintragstexten an den gewünschten Stellen auf, bevor Sie das Dokument speichern.

**Q: Funktioniert dieser Code für andere Formate als .docx, zum Beispiel .pdf?**
A: Im Beispiel wird das Dokument als .docx gespeichert, aber Aspose.Words kann in andere Formate (z. B. .pdf) speichern, indem man die Dateierweiterung in doc.Save ändert und sicherstellt, dass das entsprechende Ausgabeformat unterstützt wird.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}