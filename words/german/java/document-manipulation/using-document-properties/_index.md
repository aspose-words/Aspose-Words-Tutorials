---
date: 2026-01-16
description: Erfahren Sie, wie Sie Zoll in Punkte umrechnen, Dokument‑Metadaten in
  Java auslesen, benutzerdefinierte Eigenschaften in Java hinzufügen und Seitenränder
  in Java mit Aspose.Words für Java festlegen.
linktitle: Using Document Properties
second_title: Aspose.Words Java Document Processing API
title: Zoll in Punkte umrechnen – Verwendung von Dokumenteigenschaften in Aspose.Words
  für Java
url: /de/java/document-manipulation/using-document-properties/
weight: 32
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zoll in Punkte umrechnen – Verwendung von Dokumenteigenschaften in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie **Zoll in Punkte umrechnen** beim Festlegen von Seitenrändern, Dokumentmetadaten in Java lesen, benutzerdefinierte Eigenschaften in Java hinzufügen und mit integrierten Dokumenteigenschaften mit Aspose.Words für Java arbeiten. Egal, ob Sie Berichte, Rechnungen oder Rechtsdokumente erstellen, das Beherrschen dieser Techniken gibt Ihnen eine feinkörnige Kontrolle über das Aussehen und die Metadaten Ihrer Word-Dateien.

## Schnelle Antworten
- **Wie konvertiere ich Zoll in Punkte?** Use `ConvertUtil.inchToPoint(value)` from Aspose.Words.
- **Kann ich Dokumentmetadaten in Java lesen?** Yes – call `doc.getBuiltInDocumentProperties()` or `doc.getCustomDocumentProperties()`.
- **Wie füge ich eine benutzerdefinierte Eigenschaft in Java hinzu?** Use `doc.getCustomDocumentProperties().add(name, value)`.
- **Welche Methode legt Seitenränder in Punkten fest?** `PageSetup.setTopMargin`, `setBottomMargin`, etc., accept point values.
- **Wird das Verlinken zu einem Lesezeichen unterstützt?** Yes – use `addLinkToContent` on the custom properties collection.

## Einführung in Dokumenteigenschaften

Dokumenteigenschaften sind ein wesentlicher Bestandteil jeder Word-Datei. Sie speichern Informationen wie Titel, Autor, Betreff, Schlüsselwörter und beliebige benutzerdefinierte Metadaten, die Sie für nachgelagerte Verarbeitung benötigen. In Aspose.Words für Java können Sie sowohl integrierte als auch benutzerdefinierte Dokumenteigenschaften manipulieren und zudem Layoutdetails wie Ränder steuern, indem Sie Maßeinheiten umrechnen (z. B. **Zoll in Punkte umrechnen**).

## Was bedeutet „Zoll in Punkte umrechnen“?

In Word werden Layout‑Maße in Punkten angegeben (1 Punkt = 1/72 Zoll). Das Umrechnen von Zoll in Punkte ermöglicht es Ihnen, Ränder, Einzüge und Abstände mit bekannten imperialen Einheiten zu definieren, während die API intern mit Punkten arbeitet.

## Warum Dokumentmetadaten in Java verwalten?

Das Einbetten von Metadaten erleichtert das Suchen, Kategorisieren und Automatisieren von Workflows. Beispielsweise können Sie einen Vertrag mit einem „Authorized“-Flag versehen oder eine Revisionsnummer für Prüfpfade speichern. Das programmgesteuerte Lesen und Schreiben dieser Informationen sorgt für Konsistenz bei großen Dokumentenstapeln.

## Voraussetzungen
- Java 17+ (oder kompatibles JDK)
- Aspose.Words for Java‑Bibliothek zu Ihrem Projekt hinzugefügt (Maven/Gradle)
- Eine Beispiel‑`.docx`‑Datei (z. B. `Properties.docx`) in einem zugänglichen Verzeichnis abgelegt

## Schritt‑für‑Schritt‑Anleitung

