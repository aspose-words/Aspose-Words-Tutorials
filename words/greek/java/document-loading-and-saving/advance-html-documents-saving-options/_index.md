---
date: 2025-12-19
description: Μάθετε πώς να εξάγετε HTML με το Aspose.Words Java, καλύπτοντας προχωρημένες
  επιλογές για αποθήκευση του Word ως HTML και αποδοτική μετατροπή του Word σε HTML.
linktitle: Saving HTML Documents with
second_title: Aspose.Words Java Document Processing API
title: 'Πώς να εξάγετε HTML με το Aspose.Words Java: Προηγμένες επιλογές'
url: /el/java/document-loading-and-saving/advance-html-documents-saving-options/
weight: 16
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να Εξάγετε HTML με το Aspose.Words Java: Προχωρημένες Επιλογές

Σε αυτό το tutorial θα ανακαλύψετε **πώς να εξάγετε HTML** από έγγραφα Word χρησιμοποιώντας το Aspose.Words for Java. Είτε χρειάζεστε **να αποθηκεύσετε το Word ως HTML** για δημοσίευση στο web είτε **να μετατρέψετε το Word σε HTML** για επεξεργασία downstream, οι προχωρημένες επιλογές αποθήκευσης σας δίνουν λεπτομερή έλεγχο του αποτελέσματος. Θα περάσουμε από κάθε επιλογή βήμα‑βήμα, θα εξηγήσουμε πότε να τη χρησιμοποιήσετε και θα δείξουμε πραγματικά σενάρια όπου αυτές οι ρυθμίσεις κάνουν τη διαφορά.

## Γρήγορες Απαντήσεις
- **Ποια είναι η κύρια κλάση για εξαγωγή HTML;** `HtmlSaveOptions`  
- **Μπορούν οι γραμματοσειρές να ενσωματωθούν απευθείας στο HTML;** Ναι, ορίστε `exportFontsAsBase64` σε `true`.  
- **Πώς μπορώ να διατηρήσω τα Word‑συγκεκριμένα δεδομένα round‑trip;** Ενεργοποιήστε `exportRoundtripInformation`.  
- **Ποια μορφή είναι η καλύτερη για διανυσματικά γραφικά;** Χρησιμοποιστε `convertMetafilesToSvg` για έξοδο SVG.  
- **Μπορεί να αποφευχθεί η σύγκρουση ονομάτων κλάσεων CSS;** Ναι, χρησιμοποιήστε `addCssClassNamePrefix`.

## 1. Εισαγωγή
Το Aspose.Words for Java είναι ένα ισχυρό API που επιτρέπει στους προγραμματιστές να χειρίζονται έγγραφα Word προγραμματιστικά. Αυτός ο οδηγός εστιάζει στις προχωρημένες επιλογές αποθήκευσης εγγράφου HTML που σας επιτρέπουν να προσαρμόσετε τη διαδικασία μετατροπής ώστε να καλύπτει συγκεκριμένες απαιτήσεις web ή ενσωμάτωσης.

## 2. Export Roundtrip Information
Η διατήρηση των πληροφοριών round‑trip σας επιτρέπει να μετατρέψετε το HTML πίσω σε έγγραφο Word χωρίς να χάσετε λεπτομέρειες διάταξης ή μορφοποίησης.

```java
public void exportRoundtripInformation() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportRoundtripInformation(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportRoundtripInformation.html", saveOptions);
}
```

### Πότε να το χρησιμοποιήσετε
- Όταν χρειάζεστε μια αντιστρέψιμη διαδικασία μετατροπής (HTML → Word → HTML).  
- Ιδανικό για σενάρια συνεργατικής επεξεργασίας όπου πρέπει να διατηρηθεί η αρχική δομή του Word.

## 3. Export Fonts as Base64
Η ενσωμάτωση γραμματοσειρών απευθείας στο HTML εξαλείφει τις εξωτερικές εξαρτήσεις γραμματοσειρών και εξασφαλίζει οπτική πιστότητα σε όλα τα προγράμματα περιήγησης.

```java

public void exportFontsAsBase64() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setExportFontsAsBase64(true);
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.ExportFontsAsBase64.html", saveOptions);
}
```

### Pro tip
Χρησιμοποιήστε αυτήν την επιλογή όταν το περιβάλλον προορισμού έχει περιορισμένη πρόσβαση σε εξωτερικούς πόρους (π.χ. ενημερωτικά δελτία email).

## 4. Export Resources
Ελέγξτε πώς εκδίδονται οι πόροι CSS και γραμματοσειρών, και ορίστε προσαρμοσμένο φάκελο ή ψευδώνυμο URL για αυτά τα στοιχεία.

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

### Γιατί έχει σημασία
Ο διαχωρισμός του CSS σε εξωτερικό αρχείο μειώνει το μέγεθος του HTML και επιτρέπει την προσωρινή αποθήκευση (caching) για ταχύτερη φόρτωση σελίδων.

## 5. Convert Metafiles to EMF or WMF
Τα metafiles (π.χ. EMF/WMF) μετατρέπονται σε μορφή που οι browsers μπορούν να αποδώσουν αξιόπιστα.

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

### Περίπτωση χρήσης
Επιλέξτε EMF/WMF όταν οι στόχοι browsers υποστηρίζουν αυτές τις διανυσματικές μορφές και χρειάζεστε κλιμάκωση χωρίς απώλειες.

## 6. Convert Metafiles to SVG
Το SVG προσφέρει την καλύτερη κλιμακωσιμότητα και υποστηρίζεται ευρέως από σύγχρονα προγράμματα περιήγησης.

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

### Όφελος
Τα αρχεία SVG είναι ελαφριά και διατηρούν την ανάλυση του εγγράφου ανεξάρτητα από το μέγεθος, ιδανικά για responsive web design.

