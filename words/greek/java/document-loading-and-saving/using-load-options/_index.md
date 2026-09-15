---
date: 2025-12-27
description: Μάθετε πώς να ορίζετε το LoadOptions στο Aspose.Words for Java, συμπεριλαμβανομένου
  του πώς να καθορίζετε τον προσωρινό φάκελο, να ορίζετε την έκδοση του Word, να μετατρέπετε
  μετααρχεία σε PNG και να μετατρέπετε σχήματα σε μαθηματικά για ευέλικτη επεξεργασία
  εγγράφων.
linktitle: Using Load Options
second_title: Aspose.Words Java Document Processing API
title: Πώς να ορίσετε τις LoadOptions στο Aspose.Words για Java
url: /el/java/document-loading-and-saving/using-load-options/
weight: 11
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να ορίσετε το LoadOptions στο Aspose.Words for Java

Σε αυτό το tutorial θα περάσουμε βήμα‑βήμα **πώς να ορίσετε το LoadOptions** για μια ποικιλία πραγματικών σεναρίων κατά τη χρήση του Aspose.Words for Java. Τα LoadOptions σας δίνουν λεπτομερή έλεγχο του τρόπου ανοίγματος ενός εγγράφου — είτε χρειάζεστε την ενημέρωση «dirty» πεδίων, εργασία με κρυπτογραφημένα αρχεία, μετατροπή σχημάτων σε Office Math, ή να υποδείξετε στη βιβλιοθήκη πού να αποθηκεύει προσωρινά δεδομένα. Στο τέλος θα μπορείτε να προσαρμόζετε τη συμπεριφορά φόρτωσης ώστε να ταιριάζει ακριβώς στις απαιτήσεις της εφαρμογής σας.

## Γρήγορες Απαντήσεις
- **Τι είναι το LoadOptions;** Ένα αντικείμενο ρυθμίσεων που επηρεάζει το πώς το Aspose.Words φορτώνει ένα έγγραφο.  
- **Μπορώ να ενημερώσω πεδία κατά τη φόρτωση;** Ναι — ορίστε `setUpdateDirtyFields(true)`.  
- **Πώς ανοίγω αρχείο με κωδικό πρόσβασης;** Περάστε τον κωδικό στον κατασκευαστή του `LoadOptions`.  
- **Μπορεί να αλλάξει ο προσωρινός φάκελος;** Χρησιμοποιήστε `setTempFolder("path")`.  
- **Ποια μέθοδος μετατρέπει σχήματα σε Office Math;** `setConvertShapeToOfficeMath(true)`.

## Γιατί να Χρησιμοποιήσετε LoadOptions;
Τα LoadOptions σας επιτρέπουν να αποφύγετε βήματα επεξεργασίας μετά τη φόρτωση, να μειώσετε τη χρήση μνήμης και να διασφαλίσετε ότι το έγγραφο ερμηνεύεται ακριβώς όπως χρειάζεστε. Για παράδειγμα, η μετατροπή μετααρχείων σε PNG κατά τη φόρτωση αποτρέπει προβλήματα ραστεροποίησης αργότερα, και ο καθορισμός της έκδοσης του MS Word βοηθά στη διατήρηση της ακεραιότητας της διάταξης όταν δουλεύετε με παλιά αρχεία.

## Προαπαιτούμενα
- Java 17 ή νεότερη  
- Aspose.Words for Java (τελευταία έκδοση)  
- Έγκυρη άδεια Aspose για παραγωγική χρήση  

## Οδηγός Βήμα‑Βήμα

### Ενημέρωση Dirty Fields

Όταν ένα έγγραφο περιέχει πεδία που έχουν τροποποιηθεί αλλά δεν έχουν ανανεωθεί, μπορείτε να ζητήσετε από το Aspose.Words να τα ενημερώσει αυτόματα κατά τη φόρτωση.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setUpdateDirtyFields(true);

