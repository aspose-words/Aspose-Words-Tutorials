---
category: general
date: 2026-05-04
description: Δημιουργήστε έγγραφο Word σε Java χρησιμοποιώντας το Aspose.Words και
  μάθετε πώς να ελέγχετε τη γραμματική με ένα προσαρμοσμένο LLM. Οδηγός βήμα‑βήμα
  για προγραμματιστές Java.
draft: false
keywords:
- create word document java
- how to create docx
- how to check grammar
- use custom llm
language: el
og_description: Δημιουργήστε έγγραφο Word με Java και δείτε πώς να ελέγξετε τη γραμματική
  χρησιμοποιώντας ένα προσαρμοσμένο LLM. Πλήρης οδηγός Java με εκτελέσιμο κώδικα.
og_title: Δημιουργήστε έγγραφο Word σε Java με προσαρμοσμένο έλεγχο γραμματικής LLM
tags:
- Java
- Aspose.Words
- LLM
title: Δημιουργία εγγράφου Word σε Java με προσαρμοσμένο έλεγχο γραμματικής LLM
url: /el/java/ai-machine-learning-integration/create-word-document-java-with-custom-llm-grammar-check/
---

{{< blocks/products/pf/main-wrap-class >}}
{{< blocks/products/pf/main-container >}}
{{< blocks/products/pf/tutorial-page-section >}}

# Δημιουργία εγγράφου word java με προσαρμοσμένο έλεγχο γραμματικής LLM

Έχετε αναρωτηθεί ποτέ πώς να **create word document java** έργα που επίσης διορθώνουν αυτόματα το κείμενό τους; Δεν είστε μόνοι—πολλοί προγραμματιστές θέλουν μια ενιαία διαδικασία που παράγει ένα τελειοποιημένο αρχείο *.docx* χωρίς να χρειάζεται να διαχειρίζονται πολλά εργαλεία. Σε αυτό το tutorial θα περάσουμε ακριβώς από αυτό, δείχνοντάς σας **how to create docx** αρχεία με το Aspose.Words, να συνδέσετε ένα τοπικά φιλοξενούμενο LLM, και τελικά **how to check grammar** αυτόματα. Στο τέλος θα έχετε ένα αυτόνομο πρόγραμμα Java που γράφει, επικυρώνει και αποθηκεύει ένα έγγραφο Word—όλα ενώ **using custom LLM** endpoints ελέγχετε.

## Τι Θα Χρειαστεί

Πριν ξεκινήσουμε, βεβαιωθείτε ότι έχετε τα παρακάτω στον υπολογιστή σας:

| Προαπαιτούμενο | Γιατί είναι σημαντικό |
|--------------|----------------|
| Java 17+ (ή οποιοδήποτε πρόσφατο JDK) | Σύγχρονα χαρακτηριστικά της γλώσσας και καλύτερη υποστήριξη μονάδων |
| Aspose.Words for Java (latest version) | Η βιβλιοθήκη που σας επιτρέπει να **create word document java** αρχεία προγραμματιστικά |
| Ένας τοπικά φιλοξενούμενος διακομιστής LLM (π.χ., Ollama, LMStudio) που ακούει στο `http://localhost:11434/api/generate` | Απαιτείται για το βήμα **use custom llm** που τροφοδοτεί τον έλεγχο γραμματικής |
| Maven ή Gradle (θα χρησιμοποιήσουμε Maven στα παραδείγματα) | Απλοποιεί τη διαχείριση εξαρτήσεων |
| Ένα IDE ή κειμενογράφο (IntelliJ IDEA, VS Code, κλπ.) | Κάνει τον κώδικα και την αποσφαλμάτωση πιο εύκολα |

Αν κάποιο από αυτά σας φαίνεται άγνωστο, μην πανικοβληθείτε—κάθε στοιχείο είναι δωρεάν ή έχει μια έκδοση community‑edition που λειτουργεί τέλεια για εκπαιδευτικούς σκοπούς.

## Βήμα 1 – Ρύθμιση του Maven Project σας

