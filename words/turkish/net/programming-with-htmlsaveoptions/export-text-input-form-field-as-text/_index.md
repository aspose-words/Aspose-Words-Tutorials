---
title: Metin Giriş Formu Alanını Metin Olarak Dışa Aktar
linktitle: Metin Giriş Formu Alanını Metin Olarak Dışa Aktar
second_title: Aspose.Words Belge İşleme API'si
description: Bu kapsamlı, adım adım kılavuzla Aspose.Words for .NET kullanarak metin girişi form alanlarını düz metin olarak nasıl dışa aktaracağınızı öğrenin.
weight: 10
url: /tr/net/programming-with-htmlsaveoptions/export-text-input-form-field-as-text/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Metin Giriş Formu Alanını Metin Olarak Dışa Aktar

## giriiş

Yani, .NET için Aspose.Words dünyasına mı dalıyorsunuz? Harika bir seçim! Bir metin girişi form alanını metin olarak nasıl dışa aktaracağınızı öğrenmek istiyorsanız, doğru yerdesiniz. İster yeni başlıyor olun ister becerilerinizi tazeliyor olun, bu kılavuz bilmeniz gereken her şeyi size anlatacak. Hadi başlayalım, olur mu?

## Ön koşullar

Ayrıntılara dalmadan önce, süreci sorunsuz bir şekilde takip edebilmeniz için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

-  Aspose.Words for .NET: En son sürümü buradan indirin ve kurun[Burada](https://releases.aspose.com/words/net/).
- IDE: Visual Studio veya herhangi bir C# geliştirme ortamı.
- Temel C# Bilgisi: Temel C# sözdizimi ve nesne yönelimli programlama kavramlarının anlaşılması.
- Belge: Örnek bir Word belgesi (`Rendering.docx`) metin girişi form alanlarıyla.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekir. Bunlar her şeyin sorunsuz çalışmasını sağlayan yapı taşları gibidir.

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Saving;
```

Tamam, artık ad alanlarımız hazır olduğuna göre, aksiyona geçebiliriz!

## Adım 1: Projeyi Kurun

Koda geçmeden önce projemizin doğru bir şekilde kurulduğundan emin olalım.

## Projenin Oluşturulması

1. Visual Studio'yu açın: Visual Studio'yu veya tercih ettiğiniz C# geliştirme ortamını açarak başlayın.
2.  Yeni Bir Proje Oluşturun: Şuraya gidin:`File > New > Project` . Seçme`Console App (.NET Core)` veya herhangi bir diğer ilgili proje türü.
3.  Projenize İsim Verin: Projenize anlamlı bir isim verin, örneğin:`AsposeWordsExportExample`.

## Aspose.Words'ü ekleme

1.  NuGet Paketlerini Yönetin: Çözüm Gezgini'nde projenize sağ tıklayın ve şunu seçin:`Manage NuGet Packages`.
2.  Aspose.Words'ü arayın: NuGet Paket Yöneticisi'nde, şunu arayın:`Aspose.Words`.
3.  Aspose.Words'ü yükleyin: Üzerine tıklayın`Install` Aspose.Words kütüphanesini projenize eklemek için.

## Adım 2: Word Belgesini Yükleyin

Artık projemiz kurulduğuna göre, metin giriş form alanlarını içeren Word belgesini yükleyelim.

1. Belge Dizinini Belirleyin: Belgenizin saklandığı dizine giden yolu tanımlayın.
2.  Belgeyi Yükle: Şunu kullanın:`Document` Word belgenizi yüklemek için sınıf.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document(dataDir + "Rendering.docx");
```

## Adım 3: İhracat Dizinini Hazırlayın

Dışa aktarmadan önce, dışa aktarma dizinimizin hazır olduğundan emin olalım. HTML dosyamız ve görsellerimiz buraya kaydedilecektir.

1. Dışa Aktarım Dizinini Tanımlayın: Dışa aktarılacak dosyaların kaydedileceği yolu belirtin.
2. Dizinleri Kontrol Edin ve Temizleyin: Dizinin mevcut olduğundan ve boş olduğundan emin olun.

```csharp
string imagesDir = Path.Combine(dataDir, "Images");

if (Directory.Exists(imagesDir))
    Directory.Delete(imagesDir, true);

Directory.CreateDirectory(imagesDir);
```

## Adım 4: Kaydetme Seçeneklerini Yapılandırın

İşte sihir burada gerçekleşiyor. Metin giriş formu alanını düz metin olarak dışa aktarmak için kaydetme seçeneklerimizi ayarlamamız gerekiyor.

1.  Kaydetme Seçenekleri Oluştur: Yeni bir tane başlat`HtmlSaveOptions` nesne.
2.  Dışa Aktarma Metni Seçeneğini Ayarla:`ExportTextInputFormFieldAsText`mülk`true`.
3. Resim Klasörünü Ayarla: Resimlerin kaydedileceği klasörü tanımlayın.

```csharp
HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.Html)
{
    ExportTextInputFormFieldAsText = true,
    ImagesFolder = imagesDir
};
```

## Adım 5: Belgeyi HTML olarak kaydedin

Son olarak, yapılandırdığımız kaydetme seçeneklerini kullanarak Word belgesini bir HTML dosyası olarak kaydedelim.

1. Çıktı Yolunu Tanımlayın: HTML dosyasının kaydedileceği yolu belirtin.
2.  Belgeyi Kaydedin: Şunu kullanın:`Save` yöntemi`Document`Belgeyi dışa aktarmak için sınıf.

```csharp
doc.Save(dataDir + "ExportedDocument.html", saveOptions);
```

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir metin girişi form alanını düz metin olarak başarıyla dışa aktardınız. Bu kılavuz, bu görevi başarmanız için size açık, adım adım bir yaklaşım sunmuş olmalı. Unutmayın, pratik mükemmelleştirir, bu yüzden Aspose.Words ile başka neler yapabileceğinizi görmek için farklı seçenekler ve ayarlarla denemeler yapmaya devam edin.

## SSS

### Aynı yöntemi kullanarak diğer form alanı türlerini de dışa aktarabilir miyim?

 Evet, farklı form alanı özelliklerini yapılandırarak diğer form alanı türlerini dışa aktarabilirsiniz.`HtmlSaveOptions` sınıf.

### Belgemde görseller varsa ne olur?

 Görüntüler belirtilen görüntü klasörüne kaydedilecektir. Ayarladığınızdan emin olun`ImagesFolder` mülk`HtmlSaveOptions`.

### Aspose.Words için lisansa ihtiyacım var mı?

 Evet, ücretsiz deneme alabilirsiniz[Burada](https://releases.aspose.com/) veya bir lisans satın alın[Burada](https://purchase.aspose.com/buy).

### Dışa aktarılan HTML'yi özelleştirebilir miyim?

 Kesinlikle! Aspose.Words, HTML çıktısını özelleştirmek için çeşitli seçenekler sunar.[belgeleme](https://reference.aspose.com/words/net/) Daha detaylı bilgi için.

### Aspose.Words .NET Core ile uyumlu mu?

Evet, Aspose.Words .NET Core, .NET Framework ve diğer .NET platformlarıyla uyumludur.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
