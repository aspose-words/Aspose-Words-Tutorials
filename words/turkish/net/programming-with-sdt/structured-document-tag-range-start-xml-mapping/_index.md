---
"description": "Aspose.Words for .NET kullanarak Word'de XML verilerini yapılandırılmış belge etiketlerine dinamik olarak nasıl bağlayacağınızı öğrenin. Adım adım kılavuzumuzu izleyin."
"linktitle": "Yapılandırılmış Belge Etiket Aralığı Başlat Xml Eşlemesi"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Yapılandırılmış Belge Etiket Aralığı Başlat Xml Eşlemesi"
"url": "/tr/net/programming-with-sdt/structured-document-tag-range-start-xml-mapping/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Yapılandırılmış Belge Etiket Aralığı Başlat Xml Eşlemesi

## giriiş

XML verilerini dinamik olarak bir Word belgesine eklemek istediniz mi hiç? Şanslısınız! Aspose.Words for .NET bu görevi çocuk oyuncağı haline getiriyor. Bu eğitimde, yapılandırılmış belge etiketi aralığı başlangıç XML eşlemesine derinlemesine dalıyoruz. Bu özellik, özel XML parçalarını içerik denetimlerine bağlamanızı ve belge içeriğinizin XML verilerinizle sorunsuz bir şekilde güncellenmesini sağlar. Belgelerinizi dinamik şaheserlere dönüştürmeye hazır olun.

## Ön koşullar

Kodlama kısmına geçmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET Kütüphanesi: En son sürüme sahip olduğunuzdan emin olun. İndirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya C# destekleyen herhangi bir IDE.
3. Temel C# Bilgisi: C# programlamaya aşinalık şarttır.
4. Word Belgesi: Üzerinde çalışabileceğiniz örnek bir Word belgesi.

## Ad Alanlarını İçe Aktar

İlk önce gerekli ad alanlarını içe aktaralım. Bu, .NET için Aspose.Words'deki tüm gerekli sınıflara ve yöntemlere erişimimizi sağlayacaktır.

```csharp
using System;
using Aspose.Words;
using Aspose.Words.Markup;
using System.Text;
```

## Adım 1: Belge Dizininizi Ayarlayın

Her projenin bir temele ihtiyacı vardır, değil mi? Burada, belge dizininize giden yolu ayarlıyoruz.

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Word Belgesini Yükleyin

Sonra, Word belgesini yüklüyoruz. Bu, XML verilerimizi ekleyeceğimiz belgedir.

```csharp
Document doc = new Document(dataDir + "Multi-section structured document tags.docx");
```

## Adım 3: Özel XML Parçası Ekle

Eklemek istediğimiz verileri içeren bir XML parçası oluşturmamız ve bunu belgenin CustomXmlPart koleksiyonuna eklememiz gerekiyor. Bu özel XML parçası yapılandırılmış belge etiketlerimiz için veri kaynağı görevi görecek.

### XML Parçası Oluşturma

Öncelikle XML parçası için benzersiz bir ID oluşturalım ve içeriğini tanımlayalım.

```csharp
// Veri içeren bir XML parçası oluşturun ve bunu belgenin CustomXmlPart koleksiyonuna ekleyin.
string xmlPartId = Guid.NewGuid().ToString("B");
string xmlPartContent = "<root><text>Text element #1</text><text>Text element #2</text></root>";
CustomXmlPart xmlPart = doc.CustomXmlParts.Add(xmlPartId, xmlPartContent);
```

### XML Parça İçeriğini Doğrulayın

XML kısmının doğru şekilde eklendiğinden emin olmak için içeriğini yazdırıyoruz.

```csharp
Console.WriteLine(Encoding.UTF8.GetString(xmlPart.Data));
```

## Adım 4: Yapılandırılmış Belge Etiketi Oluşturun

Yapılandırılmış Belge Etiketi (SDT), bir XML parçasına bağlanabilen bir içerik denetimidir. Burada, özel XML parçamızın içeriklerini görüntüleyecek bir SDT oluşturuyoruz.

Öncelikle belgede SDT aralığının başlangıcını bulun.

```csharp
StructuredDocumentTagRangeStart sdtRangeStart = (StructuredDocumentTagRangeStart)doc.GetChild(NodeType.StructuredDocumentTagRangeStart, 0, true);
```

## Adım 5: SDT için XML Eşlemesini Ayarlayın

Şimdi, XML parçamızı SDT'ye bağlamanın zamanı geldi. Bir XML eşlemesi ayarlayarak, XML verisinin hangi kısmının SDT'de gösterileceğini belirtiyoruz.

XPath, görüntülemek istediğimiz XML bölümündeki belirli öğeye işaret eder. Burada, ikinci öğeye işaret ediyoruz `<text>` içindeki öğe `<root>` öğe.

```csharp
// StructuredDocumentTag için bir eşleme ayarlayın
sdtRangeStart.XmlMapping.SetMapping(xmlPart, "/root[1]/text[2]", null);
```

## Adım 6: Belgeyi Kaydedin

Son olarak, değişiklikleri eylem halinde görmek için belgeyi kaydedin. Word belgesindeki SDT artık belirtilen XML içeriğini görüntüleyecektir.

```csharp
doc.Save(dataDir + "WorkingWithSdt.StructuredDocumentTagRangeStartXmlMapping.docx");
```

## Çözüm

İşte karşınızda! Aspose.Words for .NET kullanarak bir XML parçasını Word belgesindeki yapılandırılmış bir belge etiketine başarıyla eşlediniz. Bu güçlü özellik, dinamik ve veri odaklı belgeleri zahmetsizce oluşturmanızı sağlar. İster raporlar, ister faturalar veya başka bir belge türü üretiyor olun, XML eşleme iş akışınızı önemli ölçüde kolaylaştırabilir.

## SSS

### Word'de yapılandırılmış belge etiketi nedir?
Yapılandırılmış belge etiketleri, içerik denetimleri olarak da bilinir, Word belgelerindeki belirli içerik türleri için kapsayıcılardır. Verileri bağlamak, düzenlemeyi kısıtlamak veya kullanıcıları belge oluşturmada yönlendirmek için kullanılabilirler.

### XML parçasının içeriğini dinamik olarak nasıl güncelleyebilirim?
XML parçası içeriğini değiştirerek güncelleyebilirsiniz. `xmlPartContent` dizeyi belgeye eklemeden önce. Dizeyi yeni verilerle güncelleyin ve ekleyin `CustomXmlParts` koleksiyon.

### Aynı belgedeki farklı SDT'lere birden fazla XML parçası bağlayabilir miyim?
Evet, aynı belgedeki farklı SDT'lere birden fazla XML parçası bağlayabilirsiniz. Her SDT'nin kendine özgü XML parçası ve XPath eşlemesi olabilir.

### Karmaşık XML yapılarını SDT'lere eşlemek mümkün müdür?
Kesinlikle! Karmaşık XML yapılarını, XML parçası içindeki istenen öğelere doğru bir şekilde işaret eden ayrıntılı XPath ifadelerini kullanarak SDT'lere eşleyebilirsiniz.

### Bir belgeden XML parçasını nasıl kaldırabilirim?
Bir XML parçasını, çağırarak kaldırabilirsiniz. `Remove` yöntem üzerinde `CustomXmlParts` koleksiyon, geçiş `xmlPartId` Kaldırmak istediğiniz XML parçasının.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}