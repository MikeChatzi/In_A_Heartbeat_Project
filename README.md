# In_A_Heartbeat_Project
Connecting Arduino's Light Sensor with Supercollider

This project was presented in the forest of Mon Repo, Corfu, at the World Environment Day, 22/6/5. 

Description:
This project is a drawing of nature "sensitive" to light. Half of it is beautiful and the other half is destroyed. Adjusting an Arduino circuit behind the drawing and then connecting it to Supercollider, the project "In a heartbeat", while holding a light-type object, gives you the appropriate sound effect for each situation. What do we prefer? Our nature with many colors or our nature destroyed?

In this repository you will find: 

1. The Supercollider document (.scd) used at the World Environment Day, 22/6/5. Mac Version of the code. Code contains: 
  a) how to connect Supercollider to the Arduino's circuit through a port, 
  b) how to create a Routine that collects the light sensor's data and stores the clean values of it to a variable, 
  c) how to use a wav and connect it to a synth-also the synths used for the purposes of this project,  
  d) how to connect a parameter of your synths with the variable that has the light sensor's data stored so that it changes its value dynamically. 
  (the values used in this part of the code are specifically made to kind of calibrate the result depending on the ambient light of the place this project was set) 
  
2. The Arduino's circuit source code for reading and printing the light sensor's data. (.java)

3. This README file. Link to a youtube video of the project's testing: https://www.youtube.com/shorts/BA71W2jvxu4

4. This README file. Explanation in greek language. 

Περιγραφή. 
Το συγκεκριμένο project είναι μια ζωγραφιά της φύσης "ευαίσθητη" προς το φως. Η μισή είναι όμορφη και ανθισμένη, η άλλη μισή είναι άσχημη και κατεστραμμένη. Τοποθετώντας πίσω από τη ζωγραφιά μια κατασκευή Arduino με light sensor και συνδέοντας το Arduino με το Supercollider στον υπολογιστή, το "In a heartbeat" καταφέρνει, εξετάζοντας τη
φωτογραφία με μία λάμπα (φως - φακό), να αποδώσει ηχητικά το αντίστοιχο αποτέλεσματων δύο αυτών περιπτώσεων. Τι προτιμάμε;
Τη φύση μας πολύχρωμη ή τη φύση μας καμμένη;

Υλοποίηση/Τεχνικά.
Για το Arduino: Αρχικά, χρησιμοποιήσαμε το Arduino Uno και κάναμε μια απλή συνδεσμολογία με έναν αισθητήρα φωτός και μια αντίσταση. Το συνδέσαμε με τον υπολογιστή και έπειτα ανοίξαμε το Arduino IDE για να γράψουμε τον απλό κώδικα που υπάρχει στο repository στο αρχείο .java
Εξήγηση:
Πρώτα δηλώνουμε έναν integer για να δέχεται τις τιμές του αισθητήρα. Μέσα στο void setup δηλώνουμε το serial number επικοινωνίας. Πρέπει το port που θα δηλώσουμε εδώ να είναι πάντα το ίδιο για να υπάρχει επικοινωνία. Επιπλέον, όσο πιο μεγάλος ο αριθμός του port τόσο πιο “ευαίσθητο”, δηλαδή πιο αποδοτικό, θα είναι και το τελικό αποτέλεσμα αυτού του project. (σχέση επικοινωνίας με το Supercollider, χρήση port 115200) Στη συνέχεια, στο void loop (επανάληψη) κάνουμε τον integer που δηλώνουμε στην αρχή να διαβάζει τιμές από το Α0 της πλακέτας του Arduino και του ζητάμε να τις τυπώνει. Ιδιαίτερο στοιχείο, μετά από κάθε τύπωση της τιμής του αισθητήρα, του ζητάμε να μας τυπώνει και το γράμμα ‘α’. Αυτό θα μας βοηθήσει στο κώδικα του Supercollider να ξεχωρίσουμε την κάθε τιμή από την επομένη και την προηγούμενη της για να τις χρησιμοποιήσουμε επιτυχώς. Τέλος, βάζουμε μερικό delay για τις επαναλήψεις ως συνήθως.

