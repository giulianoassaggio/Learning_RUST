# Rust Language
## Appunti 2023.10.23
### Variabili
`let` è ciò che indica la creazione di una variabile. Indicare il tipo è opzionale, esso è dedotto in automatico dal compilatore al momento della inizializzazione.


`mut` indica che la variabile può essere modificata. Le variabili in Rust infatti by default sono immutabili (e allora cazzo le chiami "variabili"? Ndr). Quindi per renderle modificabili va aggiunto `mut` dopo di `let`:
```
let a = 0;    //immutabile
let mut a = 0    //mutabile
```
### Inclusione
Il corrispettivo di `#include` di C/++ è `use`.
### Funzioni statiche
Parto da un esempio. 
```
let mut esempio = String::new();
```
`new` è quello che in java sarebbe una funzione di tipo `static`: non è legata a una specifica istanza di un oggetto, ma è una funzione riferita alla classe. Questa caratteristica si vede dal doppio `::`, un po' come la visibilità di classi e namespaces di c++. È come se fosse un "appartiene a".
`new` è una funzione associata a vari tipi, ma **non è una parola chiave**, o comunque è solo il nome di una funzione. To summarize, the `let mut esempio = String::new();` line has created a mutable variable that is currently bound to a new, empty instance of a String.
### references
Esattamente come le variabili, le reference sono immutabili by default. Ciò significa che al passaggio come parametro di una reference non basta la `&`, ma bisogna specificare `&mut`.
### Metodi - convenzione
Qualora si intenda invocare un metodo (quindi una funzione preceduta da '.'), è buona norma andare a capo e indentare, per ogni "sottometodo". Per esempio:
```
io::stdin().read_line(&mut guess)
    .expect("Failed to read line");
```
Così da aumentarne la leggibilità e la chiarezza
### Result
Le funzioni di rust (come per esempio I/O) spesso hanno come ritorno un enum `{Ok, Err}`
Gli elementi dell'enum prendono il nome di variants. Il variant `Ok` contiene il valore correttamente generato e indica che l'espressione è stata eseguita con successo. `Err` indica invece che l'operazione è fallita e contiene indicazioni sull'errore.
È il metodo che rust ha scelto per handle gli errori: ogni Result ritornato ha dei metodi in esso definiti. Per esempio, un istanza di `io::Result` ha il metodo `.expect`. Se viene ritornato un Err, expect farà crashare tutto mostrando a video il messaggio messo in expect