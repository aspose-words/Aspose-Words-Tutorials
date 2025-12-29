---
date: 2025-12-29
description: Μάθετε πώς να κρυπτογραφήσετε ένα αρχείο docx με κωδικό πρόσβασης χρησιμοποιώντας
  τις επιλογές αποθήκευσης του Aspose.Words for Java. Ασφαλίστε, βελτιστοποιήστε και
  προσαρμόστε τα αρχεία OOXML σας χωρίς κόπο.
linktitle: Saving Documents as OOXML Format
second_title: Aspose.Words Java Document Processing API
title: Πώς να κρυπτογραφήσετε DOCX με κωδικό πρόσβασης χρησιμοποιώντας το Aspose.Words
  για Java
url: /el/java/document-loading-and-saving/saving-documents-as-ooxml-format/
weight: 20
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να κρυπτογραφήσετε DOCX με κωδικό πρόσβασης χρησιμοποιώντας το Aspose.Words για Java

Σε αυτόν τον οδηγό θα ανακαλύψετε **πώς να κρυπτογραφήσετε docx με κωδικό πρόσβασης** κατά την αποθήκευση εγγράφων σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Είτε προστατεύετε εμπιστευτικές αναφορές είτε ασφαλίζετε σχέδια συμβάσεων, τα παρακάτω βήματα δείχνουν ακριβώς πώς να εφαρμόσετε προστασία με κωδικό πρόσβασης και να ρυθμίσετε λεπτομερώς άλλες επιλογές αποθήκευσης OOXML.

## Γρήγορες Απαντήσεις
- **Μπορώ να κρυπτογραφήσω ένα αρχείο DOCX με κωδικό πρόσβασης;** Ναι, χρησιμοποιήστε `OoxmlSaveOptions.setPassword()` πριν από την αποθήκευση.  
- **Ποια κλάση ελέγχει τις ρυθμίσεις αποθήκευσης OOXML;** `OoxmlSaveOptions` (μέρος του Aspose.Words).  
- **Χρειάζομαι άδεια για την προστασία με κωδικό πρόσβασης;** Απαιτείται έγκυρη άδεια Aspose.Words για παραγωγική χρήση.  
- **Μπορώ να συνδυάσω κρυπτογράφηση με ρυθμίσεις συμμόρφωσης;** Απόλυτα – ορίστε τόσο `setPassword` όσο και `setCompliance` στην ίδια παρουσία `OoxmlSaveOptions`.  
- **Ποια επίπεδα συμπίεσης είναι διαθέσιμα;** `NORMAL`, `SUPER_FAST` και `MAXIMUM` μέσω `CompressionLevel`.

## Τι σημαίνει “encrypt docx with password”;
Η κρυπτογράφηση ενός αρχείου DOCX σημαίνει ότι τα περιεχόμενα του αρχείου αποθηκεύονται σε κρυπτογραφημένη μορφή και μπορούν να ανοιχτούν μόνο μετά την εισαγωγή του σωστού κωδικού πρόσβασης. Αυτό προστατεύει ευαίσθητες πληροφορίες από μη εξουσιοδοτημένη πρόσβαση, ενώ εξακολουθεί να επιτρέπει στα τυπικά εργαλεία του Word να ανοίξουν το αρχείο μόλις δοθεί ο κωδικός.

## Γιατί να χρησιμοποιήσετε τις επιλογές αποθήκευσης του Aspose.Words για κρυπτογράφηση;
Το Aspose.Words παρέχει ένα πλούσιο σύνολο **aspose words save options** που σας επιτρέπει να ελέγχετε όχι μόνο την κρυπτογράφηση, αλλά και τα επίπεδα συμμόρφωσης, τη συμπίεση και τη διαχείριση παλαιών χαρακτήρων – όλα από κώδικα Java. Αυτό εξαλείφει την ανάγκη για χειροκίνητη επεξεργασία ή εξωτερικά εργαλεία τρίτων.

## Προαπαιτούμενα
- Java Development Kit (JDK 8 ή νεότερο)  
- Βιβλιοθήκη Aspose.Words για Java προστιθέμενη στο έργο σας (Maven/Gradle ή JAR)  
- Έγκυρη άδεια Aspose.Words για παραγωγική χρήση (προαιρετική για αξιολόγηση)

## Αποθήκευση Εγγράφου με Κρυπτογράφηση Κωδικού Πρόσβασης

