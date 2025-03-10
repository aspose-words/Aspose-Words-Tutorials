---
title: Upravit ovládací prvky obsahu
linktitle: Upravit ovládací prvky obsahu
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se upravovat tagy strukturovaných dokumentů ve Wordu pomocí Aspose.Words for .NET. Aktualizujte text, rozevírací seznamy a obrázky krok za krokem.
weight: 10
url: /cs/net/programming-with-sdt/modify-content-controls/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Upravit ovládací prvky obsahu

## Zavedení

Pokud jste někdy pracovali s dokumenty aplikace Word a potřebovali jste upravit ovládací prvky strukturovaného obsahu – jako prostý text, rozevírací seznamy nebo obrázky – pomocí Aspose.Words pro .NET, jste na správném místě! Structured Document Tags (SDT) jsou výkonné nástroje, díky nimž je automatizace dokumentů snadnější a flexibilnější. V tomto tutoriálu se ponoříme do toho, jak můžete upravit tyto SDT tak, aby vyhovovaly vašim potřebám. Ať už aktualizujete text, měníte výběr v rozevíracím seznamu nebo vyměňujete obrázky, tento průvodce vás provede procesem krok za krokem.

## Předpoklady

Než se vrhneme na to, co je nutné s úpravou ovládacích prvků obsahu, ujistěte se, že máte následující:

1.  Aspose.Words for .NET Installed: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words. Pokud ne, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).

2. Základní znalost C#: Tento tutoriál předpokládá, že jste obeznámeni se základními koncepty programování v C#.

3. Vývojové prostředí .NET: Pro spouštění aplikací .NET byste měli mít nastavené IDE jako Visual Studio.

4. Ukázkový dokument: Budeme používat ukázkový dokument aplikace Word s různými typy SDT. Můžete použít ten z příkladu nebo si vytvořit vlastní.

5.  Přístup k dokumentaci Aspose: Podrobnější informace naleznete na[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/).

## Importovat jmenné prostory

Chcete-li začít pracovat s Aspose.Words, musíte do svého projektu C# importovat příslušné jmenné prostory. Postup je následující:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Tyto jmenné prostory vám umožní přístup ke třídám a metodám nezbytným pro manipulaci se strukturovanými značkami dokumentů v dokumentech aplikace Word.

## Krok 1: Nastavte cestu k dokumentu

 Před provedením jakýchkoli změn musíte zadat cestu k dokumentu. Nahradit`"YOUR DOCUMENT DIRECTORY"` se skutečnou cestou, kde je dokument uložen.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Structured document tags.docx");
```

## Krok 2: Procházení tagů strukturovaného dokumentu

 Chcete-li upravit SDT, musíte nejprve projít všechny SDT v dokumentu. To se provádí pomocí`GetChildNodes` metoda k získání všech uzlů typu`StructuredDocumentTag`.

```csharp
foreach (StructuredDocumentTag sdt in doc.GetChildNodes(NodeType.StructuredDocumentTag, true))
{
    // Upravte SDT na základě jejich typu
}
```

## Krok 3: Upravte SDT ve formátu prostého textu

Pokud je SDT typu prostého textu, můžete jeho obsah nahradit. Nejprve vymažte stávající obsah a poté přidejte nový text.

```csharp
if (sdt.SdtType == SdtType.PlainText)
{
    sdt.RemoveAllChildren();
    Paragraph para = sdt.AppendChild(new Paragraph(doc)) as Paragraph;
    Run run = new Run(doc, "new text goes here");
    para.AppendChild(run);
}
```

 Vysvětlení: Zde,`RemoveAllChildren()`vymaže stávající obsah SDT. Poté vytvoříme nový`Paragraph` a`Run` objekt pro vložení nového textu.

## Krok 4: Upravte SDT rozevíracího seznamu

 U SDT rozevíracího seznamu můžete vybranou položku změnit přístupem k`ListItems` sbírka. Zde vybereme třetí položku v seznamu.

```csharp
if (sdt.SdtType == SdtType.DropDownList)
{
    SdtListItem secondItem = sdt.ListItems[2];
    sdt.ListItems.SelectedValue = secondItem;
}
```

Vysvětlení: Tento fragment kódu vybere položku na indexu 2 (třetí položka) z rozevíracího seznamu. Upravte index podle svých potřeb.

## Krok 5: Upravte SDT obrázků

Chcete-li aktualizovat obrázek v rámci SDT obrázku, můžete nahradit stávající obrázek novým.

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

 Vysvětlení: Tento kód zkontroluje, zda tvar obsahuje obrázek, a poté jej nahradí novým obrázkem umístěným na`ImagesDir`.

## Krok 6: Uložte svůj upravený dokument

Po provedení všech nezbytných změn uložte upravený dokument pod novým názvem, aby byl původní dokument zachován.

```csharp
doc.Save(dataDir + "WorkingWithSdt.ModifyContentControls.docx");
```

Vysvětlení: Tím se dokument uloží s novým názvem souboru, takže jej můžete snadno odlišit od originálu.

## Závěr

Úprava ovládacích prvků obsahu v dokumentu aplikace Word pomocí Aspose.Words for .NET je jednoduchá, jakmile pochopíte příslušné kroky. Ať už aktualizujete text, měníte výběry v rozevíracím seznamu nebo vyměňujete obrázky, Aspose.Words poskytuje pro tyto úkoly robustní rozhraní API. Podle tohoto kurzu můžete efektivně spravovat a přizpůsobovat ovládací prvky strukturovaného obsahu dokumentu, díky čemuž budou vaše dokumenty dynamičtější a přizpůsobené vašim potřebám.

## Nejčastější dotazy

1. Co je to značka strukturovaného dokumentu (SDT)?

SDT jsou prvky v dokumentech aplikace Word, které pomáhají spravovat a formátovat obsah dokumentu, jako jsou textová pole, rozevírací seznamy nebo obrázky.

2. Jak mohu přidat novou rozevírací položku do SDT?

 Chcete-li přidat novou položku, použijte`ListItems` vlastnost a připojit novou`SdtListItem` do sbírky.

3. Mohu použít Aspose.Words k odstranění SDT z dokumentu?

Ano, SDT můžete odstranit tak, že otevřete uzly dokumentu a smažete požadovaný SDT.

4. Jak zacházím s SDT, které jsou vnořeny do jiných prvků?

 Použijte`GetChildNodes` metoda s vhodnými parametry pro přístup k vnořeným SDT.

5. Co mám dělat, když SDT, kterou potřebuji upravit, není v dokumentu vidět?

Ujistěte se, že SDT není skrytý nebo chráněný. Zkontrolujte nastavení dokumentu a ujistěte se, že váš kód správně cílí na typ SDT.


### Příklad zdrojového kódu pro úpravu ovládacích prvků obsahu pomocí Aspose.Words pro .NET 

```csharp
// Cesta k vašemu adresáři dokumentů
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

To je vše! Úspěšně jste upravili různé typy ovládacích prvků obsahu v dokumentu aplikace Word pomocí Aspose.Words for .NET.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