### Auflisten integrierter Dokumenteigenschaften
Unten ist ein einfacher Test, der ein Dokument öffnet und alle integrierten Eigenschaften wie Titel, Autor und Schlüsselwörter ausgibt.

```java
@Test
public void enumerateProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    System.out.println(MessageFormat.format("1. Document name: {0}", doc.getOriginalFileName()));
    System.out.println("2. Built-in Properties");
    for (DocumentProperty prop : doc.getBuiltInDocumentProperties())
        System.out.println(MessageFormat.format("{0} : {1}", prop.getName(), prop.getValue()));
}
```

> **Profi‑Tipp:** Verwenden Sie diesen Codeausschnitt, um zu überprüfen, ob Ihre Metadaten während der vorherigen Schritte korrekt geschrieben wurden.

### Hinzufügen benutzerdefinierter Dokumenteigenschaften (add custom properties java)
Benutzerdefinierte Eigenschaften ermöglichen es Ihnen, beliebige Datentypen zu speichern – boolesch, Zeichenkette, Datum, Zahl usw.

```java
@Test
public void addCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    CustomDocumentProperties customDocumentProperties = doc.getCustomDocumentProperties();

    if (customDocumentProperties.get("Authorized") != null) return;

    customDocumentProperties.add("Authorized", true);
    customDocumentProperties.add("Authorized By", "John Smith");
    customDocumentProperties.add("Authorized Date", new Date());
    customDocumentProperties.add("Authorized Revision", doc.getBuiltInDocumentProperties().getRevisionNumber());
    customDocumentProperties.add("Authorized Amount", 123.45);
}
```

> **Warum das wichtig ist:** Das Hinzufügen eines Flags wie **Authorized** kann nachgelagerte Genehmigungs‑Workflows steuern, ohne den Dokumentinhalt zu ändern.

### Entfernen einer benutzerdefinierten Eigenschaft
Wenn eine Eigenschaft nicht mehr benötigt wird, können Sie sie sauber löschen.

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

### Konfigurieren eines Links zum Inhalt (bookmark linking)
Sie können ein Lesezeichen erstellen und dann eine benutzerdefinierte Eigenschaft hinzufügen, die auf dieses Lesezeichen verweist, wodurch dynamische Querverweise ermöglicht werden.

