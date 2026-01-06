---
date: 2026-01-06
description: Erfahren Sie, wie Sie Fußzeilen aus Word‑Dokumenten mit Aspose.Words
  für Java entfernen und wie Sie Abschnittswechsel, Seitenumbrüche und mehr löschen.
linktitle: Removing Content from Documents
second_title: Aspose.Words Java Document Processing API
title: Wie man Fußzeilen aus Word‑Dokumenten mit Aspose.Words für Java entfernt
url: /de/java/document-manipulation/removing-content-from-documents/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# So entfernen Sie Fußzeilen aus Word‑Dokumenten mit Aspose.Words für Java

## Einführung in Aspose.Words für Java

In diesem Tutorial erfahren Sie **wie Sie Fußzeilen aus Word**‑Dateien programmgesteuert mit Aspose.Words für Java entfernen. Egal, ob Sie generierte Berichte bereinigen, vertrauliche Informationen entfernen oder einfach eine Vorlage aufräumen möchten – dieser Leitfaden führt Sie durch die gängigsten Szenarien zum Entfernen von Inhalten: Seitenumbrüche, Abschnittswechsel, Fußzeilen und Inhaltsverzeichnisse. Los geht’s!

## Schnelle Antworten
- **Kann ich Fußzeilen entfernen, ohne andere Inhalte zu beeinflussen?** Ja, die API ermöglicht das gezielte Ansprechen von Fußzeilen‑Knoten.
- **Benötige ich eine Lizenz, um diese Beispiele auszuführen?** Eine kostenlose Testversion reicht für die Entwicklung; für den Produktionseinsatz ist eine Lizenz erforderlich.
- **Welche Word‑Formate werden unterstützt?** DOC, DOCX, DOCM und OOXML‑basierte Formate.
- **Ist der Code mit Java 8 und neuer kompatibel?** Absolut, die Bibliothek ist ab Version 8 Java‑kompatibel.
- **Wie lösche ich Abschnittswechsel?** Siehe den Abschnitt „Wie man Abschnittswechsel löscht“ weiter unten.

## Was bedeutet „Fußzeilen aus Word entfernen“?

Das Entfernen von Fußzeilen aus einem Word‑Dokument bedeutet, die `HeaderFooter`‑Knoten zu löschen, die am unteren Rand jeder Seite erscheinen. Dieser Vorgang ist üblich, wenn Sie ein sauberes Layout ohne Fußzeilen erzeugen oder wenn Fußzeilen sensible Daten enthalten, die nicht weitergegeben werden dürfen.

## Warum Aspose.Words für Java für diese Aufgabe verwenden?

Aspose.Words bietet ein hoch‑leveliges Objektmodell, das die Komplexität des DOCX‑Dateiformats abstrahiert. Sie können Absätze, Runs, Abschnitte und Fußzeilen mit wenigen Zeilen Java‑Code manipulieren, ohne dass Microsoft Word auf dem Server installiert sein muss.

## Voraussetzungen
- Java Development Kit (JDK) 8 oder neuer.
- Aspose.Words für Java‑Bibliothek (Download von der Aspose‑Website).
- Ein Beispiel‑Word‑Dokument (`Document.docx`) in einem bekannten Verzeichnis.

## Entfernen von Seitenumbrüchen

