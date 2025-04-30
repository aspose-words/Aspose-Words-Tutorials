---
"description": "Aspose.Words for .NET kullanarak Word belgelerine OLE nesnelerinin nasıl ekleneceğini öğrenin. Dosyaları sorunsuz bir şekilde yerleştirmek için ayrıntılı adım adım kılavuzumuzu izleyin."
"linktitle": "Ole Paketi ile Word'e Ole Nesnesi Ekleme"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Ole Paketi ile Word'e Ole Nesnesi Ekleme"
"url": "/tr/net/working-with-oleobjects-and-activex/insert-ole-object-with-ole-package/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Ole Paketi ile Word'e Ole Nesnesi Ekleme

## giriiş

Bir dosyayı Word belgesine gömmek istediyseniz, doğru yerdesiniz. İster bir ZIP dosyası, ister bir Excel sayfası veya başka bir dosya türü olsun, dosyayı doğrudan Word belgenize gömmek inanılmaz derecede faydalı olabilir. Bunu, belgenizde her türlü hazineyi saklayabileceğiniz gizli bir bölme gibi düşünün. Ve bugün, bunu .NET için Aspose.Words kullanarak nasıl yapacağınızı anlatacağız. Word sihirbazı olmaya hazır mısınız? Hadi başlayalım!

## Ön koşullar

Başlamadan önce aşağıdakilere sahip olduğunuzdan emin olun:

1. .NET için Aspose.Words: Henüz yapmadıysanız, şu adresten indirin: [Burada](https://releases.aspose.com/words/net/).
2. Geliştirme Ortamı: Visual Studio veya herhangi bir .NET geliştirme ortamı.
3. C# Hakkında Temel Bilgi: Uzman olmanıza gerek yok, ancak C# konusunda bilgi sahibi olmak faydalı olacaktır.
4. Belge Dizini: Belgeleri saklayabileceğiniz ve geri alabileceğiniz klasör.

## Ad Alanlarını İçe Aktar

İlk önce ilk şeyler, ad alanlarımızı sıralayalım. Projenize aşağıdaki ad alanlarını eklemeniz gerekir:

```csharp
using System;
using System.IO;
using Aspose.Words;
using Aspose.Words.Drawing;
```

Bunu takip etmesi kolay olacak şekilde küçük adımlara bölelim.

## Adım 1: Belgenizi Ayarlayın

Boş bir tuvale sahip bir sanatçı olduğunuzu düşünün. Öncelikle, Word belgemiz olan boş tuvalimize ihtiyacımız var. İşte nasıl kuracağınız:

```csharp
// Belge dizininize giden yol
string dataDir = "YOUR DOCUMENT DIRECTORY";
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
```

Bu kod yeni bir Word belgesi başlatır ve belgeye içerik eklemek için kullanacağımız DocumentBuilder'ı kurar.

## Adım 2: Ole Nesnenizi Okuyun

Sonra, gömmek istediğiniz dosyayı okuyalım. Bunu, gizli bölmenizde saklamak istediğiniz hazineyi almak olarak düşünün:

```csharp
byte[] bs = File.ReadAllBytes(dataDir + "Zip file.zip");
```

Bu satır ZIP dosyanızdaki tüm baytları okur ve bunları bir bayt dizisine depolar.

## Adım 3: Ole Nesnesini Ekle

Şimdi sihirli kısım geliyor. Dosyayı Word belgemize gömeceğiz:

```csharp
using (Stream stream = new MemoryStream(bs))
{
    Shape shape = builder.InsertOleObject(stream, "Package", true, null);
    OlePackage olePackage = shape.OleFormat.OlePackage;
    olePackage.FileName = "filename.zip";
    olePackage.DisplayName = "displayname.zip";
}
```

Burada, bayt dizisinden bir bellek akışı oluşturuyoruz ve şunu kullanıyoruz: `InsertOleObject` belgeye yerleştirme yöntemi. Ayrıca gömülü nesne için dosya adını ve görüntüleme adını da ayarladık.

## Adım 4: Belgenizi Kaydedin

Son olarak şaheserimizi kurtaralım:

```csharp
doc.Save(dataDir + "WorkingWithOleObjectsAndActiveX.InsertOleObjectWithOlePackage.docx");
```

Bu, belgenizi gömülü dosyanızla birlikte belirtilen dizine kaydeder.

## Çözüm

Ve işte oldu! Aspose.Words for .NET kullanarak bir OLE nesnesini bir Word belgesine başarıyla yerleştirdiniz. Bu, belgenizin içine istediğiniz zaman ortaya çıkarılabilecek gizli bir mücevher eklemek gibidir. Bu teknik, teknik dokümantasyondan dinamik raporlara kadar çeşitli uygulamalar için inanılmaz derecede faydalı olabilir. 

## SSS

### Bu yöntemi kullanarak başka dosya türlerini de gömebilir miyim?
Evet, Excel dosyaları, PDF'ler ve resimler gibi çeşitli dosya türlerini gömebilirsiniz.

### Aspose.Words için lisansa ihtiyacım var mı?
Evet, geçerli bir lisansa ihtiyacınız var. Bir tane alabilirsiniz [geçici lisans](https://purchase.aspose.com/temporary-license/) Değerlendirme için.

### OLE nesnesinin görüntü adını nasıl özelleştirebilirim?
Ayarlayabilirsiniz `DisplayName` mülkiyeti `OlePackage` özelleştirmek için.

### Aspose.Words .NET Core ile uyumlu mu?
Evet, Aspose.Words hem .NET Framework'ü hem de .NET Core'u destekler.

### Word belgesindeki gömülü OLE nesnesini düzenleyebilir miyim?
Hayır, OLE nesnesini doğrudan Word içinde düzenleyemezsiniz. Bunu kendi yerel uygulamasında açmanız gerekir.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}