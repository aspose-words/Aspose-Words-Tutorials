---
"description": "Aspose.Words for .NET kullanarak Word belgelerine bağlantı yorumlarının nasıl ekleneceğini öğrenin. Verimli belge işbirliği için adım adım kılavuzumuzu izleyin."
"linktitle": "Çapa Yorumu"
"second_title": "Aspose.Words Belge İşleme API'si"
"title": "Çapa Yorumu"
"url": "/tr/net/working-with-comments/anchor-comment/"
"weight": 10
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Çapa Yorumu

## giriiş

Kendinizi Word belgesinde belirli metin bölümlerine programatik olarak yorum eklemeniz gereken bir durumda buldunuz mu? Ekibinizle bir belge üzerinde iş birliği yaptığınızı ve başkalarının incelemesi için yorumlarla belirli bölümleri vurgulamanız gerektiğini düşünün. Bu eğitimde, .NET için Aspose.Words kullanarak Word belgelerine bağlantı yorumlarının nasıl ekleneceğini derinlemesine inceleyeceğiz. Süreci basit adımlara bölerek takip etmenizi ve projelerinizde uygulamanızı kolaylaştıracağız.

## Ön koşullar

Başlamadan önce ihtiyacınız olan her şeye sahip olduğunuzdan emin olalım:

- Aspose.Words for .NET: Aspose.Words kütüphanesinin yüklü olduğundan emin olun. Buradan indirebilirsiniz [Burada](https://releases.aspose.com/words/net/).
- Geliştirme Ortamı: Visual Studio gibi herhangi bir .NET geliştirme ortamı.
- C# Temel Anlayışı: C# programlamaya aşinalık, adımları kolayca takip etmenize yardımcı olacaktır.

Şimdi bu görev için içe aktarmanız gereken ad alanlarına bir göz atalım.

## Ad Alanlarını İçe Aktar

Başlamak için, projenize gerekli ad alanlarını içe aktardığınızdan emin olun. İşte gerekli ad alanları:

```csharp
using System;
using Aspose.Words;
using Aspose.Words.CommentRangeStart;
using Aspose.Words.CommentRangeEnd;
```

Önkoşulları ve ad alanlarını hallettiğimize göre, eğlenceli kısma geçelim: Süreci adım adım açıklamak.

## Adım 1: Yeni Bir Belge Oluşturun

Öncelikle yeni bir Word belgesi oluşturalım. Bu, yorumlarımız için tuval görevi görecek.

```csharp
// Belgenin kaydedileceği dizini tanımlayın
string dataDir = "YOUR DOCUMENT DIRECTORY";        

// Belge sınıfının bir örneğini oluşturun
Document doc = new Document();
```

Bu adımda yeni bir başlangıç yapıyoruz `Document` Yorumlarımızı eklemek için kullanacağımız nesne.

## Adım 2: Belgeye Metin Ekleyin

Sonra, belgeye biraz metin ekleyeceğiz. Bu metin yorumlarımızın hedefi olacak.

```csharp
// İlk paragrafı oluşturun ve çalıştırın
Paragraph para1 = new Paragraph(doc);
Run run1 = new Run(doc, "Some ");
Run run2 = new Run(doc, "text ");
para1.AppendChild(run1);
para1.AppendChild(run2);
doc.FirstSection.Body.AppendChild(para1);

// İkinci paragrafı oluşturun ve çalıştırın
Paragraph para2 = new Paragraph(doc);
Run run3 = new Run(doc, "is ");
Run run4 = new Run(doc, "added ");
para2.AppendChild(run3);
para2.AppendChild(run4);
doc.FirstSection.Body.AppendChild(para2);
```

Burada, biraz metin içeren iki paragraf oluşturuyoruz. Her metin parçası bir `Run` Daha sonra paragraflara eklenen nesne.

## Adım 3: Yorum Oluşturun

Şimdi metnimize ekleyeceğimiz yorumu oluşturalım.

```csharp
// Yeni bir Yorum Oluştur
Comment comment = new Comment(doc, "Awais Hafeez", "AH", DateTime.Today);
comment.SetText("Comment text.");
```

Bu adımda bir tane oluşturuyoruz `Comment` nesneyi ekleyin ve yorum metniyle birlikte bir paragraf ve bir koşu ekleyin.

## Adım 4: Yorum Aralığını Tanımlayın

Yorumu belirli bir metne sabitlemek için yorum aralığının başlangıcını ve sonunu tanımlamamız gerekir.

```csharp
// CommentRangeStart ve CommentRangeEnd'i tanımlayın
CommentRangeStart commentRangeStart = new CommentRangeStart(doc, comment.Id);
CommentRangeEnd commentRangeEnd = new CommentRangeEnd(doc, comment.Id);

// CommentRangeStart ve CommentRangeEnd'i belgeye ekleyin
run1.ParentNode.InsertAfter(commentRangeStart, run1);
run3.ParentNode.InsertAfter(commentRangeEnd, run3);

// Yorumu belgeye ekle
commentRangeEnd.ParentNode.InsertAfter(comment, commentRangeEnd);
```

Burada, biz yaratıyoruz `CommentRangeStart` Ve `CommentRangeEnd` nesneleri, bunları yoruma ID'siyle bağlayarak. Daha sonra bu aralıkları belgeye ekleriz, yorumumuzu belirtilen metne etkili bir şekilde sabitleriz.

## Adım 5: Belgeyi Kaydedin

Son olarak belgemizi belirtilen dizine kaydedelim.

```csharp
// Belgeyi kaydet
doc.Save(dataDir + "WorkingWithComments.AnchorComment.doc");
```

Bu adım, belgeyi, sabitlenmiş yorumla birlikte belirttiğiniz dizine kaydeder.

## Çözüm

Ve işte karşınızda! Aspose.Words for .NET kullanarak bir Word belgesindeki belirli metin bölümlerine bağlantı yorumları eklemeyi başarıyla öğrendiniz. Bu teknik, belge iş birliği için inanılmaz derecede kullanışlıdır ve metnin belirli bölümlerini kolayca vurgulamanıza ve yorumlamanıza olanak tanır. Ekibinizle bir proje üzerinde çalışıyor veya belgeleri inceliyor olun, bu yöntem üretkenliğinizi artıracak ve iş akışınızı düzene koyacaktır.

## SSS

### Word belgelerinde bağlantı yorumlarının kullanılmasının amacı nedir?
Bağlantı yorumları, metnin belirli bölümlerini vurgulamak ve bu bölümler hakkında yorum yapmak için kullanılır; böylece geri bildirim sağlamayı ve belgeler üzerinde işbirliği yapmayı kolaylaştırır.

### Aynı metin bölümüne birden fazla yorum ekleyebilir miyim?
Evet, birden fazla yorum aralığı tanımlayarak aynı metin bölümüne birden fazla yorum ekleyebilirsiniz.

### Aspose.Words for .NET'i kullanmak ücretsiz mi?
Aspose.Words for .NET, indirebileceğiniz ücretsiz bir deneme sürümü sunuyor [Burada](https://releases.aspose.com/). Tüm özellikler için bir lisans satın alabilirsiniz [Burada](https://purchase.aspose.com/buy).

### Yorumların görünümünü özelleştirebilir miyim?
Aspose.Words işlevselliğe odaklanırken, Word belgelerindeki yorumların görünümü genellikle Word tarafından kontrol edilir.

### Aspose.Words for .NET hakkında daha fazla dokümanı nerede bulabilirim?
Ayrıntılı dokümanları bulabilirsiniz [Burada](https://reference.aspose.com/words/net/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}