Seitenumbrüche steuern die Paginierung, müssen aber manchmal entfernt werden. Das folgende Snippet durchsucht jeden Absatz, setzt das Flag `PageBreakBefore` zurück und entfernt alle expliziten Seitenumbruch‑Zeichen.

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
NodeCollection paragraphs = doc.getChildNodes(NodeType.PARAGRAPH, true);
for (Paragraph para : (Iterable<Paragraph>) paragraphs) {
    if (para.getParagraphFormat().getPageBreakBefore()) {
        para.getParagraphFormat().setPageBreakBefore(false);
    }
    for (Run run : para.getRuns()) {
        if (run.getText().contains(ControlChar.PAGE_BREAK)) {
            run.setText(run.getText().replace(ControlChar.PAGE_BREAK, ""));
        }
    }
}
doc.save("Your Directory Path" + "RemoveContent.RemovePageBreaks.docx");
```

*Pro‑Tipp:* Führen Sie dies aus, bevor Sie Fußzeilen entfernen, wenn Sie ein einseitiges Layout wünschen.

## Wie man Abschnittswechsel löscht

Abschnittswechsel teilen ein Dokument in unabhängige Abschnitte, von denen jeder eigene Kopf‑ und Fußzeilen sowie Seiteneinstellungen hat. Um Abschnitte zu verschmelzen und effektiv **Abschnittswechsel zu löschen**, iterieren Sie in umgekehrter Reihenfolge, fügen den Inhalt jedes früheren Abschnitts an den letzten an und entfernen anschließend den nun leeren Abschnitt.

```java
for (int i = doc.getSections().getCount() - 2; i >= 0; i--) {
    doc.getLastSection().prependContent(doc.getSections().get(i));
    doc.getSections().get(i).remove();
}
```

Dieser Ansatz bewahrt alle Inhalte, während der strukturelle Bruch eliminiert wird.

## Entfernen von Fußzeilen (Hauptziel: Fußzeilen aus Word entfernen)

Fußzeilen enthalten häufig Seitenzahlen, Datumsangaben oder vertrauliche Notizen. Der untenstehende Code entfernt **alle Fußzeilentypen** – erste Seite, primär und sogar ungerade/gerade Seiten – aus jedem Abschnitt.

```java
Document doc = new Document("Your Directory Path" + "Header and footer types.docx");
for (Section section : doc.getSections()) {
    HeaderFooter footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_FIRST);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_PRIMARY);
    footer.remove();
    footer = section.getHeadersFooters().getByHeaderFooterType(HeaderFooterType.FOOTER_EVEN);
    footer.remove();
}
doc.save("Your Directory Path" + "RemoveContent.RemoveFooters.docx");
```

Nach Ausführung dieses Snippets enthält das resultierende Dokument **keine Fußzeilen**, wodurch das Hauptziel „Fußzeilen aus Word entfernen“ erreicht ist.

## Entfernen von Inhaltsverzeichnissen

Ein Inhaltsverzeichnis (TOC) wird als Feld gespeichert. Um es zu löschen, finden Sie das TOC‑Feld über seinen Index und entfernen den zugehörigen Knoten.

```java
Document doc = new Document("Your Directory Path" + "Table of contents.docx");
removeTableOfContents(doc, 0);
doc.save("Your Directory Path" + "RemoveContent.RemoveToc.doc");
```

*(Die Methode `removeTableOfContents` ist Teil der Aspose.Words‑Beispiele und entfernt den angegebenen TOC‑Knoten.)*

## Häufige Probleme & Fehlersuche

| Symptom | Wahrscheinliche Ursache | Lösung |
|---------|--------------------------|--------|
| Fußzeilen erscheinen weiterhin nach Ausführung des Codes | Das Dokument enthält **Kopf‑/Fußzeilen‑Paare**, die nicht angesprochen werden (z. B. fehlender `FOOTER_FIRST`) | Durchlaufen Sie alle Werte von `HeaderFooterType` oder prüfen Sie auf `null`, bevor Sie `remove()` aufrufen. |
| Seitenlayout ändert sich unerwartet nach dem Löschen von Abschnittswechseln | Abschnittsspezifische Seiteneinstellungen (Ränder, Ausrichtung) gingen verloren | Kopieren Sie die Abschnittseinstellungen in den Zielabschnitt, bevor Sie den Quellabschnitt entfernen. |
| `ControlChar.PAGE_BREAK` wird nicht entfernt | Das Dokument verwendet **Abschnittswechsel** statt Seitenumbruch‑Zeichen | Verwenden Sie zuerst die Methode „Wie man Abschnittswechsel löscht“. |

## Häufig gestellte Fragen

**F: Kann ich nur bestimmte Fußzeilen entfernen (z. B. nur die Fußzeile der ersten Seite)?**  
A: Ja. Rufen Sie die Fußzeile über ihren Typ (`FOOTER_FIRST`) ab und führen Sie `remove()` nur für diese Instanz aus.

**F: Wie lösche ich Abschnittswechsel, ohne Inhalte zu verschmelzen?**  
A: Sie können einen `Section`‑Knoten direkt entfernen, wenn Sie dessen Inhalt nicht behalten müssen; beachten Sie jedoch, dass dabei alle zugehörigen Kopf‑/Fußzeilen verloren gehen.

**F: Ist es möglich, programmgesteuert zu erkennen, ob ein Dokument ein TOC enthält, bevor man versucht, es zu löschen?**  
A: Verwenden Sie `doc.getRange().getFields()` und prüfen Sie auf Felder vom Typ `FieldType.FIELD_TABLE_OF_CONTENTS`.

**F: Unterstützt Aspose.Words das Entfernen von Fußzeilen aus verschlüsselten Word‑Dateien?**  
A: Ja, öffnen Sie das Dokument einfach mit dem Passwort: `new Document(path, new LoadOptions(password))`.

**F: Wirkt sich das Entfernen von Fußzeilen auf die Paginierung des Dokuments aus?**  
A: Das Entfernen von Fußzeilen ändert die Seitenzahlen nicht, es sei denn, die Fußzeile selbst enthält das Seitenzahlen‑Feld. Wenn Sie die Seitenzahlen neu nummerieren müssen, aktualisieren Sie die entsprechenden Felder.

## Fazit

Wir haben alles behandelt, was Sie benötigen, um **Fußzeilen aus Word**‑Dokumenten mit Aspose.Words für Java zu entfernen, einschließlich verwandter Aufgaben wie dem Löschen von Seitenumbrüchen, **wie man Abschnittswechsel löscht** und dem Entfernen von Inhaltsverzeichnissen. Mit diesen Snippets können Sie saubere, professionelle Dokumente erstellen, die exakt den Anforderungen Ihrer Anwendung entsprechen.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}

---

**Zuletzt aktualisiert:** 2026-01-06  
**Getestet mit:** Aspose.Words für Java 24.12  
**Autor:** Aspose  

---