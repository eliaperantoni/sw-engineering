# Ingegneria del software
## 01 - Introduzione
Software molto importante al giorno d'oggi per economie e società. Addirittura le nazioni vi dipendono. Però non è **tangibile** quindi complesso e difficile da mantenere.

SW *engineering* porta **teoria**, **metodi** e **strumenti** per fare sviluppo SW in modo professionale. "Ingegneria" significa produrre prodotto della **qualità** richiesta (e non oltre) nei **tempi** e nei **budget** fissati. Accompagna il SW dalla nascita fino alla fine della manutenzione.

Costo sviluppo $<$ Costo manutenzione. SW engineering vuole essere cost-effective.

Report del 2017: solo 29% dei progetti hanno rispettato deadline e budget.

Problemi comuni:
- Progetto cancellato
- Fuori deadline
- Fuori budget
- Non tutte le feature
- SW bassa qualità
- Utenti insoddisfatti

Scuse:
- Complessità intrinseca del problema
- Ostacoli tecnologici

Vere ragioni:
- Dialogo stakeholder $\leftrightarrow$ sviluppatori
- Difficoltà capire problemi degli utenti
- Difficoltà capire dominio
- Problemi di management e organizzazione del lavoro
- Problemi team working

## 02 - Software Process
Processo SW = **Insieme strutturato di attività** da compiere per sviluppare un SW.

Per ogni attività si specificano:
- Descrizione
- Output
- Ruoli e responsabilità delle persone coinvolte
- Pre/Post-condizioni

Perché seguire un processo? Per rendere sviluppo:
- Ordinato
- Controllabile
- Ripetibile

Al fine di:
- Aumentare qualità SW (cioè **qualità processo si traduce in qualità prodotto**)
- Aumentare produttività

Vari processi ma tutti includono queste attività **standard**:
- Specifica
- Design & Implementazione
- Validazione
- Evoluzione

_Le attività_ di un processo vengono _pianificate_ secondo un mix di queste management techniques:
- Plan Driven: si pianifica tutto subito e poi si inizia il processo SW tracciando progresso
- Agile (SCRUM): si pianifica mano a mano che il processo prosegue. Più facile reagire a cambiamenti

Pianificazione delle attività $\neq$ Specifica del prodotto (cioè requisiti)

Vediamo alcuni _modelli_ di processi, ogni processo _reale_ prende aspetti da >1 di questi.

### Alcuni processi
Nel **Code & Fix** si va per tentativi. Nessuna fase di analisi o design, si va dritti all'implementazione. Alla fine si controlla se è ok altrimenti si fixa il codice e repeat. Non considerato un vero processo.

---

Il **Waterfall** è sempre **Plan Driven**. Specifica del prodotto e poi sviluppo, niente interlacciamento. Stampo industriale e manifatturiero. Output attività $i$ = Input attività $i+1$ e output freezati una volta all'attività $i+1$.

Le attività sono:
1. Raccolta e definizione requisiti. Questa è la fase più critica, gli errori nati qui sono i più costosi da risolvere.
2. Design
3. Implementazione e test di ogni componente in isolamento
4. Integrazione e test dei componenti insieme.
5. Consegna al cliente e manutenzione. Per manutezione si intende:
   1. Correggiere errori
   2. Nuove feature
   3. Miglioramenti (prestazioni, stabilità, sicurezza, etc..)


Pros & Cons:
+ $+$ Enfasi su analisi requisiti e design fatti bene, implementazione lasciata per ultima
+ $+$ Disciplinato. Possibile organizzare il lavoro su tanti team complessi.
+ $-$ Funziona solo se requisiti sono **chiari** e **stabili**
+ $-$ Difficile accomodare cambi ai requisiti. Visto che sono l'output della prima attività e tutti output sono freezati.

Buono per:
- Embedded, cambi al HW difficili e costosi
- Sistemi critici, serve tanta analisi e tutto documentato
- Organizzazioni grandi e complesse

---

**Sviluppo Incrementale** ha attività di specifica, sviluppo e validazione interlacciate. SW consegnato per incrementi. Pianificazione delle attività stesse può essere **Plan Driven oppure Agile**.

<img src="img/2022-11-19-15-23-53.png" style="zoom: 80%;" />

Pros & Cons:
- $+$ Costi ridotti per reagire ai cambiamenti
- $+$ Rapidissima consegna delle feature essenziali, cliente inizia subito ad usare il SW
- $+$ Maggiore feedback dagli stakeholder che usano subito il SW, requisiti per successivi incrementi saranno presi con maggiore consapevolezza
- $+$ C'è la possibilità di correggiere precedenti requisiti sbagliati
- $+$ Minore rischio di fallimento
- $-$ Difficile tracciare progresso (anche quando pianificazione è plan driven) perché si reagisce ai cambiamenti
- $-$ Costoso produrre continuamente documentazione
- $-$ Codice si sporca con il tempo e diventa sempre più costoso fare modifiche. Serve refactoring ogni tanto
- $-$ Specifica fatta poco per volta, in alcuni domini però deve fare parte del contratto iniziale
- $-$ Alcune funzionalità base sono usate da tanti componenti, ma questi ultimi saranno definiti molto più avanti nel tempo e non siamo sicuri che i componenti base (sviluppati subito) esporranno ad essi un interfaccia corretta

---

**Integrazione e Configurazione** = prendere, adattare, configurare e integrare componenti esistenti. Può essere **Plan Driven oppure Agile**.

Attività:
- Raccolta e specifica requisiti **essenziali**, **poco dettaglio**
- Ricerca e valutazione componenti
- Raffinamento requisiti alla luce dei componenti trovati. Se non è possibile modificare requisiti per essere compatibili con componenti trovati, se ne cercano altri (fase precedente)
- 
    + Configurazione componente all-in-one
    + Adattamento componenti esistenti e sviluppo di nuovi, poi integrazione

![](img/2022-11-19-15-21-25.png)

Pros & Cons:
- $+$ Basso costo di soldi
- $+$ Consegna rapida
- $+$ Basso rischio
- $+$ Poco sviluppo from scratch
- $-$ Bassa qualità
- $-$ Compromissione requisiti, rischio insoddisfazione cliente
- $-$ Scarso controllo su evoluzione componenti terze parti

