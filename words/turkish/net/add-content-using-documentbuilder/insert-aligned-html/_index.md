---
title: Aspose.Words for .NET kullanarak Word Belgesine Hizalanmış HTML ekleyin
weight: 210
limit:
description: Aspose.Words for .NET kullanarak bir Word belgesine belirli hizalama ile HTML eklemeyi öğrenin.
keywords: [insert aligned html, Aspose.Words for .NET, documentbuilder html insertion, html alignment in word, c# insert html word]
url: /net/add-content-using-documentbuilder/insert-aligned-html/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word Belgesine Hizalanmış HTML ekleyin
Bu öğreticide, Aspose.Words for .NET'in DocumentBuilder'ını kullanarak HTML işaretlemesini bir Word belgesine gömmek ve hizalamasını kontrol etmek gösterilmektedir. HTML'i nasıl ekleyeceğinizi, paragraf hizalamasını (sol, orta veya sağ) nasıl ayarlayacağınızı ve ardından ortaya çıkan belgeyi nasıl kaydedeceğinizi göreceksiniz. Örnek, web‑stili biçimlendirmeyi koruyarak Word dosyalarını programlı olarak oluşturması gereken geliştiriciler için idealdir.

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

**Q: InsertHtml, yeni bir belge yerine mevcut bir Word belgesine HTML eklemek için kullanılabilir mi?**  
A: Evet. Mevcut dosyadan bir Document oluşturun, DocumentBuilder imlecini HTML'in eklenmesini istediğiniz konuma (örneğin builder.MoveToDocumentEnd() kullanarak) getirin ve ardından builder.InsertHtml ile işaretlemenizi çağırın.

**Q: InsertHtml hizalama için hangi HTML niteliklerini dikkate alır?**  
A: InsertHtml, &lt;p&gt;, &lt;div&gt; ve başlık etiketleri gibi blok‑seviyeli öğelerdeki \"align\" niteliğine saygı gösterir ve ortaya çıkan Word belgesinde ilgili paragraf hizalamasını uygular.

**Q: HTML dizesi desteklenmeyen etiketler veya CSS içeriyorsa ne olur?**  
A: Desteklenmeyen etiketler yok sayılır ve iç metinleri düz metin olarak eklenir; Aspose.Words'un tanımadığı satır içi CSS stilleri de yok sayılır, bu nedenle yalnızca desteklenen HTML alt kümesi işlenir.

**Q: Belgeyi kaydetmeden önce DocumentBuilder'ı kapatmam gerekir mi?**  
A: Açık bir kapatma işlemi gerekmez; HTML'i ekledikten sonra istediğiniz dosya adı ve formatıyla doğrudan doc.Save'i çağırabilirsiniz ve builder'ın kaynakları otomatik olarak serbest bırakılır.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}