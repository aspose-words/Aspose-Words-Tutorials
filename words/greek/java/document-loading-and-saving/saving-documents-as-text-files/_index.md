---
title: Αποθήκευση εγγράφων ως αρχείων κειμένου στο Aspose.Words για Java
linktitle: Αποθήκευση εγγράφων ως αρχεία κειμένου
second_title: Aspose.Words Java Document Processing API
description: Μάθετε πώς να αποθηκεύετε έγγραφα ως αρχεία κειμένου στο Aspose.Words για Java. Ακολουθήστε τον βήμα προς βήμα οδηγό μας με παραδείγματα κώδικα Java.
weight: 24
url: /el/java/document-loading-and-saving/saving-documents-as-text-files/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Αποθήκευση εγγράφων ως αρχείων κειμένου στο Aspose.Words για Java


## Εισαγωγή στην αποθήκευση εγγράφων ως αρχείων κειμένου στο Aspose.Words για Java

Σε αυτό το σεμινάριο, θα διερευνήσουμε πώς να αποθηκεύσετε έγγραφα ως αρχεία κειμένου χρησιμοποιώντας τη βιβλιοθήκη Aspose.Words για Java. Το Aspose.Words είναι ένα ισχυρό Java API για εργασία με έγγραφα του Word και παρέχει διάφορες επιλογές για αποθήκευση εγγράφων σε διαφορετικές μορφές, συμπεριλαμβανομένου απλού κειμένου. Θα καλύψουμε τα βήματα για να το πετύχουμε αυτό και θα παρέχουμε δείγμα κώδικα Java στην πορεία.

## Προαπαιτούμενα

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τις ακόλουθες προϋποθέσεις:

