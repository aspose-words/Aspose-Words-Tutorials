---
"description": "Bu adım adım kılavuzla .NET için Aspose.Words'ü kullanarak tabloların sayfalar arasında dağılmasını nasıl önleyeceğinizi öğrenin. Düzgün, profesyonel görünümlü Word belgeleri sağlayın"
"linktitle": "Masayı Bir Arada Tutun"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Masayı Bir Arada Tutun"
"url": "/tr/net/join-and-append-documents/keep-source-together/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Masayı Bir Arada Tutun

## giriiş

Tablolar birçok Word belgesinin önemli bir parçasıdır, ancak bazen tablonuzun iki sayfaya bölündüğü bir durumla karşılaşabilirsiniz. Bu, belgenizin akışını bozabilir ve okunabilirliğini etkileyebilir. Tüm tabloyu tek bir sayfada tutmanın bir yolu olsa harika olmaz mıydı? Aspose.Words for .NET ile bu soruna kolay bir çözüm var! Bu eğitimde, tabloların sayfalar arasında bölünmesini nasıl önleyeceğinizi ve belgenizin düzgün ve profesyonel görünmesini nasıl sağlayacağınızı ele alacağız.

## Ön koşullar

Eğitime başlamadan önce, süreci sorunsuz bir şekilde takip edebilmeniz için ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım.

### Aspose.Words for .NET Kütüphanesi

Öncelikle, .NET için Aspose.Words'ün yüklü olması gerekir. Bu, Word belgeleriyle programlı olarak çalışmanıza olanak tanıyan güçlü bir kütüphanedir.

