---
title: Tireleme Geri Çağrısı
linktitle: Tireleme Geri Çağrısı
second_title: Aspose.Words Belge İşleme API'si
description: Bu kapsamlı adım adım kılavuzla, Aspose.Words for .NET'te tireleme geri aramasını nasıl uygulayacağınızı öğrenin ve belge biçimlendirmesini geliştirin.
weight: 10
url: /tr/net/working-with-hyphenation/hyphenation-callback/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tireleme Geri Çağrısı


## giriiş

Merhaba! Özellikle tireleme gerektiren dillerle uğraşırken, metin biçimlendirmenin karmaşıklıkları arasında kendinizi hiç sıkışmış buldunuz mu? Yalnız değilsiniz. Tireleme, düzgün metin düzeni için önemli olsa da biraz baş ağrıtıcı olabilir. Ama tahmin edin ne oldu? Aspose.Words for .NET sizin yanınızda. Bu güçlü kütüphane, tirelemeyi bir geri çağırma mekanizmasıyla işlemek de dahil olmak üzere metin biçimlendirmesini sorunsuz bir şekilde yönetmenizi sağlar. İlginizi çekti mi? Aspose.Words for .NET kullanarak tireleme geri çağırmasını nasıl uygulayabileceğinizin inceliklerine dalalım.

## Ön koşullar

Kodlarla uğraşmaya başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: Kütüphaneye sahip olduğunuzdan emin olun.[buradan indirin](https://releases.aspose.com/words/net/).
2. IDE: Visual Studio benzeri bir geliştirme ortamı.
3. Temel C# Bilgisi: C# ve .NET framework'ünün anlaşılması.
4. Tireleme Sözlükleri: Kullanmayı planladığınız diller için tireleme sözlükleri.
5.  Aspose Lisansı: Geçerli bir Aspose lisansı. Bir tane alabilirsiniz[geçici lisans](https://purchase.aspose.com/temporary-license/) eğer yoksa.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu, kodumuzun Aspose.Words'den ihtiyacımız olan tüm sınıflara ve yöntemlere erişebilmesini sağlar.

```csharp
using Aspose.Words;
using System;
using System.IO;
```

## Adım 1: Heceleme Geri Çağrısını Kaydedin

Başlamak için tireleme geri aramamızı kaydetmemiz gerekiyor. Aspose.Words'e özel tireleme mantığımızı kullanmasını söylediğimiz yer burasıdır.

```csharp
try
{
    // Kayıt tireleme geri araması.
    Hyphenation.Callback = new CustomHyphenationCallback();
}
catch (Exception e)
{
    Console.WriteLine($"Error registering hyphenation callback: {e.Message}");
}
```

 Burada, özel geri aramamızın bir örneğini oluşturuyoruz ve bunu şuraya atıyoruz:`Hyphenation.Callback`.

## Adım 2: Belge Yolunu Tanımlayın

Sonra, belgelerimizin saklandığı dizini tanımlamamız gerekiyor. Bu çok önemli çünkü belgeleri bu yoldan yükleyip kaydedeceğiz.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

 Yer değiştirmek`"YOUR DOCUMENT DIRECTORY"` Belgelerinize giden gerçek yol ile.

## Adım 3: Belgeyi Yükleyin

Şimdi tireleme gerektiren belgeyi yükleyelim.

```csharp
Document document = new Document(dataDir + "German text.docx");
```

Burada, bir Almanca metin belgesi yüklüyoruz. Değiştirebilirsiniz`"German text.docx"` belgenizin dosya adıyla.

## Adım 4: Belgeyi Kaydedin

Belgeyi yükledikten sonra, tireleme geri çağırmasını uygulayarak yeni bir dosyaya kaydediyoruz.

```csharp
document.Save(dataDir + "TreatmentByCesureWithRecall.pdf");
```

Bu satır, belgeyi tireleme uygulanmış bir PDF olarak kaydeder.

## Adım 5: Eksik Tireleme Sözlüğü İstisnasını Ele Alın

Bazen tireleme sözlüğünün eksik olduğu bir sorunla karşılaşabilirsiniz. Hadi bunu ele alalım.

```csharp
catch (Exception e) when (e.Message.StartsWith("Missing hyphenation dictionary"))
{
    Console.WriteLine(e.Message);
}
finally
{
    Hyphenation.Callback = null;
}
```

Bu blokta eksik sözlüklerle ilgili belirli istisnayı yakalayıp mesajı yazdırıyoruz.

## Adım 6: Özel Tireleme Geri Çağırma Sınıfını Uygulayın

 Şimdi, şunu uygulayalım:`CustomHyphenationCallback` Heceleme sözlükleri için istekleri işleyen sınıf.

```csharp
public class CustomHyphenationCallback : IHyphenationCallback
{
    public void RequestDictionary(string language)
    {
        string dictionaryFolder = MyDir;
        string dictionaryFullFileName;
        switch (language)
        {
            case "en-US":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_en_US.dic");
                break;
            case "de-CH":
                dictionaryFullFileName = Path.Combine(dictionaryFolder, "hyph_de_CH.dic");
                break;
            default:
                throw new Exception($"Missing hyphenation dictionary for {language}.");
        }
        // İstenilen dil için sözlüğü kaydedin.
        Hyphenation.RegisterDictionary(language, dictionaryFullFileName);
    }
}
```

 Bu sınıfta,`RequestDictionary` bir tireleme sözlüğüne ihtiyaç duyulduğunda method çağrılır. Dili kontrol eder ve uygun sözlüğü kaydeder.

## Çözüm

Ve işte karşınızda! .NET için Aspose.Words'de tireleme geri aramasını nasıl uygulayacağınızı öğrendiniz. Bu adımları izleyerek, dilden bağımsız olarak belgelerinizin güzel bir şekilde biçimlendirildiğinden emin olabilirsiniz. İster İngilizce, ister Almanca veya başka bir dille uğraşıyor olun, bu yöntem tirelemeyi zahmetsizce halletmenizi sağlar.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin belgeleri programlı bir şekilde oluşturmalarına, değiştirmelerine ve dönüştürmelerine olanak tanıyan güçlü bir belge düzenleme kütüphanesidir.

### Belge biçimlendirmede tireleme neden önemlidir?
Tireleme, kelimeleri uygun yerlerde bölerek metin düzenini iyileştirir, daha okunabilir ve görsel olarak daha çekici bir belge sağlar.

### Aspose.Words'ü ücretsiz kullanabilir miyim?
 Aspose.Words ücretsiz deneme sunuyor. Bunu alabilirsiniz[Burada](https://releases.aspose.com/).

### Tireleme sözlüğünü nasıl edinebilirim?
Çeşitli çevrimiçi kaynaklardan tireleme sözlüklerini indirebilir veya ihtiyaç duyarsanız kendi sözlüklerinizi oluşturabilirsiniz.

### Tireleme sözlüğü eksik olursa ne olur?
 Bir sözlük eksikse,`RequestDictionary`metodu, kullanıcıyı bilgilendirmek veya bir geri dönüş sağlamak için kullanabileceğiniz bir istisna fırlatır.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
