---
title: Aspose.Words for .NET kullanarak bir Word belgesindeki belirli bir paragraf üzerine Comment ekleyin
weight: 210
limit:
description: Aspose.Words for .NET kullanarak bir Word belgesindeki seçilen bir paragrafa yazar yorumu eklemek ve DOCX olarak kaydetmek için adım adım rehber.
keywords: [add comment Aspose.Words for .NET, insert comment Word document, comment author Aspose.Words, c# add comment to Word, save DOCX with comment]
url: /net/working-with-comments/add-comment/
date: '2026-10-13'
lastmod: '2026-10-13'
schemas:
- author: Aspose
  dateModified: '2026-10-13'
  description: Aspose.Words for .NET kullanarak bir Word belgesindeki seçilen bir
    paragrafa yazar yorumu eklemek ve DOCX olarak kaydetmek için adım adım rehber.
  headline: Aspose.Words for .NET kullanarak bir Word belgesindeki belirli bir paragraf
    üzerine Comment ekleyin
  type: TechArticle
- description: Aspose.Words for .NET kullanarak bir Word belgesindeki seçilen bir
    paragrafa yazar yorumu eklemek ve DOCX olarak kaydetmek için adım adım rehber.
  name: Aspose.Words for .NET kullanarak bir Word belgesindeki belirli bir paragraf
    üzerine Comment ekleyin
  steps:
  - name: Word dosyasını oluşturmaya başlamak için yeni bir Document ve bir DocumentBuilder
      örneği oluşturun.
    text: Word dosyasını oluşturmaya başlamak için yeni bir Document ve bir DocumentBuilder
      örneği oluşturun.
  - name: Belgeye üç ayrı metin paragrafı eklemek için DocumentBuilder.Writeln kullanın.
    text: Belgeye üç ayrı metin paragrafı eklemek için DocumentBuilder.Writeln kullanın.
  - name: Belgenin iki paragraftan az olması durumunda, ikinci paragrafı güvenli bir
      şekilde al, aksi takdirde ilk paragrafı kullan.
    text: Belgenin iki paragraftan az olması durumunda, ikinci paragrafı güvenli bir
      şekilde al, aksi takdirde ilk paragrafı kullan.
  - name: Yazar detaylarıyla bir Comment oluştur, metnini ayarla ve seçilen paragrafa
      ekle.
    text: Yazar detaylarıyla bir Comment oluştur, metnini ayarla ve seçilen paragrafa
      ekle.
  - name: Değiştirilen belgeyi geçerli klasörde 'sample.docx' adıyla bir DOCX dosyası
      olarak kaydedin.
    text: Değiştirilen belgeyi geçerli klasörde 'sample.docx' adıyla bir DOCX dosyası
      olarak kaydedin.
  type: HowTo
- questions:
  - answer: '`if` bloğu, `paraList.Count` 2''den az olduğunda ilk paragraf (`paraList[0]`)
      üzerine düşer, böylece yorum eksik ikinci paragraf yerine tek paragrafa eklenir.'
    question: Kod, belge yalnızca bir paragraf içeriyorsa ne yapar?
  - answer: Yazar adı ve baş harfler, `Comment` yapıcısına ikinci ve üçüncü argüman
      olarak geçirilir – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)`
      – burada "Jordan" yazar adı, "JH" ise baş harflerdir.
    question: Bu örnekte yorum yazarının adı ve baş harfleri nasıl ayarlanıyor?
  - answer: Bu kod parçasında yorum, `AppendChild` aracılığıyla tüm `Paragraph` öğesine
      bağlanır, ancak bir metin aralığına yorum eklemek için istenen `Run` düğümlerinin
      etrafına bir `CommentRangeStart` ve `CommentRangeEnd` oluşturmanız ve ardından
      `Comment` düğümünü aralarına eklemeniz gerekir.
    question: Yorumu tüm paragraf yerine belirli bir metin parçasına ekleyebilir miyim?
  - answer: '`AppendChild`, `Comment` düğümünü paragrafın çocuk koleksiyonuna ekler
      ve Aspose.Words belge kaydedildiğinde gerekli yorum başlangıç/bitiş işaretçilerini
      otomatik olarak oluşturur.'
    question: Yorum işaretçilerini manuel olarak eklemem gerekiyor mu, yoksa `AppendChild`
      bunu otomatik olarak yapıyor mu?
  type: FAQPage
images:
- /net/working-with-comments/add-comment/og-image.png
og_title: Bir Word paragrafına yorum ekleyin
og_description: Belirli bir paragrafa yazar yorumu ekleyin ve dosyayı Aspose.Words ile DOCX olarak dışa aktarın.
og_image_alt: Aspise.Words for .NET kullanarak bir Word belgesindeki bir paragrafa yorum eklemenin gösterildiği rehber
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak bir Word belgesindeki belirli bir paragraf üzerine Comment ekleyin
Aspose.Words for .NET ile Word dosyalarına programlı olarak yorum ekleyebilirsiniz. Bu öğreticide yeni bir belge oluşturma, üç paragraf ekleme, ikinci paragrafı bulma ve yazar ile tarih bilgilerini içeren bir yorum ekleme adımları gösterilmektedir. Son olarak, belge yorum korunarak bir DOCX dosyası olarak kaydedilir.

---

{{< tutorial-widget sourcePath="words/net/working-with-comments/add-comment" >}}


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

**Q: Kod, belge yalnızca bir paragraf içeriyorsa ne yapar?**  
A: `if` bloğu, `paraList.Count` 2'den az olduğunda ilk paragraf (`paraList[0]`) üzerine düşer, böylece yorum eksik ikinci paragraf yerine tek paragrafa eklenir.

**Q: Bu örnekte yorum yazarının adı ve baş harfleri nasıl ayarlanıyor?**  
A: Yazar adı ve baş harfler, `Comment` yapıcısına ikinci ve üçüncü argüman olarak geçirilir – `new Comment(wordDoc, \"Jordan\", \"JH\", DateTime.Now)` – burada "Jordan" yazar adı, "JH" ise baş harflerdir.

**Q: Yorumu tüm paragraf yerine belirli bir metin parçasına ekleyebilir miyim?**  
A: Bu kod parçasında yorum, `AppendChild` aracılığıyla tüm `Paragraph` öğesine bağlanır, ancak bir metin aralığına yorum eklemek için istenen `Run` düğümlerinin etrafına bir `CommentRangeStart` ve `CommentRangeEnd` oluşturmanız ve ardından `Comment` düğümünü aralarına eklemeniz gerekir.

**Q: Yorum işaretçilerini manuel olarak eklemem gerekiyor mu, yoksa `AppendChild` bunu otomatik olarak yapıyor mu?**  
A: `AppendChild`, `Comment` düğümünü paragrafın çocuk koleksiyonuna ekler ve Aspose.Words belge kaydedildiğinde gerekli yorum başlangıç/bitiş işaretçilerini otomatik olarak oluşturur.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}