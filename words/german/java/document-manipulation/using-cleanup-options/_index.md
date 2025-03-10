---
title: Verwenden von Bereinigungsoptionen in Aspose.Words für Java
linktitle: Bereinigungsoptionen verwenden
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Verbessern Sie die Übersichtlichkeit von Dokumenten mit den Bereinigungsoptionen von Aspose.Words für Java. Erfahren Sie, wie Sie leere Absätze, ungenutzte Bereiche und mehr entfernen.
weight: 10
url: /de/java/document-manipulation/using-cleanup-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Bereinigungsoptionen in Aspose.Words für Java


## Einführung in die Verwendung von Bereinigungsoptionen in Aspose.Words für Java

In diesem Tutorial erfahren Sie, wie Sie Bereinigungsoptionen in Aspose.Words für Java verwenden, um Dokumente während des Seriendruckprozesses zu bearbeiten und zu bereinigen. Mit Bereinigungsoptionen können Sie verschiedene Aspekte der Dokumentbereinigung steuern, z. B. das Entfernen leerer Absätze, nicht verwendeter Bereiche und mehr.

## Voraussetzungen

 Bevor wir beginnen, stellen Sie sicher, dass Sie die Aspose.Words für Java-Bibliothek in Ihr Projekt integriert haben. Sie können sie hier herunterladen:[Hier](https://releases.aspose.com/words/java/).

## Schritt 1: Leere Absätze entfernen

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Seriendruckfelder einfügen
FieldMergeField mergeFieldOption1 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_1");
mergeFieldOption1.setFieldName("Option_1");
builder.write(" ? ");
FieldMergeField mergeFieldOption2 = (FieldMergeField) builder.insertField("MERGEFIELD", "Option_2");
mergeFieldOption2.setFieldName("Option_2");

// Bereinigungsoptionen festlegen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS);

// Aktivieren Sie die Bereinigung von Absätzen mit Satzzeichen
doc.getMailMerge().setCleanupParagraphsWithPunctuationMarks(true);

// Serienbrief ausführen
doc.getMailMerge().execute(new String[] { "Option_1", "Option_2" }, new Object[] { null, null });

// Speichern des Dokuments
doc.save("WorkingWithCleanupOptions.CleanupParagraphsWithPunctuationMarks.docx");
```

In diesem Beispiel erstellen wir ein neues Dokument, fügen Seriendruckfelder ein und legen die Bereinigungsoptionen fest, um leere Absätze zu entfernen. Zusätzlich aktivieren wir das Entfernen von Absätzen mit Satzzeichen. Nach dem Ausführen des Seriendrucks wird das Dokument mit der angegebenen Bereinigung gespeichert.

## Schritt 2: Nicht zusammengeführte Regionen entfernen

```java
Document doc = new Document("Your Directory Path" + "Mail merge destination - Northwind suppliers.docx");
DataSet data = new DataSet();

// Legen Sie Bereinigungsoptionen fest, um nicht verwendete Bereiche zu entfernen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS);

// Serienbrief mit Regionen ausführen
doc.getMailMerge().executeWithRegions(data);

// Speichern des Dokuments
doc.save("WorkingWithCleanupOptions.RemoveUnmergedRegions.docx");
```

In diesem Beispiel öffnen wir ein vorhandenes Dokument mit Seriendruckbereichen, legen die Bereinigungsoptionen fest, um nicht verwendete Bereiche zu entfernen, und führen dann den Seriendruck mit leeren Daten aus. Dieser Vorgang entfernt automatisch die nicht verwendeten Bereiche aus dem Dokument.

## Schritt 3: Leere Felder entfernen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Legen Sie Bereinigungsoptionen fest, um leere Felder zu entfernen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_FIELDS);

// Serienbrief ausführen
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Speichern des Dokuments
doc.save("WorkingWithCleanupOptions.RemoveEmptyFields.docx");
```

In diesem Beispiel öffnen wir ein Dokument mit Seriendruckfeldern, legen die Bereinigungsoptionen fest, um leere Felder zu entfernen, und führen den Seriendruck mit Daten aus. Nach dem Seriendruck werden alle leeren Felder aus dem Dokument entfernt.

## Schritt 4: Entfernen nicht verwendeter Felder

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Legen Sie Bereinigungsoptionen fest, um nicht verwendete Felder zu entfernen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS);

// Serienbrief ausführen
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Speichern des Dokuments
doc.save("WorkingWithCleanupOptions.RemoveUnusedFields.docx");
```

In diesem Beispiel öffnen wir ein Dokument mit Seriendruckfeldern, legen die Bereinigungsoptionen fest, um nicht verwendete Felder zu entfernen, und führen den Seriendruck mit Daten aus. Nach dem Seriendruck werden alle nicht verwendeten Felder aus dem Dokument entfernt.

## Schritt 5: Entfernen enthaltener Felder

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Legen Sie Bereinigungsoptionen fest, um enthaltene Felder zu entfernen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS);

// Serienbrief ausführen
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Speichern des Dokuments
doc.save("WorkingWithCleanupOptions.RemoveContainingFields.docx");
```

In diesem Beispiel öffnen wir ein Dokument mit Seriendruckfeldern, legen die Bereinigungsoptionen fest, um enthaltene Felder zu entfernen, und führen den Seriendruck mit Daten aus. Nach dem Seriendruck werden die Felder selbst aus dem Dokument entfernt.

## Schritt 6: Leere Tabellenzeilen entfernen

