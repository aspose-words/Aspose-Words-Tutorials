---
title: Belirli Seçeneklerle Metin Filigranı Ekle
linktitle: Belirli Seçeneklerle Metin Filigranı Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerinize belirli seçeneklerle metin filigranı eklemeyi öğrenin. Yazı tipini, boyutunu, rengini ve düzenini kolayca özelleştirin.
weight: 10
url: /tr/net/programming-with-watermark/add-text-watermark-with-specific-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Belirli Seçeneklerle Metin Filigranı Ekle

## giriiş

Filigranlar, Word belgelerinize şık ve işlevsel bir ek olabilir ve belgeleri gizli olarak işaretlemekten kişiselleştirilmiş bir dokunuş eklemeye kadar çeşitli amaçlara hizmet edebilir. Bu eğitimde, .NET için Aspose.Words kullanarak bir Word belgesine metin filigranı eklemeyi inceleyeceğiz. Yazı tipi ailesi, yazı tipi boyutu, renk ve düzen gibi yapılandırabileceğiniz belirli seçeneklere dalacağız. Sonunda, belgenizin filigranını tam ihtiyaçlarınıza uyacak şekilde özelleştirebileceksiniz. O halde kod düzenleyicinizi alın ve başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilerin yerinde olduğundan emin olun:

1.  Aspose.Words for .NET Kütüphanesi: Aspose.Words kütüphanesinin kurulu olması gerekir. Eğer henüz yapmadıysanız, şuradan indirebilirsiniz:[Aspose.Words İndirme Bağlantısı](https://releases.aspose.com/words/net/).
2. C#'ın Temel Anlayışı: Bu eğitimde programlama dili olarak C# kullanılacaktır. C# sözdiziminin temel bir kavrayışı faydalı olacaktır.
3. .NET Geliştirme Ortamı: .NET uygulamalarınızı oluşturabileceğiniz ve çalıştırabileceğiniz bir geliştirme ortamı (Visual Studio gibi) kurduğunuzdan emin olun.

## Ad Alanlarını İçe Aktar

Aspose.Words ile çalışmak için projenize gerekli ad alanlarını eklemeniz gerekir. İçe aktarmanız gerekenler şunlardır:

```csharp
using Aspose.Words;
using Aspose.Words.Rendering;
using System.Drawing;
```

## Adım 1: Belgenizi Ayarlayın

 Öncelikle çalışmak istediğiniz belgeyi yüklemeniz gerekir. Bu eğitim için, şu adlı örnek belgeyi kullanacağız:`Document.docx`Bu belgenin belirttiğiniz dizinde bulunduğundan emin olun.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Document.docx");
```

 Bu adımda, belgenizin bulunduğu dizini tanımlarsınız ve onu bir örneğine yüklersiniz.`Document` sınıf.

## Adım 2: Filigran Seçeneklerini Yapılandırın

Sonra, metin filigranınız için seçenekleri yapılandırın. Yazı tipi ailesi, yazı tipi boyutu, renk ve düzen gibi çeşitli yönleri özelleştirebilirsiniz. Bu seçenekleri ayarlayalım.

```csharp
TextWatermarkOptions options = new TextWatermarkOptions()
{
    FontFamily = "Arial",
    FontSize = 36,
    Color = Color.Black,
    Layout = WatermarkLayout.Horizontal,
    IsSemitrasparent = false
};
```

Her seçeneğin işlevi şöyledir:
- `FontFamily`: Filigran metninin yazı tipini belirtir.
- `FontSize`: Filigran metninin boyutunu ayarlar.
- `Color`: Filigran metninin rengini tanımlar.
- `Layout`Filigranın yönünü (yatay veya çapraz) belirler.
- `IsSemitrasparent`: Filigranın yarı saydam olup olmayacağını ayarlar.

## Adım 3: Filigran Metnini Ekleyin

Şimdi, daha önce yapılandırılmış seçenekleri kullanarak filigranı belgenize uygulayın. Bu adımda, filigran metnini "Test" olarak ayarlayacak ve tanımladığınız seçenekleri uygulayacaksınız.

```csharp
doc.Watermark.SetText("Test", options);
```

Bu kod satırı, belirtilen seçenekleri uygulayarak belgeye "Test" metniyle filigran ekler.

## Adım 4: Belgeyi Kaydedin

Son olarak, yeni filigran uygulanmış belgeyi kaydedin. Orijinal belgenin üzerine yazmamak için yeni bir adla kaydedebilirsiniz.

```csharp
doc.Save(dataDir + "WorkWithWatermark.AddTextWatermarkWithSpecificOptions.docx");
```

Bu kod parçacığı, değiştirilen belgeyi yeni bir dosya adıyla aynı dizine kaydeder.

## Çözüm

Aspose.Words for .NET kullanarak Word belgelerinize bir metin filigranı eklemek, yönetilebilir adımlara böldüğünüzde basit bir işlemdir. Bu öğreticiyi takip ederek, yazı tipi, boyut, renk, düzen ve şeffaflık dahil olmak üzere çeşitli filigran seçeneklerini nasıl yapılandıracağınızı öğrendiniz. Bu becerilerle, artık belgelerinizi ihtiyaçlarınızı daha iyi karşılayacak veya gizlilik veya markalama gibi temel bilgileri ekleyecek şekilde özelleştirebilirsiniz.

 Herhangi bir sorunuz varsa veya daha fazla yardıma ihtiyacınız varsa, şuraya göz atmaktan çekinmeyin:[Aspose.Words Belgeleri](https://reference.aspose.com/words/net/) veya ziyaret edin[Aspose Destek Forumu](https://forum.aspose.com/c/words/8) Daha fazla yardım için.

## SSS

### Filigran için farklı yazı tipleri kullanabilir miyim?

 Evet, sisteminizde yüklü olan herhangi bir yazı tipini belirterek seçebilirsiniz.`FontFamily` mülk`TextWatermarkOptions`.

### Filigranın rengini nasıl değiştirebilirim?

 Filigranın rengini,`Color` mülk`TextWatermarkOptions` herhangi birine`System.Drawing.Color` değer.

### Bir belgeye birden fazla filigran eklemek mümkün müdür?

Aspose.Words, bir defada bir filigran eklemeyi destekler. Birden fazla filigran eklemek için, bunları sırayla oluşturmanız ve uygulamanız gerekir.

### Filigranın konumunu ayarlayabilir miyim?

 The`WatermarkLayout`özellik yönelimi belirler, ancak hassas konumlandırma ayarlamaları doğrudan desteklenmez. Tam yerleştirme için başka teknikler kullanmanız gerekebilir.

### Yarı saydam bir filigrana ihtiyacım olursa ne olur?

 Ayarla`IsSemitrasparent`mülk`true` filigranınızı yarı saydam hale getirmek için.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
