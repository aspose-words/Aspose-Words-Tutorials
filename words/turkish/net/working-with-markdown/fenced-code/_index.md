---
"description": "Aspose.Words for .NET kullanarak Word belgelerine çitli kod ve bilgi dizeleri eklemeyi öğrenin. Adım adım kılavuz dahildir. Belge biçimlendirme becerilerinizi geliştirin."
"linktitle": "Çitli Kod"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Çitli Kod"
"url": "/tr/net/working-with-markdown/fenced-code/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Çitli Kod

## giriiş

Merhaba, kodlayıcı arkadaşım! Bugün, Word belgelerinize çitli kod ve bilgi dizeleriyle çitli kod ekleme sanatında ustalaşmak için Aspose.Words for .NET dünyasına dalıyoruz. Word belgenizi bir tuval olarak hayal edin ve siz, sanatçı, deneyimli bir geliştiricinin hassasiyetiyle resim yapmak üzeresiniz. Aspose.Words ile, yapılandırılmış, biçimlendirilmiş kod bloklarıyla belgelerinizi programatik olarak geliştirme gücüne kavuşursunuz ve teknik belgelerinizi profesyonellik ve netlikle parlatırsınız.

## Ön koşullar

Eğitime başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

- Temel C# bilgisi: C# hakkında genel bir anlayışa sahip olmak, kavramları hızlı bir şekilde kavramanıza yardımcı olacaktır.
- Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olması gerekir. Eğer henüz yoksa, hemen edinin [Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio veya kendinizi rahat hissettiğiniz herhangi bir C# IDE.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekir. Bu, bir projeye başlamadan önce tüm araçlarınızı toplamak gibidir.

```csharp
using Aspose.Words;
using Aspose.Words.Style;
```

Şimdi bu süreci adım adım inceleyelim.

## Adım 1: Projenizi Kurma

Word belgemizde güzel, biçimlendirilmiş kod blokları oluşturabilmemiz için öncelikle Visual Studio'da yeni bir proje kurmamız gerekiyor.

1. Yeni Bir Proje Oluşturun: Visual Studio'yu açın ve yeni bir C# Konsol Uygulaması oluşturun.
2. Aspose.Words Referansını Ekle: Aspose.Words'ü NuGet Paket Yöneticisi aracılığıyla yükleyin. Bunu Solution Explorer'da projenize sağ tıklayarak, "NuGet Paketlerini Yönet"i seçerek ve Aspose.Words'ü arayarak yapabilirsiniz.

## Adım 2: DocumentBuilder'ı başlatın

Artık projeniz kurulduğuna göre, Word belgenize içerik eklemek için kullanacağımız ana araç olacak DocumentBuilder'ı başlatalım.

```csharp
DocumentBuilder builder = new DocumentBuilder();
```

## Adım 3: Çitli Kod için Bir Stil Oluşturun

Çitli kod eklemek için öncelikle bir stil oluşturmamız gerekir. Bunu kod bloğumuz için temayı ayarlamak olarak düşünün.

```csharp
Style fencedCode = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode");
fencedCode.Font.Name = "Courier New";
fencedCode.Font.Size = 10;
fencedCode.ParagraphFormat.LeftIndent = 20;
fencedCode.ParagraphFormat.RightIndent = 20;
fencedCode.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Adım 4: Belgeye Çitli Kod Ekleyin

Stilimiz hazır olduğuna göre artık belgeye çitli bir kod bloğu ekleyebiliriz.

```csharp
builder.ParagraphFormat.Style = fencedCode;
builder.Writeln("This is a fenced code block");
```

## Adım 5: Bilgi Dizisi ile Çitli Kod için Bir Stil Oluşturun

Bazen programlama dilini belirtmek veya kod bloğunuza ekstra bilgi eklemek isteyebilirsiniz. Bunun için bir stil oluşturalım.

```csharp
Style fencedCodeWithInfo = builder.Document.Styles.Add(StyleType.Paragraph, "FencedCode.C#");
fencedCodeWithInfo.Font.Name = "Courier New";
fencedCodeWithInfo.Font.Size = 10;
fencedCodeWithInfo.ParagraphFormat.LeftIndent = 20;
fencedCodeWithInfo.ParagraphFormat.RightIndent = 20;
fencedCodeWithInfo.ParagraphFormat.Shading.BackgroundPatternColor = Color.LightGray;
```

## Adım 6: Bilgi Dizisi ile Çitli Kodu Belgeye Ekleyin

Şimdi, C# kodu olduğunu belirtmek için bir bilgi dizesi içeren çitli bir kod bloğu ekleyelim.

```csharp
builder.ParagraphFormat.Style = fencedCodeWithInfo;
builder.Writeln("This is a fenced code block with info string - C#");
```

## Çözüm

Tebrikler! Aspose.Words for .NET kullanarak Word belgelerinize çitle çevrilmiş kod blokları ve bilgi dizeleriyle çitle çevrilmiş kod eklediniz. Bu buzdağının sadece görünen kısmı. Aspose.Words ile belge işlemenizi yeni zirvelere otomatikleştirebilir ve geliştirebilirsiniz. Keşfetmeye devam edin ve mutlu kodlamalar!

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine ve dönüştürmelerine olanak tanıyan güçlü bir kütüphanedir.

### Aspose.Words'ü diğer programlama dilleriyle kullanabilir miyim?
Aspose.Words öncelikli olarak .NET dillerini destekler, ancak Java, Python ve diğer diller için de sürümleri mevcuttur.

### Aspose.Words'ü kullanmak ücretsiz mi?
Aspose.Words ticari bir üründür, ancak ücretsiz deneme sürümünü indirebilirsiniz [Burada](https://releases.aspose.com/) Özelliklerini keşfetmek için.

### Aspose.Words için nasıl destek alabilirim?
Aspose topluluğundan ve geliştiricilerden destek alabilirsiniz [Burada](https://forum.aspose.com/c/words/8).

### Aspose.Words başka hangi özellikleri sunuyor?
Aspose.Words, belge dönüştürme, şablon tabanlı belge oluşturma, raporlama ve daha birçok özelliği içeren geniş bir yelpazede özellikler sunar.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}