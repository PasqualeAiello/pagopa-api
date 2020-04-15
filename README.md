<img width="150px"  src="https://www.cittametropolitana.genova.it/sites/default/files/siti-tematici/Logo%20PagoPA.jpg" title="pagoPa" alt="pagoPa"></a>
# pagopa-specifichepagamenti-schemi


> definizione di tutte le interfacce (esposte e richieste) per la connessione con il sistema pagoPA.
> Tutti gli schemi XSD e WSDL seguono release diverse dalle SANP

Il repository è suddiviso nelle seguenti sezioni:

* **ec**: contiene la definizione delle interfacce esposte da un ente creditore.
* **psp**: contiene la definizione delle interfacce esposte da un Psp.
* **nodo**: contiene la definizione delle interfacce esposte dal sistema.
* **pda**: contiene i tipi di dati scambiati dai soggetti aderenti con il Portale delle Adesioni.
* **general**: contiene gli schemi di definizione dei documenti XML scambiati all'interno del sistema.


-------------

Migrazione (l'idea e di avere 1 wsdl con il suo unico xsd, quindi 1 a uno e da li in poi i vari import se necessari) :
 - spostamento degli xsd inline nel wsdl all'esterno in una nella cartella nominata 
   xsd con annesse rimozioni dei tag non necessari (Es.version).
 - Rinomina dei file (solo per pulizia)
 - Sistemazione degli url interni (**DA CONTROLLARE**)
 - i tag presenti negli xsd con nomi comuni sono stati spostati nel file common.xsd
 - i tag nominati intestazionePPT sono stati rinominati con <primitiva>Header
 