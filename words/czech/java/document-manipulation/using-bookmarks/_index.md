---
date: 2026-01-11
description: Naučte se, jak zobrazovat a skrývat záložky a vytvářet záložky v Javě
  pomocí Aspose.Words pro Javu pro efektivní navigaci a manipulaci s dokumenty.
linktitle: Using Bookmarks
second_title: Aspose.Words Java Document Processing API
title: Zobrazit a skrýt záložky pomocí Aspose.Words pro Java
url: /cs/java/document-manipulation/using-bookmarks/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zobrazování a skrývání záložek s Aspose.Words pro Java

## Úvod do používání záložek v Aspose.Words pro Java

Záložky jsou výkonnou funkcí v Aspose.Words pro Java, která vám umožňuje **create bookmark java**, navigovat k určitému obsahu a dokonce **show hide bookmarks**, když potřebujete generovat různé verze dokumentu. V tomto průvodci krok za krokem projdeme vytváření, přístup, aktualizaci, kopírování a přepínání viditelnosti záložek, což vám poskytne plnou kontrolu nad manipulací s dokumentem.

## Rychlé odpovědi
- **Jaký je hlavní účel záložek?** Označit a později získat konkrétní části dokumentu.  
- **Mohu skrýt značky záložek ve finálním výstupu?** Ano — použijte API pro zobrazování/skrývání k přepínání jejich viditelnosti.  
- **Jak vytvořím záložku uvnitř buňky tabulky?** Začněte a ukončete záložku pomocí `DocumentBuilder`, zatímco kurzor je uvnitř buňky.  
- **Je možné zkopírovat text se záložkou do jiného dokumentu?** Rozhodně — použijte `NodeImporter` k zachování formátování.  
- **Jaká verze Aspose.Words je vyžadována?** Jakákoli nedávná verze; kód funguje s nejnovějším sestavením z roku 2026.

## Co je „show hide bookmarks“?

Funkce **show hide bookmarks** vám umožňuje programově zobrazit nebo skrýt oddělovače záložek v uloženém dokumentu. To je užitečné, když chcete generovat čistý výstup pro koncové uživatele a zároveň si zachovat data záložek pro interní zpracování.

## Proč používat záložky v automatizaci dokumentů v Javě?

- **Efficient navigation** – Přeskočte přímo na sekce bez prohledávání celého souboru.  
- **Dynamic content generation** – Vkládejte, nahrazujte nebo odstraňujte text spojený se záložkou.  
- **Conditional visibility** – Zobrazujte nebo skrývejte značky záložek podle preferencí uživatele nebo výstupního formátu.  
- **Reusability** – Kopírujte fragmenty se záložkami mezi dokumenty a zachovávejte styly.

## Požadavky
- Java Development Kit (JDK) 8 nebo vyšší.  
- Aspose.Words for Java knihovna přidaná do projektu (Maven/Gradle nebo JAR).  
- Základní znalost tříd `Document` a `DocumentBuilder`.

## Průvodce krok za krokem

### Krok 1: Vytvořit záložku (create bookmark java)

Pro přidání záložky ji zahájíte, zapíšete obsah a poté ji ukončíte. Tento příklad vytváří jednoduchou záložku s názvem **My Bookmark**.

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);

// Start the bookmark
builder.startBookmark("My Bookmark");
builder.writeln("Text inside a bookmark.");

// End the bookmark
builder.endBookmark("My Bookmark");
```

### Krok 2: Přístup k záložkám (access bookmarks java)

Záložky lze získat buď podle jejich nulového indexu, nebo podle názvu. Níže uvedený kód demonstruje oba přístupy.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");

// By index:
Bookmark bookmark1 = doc.getRange().getBookmarks().get(0);

// By name:
Bookmark bookmark2 = doc.getRange().getBookmarks().get("MyBookmark3");
```

### Krok 3: Aktualizovat data záložky (update bookmark text)

