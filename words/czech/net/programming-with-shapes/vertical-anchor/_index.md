---
"description": "Naučte se, jak nastavit svislé kotevní pozice pro textová pole v dokumentech Word pomocí Aspose.Words pro .NET. Součástí je i jednoduchý podrobný návod."
"linktitle": "Vertikální kotva"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vertikální kotva"
"url": "/cs/net/programming-with-shapes/vertical-anchor/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vertikální kotva

## Zavedení

Už jste někdy zjistili, že potřebujete přesně ovládat, kde se text v textovém poli v dokumentu Word zobrazuje? Možná chcete, aby byl text ukotven v horní, střední nebo dolní části textového pole? Pokud ano, jste na správném místě! V tomto tutoriálu se podíváme na to, jak pomocí Aspose.Words pro .NET nastavit vertikální ukotvení textových polí v dokumentech Word. Představte si vertikální ukotvení jako kouzelnou hůlku, která umístí text přesně tam, kam ho chcete v rámci jeho kontejneru umístit. Jste připraveni se do toho pustit? Pojďme na to!

## Předpoklady

Než se ponoříme do detailů vertikálního kotvení, je třeba mít připraveno několik věcí:

1. Aspose.Words pro .NET: Ujistěte se, že máte nainstalovanou knihovnu Aspose.Words pro .NET. Pokud ji ještě nemáte, můžete [stáhněte si to zde](https://releases.aspose.com/words/net/).
2. Visual Studio: Tento tutoriál předpokládá, že pro kódování používáte Visual Studio nebo jiné vývojové prostředí .NET.
3. Základní znalost C#: Znalost C# a .NET vám pomůže plynule se orientovat.

## Importovat jmenné prostory

Chcete-li začít, musíte do kódu C# importovat potřebné jmenné prostory. Zde sdělíte své aplikaci, kde má najít třídy a metody, které budete používat. Zde je návod, jak to udělat:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Tyto jmenné prostory poskytují třídy, které budete potřebovat pro práci s dokumenty a tvary.

## Krok 1: Inicializace dokumentu

Nejdříve je potřeba vytvořit nový dokument Wordu. Představte si to jako přípravu plátna před začátkem malování.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Zde, `Document` je tvé prázdné plátno a `DocumentBuilder` je váš štětec, kterým můžete přidávat tvary a text.

## Krok 2: Vložení tvaru textového pole

Nyní přidejme do našeho dokumentu textové pole. Zde bude umístěn váš text. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

V tomto příkladu `ShapeType.TextBox` určuje požadovaný tvar a `200, 200` je šířka a výška textového pole v bodech.

## Krok 3: Nastavení svislé kotvy

tady se děje ta pravá magie! Můžete nastavit svislé zarovnání textu v textovém poli. To určuje, zda bude text ukotven v horní, střední nebo dolní části textového pole.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

V tomto případě, `TextBoxAnchor.Bottom` zajišťuje, že text bude ukotven k dolní části textového pole. Pokud byste ho chtěli vycentrovat nebo zarovnat nahoru, použili byste `TextBoxAnchnebo.Center` or `TextBoxAnchor.Top`, v uvedeném pořadí.

## Krok 4: Přidání textu do textového pole

Nyní je čas přidat do textového pole nějaký obsah. Představte si to jako vyplnění plátna finálními úpravami.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

Zde, `MoveTo` zajišťuje, že text je vložen do textového pole a `Write` přidá skutečný text.

## Krok 5: Uložte dokument

Posledním krokem je uložení dokumentu. Je to jako kdybyste zarámovali hotový obraz.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Závěr

tady to máte! Právě jste se naučili, jak ovládat svislé zarovnání textu v textovém poli v dokumentu Wordu pomocí Aspose.Words pro .NET. Ať už ukotvujete text nahoru, na střed nebo dolů, tato funkce vám dává přesnou kontrolu nad rozvržením dokumentu. Takže až budete příště potřebovat upravit umístění textu v dokumentu, budete přesně vědět, co dělat!

## Často kladené otázky

### Co je vertikální ukotvení v dokumentu Word?
Svislé ukotvení určuje umístění textu v textovém poli, například zarovnání nahoře, doprostřed nebo dole.

### Mohu použít i jiné tvary než textová pole?
Ano, vertikální ukotvení můžete použít i s jinými tvary, ačkoli textová pole jsou nejčastějším případem použití.

### Jak změním kotevní bod po vytvoření textového pole?
Kotvící bod můžete změnit nastavením `VerticalAnchor` vlastnost objektu tvaru textového pole.

### Je možné ukotvit text doprostřed textového pole?
Rozhodně! Stačí použít `TextBoxAnchor.Center` pro svislou centrování textu v textovém poli.

### Kde najdu více informací o Aspose.Words pro .NET?
Podívejte se na [Dokumentace k Aspose.Words](https://reference.aspose.com/words/net/) pro více informací a návodů.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}