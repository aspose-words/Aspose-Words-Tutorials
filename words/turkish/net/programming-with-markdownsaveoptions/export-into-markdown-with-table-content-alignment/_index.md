---
title: Tablo İçeriği Hizalamasıyla Markdown'a Aktarma
linktitle: Tablo İçeriği Hizalamasıyla Markdown'a Aktarma
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak hizalanmış tablolarla Word belgelerini Markdown'a nasıl aktaracağınızı öğrenin. Mükemmel Markdown tabloları için adım adım kılavuzumuzu izleyin.
weight: 10
url: /tr/net/programming-with-markdownsaveoptions/export-into-markdown-with-table-content-alignment/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tablo İçeriği Hizalamasıyla Markdown'a Aktarma

## giriiş

Merhaba! Word belgenizi mükemmel hizalanmış tablolarla Markdown formatına nasıl aktaracağınızı hiç merak ettiniz mi? İster dokümantasyon üzerinde çalışan bir geliştirici olun, ister sadece Markdown'ı seven biri olun, bu kılavuz tam size göre. Bunu başarmak için .NET için Aspose.Words'ü kullanmanın inceliklerine dalacağız. Word tablolarınızı düzgün hizalanmış Markdown tablolarına dönüştürmeye hazır mısınız? Hadi başlayalım!

## Ön koşullar

Koda dalmadan önce, yerinde olması gereken birkaç şey var:

1.  Aspose.Words for .NET Kütüphanesi: Aspose.Words for .NET kütüphanesine sahip olduğunuzdan emin olun. Bunu şu adresten indirebilirsiniz:[Aspose Sürüm Sayfası](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Geliştirme ortamınızı kurun. Visual Studio, .NET geliştirme için popüler bir seçimdir.
3. Temel C# Bilgisi: Bu dilde kod yazacağımız için C# dilini anlamak önemlidir.
4. Örnek Word Belgesi: Test amaçlı kullanabileceğiniz bir Word belgeniz olsun.

## Ad Alanlarını İçe Aktar

Kodlamaya başlamadan önce gerekli ad alanlarını içe aktaralım. Bunlar bize kullanacağımız Aspose.Words sınıflarına ve yöntemlerine erişim sağlayacak.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

## Adım 1: Belgeyi ve DocumentBuilder'ı Başlatın

İlk önce, yeni bir Word belgesi oluşturmamız ve bir`DocumentBuilder` Belgemizi oluşturmaya başlama nesnesi.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Yeni bir belge oluşturun.
Document doc = new Document();

// DocumentBuilder'ı başlatın.
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Hücreleri Ekle ve İçeriği Hizala

Sonra, belgemize bazı hücreler ekleyeceğiz ve hizalamalarını ayarlayacağız. Bu, Markdown dışa aktarımının doğru hizalamayı korumasını sağlamak için önemlidir.

```csharp
// Bir hücre ekleyin ve hizalamayı sağa ayarlayın.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Right;
builder.Write("Cell1");

// Başka bir hücre ekleyin ve hizalamayı ortaya ayarlayın.
builder.InsertCell();
builder.ParagraphFormat.Alignment = ParagraphAlignment.Center;
builder.Write("Cell2");
```

## Adım 3: Markdown Dışa Aktarımı için Tablo İçeriği Hizalamasını Ayarlayın

 Şimdi, yapılandırmanın zamanı geldi`MarkdownSaveOptions` dışa aktarılan Markdown dosyasındaki tablo içeriğinin hizalamasını kontrol etmek için. Nasıl çalıştığını görmek için belgeyi farklı hizalama ayarlarıyla kaydedeceğiz.

```csharp
// MarkdownSaveOptions nesnesini oluşturun.
MarkdownSaveOptions saveOptions = new MarkdownSaveOptions
{
    TableContentAlignment = TableContentAlignment.Left
};

// Belgeyi sol hizalamalı olarak kaydet.
doc.Save(dataDir + "LeftTableContentAlignment.md", saveOptions);

// Hizalamayı sağa çevirin ve kaydedin.
saveOptions.TableContentAlignment = TableContentAlignment.Right;
doc.Save(dataDir + "RightTableContentAlignment.md", saveOptions);

// Hizalamayı ortaya getirin ve kaydedin.
saveOptions.TableContentAlignment = TableContentAlignment.Center;
doc.Save(dataDir + "CenterTableContentAlignment.md", saveOptions);
```

## Adım 4: Otomatik Tablo İçeriği Hizalamasını Kullanın

 The`Auto`hizalama seçeneği, hizalamayı ilgili tablo sütunundaki ilk paragraftan alır. Bu, tek bir tabloda karışık hizalamalarınız olduğunda kullanışlı olabilir.

```csharp
// Hizalamayı Otomatik olarak ayarlayın.
saveOptions.TableContentAlignment = TableContentAlignment.Auto;

// Belgeyi otomatik hizalama ile kaydedin.
doc.Save(dataDir + "AutoTableContentAlignment.md", saveOptions);
```

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak hizalanmış tablolarla Word belgelerini Markdown'a aktarmak, nasıl yapacağınızı öğrendikten sonra çocuk oyuncağı. Bu güçlü kütüphane, tablolarınızın biçimlendirmesini ve hizalamasını kontrol etmenizi kolaylaştırarak Markdown belgelerinizin tam istediğiniz gibi görünmesini sağlar. İyi kodlamalar!

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, değiştirmelerine, dönüştürmelerine ve dışa aktarmalarına olanak tanıyan güçlü bir kütüphanedir.

### Aynı tabloda farklı sütunlar için farklı hizalamalar belirleyebilir miyim?
 Evet, kullanarak`Auto` Hizalama seçeneği ile her sütundaki ilk paragrafa göre farklı hizalamalar yapabilirsiniz.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?
 Evet, Aspose.Words for .NET tam işlevsellik için bir lisans gerektirir. Bir tane alabilirsiniz[geçici lisans](https://purchase.aspose.com/temporary-license/) Değerlendirme için.

### Aspose.Words kullanarak diğer belge öğelerini Markdown'a aktarmak mümkün müdür?
Evet, Aspose.Words başlıklar, listeler ve resimler gibi çeşitli öğelerin Markdown formatına aktarılmasını destekler.

### Sorun yaşarsam nereden destek alabilirim?
 Destek alabilirsiniz[Aspose.Words Destek Forumu](https://forum.aspose.com/c/words/8).

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
