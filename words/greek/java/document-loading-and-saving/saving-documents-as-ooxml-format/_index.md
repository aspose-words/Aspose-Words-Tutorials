---
title: Αποθήκευση εγγράφων ως μορφή OOXML στο Aspose.Words για Java
linktitle: Αποθήκευση εγγράφων ως μορφή OOXML
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να αποθηκεύετε έγγραφα σε μορφή OOXML με το Aspose.Words για Java. Ασφαλίστε, βελτιστοποιήστε και προσαρμόστε τα αρχεία σας χωρίς κόπο.
weight: 20
url: /el/java/document-loading-and-saving/saving-documents-as-ooxml-format/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφων ως μορφή OOXML στο Aspose.Words για Java


## Εισαγωγή στην αποθήκευση εγγράφων ως μορφή OOXML στο Aspose.Words για Java

Σε αυτόν τον οδηγό, θα διερευνήσουμε τον τρόπο αποθήκευσης εγγράφων σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Το OOXML (Office Open XML) είναι μια μορφή αρχείου που χρησιμοποιείται από το Microsoft Word και άλλες εφαρμογές γραφείου. Θα καλύψουμε διάφορες επιλογές και ρυθμίσεις για την αποθήκευση εγγράφων σε μορφή OOXML.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε ρυθμίσει τη βιβλιοθήκη Aspose.Words for Java στο έργο σας.

## Αποθήκευση εγγράφου με κρυπτογράφηση κωδικού πρόσβασης

Μπορείτε να κρυπτογραφήσετε το έγγραφό σας με κωδικό πρόσβασης ενώ το αποθηκεύετε σε μορφή OOXML. Δείτε πώς μπορείτε να το κάνετε:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Φορτώστε το έγγραφο
Document doc = new Document("Document.docx");

// Δημιουργήστε το OoxmlSaveOptions και ορίστε τον κωδικό πρόσβασης
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setPassword("password");

// Αποθηκεύστε το έγγραφο με κρυπτογράφηση
doc.save("EncryptedDoc.docx", saveOptions);
```

## Ρύθμιση συμμόρφωσης OOXML

Μπορείτε να καθορίσετε το επίπεδο συμμόρφωσης OOXML κατά την αποθήκευση του εγγράφου. Για παράδειγμα, μπορείτε να το ορίσετε στο ISO 29500:2008 (Αυστηρό). Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.MsWordVersion;
import com.aspose.words.OoxmlCompliance;

// Φορτώστε το έγγραφο
Document doc = new Document("Document.docx");

// Optimize για το Word 2016
doc.getCompatibilityOptions().optimizeFor(MsWordVersion.WORD_2016);

// Δημιουργήστε το OoxmlSaveOptions και ορίστε το επίπεδο συμμόρφωσης
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompliance(OoxmlCompliance.ISO_29500_2008_STRICT);

// Αποθηκεύστε το έγγραφο με ρύθμιση συμμόρφωσης
doc.save("ComplianceDoc.docx", saveOptions);
```

## Ενημέρωση της ιδιότητας τελευταίας αποθηκευμένης ώρας

Μπορείτε να επιλέξετε να ενημερώσετε την ιδιότητα "Τελευταία αποθηκευμένη ώρα" του εγγράφου κατά την αποθήκευση. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;

// Φορτώστε το έγγραφο
Document doc = new Document("Document.docx");

// Δημιουργήστε το OoxmlSaveOptions και ενεργοποιήστε την ενημέρωση της ιδιότητας Τελευταία αποθηκευμένη ώρα
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setUpdateLastSavedTimeProperty(true);

// Αποθηκεύστε το έγγραφο με την ενημερωμένη ιδιότητα
doc.save("UpdatedLastSavedTime.docx", saveOptions);
```

## Διατήρηση χαρακτήρων ελέγχου παλαιού τύπου

Εάν το έγγραφό σας περιέχει χαρακτήρες ελέγχου παλαιού τύπου, μπορείτε να επιλέξετε να τους διατηρήσετε κατά την αποθήκευση. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.SaveFormat;

//Φορτώστε ένα έγγραφο με χαρακτήρες ελέγχου παλαιού τύπου
Document doc = new Document("LegacyControlChars.doc");

// Δημιουργήστε OoxmlSaveOptions με τη μορφή FLAT_OPC και ενεργοποιήστε τη διατήρηση χαρακτήρων ελέγχου παλαιού τύπου
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setKeepLegacyControlChars(true);

// Αποθηκεύστε το έγγραφο με χαρακτήρες ελέγχου παλαιού τύπου
doc.save("LegacyControlCharsPreserved.docx", saveOptions);
```

