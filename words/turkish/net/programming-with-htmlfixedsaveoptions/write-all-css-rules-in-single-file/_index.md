---
title: Tüm Css Kurallarını Tek Bir Dosyaya Yaz
linktitle: Tüm Css Kurallarını Tek Bir Dosyaya Yaz
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerini tek bir dosyada tüm CSS kurallarıyla HTML'ye nasıl dönüştüreceğinizi öğrenin; böylece daha temiz kod ve daha kolay bakım sağlayabilirsiniz.
weight: 10
url: /tr/net/programming-with-htmlfixedsaveoptions/write-all-css-rules-in-single-file/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tüm Css Kurallarını Tek Bir Dosyaya Yaz

## giriiş

Word belgelerini HTML'e dönüştürürken kendinizi her yere dağılmış CSS kuralları ağında buldunuz mu? Endişelenmeyin! Bugün, tüm CSS kurallarını tek bir dosyaya yazmanıza olanak tanıyan Aspose.Words for .NET'in şık bir özelliğini ele alacağız. Bu, yalnızca kodunuzu düzenlemekle kalmaz, aynı zamanda hayatınızı da çok daha kolaylaştırır. Emniyet kemerlerinizi bağlayın ve daha temiz, daha verimli HTML çıktısına giden bu yolculuğa başlayalım!

## Ön koşullar

İnce ayrıntılara dalmadan önce, işleri bir sıraya koyalım. Başlamak için ihtiyacınız olanlar şunlardır:

1.  Aspose.Words for .NET: Aspose.Words for .NET kütüphanesine sahip olduğunuzdan emin olun. Henüz sahip değilseniz,[buradan indirin](https://releases.aspose.com/words/net/).
2. .NET Geliştirme Ortamı: Makinenizde kurulu bir .NET geliştirme ortamına ihtiyacınız olacak. Visual Studio popüler bir seçimdir.
3. Temel C# Bilgisi: C# programlamaya dair temel bir anlayışa sahip olmak faydalı olacaktır.
4. Word Belgesi: Dönüştürmek istediğiniz bir Word belgesi (.docx) hazır bulundurun.

## Ad Alanlarını İçe Aktar

Öncelikle, C# projenize gerekli ad alanlarını içe aktaralım. Bu, Aspose.Words işlevlerine kolayca erişmemizi sağlayacaktır.

```csharp
using Aspose.Words;
using Aspose.Words.Saving;
```

Tamam, süreci takip etmesi kolay adımlara bölelim. Her adım, her şeyin sorunsuz bir şekilde ilerlemesini sağlamak için sizi sürecin belirli bir bölümünde yönlendirecektir.

## Adım 1: Belge Dizininizi Ayarlayın

Öncelikle belge dizininize giden yolu tanımlamamız gerekiyor. Word belgenizin saklandığı ve dönüştürülen HTML'nin kaydedileceği yer burasıdır.

```csharp
// Belge dizininize erişim yolu
string dataDir = "YOUR DOCUMENTS DIRECTORY";
```

## Adım 2: Word Belgesini Yükleyin

 Sonra, HTML'ye dönüştürmek istediğiniz Word belgesini yüklüyoruz. Bu, şu şekilde yapılır:`Document` Aspose.Words kütüphanesinden sınıf.

```csharp
// Word belgesini yükleyin
Document doc = new Document(dataDir + "Document.docx");
```

## Adım 3: HTML Kaydetme Seçeneklerini Yapılandırın

 Şimdi, HTML kaydetme seçeneklerini yapılandırmamız gerekiyor. Özellikle, tüm CSS kurallarını tek bir dosyaya yazan özelliği etkinleştirmek istiyoruz. Bu,`SaveFontFaceCssSeparately`mülk`false`.

```csharp
// "Tüm CSS kurallarını tek bir dosyaya yaz" özelliği ile yedekleme seçeneklerini yapılandırın
HtmlFixedSaveOptions saveOptions = new HtmlFixedSaveOptions 
{ 
    SaveFontFaceCssSeparately = false 
};
```

## Adım 4: Belgeyi Sabit HTML'ye Dönüştür

Son olarak, yapılandırılmış kaydetme seçeneklerini kullanarak belgeyi bir HTML dosyası olarak kaydederiz. Bu adım, tüm CSS kurallarının tek bir dosyaya yazılmasını sağlar.

```csharp
// Belgeyi sabit HTML'ye dönüştür
doc.Save(dataDir + "WorkingWithHtmlFixedSaveOptions.WriteAllCssRulesInSingleFile.html", saveOptions);
```

## Çözüm

Ve işte karşınızda! Sadece birkaç satır kodla, Word belgenizi tüm CSS kurallarının tek bir dosyada düzgün bir şekilde düzenlendiği HTML'ye başarıyla dönüştürdünüz. Bu yöntem yalnızca CSS yönetiminizi basitleştirmekle kalmaz, aynı zamanda HTML belgelerinizin sürdürülebilirliğini de artırır. Yani, bir dahaki sefere bir Word belgesini dönüştürme göreviniz olduğunda, her şeyi nasıl düzenli tutacağınızı tam olarak biliyorsunuz!

## SSS

### HTML çıktım için neden tek bir CSS dosyası kullanmalıyım?
Tek bir CSS dosyası kullanmak stillerinizin yönetimini ve bakımını basitleştirir. HTML'nizi daha temiz ve daha verimli hale getirir.

### Gerekirse font yüzü CSS kurallarını ayırabilir miyim?
 Evet, ayarlayarak`SaveFontFaceCssSeparately` ile`true`, font yüzü CSS kurallarını ayrı bir dosyaya ayırabilirsiniz.

### Aspose.Words for .NET'i kullanmak ücretsiz mi?
 Aspose.Words, ücretsiz bir deneme sürümü sunuyor.[buradan indirin](https://releases.aspose.com/) . Sürekli kullanım için bir lisans satın almayı düşünün[Burada](https://purchase.aspose.com/buy).

### Aspose.Words for .NET başka hangi formatlara dönüştürülebilir?
Aspose.Words for .NET, PDF, TXT ve JPEG ve PNG gibi resim formatları da dahil olmak üzere çeşitli formatları destekler.

### Aspose.Words for .NET hakkında daha fazla kaynağı nerede bulabilirim?
 Şuna bir göz atın:[belgeleme](https://reference.aspose.com/words/net/) kapsamlı kılavuzlar ve API referansları için.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
