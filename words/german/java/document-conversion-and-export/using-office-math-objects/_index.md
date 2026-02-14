---
date: 2026-02-14
description: Erfahren Sie, wie Sie Mathematik inline anzeigen, mathematische Gleichungen
  einfügen und Office‑Math‑Objekte mühelos mit Aspose.Words für Java manipulieren.
linktitle: Using Office Math Objects
second_title: Aspose.Words Java Document Processing API
title: Mathematik inline mit Office Math in Aspose.Words für Java anzeigen
url: /de/java/document-conversion-and-export/using-office-math-objects/
weight: 13
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Mathe inline anzeigen mit Office Math in Aspose.Words für Java

In diesem umfassenden Tutorial erfahren Sie, wie Sie **Mathematik inline anzeigen** können, indem Sie Office‑Math‑Objekte in Aspose.Words für Java verwenden. Egal, ob Sie **mathematische Gleichungen** in einen Bericht einfügen oder die Formatierung komplexer Formeln feinabstimmen müssen, führt Sie dieser Leitfaden durch jeden Schritt – vom Laden eines Word‑Dokuments bis zum Speichern des Endergebnisses.

## Schnelle Antworten
- **Was bedeutet „Mathematik inline anzeigen“?** Die Gleichung erscheint im Textfluss und nicht in einer eigenen Zeile.  
- **Welche Klasse repräsentiert ein Mathe‑Objekt?** `OfficeMath` in der Aspose.Words‑API.  
- **Kann ich die Ausrichtung ändern?** Ja, verwenden Sie `setJustification` mit LEFT, CENTER oder RIGHT.  
- **Benötige ich eine Lizenz für diese Funktion?** Eine gültige Aspose.Words‑für‑Java‑Lizenz ist für den Produktionseinsatz erforderlich.  
- **Welche Version wird demonstriert?** Der Code funktioniert mit der neuesten Aspose.Words‑für‑Java‑Version (2026).

## Was bedeutet „Mathematik inline anzeigen“?
Mathematik inline anzuzeigen bedeutet, dass die Gleichung als Teil des Absatztextes behandelt wird und sich natürlich mit den umgebenden Wörtern umbrechen kann. Dies ist nützlich für kurze Formeln, die den Lesefluss nicht unterbrechen sollten.

## Warum Office‑Math‑Objekte in Aspose.Words für Java verwenden?
- **Präzise Kontrolle** über das Layout der Gleichung (inline vs. display).  
- **Programmgesteuerte Manipulation** von Gleichungen, ohne Word manuell zu öffnen.  
- **Konsistentes Rendering** über Plattformen hinweg, ideal für die automatisierte Berichtserstellung.

## Voraussetzungen
Bevor wir beginnen, stellen Sie sicher, dass Sie:

- Aspose.Words für Java installiert und in Ihrem Projekt referenziert.  
- Eine Word‑Datei, die bereits eine Office‑Math‑Gleichung enthält (z. B. `OfficeMath.docx`).  
- Eine gültige Lizenz, falls Sie den Code außerhalb des Evaluationsmodus ausführen möchten.

## Schritt‑für‑Schritt‑Anleitung

### Dokument laden
Zuerst laden Sie das Dokument, das die Office‑Math‑Gleichung enthält, mit der Sie arbeiten möchten:

```java
Document doc = new Document("Your Directory Path" + "OfficeMath.docx");
```

### Auf das Office‑Math‑Objekt zugreifen
Rufen Sie den ersten Office‑Math‑Knoten aus dem Dokument ab:

```java
OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
```

### Anzeigetyp festlegen (Inline vs. Display)
Steuern Sie, ob die Gleichung inline mit dem umgebenden Text oder in einer eigenen Zeile erscheint. Für **Mathematik inline anzeigen** verwenden Sie das `INLINE`‑Enum; für eine separate Zeile verwenden Sie `DISPLAY`:

```java
officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
```

*Wenn Sie möchten, dass die Gleichung inline bleibt, ersetzen Sie `DISPLAY` durch `INLINE`.*

### Ausrichtung festlegen
Passen Sie die Ausrichtung der Gleichung an. Unten wird sie linksbündig ausgerichtet, Sie können jedoch auch `CENTER` oder `RIGHT` wählen:

```java
officeMath.setJustification(OfficeMathJustification.LEFT);
```

### Das geänderte Dokument speichern
Schreiben Sie schließlich die Änderungen in eine neue Datei:

```java
doc.save("Your Directory Path" + "ModifiedOfficeMath.docx");
```

## Vollständiger Quellcode zur Verwendung von Office‑Math‑Objekten in Aspose.Words für Java

```java
        Document doc = new Document("Your Directory Path" + "Office math.docx");
        OfficeMath officeMath = (OfficeMath) doc.getChild(NodeType.OFFICE_MATH, 0, true);
        // OfficeMath display type represents whether an equation is displayed inline with the text or displayed on its line.
        officeMath.setDisplayType(OfficeMathDisplayType.DISPLAY);
        officeMath.setJustification(OfficeMathJustification.LEFT);
        doc.save("Your Directory Path" + "WorkingWithOfficeMath.MathEquations.docx");
```

## Häufige Probleme & Fehlerbehebung
- **Gleichung nicht gefunden:** Stellen Sie sicher, dass das Dokument tatsächlich ein Office‑Math‑Objekt enthält; andernfalls gibt `doc.getChild` `null` zurück.  
- **Anzeigetyp hat keine Wirkung:** Vergewissern Sie sich, dass Sie eine aktuelle Version von Aspose.Words verwenden; ältere Versionen unterstützen `OfficeMathDisplayType` möglicherweise nur eingeschränkt.  
- **Lizenz‑Ausnahme:** Wenn Sie einen Lizenzfehler sehen, prüfen Sie, ob Ihre Lizenzdatei korrekt geladen ist, bevor Sie die `Document`‑Instanz erstellen.

## Häufig gestellte Fragen

**F: Was ist der Zweck von Office‑Math‑Objekten in Aspose.Words für Java?**  
A: Office‑Math‑Objekte ermöglichen es, mathematische Gleichungen programmgesteuert darzustellen und zu manipulieren, wodurch Sie die volle Kontrolle über Anzeige und Formatierung erhalten.

**F: Kann ich Office‑Math‑Gleichungen in meinem Dokument unterschiedlich ausrichten?**  
A: Ja, verwenden Sie die Methode `setJustification`, um links, rechts oder zentriert auszurichten.

**F: Eignet sich Aspose.Words für Java zur Verarbeitung komplexer mathematischer Dokumente?**  
A: Absolut. Die Bibliothek unterstützt vollständig komplexe Gleichungen, verschachtelte Brüche, Matrizen und mehr.

**F: Wie kann ich mehr über Aspose.Words für Java erfahren?**  
A: Für umfassende Dokumentation und Downloads besuchen Sie [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**F: Wo kann ich Aspose.Words für Java herunterladen?**  
A: Sie können Aspose.Words für Java von der Website herunterladen: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

---

**Zuletzt aktualisiert:** 2026-02-14  
**Getestet mit:** Aspose.Words für Java 24.12 (neueste Version vom Feb 2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}