### Le attività standard nel dettaglio
Nella **Specifica** si capiscono e definiscono le funzionalità e i vincoli del prodotto, e i vincoli di sviluppo. Output è documento dei requisiti. Errori in questa fase molto costosi.

Opzionalmente preceduta da breve e cheap studio di fattibilità per decidere se proseguire con un analisi più dettagliata.

1. **Requirements elicitation and analysis**: osservare sistemi esistenti e parlare con cliente per produrre una **descrizione del sistema** da sviluppare. Possibilità di fare prototipi per capire meglio.
2. **Requirements specification**: **produrre un documento** che contiene i requisiti definiti formalmente. Requisiti sono due tipi: User (semplici da leggere, alto livello), System (dettagliati).
3. **Requirements validation**: controllo che requisiti siano realistici, _consistenti_ e _completi_ (ci siano tutti) altrimenti modifico il documento.

<img src="img/2022-11-19-16-04-22.png" style="zoom:80%;" />

---

- **Design**: tradurre specifica in descrizione struttura SW, modelli dati, interfacce tra componenti.
    - **Design architettura**. Struttura generale del software e i componenti principali.
    - **Design db**
    - **Design interfacce**. Come comunicano i componenti. Con una interfaccia precisa, i componenti possono essere utilizzati senza conoscere l'implementazione e possono essere sviluppato in isolamento.
    - **Selezione e design componenti**. Descrivo i componenti ad alto livello di dettaglio. Potrei scegliere componenti esistenti o pianificarne di nuovi.
- **Implementazione**: tradurre design in SW.

Le due fasi possono essere interlacciate. Cambiano molto da progetto a progetto, a seconda del dominio (ad esempio un progetto embedded probabilmente non avrà db design)

---

**Validazione** è controllare che SW rispetti requisiti. Controlli manuali oppure test con dati. Test case derivanti dalla specifica iniziale.

1. **Component o unit testing**, in isolamento. Test case scritti da stesse persone che hanno sviluppato componente. Automatici (unit testing). Già fatto anche durante implementazione di solito.
2. **System testing**, integro tutti componenti e testo sistema per intero.
3. **Acceptance testing**, fatto dal cliente stesso con dati realistici. Fa emergere omissioni nella specifica.

Nel processo waterfall in particolare (plan driven) testing potrebbe essere secondo modello a V, rispecchia le varie attività del processo stesso:

<img src="img/2022-11-19-16-18-07.png" style="zoom:80%;" />

---

**Evoluzione** modifica SW per adattarsi ai cambiamenti del business.

- **Change anticipation**: accorgersi in fretta di possibili cambiamenti futuri, prima che diventino troppo costosi da risolvere (più si aspetta e più il SW evolve ed è difficile da modificare).
- **Change tolerance**: processo fatto in modo da accomodare cambiamenti.

