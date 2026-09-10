---
title: Aspose.Words for .NET kullanarak Word Belgesine Hizalanmış HTML Ekleme
weight: 210
limit:
description: Aspose.Words for .NET kullanarak ham HTML'yi sol, orta veya sağ hizalama ile bir Word belgesine eklemeyi öğrenin.
keywords: [Aspose.Words for .NET, insert html word document, html alignment, documentbuilder html, c# insert html, aligned html in word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word Belgesine Hizalanmış HTML Ekleme
Bu etkileşimli öğretici, Aspose.Words for .NET kullanarak ham HTML'nin bir Word belgesine nasıl gömüleceğini ve hizalamasının—sol, orta veya sağ—nasıl kontrol edileceğini gösterir. Document ve DocumentBuilder'dan yararlanarak bir HTML dizesi ekleyebilir ve istediğiniz paragraf hizalamasını sadece birkaç kod satırıyla uygulayabilirsiniz. Örnek, HTML biçimlendirmesini korumanız ve içeriği belgenizde tam olarak istediğiniz konuma yerleştirmeniz gerektiğinde idealdir.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-aligned-html" >}}


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
   ```

4. Apply License (Optional):
   To use the full version, [apply a license](https://purchase.aspose.com/temporary-license/) or use a [free trial](https://releases.aspose.com/).

## Also See
[Aspose.Words for .NET Documentation](https://docs.aspose.com/words/net/)
[Aspose.Words for .NET References](https://reference.aspose.com/words/net/)

## Frequently asked questions

**Q: DocumentBuilder.InsertHtml metoduna geçirilen HTML dizesi, Aspose.Words'ün desteklemediği <script> veya <iframe> gibi etiketler içerirse ne olur?**
A: Desteklenmeyen etiketler yok sayılır; Aspose.Words yalnızca render edebileceği HTML alt kümesini ayrıştırır, bu nedenle <script>, <iframe> ve benzeri öğeler çıkarılırken, içeriğin geri kalanı eklenir.

**Q: InsertHtml kullanıldığında satır içi CSS stilleri (ör. <span style\="color:red;">) korunur mu?**
A: Evet, InsertHtml renk, font‑size ve arka plan gibi birçok satır içi CSS özelliğine saygı gösterir ve bunları ilgili Word biçimlendirmesine dönüştürür.

**Q: InsertHtml, <div> veya <h1> gibi blok‑seviye öğeler için otomatik olarak yeni bir paragraf oluşturur mu?**
A: Blok‑seviye öğeler Word paragraflarına eşlenir, bu yüzden her <div>, <p>, <h1> vb. belge içinde ayrı bir paragraf haline gelir.

**Q: Mevcut bir belgenin başına değil, belirli bir konumuna HTML nasıl eklenir?**
A: InsertHtml'i çağırmadan önce DocumentBuilder imlecini istenen düğüme (ör. builder.MoveToDocumentEnd() veya builder.MoveToParagraph(index)) taşıyın; HTML mevcut imleç konumuna eklenecektir.

**Q: Belge zaten metin içeriyorsa, InsertHtml çağrısı mevcut içeriği üzerine yazar mı?**
A: Hayır, InsertHtml ayrıştırılan HTML'yi builder'ın mevcut konumuna ekler ve mevcut düğümleri silmez; yalnızca imleci o düğümlere taşıyorsanız veya önceden silerseniz içerik üzerine yazılır.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}