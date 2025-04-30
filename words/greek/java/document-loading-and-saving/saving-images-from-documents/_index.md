---
"description": "Μάθετε πώς να αποθηκεύετε εικόνες από έγγραφα χρησιμοποιώντας το Aspose.Words για Java με τον ολοκληρωμένο οδηγό μας βήμα προς βήμα. Προσαρμόστε τις μορφές, τη συμπίεση και πολλά άλλα."
"linktitle": "Αποθήκευση εικόνων από έγγραφα"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Αποθήκευση εικόνων από έγγραφα στο Aspose.Words για Java"
"url": "/el/java/document-loading-and-saving/saving-images-from-documents/"
"weight": 17
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εικόνων από έγγραφα στο Aspose.Words για Java


## Εισαγωγή στην αποθήκευση εικόνων από έγγραφα στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να αποθηκεύουμε εικόνες από έγγραφα χρησιμοποιώντας το Aspose.Words για Java. Θα καλύψουμε διάφορα σενάρια και επιλογές προσαρμογής για την αποθήκευση εικόνων. Αυτός ο οδηγός παρέχει οδηγίες βήμα προς βήμα με παραδείγματα πηγαίου κώδικα.

## Προαπαιτούμενα

Πριν ξεκινήσετε, βεβαιωθείτε ότι έχετε ενσωματώσει στο έργο σας τη βιβλιοθήκη Aspose.Words για Java. Μπορείτε να την κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).

## Βήμα 1: Αποθήκευση εικόνων ως TIFF με έλεγχο κατωφλίου

Για να αποθηκεύσετε εικόνες σε μορφή TIFF με έλεγχο ορίου, ακολουθήστε τα εξής βήματα:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
saveOptions.setImageColorMode(ImageColorMode.GRAYSCALE);
saveOptions.setTiffBinarizationMethod(ImageBinarizationMethod.FLOYD_STEINBERG_DITHERING);
saveOptions.setThresholdForFloydSteinbergDithering((byte) 254);
doc.save("Your Directory Path" + "ThresholdControlledImage.tiff", saveOptions);
```

## Βήμα 2: Αποθήκευση συγκεκριμένης σελίδας ως αρχείο TIFF πολλαπλών σελίδων

Για να αποθηκεύσετε μια συγκεκριμένη σελίδα ως αρχείο TIFF πολλαπλών σελίδων, χρησιμοποιήστε τον ακόλουθο κώδικα:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(new PageRange(0, 1)));
saveOptions.setTiffCompression(TiffCompression.CCITT_4);
saveOptions.setResolution(160f);
doc.save("Your Directory Path" + "SpecificPageMultipage.tiff", saveOptions);
```

## Βήμα 3: Αποθήκευση εικόνων ως PNG με ευρετήριο 1 BPP

