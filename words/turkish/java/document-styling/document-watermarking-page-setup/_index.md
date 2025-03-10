---
title: Belge Filigranlama ve Sayfa Düzeni
linktitle: Belge Filigranlama ve Sayfa Düzeni
second_title: Aspose.Words Java Belge İşleme API'si
description: Aspose.Words for Java ile filigranların nasıl uygulanacağını ve sayfa yapılandırmalarının nasıl ayarlanacağını öğrenin. Kaynak kodlu kapsamlı bir kılavuz.
weight: 13
url: /tr/java/document-styling/document-watermarking-page-setup/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belge Filigranlama ve Sayfa Düzeni

## giriiş

Belge düzenleme alanında, Aspose.Words for Java, geliştiricilerin belge işlemenin her yönü üzerinde kontrol sahibi olmasını sağlayan güçlü bir araç olarak öne çıkıyor. Bu kapsamlı kılavuzda, Aspose.Words for Java kullanarak belge filigranlama ve sayfa kurulumunun inceliklerini inceleyeceğiz. İster deneyimli bir geliştirici olun, ister Java belge işleme dünyasına yeni adım atıyor olun, bu adım adım kılavuz size ihtiyaç duyduğunuz bilgi ve kaynak kodunu sağlayacaktır.

## Belge Filigranlama

### Filigran Ekleme

Belgelere filigran eklemek, markalaşma veya içeriğinizin güvenliğini sağlama açısından kritik olabilir. Java için Aspose.Words bu görevi kolaylaştırır. İşte nasıl:

```java
// Belgeyi yükle
Document doc = new Document("document.docx");

// Bir filigran oluşturun
Shape watermark = new Shape(doc, ShapeType.TEXT_PLAIN_TEXT);
watermark.getTextPath().setText("Confidential");
watermark.setWidth(300);
watermark.setHeight(100);

// Filigranı konumlandırın
watermark.setRelativeHorizontalPosition(RelativeHorizontalPosition.PAGE);
watermark.setRelativeVerticalPosition(RelativeVerticalPosition.PAGE);
watermark.setWrapType(WrapType.NONE);
watermark.setVerticalAlignment(VerticalAlignment.CENTER);
watermark.setHorizontalAlignment(HorizontalAlignment.CENTER);

// Filigranı ekle
doc.getFirstSection().getBody().getFirstParagraph().appendChild(watermark);

// Belgeyi kaydet
doc.save("document_with_watermark.docx");
```

### Filigranları Özelleştirme

Yazı tipini, boyutunu, rengini ve dönüşünü ayarlayarak filigranları daha da özelleştirebilirsiniz. Bu esneklik, filigranınızın belgenizin stiline kusursuz bir şekilde uymasını sağlar.

## Sayfa Düzeni

### Sayfa Boyutu ve Yönlendirme

Sayfa düzeni belge biçimlendirmede çok önemlidir. Aspose.Words for Java, sayfa boyutu ve yönü üzerinde tam kontrol sağlar:

```java
// Belgeyi yükle
Document doc = new Document("document.docx");

// Sayfa boyutunu A4 olarak ayarla
doc.getFirstSection().getPageSetup().setPageWidth(595.0);
doc.getFirstSection().getPageSetup().setPageHeight(842.0);

// Sayfa yönünü yatay olarak değiştir
doc.getFirstSection().getPageSetup().setOrientation(Orientation.LANDSCAPE);

// Değiştirilen belgeyi kaydet
doc.save("formatted_document.docx");
```

### Kenar Boşlukları ve Sayfa Numaralandırması

Profesyonel belgeler için kenar boşlukları ve sayfa numaralandırması üzerinde hassas kontrol esastır. Bunu Java için Aspose.Words ile elde edin:

```java
// Belgeyi yükle
Document doc = new Document("document.docx");

// Kenar boşluklarını ayarlayın
doc.getFirstSection().getPageSetup().setLeftMargin(72.0);
doc.getFirstSection().getPageSetup().setRightMargin(72.0);
doc.getFirstSection().getPageSetup().setTopMargin(72.0);
doc.getFirstSection().getPageSetup().setBottomMargin(72.0);

// Sayfa numaralandırmayı etkinleştir
doc.getFirstSection().getPageSetup().setDifferentFirstPageHeaderFooter(true);
HeaderFooter firstPageHeader = doc.getFirstSection().getHeadersFooters().getByHeaderFooterType(HeaderFooterType.HEADER_FIRST);
firstPageHeader.appendParagraph("First Page Header");

// Biçimlendirilmiş belgeyi kaydedin
doc.save("formatted_document.docx");
```

## SSS

### Bir belgeden filigranı nasıl kaldırabilirim?

Bir belgeden filigranı kaldırmak için, belgenin şekilleri arasında dolaşabilir ve filigranları temsil edenleri kaldırabilirsiniz. İşte bir kesit:

```java
Document doc = new Document("document_with_watermark.docx");

for (Shape shape : doc.getChildNodes(NodeType.SHAPE, true).<Shape>toArray()) {
    if (shape.getText().contains("Confidential")) {
        shape.remove();
    }
}

doc.save("document_without_watermark.docx");
```

### Tek bir belgeye birden fazla filigran ekleyebilir miyim?

Evet, ek Şekil nesneleri oluşturup bunları gerektiği gibi konumlandırarak bir belgeye birden fazla filigran ekleyebilirsiniz.

### Yatay yönde sayfa boyutunu yasal boyuta nasıl değiştirebilirim?

Yatay yönde sayfa boyutunu yasal olarak ayarlamak için sayfa genişliğini ve yüksekliğini aşağıdaki gibi değiştirin:

```java
doc.getFirstSection().getPageSetup().setPageWidth(842.0);
doc.getFirstSection().getPageSetup().setPageHeight(595.0);
```

### Filigranlar için varsayılan yazı tipi nedir?

Filigranlar için varsayılan yazı tipi Calibri'dir ve yazı tipi boyutu 36'dır.

### Belirli bir sayfadan başlayarak sayfa numaraları nasıl ekleyebilirim?

Bunu, belgenizde başlangıç sayfa numarasını aşağıdaki şekilde ayarlayarak başarabilirsiniz:

```java
doc.getFirstSection().getPageSetup().setPageStartingNumber(5);
```

### Üstbilgi veya altbilgideki metni nasıl ortaya hizalarım?

Başlık veya altbilgideki metni, başlık veya altbilgideki Paragraf nesnesinde setAlignment yöntemini kullanarak ortaya hizalayabilirsiniz.

## Çözüm

Bu kapsamlı kılavuzda, Aspose.Words for Java kullanarak belge filigranlama ve sayfa kurulumu sanatını inceledik. Sağlanan kaynak kodu parçacıkları ve içgörülerle donanmış olarak, artık belgelerinizi ustalıkla düzenlemek ve biçimlendirmek için araçlara sahipsiniz. Aspose.Words for Java, tam olarak özelliklerinize göre uyarlanmış profesyonel, markalı belgeler oluşturmanızı sağlar.

Belge düzenlemede ustalaşmak geliştiriciler için değerli bir beceridir ve Aspose.Words for Java bu yolculukta güvendiğiniz arkadaşınızdır. Bugün çarpıcı belgeler oluşturmaya başlayın!
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
