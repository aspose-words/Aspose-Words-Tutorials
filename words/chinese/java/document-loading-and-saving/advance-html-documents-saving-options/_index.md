---
date: 2025-12-19
description: 学习如何使用 Aspose.Words Java 导出 HTML，涵盖将 Word 保存为 HTML 的高级选项以及高效地将 Word 转换为
  HTML。
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 如何使用 Aspose.Words Java 导出 HTML：高级选项
url: /zh/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# 如何使用 Aspose.Words Java 导出 HTML：高级选项

在本教程中，您将了解 **如何使用 Aspose.Words for Java 将 Word 文档导出为 HTML**。无论是需要 **将 Word 保存为 HTML** 以进行网页发布，还是 **将 Word 转换为 HTML** 以进行后续处理，高级保存选项都能让您对输出进行细粒度控制。我们将逐步演示每个选项，说明何时使用，并展示这些设置在实际场景中的作用。

## 快速答案
- **导出 HTML 的主要类是什么？** `HtmlSaveOptions`  
- **可以将字体直接嵌入 HTML 吗？** 可以，将 `exportFontsAsBase64` 设置为 `true`。  
- **如何保留 Word 特有的往返数据？** 启用 `exportRoundtripInformation`。  
- **哪种格式最适合矢量图形？** 使用 `convertMetafilesToSvg` 导出为 SVG。  
- **是否可以避免 CSS 类名冲突？** 可以，使用 `addCssClassNamePrefix`。

## 1. 介绍
Aspose.Words for Java 是一个强大的 API，允许开发者以编程方式操作 Word 文档。本指南聚焦于高级 HTML 文档保存选项，帮助您根据特定的网页或集成需求定制转换过程。

## 2. 导出往返信息
保留往返信息可让您在将 HTML 再转换回 Word 文档时不丢失布局或格式细节。

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### 何时使用
- 当您需要可逆的转换流水线（HTML → Word → HTML）时。  
- 适用于协作编辑场景，需要保留原始 Word 结构。

## 3. 将字体导出为 Base64
将字体直接嵌入 HTML 可消除对外部字体的依赖，并确保在各浏览器中的视觉一致性。

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### 专业提示
在目标环境对外部资源访问受限（例如电子邮件新闻稿）时使用此选项。

## 4. 导出资源
控制 CSS 与字体资源的输出方式，并为这些资产指定自定义文件夹或 URL 别名。

```java

public void exportResources() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setExportFontResources(true);
    saveOptions.setResourceFolder("Your Directory Path" + "Resources");
    saveOptions.setResourceFolderAlias("http://example.com/resources");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportResources.html", saveOptions);
}
```

### 为什么重要
将 CSS 分离为外部文件可减小 HTML 大小，并通过缓存加快页面加载速度。

## 5. 将元文件转换为 EMF 或 WMF
元文件（如 EMF/WMF）会被转换为浏览器能够可靠渲染的格式。

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n                    vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

### 使用场景
当目标浏览器支持这些矢量格式且需要无损缩放时，选择 EMF/WMF。

## 6. 将元文件转换为 SVG
SVG 提供最佳的可伸缩性，并在现代浏览器中得到广泛支持。

```java

public void convertMetafilesToSvg() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);
	
	builder.write("Here is an SVG image: ");
	builder.insertHtml(
		"<svg height='210' width='500'>\r\n                <polygon points='100,10 40,198 190,78 10,78 160,198' \r\n                    style='fill:lime;stroke:purple;stroke-width:5;fill-rule:evenodd;' />\r\n            </svg> ");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.SVG); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToSvg.html", saveOptions);
}
```

### 好处
SVG 文件体积轻巧且保持分辨率无关性，非常适合响应式网页设计。

## 7. 添加 CSS 类名前缀
通过为所有生成的 CSS 类名添加前缀，防止样式冲突。

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### 实用技巧
在将 HTML 嵌入现有页面时，使用唯一前缀（例如项目名称）以避免 CSS 冲突。

## 8. 为 MHTML 资源导出 CID URL
保存为 MHTML 时，可使用 Content‑ID URL 导出资源，以提升邮件兼容性。

```java

public void exportCidUrlsForMhtmlResources() throws Exception {
	string dataDir = "Your Document Directory";
    Document doc = new Document(dataDir + "Content-ID.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.MHTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setExportCidUrlsForMhtmlResources(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportCidUrlsForMhtmlResources.mhtml", saveOptions);
}
```

### 何时使用
适用于生成单个自包含 HTML 文件并可作为邮件附件发送的场景。

## 9. 解析字体名称
确保 HTML 引用正确的字体族，提升跨平台一致性。

```java

public void resolveFontNames() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Missing font.docx");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setPrettyFormat(true); saveOptions.setResolveFontNames(true);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ResolveFontNames.html", saveOptions);
}
```

### 为什么有帮助
如果原始文档使用的字体在客户端机器上未安装，此选项会将其替换为网页安全字体。

## 10. 将文本输入表单字段导出为文本
将表单字段渲染为纯文本，而非交互式 HTML 输入元素。

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// The folder specified needs to exist and should be empty.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Set an option to export form fields as plain text, not as HTML input elements.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

### 使用场景
当您需要只读的表单表示用于归档或打印时。

## 常见陷阱与故障排除
| 问题 | 常见原因 | 解决方案 |
|------|----------|----------|
| 输出中缺少字体 | 未启用 `exportFontsAsBase64` | 设置 `setExportFontsAsBase64(true)` |
| 嵌入后 CSS 损坏 | 使用 `EXTERNAL` 而未提供 CSS 文件 | 确保在指定的 `resourceFolderAlias` 处部署 CSS 文件 |
| HTML 文件体积过大 | 将大量图片嵌入为 Base64 | 通过 `setExportFontResources(true)` 使用外部图片资源并配置 `resourceFolder` |
| 老旧浏览器不渲染 SVG | 浏览器不支持 SVG | 同时导出为 EMF/WMF 并提供 PNG 作为回退 |

## 常见问答

**问：我可以同时将字体嵌入为 Base64 并保持外部 CSS 吗？**  
答：可以。将 `exportFontsAsBase64(true)` 与 `CssStyleSheetType.EXTERNAL` 同时设置，即可将字体数据与样式规则分离。

**问：如何将已有的 HTML 转回 Word 文档？**  
答：使用 `Document doc = new Document("input.html");` 加载 HTML，然后 `doc.save("output.docx");`。在初始导出时通过 `exportRoundtripInformation` 保留往返数据。

**问：使用 SVG 转换会有性能影响吗？**  
答：将大型元文件转换为 SVG 可能会增加处理时间，但生成的 HTML 通常更小，且在浏览器中渲染更快。

**问：这些选项在 Aspose.Words for .NET 中也适用吗？**  
答：相同的概念在 .NET API 中也存在，尽管方法名称可能略有不同（例如 `HtmlSaveOptions` 在各平台之间是共享的）。

**问：哪种选项适合邮件友好的 HTML？**  
答：使用 `SaveFormat.MHTML` 并启用 `exportCidUrlsForMhtmlResources`，即可将所有资源直接嵌入邮件正文。

---

**最后更新：** 2025-12-19  
**测试环境：** Aspose.Words for Java 24.12  
**作者：** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}