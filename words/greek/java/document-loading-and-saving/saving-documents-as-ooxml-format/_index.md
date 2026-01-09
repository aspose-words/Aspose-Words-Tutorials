---
date: 2026-01-09
description: Μάθετε πώς να κρυπτογραφήσετε ένα αρχείο docx με κωδικό πρόσβασης και
  να αλλάξετε το επίπεδο συμπίεσης κατά την αποθήκευση εγγράφων σε μορφή OOXML χρησιμοποιώντας
  το Aspose.Words for Java.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Κρυπτογράφηση docx με κωδικό πρόσβασης – αποθήκευση OOXML με Aspose.Words Java
url: /el/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Κρυπτογράφηση docx με κωδικό πρόσβασης – αποθήκευση OOXML με Aspose.Words Java

## Εισαγωγή στην αποθήκευση εγγράφων σε μορφή OOXML με το Aspose.Words για Java

Σε αυτόν τον οδηγό, θα μάθετε πώς να **κρυπτογραφήσετε docx με κωδικό πρόσβασης** και να αποθηκεύσετε έγγραφα σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Το OOXML (Office Open XML) είναι η σύγχρονη μορφή αρχείου που χρησιμοποιείται από το Microsoft Word και πολλές άλλες εφαρμογές γραφείου. Θα περάσουμε από τις πιο συνηθισμένες επιλογές — προστασία με κωδικό, επίπεδα συμμόρφωσης, ενημέρωση ιδιοτήτων, διαχείριση παλαιών χαρακτήρων ελέγχου, και **πώς να αλλάξετε το επίπεδο συμπίεσης** — ώστε να προσαρμόσετε το αποτέλεσμα ακριβώς στις ανάγκες σας.

## Γρήγορες Απαντήσεις
- **Πώς μπορώ να προστατεύσω ένα αρχείο Word;** Χρησιμοποιήστε `OoxmlSaveOptions.setPassword("yourPassword")` πριν από την αποθήκευση.  
- **Ποιο επίπεδο συμμόρφωσης OOXML πρέπει να επιλέξω;** ISO 29500 2008 Strict για μέγιστη συμβατότητα με σύγχρονες εκδόσεις του Office.  
- **Μπορώ να διατηρήσω παλαιούς χαρακτήρες ελέγχου;** Ναι, ενεργοποιήστε `setKeepLegacyControlChars(true)`.  
- **Πώς αλλάζω το επίπεδο συμπίεσης;** Ορίστε `setCompressionLevel(CompressionLevel.SUPER_FAST)` ή `MAXIMUM` όπως απαιτείται.  
- **Επηρεάζουν αυτές οι επιλογές το μέγεθος του αρχείου;** Το επίπεδο συμπίεσης και η διαχείριση παλαιών χαρακτήρων ελέγχου μπορούν να αλλάξουν αισθητά το τελικό μέγεθος του .docx.

## Τι σημαίνει «κρυπτογράφηση docx με κωδικό πρόσβασης»;
Η κρυπτογράφηση ενός αρχείου DOCX σημαίνει ότι το έγγραφο αποθηκεύεται με κρυπτογράφηση AES‑256, απαιτώντας κωδικό πρόσβασης για το άνοιγμά του στο Word ή σε οποιονδήποτε συμβατό προβολέα. Αυτό είναι απαραίτητο για την προστασία εμπιστευτικών πληροφοριών όταν τα αρχεία μοιράζονται μέσω email, αποθήκευσης στο cloud ή εσωτερικών πύλες.

## Γιατί να χρησιμοποιήσετε τις επιλογές αποθήκευσης OOXML;
- **Ασφάλεια:** Η προστασία με κωδικό αποτρέπει μη εξουσιοδοτημένη πρόσβαση.  
- **Συμβατότητα:** Οι ρυθμίσεις συμμόρφωσης εξασφαλίζουν ότι το αρχείο λειτουργεί σε διαφορετικές εκδόσεις του Word.  
- **Απόδοση:** Η ρύθμιση της συμπίεσης μπορεί να επιταχύνει την αποθήκευση ή να μειώσει το μέγεθος του αρχείου.  
- **Διατήρηση:** Η διατήρηση παλαιών χαρακτήρων ελέγχου διασφαλίζει την πιστότητα κατά τη μετατροπή παλαιότερων εγγράφων.

