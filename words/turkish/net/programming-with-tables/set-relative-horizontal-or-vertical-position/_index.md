---
"description": "Bu adım adım kılavuzla, Aspose.Words for .NET'i kullanarak Word belgelerindeki tablolar için göreceli yatay ve dikey konumların nasıl ayarlanacağını öğrenin."
"linktitle": "Göreceli Yatay veya Dikey Pozisyonu Ayarla"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Göreceli Yatay veya Dikey Pozisyonu Ayarla"
"url": "/tr/net/programming-with-tables/set-relative-horizontal-or-vertical-position/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Göreceli Yatay veya Dikey Pozisyonu Ayarla

## giriiş

Word belgelerinizde tabloları istediğiniz şekilde nasıl konumlandıracağınız konusunda hiç sıkışmış hissettiniz mi? Eh, yalnız değilsiniz. İster profesyonel bir rapor ister şık bir broşür oluşturuyor olun, tabloları hizalamak büyük fark yaratabilir. İşte tam bu noktada Aspose.Words for .NET işe yarıyor. Bu eğitim, Word belgelerinizde tablolar için göreceli yatay veya dikey konumların nasıl ayarlanacağı konusunda size adım adım yol gösterecek. Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. Aspose.Words for .NET: Henüz indirmediyseniz, indirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET uyumlu IDE.
3. C# Temel Bilgisi: Bu eğitim, C# programlamanın temellerine aşina olduğunuzu varsayar.

## Ad Alanlarını İçe Aktar

İlk önce, gerekli ad alanlarını içe aktarmanız gerekir. Bu, Aspose.Words işlevlerine erişmek için önemlidir.

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

## Adım 1: Belgenizi Yükleyin

Başlamak için Word belgenizi programa yüklemeniz gerekir. Bunu şu şekilde yapabilirsiniz:

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document(dataDir + "Table wrapped by text.docx");
```

Bu kod parçacığı belge dizininize giden yolu ayarlar ve üzerinde çalışmak istediğiniz belirli belgeyi yükler. Herhangi bir yükleme sorununu önlemek için belge yolunuzun doğru olduğundan emin olun.

## Adım 2: Tabloya Erişim

Sonra, belge içindeki tabloya erişmemiz gerekir. Genellikle, gövde bölümündeki ilk tabloyla çalışmak istersiniz.

```csharp
Table table = doc.FirstSection.Body.Tables[0];
```

Bu kod satırı belgenin gövdesinden ilk tabloyu getirir. Belgenizde birden fazla tablo varsa, dizini buna göre ayarlayabilirsiniz.

## Adım 3: Yatay Pozisyonu Ayarlayın

Şimdi, tablonun yatay konumunu belirli bir öğeye göre ayarlayalım. Bu örnekte, onu sütuna göre konumlandıracağız.

```csharp
table.HorizontalAnchor = RelativeHorizontalPosition.Column;
```

Ayarlayarak `HorizontalAnchor` ile `RelativeHorizontalPosition.Column`, tabloya, bulunduğu sütuna göre yatay olarak hizalanmasını söylüyorsunuz.

## Adım 4: Dikey Pozisyonu Ayarlayın

Yatay konumlandırmaya benzer şekilde, dikey konumu da ayarlayabilirsiniz. Burada, onu sayfaya göre konumlandırıyoruz.

```csharp
table.VerticalAnchor = RelativeVerticalPosition.Page;
```

Ayarlama `VerticalAnchor` ile `RelativeVerticalPosition.Page` Tablonun sayfaya göre dikey olarak hizalanmasını sağlar.

## Adım 5: Belgenizi Kaydedin

Son olarak, değişikliklerinizi yeni bir belgeye kaydedin. Bu, değişikliklerinizin korunduğundan emin olmak için önemli bir adımdır.

```csharp
doc.Save(dataDir + "WorkingWithTables.SetFloatingTablePosition.docx");
```

Bu komut, değiştirilen belgeyi yeni bir adla kaydeder ve orijinal dosyanızın üzerine yazmamanızı sağlar.

## Çözüm

İşte oldu! Aspose.Words for .NET kullanarak bir Word belgesinde bir tablo için göreceli yatay ve dikey konumları başarıyla ayarladınız. Bu yeni kazanılan beceriyle, belgelerinizin düzenini ve okunabilirliğini geliştirebilir, daha profesyonel ve cilalı görünmelerini sağlayabilirsiniz. Farklı konumlarla denemeler yapmaya devam edin ve ihtiyaçlarınız için en iyi olanı görün.

## SSS

### Tabloları diğer öğelere göre konumlandırabilir miyim?  
Evet, Aspose.Words tabloları kenar boşlukları, sayfalar, sütunlar ve daha fazlası gibi çeşitli öğelere göre konumlandırmanıza olanak tanır.

### Aspose.Words for .NET'i kullanmak için lisansa ihtiyacım var mı?  
Evet, bir lisans satın alabilirsiniz [Burada](https://purchase.aspose.com/buy) veya geçici bir lisans alın [Burada](https://purchase.aspose.com/temporary-license/).

### Aspose.Words for .NET için ücretsiz deneme sürümü mevcut mu?  
Kesinlikle! Ücretsiz denemeyi indirebilirsiniz [Burada](https://releases.aspose.com/).

### Aspose.Words'ü diğer programlama dilleriyle kullanabilir miyim?  
Aspose.Words öncelikle .NET için tasarlanmıştır, ancak Java, Python ve diğer platformlar için de sürümleri mevcuttur.

### Daha detaylı dokümanları nerede bulabilirim?  
Daha ayrıntılı bilgi için Aspose.Words belgelerine bakın [Burada](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}