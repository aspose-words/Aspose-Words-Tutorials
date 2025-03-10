---
title: Aspose.Words for Java'da OLE Nesneleri ve ActiveX Denetimlerini Kullanma
linktitle: OLE Nesneleri ve ActiveX Denetimlerini Kullanma
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java'da OLE nesnelerini ve ActiveX denetimlerini kullanmayı öğrenin. Kolayca etkileşimli belgeler oluşturun. Hemen başlayın!
weight: 21
url: /tr/java/using-document-elements/using-ole-objects-and-activex/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for Java'da OLE Nesneleri ve ActiveX Denetimlerini Kullanma

Bu eğitimde, Java için Aspose.Words'de OLE (Nesne Bağlama ve Gömme) nesneleri ve ActiveX denetimleriyle nasıl çalışılacağını keşfedeceğiz. OLE nesneleri ve ActiveX denetimleri, elektronik tablolar, multimedya dosyaları veya etkileşimli denetimler gibi harici içerikleri gömerek veya bağlayarak belgelerinizi geliştirmenize olanak tanıyan güçlü araçlardır. Kod örneklerini incelerken bizi takip edin ve bu özellikleri etkili bir şekilde nasıl kullanacağınızı öğrenin.

### Ön koşullar

Başlamadan önce aşağıdaki ön koşulların mevcut olduğundan emin olun:

1.  Java için Aspose.Words: Java projenizde Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Bunu şuradan indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/).

2. Java Geliştirme Ortamı: Sisteminizde çalışan bir Java geliştirme ortamının kurulu olması gerekir.

### Bir OLE Nesnesi Ekleme

Bir Word belgesine bir OLE nesnesi ekleyerek başlayalım. Basit bir Word belgesi oluşturacağız ve ardından bir web sayfasını temsil eden bir OLE nesnesi ekleyeceğiz.

```java
string outPath = "Your Output Directory";
public void insertOleObject() throws Exception
{
    Document doc = new Document();
    DocumentBuilder builder = new DocumentBuilder(doc);
    builder.insertOleObject("http://www.aspose.com", "htmldosyası", doğru, doğru, null);
    doc.save("Your Directory Path" + "WorkingWithOleObjectsAndActiveX.InsertOleObject.docx");
}
```

Bu kodda yeni bir belge oluşturuyoruz ve Aspose web sitesini görüntüleyen bir OLE nesnesi ekliyoruz. URL'yi istediğiniz içerikle değiştirebilirsiniz.

### OlePackage ile OLE Nesnesi Ekleme

Şimdi, bir OlePackage kullanarak bir OLE nesnesinin nasıl ekleneceğini inceleyelim. Bu, harici dosyaları belgenize OLE nesneleri olarak yerleştirmenize olanak tanır.

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

Bu örnekte, harici dosyaları gömülü nesneler olarak eklemenize olanak tanıyan bir OlePackage kullanarak bir OLE nesnesi ekliyoruz.

### Bir OLE Nesnesini Simge Olarak Ekleme

Şimdi, bir OLE nesnesinin simge olarak nasıl ekleneceğini görelim. Bu, gömülü bir dosyayı temsil eden bir simge görüntülemek istediğinizde faydalıdır.

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

Bu kodda, gömülü içeriğin görsel olarak daha çekici bir sunumunu sağlayan bir OLE nesnesini simge olarak ekliyoruz.

### ActiveX Denetim Özelliklerini Okuma

Şimdi, odak noktamızı ActiveX denetimlerine kaydıralım. Bir Word belgesindeki ActiveX denetimlerinin özelliklerini nasıl okuyacağımızı öğreneceğiz.

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

Bu kodda, bir Word belgesindeki şekiller arasında dolaşıyoruz, ActiveX denetimlerini tanımlıyoruz ve özelliklerini alıyoruz.

### Çözüm

Tebrikler! Aspose.Words for Java'da OLE nesneleri ve ActiveX denetimleriyle nasıl çalışacağınızı öğrendiniz. Bu özellikler dinamik ve etkileşimli belgeler oluşturmak için bir olasılıklar dünyasının kapılarını açar.

### SSS

### Word belgesinde OLE nesnelerinin amacı nedir? 
   - OLE nesneleri, dosyalar veya web sayfaları gibi harici içerikleri bir Word belgesine yerleştirmenize veya bunlara bağlantı vermenize olanak tanır.

### Belgemdeki OLE nesnelerinin görünümünü özelleştirebilir miyim? 
   - Evet, OLE nesnelerinin görünümünü, simgeleri ve dosya adlarını ayarlama dahil olmak üzere özelleştirebilirsiniz.

### ActiveX denetimleri nelerdir ve belgelerimi nasıl geliştirebilirler? 
   - ActiveX denetimleri, form denetimleri veya multimedya oynatıcılar gibi Word belgelerinize işlevsellik katabilen etkileşimli öğelerdir.

### Aspose.Words for Java kurumsal düzeyde belge otomasyonu için uygun mudur? 
   - Evet, Aspose.Words for Java, Java uygulamalarında belge oluşturma ve düzenlemeyi otomatikleştirmek için güçlü bir kütüphanedir.

### Aspose.Words for Java'ya nereden erişebilirim? 
   -  Java için Aspose.Words'ü şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/java/).

Bugün Aspose.Words for Java'yı kullanmaya başlayın ve belge otomasyonunun ve özelleştirmesinin tüm potansiyelini ortaya çıkarın!

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
