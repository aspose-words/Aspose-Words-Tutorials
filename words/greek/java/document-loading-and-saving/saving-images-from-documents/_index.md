---
date: 2025-12-27
description: Μάθετε πώς να αποθηκεύετε μια σελίδα ως JPEG και να εξάγετε εικόνες από
  έγγραφα Word χρησιμοποιώντας το Aspose.Words for Java. Περιλαμβάνει συμβουλές για
  τη ρύθμιση της φωτεινότητας της εικόνας, της ανάλυσης και τη δημιουργία πολυσελίδων
  TIFF.
linktitle: Saving Images from Documents
second_title: Aspose.Words Java Document Processing API
title: Πώς να αποθηκεύσετε τη σελίδα ως JPEG και να εξάγετε εικόνες από έγγραφα με
  το Aspose.Words για Java
url: /el/java/document-loading-and-saving/saving-images-from-documents/
weight: 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση σελίδας ως JPEG και εξαγωγή εικόνων από έγγραφα στο Aspose.Words for Java

Σε αυτό το tutorial θα ανακαλύψετε πώς να **save page as jpeg** από ένα έγγραφο Word και πώς να **extract images from Word** αρχεία χρησιμοποιώντας το Aspose.Words for Java. Θα περάσουμε από πραγματικά σενάρια όπως η ρύθμιση της φωτεινότητας της εικόνας, η προσαρμογή της ανάλυσης της εικόνας σε Java, και η δημιουργία ενός πολυσελιδικού TIFF. Κάθε βήμα περιλαμβάνει έτοιμα κομμάτια κώδικα που μπορείτε να αντιγράψετε, να επικολλήσετε και να δείτε τα αποτελέσματα άμεσα.

## Γρήγορες Απαντήσεις
- **Μπορώ να αποθηκεύσω μια μόνο σελίδα ως JPEG;** Ναι – χρησιμοποιήστε `ImageSaveOptions` με `setPageSet(new PageSet(pageIndex))`.
- **Πώς αλλάζω τη φωτεινότητα της εικόνας;** Καλέστε `options.setImageBrightness(floatValue)` (εύρος 0‑1).
- **Τι κάνω αν χρειάζομαι ένα πολυσελιδικό TIFF;** Ορίστε ένα `PageSet` που καλύπτει τις επιθυμητές σελίδες και επιλέξτε μια μέθοδο συμπίεσης TIFF.
- **Πώς μπορώ να ελέγξω την ανάλυση της εικόνας;** Χρησιμοποιήστε `setResolution(floatDpi)` ή `setHorizontalResolution(floatDpi)`.
- **Χρειάζομαι άδεια για παραγωγή;** Απαιτείται έγκυρη άδεια Aspose.Words για μη‑δοκιμαστική χρήση.

## Τι είναι το “save page as jpeg”;
Η αποθήκευση μιας σελίδας ως JPEG σημαίνει τη μετατροπή μιας μόνο σελίδας ενός εγγράφου Word σε αρχείο raster εικόνας (JPEG). Αυτό είναι χρήσιμο για δημιουργία προεπισκόπησης, δημιουργία μικρογραφιών ή ενσωμάτωση σελίδων εγγράφου σε ιστοσελίδες όπου η απόδοση PDF δεν είναι πρακτική.

## Γιατί να εξάγετε εικόνες από έγγραφα Word;
Πολλές επιχειρησιακές ροές εργασίας απαιτούν την εξαγωγή των αρχικών γραφικών (λογότυπα, διαγράμματα, φωτογραφίες) από ένα αρχείο DOCX για επαναχρησιμοποίηση, αρχειοθέτηση ή ανάλυση. Το Aspose.Words καθιστά απλό το να εξάγετε κάθε εικόνα στη φυσική της μορφή χωρίς απώλεια ποιότητας.

