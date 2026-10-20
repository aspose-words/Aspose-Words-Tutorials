---
category: general
date: 2026-04-04
description: Узнайте, как использовать параметры сохранения PDF в Java для преобразования
  DOCX в PDF и экспорта фигур в виде встроенных тегов. Пошаговое руководство по сохранению
  DOCX в PDF.
draft: false
keywords:
- pdf save options
- convert docx to pdf
- how to export shapes
- save docx as pdf
- convert word to pdf
language: ru
og_description: Откройте для себя варианты сохранения PDF в Java, чтобы преобразовать
  DOCX в PDF и экспортировать фигуры как встроенные теги. Полное руководство по сохранению
  DOCX в PDF.
og_title: 'Параметры сохранения PDF: преобразовать DOCX в PDF с тегами фигур'
tags:
- Aspose.Words
- Java
- PDF generation
title: 'Параметры сохранения PDF: конвертировать DOCX в PDF с тегами фигур'
url: /ru/java/document-conversion-and-export/pdf-save-options-convert-docx-to-pdf-with-shape-tags/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# pdf save options – Конвертация DOCX в PDF и экспорт фигур как встроенных тегов

Когда‑нибудь задавались вопросом, как **pdf save options** могут помочь вам **convert docx to pdf**, сохраняя плавающие фигуры в порядке? Вы не одиноки. Многие разработчики сталкиваются с проблемой, когда их документы Word содержат изображения, текстовые поля или графические объекты, которые перемещаются после конвертации.  

The good news? With a few lines of Java code you can tell Aspose.Words to treat those floating shapes as inline `<span>` tags, giving you a clean PDF that respects the original layout. In this tutorial we’ll walk through the entire process, from loading a `.docx` file to configuring the **pdf save options**, and finally saving the result as a PDF. By the end, you’ll know exactly **how to export shapes** correctly, and you’ll be ready to **save docx as pdf** in any Java project.

## Что вы узнаете

- How to **convert docx to pdf** using Aspose.Words for Java.  
- The role of **pdf save options** in shaping the final output.  
- The exact steps **how to export shapes** as inline tags.  
- Tips for troubleshooting common pitfalls when you **convert word to pdf**.  
- A complete, runnable code sample that you can drop into your IDE today.

## Предварительные требования

1. **Java Development Kit (JDK) 8 or newer** – the code runs on any recent JDK.  
2. **Aspose.Words for Java** library (version 23.10 or later). You can grab it from Maven Central:

   ```xml
   <dependency>
       <groupId>com.aspose</groupId>
       <artifactId>aspose-words</artifactId>
       <version>23.10</version>
   </dependency>
   ```

3. A **Word document** (`shapes.docx`) that contains floating shapes you want to export.  
4. A favorite IDE (IntelliJ IDEA, Eclipse, VS Code…) – whatever you’re comfortable with.

> **Pro tip:** If you’re using Maven, add the dependency to your `pom.xml` and let the IDE handle the download. No manual jar juggling required.

## Пошаговая реализация

Below we break the solution into four logical steps. Each step is wrapped in an H2 header – one of them even carries the primary keyword **pdf save options** to satisfy SEO.

### 1️⃣ Load the Source DOCX Document

First, we need to bring the Word file into memory. Aspose.Words makes this a one‑liner.

```java
import com.aspose.words.*;

public class PdfShapeTagging {
    public static void main(String[] args) throws Exception {
        // Step 1: Load the source Word document
        Document wordDoc = new Document("YOUR_DIRECTORY/shapes.docx");
```

*Why this matters:* Loading the document is the foundation for any conversion. If the path is wrong, the rest of the pipeline never runs, and you’ll see an exception that looks like “File not found”. Double‑check the directory separator for your OS (`/` works on Windows, macOS, and Linux).

### 2️⃣ Configure PDF Save Options to Export Shapes Inline

Here’s where the **pdf save options** shine. By default, Aspose treats floating shapes as separate objects, which can shift during conversion. Setting `setExportFloatingShapesAsInlineTag(true)` tells the engine to wrap each shape in an inline `<span>` tag, preserving its position relative to surrounding text.

```java
        // Step 2: Configure PDF save options to export floating shapes as inline <span> tags
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);
```

*Why this matters:* Without this flag, a floating text box might appear on a different page in the PDF, breaking the layout you spent hours perfecting. This option is the key answer to the question **how to export shapes** when you **convert docx to pdf**.

