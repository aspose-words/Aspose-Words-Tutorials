---
title: Tercih Edilen Genişlik Ayarları
linktitle: Tercih Edilen Genişlik Ayarları
second_title: Aspose.Words Belge İşleme API'si
description: Bu adım adım kılavuzla Aspose.Words for .NET'te mutlak, göreli ve otomatik genişlik ayarlarına sahip tabloların nasıl oluşturulacağını öğrenin.
weight: 10
url: /tr/net/programming-with-tables/preferred-width-settings/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Tercih Edilen Genişlik Ayarları

## giriiş

Tablolar, Word belgelerinizdeki bilgileri düzenlemenin ve sunmanın güçlü bir yoludur. Aspose.Words for .NET'te tablolarla çalışırken, tablo hücrelerinin genişliğini belgenizin düzenine mükemmel şekilde uymasını sağlamak için birkaç seçeneğiniz vardır. Bu kılavuz, Aspose.Words for .NET kullanarak tercih edilen genişlik ayarlarıyla tablolar oluşturma sürecinde size yol gösterecek ve mutlak, göreli ve otomatik boyutlandırma seçeneklerine odaklanacaktır. 

## Ön koşullar

Eğitime başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1.  Aspose.Words for .NET: Geliştirme ortamınızda Aspose.Words for .NET'in yüklü olduğundan emin olun. İndirebilirsiniz[Burada](https://releases.aspose.com/words/net/).

2. .NET Geliştirme Ortamı: Visual Studio gibi bir .NET geliştirme ortamı kurun.

3. Temel C# Bilgisi: C# programlamaya aşina olmak, kod parçacıklarını ve örnekleri daha iyi anlamanıza yardımcı olacaktır.