Document doc = new Document("Your Directory Path" + "Dirty field.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.UpdateDirtyFields.docx");
```

*Η κλήση `setUpdateDirtyFields(true)` διασφαλίζει ότι τυχόν dirty πεδία επανυπολογίζονται αμέσως μόλις ανοίξει το έγγραφο.*

### Φόρτωση Κρυπτογραφημένου Εγγράφου

Αν το πηγαίο αρχείο είναι προστατευμένο με κωδικό, δώστε τον κωδικό κατά τη δημιουργία της παρουσίας `LoadOptions`. Μπορείτε επίσης να ορίσετε νέο κωδικό κατά την αποθήκευση σε διαφορετική μορφή.

```java
@Test
public void loadEncryptedDocument() throws Exception {
    Document doc = new Document("Your Directory Path" + "Encrypted.docx", new LoadOptions("docPassword"));
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.LoadAndSaveEncryptedOdt.odt", new OdtSaveOptions("newPassword"));
}
```

### Μετατροπή Σχήματος σε Office Math

Ορισμένα παλιά έγγραφα αποθηκεύουν εξισώσεις ως σχήματα. Η ενεργοποίηση αυτής της επιλογής μετατρέπει τα σχήματα σε εγγενή αντικείμενα Office Math, που είναι πιο εύκολο να επεξεργαστούν αργότερα.

```java
LoadOptions loadOptions = new LoadOptions();
loadOptions.setConvertShapeToOfficeMath(true);

Document doc = new Document("Your Directory Path" + "Office math.docx", loadOptions);
doc.save("Your Directory Path" + "WorkingWithLoadOptions.ConvertShapeToOfficeMath.docx");
```

### Ορισμός Έκδοσης MS Word

Ο καθορισμός της στοχευόμενης έκδοσης του Word βοηθά τη βιβλιοθήκη να επιλέξει τους σωστούς κανόνες απόδοσης, ειδικά όταν εργάζεστε με παλαιότερες μορφές αρχείων.

```java
@Test
public void setMsWordVersion() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setMswVersion(MsWordVersion.WORD_2010);

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
    doc.save("Your Directory Path" + "WorkingWithLoadOptions.SetMsWordVersion.docx");
}
```

### Χρήση Προσωρινού Φακέλου

Μεγάλα έγγραφα μπορεί να δημιουργούν προσωρινά αρχεία (π.χ., κατά την εξαγωγή εικόνων). Μπορείτε να κατευθύνετε αυτά τα αρχεία σε φάκελο της επιλογής σας, κάτι χρήσιμο σε περιβάλλοντα sandbox.

```java
@Test
public void useTempFolder() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setTempFolder("Your Directory Path");

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}
```

### Callback Προειδοποίησης

Κατά τη φόρτωση, το Aspose.Words μπορεί να εκδώσει προειδοποιήσεις (π.χ., μη υποστηριζόμενα χαρακτηριστικά). Η υλοποίηση ενός callback σας επιτρέπει να καταγράψετε ή να αντιδράσετε σε αυτά τα γεγονότα.

```java
@Test
public void warningCallback() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setWarningCallback(new DocumentLoadingWarningCallback());

    Document doc = new Document("Your Directory Path" + "Document.docx", loadOptions);
}

