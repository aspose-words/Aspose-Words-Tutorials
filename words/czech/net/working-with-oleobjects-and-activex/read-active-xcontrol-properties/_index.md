---
"description": "Naučte se, jak číst vlastnosti ovládacího prvku ActiveX ze souborů Wordu pomocí Aspose.Words pro .NET v podrobném návodu. Zlepšete si své dovednosti v automatizaci dokumentů."
"linktitle": "Načíst vlastnosti ovládacího prvku Active XControl ze souboru aplikace Word"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Načíst vlastnosti ovládacího prvku Active XControl ze souboru aplikace Word"
"url": "/cs/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Načíst vlastnosti ovládacího prvku Active XControl ze souboru aplikace Word

## Zavedení

dnešní digitální době je automatizace klíčem ke zvýšení produktivity. Pokud pracujete s dokumenty aplikace Word, které obsahují ovládací prvky ActiveX, můžete potřebovat číst jejich vlastnosti z různých důvodů. Ovládací prvky ActiveX, jako jsou zaškrtávací políčka a tlačítka, mohou obsahovat důležitá data. Pomocí Aspose.Words pro .NET můžete tato data efektivně extrahovat a programově s nimi manipulovat.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Knihovna Aspose.Words pro .NET: Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/net/).
2. Visual Studio nebo jakékoli C# IDE: Pro psaní a spuštění kódu.
3. Dokument aplikace Word s ovládacími prvky ActiveX: Například „Ovládací prvky ActiveX.docx“.
4. Základní znalost C#: Znalost programování v C# je nezbytná pro pokračování.

## Importovat jmenné prostory

Nejprve si importujme potřebné jmenné prostory pro práci s Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Krok 1: Načtěte dokument Wordu

Nejprve budete muset načíst dokument aplikace Word, který obsahuje ovládací prvky ActiveX.

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Krok 2: Inicializace řetězce pro uchování vlastností

Dále inicializujte prázdný řetězec pro uložení vlastností ovládacích prvků ActiveX.

```csharp
string properties = "";
```

## Krok 3: Iterujte tvary v dokumentu

Abychom našli ovládací prvky ActiveX, musíme iterovat všemi tvary v dokumentu.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Zpracování ovládacího prvku ActiveX
    }
}
```

## Krok 4: Extrakce vlastností z ovládacích prvků ActiveX

V rámci smyčky zkontrolujte, zda je ovládací prvek typu Forms2OleControl. Pokud ano, přetypujte jej a extrahujte vlastnosti.

```csharp
Forms2OleControl checkBox = (Forms2OleControl) oleControl;
properties += "\nCaption: " + checkBox.Caption;
properties += "\nValue: " + checkBox.Value;
properties += "\nEnabled: " + checkBox.Enabled;
properties += "\nType: " + checkBox.Type;

if (checkBox.ChildNodes != null)
{
    properties += "\nChildNodes: " + checkBox.ChildNodes;
}

properties += "\n";
```

## Krok 5: Spočítejte celkový počet ovládacích prvků ActiveX

Po iteraci všemi tvary spočítejte celkový počet nalezených ovládacích prvků ActiveX.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Krok 6: Zobrazení vlastností

Nakonec vypište extrahované vlastnosti do konzole.

```csharp
Console.WriteLine("\n" + properties);
```

## Závěr

tady to máte! Úspěšně jste se naučili, jak číst vlastnosti ovládacího prvku ActiveX z dokumentu Wordu pomocí Aspose.Words pro .NET. Tento tutoriál se zabýval načítáním dokumentu, procházením tvarů a extrakcí vlastností z ovládacích prvků ActiveX. Dodržením těchto kroků můžete automatizovat extrakci důležitých dat z dokumentů Wordu a zvýšit tak efektivitu svého pracovního postupu.

## Často kladené otázky

### Co jsou ovládací prvky ActiveX v dokumentech Wordu?
Ovládací prvky ActiveX jsou interaktivní objekty vložené do dokumentů aplikace Word, jako jsou zaškrtávací políčka, tlačítka a textová pole, které se používají k vytváření formulářů a automatizaci úloh.

### Mohu upravit vlastnosti ovládacích prvků ActiveX pomocí Aspose.Words pro .NET?
Ano, Aspose.Words pro .NET umožňuje programově upravovat vlastnosti ovládacích prvků ActiveX.

### Je Aspose.Words pro .NET zdarma k použití?
Aspose.Words pro .NET nabízí bezplatnou zkušební verzi, ale pro další používání si budete muset zakoupit licenci. Můžete získat bezplatnou zkušební verzi [zde](https://releases.aspose.com/).

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET kromě C#?
Ano, Aspose.Words pro .NET lze použít s jakýmkoli jazykem .NET, včetně VB.NET a F#.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
Podrobnou dokumentaci naleznete [zde](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}