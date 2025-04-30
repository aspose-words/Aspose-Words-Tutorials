---
"description": "Aspose.Words for .NET kullanarak Word'de bir tabloya anahat kenarlığı nasıl uygulanacağını öğrenin. Mükemmel tablo biçimlendirmesi için adım adım kılavuzumuzu izleyin."
"linktitle": "Anahat Sınırını Uygula"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Anahat Sınırını Uygula"
"url": "/tr/net/programming-with-table-styles-and-formatting/apply-outline-border/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Anahat Sınırını Uygula

## giriiş

Bugünkü eğitimde, .NET için Aspose.Words kullanarak belge düzenleme dünyasına dalacağız. Özellikle, bir Word belgesindeki bir tabloya anahat kenarlığı nasıl uygulanacağını öğreneceğiz. Otomatik belge oluşturma ve biçimlendirmeyle sık sık çalışıyorsanız, bu araç setinizde bulunması gereken harika bir beceridir. O halde, tablolarınızı yalnızca işlevsel değil, aynı zamanda görsel olarak da çekici hale getirme yolculuğuna başlayalım.

## Ön koşullar

Koda geçmeden önce ihtiyacınız olacak birkaç şey var:

1. Aspose.Words for .NET: Aspose.Words for .NET'in yüklü olması gerekir. İndirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio gibi uygun bir geliştirme ortamı.
3. Temel C# Bilgisi: C# hakkında temel bir anlayışa sahip olmak, eğitimi takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Başlamak için, gerekli ad alanlarının içe aktarıldığından emin olun. Bu, Aspose.Words işlevlerine erişim için çok önemlidir.

```csharp
using System;
using System.Drawing;
using Aspose.Words;
using Aspose.Words.Tables;
```

Süreci basit ve yönetilebilir adımlara bölelim.

## Adım 1: Belgeyi Yükleyin

Öncelikle biçimlendirmek istediğimiz tablonun bulunduğu Word belgesini yüklememiz gerekiyor.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Tables.docx");
```

Bu adımda şunu kullanıyoruz: `Document` Mevcut bir belgeyi yüklemek için Aspose.Words sınıfından değiştirin `"YOUR DOCUMENT DIRECTORY"` Belgenizin saklandığı gerçek yol ile.

## Adım 2: Tabloya Erişim

Daha sonra biçimlendirmek istediğimiz belirli tabloya erişmemiz gerekiyor. 

```csharp
Table table = (Table)doc.GetChild(NodeType.Table, 0, true);
```

Burada, `GetChild` yöntem belgedeki ilk tabloyu getirir. Parametreler `NodeType.Table, 0, true` doğru düğüm türünü aldığımızdan emin olalım.

## Adım 3: Tabloyu Hizalayın

Şimdi tabloyu sayfanın ortasına hizalayalım.

```csharp
table.Alignment = TableAlignment.Center;
```

Bu adım masanın düzgün bir şekilde ortalanmasını sağlayarak profesyonel bir görünüm kazandırır.

## Adım 4: Mevcut Sınırları Temizle

Yeni sınırlar uygulamadan önce mevcut sınırları temizlememiz gerekiyor.

```csharp
table.ClearBorders();
```

Sınırların temizlenmesi, eski stillerin karışmasına izin vermeden yeni sınırlarımızın temiz bir şekilde uygulanmasını sağlar.

## Adım 5: Anahat Sınırlarını Ayarlayın

Şimdi yeşil dış hat kenarlıklarını tabloya uygulayalım.

```csharp
table.SetBorder(BorderType.Left, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Right, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Top, LineStyle.Single, 1.5, Color.Green, true);
table.SetBorder(BorderType.Bottom, LineStyle.Single, 1.5, Color.Green, true);
```

Her sınır türü (sol, sağ, üst, alt) ayrı ayrı ayarlanır. Biz `LineStyle.Single` sağlam bir çizgi için, `1.5` çizgi genişliği için ve `Color.Green` kenarlık rengi için.

## Adım 6: Hücre Gölgelendirmesini Uygula

Tabloyu görsel olarak daha ilgi çekici hale getirmek için hücreleri açık yeşil renkle dolduralım.

```csharp
table.SetShading(TextureIndex.TextureSolid, Color.LightGreen, Color.Empty);
```

Burada, `SetShading` Hücrelere açık yeşil renkte düz bir renk uygulayarak tablonun belirginleşmesini sağlamak için kullanılır.

## Adım 7: Belgeyi Kaydedin

Son olarak değiştirilen belgeyi kaydedin.

```csharp
doc.Save(dataDir + "WorkingWithTableStylesAndFormatting.ApplyOutlineBorder.docx");
```

Bu adım, belgenizi uygulanan biçimlendirmeyle kaydeder. Güzel biçimlendirilmiş tabloyu görmek için açabilirsiniz.

## Çözüm

Ve işte oldu! Bu adımları izleyerek, .NET için Aspose.Words kullanarak bir Word belgesindeki tabloya başarılı bir şekilde bir anahat kenarlığı uyguladınız. Bu eğitim, belgeyi yüklemeyi, tabloya erişmeyi, hizalamayı, mevcut kenarlıkları temizlemeyi, yeni kenarlıklar uygulamayı, hücre gölgelendirmesi eklemeyi ve son olarak belgeyi kaydetmeyi kapsıyordu. 

Bu becerilerle tablolarınızın görsel sunumunu geliştirebilir, belgelerinizi daha profesyonel ve çekici hale getirebilirsiniz. Mutlu kodlamalar!

## SSS

### Tablonun her kenarına farklı stiller uygulayabilir miyim?  
Evet, parametreleri ayarlayarak her kenarlığa farklı stiller ve renkler uygulayabilirsiniz. `SetBorder` yöntem.

### Kenarlığın genişliğini nasıl değiştirebilirim?  
Üçüncü parametreyi değiştirerek genişliği değiştirebilirsiniz. `SetBorder` yöntem. Örneğin, `1.5` 1,5 puanlık bir genişlik ayarlar.

### Tek tek hücrelere gölgelendirme uygulamak mümkün müdür?  
Evet, her bir hücreye erişip, gölgelendirmeyi tek tek hücrelere uygulayabilirsiniz. `SetShading` yöntem.

### Kenarlıklar ve gölgelendirme için başka renkler kullanabilir miyim?  
Kesinlikle! Mevcut olan herhangi bir rengi kullanabilirsiniz. `System.Drawing.Color` sınıf.

### Tabloyu yatay olarak nasıl ortaya hizalarım?  
The `table.Alignment = TableAlignment.Center;` Koddaki satır tabloyu sayfada yatay olarak ortalar.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}