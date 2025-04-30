---
"description": "Ismerd meg, hogyan javíthatod a dokumentumok formázását az Aspose.Words for Java segítségével. Fedezz fel stílusokat, témákat és sok mást ebben az átfogó útmutatóban forráskódpéldákkal."
"linktitle": "Stílusok és témák használata"
"second_title": "Aspose.Words Java dokumentumfeldolgozó API"
"title": "Stílusok és témák használata az Aspose.Words for Java-ban"
"url": "/hu/java/document-manipulation/using-styles-and-themes/"
"weight": 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Stílusok és témák használata az Aspose.Words for Java-ban


## Bevezetés a stílusok és témák használatába az Aspose.Words for Java-ban

Ebben az útmutatóban azt vizsgáljuk meg, hogyan használhatunk stílusokat és témákat az Aspose.Words for Java programban a dokumentumok formázásának és megjelenésének javítása érdekében. Olyan témákat fogunk áttekinteni, mint a stílusok lekérése, stílusok másolása, témák kezelése és stíluselválasztók beszúrása. Kezdjük is!

## Stílusok visszakeresése

Stílusok dokumentumból való lekéréséhez a következő Java kódrészletet használhatja:

```java
Document doc = new Document();
String styleName = "";
// Stílusgyűjtemény lekérése a dokumentumból.
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

Ez a kód beolvassa a dokumentumban definiált stílusokat, és kinyomtatja a nevüket.

## Stílusok másolása

Stílusok másolásához egyik dokumentumból a másikba használhatja a `copyStylesFromTemplate` az alább látható módszer:

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

Ezek a kódrészletek bemutatják, hogyan lehet lekérni és módosítani a téma tulajdonságait, például a betűtípusokat és a színeket.

## Stíluselválasztók beszúrása

A stíluselválasztók hasznosak különböző stílusok egyetlen bekezdésen belüli alkalmazásához. Íme egy példa a stíluselválasztók beszúrására:

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
    // Szöveg hozzáfűzése „Címsor 1” stílusban.
    builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
    builder.write("Heading 1");
    builder.insertStyleSeparator();
    // Szöveg hozzáfűzése másik stílussal.
    builder.getParagraphFormat().setStyleName(paraStyle.getName());
    builder.write("This is text with some other formatting ");
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.InsertStyleSeparator.docx");
}
```

Ebben a kódban létrehozunk egy egyéni bekezdésstílust, és beszúrunk egy stíluselválasztót a stílusok közötti váltáshoz ugyanazon a bekezdésen belül.

## Következtetés

Ez az útmutató az Aspose.Words for Java stílusokkal és témákkal való munka alapjait ismertette. Megtanultad, hogyan kérhetsz le és másolhatsz stílusokat, hogyan kezelhetsz témákat, és hogyan szúrhatsz be stíluselválasztókat vizuálisan vonzó és jól formázott dokumentumok létrehozásához. Kísérletezz ezekkel a technikákkal, hogy a dokumentumaidat az igényeidnek megfelelően testre szabd.


## GYIK

### Hogyan tudom lekérni a téma tulajdonságait az Aspose.Words for Java fájlban?

A téma tulajdonságait a téma objektum és annak tulajdonságainak elérésével kérheti le.

### Hogyan tudom beállítani a téma tulajdonságait, például a betűtípusokat és a színeket?

A téma tulajdonságait a témaobjektum tulajdonságainak módosításával állíthatja be.

### Hogyan használhatok stíluselválasztókat stílusváltásra ugyanazon a bekezdésen belül?

Stíluselválasztókat a következővel szúrhat be: `insertStyleSeparator` a módszer `DocumentBuilder` osztály.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}