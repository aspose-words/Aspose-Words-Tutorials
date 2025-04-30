---
"description": "Naučte se, jak ukládat dokumenty jako textové soubory v Aspose.Words pro Javu. Postupujte podle našeho podrobného návodu s příklady kódu Java."
"linktitle": "Ukládání dokumentů jako textových souborů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Ukládání dokumentů jako textových souborů v Aspose.Words pro Javu"
"url": "/cs/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ukládání dokumentů jako textových souborů v Aspose.Words pro Javu


## Úvod do ukládání dokumentů jako textových souborů v Aspose.Words pro Javu

tomto tutoriálu se podíváme na to, jak ukládat dokumenty jako textové soubory pomocí knihovny Aspose.Words pro Javu. Aspose.Words je výkonné Java API pro práci s dokumenty Wordu, které nabízí různé možnosti pro ukládání dokumentů v různých formátech, včetně prostého textu. Probereme kroky, jak toho dosáhnout, a zároveň uvedeme ukázkový kód v Javě.

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

- Na vašem systému nainstalovaná sada pro vývoj Java (JDK).
- Knihovna Aspose.Words pro Javu integrovaná do vašeho projektu. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).
- Základní znalost programování v Javě.

## Krok 1: Vytvořte dokument

Abychom dokument uložili jako textový soubor, musíme nejprve vytvořit dokument pomocí Aspose.Words. Zde je jednoduchý úryvek kódu Java pro vytvoření dokumentu s nějakým obsahem:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

V tomto kódu vytvoříme nový dokument a přidáme do něj text, včetně textu v různých jazycích.

## Krok 2: Definování možností ukládání textu

Dále musíme definovat možnosti ukládání textu, které určují, jak má být dokument uložen jako textový soubor. Můžeme nakonfigurovat různá nastavení, jako je přidání oboustranných značek, odsazení seznamu a další. Podívejme se na dva příklady:

### Příklad 1: Přidání oboustranných značek

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

V tomto příkladu vytvoříme `TxtSaveOptions` objekt a nastavit `AddBidiMarks` majetek `true` zahrnout bidi značky do textového výstupu.

### Příklad 2: Použití znaku tabulátoru pro odsazení seznamu

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Zde nakonfigurujeme možnosti ukládání tak, aby pro odsazení seznamu s počtem 1 používaly znak tabulátoru.

## Krok 3: Uložte dokument jako text

Nyní, když jsme definovali možnosti ukládání textu, můžeme dokument uložit jako textový soubor. Následující kód ukazuje, jak to provést:

```java
doc.save("output.txt", saveOptions);
```

Nahradit `"output.txt"` s požadovanou cestou k souboru, kam chcete textový soubor uložit.

## Kompletní zdrojový kód pro ukládání dokumentů jako textových souborů v Aspose.Words pro Javu

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

V tomto tutoriálu jsme se naučili, jak ukládat dokumenty jako textové soubory v Aspose.Words pro Javu. Probrali jsme kroky pro vytvoření dokumentu, definování možností ukládání textu a uložení dokumentu v textovém formátu. Aspose.Words nabízí rozsáhlou flexibilitu, pokud jde o ukládání dokumentů, což vám umožňuje přizpůsobit výstup vašim specifickým požadavkům.

## Často kladené otázky

### Jak přidám bidi značky do textového výstupu?

Chcete-li do textového výstupu přidat bidi značky, nastavte `AddBidiMarks` majetek `TxtSaveOptions` na `true`Například:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Mohu si přizpůsobit znak odsazení seznamu?

Ano, znak odsazení seznamu si můžete přizpůsobit konfigurací `ListIndentation` majetek `TxtSaveOptions`Například chcete-li použít znak tabulátoru pro odsazení seznamu, můžete provést následující:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Je Aspose.Words pro Javu vhodný pro práci s vícejazyčným textem?

Ano, Aspose.Words pro Javu je vhodný pro práci s vícejazyčným textem. Podporuje různé jazyky a kódování znaků, což z něj činí všestrannou volbu pro práci s dokumenty v různých jazycích.

### Jak mohu získat přístup k další dokumentaci a zdrojům pro Aspose.Words pro Javu?

Komplexní dokumentaci a zdroje pro Aspose.Words pro Javu naleznete na webových stránkách s dokumentací k Aspose: [Dokumentace k Aspose.Words pro Javu](https://reference.aspose.com/words/java/).

### Kde si mohu stáhnout Aspose.Words pro Javu?

Knihovnu Aspose.Words pro Javu si můžete stáhnout z webových stránek Aspose: [Stáhněte si Aspose.Words pro Javu](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}