Για το Supercollider:
Όταν φορτώσουμε τον κώδικα στη πλακέτα, κλείνουμε το Arduino IDE και ανοίγουμε το Supercollider χωρίς να αποσυνδέσουμε τη πλακέτα από τη θύρα. Μέσα στο Supercollider του λέμε να συνδεθεί με τη θύρα που είναι το Arduino και να διαβάσει αυτά που στέλνει. Προσέχουμε ο αριθμός του port να είναι ίδιος με αυτόν που δηλώσαμε και στο serial του κώδικα του Arduino. Στη συνέχεια, δημιουργούμε μια ρουτίνα (αντίστοιχη διαδικασία επανάληψης) όπου μια μεταβλητή θα δέχεται τις τιμές που στέλνει το Arduino και όπως είδαμε και στο κώδικα του, θα λαμβάνει πρώτα τη τιμή του αισθητήρα και ύστερα το γράμμα ‘α’. Έτσι, η συγκεκριμένη μεταβλητή θα ξεχωρίζει τη προσωρινή τιμή του αισθητήρα από το ‘α’ και θα στέλνει σε μια νέα μεταβλητή την καθαρή πλέον τιμή του αισθητήρα τη κάθε στιγμή. Αν δε βάζαμε τη γραμμή του κώδικα με το ‘α’, το Supercollider θα δεχόταν συνεχόμενα τις τιμές του αισθητήρα χωρίς να μπορεί να τις ξεχωρίσει. Ατελείωτα νούμερα στη σειρά. Για να προχωρήσουμε στη μετάφραση των τιμών σε ήχο, δημιουργούμε synth μέσα στο Supercollider. Μόλις δηλώσουμε τις παραμέτρους του, επιλέγουμε όποια θέλουμε αναλόγως με το επιθυμητό αποτέλεσμα και τη συνδέουμε με τη δεύτερη μεταβλητή που δημιουργήσαμε πιο πάνω, η οποία κρατάει τις καθαρές τιμές του αισθητήρα. Έτσι, και πάλι στα πλαίσια μιας ρουτίνας, κάνουμε τη συγκεκριμένη παράμετρο του synth να δέχεται δυναμικά τις τιμές που στέλνει το Arduino με αποτέλεσμα την συνεχόμενη ηχητική παραλλαγή της.

Ιδέα/Συμπεράσματα.
Αποφάσισα να αξιοποιήσω τη παραπάνω συνδεσμολογία με αισθητήρα φωτός στα πλαίσια της ημέρας περιβάλλοντος. Έτσι, έφτιαξα μια κατασκευή όπου μέσα σε ένα κουτί βρίσκεται η πλακέτα με τον αισθητήρα. Από πάνω της είναι μια λευκή κόλλα για να το καλύπτει και να μη φαίνεται στο background της κατασκευής. Στο πιο πάνω μέρος του κουτιού είναι περασμένη μια διαφανής μεμβράνη όπου είναι ζωγραφισμένο ένα τοπίο. Το τοπίο όπως αναφέρω και στη περιγραφή στην αρχή, έχει στη μέση ένα δέντρο το οποίο από τη μια μεριά είναι ανθισμένο ενώ από την άλλη είναι νεκρό. Τις δύο μεριές γεμίζουν στο πίσω μέρος εικόνες από ζωή/φύση και τσιμέντο/καυσαέρια αντίστοιχα. Το Arduino είναι τοποθετημένο πίσω από τη νεκρή μεριά της κατασκευής. Για το λόγο αυτό κατά τη δημιουργία των synths στο Supercollider υπολόγιζα πως πρέπει οι υψηλές τιμές να αντιπροσωπεύουν ηχητικά την νεκρή μεριά. Τα synths που επέλεξα να δημιουργήσω στο Supercollider είναι αυτά ενός χτύπου/θυμίζει καρδιά και ενός άλλου πιο γενικότερου ήχου-synth. Επιπλέον, φόρτωσα και δυο wav αρχεία, ένα από ήχους φύσης/πουλιών και ένα ακόμα από ήχους βιομηχανίας, μηχανημάτων κτλ Το τελικό ηχητικό αποτέλεσμα είναι πως όταν ο θεατής κρατάει τη λάμπα και σημαδεύει τη χρωματιστή μεριά, ακούγεται ένας ήρεμος γενικός ήχος μαζί με ήρεμη επανάληψη του χτύπου και ταυτόχρονα ακούγονται τα πουλάκια/φύση. Όταν όμως πηγαίνει τη λάμπα στη γκρι μεριά, τότε όλα αγριεύουν. Το γενικό synth γίνεται πιο έντονο, ο παλμός του χτύπου αυξάνεται, τα πουλάκια χάνονται και ταυτόχρονα εμφανίζεται ο ήχος των μηχανημάτων. Για να δουλέψει το όλο έργο, ο θεατής αρκεί να πάρει μια λάμπα και να εξετάσει πρώτα τη μια μεριά και ύστερα την άλλη. Καθώς η λάμπα θα κινείται πιο κοντά ή πιο μακριά από τον αισθητήρα, αυτό θα έχει και το ανάλογο ηχητικό αποτέλεσμα. Επιθυμία μου με τη κατασκευή του συγκεκριμένου project ήταν να ευαισθητοποιηθεί ο θεατής και επισκέπτης στο χώρο του Μον Ρεπο ως προς το ζήτημα του καθαρού και υγιούς μας περιβάλλοντος.

Βιβλιογραφία.
"_A Gentle Introduction to SuperCollider_", Bruno Ruviaro, 2014