Metodi per ridurre la probabilità che ci sia da modificare i requisiti o attenuarne l'impatto:
- **Validare bene i requisiti con dei prototipi prima di iniziare**
- **Consegna (che richiede l'uso del processo) incrementale**, il processo accomoda facilmente i cambiamenti che sono anche meglio ponderati grazie al feedback del cliente che già usa il software

## 03 - Agile
Storicamente, la maggior parte dei SWs erano **grandi**, molto **longevi** e richiedevano **specifiche precise**. Poi (fine anni 90) **sviluppo rapido**, **poco overhead** nel processo SW e **adattamento** a **requisiti incompleti**, **imprecisi** o **mutabili** sono diventati aspetti più importanti.

Agile è una filosofia di sviluppo software. La vediamo applicata ad un processo SW che regola e caratterizza le attività di specifica, design, implementazione e validazione. Dopo vedremo SCRUM, una tecnica di project management che segue la filosofia agile ma la applica alla fase di pianificazione del processo stesso.

(Lo il processo agile è il processo incrementale visto in precedenza, ma esteso e più dettagliato)

Principi:
- Specifica, design, implementazione e testing sono **interlacciati**
- **Consegna incrementale** (2,4 settimane)
- **Coinvolgimento cliente** durante il processo. Fornisce e prioritizza i requisiti, decidendo anche quali includere nel prossimo incremento. Valuta il SW mano a mano che è consegnato e fornisce feedback
- **Valorizzare skill** del team, lasciando che proceda a modo suo senza forzare un processo rigido
- **Flessibilità**, aspettarsi cambiamenti quindi sviluppare sistema in modo da accoglierli
- **Semplicità**, sia nel prodotto che nel processo
- Ridotta **documentazione**
- Estensivo utilizzo di tool di supporto e **automatizzazione**

Agile manifesto:
- Persone e interazioni umane $>$ processi e strumenti
- SW funzionante $>$ documentazione
- **Collaborazione** con cliente $>$ **negoziazione** con cliente
- Flessibilità e prontezza $>$ seguire un piano

Applicabilità:
- Prodotto medio-**piccolo**
- Cliente **disponibile** ad essere coinvolto
- Pochi vincoli **esterni**
- Sviluppo agile allacciato ad un **management** agile

Extreme programming, spinge lo sviluppo _iterativo_ all'estremo:
- Versioni buildate molto spesso
- In ogni build, _tutti_ i test sono _eseguiti_ e devono _passare_, anche solo per condividere il codice con un collega
- Incremento consegnato ogni 2 settimane
- On-site customer
- CI/CD
- Pair programming
- TDD
- Refactoring

---

**User story** = **Storiella** che racconta un utilizzo del software dal punto di vista del cliente

**Scenario** = Fornisce maggiore **dettaglio** ad una sotto-sezione di una user story. Contiene solitamente:

- Input
- Output
- Precondizioni
- Postcondizioni
- Funzionamento normale
- Possibili problemi
- Possibili attività concorrenti

Il cliente prioritizza le user stories e gli scenari.

Si usano user story e scenari al posto del documento dei requisiti che invece è poco intuitivo e difficile da modificare.

**Task card** = Ottenute dal team di sviluppo **spezzando** le user story e gli scenari. È un pezzo di lavoro atomico. Il team stima effort e risorse necessarie per ogni card.

---

**Test Driven Development** = Test case, strettamente legati ai requisiti (user stories e scenari), sono scritti **prima** del codice ed eseguiti **automaticamente** durante lo sviluppo. Vengono definiti con l'aiuto del **cliente** e validati da esso.

**Refactoring** rallenta il degradamento della qualità del codice (leggibilità principalmente) e ne ripristina un buono stato. Necessario perché il software deteriora mano a mano che si fanno modifiche. Esempi:

- Riorganizzazione
- De-duplicazione
- Rinominazione variabili, metodi, classi

Pair Programming = Due sviluppatori allo stesso PC. Coppie create dinamicamente e cambiate di tanto in tanto. Vantaggi:
- Collective ownership, gli sviluppatori si sentono responsabili dell'intera codebase e ci tengono alla sua qualità
- Code review implicita, informale e meno costosa
- Refactoring incoraggiato, vedi collective ownership
- Condivisione della conoscenza implicitamente
- Non necessariamente inefficiente, evidence shows

---

Ora applichiamo la filosofia agile per fare project management, cioè la pianificazione del processo di sviluppo SW. La chiamiamo SCRUM e si contrappone alla metodologia di pianificazione Plan-Driven.

Secondo SCRUM, lo sviluppo avviene secondo queste fasi:
1. **Fase iniziale**: specifica iniziale del prodotto e design architettura di base
2. Serie di **sprint**, ogni sprint produce incremento
3. **Fase finale**: si completa il SW e si scrive documentazione

Terminologia:
- Product backlog: cose da fare. Le prime task si aggiungono nella fase iniziale dello SCRUM e poi vengono aggiunte mano a mano
- Sprint: periodo di sviluppo di 2-4 settimane
- Sprint backlog: cose da fare nello sprint corrente
- Scrum: meeting giornaliero
- Velocity: stima delle cose il team riesce a fare in uno sprint
- ScrumMaster: persona all'interno del team che verifica che SCRUM sia rispettato
- ProductOwner: cliente che partecipa: indicando requisiti, prioritizzandoli e fornendo feedback

Un singolo sprint funziona così:

<img src="img/2022-11-19-18-47-37.png" style="zoom:80%;" />

- Product owner dice quali task dal product backlog sarebbero più prioritarie
- Team decide quali task riesce a fare in questo sprint (anche usando la velocity stimata negli sprint precedenti) e le mette nello sprint backlog
- Sprint. Durata fissa. Team isolato dal cliente. Eventuali comunicazioni dall'esterno sono filtrate dallo scrum master. Meeting giornalieri (scrums) molto brevi (10 minuti) in cui i membri del team si scambiano informazioni:
    - Cosa ho fatto ieri
    - Cosa faccio oggi
    - Difficoltà incontrate
- Alla fine dello sprint:
    - Si valuta com'è andato lo sprint. Se e come si poteva fare di meglio
    - Si consegna l'incremento al cliente che lo valuta e fornisce feedback


Benefici:
- **Delivery on-time** (non si allunga **mai** lo sprint, al massimo si consegnano meno feature) e quindi maggiore fiducia del cliente che è più incline a fornire buon feedback
- **Visibilità e comunicazione**: tutti i membri del team sanno chi sta facendo cosa e c'è grande comunicazione, grazie agli SCRUM

È importante che la comunicazione tra membri del team e con il cliente sia efficacie e rapida. Se si fa da remoto, bisogna dotarsi di strumenti per comunicare. Anche la CI/CD assicura un processo piu fluido in caso di sviluppatori non co-locati.

---

Agile non funziona benissimo per la **manutenzione** di progetti long-lasting:

- Difficile modificare software:
  - A causa della **ridotta documentazione**
  - Membri del team potrebbero andarsene: perdita di conoscenza sulle decisioni e le **motivazioni** fatte in passato
- Cliente potrebbe non essere disponibile a **rimanere coinvolto a lungo**

---

Come **scalare** Agile per progetti più grandi o longevi oppure a team più grandi o distribuiti?

Scaling up = Un team più grande
Scaling out = Più team

IBM propone **Agility at Scale** Model (ASM) per scalare. Si usa una struttura a **cipolla**:
- **Core** agile: Piccolo team lavora in modo pienamente agile sulle feature essenziali e sviluppate per prime
- **Disciplined** agile delivery: Feature secondarie sviluppate in un agile un po' più disciplinato
- Agility at **scale**: tutto il resto si sviluppa su larga scala (team grandi e distributi) in modo ancora più disciplinato

**Multi-team scrum**. Tanti team usano scrum, li mettiamo anch'essi in comunicazione con una metodologia scrum. 

- Ogni team ha un Product Owner e uno Scrum Master. 
- Ogni team ha un Software **Architect**, tra di loro comunicano per definire la struttura completa del sistema. 
- Le **deadline** degli sprint sono **allineate**.
- **Scum of scrums**. Un rappresentante da ogni team partecipa ad uno scrum inter-team.

---

Problemi e valutazioni da fare prima di usare Agile:

- Sistema
  - Quanto **grande** è il progetto e il team che lo sviluppa?
  - Il progetto richiede tanta **analisi** e design dettagliato?
  - Qual è la **longevità** del progetto?
  - Il progetto è soggetto a **regolamentazioni** esterne?
- Team
  - Le **tecnologie** (linguaggi/framework) si prestano ad un utilizzo agile?
  - Quanto **skillati** sono i membri del team?
  - Il team è **distribuito**? Se si, potrebbe essere necessario scrivere tanta documentazione
- Organizzazione
  - Il contratto richiede una **specifica** dettagliata
  - L'organizzazione, e la sua **cultura**, accoglie bene lo sviluppo agile?
  - Il cliente accetta di essere **coinvolto**?

---

Resistenze principali a metodologie agili:
- **Grandi** organizzazioni richiedono **controlli di qualità** e **standard** rigidi. Troppa burocrazia non funziona con Agile
- Richiesti sviluppatori tanto **skillati**
- Resistenza, diffidenza, conservatorismo. A causa della **cultura** aziendale o dei **manager inesperti**

## 04 - Requisiti
I requisiti sono descrizioni delle funzionalità che il sistema dovrà fornire e vincoli sui modi con cui dovrà farlo. Riflettono i bisogni degli stakeholder (tutte le persone che hanno un qualche interesse nel software da realizzare).

Tassonomia:
- **Utente**: sono i requisiti così come forniti dal cliente. Linguaggio naturale e diagrammi. Ambigui.
  - Il sistema deve generare un report ogni mese contenete la lista dei farmaci prescritti

- **Sistema**: sono i requisiti **strutturati** e **dettagliati**. Anche colmando quelle cose lasciate non-specificate dal cliente.
  - L'ultimo giorno di ogni mese, dopo le 17:30, il sistema deve generare una lista dove è presente una riga per ciascun farmaco mai prescritto durante il mese appena trascorso. In ogni riga è riportato il nome del famarco, la categoria, il numero di volte che è stato prescritto, il numero di pazienti univoci a cui è stato prescritto [...]


I requisiti di sistema _derivano_ da quelli utente, e poi si va anche nella direzione opposta per _validare_ i requisiti di sistema.

Un'altra tassonomia ortogonale alla precedente è *funzionali* vs *non-funzionali*.

---

**Requisiti funzionali**: funzionalità che il sistema deve fornire, come deve reagire agli stimoli o comportarsi in particolari situazioni. Si trovano di diversi livelli di astrazione (infatti questa classificazione è ortogonale a Utente vs Sistema). 

Questi requisiti devono essere **completi** e **consistenti** (potrebbe essere difficile se gli stakeholder hanno idee contrastanti).

---

**Requisiti non funzionali**: vincoli sui servizi offerti dal sistema. Si applicano spesso **all'intero sistema**. Hanno spesso un grande impatto. Potrebbero essere spezzati in tanti requisiti funzionali. Tipicamente trascurati dal cliente.

<img src="img/2022-11-24-16-39-01.png" style="zoom: 80%;" />

- Prodotto: vincoli sul SW creato
  - Facilità d'uso
  - Accessibilità
  - Efficienza
  - Affidabilità
  - Sicurezza

- Organizzazione: requisiti derivati da regole e procedure nell'organizzazione del client o nel team di sviluppo
  - Linguaggi e tool da usare
  - Sistema operativo, tecnologie o altri vincoli sull'ambiente di deployment

- Esterni: requisiti che non dipendono nè dal committente nè dal team di sviluppo
  - Leggi
  - Etica

<img src="img/2022-11-24-16-43-33.png" style="zoom:67%;" />

Requisiti non funzionali sono spesso descritti con termini vaghi. Ad esempio: cosa significa che il software è "facile" da usare? Sarebbe meglio scriverli in modo quantificabile e verificabile: "ci vogliono X ore di training per poi saper usare il software commettendo massimo Y errori al giorno".

Alcuni esempi di metriche da usare:

- Velocità $\rightarrow$ Transazioni/s, tempo di risposta 
- Dimensione $\rightarrow$ MB
- Facilità d'uso $\rightarrow$ Tempo di addestramento
- Affidabilità (quanto spesso ci sono guasti) $\rightarrow$ Tempo medio prima di un guasto, percentuale di downtime
- Robustezza (quanto sono impattanti i guasti) $\rightarrow$ Tempo per il riavvio dopo un incidente, probabilità di corruzione dei dati dopo un crash
- Portabilità $\rightarrow$ Architetture CPU o sistemi operativi supportati

---

Processo che, per approssimazioni via via migliori, producono i requisiti:

<img src="img/2022-11-24-16-47-31.png" style="zoom:50%;" />

Una singola iterazione segue questo schema che avevamo già visto:

<img src="img/2022-11-24-16-48-43.png" style="zoom: 80%;" />

### Elicitation
Si cerca di capire:
- Il **dominio** del cliente
- Servizi e **funzionalità** che il software dovrà esporre
- **Vincoli** vari

Ostacoli:
- Stakeholder hanno **poco chiaro** quello che vogliono o si **esprimono male**, con il loro linguaggio, danno cose per **scontato**, non vogliono parlare di cose **private** dell'organizzazione, etc
- Stakeholder vogliono qualcosa di **impossibile**
- Diversi stakeholder hanno **conflitti** di idee
- Fattori **politici** ed organizzativi possono influenzare requisiti (manager genera requisito per funzionalità che gli darebbe più influenza o controllo)
- Requisiti **cambiano**

Interviste possono essere:
- Domanda chiuse a scelta multipla
- Domande aperte, nulla di prefissato
- Un mix

Consigli:
- Essere di **mente aperta** e ascoltare lo stakeholder
- Fare domande **trampolino** che scatenano discussioni invece di chiedere "ok cosa vuoi?"

**Etnografia**: ingegnere del requisito si immerge nell'ambiente del cliente per capirlo meglio. Permette di rilevare meglio requisiti impliciti _esistenti_ e processi già in essere, però non permette di rilevare nuove funzionalità da aggiungere. Esempio: ingegnere lavora per un po' di tempo come infermiere.

### Specification
(In un processo Agile, questa fase è striminzita perché non serve un documento di specifica super-formale. Ci si limita a raccogliere user stories e scenari in una fase che sta a cavallo tra la elicitation e questa: la specification.)

Si tratta di **scrivere** requisiti (di utente e di sistema) in un **documento dei requisiti** in modo preciso e completo perché potrebbe diventare parte del contratto.

Ricorda che i requisiti spiegano solo **cosa** il sistema deve fare e con quali **vincoli**, non il **modo** in cui lo fa. Anche se certe volte potrebbe essere difficile seguire questa regola. Ad esempio: requisiti o software esterni impongono particolari architetture o tecnologie.

Per specificare i requisiti posso usare:
- Linguaggio **naturale**. Espressivo, intuitivo, universale. Però ambiguo. Linee guida:
    - Usare **formato** e **lessico** standard e **consistente**
    - Usare **enfasi** per evidenziare parti chiave
    - Evitare lessico **tecnico**
    - Spiegare **perché** il requisito serve e come mai è stato aggiunto
- Struttura **rigorosa**, a tabella
- **Use-case** diagram. Possono essere integrati con sequence-diagrams per scendere più nel dettaglio in alcuni use-case

Il documento può seguire uno standard. Ad esempio l'IEEE ne propone uno.

Chi usa il documento:
- **Cliente**, per definire i requisiti e **verificare** che combacino con le loro richieste
- **Manager**, per fare un **preventivo** e **organizzare** lo sviluppo
- **Sviluppatori**, per sapere cosa devono **implementare**
- **Tester**, per sapere cosa **testare**
- **Manutentori**, per **comprendere** il SW già sviluppato in modo da mantenerlo

### Validation
Fase in cui si verifica che i requisiti rappresentino ciò che il cliente vuole davvero perché è molto costoso cambiare i requisiti dopo.

Checklist:
- **Validità**: il sistema fornisce le funzionalità che meglio risolvono le necessità del cliente?
- **Consistenza**: i conflitti si contraddicono?
- **Completezza**: rimane ambiguità irrisolta?
- **Realismo**: ce la facciamo a soddisfare i requisiti nei tempi e nel budget?
- **Verificabilità**: saremo in grado di controllare se i requisiti sono soddisfatti dal software prodotto?

Tecniche:
- Revisione **manuale**
- **Prototipo**, usando strumenti che permettono di ottenere molto rapidamente un mock del software da sviluppare per vedere se è davvero quello che serve al cliente
- Definizione **test case**
    - Così vediamo se un requisito è verificabile
    - Se il test case è difficile da scrivere, probabilmente la feature è difficile da implementare

### Changing
Perché i requisiti cambiano?
- Problema **intrinsecamente difficile** da definire interamente
- Cambia la **conoscenza** del problema
- **Evoluzione ambiente** di deploy, sia dal punto di vista tecnico che normativo
- Conflitti tra chi **compra** e chi **usa** il sistema
- **Cambiano priorità** degli stakeholder

Tutto il sistema di requirements engineering deve supportare le modifiche:
- **Tracciabilitá** dei requisiti con **id** univoci
- Tracciare **dipendenze** tra requisiti, e tra requisiti e design

Processo di cambiamento:
- Il cambiamento proposto va discusso per verificare che sia **necessario** e **realizzabile**
- Stima dei **costi**
- Modifica documento dei requisiti, design e altra documentazione
- Implementazione

## 05 - Architettura

Si tratta di capire come il software dovrebbe essere organizzato identificando una struttura complessiva, i componenti principali e le loro relazioni.

Requirements engineering $\rightarrow$ Architectural design $\rightarrow$ Design

Perché serve un'architettura:
- Discuterne, ad alto livello, con i **clienti**
- Facilitare il **design** fatto in seguito
- Decidere se i **requisiti** possono essere **soddisfatti**
- Per **riutilizzarla** in altri progetti
- Funge da **documentazione**

Soluzione possibile: **diagramma a blocchi**. Svantaggi:
- **Inconsistente**, non segue un linguaggio standard
- Talvolta **troppo astratto**, cioè non fornisce sufficiente informazione dettagliata (ad esempio: che tipo di relazione c'è tra due componenti)

Ogni modello è capace di mostrare soltanto una **prospettiva** tra:
- **Logical** view (classes): i componenti e le classi che compongono il software
- **Process** view (objects): come il software è scomposto in processi in esecuzione a runtime
- **Physical** view (processors): come i processi sono allocati sui processori hardware
- **Development** view: come il sw è scomposto per poterlo sviluppare

Ora invece vediamo pattern noti a cui ispirarsi per decidere un'architettura.

## MVC

Permette diverse **visualizzazioni**, **logiche di interazione** e **tecniche di conservazione dei dati** in diverse **combinazioni**. Queste possono evolvere abbastanza indipendentemente e potrebbero presentarsene di nuove in **futuro**. Adottato e imposto da diversi **framework**.

- $+$ **Separazione** delle responsabilità
- $-$ **Complessità** aggiuntiva, poco adatto per software piccoli

## Layered architecture

Funzionalità organizzata a **strati**, ognuno utilizza solo i servizi offerti dai layer adiacenti. Esempi: stack ISO/OSI, Android, iLearn.

- $+$ Permette di **rimpiazzare** un layer a patto di rispettare l'interfaccia
- $+$ Facile implementare una funzionalità **aggiuntiva** su un sistema **esistente**: mi basta sviluppare uno strato da mettere in cima
- $+$ Facile garantire una politica di **sicurezza** visto che posso fare un'analisi concentrandomi su uno strato per volta
- $+$ Facile distribuire lo **sviluppo**: uno strato per team
- $-$ Si è spesso tentati dal fare dei "**fori**" e interagire direttamente con layer non adiacenti
- $-$ **Performance** inferiori, a causa della tanta delegazione

## Repository

C'è un **database centrale** acceduto da **diversi sotto-sistemi** che non si parlano tra di loro. Si presta bene a sistemi centrati su grandi quantità di dati (magari anche longevi). Esempio: Git.

- $+$ Sistemi periferici eseguono **indipendentemente** dagli altri
- $+$ Eventi, cambiamenti dei dati e messaggi possono essere facilmente **propagati** a tutti gli altri (non servono connessioni N:N stile prodotto cartesiano, è la repository che fa da centro-smistamento)
- $+$ Facile gestire **consistenza** dei dati perché sono in un punto solo
- $-$ Introduzione di un **single point of failure**
- $-$ Calo **prestazioni**, tutto deve passare dalla repository

## Client-Server

Server mettono a disposizione i servizi utilizzati dai client.

- $+$ Server possono essere **distribuiti geograficamente** per ridurre la latenza e distribuire il carico
- $+$ **Unificazione dei servizi comuni**, ove opportuno, per evitare che due server forniscano inutilmente le stesse funzionalità
- $+$ I client conoscono il server ma **non serve che il server conosca i client**
- $-$ **Single point of failure** nel server
- $-$ **Prestazioni imprevedibili** (dipende stato rete)
- $-$ Problemi **organizzativi** se server posseduti o controllati da organizzazioni diverse

## Peer to Peer

In un certo senso, ogni peer è contemporaneamente client e server. Architettura molto robusta e resiliente a incidenti. Esempi: Torrent e Bitcoin. Molto fault-tolerant.

## Pipe and filter

Trasformazioni e filtri applicati in sequenza ai dati. Si presta a sistemi che devono analizzare e trasformare grosse moli di dati e le varie fasi di questa pipeline sono facilmente separabili.

- $+$ Facile **comprensione** della pipeline
- $+$ Facile **modificare** la pipeline
- $+$ Facile **riutilizzo** di subset della pipeline
- $+$ Pipeline può essere **sequenziale** o **concorrente**
- $+$ Dati possono entrare nella pipeline anche se ci sono elaborazioni in corso **più avanti**
- $-$ Inadeguato per sistemi **interattivi**
- $-$ Bisogna **fissare** in modo chiaro **API** e **formati dati** dei componenti
- $-$ Continuo **encoding/decoding** per passare i dati da un componente all'altro
    - **Prestazioni** inferiori
    - **Riutilizzo** di componenti o subset della pipeline è **più difficile o meno immediato** se i formati utilizzati sono **incompatibili**

---

Architetture si possono combinare in modo gerarchico. Stesso componente potrebbe **far parte di più architetture diverse** e avere **ruoli diversi** in ciascuna.

## 06 - Testing
Il testing ha due obiettivi:
- **Dimostrare** che i **requisiti siano soddisfatti** (quindi opportuno almeno 1 test-case per ogni requisito)
- **Far emergere bug** o difetti

Parola "bug" deriva da insetti in buchi di schede perforate.

Testing non può garantire **assenza** di bug ma solo la **presenza**. Però può fornire un livello di **confidenza** di correttezza che dipende da:
- Ruolo e criticità del SW
- **Aspettative** del cliente
- Rapido rilascio nel **mercato** richiesto o meno

Come alternativa al testing: revisione **manuale** senza eseguire il software. Vantaggi:
- Non serve preparare un **ambiente** di esecuzione
- Errori non **mascherano** quelli precedenti
- Si può fare anche su codice che **non compila**
- Rileva anche **altri tipi** di **difetti** (code style, inefficienza algoritmica, etc)

---

Struttura di un test:

- **Setup**
- **Call** (produce risultati)
- **Assertion** (si controlla che i risultati siano quelli corretti)
- **Teardown**

Opportuno usare **mock** per soddisfare le dipendenze dell'entità sotto test, anche quando sarebbe già disponibile la versione **concreta**. Questo garantisce **ripetibilità** e **indipendenza** dei test. Si realizza con i framework che permettono di creare classi finte i cui metodi o variabili restituiscono **valori impostati precedentemente dallo sviluppatore**.

Linee guida per scrivere i test case:

- Ci vorrebbero test case che testano situazioni e input sia **normali** e attesi, sia **anormali** e corner cases (per **stressare** il software)
- **Partizionare** gli input in classi di equivalenza. Pochissimi test case (o anche solo uno) per ogni classe:
  - Il valore centrale della classe
  - I valori vicino ai confini con altre classi
- Cercare di generare **tutti i possibili errori**
- Cercare di generare sia **output** molto **piccoli** che molto **grossi**
- Cercare di generare **output invalidi**
- Cercare di far andare dei buffer in **overflow**
- Provare a usare **puntatori nulli**
- Ripetere gli stessi input o situazioni **più volte**
- Usare **tempistiche** diverse (ad esempio, avvio dei thread in sequenze diverse)
- Quando uso collezioni, opportuno testare:
  - Con collezioni **vuote**
  - Con collezioni di **diversa lunghezza**
  - Pescando elementi dalla **testa**, **centro** e **coda** della collezione

Il Test Driven Development (**TDD**) è bellino, tipico soprattutto di Agile. Vantaggi:

- **Coverage** viene "gratis"
- **Regressioni** individuate subito
- Facile debuggare perchè ogni case testa una **singola** feature. Sò subito dove concentrare le indagini
- Test fungono da **documentazione**
- Incoraggimento a un **API** **semplice**

---

Testing si suddivide in stadi:
- A - **Development** Testing: Lo fanno sviluppatori durante sviluppo. Si alterna con il debugging. L'obiettivo di questa fase è **far emergere i bug**.
    - A1 - **Unit** Testing
    - A2 - **Component** Testing
    - A3 - **System** Testing
- B - **Release** Testing: Lo fa team separato prima di rilasciare
- C - **Acceptance** o **User** Testing: Lo fa utente finale nel suo ambiente

### A1 - Unit Testing

Si testa un'unità **atomica** che può essere: funzione, classe, piccolo componente con interfaccia semplice. Eventuali fault indicherebbero errori dovuti all'unità stessa.

Come testo completamente una classe? (Difficile coverage 100% per colpa dell'ereditarietà)
- Chiamo **tutti i metodi**
- Leggo/Scrivo **tutti i field**
- Provo tutti gli **stati** possibili

### A2 - Component Testing

Componente sono diverse unità collegate insieme. Si controlla l'interfaccia esposta dal componente. Eventuali fault indicherebbero un errore nella comunicazione tra le unità.

Unità possono comunicare in modi diversi:
- **Parametri**
- **Shared Memory**
- **Procedure Call**
- **Message Passing**

Possibili errori di interfacciamento tra unità:
- Uso incorretto dell'**interfaccia** (tipi sbagliati ad esempio)
- **Assunzione** non soddisfatte
- **Tempismo** sbagliato

### A3 - System Testing

Si mettono insieme i componenti per formare l'intero sistema. Eventuali fault indicherebbero problemi di interfacciamento tra componenti.

Questi test case possono essere basati su **use-case** individuati nella fase di requirements-engineering. Alcuni di essi potrebbero essere arredati di **sequence-diagram** per maggiore dettaglio.

Opportuno che vengano testate:
- Tutte (o quasi) le **linee** di codice
- Tutte le **funzioni**, o **combinazioni** di chiamate a esse, accessibili per l'utente dall'**interfaccia grafica**
- Per gli **input che può fornire direttamente l'utente**, testare sia quelli **corretti** sia quelli **inattesi**

### B - Release Testing

Lo fa un **team diverso**. **Black box**: non si guarda dentro il sistema ma lo si testa as-is per vedere se rispetta le specifiche.

Simile a System Testing (A3) però qui il focus è sul verificare che i **requisiti siano rispettati** e non cercare di trovare bug.

Se sono disponibili **scenarios** e **user stories**, possiamo usare direttamente quelli come situazioni da testare perché raccontano proprio un'interazione dell'utente con il software.

**Performance** Testing = Controllare che il software possa supportare il carico e rispondere nei tempi previsti.

### C - Acceptance/User Testing

Fatto dagli utenti finali o dal committente:

1. $\alpha$ fatto da pochi utenti, presso la software house
2. $\beta$ si coinvolge un numero maggiore di utenti
3. Acceptance fatto dal cliente presso il suo ambiente. Accetta o meno il software consegnato e paga

Nei metodi **Agile** **non c'è una fase separata di Acceptasnce/User testing** (C) perchè il cliente è sempre on-site e collabora per tutto il tempo con il team di sviluppo per definire i test-case e verificarne il successo. C'è il rischio però che il product owner non rappresenti il **tipico utente finale** che andrà poi a utilizzare veramente il software.

## 07 - Refactoring

Refactoring = Rendere software più **leggibile** e **semplice** **senza** che dall'esterno si possa **osservare** **alcun** **cambiamento**. **Rallenta** e compensa il normale **degradamento** della qualità del codice che avviene a ogni modifica. Il refactoring rende anche più **cheap** la maintenance e ulteriori modifiche successive.

**Debito tecnico** = A ogni modifica mi sto indebitando con lo sviluppatore che verrà dopo di me (perché il codice è leggermente più difficile da leggere). Il refactoring salda parte di questo debito.

**Re-engineering** = Rifare un software da capo. È un attività puntuale e per questo si contrappone al refactoring che invece è un processo **continuo** che accompagna il software per tutta la sua vita.

Quando fare refactoring?

- Senza una schedule precisa
- Prima di aggiungere una **feature** (così sarà più facile farlo)
- Dopo aver fixato un **bug**
- Quando si trova un **code smell**

**Code Smell** = Codice che tecnicamente funziona, però non segue buoni principi di design e degrada la qualità del codice. Esempi (con possibile soluzione):

- Codice duplicato $\rightarrow$ Estrarre metodo.

  Quando c'è duplicazione:

  - Gli errori si ripetono
  - Bisogna ricordarsi di propagare eventuali modifiche
  - Dimensione della codebase esagerata

  Del codice duplicato potrebbe non essere esattamente identico: si ha duplicazione anche se i nomi delle variabili o i tipi cambiano in modo consistente.
- Metodi o classi troppo grandi o complicate $\rightarrow$ Spezzare in metodi o classi più piccole
- Abuso di `switch` case $\rightarrow$ Usare il dynamic dispatch con polimorfismo
- Data clumping: stesso gruppetto di variabili che compare spesso insieme $\rightarrow$ Raggruppare in una classe coesa
- Generalità speculativa: cioè rendere codice più generale di quanto serva in questo momento, nel caso servisse in futuro $\rightarrow$ Togliere perché è una complicazione inutile
- Dead code $\rightarrow$ Togliere
- Classi molto piccole e prive di dinamicità (data-class)
- Lunga lista di parametri
- Try-Catch con `catch` vuoto

I **test automatici** sono importantissimi per fare refactoring perché possiamo farlo con la peace-of-mind di non aver rotto niente.

Refactoring complessi si fanno con tanti diversi refactoring più **atomici**. Quelli più semplici spesso sono automatizzati dall'IDE (rinominare classe, spostare file, etc).

Esempi di refactoring:

- **Rinomina** variabile, metodo o classe
- **Extract interface**: sostituire l'uso di una classe concreta con una nuova interfaccia che contiene solo ciò di cui si ha bisogno. Ad esempio: uso di `ArrayList<T>` diventa `Collection<T>` se abbiamo bisogno solo di fare `add`, `remove` e `contains`.
- **Pull up**: spostare membri da sottoclasse a superclasse
- **Extract method**: sostituisce codice duplicato con chiamata a nuovo metodo
- **Move method**: sposta metodo da una classe ad un'altra
- **Replace temp with query**: sostituisce il calcolo di un'espressione poi salvato in una variabile locale con una chiamata ad un metodo che fa il calcolo. Così diventa disponibile a tutti i metodi e si rimuove la tentazione di fare metodi lunghi (visto che quella variabile locale è, appunto, disponibile solo nel corpo del metodo corrente).
- **Replace parameter with method**: se un metodo può arrangiarsi a calcolare un valore, non dovrebbe richiedere che gli venga passato pre-calcolato nei parametri
- **Extract class**: spostare pezzi di una classe troppo grande in una più piccola e coesa
- **Replace inheritance with composition+delegation**: altrimenti si eredita più del necessario. Ad esempio: uno `Stack<T>` che eredita da `ArrayList<T>` erediterebbe anche `insertAt` che non ha senso in uno stack
- **Replace conditional with polymorphism**: rimpiazza uno switch case con una chiamata dynamically dispatch con una nuova classe per ogni branch
- **Separate domain from presentation**: togliere la business logic dal codice per la view

## 08 - Project Management

Essenziale perché il progetto deve rispettare vincoli:

- Organizzativi
- Di budget
- Di tempo

Un buon management **non garantisce** il successo del progetto ma un cattivo management lo **destina** al fallimento.

Peculiarità del software che rendono il management ancora più difficile:

- Sofware è intangibile
- Ogni progetto è unico e diverso
- Processi variano da organizzazione a organizzazione

Fattori che influenzano il project management:

- Dimensione dell'azienda (comunicazione informale vs gerarchie complesse e procedure formali)
- Clienti interni vs esterni (cambia la formalità richiesta per comunicare)
- Dimensione software (cambia il numero e la dimensione dei team richiesti)
- Tipo software (un sw critico richiede che ogni scelta sia registrata e giustificata)
- Cultura aziendale (tendenza a correre rischi, quantità di burocrazia)
- Processo software Agile vs Formale

Attività del project management:

- Project **Planning** = Pianificare sviluppo e assegnare persone alle task
- **Risk** Management = Individuare, analizzare e monitorare i rischi. Prepare piani di risposta
- **People** Management = Decidere chi lavora al progetto e cosa fa
- **Reporting** = Ai clienti e ai ranghi superiori dell'azienda
- **Proposal** Writing = Fare il preventivo e una proposta di progetto

### Risk Management

Attività cruciale a causa dell'**incertezza** intrinseca dei progetti SW:

- **Requisiti** imprecisi o mutabili
- Difficoltà nel fare **stime**
- Differenze nelle **skill** individuali

Attività:

1. **Identificazione**. Rischi dovuti a diversi motivi:
    - **Stime** (esempio: sottostimata la dimensione del software o il tempo richiesto per svilupparlo)
    - **Organizzazione** (esempio: cambiano i manager o cala il budget per problemi finanziari)
    - **Persone** (esempio: non si riesce ad assumere le persone con le skill necessarie)
    - **Requisiti** (esempio: stakeholder cambiano requisiti oppure nuove normative esterne)
    - **Tecnologia** (esempio: database non performante quanto anticipato)
    - **Strumenti** (esempio: strumenti di sviluppo diversi non si integrano come anticipato)
2. **Analisi** **probabilità** e **impatto**. Da rifare continuamente perché la probabilità e l'impatto sono soggettive e potrebbero cambiare mano a mano che si ottengono nuove informazioni
3. Preparazione **piani** di risposta
    - **Avoidance** strategies: Per minimizzare la probabilità che il rischio si manifesti
    - **Minimization** strategies: Per minimizzare l'impatto
    - **Contingency** plan: Se l'impatto non può essere minimizzato, come rispondere
4. **Monitoraggio**, processo che si ripete continuamente (facendo uso di indicatori) per capire se un rischo sta diventando più o meno probabile, e più o meno impattante rispetto a prima

### Managing People

Responsabilità del project manager trovare (e tenere) persone in gamba e fare in modo che la loro produttività possa essere massimizzata.

Vogliamo un team **coeso**. Perchè:

- **Quality standards** del codice nascono naturalmente
- Si impara l'uno dall'altro, **colmando** eventuali **lacune**
- **Knowledge sharing**: se un membro lascia il team, le sue parti di codice sono conosciute anche da altri
- **Refactoring** incoraggiato perché ognuno si sente responsabile dell'intera codebase

Tipi di persone:

- **Task** oriented: traggono entusiasmo dal lavoro stesso, poco socievoli
- **Self** oriented: usano il lavoro come mezzo per un obiettivo secondario (diventare ricchi o potenti)
- **Interaction** oriented: traggono entusiasmo dall'interazione con le persone. Molto socievoli ma non lavorano molto

In un buon gruppo ci deve essere un mix di questi

### Project planning (Stampo plan-driven)

In un piano si scrive:

1. Lavoro da fare
2. Chi lo fa
3. Con che tempistiche
4. Con quali prodotti ottenuti

Il piano serve ai manager per misurare il **progresso** e fare **decisioni** informate (soprattutto se il piano viene fatto prima di partire, permette di risolvere subito i primi problemi).

**Scheduling** = Suddividere il lavoro in task e decidere come saranno realizzate. Cioè:

- Tempo da calendario richiesto
- Effort (quanti giorni-uomo)
- Chi lo fa
- Altre risorse richieste
- Deadline
- Punto di fine ben definito (meeting, produzione documento, passaggio di tutti i test, etc.)

Bisogna cercare di schedulare le task in parallelo e con meno dipendenze possibile.

**Milestone** = Punto importante nella schedule in cui verificare il progresso. Ad esempio: consegna del codice per essere testato.

**Deliverable** = Cosa da consegnare al cliente. Tipicamente a una milestone può corrispondere o meno un deliverable.

(**ATTENZIONE**: Il diagramma di Gantt è una tipica domanda d'**esame**)

<img src="img/2023-01-21-15-04-48.png" style="zoom: 67%;" />

<img src="img/2023-01-21-15-05-01.png" style="zoom:67%;" />

(I rettangoli con diagonale indicano una partecipazione parziale. Magari quella persona è già impegnata con un'altra task in un altro progetto)

#### Agile planning

Contrapposto ad un planning rigido fatto subito, l'agile usa un processo di pianificazione **interattivo** e **continuo**. Software consegnato ad incrementi al cliente e le feature incluse in un incremento si decidono di volta in volta con il cliente che aiuta a prioritizzare.

Planning incrementale su due fronti:

- **Release**: decidere feature da includere in una release
- **Iteration**: (cadenza più regolare) decidere feature da includere in un incremento (non tutti gli incrementi corrispondono a release formali e grosse)

<img src="img/2023-01-21-15-09-44.png" style="zoom:80%;" />

Release (qualche mese) = Tante iterations (ciascuna un paio di settimane)

- Story Identification & Initial Estimation = Cliente e team **scrivono** le **user stories** e gli **scenari** con le feature che il SW deve avere. Stories grandi sono spezzate in piccole ed eventualmente si aggiunge dettaglio a qualche sezione usando gli scenari. Viene assegnato un **stima** dell'effort necessario per completare ogni story. Con la **velocity** (la cui stima migliora con il tempo) si può stimare il tempo richiesto per sviluppare il sistema.
- Release Planning = Si **scelgono** le stories/scenari mettere nella prossima **release** e in che ordine svilupparle.
- Iteration Planning = Si **scelgono** le stories/scenari della release da sviluppare in questa **iterazione**. Le stories/scenari sono **divise in piccole task card** (ciascuna da 4-16 ore di sviluppo, è un'unità di lavoro atomica) e ognuno si **sceglie** quelle che vuole sviluppare. Ogni tanto si guarda il progresso raggiunto e si decide se **togliere** qualche stories/scenario (ma la deadline non cambia! al massimo si fanno meno feature).

Pros & Cons sono già stati descritti parlando di Agile e SCRUM. L'unica cosa aggiunta qui è che gli svilupattori scelgono le task che vogliono sviluppare. Quindi lavorano con più entusiasmo e serenità.
## 09 - UML

Unified Modelling Language = Insieme di notazioni grafiche che supportano la _descrizione_ e il _design_ di sistemi software. Si astrae in modo da mostrare solo i componenti principali e le loro relazioni.

Digrammi servono per:

- **Capire** il dominio e il sistema
- **Proporre** soluzioni e **discutere**
- Prendere **decisioni**
- **Documentare** il sistema

Sketch sulla lavagna $\rightarrow$ Diagrammi UML $\rightarrow$ Codice

(Ci sono anche strumenti di reverse engineering che prendono del codice e ne costruiscono il diagramma UML)

Tassonomia:

- Structural
    - **Class** diagram (**statico**: struttura del codice)
    - **Object** diagram (**dinamico**: struttura del sistema quando in esecuzione)
- Behavioral
    - Interaction (talvolta si trova come categoria completamente separata e parallela ai behavioral diagrams)
        - Use-case diagram (diversi livelli di astrazione: fish poi sea poi kite)
        - Sequence diagram (descrivono in dettaglio un **singolo use case** nell'interazione di diversi attori)
    - Activity diagram (**data driven**: mostra come il sistema processa i dati)
    - State machine diagram (**event driven**: mostra come il sistema reagisce agli stimoli esterni)

(Per il resto, guarda le slide)