## 7. Add CSS Class Name Prefix
Αποτρέψτε συγκρούσεις στυλ προσθέτοντας πρόθεμα σε όλα τα παραγόμενα ονόματα κλάσεων CSS.

```java

public void addCssClassNamePrefix() throws Exception {
    Document doc = new Document("Your Directory Path" + "Rendering.docx");
    HtmlSaveOptions saveOptions = new HtmlSaveOptions();
    saveOptions.setCssStyleSheetType(CssStyleSheetType.EXTERNAL);
    saveOptions.setCssClassNamePrefix("pfx_");
    doc.save("Your Directory Path" + "WorkingWithHtmlSaveOptions.AddCssClassNamePrefix.html", saveOptions);
}
```

### Πρακτική συμβουλή
Χρησιμοποιήστε μοναδικό πρόθεμα (π.χ. το όνομα του έργου σας) όταν ενσωματώνετε το HTML σε υπάρχουσες σελίδες για να αποφύγετε συγκρούσεις CSS.

## 8. Export CID URLs for MHTML Resources
Κατά την αποθήκευση ως MHTML, μπορείτε να εξάγετε πόρους χρησιμοποιώντας URLs τύπου Content‑ID για καλύτερη συμβατότητα email.

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

### Πότε να το χρησιμοποιήσετε
Ιδανικό για δημιουργία ενός ενιαίου, αυτόνομου αρχείου HTML που μπορεί να επισυναφθεί σε email.

## 9. Resolve Font Names
Εξασφαλίζει ότι το HTML αναφέρεται στις σωστές οικογένειες γραμματοσειρών, βελτιώνοντας τη συνέπεια μεταξύ πλατφορμών.

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

### Γιατί βοηθά
Εάν το αρχικό έγγραφο χρησιμοποιεί γραμματοσειρές που δεν είναι εγκατεστημένες στον υπολογιστή του χρήστη, αυτή η επιλογή τις αντικαθιστά με εναλλακτικές web‑safe.

## 10. Export Text Input Form Field as Text
Αποδίδει τα πεδία φόρμας ως απλό κείμενο αντί για διαδραστικά στοιχεία HTML input.

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

### Περίπτωση χρήσης
Όταν χρειάζεστε μια μόνο‑ανάγνωση αναπαράσταση μιας φόρμας για αρχειοθέτηση ή εκτύπωση.

## Συνηθισμένα Πιθανά Σφάλματα & Επίλυση Προβλημάτων
| Πρόβλημα | Τυπική Αιτία | Διόρθωση |
|----------|--------------|----------|
| Απουσία γραμματοσειρών στην έξοδο | `exportFontsAsBase64` δεν είναι ενεργοποιημένο | Ορίστε `setExportFontsAsBase64(true)` |
| Κατεστραμμένο CSS μετά την ενσωμάτωση | Χρήση `EXTERNAL` χωρίς παροχή του αρχείου CSS | Βεβαιωθείτε ότι το αρχείο CSS είναι αναπτυχθεί στο καθορισμένο `resourceFolderAlias` |
| Μεγάλο μέγεθος HTML | Ενσωμάτωση πολλών εικόνων ως Base64 | Μετάβαση σε εξωτερικούς πόρους εικόνας μέσω `setExportFontResources(true)` και ρύθμιση του `resourceFolder` |
| Το SVG δεν εμφανίζεται σε παλαιότερους browsers | Ο browser δεν υποστηρίζει SVG | Παρέχετε εναλλακτικό PNG εξάγοντας επίσης ως EMF/WMF |

## Συχνές Ερωτήσεις

**Μ: Μπορώ να ενσωματώσω γραμματοσειρές ως Base64 και να διατηρήσω εξωτερικό CSS;**  
Α: Ναι. Ορίστε `exportFontsAsBase64(true)` ενώ διατηρείτε `CssStyleSheetType.EXTERNAL` για να διαχωρίσετε τα δεδομένα γραμματοσειρών από τους κανόνες στυλ.

**Μ: Πώς μπορώ να μετατρέψω ένα υπάρχον HTML πίσω σε έγγραφο Word;**  
Α: Φορτώστε το HTML με `Document doc = new Document("input.html");` και στη συνέχεια `doc.save("output.docx");`. Διατηρήστε τα round‑trip δεδομένα χρησιμοποιώντας `exportRoundtripInformation` κατά την αρχική εξαγωγή.

**Μ: Υπάρχει επίπτωση στην απόδοση όταν χρησιμοποιείται η μετατροπή σε SVG;**  
Α: Η μετατροπή μεγάλων metafiles σε SVG μπορεί να αυξήσει τον χρόνο επεξεργασίας, αλλά το παραγόμενο HTML είναι συνήθως μικρότερο και αποδίδει ταχύτερα στα προγράμματα περιήγησης.

**Μ: Λειτουργούν αυτές οι επιλογές και με το Aspose.Words για .NET;**  
Α: Οι ίδιες έννοιες υπάρχουν και στο .NET API, αν και τα ονόματα μεθόδων μπορεί να διαφέρουν ελαφρώς (π.χ. το `HtmlSaveOptions` είναι κοινό και στις δύο πλατφόρμες).

**Μ: Ποια επιλογή πρέπει να επιλέξω για HTML φιλικό σε email;**  
Α: Χρησιμοποιήστε `SaveFormat.MHTML` με `exportCidUrlsForMhtmlResources` για να ενσωματώσετε όλους τους πόρους απευθείας στο σώμα του email.

**Τελευταία ενημέρωση:** 2025-12-19  
**Δοκιμάστηκε με:** Aspose.Words for Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}