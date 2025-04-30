---
"description": "Bu kapsamlı kılavuzla, Aspose.Words for .NET kullanarak hücredeki düzeni nasıl ayarlayacağınızı öğrenin. Word belgelerini özelleştirmek isteyen geliştiriciler için mükemmeldir."
"linktitle": "Hücredeki Düzen"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Hücredeki Düzen"
"url": "/tr/net/programming-with-shapes/layout-in-cell/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Hücredeki Düzen

## giriiş

Word belgelerinizdeki tablo hücrelerinin düzenini programatik olarak ince ayarlamak istediyseniz, doğru yerdesiniz. Bugün, .NET için Aspose.Words kullanarak hücredeki düzeni nasıl ayarlayacağımıza dalacağız. Kolayca takip edebilmeniz için adım adım parçalara ayırarak pratik bir örnek üzerinden gideceğiz.

## Ön koşullar

Koda geçmeden önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

1. Aspose.Words for .NET: Aspose.Words for .NET kütüphanesinin yüklü olduğundan emin olun. Eğer yüklü değilse, [buradan indirin](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: .NET ile kurulmuş bir geliştirme ortamına ihtiyacınız olacak. Öneriler arıyorsanız Visual Studio harika bir seçimdir.
3. Temel C# Bilgisi: Her adımı açıklayacağım ancak temel C# bilgisine sahip olmak, takip etmenizi kolaylaştıracaktır.
4. Belge Dizini: Belgelerinizi kaydedeceğiniz bir dizin yolu hazırlayın. Buna şu şekilde atıfta bulunacağız: `YOUR DOCUMENT DIRECTORY`.

## Ad Alanlarını İçe Aktar

Başlamak için projenize gerekli ad alanlarını içe aktardığınızdan emin olun:

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Drawing;
using Aspose.Words.Tables;
```

Süreci yönetilebilir adımlara bölelim.

## Adım 1: Yeni Bir Belge Oluşturun

İlk olarak yeni bir Word belgesi oluşturacağız ve bir `DocumentBuilder` İçeriğimizi oluşturmamıza yardımcı olacak nesne.

```csharp
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

## Adım 2: Bir Tablo Başlatın ve Satır Biçimini Ayarlayın

Bir tablo oluşturmaya başlayacağız ve satırlar için yüksekliği ve yükseklik kuralını belirleyeceğiz.

```csharp
builder.StartTable();
builder.RowFormat.Height = 100;
builder.RowFormat.HeightRule = HeightRule.Exactly;
```

## Adım 3: Hücreleri Ekle ve İçerikle Doldur

Sonra, tabloya hücre eklemek için döngüye giriyoruz. Her 7 hücre için, yeni bir hücre oluşturmak üzere satırı sonlandıracağız.

```csharp
for (int i = 0; i < 31; i++)
{
    if (i != 0 && i % 7 == 0) builder.EndRow();
    builder.InsertCell();
    builder.Write("Cell contents");
}
builder.EndTable();
```

## Adım 4: Filigran Şekli Ekle

Şimdi, belgemize bir filigran ekleyelim. Bir tane oluşturacağız `Shape` nesneyi seçin ve özelliklerini ayarlayın.

```csharp
Shape watermark = new Shape(doc, ShapeType.TextPlainText)
{
    RelativeHorizontalPosition = RelativeHorizontalPosition.Page,
    RelativeVerticalPosition = RelativeVerticalPosition.Page,
    IsLayoutInCell = true, // Şekil bir hücreye yerleştirilecekse, onu tablo hücresinin dışında görüntüle.
    Width = 300,
    Height = 70,
    HorizontalAlignment = HorizontalAlignment.Center,
    VerticalAlignment = VerticalAlignment.Center,
    Rotation = -40
};
```

## Adım 5: Filigran Görünümünü Özelleştirin

Filigranın görünümünü, renk ve metin özelliklerini ayarlayarak daha da özelleştireceğiz.

```csharp
watermark.FillColor = Color.Gray;
watermark.StrokeColor = Color.Gray;
watermark.TextPath.Text = "watermarkText";
watermark.TextPath.FontFamily = "Arial";
watermark.Name = $"WaterMark_{Guid.NewGuid()}";
watermark.WrapType = WrapType.None;
```

## Adım 6: Belgeye Filigran Ekleme

Belgedeki son çalışmayı bulup o noktaya filigranı ekleyeceğiz.

```csharp
Run run = doc.GetChildNodes(NodeType.Run, true)[doc.GetChildNodes(NodeType.Run, true).Count - 1] as Run;
builder.MoveTo(run);
builder.InsertNode(watermark);
```

## Adım 7: Word 2010 için Belgeyi Optimize Etme

Uyumluluğu sağlamak için belgeyi Word 2010 için optimize edeceğiz.

```csharp
doc.CompatibilityOptions.OptimizeFor(MsWordVersion.Word2010);
```

## Adım 8: Belgeyi Kaydedin

Son olarak belgemizi belirtilen dizine kaydedeceğiz.

```csharp
doc.Save(dataDir + "WorkingWithShapes.LayoutInCell.docx");
```

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak özelleştirilmiş bir tablo düzeniyle bir Word belgesi oluşturdunuz ve bir filigran eklediniz. Bu eğitim, sürecin her bir bölümünü anlamanıza yardımcı olmak için net, adım adım bir kılavuz sağlamayı amaçlıyor. Bu becerilerle artık daha karmaşık ve özelleştirilmiş Word belgelerini programatik olarak oluşturabilirsiniz.

## SSS

### Filigran metni için farklı bir yazı tipi kullanabilir miyim?
Evet, yazı tipini ayarlayarak değiştirebilirsiniz. `watermark.TextPath.FontFamily` istediğiniz yazı tipine dönüştürebilirsiniz.

### Filigranın konumunu nasıl ayarlarım?
Şunu değiştirebilirsiniz: `RelativeHorizontalPosition`, `RelativeVerticalPosition`, `HorizontalAlignment`, Ve `VerticalAlignment` filigranın konumunu ayarlamak için özellikler.

### Filigran için metin yerine resim kullanmak mümkün müdür?
Kesinlikle! Bir tane yaratabilirsiniz `Shape` tip ile `ShapeType.Image` ve görüntüsünü kullanarak ayarlayın `ImageData.SetImage` yöntem.

### Değişen satır yüksekliklerine sahip tablolar oluşturabilir miyim?
Evet, her satır için farklı yükseklikler belirleyebilirsiniz. `RowFormat.Height` Hücreleri o satıra eklemeden önce özelliği.

### Belgeden filigranı nasıl kaldırabilirim?
Filigranı, belgenin şekiller koleksiyonunda bulup çağırarak kaldırabilirsiniz. `Remove` yöntem.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}