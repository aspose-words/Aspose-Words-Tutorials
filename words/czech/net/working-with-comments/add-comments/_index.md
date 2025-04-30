---
"description": "Naučte se, jak přidávat komentáře do dokumentů Word pomocí Aspose.Words pro .NET s naším průvodcem. Vylepšete proces spolupráce na dokumentech bez námahy."
"linktitle": "Přidat komentáře"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Přidat komentáře"
"url": "/cs/net/working-with-comments/add-comments/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Přidat komentáře

## Zavedení

Vítejte v našem podrobném návodu, jak přidávat komentáře do dokumentů Word pomocí Aspose.Words pro .NET! Pokud chcete zefektivnit proces kontroly dokumentů programově začleňovat komentáře, jste na správném místě. Tento návod vás provede vším, co potřebujete vědět, od nastavení prostředí až po psaní a ukládání komentářů v dokumentech Word. Pojďme se do toho pustit a ulehčit spolupráci na dokumentech hračkou!

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Aspose.Words pro .NET: Musíte mít nainstalovaný Aspose.Words pro .NET. Můžete si ho stáhnout z [zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalovaný .NET Framework.
3. Vývojové prostředí: IDE podobné Visual Studiu pro psaní a spouštění kódu.
4. Základní znalost jazyka C#: Znalost programovacího jazyka C# vám pomůže sledovat příklady.

## Importovat jmenné prostory

Nejprve je třeba do projektu importovat potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám potřebným pro práci s Aspose.Words.

```csharp
using System;
using Aspose.Words;
```

Nyní si celý proces rozdělme na snadno sledovatelné kroky. Každý krok bude obsahovat podrobné vysvětlení, které vám pomůže pochopit logiku a funkčnost.

## Krok 1: Nastavení adresáře dokumentů

Nejprve musíme definovat adresář, kam bude váš dokument uložen. Použijeme zástupný symbol `YOUR DOCUMENT DIRECTORY` kterou byste měli nahradit skutečnou cestou k adresáři.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Inicializace dokumentu

Dále inicializujeme nový dokument a objekt DocumentBuilder. DocumentBuilder nám pomůže dokument sestavit a upravit.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Přidání textu do dokumentu

Do dokumentu přidáme text pomocí nástroje DocumentBuilder. Tento text bude místem, kam vložíme náš komentář.

```csharp
builder.Write("Some text is added.");
```

## Krok 4: Vytvořte a přidejte komentář

Nyní je čas vytvořit komentář. Inicializujeme nový objekt Comment, který určí dokument, jméno autora, iniciály a datum.

```csharp
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
```

## Krok 5: Přidání obsahu do komentáře

Nakonec do komentáře přidáme obsah. Vytvoříme nový odstavec a třídu Run pro uložení textu komentáře a poté je do komentáře přidáme.

```csharp
comment.SetText("Comment text.");
```

## Krok 6: Připojení komentáře k odstavci

Komentář musíme připojit k aktuálnímu odstavci, kam jsme text přidali. To se provede připojením komentáře k odstavci.

```csharp
builder.CurrentParagraph.AppendChild(comment);
```

## Krok 7: Uložte dokument

Posledním krokem je uložení dokumentu s komentáři. Určíme adresář a název souboru.

```csharp
doc.Save(dataDir + "WorkingWithComments.AddComments.docx");
```

## Závěr

máte to! Úspěšně jste přidali komentáře do dokumentu Word pomocí Aspose.Words pro .NET. Tato výkonná funkce může výrazně vylepšit proces kontroly dokumentů, usnadnit spolupráci a sdělování zpětné vazby. Nezapomeňte prozkoumat další možnosti Aspose.Words, které vám ještě více zefektivní správu dokumentů.

## Často kladené otázky

### Co je Aspose.Words pro .NET?

Aspose.Words pro .NET je výkonné API, které umožňuje vývojářům programově vytvářet, manipulovat a převádět dokumenty Wordu pomocí jazyků .NET.

### Mohu do jednoho dokumentu přidat více komentářů?

Ano, do jednoho dokumentu můžete přidat více komentářů opakováním procesu vytváření a přidávání komentářů k různým odstavcům nebo textovým úsekům.

### Jak si mohu přizpůsobit vzhled komentářů?

Zatímco Aspose.Words se zaměřuje na obsah a strukturu komentářů, vzhled lze přizpůsobit pomocí vestavěných funkcí formátování ve Wordu.

### Je možné programově odstranit komentáře?

Ano, komentáře můžete programově odstranit iterací komentářů v dokumentu a jejich odstraňováním podle potřeby.

### Mohu přidávat odpovědi do komentářů?

Aspose.Words umožňuje pracovat s komentáři ve vláknech, což vám umožňuje přidávat odpovědi k existujícím komentářům pro podrobnější diskuse.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}