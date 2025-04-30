---
"description": "Naučte se používat seznamy v Aspose.Words pro Javu s tímto podrobným návodem. Efektivně si uspořádejte a formátujte své dokumenty."
"linktitle": "Používání seznamů"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání seznamů v Aspose.Words pro Javu"
"url": "/cs/java/using-document-elements/using-lists/"
"weight": 18
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání seznamů v Aspose.Words pro Javu


tomto komplexním tutoriálu se podíváme na to, jak efektivně používat seznamy v Aspose.Words pro Javu, což je výkonné API pro programovou práci s dokumenty Microsoft Word. Seznamy jsou nezbytné pro strukturování a organizaci obsahu v dokumentech. Probereme dva klíčové aspekty práce se seznamy: restartování seznamů v každé sekci a určení úrovní seznamů. Pojďme se na to pustit!

## Úvod do Aspose.Words pro Javu

Než začneme pracovat se seznamy, seznámme se s Aspose.Words pro Javu. Toto API poskytuje vývojářům nástroje pro vytváření, úpravy a manipulaci s dokumenty Wordu v prostředí Java. Je to všestranné řešení pro úkoly od jednoduchého generování dokumentů až po složité formátování a správu obsahu.

### Nastavení prostředí

Nejprve se ujistěte, že máte ve svém vývojovém prostředí nainstalovaný a nastavený Aspose.Words pro Javu. Můžete si ho stáhnout. [zde](https://releases.aspose.com/words/java/). 

## Restartování seznamů v každé sekci

mnoha scénářích může být nutné seznamy znovu spustit v každé části dokumentu. To může být užitečné pro vytváření strukturovaných dokumentů s více částmi, jako jsou zprávy, manuály nebo akademické práce.

Zde je podrobný návod, jak toho dosáhnout pomocí Aspose.Words pro Javu:

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
\Povolí restartování seznamu v každé sekci.

```java
List list = doc.getLists().get(0);
list.isRestartAtEachSection(true);
```

### Nastavení DocumentBuilderu: 
Vytvořte DocumentBuilder pro přidání obsahu do dokumentu.

```java
DocumentBuilder builder = new DocumentBuilder(doc);
builder.getListFormat().setList(list);
```

### Přidat položky seznamu: 
Pro přidání položek seznamu do dokumentu použijte smyčku. Za 15. položku vložíme zalomení oddílu.

```java
for (int i = 1; i < 45; i++) {
    builder.writeln(MessageFormat.format("List Item {0}", i));
    if (i == 15)
        builder.insertBreak(BreakType.SECTION_BREAK_NEW_PAGE);
}
```

### Uložte si dokument: 
Uložte dokument s požadovanými možnostmi.

```java
OoxmlSaveOptions options = new OoxmlSaveOptions();
options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL);
doc.save(outPath + "RestartListAtEachSection.docx", options);
```

Pomocí těchto kroků můžete vytvářet dokumenty se seznamy, které začínají v každé sekci, a zároveň zachovávají jasnou a organizovanou strukturu obsahu.

## Určení úrovní seznamu

Aspose.Words pro Javu umožňuje specifikovat úrovně seznamů, což je obzvláště užitečné, když v dokumentu potřebujete různé formáty seznamů. Pojďme se podívat, jak to udělat:

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
Procházejte různými úrovněmi seznamu a přidávejte obsah.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Vytvořte seznam s odrážkami: 
Nyní si vytvořme seznam s odrážkami.

```java
builder.getListFormat().setList(doc.getLists().add(ListTemplate.BULLET_DIAMONDS));
```

### Zadejte úrovně odrážkového seznamu: 
Podobně jako u číslovaného seznamu určete úrovně a přidejte obsah.

```java
for (int i = 0; i < 9; i++) {
    builder.getListFormat().setListLevelNumber(i);
    builder.writeln("Level " + i);
}
```

### Formátování seznamu zastavení: 
Chcete-li zastavit formátování seznamu, nastavte seznam na hodnotu null.

```java
builder.getListFormat().setList(null);
```

### Uložte si dokument: 
Uložte dokument.

```java
builder.getDocument().save(outPath + "SpecifyListLevel.docx");
```

Pomocí těchto kroků můžete vytvářet dokumenty s vlastními úrovněmi seznamů, což vám umožní ovládat formátování seznamů v dokumentech.

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
        // Hodnota IsRestartAtEachSection bude zapsána pouze v případě, že je shoda vyšší než OoxmlComplianceCore.Ecma376.
        OoxmlSaveOptions options = new OoxmlSaveOptions(); { options.setCompliance(OoxmlCompliance.ISO_29500_2008_TRANSITIONAL); }
        doc.save(outPath + "WorkingWithList.RestartListAtEachSection.docx", options);
    }
    @Test
    public void specifyListLevel() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Vytvořte číslovaný seznam na základě jedné ze šablon seznamů aplikace Microsoft Word
        // a aplikovat jej na aktuální odstavec nástroje pro tvorbu dokumentů.
        builder.getListFormat().setList(doc.getLists().add(ListTemplate.NUMBER_ARABIC_DOT));
        // V tomto seznamu je devět úrovní, pojďme si je všechny vyzkoušet.
        for (int i = 0; i < 9; i++)
        {
            builder.getListFormat().setListLevelNumber(i);
            builder.writeln("Level " + i);
        }
        // Vytvořte seznam s odrážkami na základě jedné ze šablon seznamů aplikace Microsoft Word
        // a aplikovat jej na aktuální odstavec nástroje pro tvorbu dokumentů.
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
        // Abychom mohli znovu použít první seznam, musíme číslování restartovat vytvořením kopie původního formátování seznamu.
        List list2 = doc.getLists().addCopy(list1);
        // Nový seznam můžeme libovolně upravovat, včetně nastavení nového startovního čísla.
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

