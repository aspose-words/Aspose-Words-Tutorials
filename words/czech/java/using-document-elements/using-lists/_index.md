---
title: Použití seznamů v Aspose.Words pro Javu
linktitle: Použití seznamů
second_title: Aspose.Words Java Document Processing API
description: Naučte se používat seznamy v Aspose.Words pro Java pomocí tohoto podrobného tutoriálu. Efektivně organizujte a formátujte své dokumenty.
weight: 18
url: /cs/java/using-document-elements/using-lists/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití seznamů v Aspose.Words pro Javu


tomto komplexním tutoriálu prozkoumáme, jak efektivně používat seznamy v Aspose.Words for Java, výkonném rozhraní API pro programovou práci s dokumenty Microsoft Word. Seznamy jsou nezbytné pro strukturování a uspořádání obsahu ve vašich dokumentech. Probereme dva klíčové aspekty práce se seznamy: restartování seznamů v každé sekci a určení úrovní seznamu. Pojďme se ponořit!

## Úvod do Aspose.Words for Java

Než začneme pracovat se seznamy, seznamme se s Aspose.Words pro Javu. Toto rozhraní API poskytuje vývojářům nástroje pro vytváření, úpravu a manipulaci s dokumenty aplikace Word v prostředí Java. Je to všestranné řešení pro úkoly od jednoduchého generování dokumentů až po složité formátování a správu obsahu.

### Nastavení vašeho prostředí

 Nejprve se ujistěte, že máte Aspose.Words for Java nainstalovaný a nastavený ve svém vývojovém prostředí. Můžete si jej stáhnout[zde](https://releases.aspose.com/words/java/). 

## Restartování seznamů v každé sekci

mnoha scénářích může být nutné restartovat seznamy v každé sekci dokumentu. To může být užitečné pro vytváření strukturovaných dokumentů s více sekcemi, jako jsou zprávy, manuály nebo akademické práce.

Zde je podrobný návod, jak toho dosáhnout pomocí Aspose.Words for Java:

### Inicializujte svůj dokument: 
Začněte vytvořením nového objektu dokumentu.

```java
Document doc = new Document();
```

### Přidat číslovaný seznam: 
Přidejte do dokumentu číslovaný seznam. Použijeme výchozí styl číslování.

```java
doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
```

### Konfigurace nastavení seznamu: 
\Povolte restartování seznamu v každé sekci.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Nastavení DocumentBuilderu: 
Vytvořte DocumentBuilder pro přidání obsahu do vašeho dokumentu.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Přidat položky seznamu: 
Použijte smyčku k přidání položek seznamu do dokumentu. Za 15. položku vložíme konec oddílu.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Uložte svůj dokument: 
Uložte dokument s požadovanými možnostmi.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Podle těchto kroků můžete vytvářet dokumenty se seznamy, které se v každé sekci restartují, a zachovávají tak jasnou a organizovanou strukturu obsahu.

## Určení úrovní seznamu

Aspose.Words for Java vám umožňuje určit úrovně seznamu, což je zvláště užitečné, když v dokumentu potřebujete různé formáty seznamu. Pojďme prozkoumat, jak to udělat:

### Inicializujte svůj dokument: 
Vytvořte nový objekt dokumentu.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

### Vytvořte číslovaný seznam: 
Použijte šablonu číslovaného seznamu z aplikace Microsoft Word.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
```

### Zadejte úrovně seznamu: 
Procházejte různé úrovně seznamu a přidávejte obsah.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Vytvořte seznam s odrážkami: 
Nyní vytvoříme seznam s odrážkami.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Zadejte úrovně seznamu s odrážkami: 
Podobně jako u číslovaného seznamu určete úrovně a přidejte obsah.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Formátování seznamu stop: 
Chcete-li zastavit formátování seznamu, nastavte seznam na hodnotu null.

```java
builder.getListFormat().setList(null);
```

### Uložte svůj dokument: 
Uložte dokument.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Podle těchto kroků můžete vytvořit dokumenty s vlastními úrovněmi seznamu, což vám umožní řídit formátování seznamů ve vašich dokumentech.

## Kompletní zdrojový kód
```java
	string outPath = "Your Output Directory";
 public void restartListAtEachSection() throws Exception
    {
        Document doc = new Document();
        doc.getLists().add(ListTemplate.NUMBER_DEFAULT);
        List list = doc.getLists().get(0);
        list.isRestartAtEachSection(true);
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.getListFormat().setList(list);
        for (int i = 1; i < 45; i++)
        {
            builder.writeln(MessageFormat.format("List Item {0}", i));
            if (i == 15)
                builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
        }
        // IsRestartAtEachSection bude zapsán pouze v případě, že je soulad vyšší než OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Vytvořte číslovaný seznam založený na jedné ze šablon seznamu Microsoft Word
        // použijte jej na aktuální odstavec tvůrce dokumentů.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // V tomto seznamu je devět úrovní, pojďme si je všechny vyzkoušet.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Vytvořte seznam s odrážkami založený na jedné ze šablon seznamu Microsoft Word
        // použijte jej na aktuální odstavec tvůrce dokumentů.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Toto je způsob, jak zastavit formátování seznamu.
        builder.getListFormat().setList(null);
        builder.getDocument().save(outPath + "WorkingWithList.SpecifyListLevel.docx");
    }
    @Test
    public void restartListNumber() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Vytvořte seznam na základě šablony.
        List list1 = doc.getLists().add(ListTemplate.NUMBER_ARABIC_PARENTHESIS);
        list1.getListLevels().get(0).getFont().setColor(Color.RED);
        list1.getListLevels().get(0).setAlignment(ListLevelAlignment.RIGHT);
        builder.writeln("List 1 starts below:");
        builder.getListFormat().setList(list1);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        // Chcete-li znovu použít první seznam, musíme restartovat číslování vytvořením kopie původního formátování seznamu.
        List list2 = doc.getLists().addCopy(list1);
        // Novou soupisku můžeme jakkoli upravit, včetně nastavení nového startovního čísla.
        list2.getListLevels().get(0).setStartAt(10);
        builder.writeln("List 2 starts below:");
        builder.getListFormat().setList(list2);
        builder.writeln("Item 1");
        builder.writeln("Item 2");
        builder.getListFormat().removeNumbers();
        builder.getDocument().save(outPath + "WorkingWithList.RestartListNumber.docx");
	}