## Προαπαιτούμενα
- Java Development Kit (JDK 8 ή νεότερο) εγκατεστημένο.
- Βιβλιοθήκη Aspose.Words for Java προστέθηκε στο έργο σας. Κατεβάστε την από [here](https://releases.aspose.com/words/java/).
- Ένα δείγμα εγγράφου Word (π.χ., `Rendering.docx`) τοποθετημένο σε γνωστό φάκελο.

## Βήμα 1: Αποθήκευση εικόνων ως TIFF με έλεγχο κατωφλίου (Δημιουργία πολυσελιδικού TIFF)
Για να δημιουργήσετε ένα υψηλής αντίθεσης, γκρι κλίμακας TIFF μπορείτε να ελέγξετε το κατώφλι δυαδικοποίησης. Αυτό είναι χρήσιμο όταν χρειάζεστε μια εκτυπώσιμη, ασπρόμαυρη έκδοση του εγγράφου σας.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Βήμα 2: Αποθήκευση συγκεκριμένης σελίδας ως πολυσελιδικό TIFF
Αν χρειάζεστε ένα TIFF που περιέχει μόνο ένα υποσύνολο σελίδων (π.χ., σελίδες 1‑2), διαμορφώστε ένα `PageSet`. Αυτό δείχνει **create multipage tiff**.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Βήμα 3: Αποθήκευση εικόνων ως 1 BPP Indexed PNG
Όταν χρειάζεστε εξαιρετικά ελαφριά ασπρόμαυρα PNG (1 bit ανά pixel), ορίστε την μορφή pixel αναλόγως. Αυτό είναι χρήσιμο για ενσωμάτωση απλών γραφικών σε σενάρια χαμηλού εύρους ζώνης.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Βήμα 4: Αποθήκευση σελίδας ως JPEG με προσαρμογή (Ορισμός φωτεινότητας εικόνας & ανάλυσης)
Εδώ **save page as jpeg** ενώ ρυθμίζουμε τη φωτεινότητα, την αντίθεση και την ανάλυση—ιδανικό για δημιουργία μικρογραφιών ή προεπισκοπήσεων έτοιμων για web.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);          // set image brightness (0‑1)
options.setImageContrast(0.7f);            // set image contrast (0‑1)
options.setHorizontalResolution(72f);      // set image resolution in DPI
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Βήμα 5: Χρήση Callback αποθήκευσης σελίδας (Προηγμένη προσαρμογή)
Ένα callback σας επιτρέπει να μετονομάζετε κάθε αρχείο εξόδου δυναμικά, κάτι που είναι χρήσιμο όταν εξάγετε πολλές σελίδες ταυτόχρονα.

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
doc.save("Your Directory Path" + "PageSavingCallback.png", imageSaveOptions);
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Πλήρης κώδικας πηγής για όλα τα σενάρια
Παρακάτω υπάρχει μια μοναδική κλάση που περιέχει κάθε μέθοδο που παρουσιάστηκε παραπάνω. Μπορείτε να εκτελέσετε κάθε δοκιμή ξεχωριστά.

```java
public void exposeThresholdControlForTiffBinarization() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setTiffCompression(TiffCompression.CCITT_3);
		saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
		saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
		saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.ExposeThresholdControlForTiffBinarization.tiff", saveOptions);
}
@Test
public void getTiffPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.MultipageTiff.tiff");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(new PageRange(0, 1))); saveOptions.setTiffCompression(TiffCompression.CCITT_4); saveOptions.setResolution(160f);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetTiffPageRange.tiff", saveOptions);
}
@Test
public void format1BppIndexed() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions saveOptions = new ImageSaveOptions();
	{
		saveOptions.setPageSet(new PageSet(1));
		saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
		saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.Format1BppIndexed.Png", saveOptions);
}
@Test
public void getJpegPageRange() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions options = new ImageSaveOptions();
	// Set the "PageSet" to "0" to convert only the first page of a document.
	options.setPageSet(new PageSet(0));
	// Change the image's brightness and contrast.
	// Both are on a 0-1 scale and are at 0.5 by default.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Change the horizontal resolution.
	// The default value for these properties is 96.0, for a resolution of 96dpi.
	options.setHorizontalResolution(72f);
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.GetJpegPageRange.jpeg", options);
}
@Test
public static void pageSavingCallback() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Rendering.docx");
	ImageSaveOptions imageSaveOptions = new ImageSaveOptions();
	{
		imageSaveOptions.setPageSet(new PageSet(new PageRange(0, doc.getPageCount() - 1)));
		imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
	}
	doc.save("Your Directory Path" + "WorkingWithImageSaveOptions.PageSavingCallback.png", imageSaveOptions);
}
private static class HandlePageSavingCallback implements IPageSavingCallback
{
	public void pageSaving(PageSavingArgs args)
	{
		args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
	}
```

