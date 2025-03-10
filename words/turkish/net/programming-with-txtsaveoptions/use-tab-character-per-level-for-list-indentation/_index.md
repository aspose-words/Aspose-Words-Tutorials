---
title: Liste Girintisi İçin Seviye Başına Sekme Karakteri Kullan
linktitle: Liste Girintisi İçin Seviye Başına Sekme Karakteri Kullan
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak sekmeli girintili çok düzeyli listeler oluşturmayı öğrenin. Belgelerinizde hassas liste biçimlendirmesi için bu kılavuzu izleyin.
weight: 10
url: /tr/net/programming-with-txtsaveoptions/use-tab-character-per-level-for-list-indentation/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Liste Girintisi İçin Seviye Başına Sekme Karakteri Kullan

## giriiş

İster bir rapor taslağı hazırlayın, ister bir araştırma makalesi yazın veya bir sunum hazırlayın, listeler içerik düzenlemede temeldir. Ancak, birden fazla girinti düzeyine sahip listeleri sunmaya gelince, istenen biçimi elde etmek biraz zor olabilir. .NET için Aspose.Words'ü kullanarak, liste girintilerini kolayca yönetebilir ve her düzeyin nasıl temsil edildiğini özelleştirebilirsiniz. Bu eğitimde, hassas biçimlendirme için sekme karakterlerini kullanarak birden fazla girinti düzeyine sahip bir liste oluşturmaya odaklanacağız. Bu kılavuzun sonunda, belgenizi doğru girinti stiliyle nasıl ayarlayacağınız ve kaydedeceğiniz konusunda net bir anlayışa sahip olacaksınız.

## Ön koşullar

Adımlara geçmeden önce aşağıdakilerin hazır olduğundan emin olun:

1.  .NET için Aspose.Words Yüklendi: Aspose.Words kütüphanesine ihtiyacınız var. Henüz yüklemediyseniz, şuradan indirebilirsiniz:[Aspose İndirmeleri](https://releases.aspose.com/words/net/).

2. C# ve .NET'in Temel Anlayışı: Bu eğitimi takip etmek için C# programlama ve .NET framework'üne aşinalık şarttır.

3. Geliştirme Ortamı: C# kodunuzu yazmak ve çalıştırmak için bir IDE veya metin düzenleyiciniz olduğundan emin olun (örneğin, Visual Studio).

4. Örnek Belge Dizini: Belgenizi kaydedeceğiniz ve test edeceğiniz bir dizin oluşturun. 

## Ad Alanlarını İçe Aktar

Öncelikle, .NET uygulamanızda Aspose.Words kullanmak için gerekli ad alanlarını içe aktarmanız gerekir. Aşağıdaki using yönergelerini C# dosyanızın başına ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Bu bölümde, .NET için Aspose.Words kullanarak sekmeli girintili çok seviyeli bir liste oluşturacağız. Şu adımları izleyin:

## Adım 1: Belgenizi Ayarlayın

Yeni Bir Belge ve DocumentBuilder Oluşturun

```csharp
// Belgelerinizin dizinine giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Yeni bir belge oluştur
Document doc = new Document();

// DocumentBuilder'ı Başlat
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Burada yeni bir kurulum yapıyoruz`Document` nesne ve bir`DocumentBuilder` Belge içerisinde içerik oluşturmaya başlamak için.

## Adım 2: Varsayılan Liste Biçimlendirmesini Uygula

Listeyi Oluşturun ve Biçimlendirin

```csharp
// Listeye varsayılan numaralandırma stilini uygula
builder.ListFormat.ApplyNumberDefault();
```

Bu adımda, listemize varsayılan numaralandırma biçimini uygularız. Bu, daha sonra özelleştirebileceğimiz numaralı bir liste oluşturmamıza yardımcı olacaktır.

## Adım 3: Farklı Düzeylerde Liste Öğeleri Ekleyin

Liste Öğeleri Ekle ve Girinti

```csharp
//İlk liste öğesini ekle
builder.Write("Element 1");

// İkinci seviyeyi oluşturmak için girinti
builder.ListFormat.ListIndent();
builder.Write("Element 2");

// Üçüncü seviyeyi oluşturmak için daha fazla girinti yapın
builder.ListFormat.ListIndent();
builder.Write("Element 3");
```

 Burada, her biri artan girinti seviyelerine sahip üç öğeyi listemize ekliyoruz.`ListIndent` Her bir sonraki öğe için girinti düzeyini artırmak amacıyla kullanılan bir yöntemdir.

## Adım 4: Kaydetme Seçeneklerini Yapılandırın

Girintiyi Sekme Karakterlerini Kullanacak Şekilde Ayarla

```csharp
// Girinti için sekme karakterlerini kullanacak şekilde kaydetme seçeneklerini yapılandırın
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.ListIndentation.Count = 1;
saveOptions.ListIndentation.Character = '\t';
```

 Biz yapılandırıyoruz`TxtSaveOptions` Kaydedilen metin dosyasında girintileme için sekme karakterlerini kullanmak için`ListIndentation.Character` mülk ayarlandı`'\t'`, bir sekme karakterini temsil eder.

## Adım 5: Belgeyi Kaydedin

Belgeyi Belirtilen Seçeneklerle Kaydet

```csharp
// Belgeyi belirtilen seçeneklerle kaydedin
doc.Save(dataDir + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
```

 Son olarak, belgeyi kullanarak kaydediyoruz`Save` özel yöntemimizle`TxtSaveOptions`Bu, listenin girinti düzeyleri için sekme karakterleriyle kaydedilmesini sağlar.

## Çözüm

Bu eğitimde, .NET için Aspose.Words kullanarak sekmeli girintili çok düzeyli bir liste oluşturmayı ele aldık. Bu adımları izleyerek, belgelerinizdeki listeleri kolayca yönetebilir ve biçimlendirebilir, bunların açık ve profesyonel bir şekilde sunulmasını sağlayabilirsiniz. İster raporlar, ister sunumlar veya başka bir belge türü üzerinde çalışıyor olun, bu teknikler liste biçimlendirmeniz üzerinde kesin kontrol sağlamanıza yardımcı olacaktır.

## SSS

### Girinti karakterini sekmeden boşluğa nasıl değiştirebilirim?
 Şunu değiştirebilirsiniz:`saveOptions.ListIndentation.Character` sekme yerine boşluk karakteri kullanma özelliği.

### Farklı seviyelere farklı liste stilleri uygulayabilir miyim?
Evet, Aspose.Words liste stillerinin çeşitli düzeylerde özelleştirilmesine izin verir. Farklı stiller elde etmek için liste biçimlendirme seçeneklerini değiştirebilirsiniz.

### Numaralar yerine madde işaretleri kullanmam gerekirse ne olur?
 Kullanın`ListFormat.ApplyBulletDefault()` yöntem yerine`ApplyNumberDefault()` madde işaretli bir liste oluşturmak.

### Girinti için kullanılan sekme karakterinin boyutunu nasıl ayarlayabilirim?
 Ne yazık ki, sekme boyutu`TxtSaveOptions`sabittir. Girinti boyutunu ayarlamak için boşluk kullanmanız veya liste biçimlendirmesini doğrudan özelleştirmeniz gerekebilir.

### PDF veya DOCX gibi diğer formatlara aktarım yaparken bu ayarları kullanabilir miyim?
Belirli sekme karakteri ayarları metin dosyalarına uygulanır. PDF veya DOCX gibi biçimler için, bu biçimler içindeki biçimlendirme seçeneklerini ayarlamanız gerekir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