```java
@Test
public void configuringLinkToContent() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.startBookmark("MyBookmark");
    builder.writeln("Text inside a bookmark.");
    builder.endBookmark("MyBookmark");

    CustomDocumentProperties customProperties = doc.getCustomDocumentProperties();

    // Add linked to content property.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

### Umwandeln zwischen Maßeinheiten (set page margins java)
Hier kommt das Hauptkeyword zum Einsatz. Wir setzen die Ränder in Zoll und dann **Zoll in Punkte umrechnen** mit `ConvertUtil`.

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Set margins in inches.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

> **Hinweis:** `ConvertUtil` bietet außerdem `pointToInch`, `mmToPoint` usw. für flexible Layout‑Verarbeitung.

### Verwenden von Steuerzeichen (read document metadata java)
Steuerzeichen helfen Ihnen, Textströme zu bereinigen. Dieses Beispiel ersetzt einen Wagenrücklauf (`\r`) durch die Windows‑Zeilenumbruchsequenz (`\r\n`).

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Replace "\r" control character with "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

## Häufige Probleme & Lösungen
| Problem | Ursache | Lösung |
|---------|---------|--------|
| Ränder sehen nach der Umrechnung falsch aus | Falsche Einheit verwendet (z. B. cm statt Zoll) | Stellen Sie sicher, dass Sie `ConvertUtil.inchToPoint` für Zoll‑Werte aufrufen |
| Benutzerdefinierte Eigenschaft erscheint nicht | Eigenschaft nach dem Speichern des Dokuments hinzugefügt | Rufen Sie `doc.save(...)` nach dem Hinzufügen der Eigenschaften auf |
| Lesezeichen‑Link defekt | Tippfehler im Lesezeichennamen | Stellen Sie sicher, dass der Lesezeichename in `addLinkToContent` exakt übereinstimmt |

## FAQ

### Wie greife ich auf integrierte Dokumenteigenschaften zu?
Um integrierte Dokumenteigenschaften in Aspose.Words für Java zuzugreifen, können Sie die Methode `getBuiltInDocumentProperties` des `Document`‑Objekts verwenden. Diese Methode gibt eine Sammlung integrierter Eigenschaften zurück, die Sie iterieren können.

### Kann ich einem Dokument benutzerdefinierte Dokumenteigenschaften hinzufügen?
Ja, Sie können einem Dokument benutzerdefinierte Dokumenteigenschaften über die Sammlung `CustomDocumentProperties` hinzufügen. Sie können benutzerdefinierte Eigenschaften mit verschiedenen Datentypen definieren, einschließlich Zeichenketten, Booleschen, Datums‑ und numerischen Werten.

### Wie kann ich eine bestimmte benutzerdefinierte Dokumenteigenschaft entfernen?
Um eine bestimmte benutzerdefinierte Dokumenteigenschaft zu entfernen, können Sie die Methode `remove` der Sammlung `CustomDocumentProperties` verwenden und dabei den Namen der zu entfernenden Eigenschaft als Parameter übergeben.

### Welchen Zweck hat das Verlinken zu Inhalten innerhalb eines Dokuments?
Das Verlinken zu Inhalten innerhalb eines Dokuments ermöglicht es, dynamische Verweise auf bestimmte Teile des Dokuments zu erstellen. Dies kann nützlich sein, um interaktive Dokumente oder Querverweise zwischen Abschnitten zu erzeugen.

### Wie kann ich zwischen verschiedenen Maßeinheiten in Aspose.Words für Java konvertieren?
Sie können zwischen verschiedenen Maßeinheiten in Aspose.Words für Java konvertieren, indem Sie die Klasse `ConvertUtil` verwenden. Sie bietet Methoden zum Umrechnen von Einheiten wie Zoll zu Punkten, Punkte zu Zentimetern und mehr.

## Häufig gestellte Fragen

**Q: Wie lese ich Dokumentmetadaten in Java, ohne die gesamte Datei zu laden?**  
A: Verwenden Sie `DocumentInfo`, um Kern‑Eigenschaften abzurufen, ohne den Dokumentinhalt vollständig zu laden.

**Q: Kann ich Seitenränder in Java programmgesteuert für bestehende Dokumente festlegen?**  
A: Ja – öffnen Sie das Dokument, ändern Sie die `PageSetup`‑Ränder (Zoll in Punkte umrechnen falls nötig) und speichern Sie.

**Q: Ist es möglich, benutzerdefinierte Eigenschaften in PDF‑Metadaten zu exportieren?**  
A: Beim Speichern als PDF mappt Aspose.Words benutzerdefinierte Dokumenteigenschaften automatisch auf benutzerdefinierte PDF‑Metadaten.

**Q: Beeinflussen Steuerzeichen die PDF‑Konvertierung?**  
A: Sie werden während der Konvertierung beibehalten; Sie können jedoch Zeilenenden zur Konsistenz normalisieren.

**Q: Welche Aspose.Words‑Version wird für `ConvertUtil` benötigt?**  
A: `ConvertUtil` ist seit Aspose.Words 16.5 verfügbar; jede neuere Version unterstützt es.

## Fazit

Durch das Beherrschen von **Zoll in Punkte umrechnen**, dem Lesen von Dokumentmetadaten in Java und dem Hinzufügen benutzerdefinierter Eigenschaften in Java erhalten Sie die vollständige Kontrolle über das visuelle Layout und die verborgenen Daten Ihrer Word‑Dateien. Diese Möglichkeiten befähigen Sie, automatisierte Dokument‑Pipelines zu bauen, Compliance durchzusetzen und reich formatierte Berichte zu erstellen – alles mit Aspose.Words für Java.

---

**Zuletzt aktualisiert:** 2026-01-16  
**Getestet mit:** Aspose.Words for Java 24.11  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}