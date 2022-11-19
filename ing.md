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

_Le attività_ di un processo vengono _pianificate_ secondo un mix di queste tecniche:
- Plan Driven: si pianifica tutto subito e poi si inizia il processo SW tracciando progresso
- Agile: si pianifica mano a mano che il processo prosegue. Più facile reagire a cambiamenti

Pianificazione delle attività $\neq$ Specifica del prodotto (cioè requisiti)

Vediamo alcuni _modelli_ di processi, ogni processo _reale_ prende aspetti da >1 di questi.

### Alcuni processi
Nel **Code & Fix** si va per tentativi. Nessuna fase di analisi o design, si va dritti all'implementazione. Alla fine si controlla se è ok altrimenti si fixa il codice e repeat. Non considerato un vero processo.

---

Il **Waterfall** è sempre **Plan Driven**. Specifica del prodotto e poi sviluppo, niente interlacciamento. Stampo industriale e manifatturiero. Output attività $i$ = Input attività $i+1$ e output freezati una volta all'attività $i+1$.

Le attività sono:
1. Raccolta e definizione requisiti
2. Design
3. Implementazione e test di ogni componente in isolamento
4. Integrazione e test dei componenti insieme.
5. Consegna al cliente e manutenzione.

Pros & Cons:
+ $+$ Enfasi su analisi requisiti e design fatti bene, implementazione lasciata per ultima
+ $+$ Disciplinato
+ $-$ Funziona solo se requisiti sono chiari e stabili
+ $-$ Difficile accomodare cambi ai requisiti. Visto che sono l'output della prima attività e tutti output sono freezati.

Buono per:
- Embedded, cambi al HW difficili e costosi
- Sistemi critici, serve tanta analisi e tutto documentato
- Organizzazioni grandi e complesse

---

**Sviluppo Incrementale** ha attività di specifica, sviluppo e validazione interlacciate. SW consegnato per incrementi. Pianificazione delle attività stesse può essere **Plan Driven oppure Agile**.

<img width="400px" src="img/2022-11-19-15-23-53.png"/>

Pros & Cons:
- $+$ Costi ridotti per reagire ai cambiamenti
- $+$ Rapidissima consegna delle feature essenziali, cliente inizia subito ad usare il SW
- $+$ Maggiore feedback dagli stakeholder che usano subito il SW, requisiti per successivi incrementi saranno presi con maggiore consapevolezza
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

<img width="600px" src="img/2022-11-19-15-21-25.png"/>

Pros & Cons:
- $+$ Basso costo di soldi e tempo
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

<img width="400px" src="img/2022-11-19-16-04-22.png"/>

---

- **Design**: tradurre specifica in descrizione struttura SW, modelli dati, interfacce tra componenti.
    - **Design architettura**. Overall structure of SW, componenti e relazioni tra di loro
    - **Design db**
    - **Design interfacce**. Come comunicano i componenti. Con una interfaccia precisa, i componenti possono essere utilizzati senza conoscere l'implementazione e possono essere sviluppato in isolamento.
    - **Selezione e design componenti**. Cerco componenti esistenti e pianifico modifiche necessarie, oppure design componenti da creare da zero.
- **Implementazione**: tradurre design in SW.

Le due fasi possono essere interlacciate. Cambiano molto da progetto a progetto, a seconda del dominio (ad esempio un progetto embedded probabilmente non avrà db design)

---

**Validazione** è controllare che SW rispetti requisiti. Controlli manuali oppure test con dati. Test case derivanti dalla specifica iniziale.

1. Component testing, in isolamento. Test case scritti da stesse persone che hanno sviluppato componente. Automatici (unit testing). Già fatto anche durante implementazione di solito.
2. System testing, integro tutti componenti e testo sistema per intero.
3. Acceptance testing, fatto dal cliente stesso con dati realistici. Fa emergere omissioni nella specifica.

Nel processo waterfall in particolare (plan driven) testing potrebbe essere secondo modello a V, rispecchia le varie attività del processo stesso:

<img width="600px" src="img/2022-11-19-16-18-07.png"/>

---

**Evoluzione** modifica SW per adattarsi ai cambiamenti del business.

- **Change anticipation**: accorgersi in fretta di possibili cambiamenti futuri, prima che diventino troppo costosi da risolvere (più si aspetta e più il SW evolve ed è difficile da modificare).
- **Change tolerance**: processo fatto in modo da accomodare cambiamenti.

Metodi:
- **Prototipi**. Durante fare di **specifica** per facilitare raccolta e specifica requisiti. Oppure durante **design** per esplorare soluzioni diverse.
- **Consegna incrementale**. Vedi il processo incrementale. Non posso fare consegna incrementale senza un processo incrementale e viceversa, sono un po' sinonimi.