Μπορείτε να κρυπτογραφήσετε το έγγραφό σας με κωδικό πρόσβασης κατά την αποθήκευση του σε μορφή OOXML. Δείτε πώς:

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

## Ορισμός Συμμόρφωσης OOXML

Μπορείτε να καθορίσετε το επίπεδο συμμόρφωσης OOXML κατά την αποθήκευση του εγγράφου. Για παράδειγμα, μπορείτε να το ορίσετε σε ISO 29500:2008 (Strict). Δείτε πώς:

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

## Ενημέρωση Ιδιότητας “Τελευταία Αποθήκευση”

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

## Ορισμός Επιπέδου Συμπίεσης

Μπορείτε να ρυθμίσετε το επίπεδο συμπίεσης κατά την αποθήκευση του εγγράφου. Για παράδειγμα, μπορείτε να το ορίσετε σε **SUPER_FAST** για ελάχιστη συμπίεση. Δείτε πώς:

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

Αυτές είναι μερικές από τις βασικές επιλογές και ρυθμίσεις που μπορείτε να χρησιμοποιήσετε όταν αποθηκεύετε έγγραφα σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Εξερευνήστε περισσότερες επιλογές και προσαρμόστε τη διαδικασία αποθήκευσης του εγγράφου σας όπως χρειάζεται.

## Πλήρης Πηγαίος Κώδικας για Αποθήκευση Εγγράφων σε Μορφή OOXML στο Aspose.Words για Java

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

Σε αυτόν τον ολοκληρωμένο οδηγό, εξετάσαμε πώς να **encrypt docx with password** και να ρυθμίσουμε λεπτομερώς μια σειρά από επιλογές αποθήκευσης OOXML χρησιμοποιώντας το Aspose.Words για Java. Είτε χρειάζεστε προστασία εμπιστευτικού περιεχομένου, συμμόρφωση με αυστηρά πρότυπα ISO, διατήρηση παλαιών χαρακτήρων ή έλεγχο της συμπίεσης, η βιβλιοθήκη σας δίνει λεπτομερή έλεγχο μέσω του ίδιου API `OoxmlSaveOptions`.

## Συχνές Ερωτήσεις

**Ε: Πώς αφαιρώ την προστασία κωδικού πρόσβασης από ένα έγγραφο που είναι προστατευμένο με κωδικό;**  
Α: Ανοίξτε το έγγραφο με τον σωστό κωδικό πρόσβασης, στη συνέχεια αποθηκεύστε το ξανά χωρίς να καλέσετε `setPassword`. Το νέο αρχείο θα είναι απροστάτευτο.

**Ε: Μπορώ να ορίσω προσαρμοσμένες ιδιότητες κατά την αποθήκευση ενός εγγράφου σε μορφή OOXML;**  
Α: Ναι. Χρησιμοποιήστε `BuiltInDocumentProperties` ή `CustomDocumentProperties` στο αντικείμενο `Document` πριν καλέσετε `save`.

**Ε: Ποιο είναι το προεπιλεγμένο επίπεδο συμπίεσης όταν αποθηκεύεται ένα έγγραφο σε μορφή OOXML;**  
Α: Το προεπιλεγμένο είναι `NORMAL`. Μπορείτε να μεταβείτε σε `SUPER_FAST` για ταχύτητα ή `MAXIMUM` για μικρότερο μέγεθος αρχείου.

**Ε: Οι aspose words save options λειτουργούν με παλαιότερες εκδόσεις του Word;**  
Α: Ναι. Με την προσαρμογή του `MsWordVersion` και των ρυθμίσεων συμμόρφωσης, μπορείτε να στοχεύσετε Word 2007‑2019 και να εξασφαλίσετε συμβατότητα.

**Ε: Είναι δυνατόν να συνδυάσω πολλαπλές επιλογές αποθήκευσης σε μία ενέργεια;**  
Α: Απόλυτα. Δημιουργήστε μία παρουσία `OoxmlSaveOptions`, ορίστε όλες τις επιθυμητές ιδιότητες (κωδικός, συμμόρφωση, συμπίεση κ.λπ.) και περάστε την στο `doc.save()`.

---

**Τελευταία ενημέρωση:** 2025-12-29  
**Δοκιμασμένο με:** Aspose.Words για Java 24.12  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}