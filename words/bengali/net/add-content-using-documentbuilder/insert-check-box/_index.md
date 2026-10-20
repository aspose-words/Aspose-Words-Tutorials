---
title: Aspose.Words for .NET ব্যবহার করে একটি Word ডকুমেন্টে চেক বক্স ফর্ম ফিল্ড যোগ করুন
weight: 210
limit:
description: Aspose.Words for .NET ব্যবহার করে প্রোগ্রাম্যাটিকভাবে একটি নতুন Word ডকুমেন্টে চেক বক্স ফর্ম ফিল্ড কীভাবে যোগ করবেন এবং ফাইলটি কীভাবে সংরক্ষণ করবেন শিখুন।
keywords: [Aspose.Words for .NET, insert check box, check box form field, .NET DocumentBuilder, Word document automation, add form field programmatically]
url: /net/add-content-using-documentbuilder/insert-check-box/
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Aspose.Words for .NET ব্যবহার করে একটি Word ডকুমেন্টে চেক বক্স ফর্ম ফিল্ড যোগ করুন
এই টিউটোরিয়ালটি দেখায় কীভাবে একটি নতুন Word ডকুমেন্ট তৈরি করা যায় এবং Aspose.Words for .NET এর DocumentBuilder ব্যবহার করে একটি চেক বক্স ফর্ম ফিল্ড সন্নিবেশ করা যায়। ধাপগুলি অনুসরণ করলে আপনি ইন্টারেক্টিভ উপাদানটি যোগ করার জন্য প্রয়োজনীয় সঠিক কোড এবং পরে ডকুমেন্টটি ফাইলে সংরক্ষণ করার পদ্ধতি দেখতে পাবেন। এটি প্রোগ্রাম্যাটিকভাবে সহজ ফর্ম-সক্ষম Word ফাইল তৈরি করার একটি দ্রুত উপায়।

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

**Q: InsertCheckBox-এ চতুর্থ আর্গুমেন্ট (0) কী প্রতিনিধিত্ব করে?**
A: এটি পয়েন্টে চেক বক্সের দৃশ্যমান আকার নির্ধারণ করে; 0 মান Aspose.Words-কে ডিফল্ট আকার ব্যবহার করতে নির্দেশ করে।

**Q: আমি কি একই নামের একাধিক চেক বক্স সন্নিবেশ করতে পারি?**
A: না – প্রতিটি ফর্ম ফিল্ডের নাম ইউনিক হতে হবে; "CheckBox" নামের আরেকটি চেক বক্স সন্নিবেশ করার চেষ্টা করলে ArgumentException ঘটবে।

**Q: নতুন ডকুমেন্টের পরিবর্তে বিদ্যমান ডকুমেন্টে কীভাবে চেক বক্স যোগ করব?**
A: প্রথমে ডকুমেন্টটি লোড করুন (যেমন, `Document doc = new Document("Existing.docx");`) তারপর সেই ডকুমেন্টের জন্য একটি DocumentBuilder তৈরি করুন এবং কাঙ্ক্ষিত কার্সার অবস্থানে `InsertCheckBox` কল করুন।

**Q: ডকুমেন্ট সংরক্ষণ করার পরে সন্নিবেশিত চেক বক্সের অবস্থা কীভাবে পড়তে পারি?**
A: `doc.Range.FormFields["CheckBox"]` এর মাধ্যমে ফর্ম ফিল্ডটি পুনরুদ্ধার করুন এবং তার `Checked` প্রপার্টি পরীক্ষা করুন যাতে দেখা যায় এটি চেকড ছিল কিনা।

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}