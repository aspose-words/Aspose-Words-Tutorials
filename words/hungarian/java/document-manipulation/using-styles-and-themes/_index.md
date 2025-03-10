---
title: Stílusok és témák használata az Aspose.Words for Java programban
linktitle: Stílusok és témák használata
second_title: Aspose.Words Java Document Processing API
description: Ismerje meg, hogyan javíthatja a dokumentumok formázását az Aspose.Words for Java segítségével. Fedezze fel a stílusokat, témákat és egyebeket ebben a forráskód-példákat tartalmazó átfogó útmutatóban.
weight: 20
url: /hu/java/document-manipulation/using-styles-and-themes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Stílusok és témák használata az Aspose.Words for Java programban


## Bevezetés az Aspose.Words for Java stílusok és témák használatába

Ebben az útmutatóban megvizsgáljuk, hogyan dolgozhat stílusokkal és témákkal az Aspose.Words for Java programban, hogy javítsa a dokumentumok formázását és megjelenését. Olyan témákkal foglalkozunk, mint a stílusok lekérése, a stílusok másolása, a témák kezelése és a stíluselválasztók beszúrása. Kezdjük is!

## Stílusok lekérése

Stílusok lekéréséhez egy dokumentumból a következő Java kódrészletet használhatja:

```java
Document doc = new Document();
String styleName = "";
//Stílusgyűjtemény lekérése a dokumentumból.
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

Ez a kód lekéri a dokumentumban meghatározott stílusokat, és kiírja a nevüket.

## Stílusok másolása

 Stílusok egyik dokumentumból a másikba másolásához használhatja a`copyStylesFromTemplate` az alábbiak szerint:

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

Ez a kód stílusokat másol egy sablondokumentumból az aktuális dokumentumba.

## Témák kezelése

A témák elengedhetetlenek a dokumentum általános megjelenésének meghatározásához. A téma tulajdonságait a következő kódban bemutatott módon kérheti le és állíthatja be:

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

Ezek a részletek bemutatják, hogyan lehet lekérni és módosítani a téma tulajdonságait, például a betűtípusokat és a színeket.

## Stíluselválasztók beszúrása

A stíluselválasztók hasznosak különböző stílusok egyetlen bekezdésen belüli alkalmazásakor. Íme egy példa a stíluselválasztók beszúrására:

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
    // Szöveg hozzáfűzése „1. címsor” stílusban.
    builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
    builder.write("Heading 1");
    builder.insertStyleSeparator();
    // Szöveg hozzáfűzése más stílussal.
    builder.getParagraphFormat().setStyleName(paraStyle.getName());
    builder.write("This is text with some other formatting ");
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.InsertStyleSeparator.docx");
}
```

Ebben a kódban egyéni bekezdésstílust hozunk létre, és stíluselválasztót szúrunk be a stílusok váltásához ugyanazon a bekezdésen belül.

## Következtetés

Ez az útmutató az Aspose.Words for Java stílusaival és témáival való munka alapjait ismerteti. Megtanulta a stílusok lekérését és másolását, a témák kezelését, valamint a stíluselválasztók beszúrását, így tetszetős és jól formázott dokumentumokat hozhat létre. Kísérletezzen ezekkel a technikákkal, hogy igényei szerint testreszabhassa dokumentumait.


## GYIK

### Hogyan kérhetem le a téma tulajdonságait az Aspose.Words for Java programban?

A téma tulajdonságait a téma objektumhoz és tulajdonságaihoz való hozzáféréssel kérheti le.

### Hogyan állíthatom be a téma tulajdonságait, például a betűtípusokat és a színeket?

A téma tulajdonságait a témaobjektum tulajdonságainak módosításával állíthatja be.

### Hogyan használhatok stíluselválasztókat a stílusok váltásához ugyanazon a bekezdésen belül?

 Stíluselválasztókat szúrhat be a`insertStyleSeparator` módszere a`DocumentBuilder` osztály.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