## Ρύθμιση επιπέδου συμπίεσης

Μπορείτε να προσαρμόσετε το επίπεδο συμπίεσης κατά την αποθήκευση του εγγράφου. Για παράδειγμα, μπορείτε να το ρυθμίσετε σε SUPER_FAST για ελάχιστη συμπίεση. Δείτε πώς:

```java
import com.aspose.words.Document;
import com.aspose.words.OoxmlSaveOptions;
import com.aspose.words.CompressionLevel;

// Φορτώστε το έγγραφο
Document doc = new Document("Document.docx");

// Δημιουργήστε το OoxmlSaveOptions και ορίστε το επίπεδο συμπίεσης
OoxmlSaveOptions saveOptions = new OoxmlSaveOptions();
saveOptions.setCompressionLevel(CompressionLevel.SUPER_FAST);

// Αποθηκεύστε το έγγραφο με το καθορισμένο επίπεδο συμπίεσης
doc.save("FastCompressionDoc.docx", saveOptions);
```

Αυτές είναι μερικές από τις βασικές επιλογές και ρυθμίσεις που μπορείτε να χρησιμοποιήσετε κατά την αποθήκευση εγγράφων σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Μη διστάσετε να εξερευνήσετε περισσότερες επιλογές και να προσαρμόσετε τη διαδικασία αποθήκευσης εγγράφων όπως απαιτείται.

## Ολοκληρώστε τον πηγαίο κώδικα για την αποθήκευση εγγράφων ως μορφή OOXML στο Aspose.Words για Java

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

## Σύναψη

Σε αυτόν τον περιεκτικό οδηγό, εξερευνήσαμε τον τρόπο αποθήκευσης εγγράφων σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java. Είτε χρειάζεται να κρυπτογραφήσετε τα έγγραφά σας με κωδικούς πρόσβασης, να διασφαλίσετε τη συμμόρφωση με συγκεκριμένα πρότυπα OOXML, να ενημερώσετε τις ιδιότητες εγγράφων, να διατηρήσετε χαρακτήρες ελέγχου παλαιού τύπου ή να προσαρμόσετε τα επίπεδα συμπίεσης, το Aspose.Words παρέχει ένα ευέλικτο σύνολο εργαλείων για να καλύψει τις απαιτήσεις σας.

## Συχνές ερωτήσεις

### Πώς μπορώ να αφαιρέσω την προστασία με κωδικό πρόσβασης από ένα έγγραφο που προστατεύεται με κωδικό πρόσβασης;

Για να καταργήσετε την προστασία με κωδικό πρόσβασης από ένα έγγραφο που προστατεύεται με κωδικό πρόσβασης, μπορείτε να ανοίξετε το έγγραφο με τον σωστό κωδικό πρόσβασης και στη συνέχεια να το αποθηκεύσετε χωρίς να καθορίσετε κωδικό πρόσβασης στις επιλογές αποθήκευσης. Αυτό θα αποθηκεύσει το έγγραφο χωρίς προστασία με κωδικό πρόσβασης.

### Μπορώ να ορίσω προσαρμοσμένες ιδιότητες κατά την αποθήκευση ενός εγγράφου σε μορφή OOXML;

 Ναι, μπορείτε να ορίσετε προσαρμοσμένες ιδιότητες για ένα έγγραφο πριν το αποθηκεύσετε σε μορφή OOXML. Χρησιμοποιήστε το`BuiltInDocumentProperties` και`CustomDocumentProperties` κλάσεις για να ορίσετε διάφορες ιδιότητες, όπως συγγραφέα, τίτλο, λέξεις-κλειδιά και προσαρμοσμένες ιδιότητες.

### Ποιο είναι το προεπιλεγμένο επίπεδο συμπίεσης κατά την αποθήκευση ενός εγγράφου σε μορφή OOXML;

 Το προεπιλεγμένο επίπεδο συμπίεσης κατά την αποθήκευση ενός εγγράφου σε μορφή OOXML χρησιμοποιώντας το Aspose.Words για Java είναι`NORMAL` . Μπορείτε να αλλάξετε το επίπεδο συμπίεσης σε`SUPER_FAST` ή`MAXIMUM` όπως χρειάζεται.
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
