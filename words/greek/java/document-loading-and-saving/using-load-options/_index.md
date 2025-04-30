---
"description": "Εξοικείωση με τις επιλογές φόρτωσης στο Aspose.Words για Java. Προσαρμόστε τη φόρτωση εγγράφων, χειριστείτε την κρυπτογράφηση, μετατρέψτε σχήματα, ορίστε εκδόσεις του Word και πολλά άλλα για αποτελεσματική επεξεργασία εγγράφων Java."
"linktitle": "Χρήση επιλογών φόρτωσης"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Χρήση επιλογών φόρτωσης στο Aspose.Words για Java"
"url": "/el/java/document-loading-and-saving/using-load-options/"
"weight": 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Χρήση επιλογών φόρτωσης στο Aspose.Words για Java


## Εισαγωγή στην εργασία με επιλογές φόρτωσης στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε τον τρόπο εργασίας με τις Επιλογές Φόρτωσης στο Aspose.Words για Java. Οι Επιλογές Φόρτωσης σάς επιτρέπουν να προσαρμόσετε τον τρόπο φόρτωσης και επεξεργασίας των εγγράφων. Θα καλύψουμε διάφορα σενάρια, όπως ενημέρωση μη επεξεργασμένων πεδίων, φόρτωση κρυπτογραφημένων εγγράφων, μετατροπή σχημάτων σε Office Math, ορισμό της έκδοσης MS Word, καθορισμό προσωρινού φακέλου, χειρισμό προειδοποιήσεων και μετατροπή μετααρχείων σε PNG. Ας εμβαθύνουμε βήμα προς βήμα.

## Ενημέρωση βρώμικων πεδίων

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

Αυτό το απόσπασμα κώδικα δείχνει πώς να ενημερώσετε τα μη απαραίτητα πεδία σε ένα έγγραφο. `setUpdateDirtyFields(true)` Η μέθοδος χρησιμοποιείται για να διασφαλιστεί ότι τα μη καθαρά πεδία ενημερώνονται κατά τη φόρτωση του εγγράφου.

## Φόρτωση κρυπτογραφημένου εγγράφου

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

Εδώ, φορτώνουμε ένα κρυπτογραφημένο έγγραφο χρησιμοποιώντας έναν κωδικό πρόσβασης. `LoadOptions` Ο κατασκευαστής αποδέχεται τον κωδικό πρόσβασης του εγγράφου και μπορείτε επίσης να καθορίσετε έναν νέο κωδικό πρόσβασης κατά την αποθήκευση του εγγράφου χρησιμοποιώντας `OdtSaveOptions`.

## Μετατροπή σχήματος σε Office Math

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

Αυτός ο κώδικας δείχνει πώς να μετατρέψετε σχήματα σε αντικείμενα του Office Math κατά τη φόρτωση εγγράφων. `setConvertShapeToOfficeMath(true)` Η μέθοδος επιτρέπει αυτήν τη μετατροπή.

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

Μπορείτε να καθορίσετε την έκδοση του MS Word για τη φόρτωση εγγράφων. Σε αυτό το παράδειγμα, ορίσαμε την έκδοση σε Microsoft Word 2010 χρησιμοποιώντας `setMswVersion`.

## Χρήση προσωρινού φακέλου

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

Ορίζοντας τον προσωρινό φάκελο χρησιμοποιώντας `setTempFolder`, μπορείτε να ελέγξετε πού αποθηκεύονται τα προσωρινά αρχεία κατά την επεξεργασία εγγράφων.

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
        // Χειριστείτε τις προειδοποιήσεις καθώς προκύπτουν κατά την φόρτωση εγγράφων.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

Αυτός ο κώδικας δείχνει πώς να ρυθμίσετε μια επανάκληση προειδοποίησης για τη διαχείριση προειδοποιήσεων κατά τη φόρτωση εγγράφων. Μπορείτε να προσαρμόσετε τη συμπεριφορά της εφαρμογής σας όταν εμφανίζονται προειδοποιήσεις.

## Μετατροπή μετααρχείων σε PNG

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

Για να μετατρέψετε μετααρχεία (π.χ., WMF) σε εικόνες PNG κατά τη φόρτωση του εγγράφου, μπορείτε να χρησιμοποιήσετε το `setConvertMetafilesToPng(true)` μέθοδος.

## Πλήρης πηγαίος κώδικας για εργασία με επιλογές φόρτωσης στο Aspose.Words για Java

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
	// Δημιουργήστε ένα νέο αντικείμενο LoadOptions, το οποίο θα φορτώνει έγγραφα σύμφωνα με την προεπιλογή του MS Word 2019.
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
		// Εκτυπώνει προειδοποιήσεις και τις λεπτομέρειές τους καθώς προκύπτουν κατά την φόρτωση του εγγράφου.
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

Σε αυτό το σεμινάριο, εμβαθύναμε σε διάφορες πτυχές της εργασίας με τις Επιλογές Φόρτωσης στο Aspose.Words για Java. Οι Επιλογές Φόρτωσης παίζουν κρίσιμο ρόλο στην προσαρμογή του τρόπου φόρτωσης και επεξεργασίας των εγγράφων, επιτρέποντάς σας να προσαρμόσετε την επεξεργασία των εγγράφων σας στις συγκεκριμένες ανάγκες σας. Ας ανακεφαλαιώσουμε τα βασικά σημεία που καλύπτονται σε αυτόν τον οδηγό:

## Συχνές ερωτήσεις

### Πώς μπορώ να χειριστώ τις προειδοποιήσεις κατά τη φόρτωση εγγράφων;

Μπορείτε να ρυθμίσετε μια προειδοποίηση επιστροφής κλήσης όπως φαίνεται στο `warningCallback()` την παραπάνω μέθοδο. Προσαρμόστε το `DocumentLoadingWarningCallback` κλάση για τη διαχείριση προειδοποιήσεων σύμφωνα με τις απαιτήσεις της εφαρμογής σας.

### Μπορώ να μετατρέψω σχήματα σε αντικείμενα του Office Math κατά τη φόρτωση ενός εγγράφου;

Ναι, μπορείτε να μετατρέψετε σχήματα σε αντικείμενα του Office Math χρησιμοποιώντας `loadOptions.setConvertShapeToOfficeMath(true)`.

### Πώς μπορώ να καθορίσω την έκδοση του MS Word για την φόρτωση εγγράφων;

Χρήση `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` για να καθορίσετε την έκδοση του MS Word για τη φόρτωση του εγγράφου.

### Ποιος είναι ο σκοπός του `setTempFolder` μέθοδος στις Επιλογές Φόρτωσης;

Ο `setTempFolder` Η μέθοδος σάς επιτρέπει να καθορίσετε τον φάκελο όπου αποθηκεύονται τα προσωρινά αρχεία κατά την επεξεργασία εγγράφων.


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}