---
"description": "Σε αυτό το σεμινάριο, καλύψαμε διάφορες προηγμένες επιλογές αποθήκευσης εγγράφων HTML με το Aspose.Words για Java. Αυτές οι επιλογές σάς δίνουν τη δυνατότητα να δημιουργείτε HTML υψηλής ποιότητας."
"linktitle": "Αποθήκευση εγγράφων HTML με"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Προηγμένες επιλογές αποθήκευσης εγγράφων HTML με το Aspose.Words Java"
"url": "/el/java/document-loading-and-saving/advance-html-documents-saving-options/"
"weight": 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Προηγμένες επιλογές αποθήκευσης εγγράφων HTML με το Aspose.Words Java


Σε αυτό το σεμινάριο, θα εξερευνήσουμε τις προηγμένες επιλογές αποθήκευσης εγγράφων HTML που παρέχονται από το Aspose.Words για Java. Το Aspose.Words είναι ένα ισχυρό API Java για εργασία με έγγραφα Word και προσφέρει ένα ευρύ φάσμα λειτουργιών για χειρισμό και μετατροπή εγγράφων.

## 1. Εισαγωγή
Το Aspose.Words για Java σάς επιτρέπει να εργάζεστε με έγγραφα του Word μέσω προγραμματισμού. Σε αυτό το σεμινάριο, θα επικεντρωθούμε σε προηγμένες επιλογές αποθήκευσης εγγράφων HTML, οι οποίες σας επιτρέπουν να ελέγχετε τον τρόπο με τον οποίο τα έγγραφα του Word μετατρέπονται σε HTML.

## 2. Εξαγωγή πληροφοριών μετ' επιστροφής
Ο `exportRoundtripInformation` Η μέθοδος σάς επιτρέπει να εξάγετε έγγραφα Word σε HTML διατηρώντας παράλληλα τις πληροφορίες roundtrip. Αυτές οι πληροφορίες μπορούν να είναι χρήσιμες όταν θέλετε να μετατρέψετε ξανά HTML σε μορφή Word χωρίς να χάσετε λεπτομέρειες που αφορούν συγκεκριμένα έγγραφα.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

## 3. Εξαγωγή γραμματοσειρών ως Base64
Με το `exportFontsAsBase64` Με τη μέθοδο, μπορείτε να εξαγάγετε γραμματοσειρές που χρησιμοποιούνται στο έγγραφο ως δεδομένα με κωδικοποίηση Base64 στην HTML. Αυτό διασφαλίζει ότι η αναπαράσταση HTML διατηρεί τα ίδια στυλ γραμματοσειράς με το αρχικό έγγραφο του Word.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

## 4. Εξαγωγικοί Πόροι
Ο `exportResources` Η μέθοδος σάς επιτρέπει να καθορίσετε τον τύπο του φύλλου στυλ CSS και να εξαγάγετε πόρους γραμματοσειράς. Μπορείτε επίσης να ορίσετε έναν φάκελο πόρων και ένα ψευδώνυμο για τους πόρους στην HTML.

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

## 5. Μετατροπή μετααρχείων σε EMF ή WMF
Ο `convertMetafilesToEmfOrWmf` Η μέθοδος σάς επιτρέπει να μετατρέψετε μετααρχεία στο έγγραφο σε μορφή EMF ή WMF, εξασφαλίζοντας συμβατότητα και ομαλή απόδοση σε HTML.

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

## 6. Μετατροπή μετααρχείων σε SVG
Χρησιμοποιήστε το `convertMetafilesToSvg` μέθοδος για τη μετατροπή μετααρχείων σε μορφή SVG. Αυτή η μορφή είναι ιδανική για την εμφάνιση διανυσματικών γραφικών σε έγγραφα HTML.

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

## 7. Προσθήκη προθέματος ονόματος κλάσης CSS
Με το `addCssClassNamePrefix` Με τη μέθοδο, μπορείτε να προσθέσετε ένα πρόθεμα στα ονόματα κλάσεων CSS στην εξαγόμενη HTML. Αυτό βοηθά στην αποφυγή διενέξεων με υπάρχοντα στυλ.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

