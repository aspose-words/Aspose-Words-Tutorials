---
title: Oluşturucu ile Belge Ekle
linktitle: Oluşturucu ile Belge Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak iki Word belgesini birleştirmeyi öğrenin. DocumentBuilder ile bir belgeyi eklemek ve biçimlendirmeyi korumak için adım adım kılavuz.
weight: 10
url: /tr/net/join-and-append-documents/insert-document-with-builder/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Oluşturucu ile Belge Ekle

## giriiş

Yani, iki Word belgeniz var ve bunları tek bir belgede birleştirmeyi düşünüyorsunuz. "Bunu programatik olarak yapmanın kolay bir yolu var mı?" diye düşünüyor olabilirsiniz. Kesinlikle! Bugün, Aspose.Words for .NET kütüphanesini kullanarak bir belgeyi diğerine ekleme sürecini adım adım anlatacağım. Bu yöntem, özellikle büyük belgelerle uğraşırken veya süreci otomatikleştirmeniz gerektiğinde çok kullanışlıdır. Hemen başlayalım!

## Ön koşullar

Başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: Eğer henüz indirmediyseniz, şu adresten indirebilirsiniz:[Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya başka uygun bir IDE'nin yüklü olduğundan emin olun.
3. Temel C# Bilgisi: C# ile ilgili biraz bilgi sahibi olmak çok işinize yarayacaktır.

## Ad Alanlarını İçe Aktar

Öncelikle, Aspose.Words kütüphane işlevlerine erişmek için gerekli ad alanlarını içe aktarmanız gerekir. Bunu nasıl yapabileceğiniz aşağıda açıklanmıştır:

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Artık ön koşullarımız hazır olduğuna göre, süreci adım adım inceleyelim.

## Adım 1: Belge Dizininizi Ayarlama

Kodlamaya başlamadan önce, belge dizininize giden yolu ayarlamanız gerekir. Kaynak ve hedef belgeleriniz burada saklanır.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` Belgelerinizin bulunduğu gerçek yol ile. Bu, programın dosyalarınızı kolayca bulmasına yardımcı olacaktır.

## Adım 2: Kaynak ve Hedef Belgeleri Yükleme

Sonra, çalışmak istediğimiz belgeleri yüklememiz gerekiyor. Bu örnekte, bir kaynak belgemiz ve bir hedef belgemiz var.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

 Burada şunu kullanıyoruz:`Document` Belgelerimizi yüklemek için Aspose.Words kütüphanesinden sınıf. Dosya adlarının dizininizdekilerle eşleştiğinden emin olun.

## Adım 3: Bir DocumentBuilder Nesnesi Oluşturma

 The`DocumentBuilder` class, Aspose.Words kütüphanesinde güçlü bir araçtır. Belgede gezinmemizi ve değişiklik yapmamızı sağlar.

```csharp
DocumentBuilder builder = new DocumentBuilder(dstDoc);
```

 Bu adımda bir tane oluşturduk`DocumentBuilder` hedef belgemiz için nesne. Bu, belgeye içerik eklememize yardımcı olacaktır.

## Adım 4: Belgenin Sonuna Geçme

Kaynak belgeyi eklemeden önce oluşturucu imlecini hedef belgenin sonuna taşımamız gerekiyor.

```csharp
builder.MoveToDocumentEnd();
```

Bu, kaynak belgenin hedef belgenin sonuna eklenmesini sağlar.

## Adım 5: Sayfa Sonu Ekleme

İşleri düzenli tutmak için, kaynak belgeyi eklemeden önce bir sayfa sonu ekleyelim. Bu, kaynak belgenin içeriğini yeni bir sayfada başlatacaktır.

```csharp
builder.InsertBreak(BreakType.PageBreak);
```

Sayfa sonu, kaynak belge içeriğinin yeni bir sayfada başlamasını sağlayarak birleştirilen belgenin profesyonel görünmesini sağlar.

## Adım 6: Kaynak Belgeyi Ekleme

Şimdi heyecan verici kısma geliyoruz: Kaynak belgeyi hedef belgeye yerleştirmek.

```csharp
builder.InsertDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

 Kullanımı`InsertDocument` yöntem, tüm kaynak belgeyi hedef belgeye ekleyebiliriz.`ImportFormatMode.KeepSourceFormatting` kaynak belgenin biçimlendirmesinin korunmasını sağlar.

## Adım 7: Birleştirilen Belgeyi Kaydetme

Son olarak, birleştirilmiş belgeyi kaydedelim. Bu, kaynak ve hedef belgeleri tek bir dosyada birleştirecektir.

```csharp
builder.Document.Save(dataDir + "JoinAndAppendDocuments.InsertDocumentWithBuilder.docx");
```

Belgeyi kaydederek iki belgeyi birleştirme işlemini tamamlıyoruz. Yeni belgeniz artık hazır ve belirtilen dizine kaydedildi.

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir belgeyi diğerine başarıyla eklediniz. Bu yöntem yalnızca verimli olmakla kalmaz, aynı zamanda her iki belgenin biçimlendirmesini de koruyarak kusursuz bir birleştirme sağlar. Tek seferlik bir proje üzerinde çalışıyor olun veya belge işlemeyi otomatikleştirmeniz gereksin, Aspose.Words for .NET sizin için her şeyi yapar.

## SSS

### Aspose.Words for .NET nedir?  
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine, dönüştürmelerine ve değiştirmelerine olanak tanıyan güçlü bir kütüphanedir.

### Kaynak belgenin biçimlendirmesini koruyabilir miyim?  
 Evet, kullanarak`ImportFormatMode.KeepSourceFormatting`Kaynak belgenin biçimlendirmesi, hedef belgeye eklendiğinde korunur.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?  
 Evet, Aspose.Words for .NET tam işlevsellik için bir lisans gerektirir. Bir tane alabilirsiniz[geçici lisans](https://purchase.aspose.com/temporary-license/) Değerlendirme için.

### Bu süreci otomatikleştirebilir miyim?  
Kesinlikle! Açıklanan yöntem, belge işleme görevlerini otomatikleştirmek için daha büyük uygulamalara dahil edilebilir.

### Daha fazla kaynak ve desteği nerede bulabilirim?  
 Daha fazla bilgi için şuraya bakabilirsiniz:[belgeleme](https://reference.aspose.com/words/net/) veya ziyaret edin[destek forumu](https://forum.aspose.com/c/words/8) yardım için.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
