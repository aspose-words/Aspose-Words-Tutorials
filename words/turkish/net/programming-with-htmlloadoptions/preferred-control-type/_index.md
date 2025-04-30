---
"description": "Aspose.Words for .NET kullanarak bir Word belgesine birleşik kutu form alanı eklemeyi öğrenin. Sorunsuz HTML içerik entegrasyonu için bu adım adım kılavuzu izleyin."
"linktitle": "Word Belgesinde Tercih Edilen Kontrol Türü"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Word Belgesinde Tercih Edilen Kontrol Türü"
"url": "/tr/net/programming-with-htmlloadoptions/preferred-control-type/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Word Belgesinde Tercih Edilen Kontrol Türü

## giriiş

Aspose.Words for .NET'te HTML yükleme seçenekleriyle nasıl çalışılacağına dair heyecan verici bir eğitime dalıyoruz, özellikle Word belgesine birleşik kutu form alanı eklerken tercih edilen denetim türünü ayarlamaya odaklanıyoruz. Bu adım adım kılavuz, Aspose.Words for .NET kullanarak Word belgelerinizdeki HTML içeriğini etkili bir şekilde nasıl işleyeceğinizi ve oluşturacağınızı anlamanıza yardımcı olacaktır.

## Ön koşullar

Koda geçmeden önce, yerinde olması gereken birkaç şey var:

1. Aspose.Words for .NET: Aspose.Words for .NET kütüphanesinin yüklü olduğundan emin olun. Bunu şuradan indirebilirsiniz: [web sitesi](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi bir geliştirme ortamı kurmuş olmanız gerekir.
3. Temel C# Bilgisi: Eğitimi takip edebilmek için C# programlamanın temellerine dair bir anlayışa sahip olmak gerekir.
4. HTML İçeriği: Bu örnekte HTML içeriğiyle çalışacağımız için temel HTML bilgisine sahip olmak faydalı olacaktır.

## Ad Alanlarını İçe Aktar

Öncelikle başlamak için gerekli ad alanlarını içe aktaralım:

```csharp
using System;
using System.IO;
using System.Text;
using Aspose.Words;
using Aspose.Words.Loading;
```

Şimdi, açıklık ve anlaşılırlığı sağlamak için örneği birden fazla adıma bölelim.

## Adım 1: HTML İçeriğinizi Ayarlayın

Öncelikle Word belgesine eklemek istediğimiz HTML içeriğini tanımlamamız gerekiyor. Kullanacağımız HTML kod parçacığı şu şekilde:

```csharp
const string html = @"
    <html>
        <select name='ComboBox' size='1'>
            <option value='val1'>item1</option>
            <option value='val2'></option>                        
        </select>
    </html>
";
```

Bu HTML, iki seçeneğe sahip basit bir birleşik kutu içerir. Bu HTML'yi bir Word belgesine yükleyeceğiz ve nasıl işleneceğini belirteceğiz.

## Adım 2: Belge Dizinini Tanımlayın

Sonra, Word belgenizin kaydedileceği dizini belirtin. Bu, dosyalarınızı düzenlemenize ve yol yönetimini temiz tutmanıza yardımcı olur.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

Yer değiştirmek `"YOUR DOCUMENT DIRECTORY"` Word belgenizi kaydetmek istediğiniz gerçek yol ile.

## Adım 3: HTML Yükleme Seçeneklerini Yapılandırın

Burada, özellikle HTML yükleme seçeneklerini yapılandırıyoruz. `PreferredControlType` özellik. Bu, birleşik kutunun Word belgesinde nasıl işleneceğini belirler.

```csharp
HtmlLoadOptions loadOptions = new HtmlLoadOptions { PreferredControlType = HtmlControlType.StructuredDocumentTag };
```

Ayarlayarak `PreferredControlType` ile `HtmlControlType.StructuredDocumentTag`, Word belgesinde birleşik kutunun yapılandırılmış belge etiketi (SDT) olarak görüntülenmesini sağlıyoruz.

## Adım 4: HTML İçeriğini Belgeye Yükleyin

Yapılandırılan yükleme seçeneklerini kullanarak HTML içeriğini yeni bir Word belgesine yüklüyoruz.

```csharp
Document doc = new Document(new MemoryStream(Encoding.UTF8.GetBytes(html)), loadOptions);
```

Burada, HTML dizesini bir bayt dizisine dönüştürüyoruz ve bir bellek akışı kullanarak belgeye yüklüyoruz. Bu, HTML içeriğinin Aspose.Words tarafından doğru şekilde yorumlanmasını ve işlenmesini sağlar.

## Adım 5: Belgeyi Kaydedin

Son olarak belgeyi DOCX formatında belirtilen dizine kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithHtmlLoadOptions.PreferredControlType.docx", SaveFormat.Docx);
```

Bu, Word belgesini, oluşturulan birleşik kutu denetimiyle birlikte belirtilen konuma kaydeder.

## Çözüm

İşte karşınızda! HTML yükleme seçeneklerinden yararlanarak Aspose.Words for .NET kullanarak bir Word belgesine birleşik kutu form alanı başarıyla ekledik. Bu adım adım kılavuz, süreci anlamanıza ve projelerinize uygulamanıza yardımcı olacaktır. İster belge oluşturmayı otomatikleştirin, ister HTML içeriğini işleyin, Aspose.Words for .NET hedeflerinize ulaşmanız için güçlü araçlar sunar.

## SSS

### Aspose.Words for .NET nedir?
Aspose.Words for .NET, geliştiricilerin Word belgelerini programlı bir şekilde oluşturmalarına, düzenlemelerine, dönüştürmelerine ve işlemelerine olanak tanıyan güçlü bir belge düzenleme kütüphanesidir.

### Aspose.Words for .NET ile diğer HTML kontrol tiplerini kullanabilir miyim?
Evet, Aspose.Words for .NET çeşitli HTML denetim türlerini destekler. Word belgesinde farklı denetimlerin nasıl işleneceğini özelleştirebilirsiniz.

### Aspose.Words for .NET'te karmaşık HTML içeriğini nasıl işlerim?
Aspose.Words for .NET, karmaşık öğeler de dahil olmak üzere HTML için kapsamlı destek sağlar. `HtmlLoadOptions` Belirli HTML içeriğinizi uygun şekilde işlemek için.

### Daha fazla örnek ve dokümanı nerede bulabilirim?
Ayrıntılı dokümanları ve örnekleri şu adreste bulabilirsiniz: [Aspose.Words for .NET dokümantasyon sayfası](https://reference.aspose.com/words/net/).

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?
Evet, ücretsiz deneme sürümünü şu adresten indirebilirsiniz: [Aspose web sitesi](https://releases.aspose.com/).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}