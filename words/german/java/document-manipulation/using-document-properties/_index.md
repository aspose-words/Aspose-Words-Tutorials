---
title: Verwenden von Dokumenteigenschaften in Aspose.Words für Java
linktitle: Verwenden von Dokumenteigenschaften
second_title: Aspose.Words Java-API zur Dokumentverarbeitung
description: Optimieren Sie die Dokumentenverwaltung mit Aspose.Words für Java. Erfahren Sie in diesem umfassenden Tutorial, wie Sie mit Dokumenteigenschaften arbeiten, benutzerdefinierte Metadaten hinzufügen und vieles mehr.
weight: 32
url: /de/java/document-manipulation/using-document-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Dokumenteigenschaften in Aspose.Words für Java


## Einführung in Dokumenteigenschaften

Dokumenteigenschaften sind ein wesentlicher Bestandteil jedes Dokuments. Sie liefern zusätzliche Informationen über das Dokument selbst, wie etwa Titel, Autor, Betreff, Schlüsselwörter und mehr. In Aspose.Words für Java können Sie sowohl integrierte als auch benutzerdefinierte Dokumenteigenschaften bearbeiten.

## Aufzählen von Dokumenteigenschaften

### Integrierte Eigenschaften

Zum Abrufen und Arbeiten mit integrierten Dokumenteigenschaften können Sie den folgenden Codeausschnitt verwenden:

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

Dieser Code zeigt den Namen und die integrierten Eigenschaften des Dokuments an, einschließlich Eigenschaften wie „Titel“, „Autor“ und „Schlüsselwörter“.

### Benutzerdefinierte Eigenschaften

Um mit benutzerdefinierten Dokumenteigenschaften zu arbeiten, können Sie den folgenden Codeausschnitt verwenden:

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

Dieser Codeausschnitt zeigt, wie benutzerdefinierte Dokumenteigenschaften hinzugefügt werden, darunter ein Boolescher Wert, eine Zeichenfolge, ein Datum, eine Revisionsnummer und ein numerischer Wert.

## Entfernen von Dokumenteigenschaften

Um bestimmte Dokumenteigenschaften zu entfernen, können Sie den folgenden Code verwenden:

```java
@Test
public void removeCustomDocumentProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "Properties.docx");
    doc.getCustomDocumentProperties().remove("Authorized Date");
}
```

Dieser Code entfernt die benutzerdefinierte Eigenschaft „Autorisierungsdatum“ aus dem Dokument.

## Link zum Inhalt konfigurieren

In manchen Fällen möchten Sie möglicherweise Links innerhalb Ihres Dokuments erstellen. So können Sie das tun:

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

    // Verknüpfte Eigenschaft zum Inhalt hinzufügen.
    DocumentProperty customProperty = customProperties.addLinkToContent("Bookmark", "MyBookmark");
    customProperty = customProperties.get("Bookmark");
    boolean isLinkedToContent = customProperty.isLinkToContent();
    String linkSource = customProperty.getLinkSource();
    String customPropertyValue = customProperty.getValue().toString();
}
```

Dieser Codeausschnitt zeigt, wie Sie in Ihrem Dokument ein Lesezeichen erstellen und eine benutzerdefinierte Dokumenteigenschaft hinzufügen, die auf dieses Lesezeichen verweist.

## Umrechnung zwischen Maßeinheiten

In Aspose.Words für Java können Sie Maßeinheiten ganz einfach umrechnen. Hier ist ein Beispiel dafür:

```java
@Test
public void convertBetweenMeasurementUnits() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    PageSetup pageSetup = builder.getPageSetup();

    // Legen Sie die Ränder in Zoll fest.
    pageSetup.setTopMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setBottomMargin(ConvertUtil.inchToPoint(1.0));
    pageSetup.setLeftMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setRightMargin(ConvertUtil.inchToPoint(1.5));
    pageSetup.setHeaderDistance(ConvertUtil.inchToPoint(0.2));
    pageSetup.setFooterDistance(ConvertUtil.inchToPoint(0.2));
}
```

Dieser Codeausschnitt legt verschiedene Ränder und Abstände in Zoll fest, indem er sie in Punkte umwandelt.

## Verwenden von Steuerzeichen

Steuerzeichen können beim Arbeiten mit Text nützlich sein. So ersetzen Sie ein Steuerzeichen in Ihrem Text:

```java
@Test
public void useControlCharacters()
{
    final String TEXT = "test\r";

    // Ersetzen Sie das Steuerzeichen "\r" durch "\r\n".
    String replace = TEXT.replace(ControlChar.CR, ControlChar.CR_LF);
}
```

In diesem Beispiel ersetzen wir den Wagenrücklauf (`\r`) mit einem Wagenrücklauf gefolgt von einem Zeilenvorschub (`\r\n`).

## Abschluss

Dokumenteigenschaften spielen eine wichtige Rolle bei der effektiven Verwaltung und Organisation Ihrer Dokumente in Aspose.Words für Java. Ob Sie mit integrierten Eigenschaften, benutzerdefinierten Eigenschaften oder Steuerzeichen arbeiten, Ihnen stehen eine Reihe von Tools zur Verfügung, um Ihre Dokumentverwaltungsfunktionen zu verbessern.

## Häufig gestellte Fragen

### Wie greife ich auf integrierte Dokumenteigenschaften zu?

 Um auf integrierte Dokumenteigenschaften in Aspose.Words für Java zuzugreifen, können Sie den`getBuiltInDocumentProperties` Methode auf der`Document` Objekt. Diese Methode gibt eine Sammlung integrierter Eigenschaften zurück, die Sie durchlaufen können.

### Kann ich einem Dokument benutzerdefinierte Dokumenteigenschaften hinzufügen?

 Ja, Sie können einem Dokument benutzerdefinierte Dokumenteigenschaften hinzufügen, indem Sie`CustomDocumentProperties` Sammlung. Sie können benutzerdefinierte Eigenschaften mit verschiedenen Datentypen definieren, darunter Zeichenfolgen, Boolesche Werte, Daten und numerische Werte.

### Wie kann ich eine bestimmte benutzerdefinierte Dokumenteigenschaft entfernen?

 Um eine bestimmte benutzerdefinierte Dokumenteigenschaft zu entfernen, können Sie das`remove` Methode auf der`CustomDocumentProperties`Sammlung, und übergeben Sie den Namen der Eigenschaft, die Sie entfernen möchten, als Parameter.

### Welchen Zweck hat das Verlinken auf Inhalte innerhalb eines Dokuments?

Durch Verknüpfen von Inhalten innerhalb eines Dokuments können Sie dynamische Verweise auf bestimmte Teile des Dokuments erstellen. Dies kann zum Erstellen interaktiver Dokumente oder von Querverweisen zwischen Abschnitten nützlich sein.

### Wie kann ich in Aspose.Words für Java zwischen verschiedenen Maßeinheiten umrechnen?

 Sie können in Aspose.Words für Java zwischen verschiedenen Maßeinheiten konvertieren, indem Sie den`ConvertUtil` Klasse. Sie bietet Methoden zum Umrechnen von Einheiten wie Zoll in Punkte, Punkte in Zentimeter und mehr.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
