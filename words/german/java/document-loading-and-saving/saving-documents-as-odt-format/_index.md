---
title: Speichern von Dokumenten im ODT-Format in Aspose.Words für Java
linktitle: Dokumente im ODT-Format speichern
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Erfahren Sie, wie Sie mit Aspose.Words für Java Dokumente im ODT-Format speichern. Stellen Sie die Kompatibilität mit Open-Source-Office-Suiten sicher.
weight: 19
url: /de/java/document-loading-and-saving/saving-documents-as-odt-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Speichern von Dokumenten im ODT-Format in Aspose.Words für Java


## Einführung zum Speichern von Dokumenten im ODT-Format in Aspose.Words für Java

In diesem Artikel erfahren Sie, wie Sie Dokumente mit Aspose.Words für Java im ODT-Format (Open Document Text) speichern. ODT ist ein beliebtes offenes Standarddokumentformat, das von verschiedenen Office-Suiten verwendet wird, darunter OpenOffice und LibreOffice. Durch das Speichern von Dokumenten im ODT-Format können Sie die Kompatibilität mit diesen Softwarepaketen sicherstellen.

## Voraussetzungen

Bevor wir beginnen, stellen Sie sicher, dass die folgenden Voraussetzungen erfüllt sind:

1. Java-Entwicklungsumgebung: Stellen Sie sicher, dass Java Development Kit (JDK) auf Ihrem System installiert ist.

2.  Aspose.Words für Java: Laden Sie die Bibliothek Aspose.Words für Java herunter und installieren Sie sie. Den Download-Link finden Sie[Hier](https://releases.aspose.com/words/java/).

3. Beispieldokument: Halten Sie ein Beispiel-Word-Dokument bereit (z. B. „Dokument.docx“), das Sie in das ODT-Format konvertieren möchten.

## Schritt 1: Dokument laden

Laden wir zunächst das Word-Dokument mit Aspose.Words für Java:

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
```

 Hier,`"Your Directory Path"` sollte auf das Verzeichnis verweisen, in dem sich Ihr Dokument befindet.

## Schritt 2: ODT-Speicheroptionen festlegen

Um das Dokument als ODT zu speichern, müssen wir die ODT-Speicheroptionen angeben. Außerdem können wir die Maßeinheit für das Dokument festlegen. Open Office verwendet Zentimeter, während MS Office Zoll verwendet. Wir stellen es auf Zoll ein:

```java
OdtSaveOptions saveOptions = new OdtSaveOptions();
saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES);
```

## Schritt 3: Speichern Sie das Dokument

Jetzt ist es an der Zeit, das Dokument im ODT-Format zu speichern:

```java
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

 Hier,`"Your Directory Path"` sollte auf das Verzeichnis verweisen, in dem Sie die konvertierte ODT-Datei speichern möchten.

## Vollständiger Quellcode zum Speichern von Dokumenten im ODT-Format in Aspose.Words für Java

```java
Document doc = new Document("Your Directory Path" + "Document.docx");
// Open Office verwendet Zentimeter bei der Angabe von Längen, Breiten und anderen messbaren Formatierungen
// und Inhaltseigenschaften in Dokumenten, während MS Office Zoll verwendet.
OdtSaveOptions saveOptions = new OdtSaveOptions(); { saveOptions.setMeasureUnit(OdtSaveMeasureUnit.INCHES); }
doc.save("Your Directory Path" + "WorkingWithOdtSaveOptions.MeasureUnit.odt", saveOptions);
```

## Abschluss

In diesem Artikel haben wir gelernt, wie man Dokumente mit Aspose.Words für Java im ODT-Format speichert. Dies kann besonders nützlich sein, wenn Sie die Kompatibilität mit Open-Source-Office-Suiten wie OpenOffice und LibreOffice sicherstellen müssen.

## Häufig gestellte Fragen

### Wie kann ich Aspose.Words für Java herunterladen?

 Sie können Aspose.Words für Java von der Aspose-Website herunterladen. Besuchen Sie[dieser Link](https://releases.aspose.com/words/java/) um auf die Download-Seite zuzugreifen.

### Welchen Vorteil bietet das Speichern von Dokumenten im ODT-Format?

Durch das Speichern von Dokumenten im ODT-Format wird die Kompatibilität mit Open-Source-Office-Suiten wie OpenOffice und LibreOffice sichergestellt. Dadurch wird den Benutzern dieser Softwarepakete der Zugriff auf Ihre Dokumente und deren Bearbeitung erleichtert.

### Muss ich beim Speichern im ODT-Format die Maßeinheit angeben?

Ja, es empfiehlt sich, die Maßeinheit anzugeben. Open Office verwendet standardmäßig Zentimeter. Wenn Sie also Zoll angeben, stellen Sie eine einheitliche Formatierung sicher.

### Kann ich mehrere Dokumente in einem Stapelprozess in das ODT-Format konvertieren?

Ja, Sie können die Konvertierung mehrerer Dokumente in das ODT-Format mit Aspose.Words für Java automatisieren, indem Sie Ihre Dokumentdateien durchlaufen und den Konvertierungsprozess anwenden.

### Ist Aspose.Words für Java mit den neuesten Java-Versionen kompatibel?

Aspose.Words für Java wird regelmäßig aktualisiert, um die neuesten Java-Versionen zu unterstützen und so Kompatibilität und Leistungsverbesserungen sicherzustellen. Überprüfen Sie unbedingt die Systemanforderungen in der Dokumentation, um die neuesten Informationen zu erhalten.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
