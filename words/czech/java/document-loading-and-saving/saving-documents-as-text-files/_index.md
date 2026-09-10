---
date: 2025-12-24
description: Naučte se, jak vytvořit soubor prostého textu z dokumentů Word pomocí
  Aspose.Words pro Java. Tento průvodce ukazuje, jak převést Word do txt, použít odsazení
  tabulátorem a uložit Word jako txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Jak vytvořit soubor prostého textu pomocí Aspose.Words pro Javu
url: /cs/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Jak vytvořit soubor prostého textu pomocí Aspose.Words pro Java

## Úvod do ukládání dokumentů jako textových souborů v Aspose.Words pro Java

V tomto tutoriálu se naučíte **jak vytvořit soubor prostého textu** z dokumentu Word pomocí knihovny Aspose.Words pro Java. Ať už potřebujete **převést word do txt**, automatizovat generování reportů nebo jen extrahovat surový text pro další zpracování, tento průvodce vás provede celým pracovním postupem – od vytvoření dokumentu až po jemné nastavení možností ukládání, jako je **použití odsazení tabulátorem** nebo přidání bidi značek. Pojďme na to!

## Rychlé odpovědi
- **Jaká je hlavní třída pro vytvoření dokumentu?** `Document` z Aspose.Words.
- **Která možnost přidává bidi značky pro jazyky psané zprava doleva?** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Jak mohu odsazovat položky seznamu pomocí tabulátorů?** Nastavte `ListIndentation.Character` na `'\t'`.
- **Potřebuji licenci pro vývoj?** Pro testování stačí bezplatná zkušební verze; licence je vyžadována pro produkční nasazení.
- **Mohu soubor uložit pod vlastním názvem a cestou?** Ano – předáte úplnou cestu metodě `doc.save()`.

## Předpoklady

Než začneme, ujistěte se, že máte následující předpoklady:

- Nainstalovaný Java Development Kit (JDK) na vašem systému.  
- Knihovna Aspose.Words pro Java integrována ve vašem projektu. Můžete si ji stáhnout [zde](https://releases.aspose.com/words/java/).  
- Základní znalosti programování v Javě.

## Krok 1: Vytvoření dokumentu

Pro **uložení wordu jako txt** nejprve potřebujeme instanci `Document`. Níže je jednoduchý Java úryvek, který vytvoří dokument a zapíše několik řádků vícejazyčného textu:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

V tomto kódu vytváříme nový dokument, přidáváme anglický, hebrejský a arabský text a povolujeme formátování zprava doleva pro hebrejský odstavec.

## Krok 2: Definování možností uložení textu

Dále nakonfigurujeme, jak bude dokument uložen jako prostý textový soubor. Aspose.Words poskytuje třídu `TxtSaveOptions`, která vám umožní řídit vše od bidi značek po odsazení seznamů.

### Příklad 1: Přidání bidi značek (jak uložit txt s podporou RTL)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Nastavením `AddBidiMarks` na `true` zajistíte, že znaky zprava doleva budou ve výsledném **prostém textovém souboru** správně reprezentovány.

### Příklad 2: Použití tabulátoru pro odsazení seznamu (použít odsazení tabulátorem)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Zde říkáme Aspose.Words, aby před každou úroveň seznamu přidal znak tabulátoru (`'\t'`), což usnadní čitelnost výstupního textu.

## Krok 3: Uložení dokumentu jako text

Nyní, když jsou možnosti uložení připravené, můžete dokument uložit jako **prostý textový soubor**:

```java
doc.save("output.txt", saveOptions);
```

Nahraďte `"output.txt"` úplnou cestou, kam chcete soubor uložit.

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
        // Create a list with three levels of indentation.
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
        // Create a list with three levels of indentation.
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

## Časté problémy a řešení

| Problém | Řešení |
|-------|----------|
| **Bidi znaky se zobrazují jako nesrozumitelný text** | Ujistěte se, že je povoleno `setAddBidiMarks(true)` a výstupní soubor je otevřen s kódováním UTF‑8. |
| **Odsazení seznamu vypadá špatně** | Zkontrolujte, že `ListIndentation.Count` a `Character` jsou nastaveny na požadované hodnoty (tabulátor `'\t'` nebo mezera `' '` ). |
| **Soubor nebyl vytvořen** | Ověřte, že cílová složka existuje a aplikace má oprávnění k zápisu. |

## Často kladené otázky

### Jak přidám bidi značky do výstupního textu?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Můžu si přizpůsobit znak pro odsazení seznamu?

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Je Aspose.Words pro Java vhodný pro práci s vícejazyčným textem?

Ano, Aspose.Words pro Java podporuje širokou škálu jazyků a znakových kódování, což jej činí ideálním pro extrakci a ukládání vícejazyčného obsahu jako prostého textu.

### Jak mohu získat více dokumentace a zdrojů pro Aspose.Words pro Java?

Komplexní dokumentaci a zdroje najdete na stránce Aspose.Words pro Java Documentation: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Kde si mohu stáhnout Aspose.Words pro Java?

Knihovnu si můžete stáhnout z oficiálního webu: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Co když potřebuji **převést word do txt** v dávkovém procesu?

Zabalte výše uvedený kód do smyčky, která načte každý soubor `.docx`, použije stejné `TxtSaveOptions` a uloží jej jako `.txt`. Nezapomeňte po každé iteraci uvolnit objekty `Document`.

### Podporuje API ukládání přímo do proudu místo do souboru?

Ano, můžete předat `OutputStream` metodě `doc.save(outputStream, saveOptions)` pro zpracování v paměti nebo při integraci s webovými službami.

---

**Poslední aktualizace:** 2025-12-24  
**Testováno s:** Aspose.Words pro Java 24.12 (nejnovější)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}