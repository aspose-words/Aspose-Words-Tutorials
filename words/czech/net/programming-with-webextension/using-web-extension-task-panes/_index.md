---
"description": "V tomto podrobném návodu se naučíte, jak přidávat a konfigurovat panely úloh webového rozšíření v dokumentech Word pomocí Aspose.Words pro .NET."
"linktitle": "Používání podoken úloh webového rozšíření"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Používání podoken úloh webového rozšíření"
"url": "/cs/net/programming-with-webextension/using-web-extension-task-panes/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání podoken úloh webového rozšíření

## Zavedení

Vítejte v tomto podrobném tutoriálu o používání panelů úloh webového rozšíření v dokumentu Word pomocí Aspose.Words pro .NET. Pokud jste někdy chtěli vylepšit své dokumenty Word interaktivními panely úloh, jste na správném místě. Tato příručka vás provede každým krokem, abyste toho bez problémů dosáhli.

## Předpoklady

Než se do toho pustíme, ujistěme se, že máte vše potřebné:

- Aspose.Words pro .NET: Můžete si ho stáhnout [zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Visual Studio nebo jakékoli jiné IDE, které preferujete.
- Základní znalost jazyka C#: To vám pomůže sledovat příklady kódu.
- Licence pro Aspose.Words: Můžete si jednu koupit [zde](https://purchase.aspose.com/buy) nebo si pořídit dočasný řidičský průkaz [zde](https://purchase.aspose.com/temporary-license/).

## Importovat jmenné prostory

Než začneme s kódováním, ujistěte se, že máte v projektu importovány následující jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Podrobný průvodce

Nyní si celý proces rozdělme na snadno sledovatelné kroky.

### Krok 1: Nastavení adresáře dokumentů

Nejdříve musíme nastavit cestu k adresáři s vašimi dokumenty. Zde bude uložen váš dokument Wordu.

```csharp
// Cesta k adresáři s dokumenty.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou ke složce s dokumenty.

### Krok 2: Vytvoření nového dokumentu

Dále vytvoříme nový dokument Wordu pomocí Aspose.Words.

```csharp
Document doc = new Document();
```

Tento řádek inicializuje novou instanci třídy `Document` třída, která představuje dokument aplikace Word.

### Krok 3: Přidání podokna úloh

Nyní do našeho dokumentu přidáme podokno úloh. Podokna úloh jsou užitečná pro poskytování dalších funkcí a nástrojů v dokumentu Word.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

Zde vytváříme nový `TaskPane` objekt a přidat ho do dokumentu `WebExtensionTaskPanes` sbírka.

### Krok 4: Konfigurace podokna úloh

Pro zobrazení našeho panelu úloh a nastavení jeho vlastností použijeme následující kód:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` určuje, kde se zobrazí podokno úloh. V tomto případě je to vpravo.
- `IsVisible` zajišťuje, že je podokno úloh viditelné.
- `Width` nastavuje šířku podokna úloh.

### Krok 5: Nastavení referenčního webového rozšíření

Dále nastavíme referenci webového rozšíření, která obsahuje ID, verzi, typ úložiště a samotné úložiště.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id` je jedinečný identifikátor pro webové rozšíření.
- `Version` určuje verzi rozšíření.
- `StoreType` označuje typ prodejny (v tomto případě OMEX).
- `Store` určuje jazykový/kulturní kód obchodu.

### Krok 6: Přidání vlastností k webovému rozšíření

Do webového rozšíření můžete přidat vlastnosti, které definují jeho chování nebo obsah.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

Zde přidáme vlastnost s názvem `mailchimpCampaign`.

### Krok 7: Vazba webového rozšíření

Nakonec přidáme k našemu webovému rozšíření vazby. Vazby umožňují propojit rozšíření s konkrétními částmi dokumentu.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` je název vazby.
- `WebExtensionBindingType.Text` označuje, že vazba je textového typu.
- `194740422` je ID části dokumentu, ke které je rozšíření vázáno.

### Krok 8: Uložení dokumentu

Po nastavení všech parametrů dokument uložte.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Tento řádek uloží dokument do zadaného adresáře s daným názvem souboru.

### Krok 9: Načtení a zobrazení informací z podokna úloh

Pro ověření a zobrazení informací v podokně úloh načteme dokument a iterujeme podokny úloh.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Tento kód načte dokument a v konzoli vypíše poskytovatele, verzi a identifikátor katalogu pro každé podokno úloh.

## Závěr

A to je vše! Úspěšně jste přidali a nakonfigurovali podokno úloh webového rozšíření v dokumentu Word pomocí Aspose.Words pro .NET. Tato výkonná funkce může výrazně vylepšit vaše dokumenty Word tím, že přímo v dokumentu poskytne další funkce. 

## Často kladené otázky

### Co je to podokno úloh ve Wordu?
Podokno úloh je prvek rozhraní, který poskytuje další nástroje a funkce v dokumentu Word, čímž zlepšuje interakci s uživatelem a produktivitu.

### Mohu si přizpůsobit vzhled podokna úloh?
Ano, vzhled podokna úloh si můžete přizpůsobit nastavením vlastností, jako je `DockState`, `IsVisible`a `Width`.

### Co jsou vlastnosti webového rozšíření?
Vlastnosti webového rozšíření jsou vlastní vlastnosti, které můžete přidat k webovému rozšíření a definovat tak jeho chování nebo obsah.

### Jak propojím webové rozšíření s částí dokumentu?
Webové rozšíření můžete svázat s částí dokumentu pomocí `WebExtensionBinding` třída s uvedením typu vazby a ID cíle.

### Kde najdu více informací o Aspose.Words pro .NET?
Podrobnou dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}