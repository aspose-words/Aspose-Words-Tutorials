---
"description": "Aspose.Words for .NET kullanarak Word belgelerini HTML olarak kaydederken bir CSS sınıf adı önekinin nasıl ekleneceğini öğrenin. Adım adım kılavuz, kod parçacıkları ve SSS dahildir."
"linktitle": "Css Sınıf Adı Öneki Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Css Sınıf Adı Öneki Ekle"
"url": "/tr/net/programming-with-htmlsaveoptions/add-css-class-name-prefix/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Css Sınıf Adı Öneki Ekle

## giriiş

Hoş geldiniz! Aspose.Words for .NET dünyasına dalıyorsanız, sizi bir sürpriz bekliyor. Bugün, Aspose.Words for .NET kullanarak bir Word belgesini HTML olarak kaydederken bir CSS sınıf adı önekinin nasıl ekleneceğini inceleyeceğiz. Bu özellik, HTML dosyalarınızda sınıf adı çakışmalarından kaçınmak istediğinizde oldukça kullanışlıdır.

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

- Aspose.Words for .NET: Eğer henüz yüklemediyseniz, [buradan indirin](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio veya herhangi bir C# IDE.
- Bir Word Belgesi: Adında bir belge kullanacağız. `Rendering.docx`. Bunu proje dizininize yerleştirin.

## Ad Alanlarını İçe Aktar

Öncelikle, C# projenize gerekli ad alanlarının aktarıldığından emin olun. Bunları kod dosyanızın en üstüne ekleyin:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Saving;
```

Şimdi adım adım rehberimize geçelim!

## Adım 1: Projenizi Kurun

CSS sınıf adı önekini eklemeye başlamadan önce projemizi ayarlayalım.

### Adım 1.1: Yeni Bir Proje Oluşturun

Visual Studio'nuzu başlatın ve yeni bir Konsol Uygulaması projesi oluşturun. Buna şu şekilde akılda kalıcı bir isim verin: `AsposeCssPrefixExample`.

### Adım 1.2: Aspose.Words for .NET'i ekleyin

Henüz yapmadıysanız, NuGet aracılığıyla Aspose.Words for .NET'i projenize ekleyin. NuGet Paket Yöneticisi Konsolunu açın ve çalıştırın:

```bash
Install-Package Aspose.Words
```

Harika! Artık kodlamaya başlamaya hazırız.

## Adım 2: Belgenizi Yükleyin

İlk yapmamız gereken HTML'e dönüştürmek istediğimiz Word belgesini yüklemek.

### Adım 2.1: Belge Yolunu Tanımlayın

Belge dizininize giden yolu ayarlayın. Bu eğitim için, belgenizin şu adlı bir klasörde olduğunu varsayalım: `Documents` proje dizininizde.

```csharp
string dataDir = @"C:\YourProject\Documents\";
```

### Adım 2.2: Belgeyi Yükleyin

Şimdi Aspose.Words kullanarak belgeyi yükleyelim:

```csharp
Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 3: HTML Kaydetme Seçeneklerini Yapılandırın

Daha sonra, HTML kaydetme seçeneklerini CSS sınıf adı önekini içerecek şekilde yapılandırmamız gerekiyor.

### Adım 3.1: HTML Kaydetme Seçeneklerini Oluşturun

Örneklemi oluştur `HtmlSaveOptions` nesneyi seçin ve CSS stil sayfası türünü ayarlayın `External`.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions
{
    CssStyleSheetType = CssStyleSheetType.External
};
```

### Adım 3.2: CSS Sınıf Adı Önekini Ayarlayın

Şimdi, şunu ayarlayalım: `CssClassNamePrefix` istediğiniz önek için özellik. Bu örnek için, kullanacağız `"pfx_"`.

```csharp
saveOptions.CssClassNamePrefix = "pfx_";
```

## Adım 4: Belgeyi HTML olarak kaydedin

Son olarak, yapılandırdığımız seçeneklerle belgeyi bir HTML dosyası olarak kaydedelim.


Çıktı HTML dosya yolunu belirtin ve belgeyi kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
```

## Adım 5: Çıktıyı Doğrulayın

Projenizi çalıştırdıktan sonra, şuraya gidin: `Documents` klasörü. Adlı bir HTML dosyası bulmalısınız `WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html`. CSS sınıflarının önekini doğrulamak için bu dosyayı bir metin düzenleyicide veya tarayıcıda açın `pfx_`.

## Çözüm

Ve işte oldu! Bu adımları izleyerek, .NET için Aspose.Words kullanarak HTML çıktınıza bir CSS sınıf adı önekini başarıyla eklediniz. Bu basit ama güçlü özellik, HTML belgelerinizde temiz ve çakışmasız stiller korumanıza yardımcı olabilir.

## SSS

### Her kaydetme işlemi için farklı bir önek kullanabilir miyim?
Evet, bir belgeyi her kaydettiğinizde öneki değiştirerek özelleştirebilirsiniz. `CssClassNamePrefix` mülk.

### Bu yöntem satır içi CSS'i destekliyor mu?
The `CssClassNamePrefix` özellik harici CSS ile çalışır. Satır içi CSS için farklı bir yaklaşıma ihtiyacınız olacak.

### Diğer HTML kaydetme seçeneklerini nasıl ekleyebilirim?
Çeşitli özelliklerini yapılandırabilirsiniz `HtmlSaveOptions` HTML çıktınızı özelleştirmek için. Kontrol edin [belgeleme](https://reference.aspose.com/words/net/) Daha detaylı bilgi için.

### HTML'yi bir akışa kaydetmek mümkün müdür?
Kesinlikle! Belgeyi akışa, akış nesnesini akışa geçirerek kaydedebilirsiniz. `Save` yöntem.

### Sorun yaşarsam nasıl destek alabilirim?
Destek alabilirsiniz [Aspose forumu](https://forum.aspose.com/c/words/8).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}