- [.NET için Aspose.Words'ü indirin](https://releases.aspose.com/words/net/)

### Geliştirme Ortamı

C# kodunu çalıştırmak için aşağıdaki gibi bir geliştirme ortamı kurmuş olmalısınız:

- Visual Studio (herhangi bir yeni sürüm)
- .NET Framework 2.0 veya üzeri

### Tablolu Bir Word Belgesi

Bir tablo içeren bir Word belgesine ihtiyacınız olacak. Bu eğitimde, adlı bir örnek belgeyle çalışacağız. `"Table spanning two pages.docx"`Bu dosya şu anda iki sayfaya yayılan bir tablo içeriyor.

### Geçici Lisans (Opsiyonel)

Aspose.Words ücretsiz deneme sürümüyle birlikte gelirken, bir [geçici lisans](https://purchase.aspose.com/temporary-license/) Kütüphanenin tüm potansiyelini ortaya çıkarmak.

## Paketleri İçe Aktar

Herhangi bir kod yazmadan önce, Aspose.Words for .NET ile çalışmak için gerekli ad alanlarını içe aktarmamız gerekir. Kod dosyanızın en üstüne aşağıdaki içe aktarmaları ekleyin:

```csharp
using Aspose.Words;
using Aspose.Words.Tables;
```

Bu ad alanları size şu tür sınıflara erişim sağlar: `Document`, `Table`, `Cell`ve bu eğitimde kullanacağımız diğerleri.

## Adım 1: Belgeyi Yükleyin

Yapmamız gereken ilk şey tabloyu içeren Word belgesini yüklemektir. Bunun için şunu kullanacağız: `Document` Aspose.Words sınıfından. Bu sınıf Word dosyalarını programlı olarak açmanıza ve düzenlemenize olanak tanır.

```csharp
// Belgeler dizinine giden yol.
string dataDir = "YOUR DOCUMENTS DIRECTORY";

Document doc = new Document(dataDir + "Table spanning two pages.docx");
```

Bu kod parçacığında, belgemizin konumunu belirtiyoruz. Değiştir `"YOUR DOCUMENTS DIRECTORY"` Belgenizin saklandığı gerçek dizinle.

## Adım 2: Tabloya Erişim

Belge yüklendikten sonraki adım, bir arada tutmak istediğimiz tabloya erişmektir. Bu örnekte, tablonun belgedeki ilk tablo olduğunu varsayıyoruz.

```csharp
Table table = (Table) doc.GetChild(NodeType.Table, 0, true);
```

Bu kod satırı belgedeki ilk tabloyu bulur. `GetChild` yöntem, bu durumda belirli bir düğüm türünü alır `NodeType.Table`. `0` ilk tabloyu istediğimizi gösterir ve `true` bayrak, tüm alt düğümlerde yinelemeli arama yapmamızı sağlar.

## Adım 3: Tablo Hücreleri Arasında Döngü

Şimdi, tablodaki her hücrede döngü yapmamız gerekiyor. Bir tablo birden fazla satır ve her satır birden fazla hücre içerdiğinden, her hücrede yineleme yapacağız ve sayfalar arasında bölünmediğinden emin olacağız.

```csharp
foreach (Cell cell in table.GetChildNodes(NodeType.Cell, true))
{
    cell.EnsureMinimum();
```

Burada, `GetChildNodes` tablodaki tüm hücreleri alır ve her birinde döngü oluştururuz. `EnsureMinimum()` Bu yöntem, her hücrenin en az bir paragraf içermesini sağlar; çünkü boş bir hücre daha sonra sorunlara yol açabilir.

## Adım 4: KeepWithNext Özelliğini Ayarlayın

Tablonun sayfalar arasında dağılmasını önlemek için, `KeepWithNext` Tablo içindeki her paragraf için özellik. Bu özellik, paragrafın bir sonraki paragrafla birlikte kalmasını sağlayarak aralarında sayfa sonlarının oluşmasını etkili bir şekilde önler.

```csharp
    foreach (Paragraph para in cell.Paragraphs)
        if (!(cell.ParentRow.IsLastRow && para.IsEndOfCell))
            para.ParagraphFormat.KeepWithNext = true;
```

Bu döngü her hücrenin içindeki her paragrafı kontrol eder. Koşul, şunu uygulamadığımızdan emin olur: `KeepWithNext` son satırdaki son paragrafa özellik. Aksi takdirde, bir sonraki paragraf olmadığı için özelliğin hiçbir etkisi olmazdı.

## Adım 5: Belgeyi Kaydedin

Son olarak, uygulandıktan sonra `KeepWithNext` özelliği, değiştirilen belgeyi kaydetmemiz gerekiyor.

```csharp
doc.Save(dataDir + "WorkingWithTables.KeepTableTogether.docx");
```

Bu satır güncellenen belgeyi yeni bir adla kaydeder ve orijinal dosyayı korur. Artık ortaya çıkan dosyayı açabilir ve tablonun artık iki sayfaya bölünmediğini görebilirsiniz!

## Çözüm

İşte bu kadar! Bu basit adımları izleyerek, .NET için Aspose.Words kullanarak Word belgelerinde tabloların sayfalar arasında dağılmasını kolayca önleyebilirsiniz. İster raporlar, ister sözleşmeler veya diğer belgeler üzerinde çalışın, tabloları olduğu gibi tutmak daha cilalı, profesyonel bir görünüm sağlar.

Aspose.Words'ün güzelliği, esnekliği ve kullanım kolaylığıdır; makinenizde Microsoft Word'ün yüklü olmasına gerek kalmadan Word belgelerini programatik olarak düzenlemenize olanak tanır. Artık tabloları bir arada tutmayı öğrendiğinize göre, belge işleme becerilerinizi bir üst seviyeye taşımak için kütüphanenin diğer özelliklerini keşfedin!

## SSS

### Bu kodu kullandıktan sonra tablom neden hala sayfalar arasında bozuluyor?

Masanız hala kırılıyorsa, şu adımları uyguladığınızdan emin olun: `KeepWithNext` Özelliği doğru bir şekilde ayarlayın. Her hücredeki sonuncusu hariç tüm paragrafların bu özelliğe sahip olduğunu iki kez kontrol edin.

### Sadece belirli satırları bir arada tutabilir miyim?

Evet, seçici olarak uygulayabilirsiniz `KeepWithNext` Tablo içindeki belirli satırlara veya paragraflara, hangi parçaların bir arada kalacağını kontrol etmek için özellik.

### Bu yöntem büyük tablolarda işe yarar mı?

Çok büyük tablolar için, tüm tabloyu bir sayfaya sığdırmak için yeterli alan yoksa Word bunları yine de sayfalara bölebilir. Daha büyük tablolara uyum sağlamak için tablonuzun biçimlendirmesini veya kenar boşluklarını ayarlamayı düşünün.

### Bu yöntemi diğer belge formatlarıyla da kullanabilir miyim?

Evet! Aspose.Words for .NET, DOC, DOCX, PDF ve diğerleri gibi birçok formatı destekler. Aynı yöntem tabloları destekleyen tüm formatlarda çalışır.

### Aspose.Words for .NET ücretsiz bir kütüphane midir?

Aspose.Words for .NET ücretsiz deneme sunuyor, ancak tüm özelliklere tam erişim için bir lisans satın almanız gerekiyor. Lisanslama seçeneklerini şu adreste inceleyebilirsiniz: [Aspose satın alma sayfası](https://purchase.aspose.com/buy).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}