Για να αποθηκεύσετε εικόνες ως PNG με ευρετήριο 1 BPP, ακολουθήστε τα εξής βήματα:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions saveOptions = new ImageSaveOptions();
saveOptions.setPageSet(new PageSet(1));
saveOptions.setImageColorMode(ImageColorMode.BLACK_AND_WHITE);
saveOptions.setPixelFormat(ImagePixelFormat.FORMAT_1_BPP_INDEXED);
doc.save("Your Directory Path" + "1BPPIndexed.png", saveOptions);
```

## Βήμα 4: Αποθήκευση σελίδας ως JPEG με προσαρμογή

Για να αποθηκεύσετε μια συγκεκριμένη σελίδα ως JPEG με επιλογές προσαρμογής, χρησιμοποιήστε αυτόν τον κώδικα:

```java
Document doc = new Document("Your Directory Path" + "Rendering.docx");
ImageSaveOptions options = new ImageSaveOptions();
options.setPageSet(new PageSet(0));
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
options.setHorizontalResolution(72f);
doc.save("Your Directory Path" + "CustomizedJPEG.jpeg", options);
```

## Βήμα 5: Χρήση της Επανάκλησης Αποθήκευσης Σελίδας

Μπορείτε να χρησιμοποιήσετε μια επανάκληση για να προσαρμόσετε την αποθήκευση σελίδας. Ακολουθεί ένα παράδειγμα:

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

## Πλήρης πηγαίος κώδικας για την αποθήκευση εικόνων από έγγραφα στο Aspose.Words για Java

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
	// Ορίστε το "PageSet" σε "0" για να μετατρέψετε μόνο την πρώτη σελίδα ενός εγγράφου.
	options.setPageSet(new PageSet(0));
	// Αλλάξτε τη φωτεινότητα και την αντίθεση της εικόνας.
	// Και τα δύο βρίσκονται σε κλίμακα 0-1 και από προεπιλογή στο 0,5.
	options.setImageBrightness(0.3f);
	options.setImageContrast(0.7f);
	// Αλλάξτε την οριζόντια ανάλυση.
	// Η προεπιλεγμένη τιμή για αυτές τις ιδιότητες είναι 96,0, για ανάλυση 96dpi.
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

## Σύναψη

Μάθατε πώς να αποθηκεύετε εικόνες από έγγραφα χρησιμοποιώντας το Aspose.Words για Java. Αυτά τα παραδείγματα παρουσιάζουν διάφορες επιλογές προσαρμογής για την αποθήκευση εικόνων, όπως η μορφή, η συμπίεση και η χρήση επανάκλησης. Εξερευνήστε περισσότερες δυνατότητες με το Aspose.Words για τις ισχυρές δυνατότητες της Java.

## Συχνές ερωτήσεις

### Πώς μπορώ να αλλάξω τη μορφή εικόνας κατά την αποθήκευση με το Aspose.Words για Java;

Μπορείτε να αλλάξετε τη μορφή εικόνας καθορίζοντας την επιθυμητή μορφή στο `ImageSaveOptions`Για παράδειγμα, για να αποθηκεύσετε ως PNG, χρησιμοποιήστε `SaveFormat.PNG` όπως φαίνεται στον κώδικα:

```java
ImageSaveOptions saveOptions = new ImageSaveOptions();
```

### Μπορώ να προσαρμόσω τις ρυθμίσεις συμπίεσης για εικόνες TIFF;

Ναι, μπορείτε να προσαρμόσετε τις ρυθμίσεις συμπίεσης εικόνας TIFF. Για παράδειγμα, για να ορίσετε τη μέθοδο συμπίεσης σε CCITT_3, χρησιμοποιήστε τον ακόλουθο κώδικα:

```java
saveOptions.setTiffCompression(TiffCompression.CCITT_3);
```

### Πώς μπορώ να αποθηκεύσω μια συγκεκριμένη σελίδα από ένα έγγραφο ως ξεχωριστή εικόνα;

Για να αποθηκεύσετε μια συγκεκριμένη σελίδα ως εικόνα, χρησιμοποιήστε το `setPageSet` μέθοδος σε `ImageSaveOptions`Για παράδειγμα, για να αποθηκεύσετε μόνο την πρώτη σελίδα, ορίστε το `PageSet` να `new PageSet(0)`.

```java
saveOptions.setPageSet(new PageSet(0)); // Αποθήκευση της πρώτης σελίδας ως εικόνα
```

### Πώς μπορώ να εφαρμόσω προσαρμοσμένες ρυθμίσεις σε εικόνες JPEG κατά την αποθήκευση;

Μπορείτε να εφαρμόσετε προσαρμοσμένες ρυθμίσεις σε εικόνες JPEG χρησιμοποιώντας `ImageSaveOptions`Προσαρμόστε ιδιότητες όπως η φωτεινότητα, η αντίθεση και η ανάλυση. Για παράδειγμα, για να αλλάξετε τη φωτεινότητα σε 0,3 και την αντίθεση σε 0,7, χρησιμοποιήστε αυτόν τον κώδικα:

```java
options.setImageBrightness(0.3f);
options.setImageContrast(0.7f);
```

### Πώς μπορώ να χρησιμοποιήσω μια επανάκληση για την προσαρμογή της αποθήκευσης εικόνων;

Για να χρησιμοποιήσετε μια επανάκληση για την προσαρμογή της αποθήκευσης εικόνας, ορίστε το `PageSavσεgCallback` in `ImageSaveOptions`Δημιουργήστε μια κλάση που υλοποιεί το `IPageSavingCallback` διεπαφή και να παρακάμψετε το `pageSaving` μέθοδος.

```java
imageSaveOptions.setPageSavingCallback(new HandlePageSavingCallback());
```

Στη συνέχεια, δημιουργήστε μια κλάση που υλοποιεί το `IPageSavingCallback` διεπαφή και προσαρμόστε το όνομα και τη θέση του αρχείου στο `pageSaving` μέθοδος.

```java
private static class HandlePageSavingCallback implements IPageSavingCallback {
    public void pageSaving(PageSavingArgs args) {
        args.setPageFileName(MessageFormat.format("Your Directory Path" + "Page_{0}.png", args.getPageIndex()));
    }
}
```


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}