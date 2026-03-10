# Lab 7 — Kotlin Nullability : !! et ?:

## Description

Ce TP consiste à développer une application simple en **Kotlin** permettant de rechercher des étudiants dans une liste prédéfinie.

Le programme fonctionne en **mode console** et permet d’effectuer deux types de recherche :

- Recherche d’un étudiant par **ID**
- Recherche d’un étudiant par **nom**

L'application utilise plusieurs concepts fondamentaux du langage **Kotlin**, notamment :

- les **data classes**
- les **collections (List)**
- les **fonctions**
- la **lecture des entrées utilisateur**
- la **recherche dans une liste**

---

# Objectifs du TP

Les objectifs de ce laboratoire sont :

- Comprendre l'utilisation des **data class**
- Manipuler les **collections**
- Utiliser la fonction **find()**
- Interagir avec l'utilisateur via la **console**
- Gérer les cas où un étudiant n'est pas trouvé

---

# Structure du projet

```
lab7/
│
├── lab7.kt
└── lab7.jar
```

- **lab7.kt** : code source du programme Kotlin  
- **lab7.jar** : application compilée exécutable

---

# Code source du programme

```kotlin
data class Student(val fullName: String, var id: Int, var grade: Double)

val students = listOf(
    Student("John", 223, 140.0),
    Student("Mark", 548, 120.0),
    Student("Natali", 342, 150.0),
    Student("Sara", 781, 130.0)
)

fun getStudentById(id: Int): Student? {
    return students.find { it.id == id }
}

fun searchInStudents(name: String): Student? {
    return students.find { it.fullName.equals(name, ignoreCase = true) }
}

fun main() {

    println("Please, Enter the student's ID")
    val id = readLine()!!.toInt()

    println(getStudentById(id) ?: "the student is not found")

    println("Please, Enter the student's name")
    val name = readLine()!!

    println(searchInStudents(name) ?: "the student is not found")
}
```

---

# Explication du code

## 1. Data Class Student

La classe `Student` représente un étudiant avec trois attributs :

- **fullName** : nom complet de l'étudiant
- **id** : identifiant de l'étudiant
- **grade** : note de l'étudiant

L'utilisation de **data class** permet à Kotlin de générer automatiquement :

- `toString()`
- `equals()`
- `hashCode()`

---

## 2. Liste des étudiants

La liste suivante contient plusieurs étudiants :

```kotlin
val students = listOf(
    Student("John", 223, 140.0),
    Student("Mark", 548, 120.0),
    Student("Natali", 342, 150.0),
    Student("Sara", 781, 130.0)
)
```

Cette liste est une **collection immuable** créée avec `listOf()`.

---

## 3. Recherche par ID

La fonction suivante permet de rechercher un étudiant à partir de son identifiant :

```kotlin
fun getStudentById(id: Int): Student? {
    return students.find { it.id == id }
}
```

La fonction **find()** parcourt la liste et retourne le premier élément correspondant.

Si aucun étudiant n'est trouvé, la fonction retourne **null**.

---

## 4. Recherche par nom

La fonction suivante permet de rechercher un étudiant par son nom :

```kotlin
fun searchInStudents(name: String): Student? {
    return students.find { it.fullName.equals(name, ignoreCase = true) }
}
```

La comparaison utilise **ignoreCase = true** afin d’ignorer les différences entre majuscules et minuscules.

---

## 5. Fonction principale

La fonction `main()` est le point d'entrée du programme.

Elle réalise les étapes suivantes :

1. Demande à l'utilisateur de saisir un **ID**
2. Recherche l'étudiant correspondant
3. Affiche le résultat
4. Demande ensuite un **nom**
5. Recherche l'étudiant correspondant
6. Affiche le résultat

Si aucun étudiant n'est trouvé, le message suivant s'affiche :

```
the student is not found
```

---

# Compilation du programme

Pour compiler le programme Kotlin et créer un fichier **JAR exécutable** :

```bash
kotlinc lab7.kt -include-runtime -d lab7.jar
```

---

# Exécution du programme

Pour lancer l'application :

```bash
java -jar lab7.jar
```

---

# Exemple d'exécution

```
Please, Enter the student's ID
223
Student(fullName=John, id=223, grade=140.0)

Please, Enter the student's name
Sara
Student(fullName=Sara, id=781, grade=130.0)
```

---

# Concepts Kotlin utilisés

Ce TP utilise plusieurs concepts importants :

- **data class**
- **List**
- **find()**
- **readLine()**
- **types nullable**
- **Elvis operator (?:)**


# Auteur

Ait Hmad Oussama
