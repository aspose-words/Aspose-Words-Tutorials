---
title: Seitenumbruch in ein Word‑Dokument einfügen mit Aspose.Words für .NET
weight: 110
limit:
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET und den Klassen Document und DocumentBuilder Seitenumbrüche zu einer Word‑Datei hinzufügen.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Seitenumbruch in ein Word‑Dokument einfügen mit Aspose.Words für .NET
In diesem interaktiven Tutorial lernen Sie, wie Sie programmgesteuert Seitenumbrüche zu einem Word‑Dokument mit Aspose.Words für .NET hinzufügen. Durch das Erstellen eines Document‑Objekts und die Verwendung von DocumentBuilder können Sie steuern, wo neue Seiten beginnen, was für die Formatierung von Berichten, Rechnungen oder jedem mehrteiligen Dokument unerlässlich ist. Folgen Sie dem Schritt‑für‑Schritt‑Beispiel, um den Code in Aktion zu sehen und die resultierende Datei vorzuschauen.

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

**Q: Kann ich InsertBreak verwenden, um stattdessen einen Zeilenumbruch oder einen Abschnittsumbruch hinzuzufügen, anstatt eines Seitenumbruchs?**
A: Ja, InsertBreak akzeptiert jeden BreakType‑Enum‑Wert, z. B. BreakType.LineBreak oder BreakType.SectionBreakContinuous, um den entsprechenden Umbruch einzufügen.

**Q: Muss ich InsertBreak vor oder nach dem Schreiben des Textes für die neue Seite aufrufen?**
A: InsertBreak sollte nach dem Inhalt aufgerufen werden, den Sie auf der aktuellen Seite haben möchten; die nächste Writeln‑Anweisung beginnt dann auf der durch den Umbruch erzeugten neuen Seite.

**Q: Was passiert, wenn der dataDir‑Pfad nicht mit einem Verzeichnistrennzeichen endet?**
A: Fehlt in dataDir ein abschließender Schrägstrich, wird der Dateiname direkt angehängt (z. B. "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), was zu einem ungültigen Pfad führen kann; stellen Sie sicher, dass der Pfad mit "\\" endet oder verwenden Sie Path.Combine.

**Q: Kann ich dieselbe DocumentBuilder‑Instanz wiederverwenden, um im gesamten Dokument mehrere Umbrüche einzufügen?**
A: Ja, derselbe DocumentBuilder kann wiederholt verwendet werden; jeder Aufruf von InsertBreak fügt einen Umbruch an der aktuellen Cursorposition des Builders ein.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}