---
title: درج شکست صفحه در یک سند Word با Aspose.Words برای .NET
weight: 110
limit:
description: یاد بگیرید چگونه با استفاده از Document و DocumentBuilder، شکست صفحه را به یک فایل Word با Aspose.Words برای .NET اضافه کنید.
keywords: [Aspose.Words for .NET, insert page break, documentbuilder page break, c# add page break, word document pagination]
url: /net/add-content-using-documentbuilder/insert-page-break/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# درج شکست صفحه در یک سند Word با Aspose.Words برای .NET
در این آموزش تعاملی، یاد می‌گیرید چگونه به‌صورت برنامه‌نویسی‌شده، شکست صفحه را به یک سند Word با استفاده از Aspose.Words برای .NET اضافه کنید. با ایجاد یک شیء Document و استفاده از DocumentBuilder می‌توانید مکان شروع صفحات جدید را کنترل کنید که برای قالب‌بندی گزارش‌ها، فاکتورها یا هر سند چندبخشی ضروری است. مثال گام‌به‌گام را دنبال کنید تا کد را در عمل ببینید و فایل حاصل را پیش‌نمایش کنید.

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

**Q: آیا می‌توانم از InsertBreak برای افزودن شکست خط یا شکست بخش به‌جای شکست صفحه استفاده کنم؟**
A: بله، InsertBreak هر مقدار enum از BreakType را می‌پذیرد، مانند BreakType.LineBreak یا BreakType.SectionBreakContinuous، تا شکست مربوطه را وارد کند.

**Q: آیا باید InsertBreak را قبل یا بعد از نوشتن متن برای صفحهٔ جدید فراخوانی کنم؟**
A: InsertBreak باید پس از محتوایی که می‌خواهید در صفحهٔ فعلی باشد فراخوانی شود؛ سپس Writeln بعدی در صفحهٔ جدیدی که توسط شکست ایجاد شده، شروع می‌شود.

**Q: اگر مسیر dataDir با جداکنندهٔ پوشه خاتمه نیابد چه اتفاقی می‌افتد؟**
A: اگر dataDir اسلش پایانی نداشته باشد، نام فایل مستقیماً به آن الحاق می‌شود (مثلاً "C:\\DocsAddContentUsingDocumentBuilder.InsertBreak.docx") که می‌تواند منجر به مسیر نامعتبر شود؛ اطمینان حاصل کنید مسیر با "\\" خاتمه یابد یا از Path.Combine استفاده کنید.

**Q: آیا می‌توانم از همان نمونهٔ DocumentBuilder برای وارد کردن چندین شکست در سراسر سند استفاده کنم؟**
A: بله، می‌توان از همان DocumentBuilder به‌صورت مکرر استفاده کرد؛ هر بار فراخوانی InsertBreak یک شکست را در موقعیت فعلی نشانگر builder وارد می‌کند.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}