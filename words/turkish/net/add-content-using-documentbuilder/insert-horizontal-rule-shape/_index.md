---
title: Aspose.Words for .NET kullanarak Word belgesine Yatay Çizgi Şekli ekleyin
weight: 110
limit:
description: Aspose.Words for .NET ile bir Word belgesine yatay çizgi şekli eklemek için adım adım rehber.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word belgesine Yatay Çizgi Şekli ekleyin
Aspose.Words for .NET'i kullanarak bir Word belgesine yatay çizgi şekli eklemenin nasıl yapılacağını öğrenin. Bu öğreticide yeni bir belge oluşturma, bir metin satırı ekleme, DocumentBuilder ile yatay çizgi şekli yerleştirme ve dosyayı kaydetme adımları gösterilmektedir. Yatay çizgi, içeriğiniz için basit bir görsel ayırıcı görevi görür.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-horizontal-rule-shape" >}}


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

**Q: DocumentBuilder.InsertHorizontalRule() ile eklenen yatay çizginin görünümünü (renk, kalınlık) değiştirebilir miyim?**
A: InsertHorizontalRule, varsayılan biçimlendirmeye sahip yerleşik bir yatay çizgi şekli oluşturur; görünümünü değiştirmek için eklenen Shape nesnesini (builder.CurrentParagraph.LastChild) almalı ve LineFormat özelliklerini ayarlamalısınız.

**Q: InsertHorizontalRule() metodunu, zaten bir satır sonu ile biten bir paragraftan sonra çağırırsam ne olur?**
A: Metod, kuralı ayrı bir paragraf olarak ekler, bu yüzden önceden gelen satır sonu sadece kuralın önünde boş bir paragraf oluşturur; kural hâlâ kendi satırında görünecektir.

**Q: DocumentBuilder kullanarak aynı belgede birden fazla yatay çizgi eklemek mümkün mü?**
A: Evet, builder.InsertHorizontalRule() her çağrıldığında mevcut imleç konumunda yeni bir yatay çizgi şekli ekler ve belge boyunca birden fazla kural kullanılabilir.

**Q: InsertHorizontalRule() DOCX dışındaki formatlara, örneğin PDF'e kaydederken çalışır mı?**
A: Yatay çizgi, belge modelinde bir şekil olarak depolanır; bu nedenle PDF, XPS veya diğer desteklenen formatlara kaydettiğinizde kural çıktıda doğru şekilde render edilir.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}