Gratulujeme! Naučili jste se efektivně pracovat se seznamy v Aspose.Words pro Javu. Seznamy jsou klíčové pro organizaci a prezentaci obsahu v dokumentech. Ať už potřebujete seznamy restartovat v každé sekci nebo specifikovat úrovně seznamů, Aspose.Words pro Javu poskytuje nástroje, které potřebujete k vytváření profesionálně vypadajících dokumentů.

Nyní můžete tyto funkce s jistotou používat k vylepšení generování a formátování dokumentů. Pokud máte jakékoli dotazy nebo potřebujete další pomoc, neváhejte se obrátit na [Fórum komunity Aspose](https://forum.aspose.com/) pro podporu.

## Často kladené otázky

### Jak nainstaluji Aspose.Words pro Javu?
Aspose.Words pro Javu si můžete stáhnout z [zde](https://releases.aspose.com/words/java/) a postupujte podle pokynů k instalaci v dokumentaci.

### Mohu si přizpůsobit formát číslování seznamů?
Ano, Aspose.Words pro Javu nabízí rozsáhlé možnosti pro přizpůsobení formátů číslování seznamů. Podrobnosti naleznete v dokumentaci k API.

### Je Aspose.Words pro Javu kompatibilní s nejnovějšími standardy pro dokumenty Wordu?
Ano, Aspose.Words pro Javu můžete nakonfigurovat tak, aby splňoval různé standardy pro dokumenty Wordu, včetně normy ISO 29500.

### Mohu generovat složité dokumenty s tabulkami a obrázky pomocí Aspose.Words pro Javu?
Rozhodně! Aspose.Words pro Javu podporuje pokročilé formátování dokumentů, včetně tabulek, obrázků a dalších prvků. Příklady naleznete v dokumentaci.

### Kde mohu získat dočasnou licenci pro Aspose.Words pro Javu?
Můžete získat dočasnou licenci [zde](https://purchase.aspose.com/temporary-license/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}