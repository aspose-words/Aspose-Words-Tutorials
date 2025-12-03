{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}
---
"date": "2025-03-29"
"description": "تعرّف على كيفية تحسين حفظ المستندات باستخدام Aspose.Words لـ Python باستخدام تنسيق XAML flow واستدعاءات التقدم. حسّن كفاءة إدارة المستندات."
"title": "تحسين حفظ المستندات في Python - استدعاءات التدفق والتقدم في Aspose.Words XAML"
"url": "/ar/python-net/performance-optimization/python-aspose-words-xaml-flow-progress-callbacks/"
"weight": 1
---

# كيفية تحسين حفظ المستندات في بايثون باستخدام Aspose.Words: استدعاءات XAML Flow وProgress

## مقدمة

هل تبحث عن إدارة تحويلات مستندات فعّالة باستخدام بايثون؟ هل تواجه صعوبة في التعامل مع الصور وتتبع التقدم أثناء حفظ المستندات؟ يرشدك هذا البرنامج التعليمي إلى كيفية تحسين حفظ المستندات باستخدام Aspose.Words لبايثون، مع التركيز على ميزتين فعّالتين: `XamlFlowSaveOptions` مع مجلد الصور واستدعاء تقدم حفظ المستندات.

يعد هذا الدليل الشامل مثاليًا للمطورين الذين يتطلعون إلى تحسين سير عمل معالجة المستندات الخاصة بهم باستخدام مكتبة Aspose.Words.

**ما سوف تتعلمه:**
- كيفية حفظ مستند بتنسيق XAML flow أثناء إدارة موارد الصورة.
- تنفيذ عمليات معاودة الاتصال بالتقدم أثناء حفظ المستند لمنع العمليات الطويلة.
- إعداد وتكوين Aspose.Words لـ Python في بيئة التطوير الخاصة بك.
- التطبيقات الواقعية لهذه الميزات في أنظمة إدارة المستندات.

دعونا نتعمق في المتطلبات الأساسية قبل أن نبدأ في الترميز!

## المتطلبات الأساسية

قبل أن تبدأ، تأكد من أن لديك ما يلي:

### المكتبات والإصدارات المطلوبة
- **كلمات Aspose لبايثون**:تأكد من أن لديك الإصدار 23.3 أو أحدث.
- **بايثون**:يوصى باستخدام الإصدار 3.6 أو أعلى.

### متطلبات إعداد البيئة
- محرر أكواد مثل VSCode أو PyCharm.
- المعرفة الأساسية ببرمجة بايثون.

### متطلبات المعرفة
- التعرف على مفاهيم معالجة المستندات.
- فهم التعامل مع الملفات وإدارة الدليل في بايثون.

## إعداد Aspose.Words لـ Python

لبدء استخدام Aspose.Words، يجب تثبيته عبر pip. افتح الطرفية أو موجه الأوامر وشغّل:

```bash
pip install aspose-words
```

