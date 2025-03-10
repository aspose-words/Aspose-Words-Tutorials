---
title: Προηγμένες επιλογές αποθήκευσης εγγράφων HTML με το Aspose.Words Java
linktitle: Αποθήκευση εγγράφων HTML με
second_title: Aspose.Words Java Document Processing API
description: Σε αυτό το σεμινάριο, έχουμε καλύψει διάφορες προηγμένες επιλογές αποθήκευσης εγγράφων HTML με το Aspose.Words για Java. Αυτές οι επιλογές σάς δίνουν τη δυνατότητα να δημιουργήσετε HTML υψηλής ποιότητας
weight: 16
url: /el/java/document-loading-and-saving/advance-html-documents-saving-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Προηγμένες επιλογές αποθήκευσης εγγράφων HTML με το Aspose.Words Java


Σε αυτό το σεμινάριο, θα εξερευνήσουμε τις προηγμένες επιλογές αποθήκευσης εγγράφων HTML που παρέχονται από το Aspose.Words για Java. Το Aspose.Words είναι ένα ισχυρό API Java για εργασία με έγγραφα του Word και προσφέρει ένα ευρύ φάσμα δυνατοτήτων για χειρισμό και μετατροπή εγγράφων.

## 1. Εισαγωγή
Το Aspose.Words για Java σάς επιτρέπει να εργάζεστε με έγγραφα του Word μέσω προγραμματισμού. Σε αυτό το σεμινάριο, θα επικεντρωθούμε σε προηγμένες επιλογές αποθήκευσης εγγράφων HTML, οι οποίες σας επιτρέπουν να ελέγχετε τον τρόπο μετατροπής των εγγράφων του Word σε HTML.

## 2. Εξαγωγή πληροφοριών μετ' επιστροφής
 Ο`exportRoundtripInformation` Η μέθοδος σάς επιτρέπει να εξάγετε έγγραφα του Word σε HTML διατηρώντας ταυτόχρονα τις πληροφορίες μετ' επιστροφής. Αυτές οι πληροφορίες μπορεί να είναι χρήσιμες όταν θέλετε να μετατρέψετε την HTML ξανά σε μορφή Word χωρίς να χάσετε λεπτομέρειες σχετικά με το έγγραφο.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Εξαγωγή γραμματοσειρών ως Base64
 Με το`exportFontsAsBase64` Με τη μέθοδο, μπορείτε να εξάγετε γραμματοσειρές που χρησιμοποιούνται στο έγγραφο ως δεδομένα κωδικοποιημένα με Base64 σε HTML. Αυτό διασφαλίζει ότι η αναπαράσταση HTML διατηρεί τα ίδια στυλ γραμματοσειράς με το αρχικό έγγραφο του Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Εξαγωγή Πόρων
 Ο`exportResources` Η μέθοδος σάς επιτρέπει να καθορίσετε τον τύπο του φύλλου στυλ CSS και να εξάγετε πόρους γραμματοσειράς. Μπορείτε επίσης να ορίσετε έναν φάκελο πόρων και ένα ψευδώνυμο για πόρους στο HTML.

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

## 5. Μετατρέψτε τα Metafiles σε EMF ή WMF
 Ο`convertMetafilesToEmfOrWmf`Η μέθοδος σάς επιτρέπει να μετατρέψετε μετα-αρχεία στο έγγραφο είτε σε μορφή EMF είτε σε μορφή WMF, διασφαλίζοντας συμβατότητα και ομαλή απόδοση σε HTML.

```java

public void convertMetafilesToEmfOrWmf() throws Exception {

	string dataDir = "Your Document Directory";
    Document doc = new Document();
	DocumentBuilder builder = new DocumentBuilder(doc);

	builder.write("Here is an image as is: ");
	builder.insertHtml(
		"<img src=\"data:image/png;base64,\r\n                    iVBORw0KGgoAAAANSUhEUgAAAAoAAAAKCAYAAACNMs+9AAAABGdBTUEAALGP\r\n                    C/xhBQAAAAlwSFlzAAALEwAACxMBAJqcGAAAAAd0SU1FB9YGARc5KB0XV+IA\r\n                    AAAddEVYdENvbW1lbnQAQ3JlYXRlZCB3aXRoIFRoZSBHSU1Q72QlbgAAAF1J\r\n                    REFUGNO9zL0NglAAxPEfdLTs4BZM4DIO4C7OwQg2JoQ9LE1exdlYvBBeZ7jq\r\n                    ch9//q1uH4TLzw4d6+ErXMMcXuHWxId3KOETnnXXV6MJpcq2MLaI97CER3N0\r\n vr4MkhoXe0rZigAAAABJRU5ErkJggg==\" alt=\"Red dot\" />");

	HtmlSaveOptions saveOptions = new HtmlSaveOptions(); { saveOptions.setMetafileFormat(HtmlMetafileFormat.EMF_OR_WMF); }

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ConvertMetafilesToEmfOrWmf.html", saveOptions);
}
```