4.  Aspose.Words Belgeleri: Şuraya bakın:[Aspose.Words Belgeleri](https://reference.aspose.com/words/net/) Ayrıntılı API bilgisi ve daha fazla bilgi için.

## Ad Alanlarını İçe Aktar

Kodlamaya başlamadan önce, gerekli ad alanlarını C# projenize aktarmanız gerekir:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Bu ad alanları, Aspose.Words'ün temel işlevlerine ve Table nesnesine erişim sağlayarak belge tablolarını düzenlemenize olanak tanır.

Farklı genişlik tercihlerine sahip bir tablo oluşturma sürecini anlaşılır ve yönetilebilir adımlara bölelim.

## Adım 1: Belgeyi ve Belge Oluşturucuyu Başlatın

Başlık: Yeni Bir Belge ve DocumentBuilder Oluşturma

 Açıklama: Yeni bir Word belgesi oluşturarak başlayın ve`DocumentBuilder` örnek.`DocumentBuilder` sınıfı, belgenize içerik eklemenin basit bir yolunu sağlar.

```csharp
// Belgenin kaydedileceği yolu tanımlayın.
string dataDir = "YOUR DOCUMENT DIRECTORY";

// Yeni bir Belge oluşturun.
Document doc = new Document();

// Bu Belge için bir DocumentBuilder oluşturun.
DocumentBuilder builder = new DocumentBuilder(doc);
```

 Burada, belgenin kaydedileceği dizini belirtirsiniz ve başlatırsınız.`Document` Ve`DocumentBuilder` nesneler.

## Adım 2: Mutlak Genişliğe Sahip İlk Tablo Hücresini Ekleyin

İlk hücreyi tabloya sabit 40 punto genişliğinde ekleyin. Bu, tablonun boyutundan bağımsız olarak bu hücrenin her zaman 40 punto genişliğini koruduğundan emin olmanızı sağlar.

```csharp
// Mutlak boyutlu bir hücre ekle.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPoints(40);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightYellow;
builder.Writeln("Cell at 40 points width");
```

Bu adımda, tabloyu oluşturmaya başlarsınız ve mutlak genişliğe sahip bir hücre eklersiniz.`PreferredWidth.FromPoints(40)` yöntem hücrenin genişliğini 40 noktaya ayarlar ve`Shading.BackgroundPatternColor` açık sarı bir arka plan rengi uygular.

## Adım 3: Göreceli Boyutlu Bir Hücre Ekle

Tablonun toplam genişliğinin %20'si genişliğinde başka bir hücre ekleyin. Bu göreli boyutlandırma, hücrenin tablonun genişliğine orantılı olarak ayarlanmasını sağlar.

```csharp
// Göreceli (yüzde) boyutlu bir hücre ekle.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.FromPercent(20);
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightBlue;
builder.Writeln("Cell at 20% width");
```

Bu hücrenin genişliği tablonun toplam genişliğinin %20'si kadar olacak ve bu sayede farklı ekran boyutlarına veya doküman düzenlerine uyum sağlayabilecek.

### Adım 4: Otomatik Boyutlandırılmış Bir Hücre Ekle

Son olarak, tabloda kalan kullanılabilir alana göre otomatik olarak boyutlandırılan bir hücre ekleyin.

```csharp
// Otomatik boyutlandırılmış bir hücre ekle.
builder.InsertCell();
builder.CellFormat.PreferredWidth = PreferredWidth.Auto;
builder.CellFormat.Shading.BackgroundPatternColor = Color.LightGreen;
builder.Writeln("Cell automatically sized. The size of this cell is calculated from the table preferred width.");
builder.Writeln("In this case the cell will fill up the rest of the available space.");
```

 The`PreferredWidth.Auto` ayar, diğer hücreler hesaba katıldıktan sonra kalan boşluğa göre bu hücrenin genişlemesine veya daralmasına izin verir. Bu, tablo düzeninin dengeli ve profesyonel görünmesini sağlar.

## Adım 5: Belgeyi Sonlandırın ve Kaydedin

Tüm hücrelerinizi ekledikten sonra tabloyu tamamlayın ve belgeyi belirttiğiniz yola kaydedin.

```csharp
// Belgeyi kaydedin.
doc.Save(dataDir + "WorkingWithTables.PreferredWidthSettings.docx");
```

Bu adım tabloyu sonlandırır ve belgeyi "WorkingWithTables.PreferredWidthSettings.docx" dosya adıyla belirlediğiniz dizine kaydeder.

## Çözüm

.NET için Aspose.Words'de tercih edilen genişlik ayarlarıyla tablolar oluşturmak, mevcut farklı boyutlandırma seçeneklerini anladığınızda basittir. Sabit, göreli veya otomatik hücre genişliklerine ihtiyacınız olsun, Aspose.Words çeşitli tablo düzeni senaryolarını verimli bir şekilde ele alma esnekliği sağlar. Bu kılavuzda özetlenen adımları izleyerek, tablolarınızın Word belgelerinizde iyi yapılandırılmış ve görsel olarak çekici olmasını sağlayabilirsiniz.

## SSS

### Mutlak ve bağıl hücre genişlikleri arasındaki fark nedir?
Mutlak hücre genişlikleri sabittir ve değişmez, bağıl genişlikler ise tablonun toplam genişliğine bağlı olarak ayarlanır.

### Göreceli genişlikler için negatif yüzdeler kullanabilir miyim?
Hayır, negatif yüzdeler hücre genişlikleri için geçerli değildir. Sadece pozitif yüzdelere izin verilir.

### Otomatik boyutlandırma özelliği nasıl çalışır?
Otomatik boyutlandırma, diğer hücreler boyutlandırıldıktan sonra tabloda kalan boşluğu dolduracak şekilde hücrenin genişliğini ayarlar.

### Farklı genişlik ayarlarına sahip hücrelere farklı stiller uygulayabilir miyim?
Evet, hücrelere genişlik ayarlarından bağımsız olarak çeşitli stiller ve biçimlendirmeler uygulayabilirsiniz.

### Tablonun toplam genişliği tüm hücre genişliklerinin toplamından küçük olursa ne olur?
Tablo, hücrelerin genişliğini mevcut alana sığacak şekilde otomatik olarak ayarlayacaktır; bu da bazı hücrelerin küçülmesine neden olabilir.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
