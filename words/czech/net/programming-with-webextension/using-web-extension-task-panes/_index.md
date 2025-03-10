---
title: Použití podoken úloh webového rozšíření
linktitle: Použití podoken úloh webového rozšíření
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se přidávat a konfigurovat podokna úloh rozšíření webu v dokumentech aplikace Word pomocí Aspose.Words for .NET v tomto podrobném, podrobném kurzu.
weight: 10
url: /cs/net/programming-with-webextension/using-web-extension-task-panes/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití podoken úloh webového rozšíření

## Zavedení

Vítejte v tomto podrobném kurzu o používání podoken úloh rozšíření webu v dokumentu aplikace Word pomocí Aspose.Words for .NET. Pokud jste někdy chtěli vylepšit své dokumenty aplikace Word pomocí interaktivních podoken úloh, jste na správném místě. Tento průvodce vás provede každým krokem, jak toho dosáhnout.

## Předpoklady

Než se ponoříme, ujistěte se, že máte vše, co potřebujete:

-  Aspose.Words for .NET: Můžete si ji stáhnout[zde](https://releases.aspose.com/words/net/).
- Vývojové prostředí .NET: Visual Studio nebo jakékoli jiné IDE, které preferujete.
- Základní znalost C#: To vám pomůže sledovat příklady kódu.
-  Licence pro Aspose.Words: Můžete si jednu koupit[zde](https://purchase.aspose.com/buy) nebo získat dočasnou licenci[zde](https://purchase.aspose.com/temporary-license/).

## Importovat jmenné prostory

Než začneme kódovat, ujistěte se, že máte do projektu importovány následující jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.WebExtensions;
```

## Průvodce krok za krokem

Nyní si tento proces rozdělíme do snadno pochopitelných kroků.

### Krok 1: Nastavení adresáře dokumentů

Nejprve musíme nastavit cestu k adresáři vašich dokumentů. Zde bude uložen váš dokument aplikace Word.

```csharp
// Cesta k adresáři dokumentů.
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou ke složce dokumentů.

### Krok 2: Vytvoření nového dokumentu

Dále vytvoříme nový dokument Word pomocí Aspose.Words.

```csharp
Document doc = new Document();
```

 Tento řádek inicializuje novou instanci souboru`Document` třídy, která představuje dokument aplikace Word.

### Krok 3: Přidání podokna úloh

Nyní do našeho dokumentu přidáme podokno úloh. Panely úloh jsou užitečné pro poskytování dalších funkcí a nástrojů v dokumentu aplikace Word.

```csharp
TaskPane taskPane = new TaskPane();
doc.WebExtensionTaskPanes.Add(taskPane);
```

 Zde vytvoříme nový`TaskPane` objekt a přidejte jej do dokumentu`WebExtensionTaskPanes` sbírka.

### Krok 4: Konfigurace podokna úloh

K zviditelnění našeho podokna úloh a nastavení jeho vlastností používáme následující kód:

```csharp
taskPane.DockState = TaskPaneDockState.Right;
taskPane.IsVisible = true;
taskPane.Width = 300;
```

- `DockState` nastavuje, kde se zobrazí podokno úloh. V tomto případě je to vpravo.
- `IsVisible` zajišťuje, že je podokno úloh viditelné.
- `Width` nastavuje šířku podokna úloh.

### Krok 5: Referenční příručka pro nastavení webového rozšíření

Dále nastavíme Web Extension Reference, který obsahuje ID, verzi, typ úložiště a úložiště.

```csharp
taskPane.WebExtension.Reference.Id = "wa102923726";
taskPane.WebExtension.Reference.Version = "1.0.0.0";
taskPane.WebExtension.Reference.StoreType = WebExtensionStoreType.OMEX;
taskPane.WebExtension.Reference.Store = "th-TH";
```

- `Id`je jedinečný identifikátor webového rozšíření.
- `Version` určuje verzi rozšíření.
- `StoreType` označuje typ obchodu (v tomto případě OMEX).
- `Store` určuje kód jazyka/kultury obchodu.

### Krok 6: Přidání vlastností do webového rozšíření

Ke svému webovému rozšíření můžete přidat vlastnosti a definovat jeho chování nebo obsah.

```csharp
taskPane.WebExtension.Properties.Add(new WebExtensionProperty("mailchimpCampaign", "mailchimpCampaign"));
```

 Zde přidáme vlastnost s názvem`mailchimpCampaign`.

### Krok 7: Svázání webového rozšíření

Nakonec do našeho webového rozšíření přidáme vazby. Vazby umožňují propojit rozšíření s konkrétními částmi dokumentu.

```csharp
taskPane.WebExtension.Bindings.Add(new WebExtensionBinding("UnnamedBinding_0_1506535429545", WebExtensionBindingType.Text, "194740422"));
```

- `UnnamedBinding_0_1506535429545` je název vazby.
- `WebExtensionBindingType.Text` označuje, že vazba je textového typu.
- `194740422` je ID části dokumentu, ke které je rozšíření vázáno.

### Krok 8: Uložení dokumentu

Po nastavení všeho dokument uložte.

```csharp
doc.Save(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");
```

Tento řádek uloží dokument do zadaného adresáře s daným názvem souboru.

### Krok 9: Načtení a zobrazení informací v podokně úloh

Abychom ověřili a zobrazili informace v podokně úloh, načteme dokument a projdeme podokny úloh.

```csharp
doc = new Document(dataDir + "WorkingWithWebExtension.UsingWebExtensionTaskPanes.docx");

Console.WriteLine("Task panes sources:\n");

foreach (TaskPane taskPaneInfo in doc.WebExtensionTaskPanes)
{
    WebExtensionReference reference = taskPaneInfo.WebExtension.Reference;
    Console.WriteLine($"Provider: \"{reference.Store}\", version: \"{reference.Version}\", catalog identifier: \"{reference.Id}\";");
}
```

Tento kód načte dokument a vytiskne identifikátor poskytovatele, verze a katalogu každého podokna úloh v konzole.

## Závěr

A je to! Úspěšně jste přidali a nakonfigurovali podokno úloh rozšíření webu v dokumentu aplikace Word pomocí Aspose.Words for .NET. Tato výkonná funkce může výrazně vylepšit vaše dokumenty aplikace Word tím, že poskytuje další funkce přímo v dokumentu. 

## FAQ

### Co je podokno úloh ve Wordu?
Podokno úloh je prvek rozhraní, který poskytuje další nástroje a funkce v dokumentu aplikace Word, čímž zlepšuje interakci a produktivitu uživatele.

### Mohu přizpůsobit vzhled podokna úloh?
 Ano, vzhled podokna úloh můžete přizpůsobit nastavením vlastností jako`DockState`, `IsVisible` a`Width`.

### Co jsou vlastnosti webových rozšíření?
Vlastnosti webového rozšíření jsou vlastní vlastnosti, které můžete přidat k webovému rozšíření a definovat jeho chování nebo obsah.

### Jak připojím webové rozšíření k části dokumentu?
 Webové rozšíření můžete svázat s částí dokumentu pomocí`WebExtensionBinding` třída s uvedením typu vazby a cílového ID.

### Kde najdu další informace o Aspose.Words pro .NET?
 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
