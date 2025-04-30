---
"description": "Aspose.Words for .NET kullanarak Word belgelerindeki başlıkları ve altbilgileri nasıl ayıracağınızı öğrenin. Belge düzenlemede ustalaşmak için ayrıntılı, adım adım kılavuzumuzu izleyin."
"linktitle": "Başlıklar Altbilgilerin Bağlantısını Kaldır"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Başlıklar Altbilgilerin Bağlantısını Kaldır"
"url": "/tr/net/join-and-append-documents/unlink-headers-footers/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Başlıklar Altbilgilerin Bağlantısını Kaldır

## giriiş

Belge işleme dünyasında, başlıkları ve alt bilgileri tutarlı tutmak bazen zor olabilir. İster belgeleri birleştirin, ister farklı bölümler için farklı başlıklar ve alt bilgiler elde etmek isteyin, bunların bağlantısını nasıl kaldıracağınızı bilmek önemlidir. Bugün, bunu .NET için Aspose.Words kullanarak nasıl başarabileceğinizi inceleyeceğiz. Kolayca takip edebilmeniz için bunu adım adım açıklayacağız. Belge düzenlemede ustalaşmaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Ayrıntılara dalmadan önce ihtiyacınız olacak birkaç şey var:

- Aspose.Words for .NET Kütüphanesi: Bunu şu adresten indirebilirsiniz: [Aspose sürüm sayfası](https://releases.aspose.com/words/net/).
- .NET Framework: Uyumlu bir .NET Framework'ün yüklü olduğundan emin olun.
- IDE: Visual Studio veya herhangi bir .NET uyumlu Entegre Geliştirme Ortamı.
- C# Temel Anlayışı: C# programlama dili hakkında temel bir anlayışa ihtiyacınız olacak.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarını içe aktardığınızdan emin olun. Bu, Aspose.Words kütüphanesine ve özelliklerine erişmenizi sağlayacaktır.

```csharp
using Aspose.Words;
```

Word belgelerinizdeki üstbilgi ve altbilgilerin bağlantısını kaldırmanıza yardımcı olmak için süreci yönetilebilir adımlara bölelim.

## Adım 1: Projenizi Kurun

Öncelikle proje ortamınızı ayarlamanız gerekir. IDE'nizi açın ve yeni bir .NET projesi oluşturun. Daha önce indirdiğiniz Aspose.Words kütüphanesine bir referans ekleyin.

```csharp
// Belge dizininize giden yol 
string dataDir = "YOUR DOCUMENT DIRECTORY";
```

## Adım 2: Kaynak Belgeyi Yükle

Sonra, değiştirmek istediğiniz kaynak belgeyi yüklemeniz gerekir. Bu belgenin başlıkları ve altbilgileri bağlantısız olacaktır.

```csharp
Document srcDoc = new Document(dataDir + "Document source.docx");
```

## Adım 3: Hedef Belgeyi Yükle

Şimdi, başlık ve altbilgilerini ayırdıktan sonra kaynak belgeyi ekleyeceğiniz hedef belgeyi yükleyin.

```csharp
Document dstDoc = new Document(dataDir + "Northwind traders.docx");
```

## Adım 4: Üstbilgiler ve Altbilgilerin Bağlantısını Kaldırın

Bu adım çok önemlidir. Kaynak belgenin başlıklarını ve altbilgilerini hedef belgenin başlıklarından ve altbilgilerinden ayırmak için şunu kullanacaksınız: `LinkToPrevious` yöntem. Bu yöntem, üstbilgi ve altbilgilerin eklenen belgeye taşınmamasını sağlar.

```csharp
// Bunu durdurmak için kaynak belgedeki üstbilgi ve altbilgilerin bağlantısını kaldırın
// hedef belgenin üstbilgi ve altbilgilerinin devam ettirilmesinden.
srcDoc.FirstSection.HeadersFooters.LinkToPrevious(false);
```

## Adım 5: Kaynak Belgeyi Ekleyin

Başlıklar ve altbilgilerin bağlantısını kaldırdıktan sonra, kaynak belgeyi hedef belgeye ekleyebilirsiniz. `AppendDocument` yöntemi ve içe aktarma biçimi modunu ayarlayın `KeepSourceFormatting` kaynak belgenin orijinal biçimlendirmesini korumak için.

```csharp
dstDoc.AppendDocument(srcDoc, ImportFormatMode.KeepSourceFormatting);
```

## Adım 6: Son Belgeyi Kaydedin

Son olarak, yeni oluşturulan belgeyi kaydedin. Bu belgenin kaynak belgenin içeriği hedef belgeye eklenecek ve başlıklar ve altbilgiler bağlantısız olacaktır.

```csharp
dstDoc.Save(dataDir + "JoinAndAppendDocuments.UnlinkHeadersFooters.docx");
```

## Çözüm

İşte oldu! Bu adımları izleyerek, kaynak belgenizdeki başlıkları ve altbilgileri başarıyla ayırdınız ve Aspose.Words for .NET kullanarak hedef belgenize eklediniz. Bu teknik, farklı bölümler için farklı başlıklar ve altbilgiler gerektiren karmaşık belgelerle çalışırken özellikle yararlı olabilir. İyi kodlamalar!

## SSS

### Aspose.Words for .NET nedir?  
Aspose.Words for .NET, .NET uygulamalarında Word belgeleriyle çalışmak için güçlü bir kütüphanedir. Geliştiricilerin belgeleri programatik olarak oluşturmasına, değiştirmesine, dönüştürmesine ve yazdırmasına olanak tanır.

### Sadece belirli bölümler için üstbilgi ve altbilgilerin bağlantısını kaldırabilir miyim?  
Evet, belirli bölümler için üstbilgi ve altbilgilerin bağlantısını kaldırmak için şuraya erişebilirsiniz: `HeadersFooters` İstenilen bölümün özelliğini kullanarak `LinkToPrevious` yöntem.

### Kaynak belgenin orijinal formatını korumak mümkün müdür?  
Evet, kaynak belgeyi eklerken şunu kullanın: `ImportFormatMode.KeepSourceFormatting` orijinal biçimlendirmeyi koruma seçeneği.

### Aspose.Words for .NET'i C# dışındaki diğer .NET dilleriyle birlikte kullanabilir miyim?  
Kesinlikle! Aspose.Words for .NET, VB.NET ve F# dahil olmak üzere herhangi bir .NET diliyle kullanılabilir.

### Aspose.Words for .NET için daha fazla doküman ve desteği nerede bulabilirim?  
Kapsamlı belgeleri şurada bulabilirsiniz: [Aspose.Words for .NET dokümantasyon sayfası](https://reference.aspose.com/words/net/)ve destek şu adreste mevcuttur: [Aspose forumu](https://forum.aspose.com/c/words/8).



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}