Για γρήγορη δημιουργία **create word document java** έργων, ξεκινήστε με ένα ελάχιστο Maven `pom.xml`. Αυτό το αρχείο εισάγει τη βιβλιοθήκη Aspose.Words και οποιονδήποτε HTTP client προτιμάτε (θα χρησιμοποιήσουμε Apache HttpClient).

```xml
<!-- pom.xml -->
<project xmlns="http://maven.apache.org/POM/4.0.0" 
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 
                             http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>word-llm-demo</artifactId>
    <version>1.0.0</version>
    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- Aspose.Words for Java -->
        <dependency>
            <groupId>com.aspose</groupId>
            <artifactId>aspose-words</artifactId>
            <version>24.9</version> <!-- replace with the latest -->
        </dependency>

        <!-- Apache HttpClient for calling the LLM endpoint -->
        <dependency>
            <groupId>org.apache.httpcomponents.client5</groupId>
            <artifactId>httpclient5</artifactId>
            <version>5.2</version>
        </dependency>
    </dependencies>
</project>
```

> **Συμβουλή:** Αν χρησιμοποιείτε Gradle, οι ίδιες εξαρτήσεις πηγαίνουν κάτω από `implementation` στο `build.gradle`.

Τώρα εκτελέστε `mvn clean install` για να κατεβάσετε τα jars. Μόλις η κατασκευή ολοκληρωθεί επιτυχώς, είστε έτοιμοι να γράψετε κώδικα Java που **creates word document java** αρχεία.

## Βήμα 2 – Γράψτε την Κλάση Java που **Creates word document java**

Παρακάτω βρίσκεται το πλήρες, έτοιμο‑για‑εκτέλεση αρχείο πηγής. Δείχνει ολόκληρη τη ροή: αρχικοποίηση ενός κεντρικού εγγράφου, διαμόρφωση προσαρμοσμένου endpoint LLM, εκτέλεση ελέγχου γραμματικής, και τελικά αποθήκευση του αποτελέσματος.

```java
package com.example.wordllmdemo;

import com.aspose.words.*;
import com.aspose.words.ai.*;

import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;

/**
 * Demonstrates how to create a Word document in Java and run a grammar‑check
 * using a self‑hosted LLM (e.g., Ollama). This example is fully self‑contained
 * and can be executed with a single `java -cp` command after Maven builds.
 */
public class SelfHostedLLMDemo {

    public static void main(String[] args) throws Exception {
        // -----------------------------------------------------------------
        // Step 2.1 – Create an empty Word document
        // -----------------------------------------------------------------
        Document document = new Document(); // this is the object that will become your .docx

        // Add a simple paragraph so the grammar engine has something to work with
        DocumentBuilder builder = new DocumentBuilder(document);
        builder.writeln("Ths sentence has a typo and a grammer error.");

        // -----------------------------------------------------------------
        // Step 2.2 – Configure the custom LLM endpoint (use custom llm)
        // -----------------------------------------------------------------
        AiEndpoint llmEndpoint = new AiEndpoint();
        llmEndpoint.setBaseUrl("http://localhost:11434/api/generate");
        llmEndpoint.setModel("llama3.1:8b"); // make sure this model is available locally

        // Initialise the Document AI engine with the endpoint we just set up
        DocumentAi documentAi = new DocumentAi(llmEndpoint);

        // -----------------------------------------------------------------
        // Step 2.3 – Run grammar checking (how to check grammar)
        // -----------------------------------------------------------------
        // AiModelType.CUSTOM tells the API to forward the request to our LLM
        documentAi.checkGrammar(document, AiModelType.CUSTOM);

        // -----------------------------------------------------------------
        // Step 2.4 – Save the corrected file
        // -----------------------------------------------------------------
        String outputPath = "output/GrammarChecked.docx";
        // Ensure the directory exists
        Files.createDirectories(Path.of("output"));
        document.save(outputPath);
        System.out.println("Document saved to " + outputPath);
    }
}
```