## Προαπαιτούμενα
- Βιβλιοθήκη Aspose.Words για Java προστιθέμενη στο έργο σας (Maven/Gradle ή χειροκίνητο JAR).  
- Java 8 ή νεότερη.  
- Ένα πηγαίο έγγραφο (`.docx` ή `.doc`) που θέλετε να επεξεργαστείτε.

## Αποθήκευση Εγγράφου με Κρυπτογράφηση Κωδικού Πρόσβασης

Μπορείτε να κρυπτογραφήσετε το έγγραφό σας με κωδικό πρόσβασης ενώ το αποθηκεύετε σε μορφή OOXML. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the password
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Save the document with encryption
doc.save("EncryptedDoc.docx", saveOptions);
```

> **Συμβουλή:** Επιλέξτε έναν ισχυρό κωδικό και αποθηκεύστε τον με ασφάλεια· ο κωδικός δεν μπορεί να ανακτηθεί από το κρυπτογραφημένο αρχείο.

## Ορισμός Συμμόρφωσης OOXML

Μπορείτε να καθορίσετε το επίπεδο συμμόρφωσης OOXML κατά την αποθήκευση του εγγράφου. Για παράδειγμα, μπορείτε να το ορίσετε σε ISO 29500:2008 (Strict). Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Load the document
Document doc = new Document("Document.docx");

// Optimize for Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Create OoxmlSaveOptions and set the compliance level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Save the document with compliance setting
doc.save("ComplianceDoc.docx", saveOptions);
```

## Ενημέρωση Ιδιότητας «Τελευταία Αποθήκευση»

Μπορείτε να επιλέξετε την ενημέρωση της ιδιότητας «Τελευταία Αποθήκευση» του εγγράφου κατά την αποθήκευση. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and enable updating the Last Saved Time property
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Save the document with the updated property
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Διατήρηση Παλαιών Χαρακτήρων Ελέγχου

Αν το έγγραφό σας περιέχει παλαιούς χαρακτήρες ελέγχου, μπορείτε να επιλέξετε να τους διατηρήσετε κατά την αποθήκευση. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

// Load a document with legacy control characters
Document doc = new Document("LegacyControlChars.doc");

// Create OoxmlSaveOptions with the FLAT_OPC format and enable keeping legacy control characters
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Save the document with legacy control characters
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Πώς να Αλλάξετε το Επίπεδο Συμπίεσης Κατά την Αποθήκευση OOXML

Μπορείτε να ρυθμίσετε το επίπεδο συμπίεσης κατά την αποθήκευση του εγγράφου. Για παράδειγμα, μπορείτε να το ορίσετε σε `SUPER_FAST` για ελάχιστη συμπίεση ή `MAXIMUM` για το μικρότερο δυνατό μέγεθος αρχείου. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Load the document
Document doc = new Document("Document.docx");

