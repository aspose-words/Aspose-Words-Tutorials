---
title: Χρήση επιλογών φόρτωσης στο Aspose.Words για Java
linktitle: Χρήση επιλογών φόρτωσης
second_title: Aspose.Words Java Document Processing API
description: Mastering Load Options στο Aspose.Words για Java. Προσαρμόστε τη φόρτωση εγγράφων, χειριστείτε την κρυπτογράφηση, μετατρέψτε σχήματα, ορίστε εκδόσεις Word και πολλά άλλα για αποτελεσματική επεξεργασία εγγράφων Java.
weight: 11
url: /el/java/document-loading-and-saving/using-load-options/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση επιλογών φόρτωσης στο Aspose.Words για Java


## Εισαγωγή στην εργασία με επιλογές φορτίου στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε τον τρόπο εργασίας με τις Επιλογές Φόρτωσης στο Aspose.Words για Java. Οι Επιλογές Φόρτωσης σάς επιτρέπουν να προσαρμόσετε τον τρόπο φόρτωσης και επεξεργασίας των εγγράφων. Θα καλύψουμε διάφορα σενάρια, όπως ενημέρωση βρώμικων πεδίων, φόρτωση κρυπτογραφημένων εγγράφων, μετατροπή σχημάτων σε Office Math, ρύθμιση έκδοσης MS Word, καθορισμός προσωρινού φακέλου, χειρισμός προειδοποιήσεων και μετατροπή μετα-αρχείων σε PNG. Ας βουτήξουμε βήμα βήμα.

## Ενημερώστε τα Dirty Fields

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

 Αυτό το απόσπασμα κώδικα δείχνει πώς να ενημερώσετε τα βρώμικα πεδία σε ένα έγγραφο. Ο`setUpdateDirtyFields(true)` Η μέθοδος χρησιμοποιείται για να διασφαλιστεί ότι τα βρώμικα πεδία ενημερώνονται κατά τη φόρτωση του εγγράφου.

## Φόρτωση κρυπτογραφημένου εγγράφου

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

 Εδώ, φορτώνουμε ένα κρυπτογραφημένο έγγραφο χρησιμοποιώντας έναν κωδικό πρόσβασης. Ο`LoadOptions` Ο κατασκευαστής αποδέχεται τον κωδικό πρόσβασης του εγγράφου και μπορείτε επίσης να καθορίσετε έναν νέο κωδικό πρόσβασης κατά την αποθήκευση του εγγράφου χρησιμοποιώντας`OdtSaveOptions`.

## Μετατροπή σχήματος σε μαθηματικά γραφείου

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

 Αυτός ο κώδικας δείχνει πώς να μετατρέψετε σχήματα σε αντικείμενα Office Math κατά τη φόρτωση του εγγράφου. Ο`setConvertShapeToOfficeMath(true)`μέθοδος επιτρέπει αυτή τη μετατροπή.

## Ορισμός έκδοσης MS Word

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

 Μπορείτε να καθορίσετε την έκδοση του MS Word για φόρτωση εγγράφων. Σε αυτό το παράδειγμα, ορίσαμε την έκδοση στο Microsoft Word 2010 χρησιμοποιώντας`setMswVersion`.

## Χρησιμοποιήστε τον Προσωρινό φάκελο

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

 Ρυθμίζοντας τον προσωρινό φάκελο χρησιμοποιώντας`setTempFolder`, μπορείτε να ελέγξετε πού αποθηκεύονται τα προσωρινά αρχεία κατά την επεξεργασία εγγράφων.

## Προειδοποίηση επανάκλησης

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Χειριστείτε τις προειδοποιήσεις καθώς προκύπτουν κατά τη φόρτωση του εγγράφου.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Αυτός ο κωδικός δείχνει πώς να ρυθμίσετε μια προειδοποιητική επιστροφή κλήσης για τη διαχείριση των προειδοποιήσεων κατά τη φόρτωση του εγγράφου. Μπορείτε να προσαρμόσετε τη συμπεριφορά της εφαρμογής σας όταν εμφανίζονται προειδοποιήσεις.

