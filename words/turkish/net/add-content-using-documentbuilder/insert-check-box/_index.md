---
title: Aspose.Words for .NET ile bir Word belgesine Check Box Form Field ekleyin
weight: 210
limit:
description: Aspose.Words for .NET kullanarak yeni bir Word belgesine programlı olarak bir onay kutusu form alanı eklemeyi ve dosyayı kaydetmeyi öğrenin.
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET ile bir Word belgesine Check Box Form Field ekleyin
Bu öğretici, yeni bir Word belgesi oluşturmayı ve Aspose.Words for .NET'in DocumentBuilder'ını kullanarak bir onay kutusu form alanı eklemeyi gösterir. Adımları izleyerek, etkileşimli öğeyi eklemek ve ardından belgeyi bir dosyaya kaydetmek için gereken kesin kodu göreceksiniz. Programlı olarak basit form‑etkin Word dosyaları oluşturmanın hızlı bir yoludur.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-check-box" >}}


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

**Q: InsertCheckBox'taki dördüncü argüman (0) neyi temsil ediyor?**
A: Bu, onay kutusunun görsel boyutunu puan cinsinden belirtir; 0 değeri Aspose.Words'e varsayılan boyutu kullanmasını söyler.

**Q: Aynı isimle birden fazla onay kutusu ekleyebilir miyim?**
A: Hayır – her form alanı adı benzersiz olmalıdır; \"CheckBox\" adlı başka bir onay kutusu eklemeye çalışmak bir ArgumentException fırlatır.

**Q: Yeni bir belge yerine mevcut bir belgeye onay kutusu nasıl eklenir?**
A: Önce belgeyi yükleyin (ör. `Document doc = new Document(\"Existing.docx\");`) ardından o belge için bir DocumentBuilder oluşturun ve istediğiniz imleç konumunda `InsertCheckBox` çağırın.

**Q: Belge kaydedildikten sonra eklenen onay kutusunun durumunu nasıl okuyabilirim?**
A: Form alanını `doc.Range.FormFields[\"CheckBox\"]` ile alın ve `Checked` özelliğini inceleyerek işaretli olup olmadığını kontrol edin.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}