---
date: 2025-12-24
description: Μάθετε πώς να δημιουργείτε απλό αρχείο κειμένου από έγγραφα Word χρησιμοποιώντας
  το Aspose.Words for Java. Αυτός ο οδηγός δείχνει πώς να μετατρέψετε το Word σε txt,
  να χρησιμοποιήσετε εσοχές με καρτέλα και να αποθηκεύσετε το Word ως txt.
linktitle: Saving Documents as Text Files
second_title: Aspose.Words Java Document Processing API
title: Πώς να δημιουργήσετε αρχείο απλού κειμένου με το Aspose.Words για Java
url: /el/java/document-loading-and-saving/saving-documents-as-text-files/
weight: 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Πώς να δημιουργήσετε αρχείο απλού κειμένου με το Aspose.Words για Java

## Εισαγωγή στην αποθήκευση εγγράφων ως αρχεία κειμένου στο Aspose.Words για Java

Σε αυτό το εκπαιδευτικό υλικό, θα μάθετε **πώς να δημιουργήσετε αρχείο απλού κειμένου** από ένα έγγραφο Word χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Είτε χρειάζεστε **να μετατρέψετε word σε txt**, να αυτοματοποιήσετε τη δημιουργία αναφορών, είτε απλώς να εξάγετε ακατέργαστο κείμενο για περαιτέρω επεξεργασία, αυτός ο οδηγός σας καθοδηγεί σε όλη τη διαδικασία — από τη δημιουργία του εγγράφου μέχρι τη λεπτομερή ρύθμιση των επιλογών αποθήκευσης, όπως **χρήση εσοχής με καρτέλα** ή προσθήκη σημάτων bidi. Ας ξεκινήσουμε!

## Γρήγορες Απαντήσεις
- **Ποια είναι η κύρια κλάση για τη δημιουργία εγγράφου;** `Document` από το Aspose.Words.
- **Ποια επιλογή προσθέτει σήματα bidi για γλώσσες από δεξιά προς αριστερά;** `TxtSaveOptions.setAddBidiMarks(true)`.
- **Πώς μπορώ να εσοχή των στοιχείων λίστας με καρτέλες;** Ορίστε `ListIndentation.Character` σε `'\t'`.
- **Χρειάζομαι άδεια για ανάπτυξη;** Μια δωρεάν δοκιμή λειτουργεί για δοκιμές· απαιτείται άδεια για παραγωγή.
- **Μπορώ να αποθηκεύσω το αρχείο με προσαρμοσμένο όνομα και διαδρομή;** Ναι — περάστε τη πλήρη διαδρομή στο `doc.save()`.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα παρακάτω προαπαιτούμενα:

- Java Development Kit (JDK) εγκατεστημένο στο σύστημα σας.  
- Βιβλιοθήκη Aspose.Words for Java ενσωματωμένη στο έργο σας. Μπορείτε να τη κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).  
- Βασικές γνώσεις προγραμματισμού Java.

## Βήμα 1: Δημιουργία Εγγράφου

Για **να αποθηκεύσετε word ως txt**, χρειάζεται πρώτα μια παρουσία `Document`. Παρακάτω υπάρχει ένα απλό απόσπασμα Java που δημιουργεί ένα έγγραφο και γράφει μερικές γραμμές πολυγλωσσικού κειμένου:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Σε αυτόν τον κώδικα δημιουργούμε ένα νέο έγγραφο, προσθέτουμε κείμενο στα Αγγλικά, Εβραϊκά και Αραβικά, και ενεργοποιούμε τη μορφοποίηση από δεξιά προς αριστερά για την εβραϊκή παράγραφο.

## Βήμα 2: Ορισμός Επιλογών Αποθήκευσης Κειμένου

Στη συνέχεια, διαμορφώνουμε πώς θα αποθηκευτεί το έγγραφο ως αρχείο απλού κειμένου. Το Aspose.Words παρέχει την κλάση `TxtSaveOptions`, η οποία σας επιτρέπει να ελέγχετε τα πάντα, από τα σήματα bidi μέχρι την εσοχή λίστας.

### Παράδειγμα 1: Προσθήκη Σημάτων Bidi (πώς να αποθηκεύσετε txt με σωστή υποστήριξη RTL)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Ο ορισμός του `AddBidiMarks` σε `true` εξασφαλίζει ότι οι χαρακτήρες από δεξιά προς αριστερά θα αναπαρασταθούν σωστά στο παραγόμενο **αρχείο απλού κειμένου**.

### Παράδειγμα 2: Χρήση Χαρακτήρα Καρτέλας για Εσοχή Λίστας (χρήση εσοχής με καρτέλα)

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Εδώ λέμε στο Aspose.Words να προσθέσει έναν χαρακτήρα καρτέλας (`'\t'`) πριν από κάθε επίπεδο λίστας, κάνοντας το κείμενο πιο ευανάγνωστο.

## Βήμα 3: Αποθήκευση του Εγγράφου ως Κείμενο

