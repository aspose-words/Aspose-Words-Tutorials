---
title: Dynamisches Datum in die Kopfzeile eines Word‑Dokuments einfügen mit Aspose.Words für .NET
weight: 110
limit:
description: Erfahren Sie, wie Sie mit Aspose.Words für .NET ein dynamisches DATE‑Feld zur primären Kopfzeile eines Word‑Dokuments hinzufügen.
keywords: [Aspose.Words for .NET, insert header date, dynamic DATE field, DocumentBuilder header, Word document header automation]
url: /net/working-with-headers-and-footers/insert-header-date/
date: '2026-09-22'
lastmod: '2026-09-22'
schemas:
- author: Aspose
  dateModified: '2026-09-22'
  description: Erfahren Sie, wie Sie mit Aspose.Words für .NET ein dynamisches DATE‑Feld
    zur primären Kopfzeile eines Word‑Dokuments hinzufügen.
  headline: Dynamisches Datum in die Kopfzeile eines Word‑Dokuments einfügen mit Aspose.Words
    für .NET
  type: TechArticle
- description: Erfahren Sie, wie Sie mit Aspose.Words für .NET ein dynamisches DATE‑Feld
    zur primären Kopfzeile eines Word‑Dokuments hinzufügen.
  name: Dynamisches Datum in die Kopfzeile eines Word‑Dokuments einfügen mit Aspose.Words
    für .NET
  steps:
  - name: Erstellen Sie ein neues Document und einen DocumentBuilder, um es zu bearbeiten.
    text: Erstellen Sie ein neues Document und einen DocumentBuilder, um es zu bearbeiten.
  - name: Bewegen Sie den Cursor des Builders zur primären Kopfzeile, damit nachfolgende
      Einfügungen die Kopfzeile betreffen.
    text: Bewegen Sie den Cursor des Builders zur primären Kopfzeile, damit nachfolgende
      Einfügungen die Kopfzeile betreffen.
  - name: Schreiben Sie das statische Etikett und fügen Sie ein DATE‑Feld mit dem
      Format „MMMM d, yyyy“ in die Kopfzeile ein, wodurch ein dynamisches Datum entsteht.
    text: Schreiben Sie das statische Etikett und fügen Sie ein DATE‑Feld mit dem
      Format „MMMM d, yyyy“ in die Kopfzeile ein, wodurch ein dynamisches Datum entsteht.
  - name: Kehren Sie zum Hauptteil zurück und fügen Sie einen Beispielabsatz hinzu,
      um normalen Dokumentinhalt neben der Kopfzeile zu demonstrieren.
    text: Kehren Sie zum Hauptteil zurück und fügen Sie einen Beispielabsatz hinzu,
      um normalen Dokumentinhalt neben der Kopfzeile zu demonstrieren.
  - name: Speichern Sie das Dokument als .docx‑Datei.
    text: Speichern Sie das Dokument als .docx‑Datei.
  type: HowTo
- questions:
  - answer: Der Aufruf `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` positioniert
      den Builder an der vorhandenen primären Kopfzeile, und `Write`/`InsertField`
      hängen einfach Text an das bereits Vorhandene an; sie löschen keinen bestehenden
      Inhalt.
    question: Was passiert, wenn das Dokument bereits eine primäre Kopfzeile hat –
      überschreibt mein Code diese?
  - answer: Ja – ändern Sie das Switch‑Format im Feldcode, der an `InsertField` übergeben
      wird, z. B. erzeugt `builder.InsertField(\"DATE \\@ \"yyyy-MM-dd\"")` ein Datum
      wie 2026-09-22.
    question: Kann ich das Datumsformat des DATE‑Feldes ändern, und wenn ja, wie?
  - answer: Ersetzen Sie `HeaderFooterType.HeaderPrimary` durch `HeaderFooterType.HeaderFirst`
      beim Aufruf von `MoveToHeaderFooter`; der Rest des Codes funktioniert identisch.
    question: Wenn ich das Datumsfeld in der Kopfzeile der ersten Seite statt in der
      primären Kopfzeile benötige, was soll ich tun?
  - answer: Das Feld wird nur mit dem Switch `\\@` eingefügt, der Word anweist, bei
      jeder Aktualisierung des Feldes (z. B. beim Öffnen der Datei oder beim Drücken
      von Strg+Alt+F9) das aktuelle Datum anzuzeigen.
    question: Wird das DATE‑Feld automatisch aktualisiert, wenn das Dokument später
      geöffnet wird?
  type: FAQPage
images:
- /net/working-with-headers-and-footers/insert-header-date/og-image.png
og_title: Ein dynamisches Datum zu einer Word‑Kopfzeile hinzufügen
og_description: Schritt‑für‑Schritt‑Anleitung, um ein Live‑Datumsfeld in Ihre Word‑Kopfzeile mit Aspose.Words einzubetten.
og_image_alt: Screenshot, der zeigt, wie man mit Aspose.Words für .NET ein dynamisches DATE‑Feld in die Kopfzeile eines Word‑Dokuments einfügt
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dynamisches Datum in die Kopfzeile eines Word‑Dokuments einfügen mit Aspose.Words für .NET
Dieses Tutorial zeigt, wie man die Klassen Document und DocumentBuilder in Aspose.Words für .NET verwendet, um ein dynamisches DATE‑Feld in die primäre Kopfzeile eines Word‑Dokuments einzufügen. Das hinzugefügte Feld wird bei jedem Öffnen des Dokuments automatisch auf das aktuelle Datum aktualisiert, sodass Ihre Kopfzeile stets das neueste Datum anzeigt. Folgen Sie dem Schritt‑für‑Schritt‑Code, um das Feld hinzuzufügen und die aktualisierte Datei zu speichern.

---

{{< tutorial-widget sourcePath="words/net/working-with-headers-and-footers/insert-header-date" >}}


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
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: Was passiert, wenn das Dokument bereits eine primäre Kopfzeile hat – überschreibt mein Code diese?**  
A: Der Aufruf `MoveToHeaderFooter(HeaderFooterType.HeaderPrimary)` positioniert den Builder an der vorhandenen primären Kopfzeile, und `Write`/`InsertField` hängen einfach Text an das bereits Vorhandene an; sie löschen keinen bestehenden Inhalt.

**Q: Kann ich das Datumsformat des DATE‑Feldes ändern, und wenn ja, wie?**  
A: Ja – ändern Sie das Switch‑Format im Feldcode, der an `InsertField` übergeben wird, z. B. erzeugt `builder.InsertField(\"DATE \\@ \"yyyy-MM-dd\"")` ein Datum wie 2026-09-22.

**Q: Wenn ich das Datumsfeld in der Kopfzeile der ersten Seite statt in der primären Kopfzeile benötige, was soll ich tun?**  
A: Ersetzen Sie `HeaderFooterType.HeaderPrimary` durch `HeaderFooterType.HeaderFirst` beim Aufruf von `MoveToHeaderFooter`; der Rest des Codes funktioniert identisch.

**Q: Wird das DATE‑Feld automatisch aktualisiert, wenn das Dokument später geöffnet wird?**  
A: Das Feld wird nur mit dem Switch `\\@` eingefügt, der Word anweist, bei jeder Aktualisierung des Feldes (z. B. beim Öffnen der Datei oder beim Drücken von Strg+Alt+F9) das aktuelle Datum anzuzeigen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}