## 6. Μετατρέψτε τα Metafiles σε SVG
 Χρησιμοποιήστε το`convertMetafilesToSvg` μέθοδος μετατροπής μετα-αρχείων σε μορφή SVG. Αυτή η μορφή είναι ιδανική για την εμφάνιση διανυσματικών γραφικών σε έγγραφα HTML.

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

## 7. Προσθέστε το πρόθεμα ονόματος κλάσης CSS
 Με το`addCssClassNamePrefix` μέθοδο, μπορείτε να προσθέσετε ένα πρόθεμα σε ονόματα κλάσεων CSS στο εξαγόμενο HTML. Αυτό βοηθά στην αποφυγή διενέξεων με υπάρχοντα στυλ.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Εξαγωγή διευθύνσεων URL CID για πόρους MHTML
 Ο`exportCidUrlsForMhtmlResources` Η μέθοδος χρησιμοποιείται κατά την αποθήκευση εγγράφων σε μορφή MHTML. Επιτρέπει την εξαγωγή διευθύνσεων URL Content-ID για πόρους.

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

## 9. Επίλυση ονομάτων γραμματοσειρών
 Ο`resolveFontNames` Η μέθοδος βοηθά στην επίλυση ονομάτων γραμματοσειρών κατά την αποθήκευση εγγράφων σε μορφή HTML, διασφαλίζοντας συνεπή απόδοση σε διαφορετικές πλατφόρμες.

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

## 10. Εξαγωγή πεδίου φόρμας εισαγωγής κειμένου ως κείμενο
 Ο`exportTextInputFormFieldAsText`Οι εξαγωγές μεθόδου σχηματίζουν πεδία ως απλό κείμενο στο HTML, καθιστώντας τα εύκολα αναγνώσιμα και επεξεργάσιμα.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Ο καθορισμένος φάκελος πρέπει να υπάρχει και να είναι κενός.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Ορίστε μια επιλογή για εξαγωγή πεδίων φόρμας ως απλό κείμενο, όχι ως στοιχεία εισαγωγής HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Σύναψη
Σε αυτό το σεμινάριο, εξερευνήσαμε τις προηγμένες επιλογές αποθήκευσης εγγράφων HTML που παρέχονται από το Aspose.Words για Java. Αυτές οι επιλογές σάς δίνουν λεπτομερή έλεγχο της διαδικασίας μετατροπής, επιτρέποντάς σας να δημιουργήσετε έγγραφα HTML που μοιάζουν πολύ με τα αρχικά έγγραφα του Word.

## Συχνές ερωτήσεις
Ακολουθούν ορισμένες συχνές ερωτήσεις σχετικά με την εργασία με το Aspose.Words for Java και τις επιλογές αποθήκευσης εγγράφων HTML:

### Ε1: Πώς μπορώ να μετατρέψω την HTML ξανά σε μορφή Word χρησιμοποιώντας το Aspose.Words για Java;
 Για να μετατρέψετε την HTML ξανά σε μορφή Word, μπορείτε να χρησιμοποιήσετε τα API του Aspose.Words`load` μέθοδος για να φορτώσετε το έγγραφο HTML και στη συνέχεια να το αποθηκεύσετε σε μορφή Word.

### Ε2: Μπορώ να προσαρμόσω τα στυλ CSS κατά την εξαγωγή σε HTML;
Ναι, μπορείτε να προσαρμόσετε τα στυλ CSS τροποποιώντας τα φύλλα στυλ που χρησιμοποιούνται στο HTML ή χρησιμοποιώντας το`addCssClassNamePrefix` μέθοδος για να προσθέσετε ένα πρόθεμα στα ονόματα κλάσεων CSS.

### Ε3: Υπάρχει τρόπος να βελτιστοποιήσετε την έξοδο HTML για την προβολή Ιστού;
Ναι, μπορείτε να βελτιστοποιήσετε την έξοδο HTML για προβολή Ιστού διαμορφώνοντας επιλογές όπως η εξαγωγή γραμματοσειρών ως Base64 και η μετατροπή μετα-αρχείων σε SVG.

### Ε4: Υπάρχουν περιορισμοί κατά τη μετατροπή σύνθετων εγγράφων του Word σε HTML;
Ενώ το Aspose.Words για Java παρέχει ισχυρές δυνατότητες μετατροπής, πολύπλοκα έγγραφα του Word με περίπλοκες διατάξεις ενδέχεται να απαιτούν πρόσθετη μετα-επεξεργασία για να επιτευχθεί η επιθυμητή έξοδος HTML.

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
