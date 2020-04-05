## Hello, World!

Ora che hai installato Rust, andiamo a scrivere il tuo primo programma Rust. 
quando si impara un nuovo linguaggio, è abitudine scrivere un piccolo programma
che scrive `Hello, world!` sullo schermo, quindi faremo la stessa cosa! 


> Nota: Questo libro presuppone una conoscenza basilare della linea dei comandi. 
> Rust non richiede requisiti specifici in merito alla modifica, agli strumenti o 
> alla posizione del codice, quindi se preferisci usare un IDE al posto della linea
> dei comandi, sentiti libero di usare il tuo IDE preferito. 
> Diversi IDE hanno diversi gradi di supporto di Rust; controlla i dettagli della
> documentazione dell'IDE per avere maggiori dettagli. Recentemente il team di Rust
> si è focalizzato su come attivare un buon supporto per gli IDE e sono stati fatti
> ottimi progressi in tal senso! 


### Creare una directory per i progetti

Inizierai creando una directory per conservare il tuo codice scritto in Rust. 
Non importa dove viene conservato il tuo codice, ma per gli esercizi e i progetti
di questo libro, noi consigliamo di creare una directory *progetti* nella tua
directory principale per conservare lì tutti i progetti. 

Apri un terminale ed esegui i seguenti comandi per creare una cartella *progetti*
e una directory per il progetto "Ciao, Mondo!" dentro la directory *progetti*. 

Per Linux, macOS, e PowerShell su Windows, scrivi questo:

```text
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Per Windows CMD, scrivi questo:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### Scrivere ed eseguire un programma Rust

Poi, crea un nuovo file e chiamalo *main.rs*. I file Rust finiscono sempre con
l'estensione *.rs*. Se usi più di una parola nel nome del tuo file, usa un 
trattino basso per separare le parole. Per esempio, utilizza *hello_world.rs*
al posto di *helloworld.rs*.

Ora apri il file *main.rs* che hai appena creato ed inserisci il codice come nell'esempio Listing 1-1.

<span class="filename">Filename: main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

<span class="caption">Listing 1-1: Un programma che scrive `Hello, world!`</span>

Salva il file e torna sulla finestra del tuo terminale. Su Linux o macOS, scrivi
i seguenti comandi per compilare ed eseguire il file:

```text
$ rustc main.rs
$ ./main
Hello, world!
```

Su Windows, scrivi il comando `.\main.exe` invece di `./main`:

```powershell
> rustc main.rs
> .\main.exe
Hello, world!
```

Indipendentemente dal sistema operativo che stai usando , la stringa "Hello, world!" 
dovrebbe essere scritta sul tuo terminale.
Se non vedi questo output, fai riferimento  alla sezione d'installazione per ricevere aiuto. 


Se sul terminale verrà scritto `Hello, world!`, congratulazioni! Hai ufficialmente scritto un 
programma Rust, questo fa di te uno sviluppatore Rust- Benvenuto! 

### Anatomia di un programma Rust 

Andiamo a vedere nel dettaglio cosa è appena successo nel tuo programma “Hello, world!”. 
Questo è il primo pezzo del puzzle:

```rust
fn main() {

}
```

Questa linea definisce una funzione in Rust. La funzione `main`è speciale: 
è il primo codice che viene eseguito in ogni programma Rust eseguibile. La prima
linea dichiara una funzione chiamata `main` che non ha parametri e non dà nulla indietro. 
Se ci fossero stati parametri, sarebbero stati inseriti tra le parentesi, `()`. 

Ancora, nota che il corpo della funzione è contenuto nelle parentesi graffe , `{}`. 
Rust le richiede nei corpi di tutte le funzioni. 
È consigliabile inserire l'apertura delle parentesi graffe nella stessa linea della dichiarazione della funzione, 
aggiungendo uno spazio tra di essi. 


Mentre stiamo scrivendo questo libro, un tool di formattazione automatico 
chiamato `rustfmt` è in fase di sviluppo. 
 If you want to stick to a standard style across Rust
projects, `rustfmt` will format your code in a particular style. The Rust team
plans to eventually include this tool with the standard Rust distribution, like
`rustc`. So depending on when you read this book, it might already be installed
on your computer! Check the online documentation for more details.

Dentro la funzione `main`c'è il seguente codice:

```rust
    println!("Hello, world!");
```

This line does all the work in this little program: it prints text to the
screen. There are four important details to notice here. First, Rust style is
to indent with four spaces, not a tab.

Second, `println!` calls a Rust macro. If it called a function instead, it
would be entered as `println` (without the `!`). We’ll discuss Rust macros in
more detail in Chapter 19. For now, you just need to know that using a `!`
means that you’re calling a macro instead of a normal function.

Third, you see the `"Hello, world!"` string. We pass this string as an argument
to `println!`, and the string is printed to the screen.

Fourth, we end the line with a semicolon (`;`), which indicates that this
expression is over and the next one is ready to begin. Most lines of Rust code
end with a semicolon.

### La compilazione e l'esecuzione sono due step separati

Hai appena eseguito un programma creato da poco, esaminiamo ogni step del processo. 

Prima di eseguire un programma scritto in Rust, devi compilarlo usando il compiler
di Rust scrivendo il comando `rustc` dandogli il nome del tuo file, cosi:

```text
$ rustc main.rs
```

If you have a C or C++ background, you’ll notice that this is similar to `gcc`
or `clang`. After compiling successfully, Rust outputs a binary executable.

On Linux, macOS, and PowerShell on Windows, you can see the executable by
entering the `ls` command in your shell. On Linux and macOS, you’ll see two
files. With PowerShell on Windows, you’ll see the same three files that you
would see using CMD.

```text
$ ls
main  main.rs
```

With CMD on Windows, you would enter the following:

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```
Questo mostra il codice sorgente del file con l'estensione *.rs*, il file
eseguibile (*main.exe* on Windows, ma *main* su tutte le altre piattaforme), 
e, quando si utilizza Windows, un file contenente le informazioni di debug 
con l'estensione *.pdb*. 
Da qui, tu esegui il file *main* or *main.exe*, come qui sotto:

```text
$ ./main # o .\main.exe su Windows
```

Se *main.rs* era il tuo programma “Hello, world!”, questa linea scriverà `Hello,
world!` sul tuo terminale.

Se hai familiarità con i linguaggi dinamici, come Ruby, Python o Javascript, 
potresti non essere abituato a compilare ed eseguire un programma in due
passaggi separati.
Rust is an *ahead-of-time compiled* language, meaning you can
compile a program and give the executable to someone else, and they can run it
even without having Rust installed. If you give someone a *.rb*, *.py*, or
*.js* file, they need to have a Ruby, Python, or JavaScript implementation
installed (respectively). But in those languages, you only need one command to
compile and run your program. Everything is a trade-off in language design.

Compilare solo con `rustc` va bene per i programmi semplici, ma mano a mano che
il tuo progetto cresce, vorrai controllare tutte le opzioni e rendere semplice
condividere il tuo codice. 
In seguito, ti presenteremo il tool Cargo, che ti aiuterà a scrivere
programmi in Rust per il mondo reale. 

[troubleshooting]: ch01-01-installation.html#troubleshooting
