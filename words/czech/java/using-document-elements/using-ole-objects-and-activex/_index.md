---
title: Použití objektů OLE a ovládacích prvků ActiveX v Aspose.Words for Java
linktitle: Použití objektů OLE a ovládacích prvků ActiveX
second_title: Aspose.Words Java Document Processing API
description: Naučte se používat OLE objekty a ovládací prvky ActiveX v Aspose.Words for Java. Vytvářejte snadno interaktivní dokumenty. Začněte hned!
weight: 21
url: /cs/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Použití objektů OLE a ovládacích prvků ActiveX v Aspose.Words for Java

V tomto tutoriálu prozkoumáme, jak pracovat s objekty OLE (Object Linking and Embedding) a ovládacími prvky ActiveX v Aspose.Words for Java. Objekty OLE a ovládací prvky ActiveX jsou výkonné nástroje, které umožňují vylepšit vaše dokumenty vložením nebo propojením externího obsahu, jako jsou tabulky, multimediální soubory nebo interaktivní ovládací prvky. Pokračujte, jak se ponoříme do příkladů kódu a naučíme se, jak tyto funkce efektivně používat.

### Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1.  Aspose.Words for Java: Ujistěte se, že máte v projektu Java nainstalovanou knihovnu Aspose.Words. Můžete si jej stáhnout z[zde](https://releases.aspose.com/words/java/).

2. Vývojové prostředí Java: Ve vašem systému byste měli mít nastavené funkční vývojové prostředí Java.

### Vložení objektu OLE

Začněme vložením objektu OLE do dokumentu aplikace Word. Vytvoříme jednoduchý dokument Word a poté vložíme OLE objekt představující webovou stránku.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmlsoubor", true, true, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

V tomto kódu vytvoříme nový dokument a vložíme OLE objekt, který zobrazí web Aspose. Adresu URL můžete nahradit požadovaným obsahem.

### Vložení objektu OLE s OlePackage

Dále prozkoumáme, jak vložit objekt OLE pomocí OlePackage. To vám umožní vložit externí soubory jako objekty OLE do vašeho dokumentu.

```java
@Test
public void insertOleObjectWithOlePackage() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    byte[] bs = FileUtils.readFileToByteArray(new File("Your Directory Path" + "Zip file.zip"));
    try (ByteArrayInputStream stream = new ByteArrayInputStream(bs))
    {
        Shape shape = builder.insertOleObject(stream, "Package", true, null);
        OlePackage olePackage = shape.getOleFormat().getOlePackage();
        olePackage.setFileName("filename.zip");
        olePackage.setDisplayName("displayname.zip");
        doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
    }
}
```

tomto příkladu vložíme objekt OLE pomocí balíčku OlePackage, který vám umožní zahrnout externí soubory jako vložené objekty.

### Vložení objektu OLE jako ikony

Nyní se podívejme, jak vložit objekt OLE jako ikonu. To je užitečné, když chcete zobrazit ikonu představující vložený soubor.

```java
@Test
public void insertOleObjectAsIcon() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObjectAsIcon("Your Directory Path" + "Presentation.pptx", false, getImagesDir() + "Logo icon.ico", "My embedded file");
    doc.save(outPath + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIcon.docx");
}
```

V tomto kódu vložíme objekt OLE jako ikonu, která poskytuje vizuálně atraktivnější reprezentaci vloženého obsahu.

### Čtení vlastností ovládacího prvku ActiveX

Nyní se zaměřme na ovládací prvky ActiveX. Naučíme se číst vlastnosti ovládacích prvků ActiveX v dokumentu aplikace Word.

```java
@Test
public void readActiveXControlProperties() throws Exception
{
    Document doc = new Document("Your Directory Path" + "ActiveX controls.docx");
    String properties = "";
    for (Shape shape : (Iterable<Shape>) doc.getChildNodes(NodeType.SHAPE, true))
    {
        if (shape.getOleFormat() == null) break;
        OleControl oleControl = shape.getOleFormat().getOleControl();
        if (oleControl.isForms2OleControl())
        {
            Forms2OleControl checkBox = (Forms2OleControl) oleControl;
            properties = properties + "\nCaption: " + checkBox.getCaption();
            properties = properties + "\nValue: " + checkBox.getValue();
            properties = properties + "\nEnabled: " + checkBox.getEnabled();
            properties = properties + "\nType: " + checkBox.getType();
            if (checkBox.getChildNodes() != null)
            {
                properties = properties + "\nChildNodes: " + checkBox.getChildNodes();
            }
            properties += "\n";
        }
    }
    properties = properties + "\nTotal ActiveX Controls found: " + doc.getChildNodes(NodeType.SHAPE, true).getCount();
    System.out.println("\n" + properties);
}
```

V tomto kódu procházíme tvary v dokumentu aplikace Word, identifikujeme ovládací prvky ActiveX a získáváme jejich vlastnosti.

### Závěr

Gratuluji! Naučili jste se pracovat s objekty OLE a ovládacími prvky ActiveX v Aspose.Words for Java. Tyto funkce otevírají svět možností pro vytváření dynamických a interaktivních dokumentů.

### Nejčastější dotazy

### Jaký je účel objektů OLE v dokumentu aplikace Word? 
   - Objekty OLE umožňují vložit nebo propojit externí obsah, jako jsou soubory nebo webové stránky, do dokumentu aplikace Word.

### Mohu upravit vzhled objektů OLE v mém dokumentu? 
   - Ano, vzhled objektů OLE můžete přizpůsobit, včetně nastavení ikon a názvů souborů.

### Co jsou ovládací prvky ActiveX a jak mohou vylepšit mé dokumenty? 
   - Ovládací prvky ActiveX jsou interaktivní prvky, které mohou přidávat funkce do dokumentů aplikace Word, jako jsou ovládací prvky formulářů nebo multimediální přehrávače.

### Je Aspose.Words for Java vhodný pro automatizaci dokumentů na podnikové úrovni? 
   - Ano, Aspose.Words for Java je výkonná knihovna pro automatizaci generování dokumentů a manipulaci s nimi v aplikacích Java.

### Kde mohu získat přístup k Aspose.Words for Java? 
   -  Aspose.Words for Java si můžete stáhnout z[zde](https://releases.aspose.com/words/java/).

Začněte s Aspose.Words for Java ještě dnes a odemkněte plný potenciál automatizace a přizpůsobení dokumentů!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
