---
"description": "Naučte se, jak vkládat objekty OLE do dokumentů Wordu pomocí Aspose.Words pro .NET. Postupujte podle našeho podrobného návodu krok za krokem a vkládejte soubory bez problémů."
"linktitle": "Vložení objektu Ole do Wordu pomocí balíčku Ole"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Vložení objektu Ole do Wordu pomocí balíčku Ole"
"url": "/cs/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Vložení objektu Ole do Wordu pomocí balíčku Ole

## Zavedení

Pokud jste někdy chtěli vložit soubor do dokumentu Wordu, jste na správném místě. Ať už se jedná o soubor ZIP, excelový list nebo jakýkoli jiný typ souboru, jeho vložení přímo do dokumentu Wordu může být neuvěřitelně užitečné. Představte si to jako tajnou přihrádku v dokumentu, kam si můžete uložit nejrůznější poklady. A dnes si ukážeme, jak to udělat pomocí Aspose.Words pro .NET. Jste připraveni stát se mágem Wordu? Pojďme se do toho pustit!

## Předpoklady

Než začneme, ujistěte se, že máte následující:

1. Aspose.Words pro .NET: Pokud jste tak ještě neučinili, stáhněte si jej z [zde](https://releases.aspose.com/words/net/).
2. Vývojové prostředí: Visual Studio nebo jakékoli jiné vývojové prostředí pro .NET.
3. Základní znalost C#: Nemusíte být expert, ale znalost C# vám pomůže.
4. Adresář dokumentů: Složka, kde můžete ukládat a vyhledávat dokumenty.

## Importovat jmenné prostory

Nejdříve si ujasníme jmenné prostory. Do projektu je třeba zahrnout následující jmenné prostory:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Rozdělme si to na několik kroků, aby se vám to snadno dařilo.

## Krok 1: Nastavení dokumentu

Představte si, že jste umělec s prázdným plátnem. Nejprve potřebujeme prázdné plátno, což je náš dokument Word. Zde je návod, jak ho nastavit:

```csharp
// Cesta k adresáři s dokumenty
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Tento kód inicializuje nový dokument Wordu a nastavuje DocumentBuilder, který použijeme k vložení obsahu do našeho dokumentu.

## Krok 2: Přečtěte si svůj objekt Ole

Dále si přečtěme soubor, který chcete vložit. Představte si to jako sbírání pokladu, který chcete schovat ve své tajné přihrádce:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Tento řádek přečte všechny bajty z vašeho ZIP souboru a uloží je do bajtového pole.

## Krok 3: Vložení objektu Ole

A teď přichází ta magická část. Soubor vložíme do našeho dokumentu Wordu:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

Zde vytvoříme paměťový proud z bajtového pole a použijeme `InsertOleObject` metodu pro vložení do dokumentu. Také nastavíme název souboru a zobrazovaný název pro vložený objekt.

## Krok 4: Uložte dokument

Nakonec si uložme naše mistrovské dílo:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Tím se dokument s vloženým souborem uloží do zadaného adresáře.

## Závěr

A tady to máte! Úspěšně jste vložili objekt OLE do dokumentu Wordu pomocí Aspose.Words pro .NET. Je to jako byste do dokumentu přidali skrytý klenot, který můžete kdykoli odhalit. Tato technika může být neuvěřitelně užitečná pro řadu aplikací, od technické dokumentace až po dynamické reporty. 

## Často kladené otázky

### Mohu touto metodou vkládat i jiné typy souborů?
Ano, můžete vkládat různé typy souborů, jako jsou excelovské listy, PDF soubory a obrázky.

### Potřebuji licenci pro Aspose.Words?
Ano, potřebujete platný řidičský průkaz. Můžete získat [dočasná licence](https://purchase.aspose.com/temporary-license/) pro hodnocení.

### Jak mohu přizpůsobit zobrazovaný název objektu OLE?
Můžete nastavit `DisplayName` majetek `OlePackage` přizpůsobit si ho.

### Je Aspose.Words kompatibilní s .NET Core?
Ano, Aspose.Words podporuje .NET Framework i .NET Core.

### Mohu upravovat vložený objekt OLE v dokumentu Wordu?
Ne, objekt OLE nelze upravovat přímo ve Wordu. Musíte ho otevřít v jeho nativní aplikaci.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}