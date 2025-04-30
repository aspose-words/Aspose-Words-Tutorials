---
"description": "Aspose.Words for .NET'te belge oluşturucu kullanmadan TOA alanı eklemeyi öğrenin. Yasal atıfları verimli bir şekilde yönetmek için adım adım kılavuzumuzu izleyin."
"linktitle": "Belge Oluşturucu Olmadan TOA Alanı Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Belge Oluşturucu Olmadan TOA Alanı Ekle"
"url": "/tr/net/working-with-fields/insert-toafield-without-document-builder/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Belge Oluşturucu Olmadan TOA Alanı Ekle

## giriiş

Word belgesinde bir Yetki Tablosu (TOA) alanı oluşturmak karmaşık bir bulmacayı bir araya getirmek gibi hissettirebilir. Ancak, .NET için Aspose.Words'ün yardımıyla süreç sorunsuz ve basit hale gelir. Bu makalede, bir belge oluşturucu kullanmadan TOA alanı ekleme adımlarında size rehberlik edeceğiz ve Word belgelerinizdeki alıntılarınızı ve yasal referanslarınızı yönetmenizi kolaylaştıracağız.

## Ön koşullar

Eğitime başlamadan önce, ihtiyacınız olacak temel bilgileri ele alalım:

- Aspose.Words for .NET: En son sürümün yüklü olduğundan emin olun. Bunu şuradan indirebilirsiniz: [Aspose web sitesi](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio gibi .NET uyumlu bir IDE.
- Temel C# Bilgisi: Temel C# sözdizimini ve kavramlarını anlamak faydalı olacaktır.
- Örnek Word Belgesi: TOA alanını eklemek istediğiniz yere bir örnek belge oluşturun veya hazır bulundurun.

## Ad Alanlarını İçe Aktar

Başlamak için, Aspose.Words kütüphanesinden gerekli ad alanlarını içe aktarmanız gerekir. Bu kurulum, belge düzenleme için gereken tüm sınıflara ve yöntemlere erişiminizin olmasını sağlar.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Fields;
```

Süreci basit, takip etmesi kolay adımlara bölelim. Her aşamada size rehberlik edeceğiz, her kod parçasının ne yaptığını ve TOA alanının oluşturulmasına nasıl katkıda bulunduğunu açıklayacağız.

## Adım 1: Belgeyi Başlatın

İlk olarak, bir örnek oluşturmanız gerekir `Document` sınıf. Bu nesne üzerinde çalıştığınız Word belgesini temsil eder.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
```

Bu kod yeni bir Word belgesi başlatır. Bunu, içeriğinizi ekleyeceğiniz boş bir tuval oluşturmak olarak düşünebilirsiniz.

## Adım 2: TA Alanını Oluşturun ve Yapılandırın

Sonra, bir TA (Yetki Tablosu) alanı ekleyeceğiz. Bu alan, TOA'da görünecek girdileri işaretler.

```csharp
Paragraph para = new Paragraph(doc);

// TA ve TOA alanlarını şu şekilde eklemek istiyoruz:
// { TA \c 1 \l "Değer 0" }
FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);
fieldTA.EntryCategory = "1";
fieldTA.LongCitation = "Value 0";

doc.FirstSection.Body.AppendChild(para);
```

İşte bir özet:
- Paragraf para = new Paragraph(doc);: Belge içerisinde yeni bir paragraf oluşturur.
- FieldTA fieldTA = (FieldTA) para.AppendField(FieldType.FieldTOAEntry, false);: Paragrafa bir TA alanı ekler. `FieldType.FieldTOAEntry` bunun bir TOA giriş alanı olduğunu belirtir.
- fieldTA.EntryCategory = "1";: Giriş kategorisini ayarlar. Bu, farklı giriş türlerini kategorilere ayırmak için yararlıdır.
- fieldTA.LongCitation = "Value 0";: Uzun alıntı metnini belirtir. Bu, TOA'da görünecek metindir.
- doc.FirstSection.Body.AppendChild(para);: TA alanını içeren paragrafı belgenin gövdesine ekler.

## Adım 3: TOA Alanını Ekleyin

Şimdi, tüm TA girdilerini bir tabloya derleyen gerçek TOA alanını ekleyeceğiz.

```csharp
para = new Paragraph(doc);

FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);
fieldToa.EntryCategory = "1";
doc.FirstSection.Body.AppendChild(para);
```

Bu adımda:
- FieldToa fieldToa = (FieldToa) para.AppendField(FieldType.FieldTOA, false);: Paragrafa bir TOA alanı ekler.
- fieldToa.EntryCategory = "1";: Girişleri yalnızca "1" kategorisiyle işaretlenenleri içerecek şekilde filtreler.

## Adım 4: TOA Alanını Güncelleyin

TOA alanını ekledikten sonra, en son girdileri yansıttığından emin olmak için güncellemeniz gerekir.

```csharp
fieldToa.Update();
```

Bu komut TOA alanını yeniler ve tüm işaretli girişlerin tabloda doğru şekilde görüntülenmesini sağlar.

## Adım 5: Belgeyi Kaydedin

Son olarak belgenizi yeni eklenen TOA alanıyla kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithFields.InsertTOAFieldWithoutDocumentBuilder.docx");
```

Bu kod satırı belgeyi belirtilen dizine kaydeder. Değiştirdiğinizden emin olun `"YOUR DOCUMENT DIRECTORY"` dosyanızı kaydetmek istediğiniz gerçek yol ile.

## Çözüm

Ve işte karşınızda! Bir belge oluşturucu kullanmadan bir Word belgesine TOA alanını başarıyla eklediniz. Bu adımları izleyerek, yasal belgelerinizde alıntıları etkili bir şekilde yönetebilir ve kapsamlı yetki tabloları oluşturabilirsiniz. .NET için Aspose.Words bu süreci pürüzsüz ve verimli hale getirerek karmaşık belge görevlerini kolayca halletmeniz için gereken araçları sağlar.

## SSS

### Farklı kategorilere sahip birden fazla TA alanı ekleyebilir miyim?
Evet, farklı kategorilere sahip birden fazla TA alanını ayarlayarak ekleyebilirsiniz. `EntryCategory` mülkiyet buna göre.

### TOA'nın görünümünü nasıl özelleştirebilirim?
Giriş biçimlendirmesi ve kategori etiketleri gibi TOA alanının özelliklerini değiştirerek TOA'nın görünümünü özelleştirebilirsiniz.

### TOA alanını otomatik olarak güncellemek mümkün müdür?
TOA alanını manuel olarak güncelleyebilirsiniz. `Update` yöntem, Aspose.Words şu anda belge değişikliklerinde otomatik güncellemeleri desteklemiyor.

### Belgenin belirli bölümlerine program aracılığıyla TA alanları ekleyebilir miyim?
Evet, istediğiniz paragraflara veya bölümlere yerleştirerek belirli yerlere TA alanları ekleyebilirsiniz.

### Tek bir belgede birden fazla TOA alanını nasıl işlerim?
Farklı TOA alanlarını atayarak birden fazla TOA alanını yönetebilirsiniz. `EntryCategory` değerlerinin sağlanması ve her TOA alanının kendi kategorisine göre girdileri filtrelemesi.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}