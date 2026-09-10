---
title: Aspose.Words for .NET kullanarak Word belgesine Yatay Çizgi Şekli ekleme
weight: 110
limit:
description: DocumentBuilder kullanarak Aspose.Words for .NET ile bir Word belgesine yatay çizgi şekli eklemeyi öğrenin.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, documentbuilder horizontal line, create Word document .NET, horizontal rule shape tutorial]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET kullanarak Word belgesine Yatay Çizgi Şekli ekleme
Bu öğreticide, Aspose.Words for .NET ile bir Word belgesine programlı olarak yatay çizgi şekli eklemeyi öğreneceksiniz. Document ve DocumentBuilder sınıflarını kullanarak yeni bir belge oluşturur, bir metin paragrafı ekler ve ardından istediğiniz konuma bir yatay çizgi şekli yerleştiririz. Yatay çizgi, bölüm ayrımları veya görsel vurgu için faydalı olabilecek bir görsel ayırıcı sağlar.

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

**Q: `builder.InsertHorizontalRule()` satırı belge içinde tam olarak nereye yerleştirir?**
A: `InsertHorizontalRule`, `DocumentBuilder`'ın mevcut imleç konumuna bir yatay çizgi şekli ekler; eğer satır başına tek başına olmasını istiyorsanız, eklemeden önce `builder.Writeln()` çağırın.

**Q: Eklenen yatay çizginin kalınlığını, rengini veya genişliğini değiştirebilir miyim?**
A: `InsertHorizontalRule`, varsayılan stilli bir çizgi ekler ve biçimlendirme seçeneklerini sunmaz; bu özellikleri özelleştirmek için bir `Shape` nesnesini manuel olarak eklemeniz gerekir (ör. `builder.InsertShape(ShapeType.HorizontalLine)`) ve ardından `LineFormat` özelliklerini ayarlamalısınız.

**Q: Aynı belgede birden fazla yatay çizgi eklemek mümkün mü?**
A: Evet—yeni bir çizgiye ihtiyacınız olduğunda `builder.InsertHorizontalRule()`'ı sadece çağırın; her çağrı, builder'ın mevcut konumunda ayrı bir şekil oluşturur.

**Q: Kaydedilen .docx Microsoft Word'de açıldığında yatay çizgi görünür mü?**
A: Kesinlikle; çizgi .docx dosyasının içinde bir şekil olarak kaydedilir, bu yüzden Word onu oluşturulan belgede göründüğü gibi tam olarak gösterir.

**Q: `doc.Save(...)` çağrılmadan önce `dataDir` klasörü mevcut değilse ne olur?**
A: `doc.Save`, bir `DirectoryNotFoundException` fırlatır; hedef dizinin var olduğundan emin olun veya kaydetmeden önce programlı olarak oluşturun.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}