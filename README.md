
Projecte inicial visible per a la practica integradora de RA1 del modul MP0486 - Acces a dades.

## Finalitat

Aquest starter serveix per treballar la gestio d'informacio en fitxers: rutes relatives, lectura, conversio de text a objectes, modificacio en memoria, escriptura, persistencia entre execucions i tractament d'errors.

No es una solucio completa. El treball de l'alumnat consisteix a evolucionar el projecte seguint el backlog RA1.

## Estructura

- `model`: classes de domini.
- `view`: interfície grafica Swing existent.
- `main`: coordinacio principal de l'aplicacio i menu de consola.
- `dao`: acces a dades basat en fitxers.
- `files`: dades de treball en text.

## Dades principals

- `files/users.txt`: usuaris per al login simulat.
- `files/items.txt`: productes inicials de la botiga.

Credencials de prova:

- usuari `1001`, contrasenya `admin`
- usuari `1002`, contrasenya `repair`

## Tasques esperades de RA1

El backlog indica quines parts s'han de completar, corregir o demostrar:

- lectura real de `items.txt`;
- conversio robusta de linies de text a `Product`;
- modificacio de l'inventari;
- guardat de l'inventari actualitzat;
- comprovacio de persistencia entre execucions;
- gestio de fitxer absent o linia mal formada;
- README i proves finals.

## Execucio

Requisits:

- JDK 25.
- Maven 3.9.x, si es vol compilar des de linia d'ordres.

Comandes utils:

```bash
mvn compile
```

Classe principal de consola:

```text
main.Shop
```

Classe principal grafica Swing:

```text
view.LoginView
```

## Limits RA1

Aquest projecte no utilitza JDBC, SQL, ORM, MongoDB, serveis externs ni bases de dades. La persistencia ha de quedar limitada a fitxers locals.

ISSUE 02:

I have verified that .txt files are located.

ISSUE 03:
I opened the file using a `try-with-resources` block to ensure it closes automatically, read it line by line, and set up the call to the `parseProductLine` method in preparation for the next issue.

- Read and process each line as text:
Using a `while` loop, we read the `items.txt` file from top to bottom,
line by line and sequentially, treating each line simply as a plain-text `String` without modifying it.
ISSUE 04:
I have verified the functionality of the `parseProductLine()` method using a  line from the `items.txt` file.
The method correctly extracts the item name, price, and stock, creates the corresponding `Product` object,
and adds it to the store's inventory.

ISSUE 05:

Robustness has been added to the `parseProductLine` method through a `try-catch` block and length validations.
This allows for the detection of malformed lines, enabling them to be ignored in a controlled manner while displaying a warning, 
without causing the application to close.

Issue 06 :
new function has been added to dynamically add new products via the console without needing to restart the application. 
The system performs step-by-step validation—ensuring that names are not duplicated and that both price and stock values ​​are numeric and logical—thereby preventing runtime errors. 
This ensures the robustness of the in-memory inventory before it is permanently saved to the file.