```

## Závěr

Gratuluji! Naučili jste se efektivně pracovat se seznamy v Aspose.Words for Java. Seznamy jsou zásadní pro uspořádání a prezentaci obsahu ve vašich dokumentech. Ať už potřebujete restartovat seznamy v každé sekci nebo zadat úrovně seznamu, Aspose.Words for Java poskytuje nástroje, které potřebujete k vytváření profesionálně vypadajících dokumentů.

Nyní můžete s jistotou používat tyto funkce k vylepšení úloh generování a formátování dokumentů. Pokud máte nějaké dotazy nebo potřebujete další pomoc, neváhejte se obrátit na[Aspose komunitní fórum](https://forum.aspose.com/) za podporu.

## Nejčastější dotazy

### Jak nainstaluji Aspose.Words for Java?
 Aspose.Words for Java si můžete stáhnout z[zde](https://releases.aspose.com/words/java/) a postupujte podle pokynů k instalaci v dokumentaci.

### Mohu přizpůsobit formát číslování seznamů?
Ano, Aspose.Words for Java poskytuje rozsáhlé možnosti přizpůsobení formátů číslování seznamů. Podrobnosti najdete v dokumentaci API.

### Je Aspose.Words for Java kompatibilní s nejnovějšími standardy dokumentů Word?
Ano, Aspose.Words pro Java můžete nakonfigurovat tak, aby vyhovovala různým standardům dokumentů aplikace Word, včetně ISO 29500.

### Mohu pomocí Aspose.Words for Java generovat složité dokumenty s tabulkami a obrázky?
Absolutně! Aspose.Words for Java podporuje pokročilé formátování dokumentů, včetně tabulek, obrázků a dalších. Příklady naleznete v dokumentaci.

### Kde mohu získat dočasnou licenci pro Aspose.Words for Java?
Můžete získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
