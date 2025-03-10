---
title: Použití stylů a motivů v Aspose.Words pro Java
linktitle: Používání stylů a motivů
second_title: Aspose.Words Java Document Processing API
description: Naučte se, jak vylepšit formátování dokumentů pomocí Aspose.Words for Java. Prozkoumejte styly, motivy a další v této komplexní příručce s příklady zdrojového kódu.
weight: 20
url: /cs/java/document-manipulation/using-styles-and-themes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití stylů a motivů v Aspose.Words pro Java


## Úvod do používání stylů a motivů v Aspose.Words pro Javu

V této příručce prozkoumáme, jak pracovat se styly a motivy v Aspose.Words pro Java, abychom zlepšili formátování a vzhled vašich dokumentů. Budeme se zabývat tématy, jako je načítání stylů, kopírování stylů, správa motivů a vkládání oddělovačů stylů. Začněme!

## Načítání stylů

Chcete-li načíst styly z dokumentu, můžete použít následující fragment kódu Java:

```java
Document doc = new Document();
String styleName = "";
//Získejte kolekci stylů z dokumentu.
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

Tento kód načte styly definované v dokumentu a vytiskne jejich názvy.

## Kopírování stylů

 Chcete-li kopírovat styly z jednoho dokumentu do druhého, můžete použít`copyStylesFromTemplate` způsob, jak je uvedeno níže:

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

Tento kód zkopíruje styly z dokumentu šablony do aktuálního dokumentu.

## Správa motivů

Motivy jsou zásadní pro definování celkového vzhledu vašeho dokumentu. Vlastnosti motivu můžete načíst a nastavit, jak je ukázáno v následujícím kódu:

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

Tyto úryvky ukazují, jak načíst a upravit vlastnosti motivu, jako jsou písma a barvy.

## Vkládání oddělovačů stylů

Oddělovače stylů jsou užitečné pro použití různých stylů v rámci jednoho odstavce. Zde je příklad, jak vložit oddělovače stylů:

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
    // Přidejte text stylem „Nadpis 1“.
    builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
    builder.write("Heading 1");
    builder.insertStyleSeparator();
    // Připojit text jiným stylem.
    builder.getParagraphFormat().setStyleName(paraStyle.getName());
    builder.write("This is text with some other formatting ");
    doc.save("Your Directory Path" + "WorkingWithStylesAndThemes.InsertStyleSeparator.docx");
}
```

V tomto kódu vytvoříme vlastní styl odstavce a vložíme oddělovač stylu pro přepínání stylů v rámci stejného odstavce.

## Závěr

Tato příručka pokrývá základy práce se styly a motivy v Aspose.Words for Java. Naučili jste se, jak získávat a kopírovat styly, spravovat motivy a vkládat oddělovače stylů, abyste vytvořili vizuálně přitažlivé a dobře formátované dokumenty. Experimentujte s těmito technikami a upravte své dokumenty podle svých požadavků.


## FAQ

### Jak mohu získat vlastnosti motivu v Aspose.Words pro Java?

Vlastnosti motivu můžete získat přístupem k objektu motivu a jeho vlastnostem.

### Jak mohu nastavit vlastnosti motivu, jako jsou písma a barvy?

Vlastnosti motivu můžete nastavit úpravou vlastností objektu motivu.

### Jak mohu použít oddělovače stylů k přepínání stylů ve stejném odstavci?

 Oddělovače stylů můžete vložit pomocí`insertStyleSeparator` metoda`DocumentBuilder` třída.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
