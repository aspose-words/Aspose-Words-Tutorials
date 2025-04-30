---
"description": "Naučte se, jak upravovat strukturované tagy dokumentů ve Wordu pomocí Aspose.Words pro .NET. Aktualizujte text, rozbalovací nabídky a obrázky krok za krokem."
"linktitle": "Úprava ovládacích prvků obsahu"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Úprava ovládacích prvků obsahu"
"url": "/cs/net/programming-with-sdt/modify-content-controls/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Úprava ovládacích prvků obsahu

## Zavedení

Pokud jste někdy pracovali s dokumenty Wordu a potřebovali jste upravit strukturované ovládací prvky obsahu – jako je prostý text, rozevírací seznamy nebo obrázky – pomocí Aspose.Words pro .NET, jste na správném místě! Strukturované tagy dokumentů (SDT) jsou výkonné nástroje, které usnadňují a zvyšují flexibilitu automatizace dokumentů. V tomto tutoriálu se ponoříme do toho, jak můžete tyto SDT upravit podle svých potřeb. Ať už aktualizujete text, měníte výběry v rozevíracích nabídkách nebo vyměňujete obrázky, tento průvodce vás krok za krokem provede celým procesem.

## Předpoklady

Než se pustíme do detailů úpravy ovládacích prvků obsahu, ujistěte se, že máte následující:

1. Nainstalovaná knihovna Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ne, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).

2. Základní znalost C#: Tento tutoriál předpokládá, že jste obeznámeni se základními koncepty programování v C#.

3. Vývojové prostředí .NET: Pro spouštění aplikací .NET byste měli mít nastavené IDE, jako je Visual Studio.

4. Ukázkový dokument: Použijeme ukázkový dokument aplikace Word s různými typy SDT. Můžete použít ten z příkladu nebo si vytvořit vlastní.

5. Přístup k dokumentaci Aspose: Podrobnější informace naleznete v [Dokumentace k Aspose.Words](https://reference.aspose.com/words/net/).

## Importovat jmenné prostory

Abyste mohli začít pracovat s Aspose.Words, musíte importovat příslušné jmenné prostory do svého projektu v C#. Postupujte takto:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Tyto jmenné prostory vám poskytnou přístup ke třídám a metodám potřebným pro manipulaci se strukturovanými tagy dokumentů v dokumentech Wordu.

## Krok 1: Nastavení cesty k dokumentu

Před provedením jakýchkoli změn je nutné zadat cestu k dokumentu. Nahradit `"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je váš dokument uložen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Krok 2: Procházení strukturovaných tagů dokumentů

Chcete-li upravit SDT, musíte nejprve projít všechny SDT v dokumentu. To se provádí pomocí `GetChildNodes` metoda pro získání všech uzlů typu `StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Upravte SDT na základě jejich typu
}
```

## Krok 3: Úprava SDT v prostém textu

Pokud je SDT typ prostého textu, můžete jeho obsah nahradit. Nejprve vymažte stávající obsah a poté přidejte nový text.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

Vysvětlení: Zde, `RemoveAllChildren()` vymaže existující obsah SDT. Poté vytvoříme nový `Paragraph` a `Run` objekt pro vložení nového textu.

## Krok 4: Úprava SDT rozevíracího seznamu

U rozbalovacích seznamů SDT můžete změnit vybranou položku přístupem k `ListItems` kolekce. Zde vybereme třetí položku v seznamu.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Vysvětlení: Tento úryvek kódu vybere položku s indexem 2 (třetí položka) z rozbalovacího seznamu. Upravte index podle svých potřeb.

## Krok 5: Úprava obrazových SDT

Chcete-li aktualizovat obrázek v rámci obrázkového SDT, můžete stávající obrázek nahradit novým.

```csharp
if (sdt.SdtType == SdtType.Picture)
{
    Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
    if (shape.HasImage)
    {
        shape.ImageData.SetImage(ImagesDir + "Watermark.png");
    }
}
```

Vysvětlení: Tento kód zkontroluje, zda tvar obsahuje obrázek, a poté jej nahradí novým obrázkem umístěným v `ImagesDir`.

## Krok 6: Uložte upravený dokument

Po provedení všech potřebných změn uložte upravený dokument pod novým názvem, aby původní dokument zůstal neporušený.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Vysvětlení: Tím se dokument uloží s novým názvem souboru, abyste ho mohli snadno odlišit od originálu.

## Závěr

Úprava ovládacích prvků obsahu v dokumentu Word pomocí Aspose.Words pro .NET je jednoduchá, jakmile pochopíte jednotlivé kroky. Ať už aktualizujete text, měníte výběry v rozbalovacích nabídkách nebo vyměňujete obrázky, Aspose.Words poskytuje robustní API pro tyto úkoly. Dodržováním tohoto tutoriálu můžete efektivně spravovat a přizpůsobovat strukturované ovládací prvky obsahu dokumentu, čímž se vaše dokumenty stanou dynamičtějšími a přizpůsobenějšími vašim potřebám.

## Často kladené otázky

1. Co je to tag strukturovaného dokumentu (SDT)?

SDT jsou prvky v dokumentech Wordu, které pomáhají spravovat a formátovat obsah dokumentu, jako jsou textová pole, rozevírací seznamy nebo obrázky.

2. Jak mohu do SDT přidat novou položku rozbalovací nabídky?

Chcete-li přidat novou položku, použijte `ListItems` vlastnost a přidat novou `SdtListItem` do sbírky.

3. Mohu použít Aspose.Words k odstranění SDT z dokumentu?

Ano, SDT můžete odstranit tak, že přistoupíte k uzlům dokumentu a smažete požadovaný SDT.

4. Jak mám zpracovat SDT, které jsou vnořené do jiných prvků?

Použijte `GetChildNodes` metoda s příslušnými parametry pro přístup k vnořeným SDT.

5. Co mám dělat, když SDT, který potřebuji upravit, není v dokumentu viditelný?

Ujistěte se, že SDT není skrytý nebo chráněný. Zkontrolujte nastavení dokumentu a ujistěte se, že váš kód správně cílí na typ SDT.


### Příklad zdrojového kódu pro úpravu ovládacích prvků obsahu pomocí Aspose.Words pro .NET 

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Structured document tags.docx");
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
	switch (sdt.SdtType)
	{
		case SdtType.PlainText:
		{
			sdt.RemoveAllChildren();
			Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
			Run run = new Run(doc, "new text goes here");
			para.AppendChild(run);
			break;
		}
		case SdtType.DropDownList:
		{
			SdtListItem secondItem = sdt.ListItems[2];
			sdt.ListItems.SelectedValue = secondItem;
			break;
		}
		case SdtType.Picture:
		{
			Shape shape = (Shape) sdt.GetChild(NodeType.Shape, 0, true);
			if (shape.HasImage)
			{
				shape.ImageData.SetImage(ImagesDir + "Watermark.png");
			}
			break;
		}
	}
}
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");

```

To je vše! Úspěšně jste upravili různé typy ovládacích prvků obsahu v dokumentu Word pomocí Aspose.Words pro .NET.

{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}