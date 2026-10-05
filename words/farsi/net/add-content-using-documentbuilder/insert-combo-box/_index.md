---
title: افزودن فیلد فرم Combo Box به یک سند Word با Aspose.Words for .NET
weight: 310
limit:
description: یاد بگیرید چگونه یک فیلد فرم combo box با آیتم‌های از پیش تعریف‌شده را به یک سند Word با استفاده از Aspose.Words for .NET اضافه کنید.
keywords: [combo box form field, Aspose.Words for .NET, documentbuilder combo box, add combo box word, word document form field]
url: /net/add-content-using-documentbuilder/insert-combo-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# افزودن فیلد فرم Combo Box به یک سند Word با Aspose.Words
این آموزش نشان می‌دهد چگونه از DocumentBuilder در Aspose.Words for .NET برای ایجاد یک سند Word جدید و درج یک فیلد فرم combo box که با آیتم‌های از پیش تعریف‌شده پر شده است، استفاده کنید. با دنبال کردن کد گام‌به‌گام، خواهید دید چگونه گزینه‌های combo box را پیکربندی کنید و سپس سند را برای استفاده در فرم‌های تعاملی ذخیره کنید.

---

{{< tutorial-widget sourcePath="words/net/add-content-using-documentbuilder/insert-combo-box" >}}


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

**Q: آرایهٔ `items` که به `InsertComboBox` پاس داده می‌شود، چه چیزی را نشان می‌دهد؟**
A: این آرایه فهرست رشته‌هایی را تعریف می‌کند که به‌عنوان گزینه‌های قابل انتخاب در منوی کشویی combo box ظاهر می‌شوند.

**Q: چگونه می‌توانم آیتم پیش‌فرضی که هنگام باز شدن سند انتخاب می‌شود را تغییر دهم؟**
A: آرگومان سوم (`selectedIndex`) متد `InsertComboBox` را به اندیس صفر‑پایهٔ آیتم پیش‌فرض موردنظر تنظیم کنید (مثلاً `2` برای «Three»).

**Q: آیا امکان قرار دادن combo box در مکان خاصی از سند وجود دارد؟**
A: بله—پیش از فراخوانی `InsertComboBox`، مکان‌نمای `DocumentBuilder` را با استفاده از متدهایی مانند `MoveToParagraph`، `InsertParagraph` یا `Write` به نقطهٔ موردنظر منتقل کنید.

**Q: این کد چه فرمت فایلی ایجاد می‌کند و آیا می‌توان آن را در نسخه‌های قدیمی‌تر Word باز کرد؟**
A: کد یک فایل `.docx` ذخیره می‌کند که می‌تواند توسط Word 2007 و نسخه‌های بعدی، و همچنین هر برنامه‌ای که از فرمت OpenXML پشتیبانی می‌کند، باز شود.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}