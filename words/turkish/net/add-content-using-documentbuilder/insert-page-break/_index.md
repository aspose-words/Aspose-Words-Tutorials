---
title: Aspose.Words for .NET ile bir Word belgesine Sayfa Sonu ekleyin
weight: 110
limit:
description: Document ve DocumentBuilder kullanarak Aspose.Words for .NET ile bir Word dosyasına sayfa sonları eklemeyi öğrenin.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET ile bir Word belgesine Sayfa Sonu ekleyin
Bu etkileşimli öğreticide, Aspose.Words for .NET kullanarak bir Word belgesine programlı olarak sayfa sonları eklemeyi öğreneceksiniz. Bir Document nesnesi oluşturarak ve DocumentBuilder kullanarak, yeni sayfaların nerede başlayacağını kontrol edebilirsiniz; bu, raporlar, faturalar veya çok bölümlü herhangi bir belgeyi biçimlendirmek için önemlidir. Kodu çalışırken görmek ve ortaya çıkan dosyayı ön izlemek için adım adım örneği izleyin.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-page-break" >}}


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

**Q: InsertBreak'i bir sayfa sonu yerine satır sonu veya bölüm sonu eklemek için kullanabilir miyim?**
A: Evet, InsertBreak, BreakType.LineBreak veya BreakType.SectionBreakContinuous gibi herhangi bir BreakType enum değerini kabul eder ve ilgili kesintiyi ekler.

**Q: Yeni sayfa için metni yazmadan önce mi yoksa sonra mı InsertBreak çağırmam gerekir?**
A: InsertBreak, mevcut sayfada istediğiniz içeriği ekledikten sonra çağrılmalıdır; sonraki Writeln, kesintiyle oluşturulan yeni sayfada başlayacaktır.

**Q: dataDir yolu bir dizin ayırıcı ile bitmezse ne olur?**
A: dataDir sonunda bir eğik çizgi (slash) yoksa dosya adı doğrudan birleştirilecektir (ör. "C:\DocsAddContentUsingDocumentBuilder.InsertBreak.docx"), bu da geçersiz bir yol oluşturabilir; yolun "\" ile bittiğinden emin olun veya Path.Combine kullanın.

**Q: Belge boyunca birden fazla kesinti eklemek için aynı DocumentBuilder örneğini yeniden kullanabilir miyim?**
A: Evet, aynı DocumentBuilder tekrar tekrar kullanılabilir; InsertBreak'in her çağrısı, builder'ın mevcut imleç konumunda bir kesinti ekler.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}