// Create OoxmlSaveOptions and set the compression level
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Save the document with the specified compression level
doc.save("FastCompressionDoc.docx", saveOptions);
```

Αυτές είναι μερικές από τις βασικές επιλογές και ρυθμίσεις που μπορείτε να χρησιμοποιήσετε όταν αποθηκεύετε έγγραφα σε μορφή OOXML με το Aspose.Words για Java. Εξερευνήστε περισσότερες επιλογές και προσαρμόστε τη διαδικασία αποθήκευσης του εγγράφου σας όπως χρειάζεται.

## Πλήρης Πηγαίος Κώδικας για την Αποθήκευση Εγγράφων σε Μορφή OOXML με το Aspose.Words για Java

```java
public void encryptDocxWithPassword() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setPassword("password"); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.EncryptDocxWithPassword.docx", saveOptions);
}
@Test
public void ooxmlComplianceIso29500_2008_Strict() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.OoxmlComplianceIso29500_2008_Strict.docx", saveOptions);
}
@Test
public void updateLastSavedTimeProperty() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setUpdateLastSavedTimeProperty(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.UpdateLastSavedTimeProperty.docx", saveOptions);
}
@Test
public void keepLegacyControlChars() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Legacy control character.doc");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setKeepLegacyControlChars(true); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.KeepLegacyControlChars.docx", saveOptions);
}
@Test
public void setCompressionLevel() throws Exception
{
	Document doc = new Document("Your Directory Path" + "Document.docx");
	OoxmlSaveOptions saveOptions = new OoxmlSaveOptions(); { saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST); }
	doc.save("Your Directory Path" + "WorkingWithOoxmlSaveOptions.SetCompressionLevel.docx", saveOptions);
}
```

## Συμπέρασμα

Σε αυτόν τον ολοκληρωμένο οδηγό, εξετάσαμε πώς να **κρυπτογραφήσετε docx με κωδικό πρόσβασης** και να αποθηκεύσετε έγγραφα σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Είτε χρειάζεστε προστασία αρχείων, εξασφάλιση αυστηρής συμμόρφωσης OOXML, ενημέρωση ιδιοτήτων εγγράφου, διατήρηση παλαιών χαρακτήρων ελέγχου, είτε **αλλαγή του επιπέδου συμπίεσης**, το Aspose.Words παρέχει ένα ευέλικτο σύνολο εργαλείων για να καλύψετε τις απαιτήσεις σας.

## Συχνές Ερωτήσεις

**Ε: Πώς αφαιρώ την προστασία κωδικού από ένα έγγραφο που είναι κλειδωμένο με κωδικό;**  
Α: Ανοίξτε το έγγραφο με τον σωστό κωδικό, στη συνέχεια αποθηκεύστε το χωρίς να καθορίσετε κωδικό στο `OoxmlSaveOptions`. Αυτό δημιουργεί ένα αντίγραφο χωρίς προστασία.

**Ε: Μπορώ να ορίσω προσαρμοσμένες ιδιότητες κατά την αποθήκευση ενός εγγράφου σε μορφή OOXML;**  
Α: Ναι. Χρησιμοποιήστε `BuiltInDocumentProperties` και `CustomDocumentProperties` στο αντικείμενο `Document` πριν καλέσετε `save()`.

**Ε: Ποιο είναι το προεπιλεγμένο επίπεδο συμπίεσης όταν αποθηκεύεται ένα έγγραφο σε μορφή OOXML;**  
Α: Το προεπιλεγμένο είναι `CompressionLevel.NORMAL`. Μπορείτε να μεταβείτε σε `SUPER_FAST` για ταχύτητα ή `MAXIMUM` για το μικρότερο δυνατό μέγεθος αρχείου.

**Ε: Θα επηρεάσει η ενεργοποίηση του `keepLegacyControlChars` τη συμβατότητα με σύγχρονες εκδόσεις του Word;**  
Α: Το σύγχρονο Word μπορεί να ανοίξει αρχεία με παλαιούς χαρακτήρες ελέγχου, αλλά ορισμένα παλαιότερα χαρακτηριστικά ενδέχεται να εμφανιστούν διαφορετικά. Χρησιμοποιήστε αυτήν την επιλογή μόνο όταν χρειάζεται να διατηρήσετε το ακριβές αρχικό περιεχόμενο.

**Ε: Είναι δυνατόν να συνδυάσω πολλαπλές επιλογές αποθήκευσης (π.χ., κωδικός + συμπίεση) σε μία κλήση;**  
Α: Απόλυτα. Διαμορφώστε όλες τις επιθυμητές ιδιότητες σε ένα μόνο αντικείμενο `OoxmlSaveOptions` πριν το περάσετε στο `doc.save()`.

---

**Τελευταία ενημέρωση:** 2026-01-09  
**Δοκιμή με:** Aspose.Words για Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}