### خطوات الحصول على الترخيص
1. **نسخة تجريبية مجانية**:الوصول إلى ترخيص مؤقت [هنا](https://purchase.aspose.com/temporary-license/) لأغراض الاختبار.
2. **شراء**:للاستخدام طويل الأمد، قم بشراء ترخيص [هنا](https://purchase.aspose.com/buy).
3. **التهيئة والإعداد الأساسي**:
   - قم بتحميل مستندك باستخدام `aw.Document()`.
   - قم بتكوين خيارات الحفظ حسب الحاجة.

## دليل التنفيذ

سوف يرشدك هذا القسم خلال تنفيذ الميزتين الرئيسيتين لهذا البرنامج التعليمي: XamlFlowSaveOptions مع مجلد الصور، واستدعاء تقدم حفظ المستند.

### الميزة 1: XamlFlowSaveOptions مع مجلد الصور

#### ملخص
تتيح لك هذه الميزة حفظ مستند بتنسيق XAML flow مع تحديد مجلد الصور واسم مستعار. وهي مثالية لإدارة المستندات الكبيرة المضمنة بالصور بكفاءة.

#### خطوات التنفيذ

##### الخطوة 1: استيراد المكتبات الضرورية
```python
import os
from datetime import datetime
import aspose.words as aw
```

##### الخطوة 2: تحديد فئة استدعاء ImageUriPrinter
تقوم هذه الفئة بحساب وإعادة توجيه تدفقات الصور إلى مجلد اسم مستعار محدد أثناء التحويل.

```python
class ExXamlFlowSaveOptionsImageFolder:
    class ImageUriPrinter(aw.saving.IImageSavingCallback):
        """Counts and prints filenames of images while their parent document is converted to flow-form .xaml."""
        
        def __init__(self, images_folder_alias: str):
            self.images_folder_alias = images_folder_alias
            self.resources = []  # النوع: قائمة[str]

        def image_saving(self, args: aw.saving.ImageSavingArgs):
            self.resources.append(args.image_file_name)
            with open(f"{self.images_folder_alias}/{args.image_file_name}", "wb") as image_stream:
                args.image_stream = image_stream
            args.keep_image_stream_open = False

    def test_image_folder(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Rendering.docx")
        callback = self.ImageUriPrinter(YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias")

        options = aw.saving.XamlFlowSaveOptions()
        options.images_folder = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolder"
        options.images_folder_alias = YOUR_OUTPUT_DIRECTORY + "XamlFlowImageFolderAlias"
        options.image_saving_callback = callback

        os.makedirs(options.images_folder_alias, exist_ok=True)
        
        doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.image_folder.xaml", options)

        for resource in callback.resources:
            print(f"{callback.images_folder_alias}/{resource}")
```
**خيارات تكوين المفاتيح:**
- `images_folder`:يحدد الدليل الذي سيتم حفظ الصور فيه.
- `images_folder_alias`:يحدد مسارًا مستعارًا يُستخدم أثناء تحويل المستند.

##### نصائح استكشاف الأخطاء وإصلاحها
- تأكد من وجود جميع الدلائل قبل تشغيل التعليمات البرمجية لتجنب أخطاء عدم العثور على الملف.
- التحقق من أذونات الكتابة في دليل الإخراج الخاص بك.

### الميزة 2: استدعاء تقدم حفظ المستند

#### ملخص
تعمل هذه الميزة على إدارة عملية الحفظ باستخدام استدعاء التقدم، مما يسمح لك بإلغاء عمليات الحفظ الطويلة الأمد.

#### خطوات التنفيذ

##### الخطوة 1: تحديد فئة SavingProgressCallback
تقوم الفئة بمراقبة مدة حفظ المستند وتلغي العملية إذا تجاوزت حدًا زمنيًا محددًا.

```python
class ExXamlFlowSaveOptionsProgressCallback:
    class SavingProgressCallback(aw.saving.IDocumentSavingCallback):
        """Saving progress callback. Cancel document saving after the 'max_duration' seconds."""
        
        def __init__(self):
            self.saving_started_at = datetime.now()
            self.max_duration = 0.01  # الحد الأقصى للمدة المسموح بها بالثانية.

        def notify(self, args: aw.saving.DocumentSavingArgs):
            canceled_at = datetime.now()
            elapsed_seconds = (canceled_at - self.saving_started_at).total_seconds()
            if elapsed_seconds > self.max_duration:
                raise OperationCanceledException(f"estimated_progress = {args.estimated_progress}; canceled_at = {canceled_at}")

    def test_progress_callback(self):
        YOUR_DOCUMENT_DIRECTORY = 'YOUR_DOCUMENT_DIRECTORY'
        YOUR_OUTPUT_DIRECTORY = 'YOUR_OUTPUT_DIRECTORY'

        parameters = [
            (aw.SaveFormat.XAML_FLOW, "xamlflow"),
            (aw.SaveFormat.XAML_FLOW_PACK, "xamlflowpack"),
        ]

        for save_format, ext in parameters:
            doc = aw.Document(f"{YOUR_DOCUMENT_DIRECTORY}/Big document.docx")
            save_options = aw.saving.XamlFlowSaveOptions(save_format)
            save_options.progress_callback = self.SavingProgressCallback()

            try:
                doc.save(f"{YOUR_OUTPUT_DIRECTORY}/XamlFlowSaveOptions.progress_callback.{ext}", save_options)
            except OperationCanceledException as e:
                print(e)
```
**خيارات تكوين المفاتيح:**
- `save_format`:اختر بين XAML_FLOW وXAML_FLOW_PACK.
- `progress_callback`:تراقب عملية الحفظ والتقدم للتعامل مع العمليات الطويلة.

##### نصائح استكشاف الأخطاء وإصلاحها
- يُعدِّل `max_duration` بناءً على حجم المستند وتعقيده.
- تعامل مع الاستثناءات بشكل جيد لتوفير رسائل خطأ مفيدة.

## التطبيقات العملية

فيما يلي بعض حالات الاستخدام الواقعية لهذه الميزات:
1. **أنظمة إدارة المستندات**:قم بإدارة المستندات الكبيرة التي تحتوي على صور مدمجة بكفاءة من خلال تحديد مجلدات الصور، مما يؤدي إلى تحسين الأداء والتنظيم.
2. **أدوات إعداد التقارير الآلية**:استخدم عمليات معاودة الاتصال بالتقدم للتأكد من إنشاء التقارير ضمن الأطر الزمنية المقبولة، مما يؤدي إلى تحسين تجربة المستخدم.
3. **شبكات توزيع المحتوى**:تبسيط عملية تحويل المستندات للتوزيع عبر الويب مع إدارة الموارد بشكل فعال.

## اعتبارات الأداء

لتحسين الأداء عند استخدام Aspose.Words مع Python:
- **إدارة الذاكرة**:راقب استخدام الموارد وقم بإدارة الذاكرة بكفاءة من خلال التخلص من الكائنات بعد الاستخدام.
- **عمليات إدخال/إخراج الملفات**:تقليل عمليات قراءة/كتابة الملفات لتحسين السرعة.
- **معالجة الدفعات**:قم بمعالجة المستندات على دفعات عندما يكون ذلك ممكنًا لتقليل النفقات العامة.

## خاتمة

في هذا البرنامج التعليمي، استكشفنا كيفية تحسين حفظ المستندات باستخدام Aspose.Words لـ Python باستخدام XAML Flow ووظائف استدعاء التقدم. بتطبيق هذه الميزات، يمكنك تحسين كفاءة سير عمل معالجة المستندات، وإدارة الموارد بفعالية، وضمان سير العمليات في الوقت المناسب.
{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}