> **Γιατί λειτουργεί αυτό:**  
> * `Document` είναι η κύρια κλάση Aspose.Words που αντιπροσωπεύει ένα *.docx* στη μνήμη.  
> * `AiEndpoint` λέει στο AI module του Aspose πού να στείλει το prompt. Κατευθύνοντάς το στο `localhost:11434` εμείς **use custom llm** αντί για υπηρεσία cloud.  
> * `checkGrammar` με `AiModelType.CUSTOM` προωθεί το κείμενο του εγγράφου στο LLM, λαμβάνει διορθωμένο κείμενο και ξαναγράφει τους υποκείμενους κόμβους Word.  
> * Τέλος, καλούμε `save` για να γράψουμε το αρχείο στο δίσκο, παρέχοντάς σας ένα τελειοποιημένο αρχείο Word.

### Αναμενόμενο Αποτέλεσμα

Αφού εκτελέσετε `mvn exec:java -Dexec.mainClass="com.example.wordllmdemo.SelfHostedLLMDemo"` θα πρέπει να δείτε:

```
Document saved to output/GrammarChecked.docx
```

Ανοίξτε το παραγόμενο `GrammarChecked.docx` στο Microsoft Word (ή LibreOffice). Η αρχική πρόταση *«Ths sentence has a typo and a grammer error.»* θα γίνει τώρα *«This sentence has a typo and a grammar error.»* – απόδειξη ότι το βήμα **how to check grammar** ολοκληρώθηκε.

## Βήμα 3 – Πώς να δημιουργήσετε docx με διαφορετικό περιεχόμενο (Προαιρετικό)

Αν θέλετε να δημιουργήσετε πιο πλούσια έγγραφα—πίνακες, εικόνες ή μορφοποιημένο κείμενο—απλώς συνεχίστε να χρησιμοποιείτε `DocumentBuilder`. Εδώ είναι ένα σύντομο απόσπασμα που δείχνει την προσθήκη μιας επικεφαλίδας και ενός πίνακα:

```java
// Adding a heading
builder.getParagraphFormat().setStyleIdentifier(StyleIdentifier.HEADING_1);
builder.writeln("Demo Report");

// Adding a 2x2 table
Table table = builder.startTable();
builder.insertCell();
builder.write("Item");
builder.insertCell();
builder.write("Quantity");
builder.endRow();

builder.insertCell();
builder.write("Apples");
builder.insertCell();
builder.write("42");
builder.endRow();
builder.endTable();
```

Μπορείτε να ενσωματώσετε αυτόν τον κώδικα οπουδήποτε μεταξύ του μπλοκ δημιουργίας εγγράφου (Βήμα 2.1) και της κλήσης ελέγχου γραμματικής (Βήμα 2.3). Το LLM θα λάβει ακόμη ολόκληρο το κείμενο, ώστε να μπορεί να διορθώσει τυχόν τμήματα φυσικής γλώσσας ενώ οι πίνακες θα παραμείνουν αμετάβλητοι.

## Βήμα 4 – Αντιμετώπιση Προβλημάτων Endpoint (Χρήση Custom LLM με Ασφάλεια)

Κατά τη χρήση **using custom llm** endpoints, μερικά προβλήματα είναι συχνά:

| Σύμπτωμα | Πιθανή αιτία | Διόρθωση |
|---------|--------------|-----|
| `Connection refused` σφάλμα | Ο διακομιστής LLM δεν εκτελείται ή λάθος θύρα | Ξεκινήστε το Ollama (`ollama serve`) και επαληθεύστε ότι το `http://localhost:11434/api/generate` λειτουργεί με `curl`. |
| Απάντηση JSON χωρίς πεδίο `completion` | Ασυμφωνία ονόματος μοντέλου | Βεβαιωθείτε ότι το μοντέλο που έχετε ορίσει (`llama3.1:8b`) είναι εγκατεστημένο (`ollama list`). |
| Ο έλεγχος γραμματικής επιστρέφει το αρχικό κείμενο αμετάβλητο | Το prompt δεν αναγνωρίζεται από το LLM | Ρυθμίστε το σύστημα του μοντέλου |

{{< /blocks/products/pf/tutorial-page-section >}}
{{< /blocks/products/pf/main-container >}}
{{< /blocks/products/pf/main-wrap-class >}}
{{< blocks/products/products-backtop-button >}}