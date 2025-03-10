---
title: Ukládání dokumentů jako textových souborů v Aspose.Words pro Java
linktitle: Ukládání dokumentů jako textových souborů
second_title: Aspose.Words Java Document Processing API
description: Naučte se ukládat dokumenty jako textové soubory v Aspose.Words for Java. Postupujte podle našeho podrobného průvodce s příklady kódu Java.
weight: 24
url: /cs/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů jako textových souborů v Aspose.Words pro Java


## Úvod do ukládání dokumentů jako textových souborů v Aspose.Words pro Java

V tomto tutoriálu prozkoumáme, jak ukládat dokumenty jako textové soubory pomocí knihovny Aspose.Words for Java. Aspose.Words je výkonné Java API pro práci s dokumenty Wordu a poskytuje různé možnosti pro ukládání dokumentů v různých formátech, včetně prostého textu. Probereme kroky, jak toho dosáhnout, a poskytneme vzorový kód Java.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

- Java Development Kit (JDK) nainstalovaný ve vašem systému.
-  Knihovna Aspose.Words for Java integrovaná do vašeho projektu. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).
- Základní znalost programování v Javě.

## Krok 1: Vytvořte dokument

Chcete-li uložit dokument jako textový soubor, musíme nejprve vytvořit dokument pomocí Aspose.Words. Zde je jednoduchý fragment kódu Java pro vytvoření dokumentu s určitým obsahem:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

tomto kódu vytvoříme nový dokument a přidáme do něj nějaký text, včetně textu v různých jazycích.

## Krok 2: Definujte možnosti ukládání textu

Dále musíme definovat možnosti ukládání textu, které určují, jak má být dokument uložen jako textový soubor. Můžeme nakonfigurovat různá nastavení, jako je přidání značek bidi, odsazení seznamu a další. Podívejme se na dva příklady:

### Příklad 1: Přidání značek Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 V tomto příkladu vytvoříme a`TxtSaveOptions` objekt a nastavte`AddBidiMarks`majetek do`true` zahrnout do textového výstupu značky bidi.

### Příklad 2: Použití znaku tabulátoru pro odsazení seznamu

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Zde nakonfigurujeme možnosti uložení tak, aby se pro odsazení seznamu používal znak tabulátoru s počtem 1.

## Krok 3: Uložte dokument jako text

Nyní, když jsme definovali možnosti uložení textu, můžeme dokument uložit jako textový soubor. Následující kód ukazuje, jak to udělat:

```java
doc.save("output.txt", saveOptions);
```

 Nahradit`"output.txt"` s požadovanou cestou k souboru, kam chcete textový soubor uložit.

## Kompletní zdrojový kód pro ukládání dokumentů jako textových souborů v Aspose.Words pro Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Vytvořte seznam se třemi úrovněmi odsazení.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Vytvořte seznam se třemi úrovněmi odsazení.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Závěr

V tomto tutoriálu jsme se naučili ukládat dokumenty jako textové soubory v Aspose.Words for Java. Probrali jsme kroky k vytvoření dokumentu, definování možností uložení textu a uložení dokumentu v textovém formátu. Aspose.Words poskytuje rozsáhlou flexibilitu, pokud jde o ukládání dokumentů, což vám umožňuje přizpůsobit výstup vašim konkrétním požadavkům.

## FAQ

### Jak přidám značky bidi do textového výstupu?

 Chcete-li do textového výstupu přidat značky bidi, nastavte`AddBidiMarks` vlastnictví`TxtSaveOptions` na`true`. Například:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Mohu přizpůsobit znak odsazení seznamu?

 Ano, znak odsazení seznamu můžete přizpůsobit konfigurací`ListIndentation` vlastnictví`TxtSaveOptions`. Chcete-li například použít znak tabulátoru pro odsazení seznamu, můžete provést následující:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Je Aspose.Words for Java vhodný pro práci s vícejazyčným textem?

Ano, Aspose.Words for Java je vhodný pro práci s vícejazyčným textem. Podporuje různé jazyky a kódování znaků, což z něj činí všestrannou volbu pro práci s dokumenty v různých jazycích.

### Jak mohu získat přístup k další dokumentaci a zdrojům pro Aspose.Words for Java?

 Kompletní dokumentaci a zdroje pro Aspose.Words pro Java můžete najít na webu dokumentace Aspose:[Aspose.Words pro dokumentaci Java](https://reference.aspose.com/words/java/).

### Kde si mohu stáhnout Aspose.Words for Java?

 Knihovnu Aspose.Words for Java si můžete stáhnout z webu Aspose:[Stáhněte si Aspose.Words pro Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