public static class DocumentLoadingWarningCallback implements IWarningCallback {
    public void warning(WarningInfo info) {
        // Handle warnings as they arise during document loading.
        System.out.println(MessageFormat.format("WARNING: {0}, source: {1}", info.getWarningType(), info.getSource()));
        System.out.println(MessageFormat.format("\tDescription: {0}", info.getDescription()));
    }
}
```

### Μετατροπή Μετααρχείων σε PNG

Μετααρχεία όπως WMF μπορούν να ραστεροποιηθούν σε PNG κατά τη φόρτωση, εξασφαλίζοντας συνεπή απόδοση σε όλες τις πλατφόρμες.

```java
@Test
public void convertMetafilesToPng() throws Exception {
    LoadOptions loadOptions = new LoadOptions();
    loadOptions.setConvertMetafilesToPng(true);

    Document doc = new Document("Your Directory Path" + "WMF with image.docx", loadOptions);
}
```

## Πλήρης Πηγαίος Κώδικας για Εργασία με Load Options στο Aspose.Words for Java

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
	// Create a new LoadOptions object, which will load documents according to MS Word 2019 specification by default
	// and change the loading version to Microsoft Word 2010.
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
		// Prints warnings and their details as they arise during document loading.
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

## Συνηθισμένες Περιπτώσεις Χρήσης & Συμβουλές

- **Διαδικασίες μαζικής μετατροπής** – Συνδυάστε `setTempFolder` με προγραμματισμένη εργασία για επεξεργασία εκατοντάδων αρχείων χωρίς να γεμίσει ο φάκελος temp του συστήματος.  
- **Μεταφορά παλαιών εγγράφων** – Χρησιμοποιήστε `setMswVersion` μαζί με `setConvertShapeToOfficeMath` για να μεταφέρετε παλιά τεχνικά έγγραφα σε σύγχρονη μορφή διατηρώντας τις εξισώσεις.  
- **Ασφαλής διαχείριση εγγράφων** – Συνδυάστε `loadEncryptedDocument` με `OdtSaveOptions` για να επανακρυπτογραφήσετε αρχεία με νέο κωδικό σε διαφορετική μορφή.  

## Συχνές Ερωτήσεις

**Ε: Πώς μπορώ να διαχειριστώ προειδοποιήσεις κατά τη φόρτωση εγγράφου;**  
Α: Υλοποιήστε ένα προσαρμοσμένο `IWarningCallback` (όπως φαίνεται στο παράδειγμα *Warning Callback*) και καταχωρίστε το μέσω `loadOptions.setWarningCallback(...)`. Αυτό σας επιτρέπει να καταγράψετε, να αγνοήσετε ή να διακόψετε τη διαδικασία ανάλογα με τη σοβαρότητα της προειδοποίησης.

**Ε: Μπορώ να μετατρέψω σχήματα σε αντικείμενα Office Math κατά τη φόρτωση ενός εγγράφου;**  
Α: Ναι — καλέστε `loadOptions.setConvertShapeToOfficeMath(true)` πριν δημιουργήσετε το `Document`. Η βιβλιοθήκη θα αντικαταστήσει αυτόματα τα συμβατά σχήματα με εγγενή αντικείμενα Office Math.

**Ε: Πώς ορίζω την έκδοση MS Word για τη φόρτωση εγγράφου;**  
Α: Χρησιμοποιήστε `loadOptions.setMswVersion(MsWordVersion.WORD_2010)` (ή οποιαδήποτε άλλη τιμή του enum) για να υποδείξετε στο Aspose.Words τους κανόνες απόδοσης της αντίστοιχης έκδοσης του Word.

**Ε: Ποιος είναι ο σκοπός της μεθόδου `setTempFolder` στα LoadOptions;**  
Α: Κατευθύνει όλα τα προσωρινά αρχεία που δημιουργούνται κατά τη φόρτωση (όπως εξαγόμενες εικόνες) σε φάκελο που εσείς ελέγχετε, κάτι ουσιώδες για περιβάλλοντα με περιορισμένους καταλόγους temp του συστήματος.

**Ε: Είναι δυνατόν να μετατρέψω μετααρχεία όπως WMF σε PNG κατά τη φόρτωση;**  
Α: Απόλυτα — ενεργοποιήστε το με `loadOptions.setConvertMetafilesToPng(true)`. Αυτό εξασφαλίζει ότι οι ραστερ εικόνες αποθηκεύονται ως PNG, βελτιώνοντας τη συμβατότητα με σύγχρονους προβολείς.

## Συμπέρασμα

Καλύψαμε τις βασικές τεχνικές για **πώς να ορίσετε το LoadOptions** στο Aspose.Words for Java, από την ενημέρωση dirty πεδίων μέχρι τη διαχείριση κρυπτογραφημένων αρχείων, τη μετατροπή σχημάτων, τον καθορισμό έκδοσης Word, την κατεύθυνση προσωρινής αποθήκευσης και πολλά άλλα. Εκμεταλλευόμενοι αυτές τις επιλογές, μπορείτε να δημιουργήσετε αξιόπιστες, υψηλής απόδοσης pipelines επεξεργασίας εγγράφων που προσαρμόζονται σε ένα ευρύ φάσμα σεναρίων εισόδου.

---

**Τελευταία Ενημέρωση:** 2025-12-27  
**Δοκιμασμένο Με:** Aspose.Words for Java 24.11  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}