```java
Document doc = new Document("Your Directory Path" + "Table with fields.docx");

// Legen Sie Bereinigungsoptionen fest, um leere Tabellenzeilen zu entfernen
doc.getMailMerge().setCleanupOptions(MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS);

// Serienbrief ausführen
doc.getMailMerge().execute(new String[] { "FullName", "Company", "Address", "Address2", "City" },
    new Object[] { "James Bond", "MI5 Headquarters", "Milbank", "", "London" });

// Speichern des Dokuments
doc.save("WorkingWithCleanupOptions.RemoveEmptyTableRows.docx");
```

In diesem Beispiel öffnen wir ein Dokument mit einer Tabelle und Seriendruckfeldern, legen die Bereinigungsoptionen fest, um leere Tabellenzeilen zu entfernen, und führen den Seriendruck mit Daten aus. Nach dem Seriendruck werden alle leeren Tabellenzeilen aus dem Dokument entfernt.

## Abschluss

In diesem Tutorial haben Sie gelernt, wie Sie Bereinigungsoptionen in Aspose.Words für Java verwenden, um Dokumente während des Seriendruckprozesses zu bearbeiten und zu bereinigen. Diese Optionen bieten eine detaillierte Kontrolle über die Dokumentbereinigung, sodass Sie mühelos ausgefeilte und benutzerdefinierte Dokumente erstellen können.

## Häufig gestellte Fragen

### Welche Bereinigungsoptionen gibt es in Aspose.Words für Java?

Bereinigungsoptionen in Aspose.Words für Java sind Einstellungen, mit denen Sie verschiedene Aspekte der Dokumentbereinigung während des Seriendruckprozesses steuern können. Sie ermöglichen es Ihnen, unnötige Elemente wie leere Absätze, nicht verwendete Bereiche und mehr zu entfernen und so sicherzustellen, dass Ihr endgültiges Dokument gut strukturiert und ausgefeilt ist.

### Wie kann ich leere Absätze aus meinem Dokument entfernen?

 Um leere Absätze aus Ihrem Dokument mit Aspose.Words für Java zu entfernen, können Sie die`MailMergeCleanupOptions.REMOVE_EMPTY_PARAGRAPHS` Option auf „true“. Dadurch werden Absätze ohne Inhalt automatisch eliminiert, was zu einem übersichtlicheren Dokument führt.

###  Was ist der Zweck der`REMOVE_UNUSED_REGIONS` cleanup option?

 Der`MailMergeCleanupOptions.REMOVE_UNUSED_REGIONS` Mit dieser Option können Sie während des Seriendrucks Bereiche in einem Dokument entfernen, die keine entsprechenden Daten enthalten. Sie hilft Ihnen, Ihr Dokument übersichtlich zu halten, indem Sie nicht verwendete Platzhalter entfernen.

### Kann ich mit Aspose.Words für Java leere Tabellenzeilen aus einem Dokument entfernen?

 Ja, Sie können leere Tabellenzeilen aus einem Dokument entfernen, indem Sie die`MailMergeCleanupOptions.REMOVE_EMPTY_TABLE_ROWS`Bereinigungsoption auf „true“. Dadurch werden automatisch alle Tabellenzeilen gelöscht, die keine Daten enthalten, und so eine gut strukturierte Tabelle in Ihrem Dokument sichergestellt.

###  Was passiert, wenn ich die`REMOVE_CONTAINING_FIELDS` option?

 Einstellen der`MailMergeCleanupOptions.REMOVE_CONTAINING_FIELDS` Mit dieser Option wird während des Seriendruckvorgangs das gesamte Seriendruckfeld, einschließlich des darin enthaltenen Absatzes, aus dem Dokument entfernt. Dies ist nützlich, wenn Sie Seriendruckfelder und den zugehörigen Text entfernen möchten.

### Wie kann ich nicht verwendete Seriendruckfelder aus meinem Dokument entfernen?

 Um nicht verwendete Seriendruckfelder aus einem Dokument zu entfernen, können Sie die`MailMergeCleanupOptions.REMOVE_UNUSED_FIELDS` Option auf „true“. Dadurch werden Seriendruckfelder, die während des Seriendrucks nicht ausgefüllt werden, automatisch eliminiert, was zu einem übersichtlicheren Dokument führt.

###  Was ist der Unterschied zwischen`REMOVE_EMPTY_FIELDS` and `REMOVE_UNUSED_FIELDS` cleanup options?

 Der`REMOVE_EMPTY_FIELDS` entfernt Seriendruckfelder, die keine Daten enthalten oder leer sind, während des Seriendruckprozesses. Andererseits wird mit der`REMOVE_UNUSED_FIELDS`Mit dieser Option werden Seriendruckfelder entfernt, die während des Zusammenführens nicht mit Daten gefüllt werden. Die Auswahl zwischen diesen Feldern hängt davon ab, ob Sie Felder ohne Inhalt oder solche entfernen möchten, die bei dem jeweiligen Zusammenführungsvorgang nicht verwendet werden.

### Wie kann ich das Entfernen von Absätzen mit Satzzeichen aktivieren?

 Um das Entfernen von Absätzen mit Satzzeichen zu ermöglichen, können Sie die`cleanupParagraphsWithPunctuationMarks` auf true und geben Sie die Satzzeichen an, die bei der Bereinigung berücksichtigt werden sollen. Auf diese Weise können Sie ein verfeinertes Dokument erstellen, indem Sie unnötige Absätze entfernen, die nur aus Satzzeichen bestehen.

### Kann ich die Bereinigungsoptionen in Aspose.Words für Java anpassen?

Ja, Sie können die Bereinigungsoptionen Ihren spezifischen Anforderungen entsprechend anpassen. Sie können auswählen, welche Bereinigungsoptionen angewendet werden sollen, und sie entsprechend Ihren Dokumentbereinigungsanforderungen konfigurieren, um sicherzustellen, dass Ihr endgültiges Dokument Ihren gewünschten Standards entspricht.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