Τώρα που οι επιλογές αποθήκευσης είναι έτοιμες, μπορείτε να αποθηκεύσετε το έγγραφο ως **αρχείο απλού κειμένου**:

```java
doc.save("output.txt", saveOptions);
```

Αντικαταστήστε το `"output.txt"` με τη πλήρη διαδρομή όπου θέλετε να αποθηκευτεί το αρχείο.

## Πλήρης Πηγαίος Κώδικας για την Αποθήκευση Εγγράφων ως Αρχεία Κειμένου στο Aspose.Words για Java

```java
    public void addBidiMarks() throws Exception
    {        
		Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        builder.writeln("Hello world!");
        builder.getParagraphFormat().setBidi(true);
        builder.writeln("שלום עולם!");
        builder.writeln("مرحبا بالعالم!");
        TxtSaveOptions saveOptions = new TxtSaveOptions(); { saveOptions.setAddBidiMarks(true); }
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.AddBidiMarks.txt", saveOptions);
    }
    @Test
    public void useTabCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(1);
        saveOptions.getListIndentation().setCharacter('\t');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseTabCharacterPerLevelForListIndentation.txt", saveOptions);
    }
    @Test
    public void useSpaceCharacterPerLevelForListIndentation() throws Exception
    {
        Document doc = new Document();
        DocumentBuilder builder = new DocumentBuilder(doc);
        // Create a list with three levels of indentation.
        builder.getListFormat().applyNumberDefault();
        builder.writeln("Item 1");
        builder.getListFormat().listIndent();
        builder.writeln("Item 2");
        builder.getListFormat().listIndent(); 
        builder.write("Item 3");
        TxtSaveOptions saveOptions = new TxtSaveOptions();
        saveOptions.getListIndentation().setCount(3);
        saveOptions.getListIndentation().setCharacter(' ');
        doc.save("Your Directory Path" + "WorkingWithTxtSaveOptions.UseSpaceCharacterPerLevelForListIndentation.txt", saveOptions);
	}
```

## Συνηθισμένα Προβλήματα και Λύσεις

| Πρόβλημα | Λύση |
|----------|------|
| **Οι χαρακτήρες bidi εμφανίζονται ως ακατάληπτο κείμενο** | Βεβαιωθείτε ότι το `setAddBidiMarks(true)` είναι ενεργοποιημένο και ότι το αρχείο εξόδου ανοίγει με κωδικοποίηση UTF‑8. |
| **Η εσοχή λίστας φαίνεται λανθασμένη** | Ελέγξτε ότι το `ListIndentation.Count` και το `Character` έχουν οριστεί στις επιθυμητές τιμές (καρτέλα `'\t'` ή κενό `' '` ). |
| **Το αρχείο δεν δημιουργείται** | Ελέγξτε ότι η διαδρομή του καταλόγου υπάρχει και ότι η εφαρμογή έχει δικαιώματα εγγραφής. |

## Συχνές Ερωτήσεις

### Πώς να προσθέσω σήματα bidi στην έξοδο κειμένου;

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Μπορώ να προσαρμόσω τον χαρακτήρα εσοχής λίστας;

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Είναι το Aspose.Words για Java κατάλληλο για διαχείριση πολυγλωσσικού κειμένου;

Ναι, το Aspose.Words για Java υποστηρίζει ένα ευρύ φάσμα γλωσσών και κωδικοποιήσεων χαρακτήρων, καθιστώντας το ιδανικό για εξαγωγή και αποθήκευση πολυγλωσσικού περιεχομένου ως απλό κείμενο.

### Πώς μπορώ να αποκτήσω περισσότερη τεκμηρίωση και πόρους για το Aspose.Words για Java;

Μπορείτε να βρείτε ολοκληρωμένη τεκμηρίωση και πόρους στη σελίδα τεκμηρίωσης του Aspose.Words για Java: [Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Πού μπορώ να κατεβάσω το Aspose.Words για Java;

Μπορείτε να κατεβάσετε τη βιβλιοθήκη από την επίσημη ιστοσελίδα: [Download Aspose.Words for Java](https://releases.aspose.com/words/java/).

### Τι κάνω αν χρειαστεί να **μετατρέψω word σε txt** σε διαδικασία παρτίδας;

Τυλίξτε τον παραπάνω κώδικα σε έναν βρόχο που φορτώνει κάθε αρχείο `.docx`, εφαρμόζει τις ίδιες `TxtSaveOptions` και αποθηκεύει το καθένα ως `.txt`. Φροντίστε να διαχειρίζεστε τους πόρους απελευθερώνοντας τα αντικείμενα `Document` μετά από κάθε επανάληψη.

### Υποστηρίζει το API την αποθήκευση απευθείας σε ροή αντί για αρχείο;

Ναι, μπορείτε να περάσετε ένα `OutputStream` στο `doc.save(outputStream, saveOptions)` για επεξεργασία στη μνήμη ή όταν ενσωματώνετε με υπηρεσίες web.

---

**Τελευταία ενημέρωση:** 2025-12-24  
**Δοκιμή με:** Aspose.Words for Java 24.12 (latest)  
**Συγγραφέας:** Aspose  

{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}