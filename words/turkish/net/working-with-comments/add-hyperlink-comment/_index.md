---
title: Aspose.Words for .NET kullanarak Hyperlink Comment ekleyin ve PDF Annotation olarak dışa aktarın
weight: 110
limit:
description: Aspose.Words for .NET ile bir Word file içinde hyperlink comment eklemeyi ve bunu PDF annotation olarak dışa aktarmayı öğrenin.
keywords: [Aspose.Words for .NET, add hyperlink comment, PDF annotation, export Word to PDF, comment with hyperlink, verify PDF output]
url: /net/working-with-comments/add-hyperlink-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET ile bir Word file içinde hyperlink comment eklemeyi
    ve bunu PDF annotation olarak dışa aktarmayı öğrenin.
  headline: Aspose.Words for .NET kullanarak Hyperlink Comment ekleyin ve PDF Annotation
    olarak dışa aktarın
  type: TechArticle
- description: Aspose.Words for .NET ile bir Word file içinde hyperlink comment eklemeyi
    ve bunu PDF annotation olarak dışa aktarmayı öğrenin.
  name: Aspose.Words for .NET kullanarak Hyperlink Comment ekleyin ve PDF Annotation
    olarak dışa aktarın
  steps:
  - name: Yeni boş bir Document nesnesi ve onunla çalışmak için bir DocumentBuilder
      oluşturun.
    text: Yeni boş bir Document nesnesi ve onunla çalışmak için bir DocumentBuilder
      oluşturun.
  - name: Gelecek yorumu barındıracak görünür bir metin satırı yazın.
    text: Gelecek yorumu barındıracak görünür bir metin satırı yazın.
  - name: Jane Doe tarafından oluşturulan bir Comment oluşturun ve document'in ilk
      paragrafına ekleyin.
    text: Jane Doe tarafından oluşturulan bir Comment oluşturun ve document'in ilk
      paragrafına ekleyin.
  - name: Yorumun içinde bir paragraf ekleyin ve Aspose.Words Library web sitesine
      mavi, altı çizili bir hyperlink ekleyin.
    text: Yorumun içinde bir paragraf ekleyin ve Aspose.Words Library web sitesine
      mavi, altı çizili bir hyperlink ekleyin.
  - name: Belgeyi yorumları PDF annotation olarak render edecek şekilde yapılandırın
      ve yerleşimi yenileyin.
    text: Belgeyi yorumları PDF annotation olarak render edecek şekilde yapılandırın
      ve yerleşimi yenileyin.
  - name: Oluşturulan PDF'yi depolamak için geçerli dizinde bir "Output" klasörü oluşturun.
    text: Oluşturulan PDF'yi depolamak için geçerli dizinde bir "Output" klasörü oluşturun.
  - name: Hazırlanan belgeyi PdfSaveOptions kullanarak PDF dosyası olarak kaydedin.
    text: Hazırlanan belgeyi PdfSaveOptions kullanarak PDF dosyası olarak kaydedin.
  - name: PDF dosyasının mevcut olduğunu ve veri içerdiğini kontrol edin, ardından
      sonucu konsola yazdırın.
    text: PDF dosyasının mevcut olduğunu ve veri içerdiğini kontrol edin, ardından
      sonucu konsola yazdırın.
  type: HowTo
- questions:
  - answer: '`InsertHyperlink`''in üçüncü parametresi, linkin bir alan (field) olarak
      ele alınıp alınmayacağını belirler; `false` olarak ayarlandığında, alan koduna
      ihtiyaç duymadan PDF annotation içinde çalışan düz bir hyperlink eklenir.'
    question: '`InsertHyperlink` içindeki üçüncü argüman (`false`) neyi kontrol eder?'
  - answer: '`Save` metodunu çağırmadan önce `myDocument.LayoutOptions.CommentDisplayMode`
      değerini `CommentDisplayMode.ShowInBalloons` olarak ayarlayın; PDF böylece yorumu
      bir açıklama yerine normal bir Word yorumu olarak içerecektir.'
    question: Yorumu PDF annotation yerine Word belgesinde balon olarak nasıl gösterebilirim?
  - answer: Evet—bir paragrafın sonuna eklediğiniz her `Comment` kendi `InsertHyperlink`
      çağrısını içerebilir ve belge kaydedildiğinde tüm hyperlink'ler ayrı PDF annotation'ları
      olarak korunur.
    question: Birden fazla yorum eklersem, her hyperlink dışa aktarılan PDF'de çalışır
      mı?
  - answer: Oluşturulan PDF'yi açın, yorum annotation'ını (genellikle bir not simgesi
      olarak gösterilir) bulun, yorum metnini göstermek için üzerine tıklayın ve ardından
      mavi altı çizili linke tıklayın; hedef URL bir web tarayıcısında açılmalıdır.
    question: PDF oluşturulduktan sonra yorum içindeki hyperlink'in gerçekten çalıştığını
      nasıl doğrularım?
  type: FAQPage
