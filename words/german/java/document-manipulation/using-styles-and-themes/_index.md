---
"description": "Erfahren Sie, wie Sie die Dokumentformatierung mit Aspose.Words für Java verbessern. Entdecken Sie Stile, Designs und mehr in diesem umfassenden Handbuch mit Quellcodebeispielen."
"linktitle": "Verwenden von Stilen und Designs"
"second_title": "Aspose.Words Java-Dokumentverarbeitungs-API"
"title": "Verwenden von Stilen und Designs in Aspose.Words für Java"
"url": "/de/java/document-manipulation/using-styles-and-themes/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Verwenden von Stilen und Designs in Aspose.Words für Java


## Einführung in die Verwendung von Stilen und Designs in Aspose.Words für Java

In dieser Anleitung erfahren Sie, wie Sie mit Stilen und Designs in Aspose.Words für Java arbeiten, um die Formatierung und das Erscheinungsbild Ihrer Dokumente zu verbessern. Wir behandeln Themen wie das Abrufen und Kopieren von Stilen, das Verwalten von Designs und das Einfügen von Stiltrennzeichen. Los geht's!

## Abrufen von Stilen

Um Stile aus einem Dokument abzurufen, können Sie den folgenden Java-Codeausschnitt verwenden:

```java
Document doc = new Document();
String styleName = "";
// Holen Sie sich die Stilsammlung aus dem Dokument.
StyleCollection styles = doc.getStyles();
for (Style style : styles)
{
    if ("".equals(styleName))
    {
        styleName = style.getName();
        System.out.println(styleName);
    }
    else
    {
        styleName = styleName + ", " + style.getName();
        System.out.println(styleName);
    }
}
```

Dieser Code ruft die im Dokument definierten Stile ab und druckt ihre Namen.

## Stile kopieren

Um Stile von einem Dokument in ein anderes zu kopieren, können Sie die `copyStylesFromTemplate` Methode wie unten gezeigt:

```java
@Test
public void copyStyles() throws Exception
{
    Document doc = new Document();
    Document target = new Document("Your Directory Path" + "Rendering.docx");
    target.copyStylesFromTemplate(doc);
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.CopyStyles.docx");
}
```

Dieser Code kopiert Stile aus einem Vorlagendokument in das aktuelle Dokument.

## Themen verwalten

Designs sind für die Gestaltung Ihres Dokuments unerlässlich. Sie können Designeigenschaften wie im folgenden Code gezeigt abrufen und festlegen:

```java
@Test
public void getThemeProperties() throws Exception
{
    Document doc = new Document();
    Theme theme = doc.getTheme();
    System.out.println(theme.getMajorFonts().getLatin());
    System.out.println(theme.getMinorFonts().getEastAsian());
    System.out.println(theme.getColors().getAccent1());
}

@Test
public void setThemeProperties() throws Exception
{
    Document doc = new Document();
    Theme theme = doc.getTheme();
    theme.getMinorFonts().setLatin("Times New Roman");
    theme.getColors().setHyperlink(Color.ORANGE);
}
```

Diese Codeausschnitte zeigen, wie Designeigenschaften wie Schriftarten und Farben abgerufen und geändert werden.

## Einfügen von Stiltrennzeichen

Stiltrennzeichen sind nützlich, um innerhalb eines Absatzes unterschiedliche Stile anzuwenden. Hier ist ein Beispiel für das Einfügen von Stiltrennzeichen:

```java
@Test
public void insertStyleSeparator() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    Style paraStyle = builder.getDocument().getStyles().add(StyleType.PARAGRAPH, "MyParaStyle");
    paraStyle.getFont().setBold(false);
    paraStyle.getFont().setSize(8.0);
    paraStyle.getFont().setName("Arial");
    // Fügen Sie Text im Stil „Überschrift 1“ an.
    builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
    builder.write("Heading 1");
    builder.insertStyleSeparator();
    // Fügen Sie Text mit einem anderen Stil hinzu.
    builder.getParagraphFormat().setStyleName(paraStyle.getName());
    builder.write("This is text with some other formatting ");
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.InsertStyleSeparator.docx");
}
```

In diesem Code erstellen wir einen benutzerdefinierten Absatzstil und fügen einen Stiltrenner ein, um Stile innerhalb desselben Absatzes zu wechseln.

## Abschluss

Dieses Handbuch behandelt die Grundlagen der Arbeit mit Stilen und Designs in Aspose.Words für Java. Sie haben gelernt, wie Sie Stile abrufen und kopieren, Designs verwalten und Stiltrennzeichen einfügen, um optisch ansprechende und gut formatierte Dokumente zu erstellen. Experimentieren Sie mit diesen Techniken, um Ihre Dokumente Ihren Anforderungen entsprechend anzupassen.


## Häufig gestellte Fragen

### Wie kann ich Designeigenschaften in Aspose.Words für Java abrufen?

Sie können Designeigenschaften abrufen, indem Sie auf das Designobjekt und seine Eigenschaften zugreifen.

### Wie kann ich Designeigenschaften wie Schriftarten und Farben festlegen?

Sie können Designeigenschaften festlegen, indem Sie die Eigenschaften des Designobjekts ändern.

### Wie kann ich Stiltrennzeichen verwenden, um Stile innerhalb desselben Absatzes zu wechseln?

Sie können Stiltrennzeichen einfügen, indem Sie `insertStyleSeparator` Methode der `DocumentBuilder` Klasse.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}