---
title: درج شکل خط افقی در سند Word با استفاده از Aspose.Words برای .NET
weight: 110
limit:
description: راهنمای گام به گام برای درج یک شکل خط افقی در سند Word با Aspose.Words برای .NET.
keywords: [Aspose.Words for .NET, insert horizontal rule shape, horizontal rule shape .NET, DocumentBuilder horizontal rule, add horizontal line Word, create Word document Aspose]
url: /net/add-content-using-documentbuilder/insert-horizontal-rule-shape/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# درج شکل خط افقی در سند Word با استفاده از Aspose.Words برای .NET
بیاموزید چگونه از Aspose.Words برای .NET برای درج یک شکل خط افقی در یک سند Word استفاده کنید. این آموزش شما را گام به گام در ایجاد یک سند جدید، افزودن یک خط متن، قرار دادن یک شکل خط افقی با DocumentBuilder و ذخیره فایل راهنمایی می‌کند. خط افقی یک جداکننده بصری ساده برای محتوای شما فراهم می‌کند.

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

**Q: آیا می‌توانم ظاهر (رنگ، ضخامت) خط افقی وارد شده با DocumentBuilder.InsertHorizontalRule() را تغییر دهم؟**
A: InsertHorizontalRule یک شکل خط افقی داخلی با قالب‌بندی پیش‌فرض ایجاد می‌کند؛ برای تغییر ظاهر آن باید شیء Shape وارد شده (builder.CurrentParagraph.LastChild) را بازیابی کنید و ویژگی‌های LineFormat آن را تنظیم کنید.

**Q: اگر InsertHorizontalRule() را پس از پاراگرافی که قبلاً با یک شکست خط تمام می‌شود فراخوانی کنم، چه اتفاقی می‌افتد؟**
A: این متد خط افقی را به عنوان یک پاراگراف جداگانه وارد می‌کند، بنابراین هر شکست خط پیشین فقط یک پاراگراف خالی قبل از خط افقی ایجاد می‌کند؛ خط افقی همچنان در خط خود ظاهر می‌شود.

**Q: آیا امکان درج بیش از یک خط افقی در همان سند با استفاده از DocumentBuilder وجود دارد؟**
A: بله، هر بار فراخوانی builder.InsertHorizontalRule() یک شکل خط افقی جدید را در موقعیت فعلی مکان‌نما اضافه می‌کند و امکان داشتن چندین خط افقی در سراسر سند را فراهم می‌آورد.

**Q: آیا InsertHorizontalRule() هنگام ذخیره سند به فرمت‌های دیگری غیر از DOCX، مانند PDF، کار می‌کند؟**
A: خط افقی به عنوان یک Shape در مدل سند ذخیره می‌شود، بنابراین هنگام ذخیره به PDF، XPS یا سایر فرمت‌های پشتیبانی‌شده، خط افقی به‌درستی در خروجی رندر می‌شود.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}