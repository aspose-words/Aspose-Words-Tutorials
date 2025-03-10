---
title: Číst vlastnosti Active XControl ze souboru aplikace Word
linktitle: Číst vlastnosti Active XControl ze souboru aplikace Word
second_title: Aspose.Words API pro zpracování dokumentů
description: Naučte se číst vlastnosti ovládacího prvku ActiveX ze souborů aplikace Word pomocí Aspose.Words for .NET v podrobném průvodci. Vylepšete své dovednosti v oblasti automatizace dokumentů.
weight: 10
url: /cs/net/working-with-oleobjects-and-activex/read-active-xcontrol-properties/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Číst vlastnosti Active XControl ze souboru aplikace Word

## Zavedení

V dnešní digitální době je automatizace klíčem ke zvýšení produktivity. Pokud pracujete s dokumenty aplikace Word, které obsahují ovládací prvky ActiveX, možná budete muset pro různé účely přečíst jejich vlastnosti. Ovládací prvky ActiveX, jako jsou zaškrtávací políčka a tlačítka, mohou obsahovat důležitá data. Pomocí Aspose.Words for .NET můžete tato data efektivně extrahovat a programově s nimi manipulovat.

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1.  Aspose.Words for .NET Library: Můžete si ji stáhnout z[zde](https://releases.aspose.com/words/net/).
2. Visual Studio nebo jakékoli C# IDE: Chcete-li napsat a spustit váš kód.
3. Dokument aplikace Word s ovládacími prvky ActiveX: Například „ovládací prvky ActiveX.docx“.
4. Základní znalost C#: Nutná je znalost programování v C#.

## Importovat jmenné prostory

Nejprve importujme potřebné jmenné prostory pro práci s Aspose.Words pro .NET.

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Drawing.Ole;
using System;
```

## Krok 1: Načtěte dokument aplikace Word

Chcete-li začít, budete muset načíst dokument aplikace Word, který obsahuje ovládací prvky ActiveX.

```csharp
// Cesta k vašemu adresáři dokumentů
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "ActiveX controls.docx");
```

## Krok 2: Inicializujte vlastnosti řetězce pro podržení

Dále inicializujte prázdný řetězec pro uložení vlastností ovládacích prvků ActiveX.

```csharp
string properties = "";
```

## Krok 3: Opakujte tvary v dokumentu

Abychom našli ovládací prvky ActiveX, musíme iterovat všechny obrazce v dokumentu.

```csharp
foreach (Shape shape in doc.GetChildNodes(NodeType.Shape, true))
{
    if (shape.OleFormat is null) continue;
    
    OleControl oleControl = shape.OleFormat.OleControl;
    if (oleControl.IsForms2OleControl)
    {
        // Zpracujte ovládací prvek ActiveX
    }
}
```

## Krok 4: Extrahujte vlastnosti z ovládacích prvků ActiveX

V rámci smyčky zkontrolujte, zda je ovládací prvek Forms2OleControl. Pokud ano, odlijte jej a extrahujte vlastnosti.

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

## Krok 5: Spočítat celkový počet ovládacích prvků ActiveX

Po procházení všemi tvary spočítejte celkový počet nalezených ovládacích prvků ActiveX.

```csharp
properties += "\nTotal ActiveX Controls found: " + doc.GetChildNodes(NodeType.Shape, true).Count;
```

## Krok 6: Zobrazte vlastnosti

Nakonec vytiskněte extrahované vlastnosti do konzoly.

```csharp
Console.WriteLine("\n" + properties);
```

## Závěr

tady to máte! Úspěšně jste se naučili číst vlastnosti ovládacího prvku ActiveX z dokumentu aplikace Word pomocí Aspose.Words for .NET. Tento kurz se zabýval načítáním dokumentu, iterací tvarů a extrahováním vlastností z ovládacích prvků ActiveX. Pomocí těchto kroků můžete zautomatizovat extrakci důležitých dat z dokumentů aplikace Word a zvýšit efektivitu pracovního postupu.

## FAQ

### Co jsou ovládací prvky ActiveX v dokumentech aplikace Word?
Ovládací prvky ActiveX jsou interaktivní objekty vložené do dokumentů aplikace Word, jako jsou zaškrtávací políčka, tlačítka a textová pole, používané k vytváření formulářů a automatizaci úloh.

### Mohu upravit vlastnosti ovládacích prvků ActiveX pomocí Aspose.Words for .NET?
Ano, Aspose.Words for .NET umožňuje programově upravovat vlastnosti ovládacích prvků ActiveX.

### Je Aspose.Words for .NET zdarma k použití?
 Aspose.Words for .NET nabízí bezplatnou zkušební verzi, ale pro další používání si budete muset zakoupit licenci. Můžete získat bezplatnou zkušební verzi[zde](https://releases.aspose.com/).

### Mohu používat Aspose.Words pro .NET s jinými jazyky .NET kromě C#?
Ano, Aspose.Words for .NET lze použít s jakýmkoli jazykem .NET, včetně VB.NET a F#.

### Kde najdu další dokumentaci k Aspose.Words pro .NET?
 Můžete najít podrobnou dokumentaci[zde](https://reference.aspose.com/words/net/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
