---
"description": "Bu ayrıntılı, adım adım eğitimde Aspose.Words for .NET ile bir akış kullanarak bir OLE nesnesinin simge olarak nasıl ekleneceğini öğrenin."
"linktitle": "Stream Kullanarak Ole Nesnesini Simge Olarak Ekle"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Stream Kullanarak Ole Nesnesini Simge Olarak Ekle"
"url": "/tr/net/working-with-oleobjects-and-activex/insert-ole-object-as-icon-using-stream/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Stream Kullanarak Ole Nesnesini Simge Olarak Ekle

## giriiş

Bu eğitimde, .NET için Aspose.Words'ün süper havalı bir özelliğini ele alacağız: Bir akış kullanarak bir OLE (Nesne Bağlama ve Gömme) nesnesini simge olarak eklemek. İster bir PowerPoint sunumu, ister bir Excel elektronik tablosu veya başka bir tür dosya gömüyor olun, bu kılavuz size bunu tam olarak nasıl yapacağınızı gösterecek. Başlamaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Koda geçmeden önce ihtiyacınız olacak birkaç şey var:

- Aspose.Words for .NET: Eğer henüz yapmadıysanız, [indirmek](https://releases.aspose.com/words/net/) ve .NET için Aspose.Words'ü yükleyin.
- Geliştirme Ortamı: Visual Studio veya herhangi bir C# geliştirme ortamı.
- Giriş Dosyaları: Gömmek istediğiniz dosya (örneğin, bir PowerPoint sunumu) ve bir simge resmi.

## Ad Alanlarını İçe Aktar

Başlamak için projenize gerekli ad alanlarını içe aktardığınızdan emin olun:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Takip etmeyi kolaylaştırmak için süreci adım adım açıklayalım.

## Adım 1: Yeni Bir Belge Oluşturun

Öncelikle yeni bir belge ve bu belgeyle çalışacak bir belge oluşturucu oluşturacağız.

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Düşünün `Document` boş tuvaliniz ve `DocumentBuilder` boya fırçanız olarak. Başyapıtımızı yaratmaya başlamak için araçlarımızı ayarlıyoruz.

## Adım 2: Akışı Hazırlayın

Sonra, gömmek istediğimiz dosyayı içeren bir bellek akışı hazırlamamız gerekiyor. Bu örnekte, bir PowerPoint sunumunu gömeceğiz.

```csharp
using (MemoryStream stream = new MemoryStream(File.ReadAllBytes("Path_to_your_directory/Presentation.pptx")))
{
```

Bu adım, boyanızı fırçaya yüklemek gibidir. Dosyamızı gömülmeye hazır hale getiriyoruz.

## Adım 3: OLE Nesnesini Simge Olarak Ekle

Şimdi, OLE nesnesini belgeye eklemek için belge oluşturucuyu kullanacağız. Dosya akışını, dosya türü için ProgID'yi (bu durumda, "Paket"), simge resminin yolunu ve gömülü dosya için bir etiketi belirteceğiz.

```csharp
builder.InsertOleObjectAsIcon(stream, "Package", "Path_to_your_directory/Logo icon.ico", "My embedded file");
}
```

İşte sihir burada gerçekleşiyor! Dosyamızı gömüyor ve onu belge içinde bir simge olarak görüntülüyoruz.

## Adım 4: Belgeyi Kaydedin

Son olarak belgeyi belirtilen yola kaydediyoruz.

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectAsIconUsingStream.docx");
```

Bu adım, bitmiş resminizi bir çerçeveye koyup duvara asmak gibidir. Belgeniz artık kullanıma hazır!

## Çözüm

İşte karşınızda! Aspose.Words for .NET kullanarak bir OLE nesnesini bir Word belgesine simge olarak başarıyla yerleştirdiniz. Bu güçlü özellik, dinamik ve etkileşimli belgeleri kolaylıkla oluşturmanıza yardımcı olabilir. İster sunumlar, ister elektronik tablolar veya diğer dosyaları yerleştirin, Aspose.Words bunu kolaylaştırır. Hadi, deneyin ve belgelerinizde yaratabileceği farkı görün!

## SSS

### Bu yöntemi kullanarak farklı dosya türlerini gömebilir miyim?
Evet, Word, Excel, PowerPoint ve daha fazlası dahil olmak üzere OLE tarafından desteklenen herhangi bir dosya türünü gömebilirsiniz.

### Aspose.Words for .NET'i kullanmak için özel bir lisansa ihtiyacım var mı?
Evet, Aspose.Words for .NET bir lisans gerektirir. Bir tane alabilirsiniz [ücretsiz deneme](https://releases.aspose.com/) veya satın al [geçici lisans](https://purchase.aspose.com/temporary-license/) test için.

### OLE nesnesi için kullanılan simgeyi özelleştirebilir miyim?
Kesinlikle! İkon için herhangi bir resim dosyasını, yolunu belirterek kullanabilirsiniz. `InsertOleObjectAsIcon` yöntem.

### Dosya veya simge yolları yanlışsa ne olur?
Yöntem bir istisna fırlatacaktır. Hatalardan kaçınmak için dosyalarınıza giden yolların doğru olduğundan emin olun.

### Gömülü nesneyi gömmek yerine bağlamak mümkün müdür?
Evet, Aspose.Words, dosyanın içeriğini gömmeden dosyaya başvuran bağlantılı OLE nesneleri eklemenize olanak tanır.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}