## 8. Εξαγωγή URL CID για πόρους MHTML
Ο `exportCidUrlsForMhtmlResources` Η μέθοδος χρησιμοποιείται κατά την αποθήκευση εγγράφων σε μορφή MHTML. Επιτρέπει την εξαγωγή URL Content-ID για πόρους.

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
Ο `resolveFontNames` Η μέθοδος βοηθά στην ανάλυση των ονομάτων γραμματοσειρών κατά την αποθήκευση εγγράφων σε μορφή HTML, διασφαλίζοντας συνεπή απόδοση σε διαφορετικές πλατφόρμες.

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
Ο `exportTextInputFormFieldAsText` Η μέθοδος εξάγει τα πεδία φόρμας ως απλό κείμενο στην HTML, καθιστώντας τα εύκολα αναγνώσιμα και επεξεργάσιμα.

```java

public void exportTextInputFormFieldAsText() throws Exception {
    
	string dataDir = "Your Document Directory";
	Document doc = new Document(dataDir + "Rendering.docx");

	String imagesDir = Path.combine(dataDir, "Images");

	// Ο καθορισμένος φάκελος πρέπει να υπάρχει και να είναι κενός.
	if (Directory.exists(imagesDir))
		Directory.delete(imagesDir, true);

	Directory.createDirectory(imagesDir);

	// Ορίστε μια επιλογή για εξαγωγή πεδίων φόρμας ως απλό κείμενο και όχι ως στοιχεία εισόδου HTML.
	HtmlSaveOptions saveOptions = new HtmlSaveOptions(SaveFormat.HTML);
	{
		saveOptions.setExportTextInputFormFieldAsText(true); saveOptions.setImagesFolder(imagesDir);
	}

	doc.save(dataDir + "WorkingWithHtmlSaveOptions.ExportTextInputFormFieldAsText.html", saveOptions);
}
```

## Σύναψη
Σε αυτό το σεμινάριο, εξερευνήσαμε τις προηγμένες επιλογές αποθήκευσης εγγράφων HTML που παρέχονται από το Aspose.Words για Java. Αυτές οι επιλογές σάς δίνουν λεπτομερή έλεγχο της διαδικασίας μετατροπής, επιτρέποντάς σας να δημιουργείτε έγγραφα HTML που μοιάζουν πολύ με τα αρχικά έγγραφα του Word.

## Συχνές ερωτήσεις
Ακολουθούν ορισμένες συχνές ερωτήσεις σχετικά με την εργασία με το Aspose.Words για επιλογές αποθήκευσης εγγράφων Java και HTML:

### Ε1: Πώς μπορώ να μετατρέψω ξανά HTML σε μορφή Word χρησιμοποιώντας το Aspose.Words για Java;
Για να μετατρέψετε ξανά HTML σε μορφή Word, μπορείτε να χρησιμοποιήσετε τα API Aspose.Words `load` μέθοδος για να φορτώσετε το έγγραφο HTML και στη συνέχεια να το αποθηκεύσετε σε μορφή Word.

### Ε2: Μπορώ να προσαρμόσω τα στυλ CSS κατά την εξαγωγή σε HTML;
Ναι, μπορείτε να προσαρμόσετε τα στυλ CSS τροποποιώντας τα φύλλα στυλ που χρησιμοποιούνται στην HTML ή χρησιμοποιώντας το `addCssClassNamePrefix` Μέθοδος για την προσθήκη ενός προθέματος στα ονόματα κλάσεων CSS.

### Ε3: Υπάρχει τρόπος βελτιστοποίησης της εξόδου HTML για προβολή στο web;
Ναι, μπορείτε να βελτιστοποιήσετε την έξοδο HTML για προβολή ιστού διαμορφώνοντας επιλογές όπως η εξαγωγή γραμματοσειρών ως Base64 και η μετατροπή μετααρχείων σε SVG.

### Ε4: Υπάρχουν περιορισμοί κατά τη μετατροπή σύνθετων εγγράφων Word σε HTML;
Ενώ το Aspose.Words για Java παρέχει ισχυρές δυνατότητες μετατροπής, τα σύνθετα έγγραφα Word με περίπλοκες διατάξεις ενδέχεται να απαιτούν πρόσθετη επεξεργασία μετά την επεξεργασία για να επιτευχθεί το επιθυμητό αποτέλεσμα HTML.



{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}