Můžete přejmenovat záložku nebo nahradit její textový obsah. To je užitečné, když se podkladový dokument mění.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark bookmark = doc.getRange().getBookmarks().get("MyBookmark1");
String name = bookmark.getName();
String text = bookmark.getText();
bookmark.setName("RenamedBookmark");
bookmark.setText("This is new bookmarked text.");
```

### Krok 4: Práce s textem se záložkou (copy bookmarked text)

Kopírování fragmentu se záložkou do jiného dokumentu při zachování původního formátování je jednoduché pomocí `NodeImporter`.

```java
Document srcDoc = new Document("Your Directory Path" + "Bookmarks.docx");
Bookmark srcBookmark = srcDoc.getRange().getBookmarks().get("MyBookmark1");
Document dstDoc = new Document();
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KEEP_SOURCE_FORMATTING);
appendBookmarkedText(importer, srcBookmark, dstDoc.getLastSection().getBody());
dstDoc.save("Your Directory Path" + "WorkingWithBookmarks.CopyBookmarkedText.docx");
```

### Krok 5: Zobrazit a skrýt záložky (show hide bookmarks)

Následující úryvek ukazuje, jak skrýt značky záložky v uloženém souboru. Předávejte `false` pro skrytí, `true` pro zobrazení.

```java
Document doc = new Document("Your Directory Path" + "Bookmarks.docx");
showHideBookmarkedContent(doc, "MyBookmark1", false);
doc.save("Your Directory Path" + "WorkingWithBookmarks.ShowHideBookmarks.docx");
```

### Krok 6: Rozplést záložky řádků (bookmark table cell)

Když záložky zasahují do řádků tabulky, mohou se zamotat. Níže uvedené pomocné metody je rozplétají a umožňují smazat konkrétní řádek podle jeho záložky.

```java
Document doc = new Document("Your Directory Path" + "Table column bookmarks.docx");
untangle(doc);
deleteRowByBookmark(doc, "ROW2");
doc.save("Your Directory Path" + "WorkingWithBookmarks.UntangleRowBookmarks.docx");
```

## Časté problémy a řešení

| Issue | Solution |
|-------|----------|
| **Záložka nenalezena** | Ověřte, že název záložky přesně odpovídá (rozlišuje velká a malá písmena) a že dokument byl po vytvoření uložen. |
| **Zkopírovaný text ztrácí formátování** | Použijte `ImportFormatMode.KEEP_SOURCE_FORMATTING` s `NodeImporter`, jak je ukázáno v kroku 4. |
| **Zobrazit/skrýt neovlivňuje výstup** | Ujistěte se, že voláte `showHideBookmarkedContent` **před** uložením dokumentu. |
| **Záložka uvnitř buňky tabulky je ignorována** | Umístěte volání start/end, když je kurzor builderu uvnitř cílové buňky. |

## Často kladené otázky

**Q: Jak vytvořím záložku v buňce tabulky?**  
A: Použijte `DocumentBuilder` k přesunu kurzoru do požadované buňky, poté zavolejte `startBookmark` a `endBookmark` kolem obsahu buňky.

**Q: Mohu zkopírovat záložku do jiného dokumentu?**  
A: Ano — použijte třídu `NodeImporter` (viz krok 4) k importu uzlu se záložkou při zachování původního formátování.

**Q: Jak mohu smazat řádek podle jeho záložky?**  
A: Nejprve najděte řádek, který obsahuje záložku, poté zavolejte `remove` na uzlu řádku (jak je ukázáno v kroku 6).

**Q: Jaké jsou některé běžné případy použití záložek?**  
A: Generování obsahu, extrakce konkrétních sekcí pro reportování a automatizace sestavování dokumentů na základě výběru uživatele.

**Q: Kde mohu najít více informací o Aspose.Words pro Java?**  
A: Pro podrobnou dokumentaci a ke stažení navštivte [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

**Poslední aktualizace:** 2026-01-11  
**Testováno s:** Aspose.Words for Java 24.11 (2026)  
**Autor:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}