images:
- /net/working-with-comments/add-hyperlink-comment/og-image.png
og_title: Hyperlink Comment ekle ve PDF'ye dışa aktar
og_description: Word comment'ına tıklanabilir bir link yerleştirmeyi ve bunu PDF annotation'a dönüştürmeyi öğrenin.
og_image_alt: Aspose.Words for .NET kullanarak bir Word document'e tıklanabilir hyperlink içeren bir yorum eklemeyi ve bunu PDF annotation olarak dışa aktarmayı gösteren rehber.
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Hyperlink Comment ekleyin ve PDF Annotation olarak dışa aktarın
Bu öğreticide, bir Word document oluşturmayı, harici bir web sitesine tıklanabilir bir hyperlink içeren bir yorum eklemeyi, bu yorumun PDF annotation olarak görünmesini yapılandırmayı, document'i PDF olarak dışa aktarmayı ve ortaya çıkan PDF dosyasını doğrulamayı göreceksiniz. Adım adım kod, zengin, link‑etkin yorumlar eklemenizi ve bunları PDF'ye dönüştürürken korumanızı sağlar; böylece okuyucularla etkileşimli notları paylaşmak kolaylaşır.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-hyperlink-comment" >}}


{{< /blocks/products/pf/tutorial-page-section >}}

{{< blocks/products/pf/tutorial-page-section >}}
## Installation Instructions
1. Download Aspose.Words for .NET:
   Get the latest version from the [Aspose Downloads page](https://releases.aspose.com/words/net/).

2. Install via NuGet:
   - Open your Visual Studio project.
   - Navigate to the NuGet Package Manager (Tools > NuGet Package Manager > Manage NuGet Packages for Solution).
   - Search for "Aspose.Words" and click Install.

3. Add Namespace References:
   Add the following namespace at the top of your code file:
   ```csharp
   using Aspose.Words;
   using Aspose.Words.Saving;
   using Aspose.Words.Drawing;
   using Aspose.Words.Fields;
   using System.Drawing;
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: `InsertHyperlink` içindeki üçüncü argüman (`false`) neyi kontrol eder?**  
A: `InsertHyperlink`'in üçüncü parametresi, linkin bir alan (field) olarak ele alınıp alınmayacağını belirler; `false` olarak ayarlandığında, alan koduna ihtiyaç duymadan PDF annotation içinde çalışan düz bir hyperlink eklenir.

**Q: Yorumu PDF annotation yerine Word belgesinde balon olarak nasıl gösterebilirim?**  
A: `Save` metodunu çağırmadan önce `myDocument.LayoutOptions.CommentDisplayMode` değerini `CommentDisplayMode.ShowInBalloons` olarak ayarlayın; PDF böylece yorumu bir açıklama yerine normal bir Word yorumu olarak içerecektir.

**Q: Birden fazla yorum eklersem, her hyperlink dışa aktarılan PDF'de çalışır mı?**  
A: Evet—bir paragrafın sonuna eklediğiniz her `Comment` kendi `InsertHyperlink` çağrısını içerebilir ve belge kaydedildiğinde tüm hyperlink'ler ayrı PDF annotation'ları olarak korunur.

**Q: PDF oluşturulduktan sonra yorum içindeki hyperlink'in gerçekten çalıştığını nasıl doğrularım?**  
A: Oluşturulan PDF'yi açın, yorum annotation'ını (genellikle bir not simgesi olarak gösterilir) bulun, yorum metnini göstermek için üzerine tıklayın ve ardından mavi altı çizili linke tıklayın; hedef URL bir web tarayıcısında açılmalıdır.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}