### 3️⃣ Save the Document as PDF Using the Configured Options

Now we actually write the PDF file. The `save` method takes the target path and the `PdfSaveOptions` we just set up.

```java
        // Step 3: Save the document as a PDF using the configured options
        wordDoc.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);
    }
}
```

*Why this matters:* The combination of `Document.save` and the customized `PdfSaveOptions` ensures that the final PDF respects both text flow and shape positioning. This is the definitive way to **save docx as pdf** when you need shape fidelity.

### 4️⃣ Verify the Result – What to Expect

After the program runs, open `output.pdf` in any PDF viewer. You should see:

- All paragraphs exactly as they appear in the original Word file.  
- Floating shapes (e.g., text boxes, images) rendered **inline** inside the surrounding paragraph, wrapped in invisible `<span>` tags (you won’t see the tags, but they keep layout intact).  
- No unexpected page breaks or shifted objects.

If anything looks off, double‑check that the source document actually uses floating shapes and that you’re using a recent version of Aspose.Words. Older versions may ignore the `setExportFloatingShapesAsInlineTag` flag.

> **Common pitfall:** Some developers try to **convert word to pdf** by simply calling `Document.save("out.pdf")` without setting any options. That works for plain text but often mangles complex layouts. Always configure the appropriate **pdf save options** when dealing with graphics.

## Полный рабочий пример

Below is the complete, self‑contained Java program you can copy‑paste into a new class file. Replace `YOUR_DIRECTORY` with the absolute path to your files.

```java
import com.aspose.words.*;

public class PdfShapeTagging {
    public static void main(String[] args) throws Exception {
        // Load the source Word document (make sure the path is correct)
        Document wordDoc = new Document("YOUR_DIRECTORY/shapes.docx");

        // Create PDF save options and tell Aspose to export floating shapes as inline <span> tags
        PdfSaveOptions pdfSaveOptions = new PdfSaveOptions();
        pdfSaveOptions.setExportFloatingShapesAsInlineTag(true);

        // Save the document as PDF using the configured options
        wordDoc.save("YOUR_DIRECTORY/output.pdf", pdfSaveOptions);

        System.out.println("Conversion complete! Check output.pdf to see the results.");
    }
}
```

**Expected console output:**

```
Conversion complete! Check output.pdf to see the results.
```

Open `output.pdf` and you’ll notice that every shape stays exactly where you placed it in `shapes.docx`. That’s the power of the right **pdf save options**.

## Часто задаваемые вопросы (FAQs)

**Q: Does this work with password‑protected DOCX files?**  
A: Yes. Load the document with a `LoadOptions` object that includes the password, then apply the same **pdf save options**.

**Q: Can I export shapes as separate images instead of inline tags?**  
A: Absolutely. Set `pdfSaveOptions.setExportFloatingShapesAsInlineTag(false)` and use `pdfSaveOptions.setExportEmbeddedImages(true)` to keep them as images.

**Q: What if I need to **convert docx to pdf** in a web service?**  
A: The same code applies; just stream the input and output bytes instead of using file paths. Aspose.Words works equally well with `InputStream`/`OutputStream`.

**Q: Is there a way to control the DPI of exported images?**  
A: Yes. Use `pdfSaveOptions.setImageDpi(300)` (or any value you need) before calling `save`.

## Следующие шаги и связанные темы

Now that you’ve mastered **pdf save options** for shape handling, you might want to explore:

- **How to export shapes** as SVG for vector‑rich PDFs.  
- Using **convert docx to pdf** with custom page margins and headers/footers.  
- Batch processing multiple Word files with a single Java routine.  
- Integrating the conversion into a Spring Boot REST endpoint to **save docx as pdf** on the fly.  

Each of these builds on the same foundation we covered here, so you’ll find the transition smooth.

## Заключение

We’ve walked through a complete, end‑to‑end solution that shows exactly **how to export shapes** when you **convert docx to pdf** using Aspose.Words for Java. By configuring the **pdf save options** to treat floating objects as inline tags, you get a faithful PDF representation without the layout surprises that often plague naive conversions.  

Give it a try, tweak the options to suit your project, and let the library do the heavy lifting. If you run into trouble, revisit the FAQs or check Aspose’s official docs – they’re a solid reference.

*Happy coding!*  

---

![Diagram illustrating pdf save options in action](image.png "pdf save options diagram")

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}