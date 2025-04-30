---
"description": "Naučte se, jak importovat dokumenty se zachováním formátování pomocí Aspose.Words pro .NET. Podrobný návod s příklady kódu."
"linktitle": "Zachovat číslování zdrojů"
"second_title": "Rozhraní API pro zpracování dokumentů Aspose.Words"
"title": "Zachovat číslování zdrojů"
"url": "/cs/net/join-and-append-documents/keep-source-numbering/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Zachovat číslování zdrojů

## Zavedení

Při práci s Aspose.Words pro .NET lze efektivně zvládnout import dokumentů z jednoho zdroje do druhého se zachováním formátování pomocí... `NodeImporter` třída. Tento tutoriál vás krok za krokem provede celým procesem.

## Předpoklady

Než začnete, ujistěte se, že máte následující:
- Visual Studio nainstalované na vašem počítači.
- Aspose.Words pro .NET je nainstalován. Pokud ne, stáhněte si ho z [zde](https://releases.aspose.com/words/net/).
- Základní znalost programování v C# a .NET.

## Importovat jmenné prostory

Nejprve do projektu zahrňte potřebné jmenné prostory:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

## Krok 1: Nastavení projektu

Začněte vytvořením nového projektu C# ve Visual Studiu a nainstalujte Aspose.Words pomocí Správce balíčků NuGet.

## Krok 2: Inicializace dokumentů
Vytvořit instance zdroje (`srcDoc`) a cíl (`dstDoc`) dokumenty.

```csharp
// Cesta k adresáři s dokumenty 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Krok 3: Konfigurace možností importu
Nastavte možnosti importu tak, aby zachovaly formátování zdroje, včetně číslovaných odstavců.

```csharp
ImportFormatOptions importFormatOptions = new ImportFormatOptions { KeepSourceNumbering = true };
NodeImporter importer = new NodeImporter(srcDoc, dstDoc, ImportFormatMode.KeepSourceFormatting,
	importFormatOptions);
```

## Krok 4: Import odstavců
Projděte si odstavce ve zdrojovém dokumentu a importujte je do cílového dokumentu.

```csharp
ParagraphCollection srcParas = srcDoc.FirstSection.Body.Paragraphs;
foreach (Paragraph srcPara in srcParas)
{
    Node importedNode = importer.ImportNode(srcPara, false);
    dstDoc.FirstSection.Body.AppendChild(importedNode);
}
```

## Krok 5: Uložte dokument
Uložte sloučený dokument na požadované místo.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.KeepSourceNumbering.docx");
```

## Závěr

Závěrem lze říci, že použití Aspose.Words pro .NET k importu dokumentů se zachováním formátování je srozumitelné. `NodeImporter` třída. Tato metoda zajišťuje, že si vaše dokumenty bez problémů zachovají svůj původní vzhled a strukturu.

## Často kladené otázky

### Mohu importovat dokumenty s různými styly formátování?
Ano, `NodeImporter` třída podporuje import dokumentů s různými styly formátování.

### Co když mé dokumenty obsahují složité tabulky a obrázky?
Aspose.Words pro .NET zpracovává během importu složité struktury, jako jsou tabulky a obrázky.

### Je Aspose.Words kompatibilní se všemi verzemi .NET?
Aspose.Words podporuje verze .NET Framework a .NET Core pro bezproblémovou integraci.

### Jak mohu ošetřit chyby během importu dokumentu?
Pro zpracování výjimek, které mohou nastat během procesu importu, použijte bloky try-catch.

### Kde najdu podrobnější dokumentaci k Aspose.Words pro .NET?
Navštivte [dokumentace](https://reference.aspose.com/words/net/) pro komplexní průvodce a reference API.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}