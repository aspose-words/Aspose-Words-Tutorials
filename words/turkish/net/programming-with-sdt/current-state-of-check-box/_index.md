---
title: Onay Kutusunun Mevcut Durumu
linktitle: Onay Kutusunun Mevcut Durumu
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET ile Word belgelerindeki onay kutularını nasıl yöneteceğinizi öğrenin. Bu kılavuz, onay kutularını programatik olarak ayarlamayı, güncellemeyi ve kaydetmeyi kapsar.
weight: 10
url: /tr/net/programming-with-sdt/current-state-of-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Onay Kutusunun Mevcut Durumu

## giriiş

Bu eğitimde, Word belgelerinde onay kutularıyla çalışma sürecini ele alacağız. Bir onay kutusuna nasıl erişeceğinizi, durumunu nasıl belirleyeceğinizi ve buna göre nasıl güncelleyeceğinizi ele alacağız. İster kontrol edilebilir seçeneklere ihtiyaç duyan bir form geliştiriyor olun, ister belge değişikliklerini otomatikleştiriyor olun, bu kılavuz size sağlam bir temel sağlayacaktır.

## Ön koşullar

Eğitime başlamadan önce aşağıdaki ön koşullara sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET Kütüphanesi: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Henüz yapmadıysanız, şuradan indirebilirsiniz:[Aspose web sitesi](https://releases.aspose.com/words/net/).

2. Visual Studio: Kodunuzu derlemek ve çalıştırmak için Visual Studio gibi bir .NET geliştirme ortamına ihtiyacınız olacak.

3. Temel C# Bilgisi: C# programlamaya aşinalık, verilen örnekleri anlamanıza ve takip etmenize yardımcı olacaktır.

4. Onay Kutuları İçeren Word Belgesi: Bu eğitim için, onay kutusu form alanları içeren bir Word belgesine ihtiyacınız olacak. Bu belgeyi, onay kutularını programatik olarak nasıl yöneteceğinizi göstermek için kullanacağız.

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET ile başlamak için gerekli ad alanlarını içe aktarmanız gerekir. C# dosyanızın başına aşağıdaki using yönergelerini ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Markup;
```

Bu ad alanları, Aspose.Words API'sine erişmenizi ve onunla çalışmanızı ve onay kutuları da dahil olmak üzere yapılandırılmış belge etiketlerini işlemenizi sağlayacaktır.

## Adım 1: Belge Yolunu Ayarlama

 Öncelikle Word belgenizin yolunu belirtmeniz gerekir. Aspose.Words'ün işlemleri gerçekleştirmek için dosyayı arayacağı yer burasıdır. Değiştir`"YOUR DOCUMENT DIRECTORY"` Belgenizin saklandığı gerçek yol ile.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Belgeyi Yükleme

 Sonra, Word belgesini bir örneğine yükleyin`Document` sınıf. Bu sınıf, Word belgenizi kodda temsil eder ve onu düzenlemek için çeşitli yöntemler sağlar.

```csharp
Document doc = new Document(dataDir + "Structured document tags.docx");
```

 Burada,`"Structured document tags.docx"` Word dosyanızın adıyla değiştirilmelidir.

## Adım 3: Onay Kutusu Form Alanına Erişim

Belirli bir onay kutusuna erişmek için onu belgeden almanız gerekir. Aspose.Words onay kutularını yapılandırılmış belge etiketleri olarak ele alır. Aşağıdaki kod belgedeki ilk yapılandırılmış belge etiketini alır ve bunun bir onay kutusu olup olmadığını kontrol eder.

```csharp
//Belgeden ilk içerik kontrolünü alın.
StructuredDocumentTag sdtCheckBox =
    (StructuredDocumentTag) doc.GetChild(NodeType.StructuredDocumentTag, 0, true);
```

## Adım 4: Onay Kutusu Durumunu Kontrol Etme ve Güncelleme

 Bir kez sahip olduğunuzda`StructuredDocumentTag` örneğin, türünü kontrol edebilir ve durumunu güncelleyebilirsiniz. Bu örnek, gerçekten bir onay kutusuysa onay kutusunu işaretli olarak ayarlar.

```csharp
if (sdtCheckBox.SdtType == SdtType.Checkbox)
    sdtCheckBox.Checked = true;
```

## Adım 5: Belgeyi Kaydetme

Son olarak, değiştirilen belgeyi yeni bir dosyaya kaydedin. Bu, orijinal belgeyi korumanıza ve güncellenmiş sürümle çalışmanıza olanak tanır.

```csharp
doc.Save(dataDir + "WorkingWithSdt.CurrentStateOfCheckBox.docx");
```

 Bu örnekte,`"WorkingWithSdt.CurrentStateOfCheckBox.docx"` değiştirilen belgenin kaydedileceği dosyanın adıdır.

## Çözüm

Bu eğitimde, Aspose.Words for .NET kullanarak Word belgelerindeki onay kutusu form alanlarını nasıl düzenleyeceğinizi ele aldık. Belge yolunu nasıl ayarlayacağınızı, belgeyi nasıl yükleyeceğinizi, onay kutularına nasıl erişeceğinizi, durumlarını nasıl güncelleyeceğinizi ve değişiklikleri nasıl kaydedeceğinizi inceledik. Bu becerilerle artık daha etkileşimli ve dinamik Word belgelerini programatik olarak oluşturabilirsiniz.

## SSS

### Aspose.Words for .NET ile hangi tür belge öğelerini işleyebilirim?
Aspose.Words for .NET, paragraflar, tablolar, resimler, üstbilgiler, altbilgiler ve onay kutuları gibi yapılandırılmış belge etiketleri de dahil olmak üzere çeşitli belge öğelerini düzenlemenize olanak tanır.

### Bir belgede birden fazla onay kutusunu nasıl yönetebilirim?
Birden fazla onay kutusunu işlemek için, yapılandırılmış belge etiketleri koleksiyonunda döngüye girip her birinin onay kutusu olup olmadığını belirlemek için kontrol etmeniz gerekir.

### Word belgesinde yeni onay kutuları oluşturmak için Aspose.Words for .NET'i kullanabilir miyim?
 Evet, şu türde yapılandırılmış belge etiketleri ekleyerek yeni onay kutuları oluşturabilirsiniz:`SdtType.Checkbox` belgenize.

### Bir onay kutusunun durumunu bir belgeden okumak mümkün müdür?
 Kesinlikle. Bir onay kutusunun durumunu şuraya erişerek okuyabilirsiniz:`Checked` mülkiyeti`StructuredDocumentTag` eğer tip ise`SdtType.Checkbox`.

### Aspose.Words for .NET için geçici lisansı nasıl alabilirim?
 Geçici bir lisansı şuradan alabilirsiniz:[Aspose satın alma sayfası](https://purchase.aspose.com/temporary-license/), kütüphanenin tüm işlevlerini değerlendirmenize olanak tanır.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
