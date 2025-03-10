---
title: Köşeler Kesildi Ekle
linktitle: Köşeler Kesildi Ekle
second_title: Aspose.Words Belge İşleme API'si
description: Aspose.Words for .NET kullanarak Word belgelerinize köşeleri kesilmiş bir şeklin nasıl ekleneceğini öğrenin. Bu adım adım kılavuz, belgelerinizi kolayca geliştirebilmenizi sağlar.
weight: 10
url: /tr/net/programming-with-shapes/add-corners-snipped/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Köşeler Kesildi Ekle

## giriiş

Word belgelerinize özel şekiller eklemek, önemli bilgileri vurgulamanın veya içeriğinize biraz gösteriş katmanın eğlenceli ve görsel olarak çekici bir yolu olabilir. Bu eğitimde, Aspose.Words for .NET kullanarak Word belgelerinize "Corners Snpped" şekillerini nasıl ekleyebileceğinizi inceleyeceğiz. Bu kılavuz, bu şekilleri zahmetsizce ekleyebilmenizi ve belgelerinizi bir profesyonel gibi özelleştirebilmenizi sağlayarak her adımda size yol gösterecektir.

## Ön koşullar

Koda geçmeden önce, başlamak için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1.  Aspose.Words for .NET: Eğer henüz yapmadıysanız, en son sürümü şu adresten indirin:[Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Geliştirme ortamınızı kurun. Visual Studio popüler bir seçimdir, ancak .NET'i destekleyen herhangi bir IDE'yi kullanabilirsiniz.
3.  Lisans: Sadece deney yapıyorsanız, bir[ücretsiz deneme](https://releases.aspose.com/) veya bir tane al[geçici lisans](https://purchase.aspose.com/temporary-license/) tüm işlevlerin kilidini açmak için.
4. C# Temel Anlayışı: C# programlamaya aşinalık, örnekleri takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Aspose.Words for .NET ile çalışmaya başlamadan önce, gerekli ad alanlarını içe aktarmamız gerekir. Bunları C# dosyanızın en üstüne ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Şimdi, "Köşeler Kesildi" şekli ekleme sürecini birden fazla adıma bölelim. Her şeyin düzgün çalıştığından emin olmak için bu adımları yakından izleyin.

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

 Yapmamız gereken ilk şey yeni bir belge oluşturmak ve bir`DocumentBuilder` nesne. Bu oluşturucu, belgemize içerik eklememize yardımcı olacak.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Bu adımda, belgemizi ve oluşturucumuzu ayarladık. Şunu düşünün`DocumentBuilder` Word belgenizde yazmaya ve çizmeye hazır dijital kaleminiz olarak.

## Adım 2: Köşeleri Kesilmiş Şekli Yerleştirin

 Daha sonra şunu kullanacağız:`DocumentBuilder` "Köşeler Kesildi" şekli eklemek için. Bu şekil türü Aspose.Words'de önceden tanımlanmıştır ve tek bir kod satırıyla kolayca eklenebilir.

```csharp
builder.InsertShape(ShapeType.TopCornersSnipped, 50, 50);
```

Burada şekil türünü ve boyutlarını (50x50) belirtiyoruz. Belgenize küçük, mükemmel kesilmiş bir köşe etiketi yerleştirdiğinizi düşünün. 

## Adım 3: Uyumluluk ile Kaydetme Seçeneklerini Tanımlayın

Belgemizi kaydetmeden önce, belgemizin belirli standartlara uymasını sağlamak için kaydetme seçeneklerini tanımlamamız gerekir.`OoxmlSaveOptions` Bunun için bir sınıf.

```csharp
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(SaveFormat.Docx)
{
    Compliance = OoxmlCompliance.Iso29500_2008_Transitional
};
```

Bu kaydetme seçenekleri, uyumluluk ve belgenin uzun ömürlülüğü açısından kritik önem taşıyan ISO/IEC 29500:2008 standardına uygun belgelerimizin kullanılmasını sağlar.

## Adım 4: Belgeyi Kaydedin

Son olarak daha önce tanımladığımız kaydetme seçeneklerini kullanarak belgemizi belirtilen dizine kaydediyoruz.

```csharp
doc.Save(dataDir + "WorkingWithShapes.AddCornersSnipped.docx", saveOptions);
```

Ve böylece, belgeniz artık gerekli uyumluluk seçenekleriyle kaydedilmiş, özel bir "Köşeler Kesildi" şekli içeriyor.

## Çözüm

İşte oldu! Aspose.Words for .NET kullanarak Word belgelerinize özel şekiller eklemek basittir ve belgelerinizin görsel çekiciliğini büyük ölçüde artırabilir. Bu adımları izleyerek, kolayca bir "Köşeler Kesildi" şekli ekleyebilir ve belgenizin gerekli standartları karşıladığından emin olabilirsiniz. İyi kodlamalar!

## SSS

### "Köşeler Kesildi" şeklinin boyutunu özelleştirebilir miyim?
Evet, boyutları değiştirerek boyutu ayarlayabilirsiniz.`InsertShape` yöntem.

### Başka şekil türleri eklemek mümkün mü?
 Kesinlikle! Aspose.Words çeşitli şekilleri destekler. Sadece şunu değiştirin`ShapeType` İstediğiniz şekle getirin.

### Aspose.Words'ü kullanmak için lisansa ihtiyacım var mı?
Ücretsiz deneme veya geçici lisans kullanabilirsiniz ancak sınırsız kullanım için tam lisansa ihtiyacınız var.

### Şekilleri daha fazla nasıl şekillendirebilirim?
Şekillerin görünümünü ve davranışını özelleştirmek için Aspose.Words tarafından sağlanan ek özellikleri ve yöntemleri kullanabilirsiniz.

### Aspose.Words diğer formatlarla uyumlu mudur?
Evet, Aspose.Words DOCX, PDF, HTML ve daha fazlası dahil olmak üzere birden fazla belge biçimini destekler.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
