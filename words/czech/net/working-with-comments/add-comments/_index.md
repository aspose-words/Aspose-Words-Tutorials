---
title: Přidat komentáře
linktitle: Přidat komentáře
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se v našem průvodci přidávat komentáře do dokumentů aplikace Word pomocí Aspose.Words for .NET. Vylepšete svůj proces spolupráce na dokumentech bez námahy.
weight: 10
url: /cs/net/working-with-comments/add-comments/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Přidat komentáře

## Zavedení

Vítejte v našem podrobném průvodci přidáváním komentářů do dokumentů aplikace Word pomocí Aspose.Words pro .NET! Pokud chcete zefektivnit proces kontroly dokumentů programovým začleněním komentářů, jste na správném místě. Tento tutoriál vás provede vším, co potřebujete vědět, od nastavení prostředí až po psaní a ukládání komentářů v dokumentech aplikace Word. Pojďme se ponořit a udělejte ze spolupráce na dokumentech hračku!

## Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Aspose.Words for .NET: Musíte mít nainstalovanou aplikaci Aspose.Words for .NET. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/net/).
2. .NET Framework: Ujistěte se, že máte na svém počítači nainstalované rozhraní .NET Framework.
3. Vývojové prostředí: IDE jako Visual Studio pro psaní a spouštění vašeho kódu.
4. Základní znalost C#: Znalost programovacího jazyka C# vám pomůže postupovat podle příkladů.

## Importovat jmenné prostory

Nejprve musíte do projektu importovat potřebné jmenné prostory. To vám umožní přístup ke třídám a metodám potřebným pro práci s Aspose.Words.

```csharp
using System;
using Aspose.Words;
```

Nyní si tento proces rozdělíme do snadno pochopitelných kroků. Každý krok bude obsahovat podrobné vysvětlení, které vám pomůže pochopit logiku a funkce.

## Krok 1: Nastavte adresář dokumentů

 Nejprve musíme definovat adresář, kam bude váš dokument uložen. Použijeme zástupný symbol`YOUR DOCUMENT DIRECTORY` kterou byste měli nahradit svou skutečnou cestou k adresáři.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Krok 2: Inicializujte dokument

Dále inicializujeme nový dokument a objekt DocumentBuilder. DocumentBuilder nám pomáhá sestavit a upravit dokument.

```csharp
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Krok 3: Přidejte text do dokumentu

Do dokumentu přidáme nějaký text pomocí DocumentBuilderu. K tomuto textu připojíme náš komentář.

```csharp
builder.Write("Some text is added.");
```

## Krok 4: Vytvořte a připojte komentář

Nyní je čas vytvořit komentář. Inicializujeme nový objekt Comment s uvedením dokumentu, jména autora, iniciál a data.

```csharp
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
```

## Krok 5: Přidejte obsah do komentáře

Nakonec do komentáře přidáme obsah. Vytvoříme nový Odstavec a Spustit, ve kterých bude text komentáře uložen, a poté je přidáme do komentáře.

```csharp
comment.SetText("Comment text.");
```

## Krok 6: Připojte komentář k odstavci

Komentář musíme připojit k aktuálnímu odstavci, kam jsme text přidali. To se provádí připojením komentáře k odstavci.

```csharp
builder.CurrentParagraph.AppendChild(comment);
```

## Krok 7: Uložte dokument

Posledním krokem je uložení dokumentu s komentáři. Zadáme adresář a název souboru.

```csharp
doc.Save(dataDir + "WorkingWithComments.AddComments.docx");
```

## Závěr

Tady to máš! Úspěšně jste přidali komentáře do dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná funkce může výrazně vylepšit váš proces recenzování dokumentů a usnadnit spolupráci a sdělování zpětné vazby. Nezapomeňte prozkoumat další možnosti Aspose.Words, abyste dále zjednodušili své úkoly správy dokumentů.

## FAQ

### Co je Aspose.Words for .NET?

Aspose.Words for .NET je výkonné rozhraní API, které umožňuje vývojářům vytvářet, manipulovat a převádět dokumenty aplikace Word programově pomocí jazyků .NET.

### Mohu přidat více komentářů k jednomu dokumentu?

Ano, k jednomu dokumentu můžete přidat více komentářů opakováním procesu vytváření a přidávání komentářů do různých odstavců nebo textových úseků.

### Jak mohu upravit vzhled komentářů?

Zatímco Aspose.Words se zaměřuje na obsah a strukturu komentářů, vzhled lze přizpůsobit pomocí vestavěných funkcí formátování aplikace Word.

### Je možné odstranit komentáře programově?

Ano, komentáře můžete odstraňovat programově tak, že projdete komentáře v dokumentu a odeberete je podle potřeby.

### Mohu přidávat odpovědi do komentářů?

Aspose.Words vám umožňuje pracovat s vláknovými komentáři a umožňuje vám přidávat odpovědi na existující komentáře pro podrobnější diskuse.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
