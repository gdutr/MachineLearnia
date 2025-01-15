Les exercices ont été réalisés à l'aide de l'outil bac à sable SQL -> [lien](https://tchou.github.io/sqlsb/?lang=fr)

# Exercice 1 : Création des tables
## Enoncé
1. Livres (LivreID, Titre, AuteurID, GenreID, DatePublication, Disponible)
2. Auteurs (AuteurID, Nom, Prénom, Pays)
3. Genres (GenreID, NomGenre)
4. Emprunteurs (EmprunteurID, Nom, Prénom, Email, Téléphone)
5. Emprunts (EmpruntID, LivreID, EmprunteurID, DateEmprunt, DateRetourPrévue, DateRetourEffective)
___

### 1. <ins> Livres</ins> (LivreID, Titre, AuteurID, GenreID, DatePublication, Disponible) :
``` SQL
CREATE TABLE Livres(
    LivreID INT PRIMARY KEY, 
    Titre VARCHAR(100), 
    AuteurID INT, 
    GenreID INT,  
    DatePublication DATE, 
    Disponible BOOL,
    FOREIGN KEY (AuteurID) REFERENCES Auteur(AuteurID), 
    FOREIGN KEY (GenreID) REFERENCES Genres(GenreID)
);
```
### 2. Auteurs (AuteurID, Nom, Prénom, Pays)
```SQL
CREATE TABLE Auteurs(
    AuteurID INT PRIMARY KEY,
    Nom VARCHAR(100),
    Prénom VARCHAR(100),
    Pays VARCHAR(100)
);
```
### 3. Genres (GenreID, NomGenre)
```SQL
CREATE TABLE Genres(
    GenreID INT PRIMARY KEY,
    NomGenre VARCHAR(100) 
);
```

### 4. Emprunteurs (EmprunteurID, Nom, Prénom, Email, Téléphone)
```SQL
CREATE TABLE Emprunteurs(
    EmprunteurID INT PRIMARY KEY,
    Nom VARCHAR(100),
    Prénom VARCHAR(100),
    Email VARCHAR(100),
    Téléphone VARCHAR(100)
);
```

### 5. Emprunts (EmpruntID, LivreID, EmprunteurID, DateEmprunt, DateRetourPrévue, DateRetourEffective)

```SQL
CREATE TABLE Emprunts(
    EmpruntID INT PRIMARY KEY,
    LivreID INT,
    EmprunteurID INT,
    DateEmprunt DATE,
    DateRetourPrévue DATE,
    DateRetourEffective DATE,
    FOREIGN KEY (LivreID) REFERENCES Livres(LivreID),
    FOREIGN KEY (EmprunteurID) REFERENCES Emprunteurs(EmprunteurID)
);
```

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

 # Exercice 2 : Insérer des données
 <ins> Code pour insérer les données :</ins>

 ```SQL
 INSERT INTO Auteurs (AuteurID, Nom, Prénom, Pays) VALUES
(1, 'Hugo', 'Victor', 'France'),
(2, 'Orwell', 'George', 'Royaume-Uni'),
(3, 'Asimov', 'Isaac', 'Russie'),
(4, 'Tolkien', 'J.R.R.', 'Royaume-Uni'),
(5, 'Austen', 'Jane', 'Royaume-Uni'),
(6, 'Dumas', 'Alexandre', 'France'),
(7, 'Bradbury', 'Ray', 'États-Unis'),
(8, 'Camus', 'Albert', 'France'),
(9, 'Verne', 'Jules', 'France'),
(10, 'Hemingway', 'Ernest', 'États-Unis');


INSERT INTO Genres (GenreID, NomGenre) VALUES
(1, 'Roman'),
(2, 'Science-fiction'),
(3, 'Fantasy'),
(4, 'Classique'),
(5, 'Philosophie'),
(6, 'Aventure'),
(7, 'Horreur'),
(8, 'Biographie');


INSERT INTO Livres (LivreID, Titre, AuteurID, GenreID, DatePublication, Disponible) VALUES
(1, 'Les Misérables', 1, 1, '1862-01-01', TRUE),
(2, '1984', 2, 2, '1949-06-08', FALSE),
(3, 'Fondation', 3, 2, '1951-01-01', TRUE),
(4, 'Le Seigneur des Anneaux', 4, 3, '1954-07-29', TRUE),
(5, 'Orgueil et Préjugés', 5, 4, '1813-01-28', TRUE),
(6, 'Le Comte de Monte-Cristo', 6, 6, '1844-08-28', TRUE),
(7, 'Fahrenheit 451', 7, 2, '1953-10-19', TRUE),
(8, 'L’Étranger', 8, 5, '1942-01-01', FALSE),
(9, 'Vingt mille lieues sous les mers', 9, 6, '1870-06-20', TRUE),
(10, 'Le Vieil Homme et la Mer', 10, 4, '1952-09-01', FALSE),
(11, 'Les Trois Mousquetaires', 6, 6, '1844-03-14', TRUE),
(12, 'Le Château', NULL, 4, '1926-01-01', TRUE);


INSERT INTO Emprunteurs (EmprunteurID, Nom, Prénom, Email, Téléphone) VALUES
(1, 'Dupont', 'Jean', 'jean.dupont@mail.com', '0601020304'),
(2, 'Martin', 'Lucie', 'lucie.martin@mail.com', '0602030405'),
(3, 'Bernard', 'Paul', 'paul.bernard@mail.com', '0603040506'),
(4, 'Durand', 'Sophie', 'sophie.durand@mail.com', '0604050607'),
(5, 'Lefevre', 'Antoine', NULL, '0605060708'),
(6, 'Roux', 'Marie', 'marie.roux@mail.com', '0606070809'),
(7, 'Moreau', 'Julie', 'julie.moreau@mail.com', '0607080910'),
(8, 'Petit', 'Nicolas', 'nicolas.petit@mail.com', '0608091011'),
(9, 'Girard', 'Laure', 'laure.girard@mail.com', '0609101112'),
(10, 'Andre', 'Thomas', 'thomas.andre@mail.com', NULL),
(11, 'Lam', 'Marc', 'marc.lam@mail.com', '0609101113')
;


INSERT INTO Emprunts (EmpruntID, LivreID, EmprunteurID, DateEmprunt, DateRetourPrévue, DateRetourEffective) VALUES
(1, 1, 1, '2024-10-10', '2024-10-17', NULL),
(2, 2, 2, '2024-10-11', '2024-10-18', '2024-10-13'),
(3, 3, 3, '2024-10-12', '2024-10-19', NULL),
(4, 4, 4, '2024-10-13', '2024-10-20', '2024-10-17'),
(5, 5, 5, '2024-10-14', '2024-10-21', NULL),
(6, 6, 6, '2024-10-15', '2024-10-22', '2024-10-20'),
(7, 7, 7, '2024-10-16', '2024-10-23', NULL),
(8, 8, 8, '2024-10-17', '2024-10-24', '2024-10-28'),
(9, 9, 9, '2024-10-18', '2024-10-25', NULL),
(10, 5, 10, '2024-10-19', '2024-10-26', NULL),
(11, 11, 1, '2024-10-20', '2024-10-27', '2024-10-25'),
(12, 7, 2, '2024-10-21', '2024-10-28', NULL),
(13, 8, 3, '2024-10-22', '2024-10-29', NULL),
(15, 1, 5, '2024-10-24', '2024-10-31', NULL),
(16, 4, 6, '2024-10-25', '2024-11-01', NULL),
(17, 9, 7, '2024-10-26', '2024-11-02', NULL);
 ```

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

 # Exercice 3 : Sélectionner les Livres Disponibles
<ins>Enoncé</ins> : Écrivez une requête pour récupérer tous les livres disponibles.

 Code :
```SQL
SELECT Titre FROM Livres
WHERE Disponible = 1
```

Résultat :

  
|  | Titre                       |
|---|:----------------------------:|
| 0 | Les Misérables              |
| 1 | Fondation                   |
| 2 | Le Seigneur des Anneaux     |
| 3 | Orgueil et Préjugés         |
| 4 | Le Comte de Monte-Cristo    |
| 5 | Fahrenheit 451              |
| 6 | Vingt mille lieues sous les mers |
| 7 | Les Trois Mousquetaires     |
| 8 | Le Château                  |

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 4 : Trier les Livres par Date de Publication
<ins>Enoncé</ins> : Trier les Livres par Date de Publication

Code :
```SQL
SELECT Titre, DatePublication FROM Livres
ORDER BY DatePublication ASC
```
Resultat :

|  |Titre|	DatePublication |
|:-|:---:|:----------------:|
|0|	Orgueil et Préjugés|	1813-01-28
|1|	Les Trois Mousquetaires|	1844-03-14
|2|	Le Comte de Monte-Cristo|	1844-08-28
|3|	Les Misérables|	1862-01-01
|4|	Vingt mille lieues sous les mers|	1870-06-20
|5|	Le Château|	1926-01-01
|6|	L’Étranger|	1942-01-01
|7|	1984|	1949-06-08
|8|	Fondation|	1951-01-01
|9|	Le Vieil Homme et la Mer|	1952-09-01
|10|	Fahrenheit 451|	1953-10-19
|11|	Le Seigneur des Anneaux|	1954-07-29

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 5 : Filtrer les Emprunts en Cours
<ins>Enoncé</ins> : Écrivez une requête pour récupérer les emprunts dont la DateRetourEffective est encore NULL, ce qui signifie que le livre n’a pas encore été rendu.

Code :
```SQL
SELECT Livres.Titre, Emprunts.DateRetourEffective
FROM Livres
LEFT JOIN Emprunts ON Emprunts.LivreID = Livres.LivreID
WHERE Emprunts.DateRetourEffective IS NULL
```

Resultat :
||	Titre|	DateRetourEffective |
|:-:|:--:|:---------------------:|
|0	|Les Misérables|	null
|1	|Les Misérables|	null
|2	|Fondation|	null
|3	|Le Seigneur des Anneaux|	null
|4	|Orgueil et Préjugés|	null
|5	|Orgueil et Préjugés|	null
|6	|Fahrenheit 451	|null
|7	|Fahrenheit 451	|null
|8	|L’Étranger	|null
|9	|Vingt mille lieues sous les mers|	null
|10	|Vingt mille lieues sous les mers|	null
|11	|Le Vieil Homme et la Mer|	null
|12|	Le Château|	null

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 6 : Calculer la Durée d'un Emprunt
<ins>Enoncé</ins> : Écrivez une requête pour calculer la durée (en jours) entre la date d'emprunt et la date de retour effective pour chaque emprunt, et nommez cette nouvelle colonne DureeEmprunt.

Code :

```SQL
SELECT L.Titre,julianday(DateRetourEffective) - julianday(DateEmprunt) AS 'Durée emprunt' FROM Emprunts AS E
LEFT JOIN Livres AS L ON L.LivreID = E.LivreID
WHERE DateRetourEffective NOT NULL
```

Résultat :

||Titre|	Durée emprunt|
|:-:|:-:|:-:|
|0|	1984|	2|
|1|	Le Seigneur des Anneaux|	4|
|2|	Le Comte de Monte-Cristo|	5|
|3|	L’Étranger|	11|
|4|	Les Trois Mousquetaires|	5|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 7 : Jointure sur les Livres et les Auteurs

<ins> Enoncé</ins> : Écrivez une requête SQL pour afficher le titre des livres ainsi que le nom complet (Nom et Prénom) de leur auteur. Je veux afficher un livre même s'il n'a pas d'auteur connu, par contre je ne veux pas afficher les auteurs qui n'ont pas de livre dans la base.

```SQL
SELECT L.Titre, A.Prénom, A.Nom FROM Livres AS L
LEFT JOIN Auteurs AS A ON L.AuteurID = A.AuteurID
```

Résultat :

||	Titre|	Prénom|	Nom|
|:-:|:-:|:-:|:-:|
|0|	Les Misérables|	Victor|	Hugo|
|1|	1984|	George|	Orwell|
|2|	Fondation	|Isaac|	Asimov|
|3|	Le Seigneur des Anneaux|	J.R.R.	|Tolkien|
|4|	Orgueil et Préjugés	| Jane	|Austen|
|5|	Le Comte de Monte-Cristo|	Alexandre|	Dumas|
|6|	Fahrenheit 451	|Ray	|Bradbury|
|7|	L’Étranger|	Albert	|Camus|
|8|	Vingt mille lieues sous les mers|	Jules|	Verne|
|9|	Le Vieil Homme et la Mer|	Ernest|	Hemingway|
|10|	Les Trois Mousquetaires|	Alexandre|	Dumas|
|11|	Le Château	|null	|null|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 8 : Filtrer les Emprunteurs qui n’ont pas encore rendu de livres
<ins> Enoncé</ins> : Utilisez une jointure pour afficher les informations des emprunteurs (Nom, Prénom, Email) qui n’ont pas encore rendu leurs livres (c’est-à-dire les emprunts où la date de retour effective est NULL).

Code :

```SQL
SELECT E.Prénom, E.Nom, E.Email, L.Titre
FROM Emprunteurs AS E
INNER JOIN Emprunts ON Emprunts.EmprunteurID = E.EmprunteurID
LEFT JOIN Livres AS L ON L.LivreID = Emprunts.LivreID
WHERE Emprunts.DateRetourEffective IS NULL
```

Résultat :

||Prénom|	Nom|	Email| Titre |
|:-:|:-:|:-:|:-:|:-:|
|0|	Jean|	Dupont|	jean.dupont@mail.com| Les Misérables|
|1|	Paul|	Bernard|	paul.bernard@mail.com|Fondation |
|2|	Antoine|	Lefevre|	null|Orgueil et Préjugés |
|3|	Julie|	Moreau|	julie.moreau@mail.com| Fahrenheit 451|
|4|	Laure|	 Girard |	laure.girard@mail.com| Vingt mille lieues sous les mers|
|5|	Thomas|	Andre|	thomas.andre@mail.com| Orgueil et Préjugés|
|6|	Lucie|	Martin|	lucie.martin@mail.com|Fahrenheit 451 |
|7|	Paul|	Bernard|	paul.bernard@mail.com|L’Étranger |
|8|	Antoine|	Lefevre|	null|Les Misérables |
|9|	Marie|	Roux|	marie.roux@mail.com| Le Seigneur des Anneaux|
|10|	Julie|	Moreau|	julie.moreau@mail.com|Vingt mille lieues sous les mers |

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 9 : Nombre de Livres par Genre

<ins>Enoncé</ins> : Écrivez une requête qui utilise une jointure pour afficher le nombre de livres par genre. Le résultat doit montrer le nom du genre et le nombre de livres associés.

Code :

```SQL
SELECT  G.NomGenre AS Genre, 
        COUNT(L.Titre) AS Quantité 
FROM Livres AS L
LEFT JOIN Genres AS G ON G.GenreID = L.GenreID
GROUP BY G.NomGenre
```

Résultat :

||	Genre|	Quantité|
|:-:|:-:|:-:|
|0|	Aventure	|3|
|1|	Classique	|3|
|2|	Fantasy	|1|
|3|	Philosophie	|1|
|4|	Roman	|1|
|5|	Science-fiction	|3|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 10 : Durée Moyenne d’Emprunt par Emprunteur
<ins>Enoncé</ins> : Calculez la durée moyenne des emprunts pour chaque emprunteur, et affichez leur nom et prénom ainsi que la durée moyenne en jours.

Code :

```SQL
SELECT  E.Prénom, E.Nom, 
        AVG(julianday(DateRetourEffective) - julianday(DateEmprunt)) AS 'Durée emprunt'
FROM Emprunteurs AS E
LEFT JOIN Emprunts ON Emprunts.EmprunteurID = E.EmprunteurID
WHERE DateRetourEffective IS NOT NULL
GROUP BY E.Prénom, E.Nom
```

Résultat :

||	Prénom|	Nom|	Durée emprunt|
|:-:|:---:|:--:|:---------------:|
|0|	Jean	|Dupont	|5|
|1|	Lucie	|Martin	|2|
|2|	Marie	|Roux	|5|
|3|	Nicolas	|Petit	|11|
|4|	Sophie	|Durand	|4|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 11 : Jointure avec Emprunteurs, Livres, et Genres
<ins>Enoncé</ins> : Affichez le nom et prénom de chaque emprunteur, le titre du livre emprunté et le genre de ce livre. Je veux voir tous les livres, même ceux qui n'ont pas été emprunté, ainsi que tous les Emprunteurs, même s'ils n'ont pas encore emprunté de livre et tous les genres, même s'il n'existe pas de livre pour ces genres.

Code :

```SQL
SELECT  E.Prénom,
        E.Nom,
        L.Titre,
        G.NomGenre
FROM Emprunts
FULL JOIN Emprunteurs AS E ON Emprunts.EmprunteurID = E.EmprunteurID
FULL JOIN Livres AS L ON L.LivreID = Emprunts.LivreID
FULL JOIN Genres AS G ON G.GenreID = L.GenreID
```

Résultat :

||Prénom|	Nom|	Titre|	NomGenre|
|:-:|:-:|:----:|:-------:|:--------:|
|0|	Jean|	Dupont|	Les Misérables|	Roman|
|1|	Lucie|	Martin|	1984|	Science-fiction|
|2|	Paul|	Bernard|	Fondation|	Science-fiction|
|3|	Sophie|	Durand|	Le Seigneur des Anneaux|	Fantasy|
|4|	Antoine|	Lefevre|	Orgueil et Préjugés|	Classique|
|5|	Marie|	Roux|	Le Comte de Monte-Cristo|	Aventure|
|6|	Julie|	Moreau|	Fahrenheit 451|	Science-fiction|
|7|	Nicolas|	Petit|	L’Étranger|	Philosophie|
|8|	Laure|	Girard|	Vingt mille lieues sous les mers|	Aventure|
|9|	Thomas|	Andre|	Orgueil et Préjugés|	Classique|
|10|	Jean|	Dupont|	Les Trois Mousquetaires|	Aventure|
|11|	Lucie|	Martin|	Fahrenheit 451|	Science-fiction|
|12|	Paul|	Bernard|	L’Étranger|	Philosophie|
|13|	Antoine|	Lefevre|	Les Misérables|	Roman|
|14|	Marie|	Roux|	Le Seigneur des Anneaux|	Fantasy|
|15|	Julie|	Moreau|	Vingt mille lieues sous les mers|	Aventure|
|16|	Marc|	Lam|	null|	null|
|17|	null|	null|	Le Vieil Homme et la Mer|	Classique|
|18|	null|	null|	Le Château|	Classique|
|19|	null|	null|	null|	Horreur|
|20|	null|	null|	null|	Biographie|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 12 : Livres les Plus Empruntés
<ins>Enoncé</ins> : Écrivez une requête SQL pour trouver les trois livres les plus empruntés. Affichez leur titre et le nombre d’emprunts.

Code :

```SQL
SELECT L.Titre, COUNT(L.Titre) AS 'Quantité' FROM Emprunts
LEFT JOIN Livres AS L ON L.LivreID = Emprunts.LivreID
GROUP BY L.Titre
ORDER BY COUNT(L.Titre) DESC
LIMIT 3
```

Résultat :

||	Titre|	Quantité|
|:-:|:-:|:-:|
|0|	Vingt mille lieues sous les mers|	2|
|1|	Orgueil et Préjugés	|2|
|2|	L’Étranger	|2|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 13 : Nombre de Livres Empruntés par Emprunteur

<ins>Enoncé</ins> : Écrivez une requête SQL pour afficher le nombre total de livres empruntés par chaque emprunteur. Le résultat doit inclure les emprunteurs qui n’ont jamais emprunté de livre.

Code : 

```SQL
SELECT E.Prénom, E.Nom, COUNT(Emprunts.EmpruntID) AS 'Quantité' 
FROM Emprunts
RIGHT JOIN Emprunteurs AS E ON E.EmprunteurID = Emprunts.EmprunteurID
GROUP BY E.Prénom, E.Nom
ORDER BY COUNT(Emprunts.EmpruntID) DESC
```

Résultat :

||Prénon	|Nom	|Quantité|
|:-:|:-:|:-:|:-----:|
|0|	Antoine	|Lefevre	|2|
|1|	Jean	|Dupont	|2|
|2|	Julie	|Moreau	|2|
|3|	Lucie	|Martin	|2|
|4|	Marie	|Roux	|2|
|5|	Paul	|Bernard|	2|
|6|	Laure	|Girard	|1|
|7|	Nicolas	|Petit	|1|
|8|	Sophie	|Durand	|1|
|9|	Thomas	|Andre	|1|
|10|	Marc|	Lam|	0|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 14 : Livres Jamais Empruntés

<ins>Enoncé</ins> : Écrivez une requête SQL pour afficher la liste des livres qui n’ont jamais été empruntés.

Code :

```SQL
SELECT Titre FROM Livres
LEFT JOIN Emprunts ON Emprunts.LivreID = Livres.LivreID
WHERE Emprunts.LivreID IS NULL
```
OU

```SQL
-- Avec sous-requête
SELECT Titre FROM Livres
WHERE Livres.LivreID NOT IN (SELECT LivreID FROM Emprunts)
```

Résultat :

||	Titre|
|:-:|:-:|
|0|	Le Vieil Homme et la Mer|
|1|	Le Château|

<div style="margin-top: 65px;"></div> <!-- Ajoute une marge verticale -->

# Exercice 15 : Nombre d’Emprunteurs par Auteur
<ins>Enoncé</ins> : Écrivez une requête SQL pour afficher le nombre total d’emprunteurs pour chaque auteur. Le résultat doit inclure les auteurs dont aucun livre n’a été emprunté.

Code :

```SQL
SELECT A.Prénom, A.Nom, COUNT(Emprunts.EmpruntID) AS 'Quantité'
FROM Auteurs AS A
LEFT JOIN Livres AS L ON L.AuteurID = A.AuteurID
LEFT JOIN Emprunts ON Emprunts.LivreID = L.LivreID
GROUP BY A.Prénom, A.Nom
```

Résultat :

|	|Prénom	|Nom	|Quantité|
|:-:|:-----:|:-----:|:------:|
|0	|Albert	|Camus	|2|
|1	|Alexandre	|Dumas	|2|
|2	|Ernest	|Hemingway	|0|
|3	|George	|Orwell	|1|
|4	|Isaac	|Asimov	|1|
|5	|J.R.R.	|Tolkien	|2|
|6	|Jane	|Austen	|2|
|7	|Jules	|Verne	|2|
|8	|Ray	|Bradbury	|2|
|9	|Victor	|Hugo	|2|