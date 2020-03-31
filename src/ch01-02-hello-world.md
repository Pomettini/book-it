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
Se non vedi questo output, fai riferimento alla [“Troubleshooting”][troubleshooting]<!-- ignore --> 
alla sezione d'installazione per ricevere aiuto. 


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


At the time of this writing, an automatic formatter tool called `rustfmt` is
under development. If you want to stick to a standard style across Rust
projects, `rustfmt` will format your code in a particular style. The Rust team
plans to eventually include this tool with the standard Rust distribution, like
`rustc`. So depending on when you read this book, it might already be installed
on your computer! Check the online documentation for more details.

Inside the `main` function is the following code:

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

You’ve just run a newly created program, so let’s examine each step in the process.

Before running a Rust program, you must compile it using the Rust compiler by
entering the `rustc` command and passing it the name of your source file, like
this:

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

This shows the source code file with the *.rs* extension, the executable file
(*main.exe* on Windows, but *main* on all other platforms), and, when using
Windows, a file containing debugging information with the *.pdb* extension.
From here, you run the *main* or *main.exe* file, like this:

```text
$ ./main # or .\main.exe on Windows
```

Se *main.rs* era il tuo programma “Hello, world!”, questa linea scriverà `Hello,
world!` sul tuo terminale.

If you’re more familiar with a dynamic language, such as Ruby, Python, or
JavaScript, you might not be used to compiling and running a program as
separate steps. Rust is an *ahead-of-time compiled* language, meaning you can
compile a program and give the executable to someone else, and they can run it
even without having Rust installed. If you give someone a *.rb*, *.py*, or
*.js* file, they need to have a Ruby, Python, or JavaScript implementation
installed (respectively). But in those languages, you only need one command to
compile and run your program. Everything is a trade-off in language design.

Just compiling with `rustc` is fine for simple programs, but as your project
grows, you’ll want to manage all the options and make it easy to share your
code. Next, we’ll introduce you to the Cargo tool, which will help you write
real-world Rust programs.

[troubleshooting]: ch01-01-installation.html#troubleshooting
