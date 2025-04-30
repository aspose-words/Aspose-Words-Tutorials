---
"description": "Μάθετε πώς να αποθηκεύετε έγγραφα ως αρχεία κειμένου στο Aspose.Words για Java. Ακολουθήστε τον αναλυτικό οδηγό μας με παραδείγματα κώδικα Java."
"linktitle": "Αποθήκευση εγγράφων ως αρχεία κειμένου"
"second_title": "API επεξεργασίας εγγράφων Java Aspose.Words"
"title": "Αποθήκευση εγγράφων ως αρχεία κειμένου στο Aspose.Words για Java"
"url": "/el/java/document-loading-and-saving/saving-documents-as-text-files/"
"weight": 24
---

{{< blocks/products/pf/main-wrap-class >}}

{{< blocks/products/pf/main-container >}}

{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφων ως αρχεία κειμένου στο Aspose.Words για Java


## Εισαγωγή στην αποθήκευση εγγράφων ως αρχεία κειμένου στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα εξερευνήσουμε πώς να αποθηκεύουμε έγγραφα ως αρχεία κειμένου χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Το Aspose.Words είναι ένα ισχυρό API Java για εργασία με έγγραφα Word και παρέχει διάφορες επιλογές για την αποθήκευση εγγράφων σε διαφορετικές μορφές, συμπεριλαμβανομένου του απλού κειμένου. Θα καλύψουμε τα βήματα για να το πετύχουμε αυτό και θα παρέχουμε δείγματα κώδικα Java στην πορεία.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Το Java Development Kit (JDK) είναι εγκατεστημένο στο σύστημά σας.
- Aspose.Words για βιβλιοθήκη Java ενσωματωμένη στο έργο σας. Μπορείτε να την κατεβάσετε από [εδώ](https://releases.aspose.com/words/java/).
- Βασικές γνώσεις προγραμματισμού Java.

## Βήμα 1: Δημιουργία εγγράφου

Για να αποθηκεύσουμε ένα έγγραφο ως αρχείο κειμένου, πρέπει πρώτα να δημιουργήσουμε ένα έγγραφο χρησιμοποιώντας το Aspose.Words. Ακολουθεί ένα απλό απόσπασμα κώδικα Java για να δημιουργήσετε ένα έγγραφο με κάποιο περιεχόμενο:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Σε αυτόν τον κώδικα, δημιουργούμε ένα νέο έγγραφο και προσθέτουμε κείμενο σε αυτό, συμπεριλαμβανομένου κειμένου σε διαφορετικές γλώσσες.

## Βήμα 2: Ορισμός επιλογών αποθήκευσης κειμένου

Στη συνέχεια, πρέπει να ορίσουμε τις επιλογές αποθήκευσης κειμένου που καθορίζουν τον τρόπο με τον οποίο το έγγραφο θα πρέπει να αποθηκευτεί ως αρχείο κειμένου. Μπορούμε να διαμορφώσουμε διάφορες ρυθμίσεις, όπως προσθήκη σημαδιών bidi, εσοχή λίστας και άλλα. Ας δούμε δύο παραδείγματα:

### Παράδειγμα 1: Προσθήκη Σημαδιών Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

Σε αυτό το παράδειγμα, δημιουργούμε ένα `TxtSaveOptions` αντικείμενο και ορίστε το `AddBidiMarks` ιδιοκτησία σε `true` για να συμπεριλάβετε σημάδια bidi στο κείμενο που προκύπτει.

### Παράδειγμα 2: Χρήση χαρακτήρα Tab για εσοχή λίστας

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Εδώ, ρυθμίζουμε τις επιλογές αποθήκευσης ώστε να χρησιμοποιούν έναν χαρακτήρα tab για την εσοχή της λίστας με αριθμό 1.

## Βήμα 3: Αποθήκευση του εγγράφου ως κείμενο

Τώρα που έχουμε ορίσει τις επιλογές αποθήκευσης κειμένου, μπορούμε να αποθηκεύσουμε το έγγραφο ως αρχείο κειμένου. Ο ακόλουθος κώδικας δείχνει πώς να το κάνετε αυτό:

```java
doc.save("output.txt", saveOptions);
```

Αντικαθιστώ `"output.txt"` με την επιθυμητή διαδρομή αρχείου όπου θέλετε να αποθηκεύσετε το αρχείο κειμένου.

## Πλήρης πηγαίος κώδικας για την αποθήκευση εγγράφων ως αρχεία κειμένου στο Aspose.Words για Java

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
        // Δημιουργήστε μια λίστα με τρία επίπεδα εσοχής.
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
        // Δημιουργήστε μια λίστα με τρία επίπεδα εσοχής.
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

## Σύναψη

Σε αυτό το σεμινάριο, μάθαμε πώς να αποθηκεύουμε έγγραφα ως αρχεία κειμένου στο Aspose.Words για Java. Καλύψαμε τα βήματα για τη δημιουργία ενός εγγράφου, τον ορισμό επιλογών αποθήκευσης κειμένου και την αποθήκευση του εγγράφου σε μορφή κειμένου. Το Aspose.Words παρέχει εκτεταμένη ευελιξία όσον αφορά την αποθήκευση εγγράφων, επιτρέποντάς σας να προσαρμόσετε το αποτέλεσμα στις συγκεκριμένες απαιτήσεις σας.

## Συχνές ερωτήσεις

### Πώς μπορώ να προσθέσω σημάδια bidi στο κείμενο που προκύπτει;

Για να προσθέσετε σημάδια bidi στο κείμενο που εμφανίζεται, ορίστε το `AddBidiMarks` ιδιοκτησία του `TxtSaveOptions` να `true`Για παράδειγμα:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Μπορώ να προσαρμόσω τον χαρακτήρα εσοχής λίστας;

Ναι, μπορείτε να προσαρμόσετε τον χαρακτήρα εσοχής της λίστας διαμορφώνοντας το `ListIndentation` ιδιοκτησία του `TxtSaveOptions`Για παράδειγμα, για να χρησιμοποιήσετε έναν χαρακτήρα tab για εσοχή λίστας, μπορείτε να κάνετε τα εξής:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Είναι το Aspose.Words για Java κατάλληλο για χειρισμό πολύγλωσσου κειμένου;

Ναι, το Aspose.Words για Java είναι κατάλληλο για τη διαχείριση πολύγλωσσου κειμένου. Υποστηρίζει διάφορες γλώσσες και κωδικοποιήσεις χαρακτήρων, καθιστώντας το μια ευέλικτη επιλογή για εργασία με έγγραφα σε διαφορετικές γλώσσες.

### Πώς μπορώ να έχω πρόσβαση σε περισσότερη τεκμηρίωση και πόρους για το Aspose.Words για Java;

Μπορείτε να βρείτε ολοκληρωμένη τεκμηρίωση και πόρους για το Aspose.Words για Java στον ιστότοπο τεκμηρίωσης του Aspose: [Aspose.Words για τεκμηρίωση Java](https://reference.aspose.com/words/java/).

### Πού μπορώ να κατεβάσω το Aspose.Words για Java;

Μπορείτε να κατεβάσετε τη βιβλιοθήκη Aspose.Words για Java από τον ιστότοπο Aspose: [Λήψη Aspose.Words για Java](https://releases.aspose.com/words/java/).


{{< /blocks/products/pf/tutorial-page-section >}}


{{< /blocks/products/pf/main-container >}}

{{< /blocks/products/pf/main-wrap-class >}}


{{< blocks/products/products-backtop-button >}}