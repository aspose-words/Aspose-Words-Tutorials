---
title: Belge Oluşturucu Olmadan Alan Ekleme Metin Ekleme
linktitle: Belge Oluşturucu Olmadan FieldIncludeText Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET'te DocumentBuilder kullanmadan FieldIncludeText'in nasıl ekleneceğini ayrıntılı, adım adım kılavuzumuzla öğrenin.
weight: 10
url: /tr/net/working-with-fields/insert-field-include-text-without-document-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belge Oluşturucu Olmadan Alan Ekleme Metin Ekleme

## giriiş

Belge otomasyonu ve düzenleme dünyasında, Aspose.Words for .NET güçlü bir araç olarak öne çıkıyor. Bugün, DocumentBuilder kullanmadan FieldIncludeText'in nasıl ekleneceğine dair ayrıntılı bir kılavuza dalıyoruz. Bu eğitim, kodun her bir bölümünü ve amacını anlamanızı sağlayarak sizi adım adım süreçte yönlendirecektir.

## Ön koşullar

Koda dalmadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: En son sürümün yüklü olduğundan emin olun. Buradan indirebilirsiniz[Burada](https://releases.aspose.com/words/net/).
2. .NET Geliştirme Ortamı: Visual Studio gibi herhangi bir .NET uyumlu IDE.
3. Temel C# Bilgisi: C# programlamaya aşina olmanız, takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmamız gerekiyor. Bu ad alanları, Word belgelerini düzenlemek için gereken sınıflara ve yöntemlere erişim sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Fields;
```

Şimdi örneği birden fazla adıma bölelim. Her adım, netliği sağlamak için ayrıntılı olarak açıklanacaktır.

## Adım 1: Dizin Yolunu Ayarlayın

İlk adım, belgeler dizininize giden yolu tanımlamaktır. Word belgelerinizin saklanacağı ve erişileceği yer burasıdır.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Adım 2: Belgeyi ve Paragrafı Oluşturun

Sonra, yeni bir belge ve bu belgenin içinde bir paragraf oluşturuyoruz. Bu paragraf FieldIncludeText alanını tutacak.

```csharp
// Belgeyi ve paragrafı oluşturun.
Document doc = new Document();
Paragraph para = new Paragraph(doc);
```

## Adım 3: FieldIncludeText Alanını Ekle

Şimdi, FieldIncludeText alanını paragrafa ekliyoruz. Bu alan, başka bir belgeden metin eklemenize olanak tanır.

```csharp
// FieldIncludeText alanını ekleyin.
FieldIncludeText fieldIncludeText = (FieldIncludeText)para.AppendField(FieldType.FieldIncludeText, false);
```

## Adım 4: Alan Özelliklerini Ayarlayın

FieldIncludeText alanı için özellikleri belirtmemiz gerekiyor. Bu, yer imi adını ve kaynak belgenin tam yolunu ayarlamayı içerir.

```csharp
fieldIncludeText.BookmarkName = "bookmark";
fieldIncludeText.SourceFullName = dataDir + "IncludeText.docx";
```

## Adım 5: Belgeye Paragraf Ekle

Alan ayarlandıktan sonra paragrafı belgenin ilk bölüm gövdesine ekliyoruz.

```csharp
doc.FirstSection.Body.AppendChild(para);
```

## Adım 6: Alanı Güncelle

Belgeyi kaydetmeden önce, kaynak belgeden doğru içeriği çektiğinden emin olmak için FieldIncludeText'i güncellememiz gerekiyor.

```csharp
fieldIncludeText.Update();
```

## Adım 7: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydediyoruz.

```csharp
doc.Save(dataDir + "InsertionFieldFieldIncludeTextWithoutDocumentBuilder.docx");
```

## Çözüm

Ve işte oldu! Bu adımları izleyerek, .NET için Aspose.Words'de DocumentBuilder kullanmadan kolayca bir FieldIncludeText ekleyebilirsiniz. Bu yaklaşım, bir belgeden diğerine içerik eklemenin kolaylaştırılmış bir yolunu sunarak belge otomasyon görevlerinizi çok daha basit hale getirir.

## SSS

### Aspose.Words for .NET nedir?  
Aspose.Words for .NET, .NET uygulamalarında Word belgeleriyle çalışmak için güçlü bir kütüphanedir. Belgeleri programatik olarak oluşturmanıza, düzenlemenize ve dönüştürmenize olanak tanır.

### FieldIncludeText'i neden kullanmalısınız?  
FieldIncludeText, bir belgeden diğerine içerikleri dinamik olarak eklemek için kullanışlıdır ve daha modüler ve sürdürülebilir belgeler sağlar.

### Bu yöntemi diğer dosya biçimlerinden metin eklemek için kullanabilir miyim?  
FieldIncludeText özellikle Word belgeleriyle çalışır. Diğer biçimler için Aspose.Words tarafından sağlanan farklı yöntemlere veya sınıflara ihtiyacınız olabilir.

### Aspose.Words for .NET, .NET Core ile uyumlu mudur?  
Evet, Aspose.Words for .NET, .NET Framework, .NET Core ve .NET 5/6'yı destekler.

### Aspose.Words for .NET'in ücretsiz deneme sürümünü nasıl edinebilirim?  
 Ücretsiz deneme sürümünü şuradan alabilirsiniz:[Burada](https://releases.aspose.com/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
