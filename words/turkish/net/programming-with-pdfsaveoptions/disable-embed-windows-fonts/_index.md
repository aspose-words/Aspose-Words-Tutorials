---
"description": "Aspose.Words for .NET kullanarak gömülü yazı tiplerini devre dışı bırakarak PDF boyutunu küçültün. Belgelerinizi verimli depolama ve paylaşım için optimize etmek üzere adım adım kılavuzumuzu izleyin."
"linktitle": "Gömülü Yazı Tiplerini Devre Dışı Bırakarak PDF Boyutunu Küçültün"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Gömülü Yazı Tiplerini Devre Dışı Bırakarak PDF Boyutunu Küçültün"
"url": "/tr/net/programming-with-pdfsaveoptions/disable-embed-windows-fonts/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Gömülü Yazı Tiplerini Devre Dışı Bırakarak PDF Boyutunu Küçültün

## giriiş

PDF dosyalarının boyutunu küçültmek, verimli depolama ve hızlı paylaşım için çok önemli olabilir. Bunu yapmanın etkili bir yolu, özellikle standart yazı tipleri çoğu sistemde zaten mevcut olduğunda, gömülü yazı tiplerini devre dışı bırakmaktır. Bu eğitimde, .NET için Aspose.Words kullanarak gömülü yazı tiplerini devre dışı bırakarak PDF boyutunu nasıl küçülteceğinizi inceleyeceğiz. Bunu kendi projelerinizde kolayca uygulayabilmenizi sağlamak için her adımı ele alacağız.

## Ön koşullar

Koda dalmadan önce aşağıdakilerin mevcut olduğundan emin olun:

- Aspose.Words for .NET: Eğer henüz yapmadıysanız, şu adresten indirip kurun: [İndirme bağlantısı](https://releases.aspose.com/words/net/).
- .NET Geliştirme Ortamı: Visual Studio popüler bir seçimdir.
- Örnek Bir Word Belgesi: PDF'e dönüştürmek istediğiniz bir DOCX dosyanız hazır olsun.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarının aktarıldığından emin olun. Bu, görevimiz için gereken sınıflara ve yöntemlere erişmenizi sağlar.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Süreci basit, yönetilebilir adımlara bölelim. Her adım sizi görev boyunca yönlendirecek ve her noktada ne olduğunu anlamanızı sağlayacaktır.

## Adım 1: Belgenizi Başlatın

Öncelikle PDF'e dönüştürmek istediğiniz Word belgesini yüklememiz gerekiyor. Yolculuğunuz burada başlıyor.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

Burada, `dataDir` belgenizin bulunduğu dizin için bir yer tutucudur. Değiştir `"YOUR DOCUMENT DIRECTORY"` gerçek yol ile.

## Adım 2: PDF Kaydetme Seçeneklerini Yapılandırın

Sonra, PDF kaydetme seçeneklerini ayarlayacağız. Burada standart Windows yazı tiplerini gömmek istemediğimizi belirteceğiz.

```csharp
// Çıktı PDF'i standart Windows yazı tipleri gömülmeden kaydedilecektir.
PdfSaveOptions saveOptions = new PdfSaveOptions
{
    FontEmbeddingMode = PdfFontEmbeddingMode.EmbedNone
};
```

Ayarlayarak `FontEmbeddingMode` ile `EmbedNone`, Aspose.Words'e bu yazı tiplerini PDF'e eklememesini talimatlandırıyoruz, böylece dosya boyutu küçülüyor.

## Adım 3: Belgeyi PDF olarak kaydedin

Son olarak, yapılandırılmış kaydetme seçeneklerini kullanarak belgeyi PDF olarak kaydediyoruz. Bu, DOCX'inizin kompakt bir PDF'ye dönüştüğü gerçek an.

```csharp
doc.Save(dataDir + "WorkingWithPdfSaveOptions.DisableEmbedWindowsFonts.pdf", saveOptions);
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` gerçek dizin yolunuzla bir kez daha. Çıktı PDF'i artık gömülü standart yazı tipleri olmadan belirtilen dizine kaydedilecektir.

## Çözüm

Bu adımları izleyerek PDF dosyalarınızın boyutunu önemli ölçüde azaltabilirsiniz. Gömülü yazı tiplerini devre dışı bırakmak, belgelerinizi daha hafif ve paylaşımını daha kolay hale getirmenin basit ancak etkili bir yoludur. Aspose.Words for .NET bu süreci sorunsuz hale getirerek dosyalarınızı minimum çabayla optimize edebilmenizi sağlar.

## SSS

### PDF'deki gömülü yazı tiplerini neden devre dışı bırakmalıyım?
Gömülü yazı tiplerini devre dışı bırakmak, bir PDF'in dosya boyutunu önemli ölçüde azaltabilir, bu da depolamayı daha verimli hale getirir ve paylaşımı daha hızlı hale getirir.

### Gömülü yazı tipleri olmadan PDF yine de düzgün şekilde görüntülenecek mi?
Evet, yazı tipleri standart olduğu ve PDF'in görüntülendiği sistemde mevcut olduğu sürece düzgün bir şekilde görüntülenecektir.

### PDF'e yalnızca belirli yazı tiplerini seçerek yerleştirebilir miyim?
Evet, Aspose.Words for .NET, hangi yazı tiplerinin yerleştirileceğini özelleştirmenize olanak tanır ve dosya boyutunu nasıl azaltacağınız konusunda esneklik sağlar.

### PDF'lerdeki gömülü yazı tiplerini devre dışı bırakmak için Aspose.Words for .NET'e ihtiyacım var mı?
Evet, Aspose.Words for .NET, PDF'lerdeki yazı tipi yerleştirme seçeneklerini yapılandırmak için gereken işlevselliği sağlar.

### Sorun yaşarsam nasıl destek alabilirim?
Ziyaret edebilirsiniz [Destek forumu](https://forum.aspose.com/c/words/8) Karşılaştığınız herhangi bir sorunda yardım için.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}