## Συνηθισμένα προβλήματα και λύσεις
- **“Unable to locate the document file”** – Επαληθεύστε ότι η διαδρομή αρχείου χρησιμοποιεί το σωστό διαχωριστικό (`/` ή `\\`) για το λειτουργικό σας σύστημα.
- **Images appear blank** – Βεβαιωθείτε ότι έχετε ορίσει ένα κατάλληλο `ImageColorMode` (π.χ., `GRAYSCALE` για TIFF).
- **Out‑of‑memory errors on large documents** – Επεξεργαστείτε τις σελίδες σε παρτίδες ρυθμίζοντας το εύρος του `PageSet`.
- **JPEG quality looks poor** – Αυξήστε την ανάλυση με `setHorizontalResolution` ή `setResolution`.

## Συχνές Ερωτήσεις

**Q: Πώς αλλάζω τη μορφή εικόνας κατά την αποθήκευση με Aspose.Words for Java;**  
A: Ορίστε τη ζητούμενη μορφή στο `ImageSaveOptions`. Για PNG, μπορείτε απλώς να δημιουργήσετε ένα `ImageSaveOptions` και να ορίσετε `SaveFormat.PNG` αν χρειάζεται.

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

**Q: Μπορώ να προσαρμόσω τις ρυθμίσεις συμπίεσης για εικόνες TIFF;**  
A: Ναι. Χρησιμοποιήστε `setTiffCompression` για να επιλέξετε έναν αλγόριθμο συμπίεσης όπως `CCITT_3`.

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

**Q: Πώς μπορώ να αποθηκεύσω μια συγκεκριμένη σελίδα από ένα έγγραφο ως ξεχωριστή εικόνα;**  
A: Χρησιμοποιήστε τη μέθοδο `setPageSet` με έναν μοναδικό δείκτη σελίδας.

```java
saveOptions.setPageSet(new PageSet(0)); // Save the first page as an image
```

**Q: Πώς εφαρμόζω προσαρμοσμένες ρυθμίσεις σε εικόνες JPEG κατά την αποθήκευση;**  
A: Ρυθμίστε ιδιότητες όπως φωτεινότητα, αντίθεση και ανάλυση μέσω του `ImageSaveOptions`.

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

**Q: Πώς μπορώ να χρησιμοποιήσω ένα callback για προσαρμογή της αποθήκευσης εικόνας;**  
A: Υλοποιήστε το `IPageSavingCallback` και αναθέστε το με `setPageSavingCallback`.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```

## Συμπέρασμα
Τώρα έχετε ένα πλήρες σύνολο εργαλείων για **saving page as jpeg**, εξαγωγή εικόνων, έλεγχο φωτεινότητας εικόνας, ορισμό ανάλυσης εικόνας σε Java, και δημιουργία πολυσελιδικών αρχείων TIFF με το Aspose.Words for Java. Πειραματιστείτε με διαφορετικές ρυθμίσεις του `ImageSaveOptions` ώστε να ταιριάζουν στις ανάγκες του έργου σας, και εξερευνήστε το ευρύτερο API του Aspose.Words για ακόμη περισσότερες δυνατότητες διαχείρισης εγγράφων.

---

**Τελευταία ενημέρωση:** 2025-12-27  
**Δοκιμή με:** Aspose.Words for Java 24.12 (latest at time of writing)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}