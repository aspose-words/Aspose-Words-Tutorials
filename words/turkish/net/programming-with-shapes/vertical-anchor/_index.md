---
"description": "Aspose.Words for .NET kullanarak Word belgelerindeki metin kutuları için dikey bağlantı konumlarının nasıl ayarlanacağını öğrenin. Kolay adım adım kılavuz dahildir."
"linktitle": "Dikey Çapa"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Dikey Çapa"
"url": "/tr/net/programming-with-shapes/vertical-anchor/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Dikey Çapa

## giriiş

Hiç kendinizi bir Word belgesinde bir metin kutusunun içinde metnin tam olarak nerede görüneceğini kontrol etme ihtiyacı içinde buldunuz mu? Belki metninizin metin kutusunun üstüne, ortasına veya altına sabitlenmesini istiyorsunuz? Öyleyse, doğru yerdesiniz! Bu eğitimde, Word belgelerinde metin kutularının dikey sabitleyicisini ayarlamak için Aspose.Words for .NET'i nasıl kullanacağınızı keşfedeceğiz. Dikey sabitlemeyi, metninizi tam olarak istediğiniz kabın içinde konumlandıran sihirli değnek olarak düşünün. Başlamaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Dikey ankrajın temellerine dalmadan önce, birkaç şeyin yerinde olması gerekir:

1. Aspose.Words for .NET: Aspose.Words for .NET kütüphanesinin yüklü olduğundan emin olun. Henüz yüklü değilse, [buradan indirin](https://releases.aspose.com/words/net/).
2. Visual Studio: Bu eğitimde kodlama için Visual Studio veya başka bir .NET IDE kullandığınızı varsayıyoruz.
3. Temel C# Bilgisi: C# ve .NET'e aşinalık, konuyu sorunsuz bir şekilde takip etmenize yardımcı olacaktır.

## Ad Alanlarını İçe Aktar

Başlamak için, gerekli ad alanlarını C# kodunuza aktarmanız gerekir. Burada uygulamanıza kullanacağınız sınıfları ve yöntemleri nerede bulacağını söylersiniz. İşte nasıl yapacağınız:

```csharp
using Aspose.Words;
using Aspose.Words.Drawing;
```

Bu ad alanları, belgeler ve şekillerle çalışmak için ihtiyaç duyacağınız sınıfları sağlar.

## Adım 1: Belgeyi Başlatın

İlk önce, yeni bir Word belgesi oluşturmanız gerekir. Bunu, boyamaya başlamadan önce tuvalinizi ayarlamak olarak düşünün.

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";

Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Burada, `Document` boş tuvalinizdir ve `DocumentBuilder` şekil ve metin eklemenize olanak sağlayan boya fırçanızdır.

## Adım 2: Bir TextBox Şekli Ekle

Şimdi, belgemize bir metin kutusu ekleyelim. Metninizin yaşayacağı yer burasıdır. 

```csharp
Shape textBox = builder.InsertShape(ShapeType.TextBox, 200, 200);
```

Bu örnekte, `ShapeType.TextBox` istediğiniz şekli belirtir ve `200, 200` metin kutusunun genişliği ve yüksekliği noktalardır.

## Adım 3: Dikey Bağlantıyı Ayarlayın

İşte sihir burada gerçekleşiyor! Metin kutusu içindeki metnin dikey hizalamasını ayarlayabilirsiniz. Bu, metnin metin kutusunun üstüne, ortasına veya altına sabitlenip sabitlenmeyeceğini belirler.

```csharp
textBox.TextBox.VerticalAnchor = TextBoxAnchor.Bottom;
```

Bu durumda, `TextBoxAnchor.Bottom` metnin metin kutusunun altına sabitlenmesini sağlar. Ortalanmasını veya üste hizalanmasını istiyorsanız, şunu kullanırsınız `TextBoxAnchveya.Center` or `TextBoxAnchor.Top`Sırasıyla.

## Adım 4: TextBox'a Metin Ekleyin

Şimdi metin kutunuza biraz içerik ekleme zamanı. Bunu tuvalinizi son rötuşlarla doldurmak olarak düşünün.

```csharp
builder.MoveTo(textBox.FirstParagraph);
builder.Write("Textbox contents");
```

Burada, `MoveTo` metnin metin kutusuna eklenmesini sağlar ve `Write` gerçek metni ekler.

## Adım 5: Belgeyi Kaydedin

Son adım belgenizi kaydetmektir. Bu, bitmiş resminizi bir çerçeveye koymak gibidir.

```csharp
doc.Save(dataDir + "WorkingWithShapes.VerticalAnchor.docx");
```

## Çözüm

İşte bu kadar! Aspose.Words for .NET kullanarak bir Word belgesindeki metin kutusundaki metnin dikey hizalamasını nasıl kontrol edeceğinizi öğrendiniz. Metni üste, ortaya veya alta sabitleyin, bu özellik belgenizin düzeni üzerinde hassas bir kontrol sağlar. Böylece bir dahaki sefere belgenizin metin yerleşimini ayarlamanız gerektiğinde ne yapmanız gerektiğini bileceksiniz!

## SSS

### Word belgesinde dikey sabitleme nedir?
Dikey sabitleme, metnin bir metin kutusu içinde nereye yerleştirileceğini (örneğin üst, orta veya alt hizalama) kontrol eder.

### Metin kutularının dışında başka şekiller kullanabilir miyim?
Evet, dikey sabitlemeyi diğer şekillerde de kullanabilirsiniz, ancak en yaygın kullanım şekli metin kutularıdır.

### Metin kutusunu oluşturduktan sonra bağlantı noktasını nasıl değiştirebilirim?
Bağlantı noktasını, `VerticalAnchor` metin kutusu şekil nesnesindeki özellik.

### Metni metin kutusunun ortasına sabitlemek mümkün müdür?
Kesinlikle! Sadece kullan `TextBoxAnchor.Center` metni metin kutusu içinde dikey olarak ortalamak için.

### Aspose.Words for .NET hakkında daha fazla bilgiyi nerede bulabilirim?
Şuna bir göz atın: [Aspose.Words Belgeleri](https://reference.aspose.com/words/net/) Daha detaylı bilgi ve rehberler için.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}