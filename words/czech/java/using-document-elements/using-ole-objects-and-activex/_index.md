---
"description": "Naučte se používat objekty OLE a ovládací prvky ActiveX v Aspose.Words pro Javu. Snadno vytvářejte interaktivní dokumenty. Začněte hned teď!"
"linktitle": "Používání objektů OLE a ovládacích prvků ActiveX"
"second_title": "Rozhraní API pro zpracování dokumentů v Javě od Aspose.Words"
"title": "Používání objektů OLE a ovládacích prvků ActiveX v Aspose.Words pro Javu"
"url": "/cs/java/using-document-elements/using-ole-objects-and-activex/"
"weight": 21
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Používání objektů OLE a ovládacích prvků ActiveX v Aspose.Words pro Javu

tomto tutoriálu se podíváme na to, jak pracovat s objekty OLE (Object Linking and Embedding) a ovládacími prvky ActiveX v Aspose.Words pro Javu. Objekty OLE a ovládací prvky ActiveX jsou výkonné nástroje, které vám umožňují vylepšit vaše dokumenty vkládáním nebo propojováním externího obsahu, jako jsou tabulky, multimediální soubory nebo interaktivní ovládací prvky. Sledujte nás, jak se ponoříme do příkladů kódu a naučíme se tyto funkce efektivně používat.

### Předpoklady

Než začneme, ujistěte se, že máte splněny následující předpoklady:

1. Aspose.Words pro Javu: Ujistěte se, že máte ve svém projektu Java nainstalovanou knihovnu Aspose.Words. Můžete si ji stáhnout z [zde](https://releases.aspose.com/words/java/).

2. Vývojové prostředí Java: Na vašem systému byste měli mít nainstalované funkční vývojové prostředí Java.

### Vložení objektu OLE

Začněme vložením objektu OLE do dokumentu Wordu. Vytvoříme jednoduchý dokument Wordu a poté do něj vložíme objekt OLE představující webovou stránku.

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

V tomto kódu vytvoříme nový dokument a vložíme do něj objekt OLE, který zobrazuje webovou stránku Aspose. URL adresu můžete nahradit požadovaným obsahem.

### Vložení objektu OLE pomocí OlePackage

Dále se podíváme na to, jak vložit objekt OLE pomocí OlePackage. To vám umožní vložit externí soubory jako objekty OLE do dokumentu.

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

V tomto příkladu vkládáme objekt OLE pomocí OlePackage, což vám umožňuje zahrnout externí soubory jako vložené objekty.

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

V tomto kódu vkládáme objekt OLE jako ikonu, což poskytuje vizuálně atraktivnější reprezentaci vloženého obsahu.

### Čtení vlastností ovládacího prvku ActiveX

Nyní se zaměřme na ovládací prvky ActiveX. Naučíme se, jak číst vlastnosti ovládacích prvků ActiveX v dokumentu Wordu.

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

V tomto kódu iterujeme tvary v dokumentu Wordu, identifikujeme ovládací prvky ActiveX a načítáme jejich vlastnosti.

### Závěr

Gratulujeme! Naučili jste se pracovat s objekty OLE a ovládacími prvky ActiveX v Aspose.Words pro Javu. Tyto funkce otevírají svět možností pro vytváření dynamických a interaktivních dokumentů.

### Často kladené otázky

### K čemu slouží objekty OLE v dokumentu Wordu? 
   - Objekty OLE umožňují vkládat nebo propojovat externí obsah, například soubory nebo webové stránky, v rámci dokumentu aplikace Word.

### Mohu si přizpůsobit vzhled objektů OLE v dokumentu? 
   - Ano, vzhled objektů OLE si můžete přizpůsobit, včetně nastavení ikon a názvů souborů.

### Co jsou ovládací prvky ActiveX a jak mohou vylepšit mé dokumenty? 
   - Ovládací prvky ActiveX jsou interaktivní prvky, které mohou přidat funkce do dokumentů aplikace Word, například ovládací prvky formulářů nebo multimediální přehrávače.

### Je Aspose.Words pro Javu vhodný pro automatizaci dokumentů na podnikové úrovni? 
   - Ano, Aspose.Words pro Javu je výkonná knihovna pro automatizaci generování a manipulace s dokumenty v aplikacích Java.

### Kde mohu získat přístup k Aspose.Words pro Javu? 
   - Aspose.Words pro Javu si můžete stáhnout z [zde](https://releases.aspose.com/words/java/).

Začněte s Aspose.Words pro Javu ještě dnes a odemkněte plný potenciál automatizace a přizpůsobení dokumentů!



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}