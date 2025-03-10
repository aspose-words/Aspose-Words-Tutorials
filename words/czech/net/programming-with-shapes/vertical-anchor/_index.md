---
title: Vertikální kotva
linktitle: Vertikální kotva
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se, jak nastavit vertikální pozice ukotvení pro textová pole v dokumentech aplikace Word pomocí Aspose.Words for .NET. Včetně jednoduchého průvodce krok za krokem.
weight: 10
url: /cs/net/programming-with-shapes/vertical-anchor/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Vertikální kotva

## Zavedení

Stalo se vám někdy, že jste potřebovali přesně řídit, kde se text objeví v textovém poli v dokumentu aplikace Word? Možná chcete, aby byl váš text ukotven v horní, střední nebo spodní části textového pole? Pokud ano, jste na správném místě! V tomto tutoriálu prozkoumáme, jak používat Aspose.Words pro .NET k nastavení vertikálního ukotvení textových polí v dokumentech aplikace Word. Vertikální ukotvení si představte jako kouzelnou hůlku, která umístí váš text v kontejneru přesně tam, kde ho chcete. Jste připraveni se ponořit? Začněme!

## Předpoklady

Než se ponoříme do matic a šroubů vertikálního kotvení, budete muset mít na svém místě několik věcí:

1.  Aspose.Words for .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words for .NET. Pokud ho ještě nemáte, můžete[stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Visual Studio: Tento kurz předpokládá, že pro kódování používáte Visual Studio nebo jiné .NET IDE.
3. Základní znalost C#: Znalost C# a .NET vám pomůže hladce pokračovat.

## Importovat jmenné prostory

Chcete-li začít, musíte do kódu C# importovat potřebné jmenné prostory. Zde sdělíte své aplikaci, kde má najít třídy a metody, které použijete. Jak na to:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Tyto jmenné prostory poskytují třídy, které budete potřebovat pro práci s dokumenty a tvary.

## Krok 1: Inicializujte dokument

Nejprve musíte vytvořit nový dokument aplikace Word. Berte to jako nastavení plátna, než začnete malovat.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Zde,`Document` je vaše prázdné plátno a`DocumentBuilder` je váš štětec, který vám umožňuje přidávat tvary a text.

## Krok 2: Vložte tvar textového pole

Nyní do našeho dokumentu přidáme textové pole. Tady bude váš text žít. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

 V tomto příkladu`ShapeType.TextBox` určuje požadovaný tvar a`200, 200` jsou šířka a výška textového pole v bodech.

## Krok 3: Nastavte vertikální kotvu

Tady se děje kouzlo! V textovém poli můžete nastavit svislé zarovnání textu. To určuje, zda je text ukotven k horní, střední nebo spodní části textového pole.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

 v tomto případě`TextBoxAnchor.Bottom`zajistí, že text bude ukotven ke spodní části textového pole. Pokud byste ji chtěli vycentrovat nebo zarovnat nahoru, použili byste`TextBoxAnchor.Center` nebo`TextBoxAnchor.Top`, resp.

## Krok 4: Přidejte text do textového pole

Nyní je čas přidat do textového pole nějaký obsah. Představte si to jako vyplnění vašeho plátna posledními úpravami.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

 Zde,`MoveTo` zajistí vložení textu do textového pole a`Write` přidá aktuální text.

## Krok 5: Uložte dokument

Posledním krokem je uložení dokumentu. Je to jako vložit hotový obraz do rámu.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Závěr

A tady to máte! Právě jste se naučili, jak ovládat vertikální zarovnání textu v textovém poli v dokumentu aplikace Word pomocí Aspose.Words for .NET. Ať už ukotvujete text nahoru, doprostřed nebo dolů, tato funkce vám poskytuje přesnou kontrolu nad rozložením dokumentu. Takže až budete příště potřebovat upravit umístění textu v dokumentu, budete vědět, co máte dělat!

## FAQ

### Co je vertikální ukotvení v dokumentu aplikace Word?
Svislé ukotvení řídí, kde je text umístěn v textovém poli, jako je zarovnání nahoru, na střed nebo dolů.

### Mohu použít jiné tvary kromě textových polí?
Ano, vertikální ukotvení můžete použít s jinými tvary, ačkoli textová pole jsou nejčastějším případem použití.

### Jak změním kotevní bod po vytvoření textového pole?
 Kotevní bod můžete změnit nastavením`VerticalAnchor` vlastnost na objektu tvaru textového pole.

### Je možné ukotvit text doprostřed textového pole?
 Absolutně! Stačí použít`TextBoxAnchor.Center` pro svislé vystředění textu v textovém poli.

### Kde najdu další informace o Aspose.Words pro .NET?
 Podívejte se na[Dokumentace Aspose.Words](https://reference.aspose.com/words/net/) pro další podrobnosti a průvodce.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