## Μετατροπή Metafiles σε PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

 Για να μετατρέψετε μετα-αρχεία (π.χ. WMF) σε εικόνες PNG κατά τη φόρτωση εγγράφων, μπορείτε να χρησιμοποιήσετε το`setConvertMetafilesToPng(true)` μέθοδος.

## Ολοκληρωμένος πηγαίος κώδικας για εργασία με επιλογές φόρτωσης στο Aspose.Words για Java

```java
public void updateDirtyFields() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setUpdateDirtyFields(true);
	}
	Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
}
@Test
public void loadEncryptedDocument() throws Exception {
	Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
@Test
public void convertShapeToOfficeMath() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertShapeToOfficeMath(true);
	}
	Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
}
@Test
public void setMsWordVersion() throws Exception {
	// Δημιουργήστε ένα νέο αντικείμενο LoadOptions, το οποίο θα φορτώνει έγγραφα σύμφωνα με τις προδιαγραφές του MS Word 2019 από προεπιλογή
	// και αλλάξτε την έκδοση φόρτωσης σε Microsoft Word 2010.
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setMswVersion(MsWordVersion.WORD_2010);
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
	doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
@Test
public void useTempFolder() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setTempFolder("Your Directory Path");
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
@Test
public void warningCallback() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());
	}
	Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
public static class DocumentLoadingWarningCallback implements IWarningCallback {
	public void warning(WarningInfo info) {
		//Εκτυπώνει τις προειδοποιήσεις και τα στοιχεία τους όπως προκύπτουν κατά τη φόρτωση του εγγράφου.
		System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
		System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
	}
}
@Test
public void convertMetafilesToPng() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setConvertMetafilesToPng(true);
	}
	Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
@Test
public void loadChm() throws Exception {
	LoadOptions loadOptions = new LoadOptions();
	{
		loadOptions.setEncoding(Charset.forName("windows-1251"));
	}
	Document doc = new Document("Your Directory Path" + "HTML help.chm", loadOptions);
}
```

## Σύναψη

Σε αυτό το σεμινάριο, έχουμε εμβαθύνει σε διάφορες πτυχές της εργασίας με τις Επιλογές Φόρτωσης στο Aspose.Words για Java. Οι επιλογές φόρτωσης διαδραματίζουν κρίσιμο ρόλο στην προσαρμογή του τρόπου φόρτωσης και επεξεργασίας των εγγράφων, επιτρέποντάς σας να προσαρμόσετε την επεξεργασία των εγγράφων σας στις συγκεκριμένες ανάγκες σας. Ας ανακεφαλαιώσουμε τα βασικά σημεία που καλύπτονται σε αυτόν τον οδηγό:

## Συχνές ερωτήσεις

### Πώς μπορώ να χειριστώ τις προειδοποιήσεις κατά τη φόρτωση του εγγράφου;

 Μπορείτε να ρυθμίσετε μια προειδοποιητική επανάκληση όπως φαίνεται στο`warningCallback()` παραπάνω μέθοδο. Προσαρμόστε το`DocumentLoadingWarningCallback` τάξη για να χειριστεί τις προειδοποιήσεις σύμφωνα με τις απαιτήσεις της αίτησής σας.

### Μπορώ να μετατρέψω σχήματα σε αντικείμενα Office Math κατά τη φόρτωση ενός εγγράφου;

 Ναι, μπορείτε να μετατρέψετε σχήματα σε αντικείμενα Office Math χρησιμοποιώντας`loadOptions.setConvertShapeToOfficeMath(true)`.

### Πώς μπορώ να καθορίσω την έκδοση του MS Word για φόρτωση εγγράφων;

 Χρήση`loadOptions.setMswVersion(MsWordVersion.WORD_2010)` για να καθορίσετε την έκδοση του MS Word για φόρτωση εγγράφων.

###  Ποιος είναι ο σκοπός του`setTempFolder` method in Load Options?

 Ο`setTempFolder`Η μέθοδος σάς επιτρέπει να καθορίσετε το φάκελο όπου αποθηκεύονται τα προσωρινά αρχεία κατά την επεξεργασία των εγγράφων.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