- Το Java Development Kit (JDK) είναι εγκατεστημένο στο σύστημά σας.
-  Η βιβλιοθήκη Aspose.Words for Java είναι ενσωματωμένη στο έργο σας. Μπορείτε να το κατεβάσετε από[εδώ](https://releases.aspose.com/words/java/).
- Βασικές γνώσεις προγραμματισμού Java.

## Βήμα 1: Δημιουργήστε ένα έγγραφο

Για να αποθηκεύσουμε ένα έγγραφο ως αρχείο κειμένου, πρέπει πρώτα να δημιουργήσουμε ένα έγγραφο χρησιμοποιώντας το Aspose.Words. Ακολουθεί ένα απλό απόσπασμα κώδικα Java για τη δημιουργία ενός εγγράφου με κάποιο περιεχόμενο:

```java
Document doc = new Document();
DocumentBuilder builder = new DocumentBuilder(doc);
builder.writeln("Hello world!");
builder.getParagraphFormat().setBidi(true);
builder.writeln("שלום עולם!");
builder.writeln("مرحبا بالعالم!");
```

Σε αυτόν τον κώδικα, δημιουργούμε ένα νέο έγγραφο και προσθέτουμε κείμενο σε αυτό, συμπεριλαμβανομένου κειμένου σε διαφορετικές γλώσσες.

## Βήμα 2: Ορίστε τις επιλογές αποθήκευσης κειμένου

Στη συνέχεια, πρέπει να ορίσουμε τις επιλογές αποθήκευσης κειμένου που καθορίζουν τον τρόπο αποθήκευσης του εγγράφου ως αρχείο κειμένου. Μπορούμε να διαμορφώσουμε διάφορες ρυθμίσεις, όπως προσθήκη σημάτων bidi, εσοχή λίστας και πολλά άλλα. Ας δούμε δύο παραδείγματα:

### Παράδειγμα 1: Προσθήκη σημάτων Bidi

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
doc.save("output.txt", saveOptions);
```

 Σε αυτό το παράδειγμα, δημιουργούμε ένα`TxtSaveOptions` αντικείμενο και ορίστε το`AddBidiMarks`ιδιοκτησία σε`true` για να συμπεριλάβετε σημάδια bidi στην έξοδο κειμένου.

### Παράδειγμα 2: Χρήση χαρακτήρα καρτέλας για εσοχή λίστας

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
doc.save("output.txt", saveOptions);
```

Εδώ, διαμορφώνουμε τις επιλογές αποθήκευσης ώστε να χρησιμοποιούν έναν χαρακτήρα καρτέλας για εσοχή λίστας με πλήθος 1.

## Βήμα 3: Αποθηκεύστε το έγγραφο ως κείμενο

Τώρα που έχουμε ορίσει τις επιλογές αποθήκευσης κειμένου, μπορούμε να αποθηκεύσουμε το έγγραφο ως αρχείο κειμένου. Ο παρακάτω κώδικας δείχνει πώς να το κάνετε αυτό:

```java
doc.save("output.txt", saveOptions);
```

 Αντικαθιστώ`"output.txt"` με την επιθυμητή διαδρομή αρχείου όπου θέλετε να αποθηκεύσετε το αρχείο κειμένου.

## Ολοκληρώστε τον πηγαίο κώδικα για την αποθήκευση εγγράφων ως αρχείων κειμένου στο Aspose.Words για Java

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

Σε αυτό το σεμινάριο, μάθαμε πώς να αποθηκεύουμε έγγραφα ως αρχεία κειμένου στο Aspose.Words για Java. Καλύψαμε τα βήματα για τη δημιουργία ενός εγγράφου, τον ορισμό των επιλογών αποθήκευσης κειμένου και την αποθήκευση του εγγράφου σε μορφή κειμένου. Το Aspose.Words παρέχει μεγάλη ευελιξία όσον αφορά την αποθήκευση εγγράφων, επιτρέποντάς σας να προσαρμόσετε το αποτέλεσμα στις συγκεκριμένες απαιτήσεις σας.

## Συχνές ερωτήσεις

### Πώς μπορώ να προσθέσω σημάδια bidi στην έξοδο κειμένου;

 Για να προσθέσετε σημάδια bidi στην έξοδο κειμένου, ορίστε το`AddBidiMarks` ιδιοκτησία του`TxtSaveOptions` να`true`. Για παράδειγμα:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.setAddBidiMarks(true);
```

### Μπορώ να προσαρμόσω τον χαρακτήρα της εσοχής της λίστας;

 Ναι, μπορείτε να προσαρμόσετε τον χαρακτήρα της εσοχής της λίστας ρυθμίζοντας τις παραμέτρους του`ListIndentation` ιδιοκτησία του`TxtSaveOptions`. Για παράδειγμα, για να χρησιμοποιήσετε έναν χαρακτήρα καρτέλας για την εσοχή λίστας, μπορείτε να κάνετε τα εξής:

```java
TxtSaveOptions saveOptions = new TxtSaveOptions();
saveOptions.getListIndentation().setCount(1);
saveOptions.getListIndentation().setCharacter('\t');
```

### Είναι το Aspose.Words για Java κατάλληλο για χειρισμό πολύγλωσσου κειμένου;

Ναι, το Aspose.Words για Java είναι κατάλληλο για χειρισμό πολύγλωσσου κειμένου. Υποστηρίζει διάφορες γλώσσες και κωδικοποιήσεις χαρακτήρων, καθιστώντας το μια ευέλικτη επιλογή για εργασία με έγγραφα σε διαφορετικές γλώσσες.

### Πώς μπορώ να έχω πρόσβαση σε περισσότερη τεκμηρίωση και πόρους για το Aspose.Words για Java;

 Μπορείτε να βρείτε ολοκληρωμένη τεκμηρίωση και πόρους για το Aspose.Words για Java στον ιστότοπο τεκμηρίωσης Aspose:[Aspose.Words for Java Documentation](https://reference.aspose.com/words/java/).

### Πού μπορώ να κατεβάσω το Aspose.Words για Java;

 Μπορείτε να κάνετε λήψη της βιβλιοθήκης Aspose.Words για Java από τον ιστότοπο Aspose:[Κατεβάστε το Aspose.Words για Java](https://releases.aspose.com/words/java/).
{{< /blocks/products/pf/tutorial-page-section >}}

{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}

{{< blocks/products/products-backtop-button >}}
