---
"description": "Bu kılavuzla Aspose.Words for .NET'te alan güncelleme kültür kaynağını nasıl değiştireceğinizi öğrenin. Farklı kültürlere göre tarih biçimlendirmesini kolayca kontrol edin."
"linktitle": "Alan Değiştir Kültür Kaynağını Güncelle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Alan Değiştir Kültür Kaynağını Güncelle"
"url": "/tr/net/working-with-fields/change-field-update-culture-source/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Alan Değiştir Kültür Kaynağını Güncelle

## giriiş

Bu eğitimde, .NET için Aspose.Words dünyasına dalacağız ve alan güncelleme kültürü kaynağının nasıl değiştirileceğini keşfedeceğiz. Tarih alanları içeren Word belgeleriyle uğraşıyorsanız ve bu tarihlerin farklı kültürlere göre nasıl biçimlendirileceğini kontrol etmeniz gerekiyorsa, bu kılavuz tam size göre. Her kavramı kavradığınızdan ve projelerinizde etkili bir şekilde uygulayabildiğinizden emin olarak süreci adım adım inceleyelim.

## Ön koşullar

Koda geçmeden önce aşağıdakilerin mevcut olduğundan emin olun:

- Aspose.Words for .NET: Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Herhangi bir .NET uyumlu IDE (örneğin, Visual Studio).
- Temel C# Bilgisi: Bu eğitimde C# programlama hakkında temel bir anlayışa sahip olduğunuzu varsayıyoruz.

## Ad Alanlarını İçe Aktar

Öncelikle projemiz için gerekli ad alanlarını içe aktaralım. Bu, Aspose.Words tarafından sağlanan tüm gerekli sınıflara ve yöntemlere erişimimizin olmasını sağlayacaktır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Şimdi, Aspose.Words for .NET'te alan güncelleme kültürü kaynağının nasıl değiştirileceğini anlamanıza yardımcı olmak için örneği birden fazla adıma bölelim.

## Adım 1: Belgeyi Başlatın

İlk adım, yeni bir örnek oluşturmaktır `Document` sınıf ve bir `DocumentBuilder`Bu, Word belgemizi oluşturmak ve düzenlemek için temel oluşturur.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Belirli Yerel Ayarlara Sahip Alanları Ekle

Sonra, belgeye alanlar eklememiz gerekiyor. Bu örnek için iki tarih alanı ekleyeceğiz. Kültürün tarih biçimini nasıl etkilediğini göstermek için yazı tipinin yerel ayarını Almanca (LocaleId = 1031) olarak ayarlayacağız.

```csharp
builder.Font.LocaleId = 1031; // Almanca
builder.InsertField("MERGEFIELD Date1 \\@ \"dddd, d MMMM yyyy\"");
builder.Write(" - ");
builder.InsertField("MERGEFIELD Date2 \\@ \"dddd, d MMMM yyyy\"");
```

## Adım 3: Alan Güncelleme Kültür Kaynağını Ayarla

Alanları güncellerken kullanılan kültürü kontrol etmek için, `FieldUpdateCultureSource` mülkiyeti `FieldOptions` sınıf. Bu özellik kültürün alan kodundan mı yoksa belgeden mi alındığını belirler.

```csharp
doc.FieldOptions.FieldUpdateCultureSource = FieldUpdateCultureSource.FieldCode;
```

## Adım 4: Posta Birleştirmeyi Çalıştırın

Şimdi alanları gerçek verilerle doldurmak için bir posta birleştirme işlemi yapmamız gerekiyor. Bu örnekte, ikinci tarih alanını (`Date2`) 1 Ocak 2011'e kadar.

```csharp
doc.MailMerge.Execute(new string[] { "Date2" }, new object[] { new DateTime(2011, 1, 1) });
```

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi belirtilen dizine kaydediyoruz. Bu adım, alan güncelleme kültürü kaynağını değiştirme sürecini tamamlar.

```csharp
doc.Save(dataDir + "WorkingWithFields.ChangeFieldUpdateCultureSource.docx");
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET'te alan güncelleme kültür kaynağını başarıyla değiştirdiniz. Bu adımları izleyerek, Word belgelerinizin tarihleri ve diğer alan değerlerini belirtilen kültür ayarlarına göre görüntülemesini sağlayabilirsiniz. Bu, özellikle uluslararası bir kitle için belgeler oluştururken yararlı olabilir.

## SSS

### Bu ayarın amacı nedir? `LocaleId`?
The `LocaleId` Metnin kültür ayarlarını belirtir; bu ayarlar tarihlerin ve diğer yerel ayarlara duyarlı verilerin nasıl biçimlendirileceğini etkiler.

### Almanca dışında farklı bir yerel ayar kullanabilir miyim?
Evet, ayarlayabilirsiniz `LocaleId` herhangi bir geçerli yerel tanımlayıcıya. Örneğin, İngilizce (ABD) için 1033.

### Ayarlamazsam ne olur? `FieldUpdateCultureSource` mülk?
Bu özellik ayarlanmazsa, alanlar güncellenirken belgenin varsayılan kültür ayarları kullanılır.

### Alan kodu yerine belgenin kültürüne göre alanları güncellemek mümkün müdür?
Evet, ayarlayabilirsiniz `FieldUpdateCultureSource` ile `FieldUpdateCultureSource.Document` Belgenin kültür ayarlarını kullanmak için.

### Tarihleri farklı bir desende nasıl biçimlendirebilirim?
Tarih biçimi desenini şurada değiştirebilirsiniz: `InsertField` yöntemi değiştirerek `\\@` anahtar değeri.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}