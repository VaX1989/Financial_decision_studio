# FINANCIAL DECISION STUDIO
## Guida completa all'utilizzo

**Versione documentata:** Financial Decision Studio 3.0.0  
**Engine:** 3.0.0  
**Schema:** 2.1.0  
**Build:** `FDS-DEFINITIVE-20260826`

---

## Come usare questa guida

Financial Decision Studio usa un'interfaccia in inglese. In questa guida i nomi reali dell'interfaccia sono mantenuti in inglese e spiegati in italiano, per esempio **Liquid Net Worth — patrimonio netto liquido**.

Se vuoi iniziare subito, leggi **Parte II — Inizia in 5 minuti** e poi **Parte IV — Dashboard e KPI**. Se stai confrontando alternative, passa a **Parte V — Decisions**. Se vuoi capire la probabilità e la fragilità di una decisione, usa **Parte VIII — Lab**. Le sezioni su **Data**, **Audit** ed **Expert plan JSON** sono pensate soprattutto per utenti avanzati.

> **Importante —** Financial Decision Studio è uno strumento di pianificazione e analisi di scenari. Non è una promessa sul futuro, non è un software fiscale dichiarativo e non sostituisce consulenza finanziaria, fiscale, legale o assicurativa professionale.

---

# Parte I — Introduzione

## 1. Che cos'è Financial Decision Studio

Financial Decision Studio è un'applicazione di pianificazione finanziaria personale contenuta in un singolo file HTML. Costruisce una proiezione mensile della situazione economico-patrimoniale di un nucleo familiare e permette di confrontare decisioni alternative mantenendo esplicite le ipotesi.

Il modello può rappresentare, tra le altre cose:

- cassa e investimenti;
- redditi e spese;
- abitazione principale, affitto e mutuo;
- immobili aggiuntivi;
- altri debiti;
- obiettivi finanziari;
- eventi futuri;
- premi e benefici assicurativi configurati;
- regole di riserva, investimento del surplus e ribilanciamento;
- tassazione secondo i tax pack disponibili;
- scenari alternativi;
- simulazione Monte Carlo parametrica;
- analisi di robustezza, sensitivity e attribution;
- confronto **Actual vs plan**;
- registro contabile a partita doppia per rendere verificabili i movimenti.

L'obiettivo non è produrre un unico numero “magico”, ma aiutarti a rispondere a domande come:

- Posso permettermi davvero questa casa senza compromettere la liquidità?
- Mi conviene destinare una certa somma al mutuo oppure agli investimenti?
- Quanto dipende la scelta affitto/acquisto dal tasso del mutuo o dal rendimento atteso?
- Il mio obiettivo patrimoniale è raggiungibile solo nello scenario centrale oppure anche sotto ipotesi meno favorevoli?
- Dopo un anno, la realtà si sta discostando dal piano? E come devo aggiornare il futuro senza cancellare il passato?

## 2. Filosofia del prodotto: decisioni, non predizioni

Financial Decision Studio separa tre livelli che è utile non confondere:

**Piano** — descrive la tua situazione iniziale, i flussi previsti e le regole che vuoi applicare.

**Scenario** — modifica uno o più elementi del piano per rappresentare un'alternativa: comprare casa, restare in affitto, andare in pensione prima, aumentare il risparmio, cambiare LTV e così via.

**Simulazione** — calcola le conseguenze delle ipotesi. La simulazione deterministica usa i valori attesi inseriti; Monte Carlo genera molti percorsi possibili attorno a quelle ipotesi.

Una previsione afferma implicitamente “questo è ciò che accadrà”. Una pianificazione seria dice invece: “se queste ipotesi e questi comportamenti fossero ragionevoli, quali conseguenze avrei e quali rischi emergerebbero?”. Financial Decision Studio appartiene alla seconda categoria.

## 3. Local-first, offline e file singolo

L'applicazione è progettata per funzionare **local-first**: il calcolo avviene nel browser e il prodotto non richiede un backend o una connessione di rete per funzionare. Puoi conservare il file sul dispositivo e aprirlo come normale documento HTML.

Questo ha due conseguenze pratiche:

1. i dati del piano non devono essere inviati a un server del prodotto per essere elaborati;
2. la persistenza locale dipende però dalle capacità e dalle politiche del browser, soprattutto quando l'HTML viene aperto tramite `file://`.

Per questo la strategia corretta non è affidarsi esclusivamente allo storage del browser, ma mantenere periodicamente una copia **Plan JSON** o **Portable HTML**.

## 4. Il modello mentale essenziale

Prima di usare l'app, conviene distinguere sei concetti.

| Concetto | Significato pratico |
|---|---|
| **Patrimonio / Net Worth** | Attività meno passività. Include anche beni non immediatamente spendibili, come un immobile. |
| **Liquidità / Accessible Wealth** | Cassa più investimenti liquidi stimati al netto dell'eventuale tassazione latente sulle plusvalenze. |
| **Liquid Net Worth** | Liquidità accessibile meno i debiti che restano economicamente a carico del patrimonio. |
| **Reddito** | Risorsa economica che entra dall'esterno del patrimonio, per esempio stipendio o pensione. |
| **Spesa** | Costo consumato: riduce il patrimonio, per esempio affitto, interessi, manutenzione o consumi. |
| **Trasferimento patrimoniale** | Sposta valore da una forma a un'altra senza essere, di per sé, una spesa. Esempi: comprare un investimento o rimborsare capitale di un mutuo. |

> **Esempio —** Se versi 1.000 € dalla cassa a un ETF, hai meno cassa e più investimenti, ma non hai “speso” 1.000 € in senso patrimoniale. Se invece paghi 1.000 € di interessi o di affitto, quei 1.000 € sono un costo consumato.

---

# Parte II — Inizia in 5 minuti

## 5. I tre percorsi iniziali

Alla prima apertura senza un piano già salvato, Financial Decision Studio mostra tre possibilità.

### Quick Decision

Apre direttamente **Decisions → Rent vs Buy**. È il percorso più rapido se la tua domanda è specifica: “affitto o acquisto?”. Non devi prima compilare l'intero modello familiare.

Usalo se vuoi fare un primo confronto controllato e capire quali ipotesi spostano il risultato. Se il confronto diventa importante, trasforma poi le alternative in scenari del modello completo con **Create Rent / Buy scenarios**.

### Explore example

Mantiene aperto il piano dimostrativo preconfigurato. È il modo migliore per imparare l'interfaccia senza inserire subito dati personali.

Prova a cambiare un'ipotesi alla volta in **Fast assumptions**, passa da **Plan** a **Decisions**, osserva **Goals** e infine esegui una simulazione in **Lab → Risk**.

### Build my plan

Avvia un wizard in cinque passaggi:

1. **Household** — nome del piano, numero di adulti, anno di nascita e anno pensionistico indicativo;
2. **Current position** — cassa, investimenti, situazione abitativa, valore della casa e mutuo se posseduta;
3. **Monthly cash flow** — reddito netto familiare mensile, spese essenziali e affitto se applicabile;
4. **Main goal** — obiettivo patrimoniale, anni al target e importanza del goal;
5. **Assumptions review** — orizzonte, inflazione e rendimento atteso dell'azionario globale.

Il piano creato dal wizard usa il tax pack **Generic / user-net inputs**, quindi non applica automaticamente una tassazione sul reddito; usa inoltre l'allocazione diversificata di esempio, che puoi modificare in seguito.

## 6. Percorso consigliato per un nuovo utente

Per un piano personale completo, il percorso più sicuro è:

1. avvia **Build my plan**;
2. compila solo valori ragionevoli e facilmente verificabili;
3. nella schermata **Plan**, controlla subito **Liquid Net Worth** e **Liquidity Runway**;
4. passa a **Detailed** per separare redditi, spese, investimenti e abitazione;
5. apri **Goals** e definisci cosa vuoi ottenere;
6. crea una sola decisione alternativa in **Decisions**;
7. confronta deterministicamente gli scenari;
8. solo dopo esegui **Lab → Risk**.

> **Suggerimento —** Non cercare di modellare tutto al centesimo al primo utilizzo. È più utile avere una baseline coerente e trasparente che un modello estremamente dettagliato costruito su ipotesi incerte.

## 6.1 Orientarsi nell'interfaccia

La navigazione principale contiene cinque aree: **Plan**, **Decisions**, **Goals**, **Optimize** e **Lab**. Su desktop sono nella barra laterale; su schermi mobili diventano la navigazione inferiore.

Nell'header trovi inoltre:

- l'indicatore **Inputs valid** oppure il numero di warning/blocking issues;
- **Undo** e **Redo** quando disponibili;
- lo stato di salvataggio;
- **Share**;
- **Export**, che esporta il Plan JSON;
- il comando per tema chiaro/scuro;
- il menu **⋯ → Data, storage & sharing**.

Nel menu dati trovi anche **Print / PDF**, **Expert JSON editor**, il controllo della privacy mode e l'accesso diretto a **Data Lab**.

In **Plan** sono disponibili anche **Blank plan**, che sostituisce il piano in memoria dopo conferma, **Checkpoint**, che tenta il salvataggio locale, e **Reset example** nel riquadro Fast assumptions.

---

# Parte III — Costruire il proprio piano

## 7. Simple, Detailed ed Expert

Nella pagina **Plan** puoi scegliere tre livelli di disclosure.

### Simple

Mostra KPI, grafici e **Fast assumptions**. È pensato per modificare rapidamente le variabili più importanti:

- Analysis horizon;
- Starting cash;
- Monthly income;
- Essential living costs;
- Housing strategy;
- Monthly rent oppure Home price;
- Rent growth oppure Mortgage rate e LTV;
- Equity expected return;
- Inflation;
- Minimum cash reserve;
- Additional net cash flow.

**Additional net cash flow** è una risorsa esterna aggiuntiva mensile. Non è un trasferimento della cassa già esistente e non va usata per rappresentare un PAC finanziato dallo stesso reddito già inserito.

### Detailed

Aggiunge gli editor strutturati per:

- **Income & expenses**;
- **Portfolio**;
- **Housing & debt**;
- **Actual vs plan**.

### Expert

Mantiene le stesse informazioni del piano e segnala che la configurazione completa è disponibile soprattutto in **Lab → Data / Audit** e nell'**Expert plan JSON editor**.

> **Attenzione —** Cambiare livello Simple/Detailed/Expert non cambia la finanza del piano. Cambia solo ciò che l'interfaccia espone.

## 8. Household — nucleo familiare

Percorso: **Lab → Data → Household members**.

Per ogni persona puoi configurare:

- Name;
- Role: **Adult** o **Dependent**;
- Birth year;
- Retirement year.

Il modello mantiene almeno un membro del nucleo. I flussi di reddito possono essere associati a persone specifiche tramite configurazione Expert; il template Retirement usa la timeline dell'adulto principale come riferimento indicativo.

Il nucleo familiare non è un motore demografico o attuariale: anno di nascita e pensionamento servono principalmente a organizzare il piano e ad assistere alcuni template.

## 9. Starting Cash — cassa iniziale

In **Plan → Simple → Fast assumptions**, **Starting cash** modifica la cassa iniziale principale.

La cassa è importante per tre ragioni:

- finanzia le spese e gli obblighi prima di vendere investimenti;
- determina parte della liquidità disponibile;
- alimenta la riserva protetta dalle policy.

Non inserire qui disponibilità che in realtà non sono immediatamente utilizzabili. Un fondo vincolato o un bene non liquido non è equivalente alla cassa.

## 10. Accounts, Assets e Positions

Il modello distingue concettualmente:

**Account** — contenitore finanziario, per esempio cassa o conto di investimento tassabile.

**Asset** — lo strumento o classe di investimento con proprie ipotesi di rendimento, volatilità, distribuzioni e commissioni.

**Position / Holding** — la posizione effettivamente detenuta, con valore di mercato, cost basis e peso target.

L'interfaccia normale espone soprattutto gli asset/holding attraverso **Plan → Detailed → Portfolio**. La gestione completa di account e più posizioni dello stesso asset è una capacità avanzata dello schema e non dispone, in questa versione, di un editor grafico completo dedicato.

### 10.1 Campi dell'editor Asset

Con **+ Asset** o **Edit** puoi impostare:

- Name;
- Asset class: equity, bond, alternative, cash, other;
- Return model;
- Expected annual return;
- Distribution yield;
- Annual volatility;
- Annual fee;
- Opening value;
- Cost basis;
- Target weight.

Dopo il salvataggio, i target weight positivi vengono normalizzati rispetto al totale.

### 10.2 Total return vs Price return + distributions

**Total return** significa che il rendimento atteso include già eventuali distribuzioni. In questa modalità il **Distribution yield** deve essere zero.

**Price return + distributions** separa invece:

- crescita del prezzo;
- distribuzioni periodiche.

Questa distinzione evita di contare due volte lo stesso rendimento.

### 10.3 Cost basis

Il **Cost basis** è il costo fiscale attribuito alla posizione. Serve per stimare la plusvalenza latente e quindi:

- il valore realmente accessibile dopo un'eventuale vendita;
- la tassazione delle liquidazioni;
- il costo fiscale di ribilanciamenti o vendite forzate.

> **Esempio —** Una posizione vale 100.000 €, ma ha cost basis 60.000 €. Se il tax pack applica una tassa alle plusvalenze, non è corretto considerare tutti i 100.000 € come liquidità netta disponibile.

## 11. Income — redditi

Percorso: **Plan → Detailed → Income & expenses → + Income**.

Campi disponibili:

- Name;
- Monthly / periodic amount;
- Frequency: monthly, quarterly, annual, one_time;
- Annual growth;
- Start month;
- End month;
- Tax mode: **Net amount** oppure **Gross — apply tax pack**.

Se selezioni **Net amount**, il flusso viene trattato come già netto. Se selezioni **Gross**, il tax pack attivo viene usato per il modello fiscale semplificato.

Per piani che iniziano a metà anno, lo schema supporta anche informazioni fiscali di apertura dell'anno tramite configurazione Expert, in modo da non trattare una frazione d'anno come se fosse un anno fiscale completamente isolato.

## 12. Expenses — spese

Percorso: **Plan → Detailed → Income & expenses → + Expense**.

Oltre a importo, frequenza, crescita e periodo, scegli la priorità:

- **Essential** — spesa essenziale;
- **Discretionary** — spesa discrezionale.

La distinzione è importante. Le spese essenziali contribuiscono al calcolo della riserva e della **Liquidity Runway**. Una spesa discrezionale può essere trattata diversamente quando la liquidità è scarsa.

> **Attenzione —** Una spesa non è la stessa cosa di un acquisto di asset o del rimborso di capitale. Il Ledger mantiene questa separazione.

## 13. Housing — affitto

Percorso: **Plan → Detailed → Housing & debt → Edit**.

Per l'affitto puoi impostare:

- Strategy = Rent;
- Rent entry state: Existing lease o New lease at plan start;
- Monthly rent;
- Rent annual growth;
- Security deposit months;
- Rental entry costs.

Il deposito cauzionale viene trattato come attività patrimoniale, non come spesa immediata. Quando è configurata una fine del contratto, il motore può liquidare il deposito distinguendo quota recuperata e quota persa. La fine del contratto e la percentuale di perdita del deposito sono parametri avanzati accessibili tramite **Expert plan JSON** nella versione attuale.

Dopo la fine del contratto configurata, il modello non continua a registrare il canone.

## 14. Housing — proprietà e mutuo

Nello stesso editor puoi scegliere **Own / buy** e configurare:

- Ownership state: Purchase at plan start oppure Already owned;
- Home price / current value;
- LTV for new purchase;
- Current mortgage balance;
- Mortgage rate;
- Mortgage term years;
- Remaining term years;
- Extra principal / month;
- Purchase costs;
- Maintenance rate;
- Property-tax rate;
- Insurance / year;
- Home appreciation;
- Sale cost rate;
- Terminal sale-tax assumption.

### 14.1 Acquisto nuovo vs casa già posseduta

Se scegli **Purchase at plan start**, LTV e prezzo servono a determinare il finanziamento iniziale.

Se scegli **Already owned**, la variabile economicamente rilevante per il debito esistente è **Current mortgage balance**, insieme a tasso e durata residua. Per questo i solver di prezzo/LTV non vengono applicati come se la casa già posseduta fosse un nuovo acquisto.

### 14.2 Capitale e interessi

La rata del mutuo contiene due componenti:

- **principal** — riduce il debito; è un trasferimento patrimoniale;
- **interest** — costo consumato; è una spesa.

Questo è il motivo per cui una rata da 1.000 € non equivale automaticamente a “1.000 € di spesa”. La parte capitale riduce una passività e quindi non distrugge patrimonio nello stesso modo degli interessi.

### 14.3 Extra principal

**Extra principal / month** indica un rimborso aggiuntivo del mutuo. È un'allocazione opzionale e rispetta la regola della riserva: il motore non dovrebbe sacrificare la riserva protetta solo per eseguire un prepayment opzionale.

## 15. Additional Properties — immobili aggiuntivi

Percorso: **Lab → Data → Additional properties**.

Campi disponibili:

- Name;
- Current / purchase value;
- Purchase month, con 0 = già posseduto;
- Purchase costs;
- Sale month, vuoto = mantenimento;
- Sale cost rate;
- Sale tax / disposal-tax assumption;
- Appreciation;
- Maintenance rate;
- Property tax rate;
- Insurance / year;
- Rental income / month;
- Rent growth;
- Vacancy rate.

Se programmi una vendita, il modello richiede un'ipotesi esplicita per **Sale tax / disposal-tax assumption**: inserisci 0 solo se vuoi deliberatamente assumere nessuna tassa di dismissione.

Il valore dell'immobile, i costi di vendita, la tassa configurata e gli eventuali debiti collegati sono concetti distinti. Non interpretare quindi il prezzo di vendita lordo come denaro immediatamente disponibile.

## 16. Liabilities — altri debiti

Percorso: **Lab → Data → Other liabilities**.

Tipi disponibili:

- fixed amortizing;
- interest only;
- balloon.

Campi principali:

- Principal / current balance;
- Annual rate;
- Term months;
- Start month;
- Extra principal / month.

**Start month = 0** rappresenta un debito già esistente. Un mese futuro rappresenta nuovo finanziamento: in quel momento il modello accredita i proventi del prestito alla cassa e crea la passività.

Tassi negativi sui debiti generici non sono una semantica supportata dalla simulazione e vengono bloccati dalla validazione.

## 17. Goals — obiettivi

I goal si gestiscono dalla pagina **Goals**. Vedi la Parte VI per la semantica completa.

Nel piano possono misurare:

- Net worth;
- Liquid wealth;
- Cash reserve.

Ogni goal ha una data, un target, una priorità e una base di valore nominale o in potere d'acquisto corrente.

## 18. Events — eventi di vita

Percorso: **Lab → Data → Life events**.

L'editor strutturato permette un'azione principale per evento:

- cash inflow;
- cash outflow;
- investment contribution;
- debt prepay.

Puoi configurare:

- Name;
- Month;
- Timing: Start of month o End of month;
- Amount;
- Liability ID per il prepayment.

Gli eventi creati dall'editor sono obbligatori. Prima di eseguire un evento, il motore verifica la capacità di finanziare le azioni obbligatorie; se non è possibile, il percorso può fallire invece di produrre una cassa artificialmente negativa.

**Expert plan JSON** consente eventi con più azioni nello stesso blocco.

## 19. Insurance & protection

Percorso: **Lab → Data → Insurance & protection**.

Puoi rappresentare:

- Monthly premium;
- Start month;
- End month;
- Benefit month opzionale;
- Benefit amount.

Il premio è un costo periodico. Il beneficio, se viene configurato un mese specifico, entra come flusso in quel mese.

> **Importante —** Questa è una rappresentazione deterministica di premi e benefici programmati. Non è un modello attuariale della probabilità di sinistro, della qualità della copertura o dell'adeguatezza assicurativa.

## 20. Financial Policies

Percorso: **Lab → Data → Financial policies**.

Tre tipi sono implementati:

### Reserve

Definisce quanti mesi di spese essenziali proteggere come riserva.

### Invest surplus

Può investire una frazione del surplus sopra la riserva. La **Surplus invest fraction** va da 0 a 1.

### Rebalance

Definisce:

- frequenza di ribilanciamento in mesi;
- tolerance band percentuale.

Il ribilanciamento usa prima la cassa disponibile per acquistare gli asset sottopesati e ricorre alle vendite solo quando necessario; le vendite tassabili tengono conto del cost basis.

Le policy sono ordinate per **Priority** e, dove applicabile, prevalgono sulle impostazioni equivalenti più vecchie del piano.

> **Importante —** La riserva protegge soprattutto le **allocazioni opzionali** come investimento pianificato, investimento del surplus e prepayment extra. Non è una cassaforte intoccabile davanti a un obbligo essenziale: se una spesa obbligatoria deve essere pagata, il funding waterfall può usare la cassa disponibile e, se necessario, vendere investimenti; se le risorse accessibili restano insufficienti, il path fallisce.

## 21. Assumptions e tax pack

Percorso: **Lab → Data → Assumptions & tax pack**.

Qui trovi:

- Inflation;
- Tax pack;
- Tax pack version;
- Investment capital gain;
- Investment income;
- Investment stamp assumption;
- Mortgage interest credit;
- Edit asset correlation matrix.

### Generic / user-net inputs

Non calcola automaticamente un'imposta sul reddito. È adatto quando inserisci flussi già netti o vuoi evitare che il modello applichi un sistema fiscale semplificato.

### Italy 2026 planning pack

La versione fornita contiene un modello di pianificazione con:

- aliquote IRPEF nazionali headline 23% / 33% / 43% per gli scaglioni configurati;
- ipotesi generica del 26% per capital gain e redditi finanziari contemplati dal modello;
- ipotesi annua dello 0,20% per l'imposta di bollo sugli investimenti;
- modello semplificato di credito/detrazione per interessi del mutuo dell'abitazione principale al 19% con cap configurato di 4.000 € di interessi eleggibili.

Queste sono **ipotesi di pianificazione**, non un calcolo fiscale ufficiale. Il pack omette o semplifica, tra l'altro, addizionali regionali e comunali, deduzioni, crediti, interazioni per redditi elevati, regimi specifici degli strumenti, trattamento preferenziale di titoli sovrani, requisiti dettagliati di eleggibilità e future modifiche normative.

Se l'orizzonte supera l'anno di efficacia del pack, l'app segnala il problema e usa la regola configurata di mantenimento delle ultime ipotesi, non una previsione certa della legislazione futura.

## 22. Correlation matrix

La matrice di correlazione viene usata nella simulazione Monte Carlo per generare shock coerenti tra gli asset.

La matrice deve avere:

- una riga e una colonna per ogni driver/asset attivo;
- diagonale pari a 1;
- simmetria;
- correlazioni tra -1 e +1;
- struttura matematicamente valida, cioè positiva semidefinita.

Una correlazione perfetta può essere valida; una matrice incoerente viene bloccata dalla validazione.

---

# Parte IV — Dashboard e KPI

## 23. Projected Net Worth — patrimonio netto proiettato

### Cosa significa

È il patrimonio netto alla fine dell'orizzonte del piano:

**attività − passività**.

Comprende cassa, investimenti, immobili e altre attività riconosciute dal modello, sottraendo i debiti.

### Come viene utilizzato

È il principale indicatore patrimoniale di lungo periodo e alimenta molte comparazioni tra scenari.

### Come interpretarlo

Usalo per capire la scala patrimoniale finale del piano e per confrontare strategie con le stesse risorse iniziali.

### Attenzione a

Un patrimonio netto elevato non significa necessariamente elevata liquidità. Una grande quota può essere immobilizzata in una casa. Inoltre il valore ordinario di Net Worth non equivale automaticamente al valore netto dopo una liquidazione completa.

## 24. Liquid Net Worth — patrimonio netto liquido

### Cosa significa

Il modello parte da **Accessible Wealth**, cioè:

**cassa + valore stimato degli investimenti liquidi dopo l'eventuale tassazione latente delle plusvalenze**.

Poi calcola:

**Liquid Net Worth = Accessible Wealth − debiti**.

### Come interpretarlo

È molto più utile del Net Worth quando la domanda è: “quanto margine finanziario realmente mobilizzabile ho, tenendo conto dei debiti?”.

### Attenzione a

Non è semplicemente cassa + valore lordo del portafoglio. E non include automaticamente il valore di un immobile come liquidità disponibile.

> **Segnale di rischio —** Un piano può avere Projected Net Worth positivo ma Liquid Net Worth debole o negativo. È una situazione che merita attenzione, perché la solvibilità patrimoniale non sostituisce la capacità di finanziare gli obblighi nel tempo.

## 25. Primary Goal

### Cosa significa

Mostra il funding ratio del primo goal configurato nel piano, insieme a priorità e stato.

### Come interpretarlo

100% indica che il valore della metrica ha raggiunto il target nominale calcolato alla data del goal. Valori inferiori indicano quanto del target è coperto.

### Attenzione a

Con più goal, il KPI non sostituisce la pagina **Goals**: è un riepilogo del primo obiettivo, non una sintesi completa di tutti gli obiettivi.

## 26. Liquidity Runway — autonomia di liquidità

### Cosa significa

È una stima dei mesi per cui la ricchezza accessibile potrebbe coprire l'uscita essenziale media recente. Il motore usa la liquidità accessibile e una media mobile delle spese essenziali.

### Come interpretarlo

Più è alto, maggiore è il cuscinetto. La UI evidenzia in modo più severo runway inferiori a 6 mesi e con cautela quelli inferiori a 12 mesi.

### Cosa NON significa

Non è una garanzia che puoi smettere di lavorare per quel numero di mesi senza conseguenze. Non incorpora automaticamente ogni comportamento futuro o ogni shock reale.

### Segnale di rischio

Una runway bassa significa che un imprevisto può costringere il piano a vendere investimenti, ridurre spese discrezionali o fallire un obbligo.

## 27. Debt Free

### Cosa significa

Mostra il primo mese futuro in cui il debito totale scende sotto la soglia tecnica del modello.

### Come interpretarlo

È utile per vedere quando mutuo e altri debiti si azzerano nel percorso corrente.

### Attenzione a

Se hai configurato un nuovo prestito in un mese successivo, questa è la **prima** data di debito zero, non necessariamente la prova che non avrai mai più debito dopo quella data.

## 28. Plan Status

La logica effettiva distingue:

**Incomplete** — il piano ha un problema di validazione che impedisce la simulazione.

**Off track** — la simulazione fallisce per liquidità oppure un goal richiesto Hard/Target è sotto la propria soglia minima.

**Needs attention** — un goal di tipo Target si trova nella fascia marginale tra minimum e target.

**At risk** — il deterministico non fallisce, ma dopo una simulazione Risk la probabilità complessiva di successo dei goal richiesti è inferiore alla soglia configurata del piano, 90% di default.

**On track** — nessuna delle condizioni precedenti è attiva.

> **Importante —** Prima di eseguire Monte Carlo, **On track** è soprattutto una valutazione deterministica. Non interpretarlo come “90% di probabilità di successo” se non hai ancora eseguito **Lab → Risk**.

## 29. I grafici della pagina Plan

### Wealth trajectory

Mostra l'evoluzione del **Net Worth** e del **Liquid Net Worth**. Puoi toccare o passare con il mouse per ispezionare, trascinare orizzontalmente per fare zoom e usare doppio tap/doppio clic per resettare.

### Balance-sheet composition

Mostra come cambiano nel tempo investimenti, proprietà e debito. È utile per capire *da dove* deriva il patrimonio e non solo quanto vale.

---

# Parte V — Decisions

## 30. Baseline e scenari

La **Baseline** è il piano di riferimento. Gli altri scenari sono rami che ereditano il piano padre e memorizzano solo le differenze.

Questo ha una conseguenza importante: **Branch** non significa copia congelata. Se la baseline cambia, un ramo continua a ereditarne gli elementi che non ha sovrascritto.

Nello **Scenario manager** trovi:

- Scenario;
- Net worth;
- Liquid;
- Goal;
- Min runway;
- Status;
- comandi Branch/Edit/Delete dove applicabili.

Lo status della tabella scenario, **Feasible/Failed**, descrive soprattutto la fattibilità del percorso. Non va confuso con il più articolato **Plan Status**.

## 31. Creare uno scenario

Con **+ Scenario** puoi creare un ramo manuale. L'editor avanzato chiede:

- Name;
- Parent scenario;
- Patches JSON.

Le patch rappresentano cambi deterministici rispetto al parent, per esempio modificare il tasso del mutuo. Questo editor è pensato per utenti avanzati. Per le decisioni comuni, i template sono più sicuri e veloci.

## 32. Il principio di confronto equo

Un confronto è utile solo se le alternative partono dalle stesse risorse, salvo ciò che vuoi deliberatamente cambiare.

Se “Investire” riceve 500 € al mese di reddito extra mentre “Prepagare il mutuo” no, non stai confrontando due strategie: stai confrontando due famiglie con risorse diverse.

Financial Decision Studio cerca di evitare questo errore nei template controllati, ma spetta a te mantenerlo quando costruisci scenari manuali.

## 33. Rent vs Buy

Il template **Rent vs Buy** è un modello focalizzato e controllato. L'interfaccia rapida espone:

- Home price;
- Monthly rent;
- Mortgage rate;
- Loan-to-value;
- Home appreciation;
- Portfolio return.

Usa anche altre ipotesi del piano, tra cui orizzonte, crescita dell'affitto, deposito, costi di acquisto, manutenzione, durata mutuo, commissioni del portafoglio e costi di vendita.

Risultati principali:

- **Rent + invest**;
- **Buy with mortgage**;
- **Mortgage − Rent**;
- **Mortgage payment**.

Il confronto equalizza le risorse necessarie nel modello focalizzato: l'opzione più economica può investire la differenza, invece di far apparire il confronto favorevole solo perché una strategia “spende meno” senza contabilizzare il capitale residuo.

### Create Rent / Buy scenarios

Crea due scenari nel motore finanziario completo partendo dalla stessa baseline:

- Rent + invest;
- Buy with mortgage.

È il passaggio consigliato quando il confronto rapido diventa una decisione reale: dopo la creazione dei rami puoi usare Dashboard, Goals e Risk sul modello completo.

> **Attenzione —** I due rami canonici trasferiscono le principali **ipotesi abitative** del template. Il campo focalizzato **Portfolio return** usato nel confronto Rent vs Buy non viene scritto automaticamente nell'asset della baseline quando premi Create Rent / Buy scenarios. Se lo hai cambiato soltanto nel template, allinea anche l'**Expected annual return** dell'asset nel piano prima di usare i rami canonici per una decisione definitiva.

## 34. Esempio completo — continuare in affitto vs acquistare casa

Immagina:

- casa: 250.000 €;
- affitto: 900 €/mese;
- mutuo: 3,5%;
- LTV: 80%;
- apprezzamento casa: 2% annuo;
- rendimento portafoglio: 5% annuo.

Procedura:

1. apri **Decisions → Rent vs Buy**;
2. inserisci i sei valori;
3. osserva **Mortgage − Rent**;
4. non fermarti al segno positivo/negativo: apri **Open sensitivity**;
5. verifica a quale tasso mutuo il risultato cambia segno;
6. crea **Rent / Buy scenarios**;
7. nel modello completo confronta anche **Liquid Net Worth** e **Min runway**;
8. esegui Monte Carlo sui due scenari;
9. controlla se il vincitore deterministico rimane il vincitore sotto incertezza;
10. considera infine preferenze personali: mobilità, stabilità abitativa, rischio occupazionale, desiderio di proprietà e capacità di gestire costi imprevisti.

Il punto non è ottenere “comprare è meglio” o “affittare è meglio” in assoluto. Il punto è capire **quali condizioni rendono vera una risposta**.

## 35. Prepay vs Invest

Richiede un piano con **Own / buy**.

Il template confronta:

- Scheduled mortgage only;
- Extra principal;
- Invest same cash allocation.

La stessa allocazione mensile viene destinata, alternativamente, a capitale del mutuo o investimenti. Non viene trattata come nuovo reddito esterno. Inoltre l'allocazione opzionale rispetta la riserva di liquidità.

Il valore mensile usato è l'**Extra principal / month** configurato sulla casa; se non ne hai impostato uno, il template usa un valore illustrativo minimo di 500 €/mese.

## 36. Refinance

Il template mostra un **economic screen** del rifinanziamento. Per una casa già posseduta usa saldo corrente e durata residua e confronta il pagamento attuale con un tasso illustrativo inferiore di un punto percentuale, con minimo zero.

Non include automaticamente:

- eleggibilità al nuovo mutuo;
- disponibilità di mercato;
- costi notarili o bancari;
- penali;
- tempi di esecuzione.

Per una decisione reale devi rappresentare costi e condizioni in uno scenario esplicito.

## 37. Retirement

Il template crea uno scenario che:

- termina il primo flusso di reddito selezionato al mese precedente al pensionamento;
- aggiunge un reddito mensile di pensione/retirement income;
- può aggiungere ulteriore spesa pensionistica;
- mantiene le altre spese esistenti, salvo tue modifiche.

È uno strumento di scenario cash-flow, non un modello attuariale completo di longevità, superstiti o long-term care.

## 38. Big Purchase

Il template crea un acquisto una tantum come **one-time essential expense**. È adatto a domande come:

- auto;
- ristrutturazione;
- grande spesa familiare.

Puoi poi creare rami alternativi per confrontare acquisto ora, rinvio, importo inferiore o finanziamento modellato separatamente.

---

# Parte VI — Goals

## 39. Cosa può misurare un goal

I tipi disponibili sono:

**Net worth** — patrimonio netto.

**Liquid wealth** — usa la definizione canonica di Liquid Net Worth del modello.

**Cash reserve** — cassa disponibile.

## 40. Hard, Target e Aspirational

### Hard

La soglia **minimum** è vincolante. In Monte Carlo, il goal Hard è considerato soddisfatto quando raggiunge almeno il minimum. Il target può rappresentare un livello più ambizioso.

### Target

Il successo richiede il raggiungimento del **target**. Se il risultato è sopra il minimum ma sotto il target, lo stato è marginale e il piano mostra **Needs attention**.

### Aspirational

È informativo: può essere raggiunto o mancato, ma non determina il fallimento complessivo dei goal richiesti.

## 41. Target e minimum

**Target** è l'obiettivo pieno.

**Minimum** è la soglia minima accettabile usata per distinguere una situazione marginale da una situazione off-track.

Nella versione corrente l'editor grafico standard di un goal permette di cambiare target, priorità, data e metrica, ma **non espone un campo separato per minimum**. Il wizard iniziale imposta:

- Hard: minimum = target;
- Target/Aspirational: minimum = 80% del target.

Il piano di esempio può avere un proprio minimum. Un goal creato direttamente con **+ Goal** inizializza invece `minimumValue` a 0 e l'editor standard non lo modifica. Se vuoi una soglia minima significativa e distinta dal target, devi quindi ispezionare o modificare esplicitamente `minimumValue` tramite **Lab → Data → Expert plan JSON**.

## 42. Target month

La data viene espressa come numero di mesi dall'inizio del piano. Per esempio, mese 120 = 10 anni.

Il goal deve trovarsi dentro l'orizzonte del piano.

## 43. Nominal at target vs Current purchasing power

### Nominal at target

Il valore che inserisci è la cifra nominale che vuoi vedere alla data futura.

### Current purchasing power

Il valore che inserisci rappresenta potere d'acquisto di oggi. Il motore lo rivaluta con l'ipotesi d'inflazione fino alla data del goal per ricavare la soglia nominale futura.

> **Esempio —** “Voglio un patrimonio equivalente oggi a 500.000 €” è concettualmente diverso da “voglio leggere 500.000 € nominali fra 25 anni”. Usa **Current purchasing power** nel primo caso.

## 44. Come leggere lo stato di un goal

**On track** — la metrica è almeno pari al target.

**Marginal** — la metrica è sotto il target ma almeno pari al minimum.

**Off track** — la metrica è sotto il minimum.

La progress bar mostra il rapporto tra risultato e target, mentre **Goal diagnostics** riporta il valore raggiunto e il target nominale alla data.

---

# Parte VII — Optimize

## 45. Cosa fa davvero Optimize

La pagina **Optimize** contiene solver deterministici limitati e trasparenti. Non usa NSGA-II, Differential Evolution o un ottimizzatore stocastico globale.

I risultati **non vengono applicati automaticamente**: puoi scegliere **Create scenario**, conservando la baseline.

## 46. Affordable home price

### Cosa cerca

Il prezzo massimo di un **nuovo acquisto** che conserva la soglia minima di liquidity runway configurata.

### Metodo

Ricerca deterministica limitata tramite bisezione.

### Vincoli

- nessun fallimento di percorso;
- minimum runway almeno pari alla riserva configurata;
- limite di ricerca del prezzo nella versione corrente: 1.500.000 €.

### Come interpretarlo

È un limite di sostenibilità **del modello**, non un prezzo che una banca è obbligata a finanziarti.

Per una casa già posseduta il solver è correttamente indicato come non applicabile: cambiare il “prezzo di acquisto” di una proprietà che già possiedi non è una decisione economica attuale.

## 47. LTV search

### Cosa cerca

Il livello di LTV che massimizza l'obiettivo terminale tra le alternative che rispettano il vincolo di liquidità.

### Metodo

Grid search deterministica su 21 livelli tra 0% e 100%.

### Vincoli

Scarta le configurazioni che falliscono o non mantengono la minimum runway.

### Come interpretarlo

Un LTV “ottimo” è tale solo rispetto alle ipotesi di rendimento, costi, tassi, liquidità e orizzonte del modello. Non misura il rischio psicologico o la tolleranza personale alla leva.

## 48. Required external monthly capacity

### Cosa cerca

Quanto **nuovo flusso netto esterno mensile** occorrerebbe per raggiungere il goal deterministico selezionato.

### Metodo

Ricerca deterministica per bisezione tra 0 e 10.000 €/mese.

### Attenzione

Non è “quanto devi investire” da risorse già presenti. Aumenta esplicitamente **Additional net cash flow**, quindi rappresenta capacità economica aggiuntiva: maggior reddito, minore spesa già rimossa altrove, o altra risorsa esterna coerentemente modellata.

## 49. Dopo Optimize

La procedura corretta è:

1. lascia invariata la baseline;
2. crea lo scenario proposto dal solver;
3. confronta la liquidità oltre al patrimonio finale;
4. esegui **Lab → Risk**;
5. verifica che il risultato rimanga ragionevole con ipotesi meno favorevoli.

---

# Parte VIII — Lab

## 50. Risk / Monte Carlo

### 50.1 Che cos'è

La simulazione Monte Carlo genera molti percorsi alternativi dei rendimenti e dei valori immobiliari intorno alle ipotesi configurate. Gli shock degli asset sono correlati secondo la matrice definita nel piano.

Il solo modo implementato in questa versione è **parametric Monte Carlo**.

### 50.2 Paths

Nella UI puoi scegliere da 500 a 20.000 path, a incrementi di 500.

Più path riducono il rumore statistico delle stime, ma richiedono più calcolo. Se il Web Worker non è disponibile, l'app passa a un fallback main-thread a blocchi e riduce i path effettivi fino a un massimo di 2.000 per evitare di bloccare il dispositivo.

Dopo qualunque modifica materiale a piano, scenario, tax pack, correlazioni o ipotesi, **riesegui Risk** prima di interpretare di nuovo Plan Status o i grafici stochastic: i risultati Monte Carlo mostrati sono il risultato dell'ultima simulazione eseguita, non un calcolo automatico continuo a ogni modifica.

### 50.3 Seed

Il **seed** rende riproducibile la sequenza pseudo-casuale. Stesso piano + stesso seed permettono di ripetere lo stesso esperimento.

Quando confronti scenari, l'app usa shock esogeni coerenti tra i rami, così la differenza non dipende semplicemente dall'avere “avuto fortuna” in una simulazione e sfortuna nell'altra.

### 50.4 Median terminal

È la mediana della distribuzione terminale. Il 50% dei path termina sopra e il 50% sotto, nel campione simulato.

Non è “il valore che il mercato prevede”.

### 50.5 P10 / P90 e percentili

P10 è il valore sotto il quale cade circa il 10% dei path; P90 è quello sotto il quale cade circa il 90%.

La distanza tra percentili dà un'idea dell'incertezza degli esiti.

### 50.6 Goal success

È la quota di path che soddisfa tutti i goal richiesti secondo la loro semantica e non incontra un fallimento di liquidità.

Viene mostrato anche un **95% confidence interval** di Wilson. Questo intervallo descrive l'incertezza statistica della probabilità stimata a causa del numero finito di simulazioni; non descrive tutta l'incertezza del mondo reale.

### 50.7 Liquidity failure

È la quota di path in cui un obbligo non può essere finanziato con le risorse accessibili previste dal modello.

È spesso un indicatore più decisionale della sola ricchezza terminale: un piano che “finisce ricco” in media ma ha un'alta probabilità di fallire a metà percorso è fragile.

### 50.8 P5 minimum liquidity

Descrive la coda bassa della liquidità minima raggiunta lungo i path. Aiuta a capire quanto può diventare stretta la situazione nei percorsi avversi.

### 50.9 Max drawdown

Misura la massima discesa del patrimonio rispetto al precedente picco del singolo path. La UI mostra mediana e P95 del max drawdown.

### 50.10 Outcome distribution

L'istogramma mostra la distribuzione del risultato terminale dello scenario attivo. Normalmente coincide con il Net Worth terminale; se l'impostazione avanzata `terminalLiquidation` è attiva, il motore usa invece l'obiettivo di liquidazione dopo i costi e le imposte modellate.

I path falliti non vengono semplicemente rimossi: il risultato terminale incondizionato li include al loro stato di fallimento e la UI riporta separatamente anche la **survivor-only median** quando ci sono fallimenti.

### 50.11 Fan chart

Mostra nel tempo bande P5–P95, con fasce interne e mediana. La banda più larga indica la dispersione crescente dei possibili percorsi. Nei path che terminano anticipatamente per failure, il fan chart riutilizza l'ultimo checkpoint annuale disponibile per i periodi successivi. Per questo non va mai letto isolatamente: interpreta sempre le bande insieme a **Liquidity failure** e alla distribuzione terminale.

> **Importante —** Monte Carlo non prevede il futuro. Campiona un modello. Se rendimento atteso, volatilità, correlazioni, inflazione o tassazione sono sbagliati, migliaia di path non rendono corrette quelle ipotesi.

## 51. Robustness

La sezione **Robustness** è specifica per il confronto controllato **Rent vs Buy**. Non è un'analisi generale di robustezza dell'intero piano familiare.

Genera 1.000 stati deterministici di ipotesi attorno al caso corrente variando parametri come:

- mortgage rate;
- monthly rent;
- portfolio return;
- home appreciation;
- rent growth;
- owner/maintenance costs.

### Indicatori

**Buy win rate** — quota degli stati di ipotesi in cui Buy supera Rent.

**Median Buy − Rent** — differenza mediana.

**P5 / P95 decision delta** — dispersione del vantaggio.

**Regret proxy** — indicatore descrittivo della distanza dalla scelta migliore nei campioni; è esplicitamente un proxy, non una formalizzazione universale del regret decisionale.

**Decision-critical assumptions** — correlazioni tra variazione delle ipotesi e differenza Buy − Rent. Barre più lunghe indicano le ipotesi che, in quella regione, muovono maggiormente il risultato.

La UI considera:

- Buy come robust winner se Buy win rate > 70%;
- Rent se < 30%;
- No dominant choice tra 30% e 70%.

Queste soglie sono euristiche dell'interfaccia, non leggi finanziarie.

## 52. Sensitivity

Anche **Sensitivity** è specifica per Rent vs Buy.

La heatmap 7×7 varia:

- mortgage rate attorno al valore corrente;
- monthly rent attorno al valore corrente.

Ogni cella rappresenta:

**Buy with mortgage Net Worth − Rent + invest Net Worth**.

Una cella positiva favorisce Buy nel modello focalizzato; una negativa favorisce Rent.

### Break-even

**Mortgage-rate break-even** cerca i tassi tra 0% e 12% ai quali il vantaggio cambia segno o tocca il punto di parità.

È particolarmente utile perché una decisione con vantaggio di 100.000 € e break-even lontano dall'ipotesi corrente è molto diversa da una decisione con vantaggio di 5.000 € e break-even a pochi decimi di punto.

> **Suggerimento —** Usa la sensitivity prima di aumentare i path Monte Carlo. Se un risultato deterministico cambia segno con una variazione minima di una singola ipotesi, hai già imparato qualcosa di importante sulla fragilità della decisione.

## 53. Attribution

**Attribution** spiega la differenza di patrimonio terminale tra uno scenario figlio e la baseline.

Mostra:

- Baseline;
- Active scenario;
- Total delta;
- Method;
- Residual;
- contributi dei gruppi di modifiche.

Il metodo è una decomposizione **Shapley-style**:

- esatta fino a 8 gruppi di patch;
- permutation-sampled oltre quella soglia.

I contributi positivi aumentano il risultato dello scenario attivo; quelli negativi lo riducono. **Residual** mostra l'eventuale differenza di riconciliazione tra contributi e delta totale.

Attribution è uno strumento di decomposizione del modello, non una dimostrazione di causalità nel mondo reale.

## 54. Ledger

### 54.1 Perché esiste

Il Ledger rende esplicita la logica contabile e permette di verificare che i movimenti non creino o distruggano patrimonio per errore.

La pagina mostra:

- Assets;
- Liabilities;
- Net worth;
- Journal entries;
- Ledger status;
- Consumed costs;
- Journal explorer;
- Export CSV.

### 54.2 Double-entry logic

Ogni registrazione deve bilanciare debiti e crediti contabili. Questo aiuta a distinguere cash flow, trasferimenti e variazioni di valore.

### 54.3 Esempi fondamentali

**Contributo a un investimento**  
Cassa diminuisce, investimento aumenta. Non è una spesa.

**Rimborso del capitale del mutuo**  
Cassa diminuisce, debito diminuisce. Non è una spesa consumata.

**Interessi del mutuo**  
Cassa diminuisce e si registra un costo. È una spesa.

**Acquisto casa**  
Nasce/aumenta un'attività immobiliare; il prezzo non è interamente una spesa. I costi di transazione, invece, sono costi consumati.

**Rivalutazione di un asset**  
Aumenta o riduce il valore patrimoniale senza essere un flusso di cassa.

**Deposito cauzionale**  
È un'attività finché non viene restituito o perso.

### 54.4 Journal explorer

Mostra le ultime 250 registrazioni. **Export CSV** esporta la traccia completa.

## 55. Data

**Lab → Data** è il centro delle impostazioni avanzate. Contiene:

- Assumptions & tax pack;
- Expert plan JSON;
- Household members;
- Financial policies;
- Other liabilities;
- Additional properties;
- Life events;
- Insurance & protection;
- Plan health.

### Plan health

Classifica i problemi come:

- **blocking** — impediscono l'esecuzione affidabile;
- **warning** — il piano può girare ma richiede attenzione;
- **informational** — nota utile.

Non ignorare un warning solo perché il risultato numerico appare plausibile.

## 56. Audit

**Lab → Audit** contiene due gruppi di informazioni.

### Embedded diagnostics

Esegue self-test rapidi sulle funzioni del motore e mostra quanti sono PASS/FAIL.

### Reproducibility & capabilities

Mostra:

- Build;
- Engine;
- Schema;
- App;
- Plan fingerprint;
- Storage mode;
- IndexedDB API;
- localStorage;
- Web Worker;
- Web Crypto;
- File API;
- Share files;
- Risk seed / paths;
- Network dependency.

Il **Plan fingerprint** è un identificatore deterministico compatto della configurazione risolta e della versione del motore. È utile per capire se due analisi si riferiscono davvero alla stessa configurazione; non è una firma digitale di autenticità.

---

# Parte IX — Actual vs Plan

## 57. Perché usare Actual vs plan

Un piano diventa utile nel tempo solo se confronti ciò che immaginavi con ciò che è realmente accaduto.

Percorso: **Plan → Detailed → Actual vs plan**.

## 58. Actual Snapshot

Con **Record snapshot** inserisci:

- As-of month;
- Cash;
- Investments;
- Property;
- Total debt;
- Note.

Il Net Worth osservato viene derivato come:

**cash + investments + property − debt**.

Il pannello confronta l'ultimo snapshot con il valore che il piano proiettava per lo stesso mese e mostra la **Variance**.

### Interpretare la variance

Una variance positiva non significa automaticamente “hai fatto meglio”. Potrebbe derivare da:

- maggiore reddito;
- spese inferiori;
- mercati migliori;
- rivalutazione immobiliare;
- debito inferiore;
- dati inseriti con criteri diversi.

Usala come segnale per investigare, non come voto.

## 59. Rebase Plan

**Rebase future plan from this snapshot** trasforma lo snapshot osservato nel nuovo punto iniziale della proiezione.

Aggiorna la composizione iniziale di:

- cash;
- investments;
- property;
- debt.

Sposta inoltre i riferimenti temporali futuri per mantenere, dove possibile, il significato calendale di goal, flussi ed eventi.

## 60. Aggiornare il futuro non significa riscrivere il passato

Prima del rebase, il motore conserva un **forecast archive** con il forecast precedente, includendo versione del motore/schema, periodo, scenario e checkpoint mensili principali.

Gli snapshot reali restano conservati.

Quindi:

- **Rebase** = “da oggi in poi parto dalla realtà osservata”;
- **non** = “faccio finta che il vecchio forecast avesse sempre previsto la realtà”.

Nella versione corrente gli archivi forecast sono conservati nel piano/esportazione e ispezionabili tramite Expert JSON; non esiste una schermata grafica dedicata che elenchi tutti gli archivi.

> **Pratica consigliata —** Registra snapshot a intervalli regolari, per esempio ogni 6 o 12 mesi, ma fai Rebase solo quando vuoi realmente sostituire il punto di partenza futuro.

---

# Parte X — Salvataggio, privacy e condivisione

## 61. Il sistema di persistenza

Financial Decision Studio prova in quest'ordine:

1. **IndexedDB**;
2. **localStorage**;
3. **memory/session-only**.

Se IndexedDB non risponde entro il timeout interno, l'app passa al fallback invece di rimanere bloccata.

Nell'header puoi vedere stati come:

- Saved · IndexedDB;
- Saved · localStorage;
- Unsaved;
- Session only;
- Storage pending.

## 62. Perché `file://` richiede prudenza

Quando apri un HTML locale direttamente dal file system, browser diversi possono trattare lo storage in modi diversi. Aggiornamenti del browser, modalità privata, pulizia dati, politiche di sicurezza o spostamento del file possono influire sulla persistenza.

Per questo lo storage del browser va considerato una comodità operativa, non l'unico backup.

> **Regola pratica —** Conserva periodicamente almeno una copia **Plan JSON** o **Portable HTML** fuori dallo storage del browser.

## 63. Checkpoint

Il pulsante **Checkpoint** tenta di salvare il piano nello storage locale disponibile.

Se l'app è in memory/session-only, il checkpoint non può trasformare magicamente la sessione in un salvataggio durevole: la UI ti invita a esportare.

## 64. Plan JSON

**Export** nell'header esporta direttamente il piano in JSON.

Dal menu **⋯ → Data, storage & sharing** puoi anche:

- Import plan JSON;
- Export plan JSON.

Il JSON è utile come backup strutturato, ma contiene i dati del piano in chiaro. Trattalo come un documento finanziario personale.

L'importazione passa attraverso migrazione e validazione prima di sostituire il piano attivo. I dati importati sono trattati come configurazione dichiarativa: schema futuro non supportato, percorsi di patch pericolosi o combinazioni bloccanti vengono rifiutati invece di essere eseguiti come codice.

## 65. Portable HTML

**Create portable HTML** genera una nuova copia dell'intera applicazione con il piano incorporato.

Vantaggi:

- è un unico file;
- si apre senza import manuale;
- include app + piano + scenario attivo;
- è utile per archiviare uno “snapshot operativo” condivisibile.

La Portable HTML normale **non è cifrata**. Il payload incorporato non deve essere considerato segreto solo perché è codificato.

## 66. Encrypted Portable HTML

Se **Web Crypto** è disponibile, puoi creare **Encrypted portable HTML**.

La protezione implementata usa:

- PBKDF2-HMAC-SHA-256;
- 310.000 iterazioni;
- salt casuale di 16 byte;
- AES-GCM a 256 bit;
- IV casuale di 12 byte.

### Cosa succede quando la apri

1. il file chiede la password;
2. deriva la chiave dalla password;
3. autentica e decripta il piano;
4. se la password è corretta, apre il piano in **session-only / privacy mode**;
5. per salvarlo localmente devi disabilitare deliberatamente la privacy mode.

### Se la password è sbagliata

La decrittazione fallisce e il piano non viene aperto.

### Se perdi la password

L'app non contiene un sistema di recupero o escrow della password. **Se perdi la password e non hai un'altra copia, il contenuto cifrato può diventare irrecuperabile.**

> **Suggerimento —** Usa una passphrase lunga e unica e conservala in un password manager affidabile. Mantieni anche una strategia di backup coerente con il livello di sensibilità dei dati.

## 67. Share e Web Share

Il pulsante **Share** apre:

- Share portable HTML;
- Share plan JSON;
- Encrypted portable HTML;
- Download portable HTML.

Se il browser supporta la condivisione di file tramite Web Share, viene usato il meccanismo di condivisione del sistema operativo/browser. Altrimenti l'app effettua un download del file come fallback.

## 68. Privacy mode

Nel menu **Data, storage & sharing** puoi scegliere **Do not persist locally**.

In privacy mode:

- lo storage locale del piano viene cancellato;
- le modifiche restano in memoria;
- devi esportare per conservarle.

È utile su dispositivi condivisi o quando non vuoi che il browser mantenga una copia locale.

## 69. Recovery mode

Se un errore grave di runtime viene intercettato, l'app prova a mostrare una schermata di recovery invece di lasciare una pagina bianca.

Può offrire:

- Export recoverable plan;
- Open safe example;
- Clear local storage & reload.

Se un piano salvato o incorporato non supera migrazione/validazione, l'app può aprire un piano sicuro in session-only e mostrare un messaggio di recovery.

---

# Parte XI — Come prendere decisioni con Financial Decision Studio

## 70. Metodo pratico in 10 passaggi

### 1. Costruisci una baseline realistica

Usa dati che puoi difendere. Non partire da rendimento, inflazione o crescita immobiliare scelti per ottenere il risultato che desideri.

### 2. Controlla la liquidità

Prima di guardare il patrimonio terminale, controlla:

- Liquid Net Worth;
- Liquidity Runway;
- eventuali failure;
- riserva minima.

### 3. Definisci gli obiettivi

Distingui ciò che è realmente vincolante da ciò che è un target o un desiderio.

### 4. Crea alternative

Usa Branch o un template. Cambia solo ciò che rappresenta davvero la decisione.

### 5. Confronta il deterministico

Il deterministico è il modo più semplice per capire il meccanismo economico. Se non sai spiegare perché uno scenario vince nel caso centrale, Monte Carlo non risolverà il problema concettuale.

### 6. Osserva i break-even

Chiediti: quale tasso, prezzo, affitto o rendimento farebbe cambiare la scelta?

### 7. Esegui Monte Carlo

Guarda probabilità di goal success, liquidity failure e dispersione, non solo la mediana.

### 8. Verifica la robustezza

Per Rent vs Buy, controlla se il vincitore resta tale quando le ipotesi cambiano contemporaneamente.

### 9. Identifica le ipotesi decisive

Sensitivity e Attribution aiutano a distinguere le variabili che contano davvero da quelle che muovono poco il risultato.

### 10. Scegli considerando vincoli e preferenze personali

L'opzione con il patrimonio terminale maggiore **non è automaticamente la scelta migliore**.

Una decisione può avere Net Worth più alto ma:

- meno liquidità;
- più leva;
- maggiore rischio di failure;
- maggiore volatilità;
- minore flessibilità;
- più complessità operativa;
- caratteristiche personali che non vuoi accettare.

Il modello misura conseguenze finanziarie secondo ipotesi. La funzione di utilità finale appartiene a te.

---

# Parte XII — Esempi pratici

## 71. Caso 1 — Affitto vs acquisto casa

**Situazione:** 40.000 € di cassa, 30.000 € investiti, reddito netto 3.500 €/mese, spese essenziali 1.700 €/mese. Stai valutando una casa da 250.000 € contro 900 €/mese di affitto.

### Procedura

1. costruisci la baseline con reddito, spese e patrimonio reali;
2. imposta una riserva, per esempio 6 mesi;
3. apri **Decisions → Rent vs Buy**;
4. inserisci casa, affitto, tasso, LTV, apprezzamento e rendimento;
5. guarda il delta, ma non decidere ancora;
6. apri **Sensitivity** e osserva il break-even del tasso;
7. crea i due scenari canonici;
8. confronta Liquid Net Worth e Min runway;
9. esegui Risk sui due rami;
10. se Buy vince solo con apprezzamento elevato e liquidità molto bassa, considera la scelta fragile anche se il Net Worth centrale è maggiore.

## 72. Caso 2 — Anticipare il mutuo vs investire

**Situazione:** mutuo esistente, tasso 3%, vuoi destinare 500 €/mese in più.

### Procedura

1. in **Housing & debt**, imposta Extra principal / month = 500;
2. apri **Decisions → Prepay vs Invest**;
3. confronta Scheduled mortgage only, Extra principal e Invest same cash allocation;
4. verifica che la riserva rimanga intatta;
5. osserva la differenza di Net Worth, ma considera anche il debito residuo e la volatilità degli investimenti;
6. se il vantaggio dell'investimento è piccolo e dipende da un rendimento atteso aggressivo, la certezza del risparmio di interessi può avere un valore decisionale che il solo patrimonio medio non rappresenta.

## 73. Caso 3 — Verificare se una casa è realmente sostenibile

**Situazione:** vuoi sapere non “quanto mi presta la banca”, ma “quanto posso comprare senza svuotare il cuscinetto”.

### Procedura

1. inserisci cassa, redditi, spese e investimenti realistici;
2. imposta **Minimum cash reserve**;
3. configura costi di acquisto, manutenzione, assicurazione, property-tax assumption e tasso;
4. apri **Optimize → Affordable home price**;
5. considera il risultato come massimo del modello, non come prezzo consigliato;
6. crea lo scenario;
7. esegui Monte Carlo;
8. se Liquidity failure è significativa, riduci il prezzo o aumenta il margine di sicurezza anche se il deterministico risulta fattibile.

## 74. Caso 4 — Probabilità di raggiungere un obiettivo patrimoniale

**Situazione:** vuoi 600.000 € di Net Worth fra 20 anni.

### Procedura

1. crea un goal Target da 600.000 € al mese 240;
2. scegli **Nominal at target** se intendi 600.000 € nominali futuri, oppure **Current purchasing power** se intendi potere d'acquisto equivalente a 600.000 € di oggi;
3. controlla il risultato deterministico;
4. apri **Lab → Risk**;
5. esegui almeno 2.000 path come prima analisi;
6. guarda Goal success e relativo 95% CI;
7. controlla Liquidity failure;
8. se il target ha successo solo nel 55% dei path, non interpretare il deterministico “On track” come sufficiente;
9. crea uno scenario con maggior capacità esterna o target/data diversi e ripeti.

## 75. Caso 5 — Aggiornare il piano dopo un anno

**Situazione:** un anno fa avevi pianificato 25.000 € cash, 50.000 € investimenti e 180.000 € debito. Oggi i valori reali sono diversi.

### Procedura

1. passa a **Plan → Detailed**;
2. in **Actual vs plan**, premi **Record snapshot**;
3. inserisci cassa, investimenti, proprietà e debito reali;
4. leggi la variance rispetto a ciò che il piano prevedeva per quel mese;
5. annota la causa principale della differenza;
6. se vuoi mantenere il piano originale come confronto storico, non serve rebase immediato;
7. se vuoi che tutte le proiezioni future partano dalla realtà attuale, usa **Rebase future plan from this snapshot**;
8. il vecchio forecast viene archiviato invece di essere riscritto;
9. esegui nuovamente Risk, perché una nuova base patrimoniale può cambiare la probabilità di successo.

---

# Parte XIII — Errori comuni

## 76. Usare rendimenti troppo ottimistici

Un 9–10% annuo costante può trasformare quasi ogni piano di lungo periodo in un successo deterministico. Il problema non è che un rendimento elevato sia impossibile; è che stai trattando una media incerta come una certezza del piano centrale.

## 77. Confondere Net Worth e Liquid Net Worth

Una casa da 400.000 € con molto debito può produrre un patrimonio positivo e contemporaneamente una liquidità fragile.

## 78. Ignorare la liquidity runway

Le decisioni falliscono spesso per timing, non perché il valore finale teorico sia basso. Controlla la capacità di attraversare gli anni intermedi.

## 79. Trattare Monte Carlo come previsione

2.000 o 20.000 path non compensano ipotesi errate. Monte Carlo misura le conseguenze probabilistiche del modello che gli hai dato.

## 80. Confrontare scenari con risorse iniziali diverse

È uno degli errori più gravi. Mantieni baseline, patrimonio iniziale e flussi esterni comuni, salvo che la differenza sia proprio ciò che vuoi studiare.

## 81. Dimenticare i costi immobiliari

Prezzo della casa e rata non bastano. Inserisci acquisto, manutenzione, assicurazione, property tax assumption, costi di vendita e tassazione di dismissione se rilevante.

## 82. Trattare il tax pack come dichiarazione fiscale

Il pack Italy 2026 è una planning approximation. Per decisioni sensibili alle tasse, verifica separatamente il caso fiscale reale.

## 83. Ignorare l'inflazione

Un target nominale di 500.000 € tra 30 anni non ha lo stesso significato economico di 500.000 € oggi. Usa **Current purchasing power** quando il tuo obiettivo è espresso in potere d'acquisto corrente.

## 84. Guardare solo il risultato terminale

Controlla anche:

- min liquidity;
- failure;
- drawdown;
- debito;
- distribuzione Monte Carlo;
- goal success.

## 85. Modificare troppe variabili contemporaneamente

Se una branch cambia casa, reddito, spese, rendimento e pensionamento insieme, Attribution può aiutare, ma la decisione diventa più difficile da capire. Preferisci scenari interpretabili.

## 86. Usare Additional net cash flow per “far tornare” il piano

È una risorsa esterna. Se la aggiungi senza una fonte economica reale, stai migliorando artificialmente il piano.

## 87. Ignorare warning e blocking issues

Un risultato numerico non rende valide ipotesi incoerenti. Controlla **Plan health** prima di affidarti alla simulazione.

---

# Parte XIV — Limiti reali del modello

## 88. Tax engine

Il motore fiscale è una pianificazione semplificata. Italy 2026 non implementa l'intero sistema tributario italiano e non è software per dichiarazioni fiscali.

## 89. Account types

La simulazione supporta semanticamente account di tipo:

- cash;
- taxable investment.

Non implementa ancora come categorie distinte complete conti pensionistici/tax-sheltered con regole fiscali e di prelievo specifiche.

## 90. Multi-currency

La versione è **base-currency only**. Conti o asset con valuta diversa dalla valuta base vengono bloccati invece di essere convertiti con un FX implicito.

## 91. Tax lots

Il modello conserva identità e cost basis per posizione, ma non è un motore fiscale completo di singoli lotti con FIFO/LIFO/ottimizzazione fiscale di ogni acquisto storico.

## 92. Monte Carlo

È disponibile la modalità **parametric**. Non sono implementate come modalità utente:

- historical sequence simulation;
- block bootstrap;
- regime switching.

## 93. Optimization

I solver sono deterministici, bounded e trasparenti. Non esiste un ottimizzatore stocastico multi-obiettivo o Pareto formalmente implementato nella UI.

## 94. Pensione

Il template Retirement modifica flussi di reddito e spesa. Non è un motore attuariale completo di longevità, superstiti, previdenza pubblica dettagliata, long-term care o regole fiscali dei conti pensionistici.

## 95. Insurance

Il modello rappresenta premi e benefici a date configurate. Non stima frequenza/severità dei sinistri o adeguatezza della copertura.

## 96. Immobili

Gli immobili usano ipotesi di apprezzamento, costi, vacancy, canoni e tassazione configurata. Non sono un modello completo del mercato immobiliare locale né del diritto tributario immobiliare.

## 97. Rent vs Buy Robustness e Sensitivity

Queste due analisi sono specifiche del modello controllato Rent vs Buy. Non equivalgono a una sensitivity globale di ogni variabile del piano familiare.

## 98. Attribution

Spiega la differenza prodotta dalle patch di scenario nel modello. Non dimostra causalità economica nel mondo reale.

## 99. Dati di mercato e normativa

Il file funziona offline e non aggiorna automaticamente rendimenti, tassi, inflazione, prezzi immobiliari o leggi fiscali dal web. Le ipotesi devono essere mantenute consapevolmente dall'utente.

## 100. Browser e storage

Persistenza, Web Share, Web Crypto, Web Worker e File API dipendono dal browser. Il prodotto degrada quando possibile, ma alcune funzioni possono essere indisponibili in determinati contesti locali.

## 101. Precisione vs realtà

Una simulazione mensile coerente può essere numericamente precisa rispetto alle proprie regole senza essere “esatta” rispetto alla vita futura. La qualità della decisione dipende dalla qualità delle ipotesi, dalla completezza del modello e dall'uso di margini di sicurezza.

---

# Glossario

| Termine UI | Significato |
|---|---|
| **Baseline** | Piano/scenario di riferimento da cui derivano i rami. |
| **Branch** | Scenario figlio che eredita il parent e memorizza differenze. |
| **Net Worth** | Attività meno passività. |
| **Accessible Wealth** | Cassa + investimenti liquidi stimati dopo tassazione latente applicabile. |
| **Liquid Net Worth** | Accessible Wealth meno debiti. |
| **Liquidity Runway** | Mesi stimati di copertura degli outflow essenziali con ricchezza accessibile. |
| **Cost basis** | Costo fiscale attribuito a una posizione d'investimento. |
| **Target weight** | Peso desiderato di un asset nel portafoglio. |
| **Rebalancing** | Riallineamento del portafoglio ai pesi target. |
| **Goal** | Obiettivo misurabile a una data futura. |
| **Hard** | Goal con minimum vincolante. |
| **Target** | Goal il cui successo pieno richiede il target. |
| **Aspirational** | Goal informativo che non determina il fallimento complessivo. |
| **Minimum** | Soglia minima accettabile del goal. |
| **Current purchasing power** | Target espresso in potere d'acquisto di oggi e rivalutato con inflazione. |
| **Path** | Un singolo percorso simulato in Monte Carlo. |
| **Seed** | Valore che rende riproducibile la pseudo-casualità della simulazione. |
| **Percentile** | Posizione di un risultato nella distribuzione dei path. |
| **Wilson CI** | Intervallo statistico usato per probabilità binarie come goal success. |
| **Drawdown** | Discesa da un precedente massimo. |
| **Sensitivity** | Analisi di come il risultato cambia al variare di ipotesi. |
| **Break-even** | Valore dell'ipotesi in cui due alternative diventano equivalenti. |
| **Robustness** | Verifica se la decisione resiste a errori plausibili nelle ipotesi. |
| **Attribution** | Decomposizione del delta di scenario nei contributi delle modifiche. |
| **Ledger** | Registro contabile dei movimenti del modello. |
| **Rebase** | Aggiornamento del punto iniziale futuro usando uno snapshot reale. |
| **Forecast archive** | Copia storica del forecast precedente a un rebase. |
| **Tax pack** | Insieme di ipotesi fiscali semplificate usate dalla pianificazione. |
| **Portable HTML** | Copia dell'app con il piano incorporato in un singolo HTML. |
| **Encrypted Portable HTML** | Portable HTML con piano cifrato e protetto da password. |
| **Session only** | Il piano è solo in memoria; serve esportarlo per conservarlo. |
| **Plan fingerprint** | Identificatore deterministico compatto della configurazione e del motore. |

---

# FAQ

## Devo essere online?

No per il funzionamento ordinario dell'app. Il prodotto è progettato per lavorare offline e non ha una dipendenza di rete per il motore.

## Se chiudo il browser perdo tutto?

Dipende dallo storage disponibile. Se vedi **Saved · IndexedDB** o **Saved · localStorage**, il browser ha accettato il salvataggio locale; se vedi **Session only**, devi esportare. In ogni caso è consigliato mantenere backup esterni.

## Qual è il backup migliore?

**Plan JSON** è semplice e strutturato. **Portable HTML** è più comodo perché include app e piano. Per dati sensibili condivisi o archiviati, **Encrypted Portable HTML** aggiunge cifratura, purché tu conservi la password.

## Posso usare Italy 2026 per compilare la dichiarazione?

No. È un planning pack semplificato.

## Perché il mio Net Worth è alto ma Liquid Net Worth basso?

Probabilmente una parte importante del patrimonio è illiquida, gli investimenti hanno tassazione latente, oppure i debiti sono elevati.

## Perché un contributo a investimenti non appare come spesa?

Perché sposta valore dalla cassa a un asset. Non è consumo di patrimonio.

## Perché il capitale del mutuo non è spesa?

Perché riduce la passività. Gli interessi sono il costo consumato; il capitale è rimborso del debito.

## Il Monte Carlo mi dice la probabilità reale che il mercato farà X?

No. Stima probabilità interne al modello usando rendimento, volatilità, correlazioni e altre ipotesi configurate.

## Quanti path devo usare?

Per esplorare, 500–2.000 sono spesso sufficienti per vedere la struttura del risultato. Aumenta i path quando vuoi ridurre il rumore statistico, ricordando che più simulazioni non correggono ipotesi sbagliate.

## Perché Optimize non mi dà un “portafoglio ottimo”?

Questa versione implementa solver specifici per affordable home price, LTV e capacità mensile esterna richiesta. Non presenta un ottimizzatore generale di portafoglio o Pareto che non sia realmente implementato.

## Posso modellare un conto pensione con tassazione diversa?

Non come account type pienamente distinto nella simulazione corrente. Gli account supportati sono cash e taxable investment.

## Posso usare più valute?

No. La versione corrente è base-currency only.

## Posso modellare più immobili?

Sì, tramite **Lab → Data → Additional properties**, entro le semplificazioni del modello immobiliare.

## Posso modellare un evento con più azioni?

L'editor strutturato offre una sola azione principale. **Expert plan JSON** può rappresentare più azioni nello stesso evento.

## Perché il mio scenario cambia quando modifico la baseline?

Perché **Branch** usa ereditarietà live: il ramo conserva le proprie differenze e continua a ereditare il resto dal parent.

## Cosa succede se un pagamento obbligatorio non è finanziabile?

Il motore prova la cascata di funding prevista, inclusa la vendita di investimenti liquidi tassabili quando appropriato. Se le risorse accessibili non bastano, il percorso viene marcato come failure invece di creare un prestito implicito o cassa negativa artificiale.

## Un goal Aspirational abbassa Goal success?

No: non è un goal richiesto per il successo complessivo.

## Posso vedere i forecast archive dopo un Rebase?

Sono conservati nel piano e nelle esportazioni e possono essere ispezionati via Expert JSON. Non c'è, nella versione corrente, un browser grafico dedicato degli archivi.

## La password di un Encrypted Portable HTML può essere recuperata?

No. Se la dimentichi e non hai una copia alternativa, non c'è un meccanismo di recupero integrato.

---

# Checklist — Prima di prendere una decisione importante

- [ ] La baseline usa dati correnti e non valori desiderati.
- [ ] Ho controllato **Plan health** e non ci sono blocking issues.
- [ ] Ho distinto Net Worth, Accessible Wealth e Liquid Net Worth.
- [ ] La Liquidity Runway è compatibile con il mio margine di sicurezza.
- [ ] I costi immobiliari o di transazione sono inclusi.
- [ ] Le ipotesi fiscali sono appropriate come planning assumption e non vengono trattate come calcolo ufficiale.
- [ ] Gli scenari confrontati hanno le stesse risorse iniziali salvo differenze deliberate.
- [ ] Ho definito almeno un goal con priorità coerente.
- [ ] Ho controllato il risultato deterministico prima di Monte Carlo.
- [ ] Ho identificato almeno un break-even o un'ipotesi decisiva.
- [ ] Ho eseguito Risk con seed e numero di path annotati.
- [ ] Ho guardato Goal success e Liquidity failure, non solo Median terminal.
- [ ] Ho verificato la robustezza quando disponibile.
- [ ] Ho considerato leva, flessibilità e preferenze personali oltre al patrimonio terminale.
- [ ] Ho creato un backup del piano prima di una modifica importante.

---

# Checklist — Backup e sicurezza dei dati

- [ ] Ho verificato nell'header se lo storage è IndexedDB, localStorage o Session only.
- [ ] Non considero lo storage `file://` come unico backup.
- [ ] Esporto periodicamente un **Plan JSON** o un **Portable HTML**.
- [ ] Conservo almeno una copia in una posizione diversa dal dispositivo principale.
- [ ] Se il file contiene dati sensibili, valuto **Encrypted Portable HTML**.
- [ ] Uso una password/passphrase lunga e unica per la copia cifrata.
- [ ] Conservo la password in modo indipendente dal file cifrato.
- [ ] So che la password dell'Encrypted Portable HTML non è recuperabile dall'app.
- [ ] Prima di condividere un Plan JSON o Portable HTML non cifrato, ricordo che i dati sono leggibili da chi riceve il file.
- [ ] Se uso **Privacy mode**, esporto prima di chiudere la sessione.
- [ ] Dopo un Rebase o una modifica strutturale importante, creo un nuovo backup.

---

# Conclusione

Financial Decision Studio è più utile quando viene trattato come un **laboratorio decisionale disciplinato**, non come un oracolo.

La sequenza fondamentale è semplice:

**rappresenta correttamente la situazione → proteggi la liquidità → definisci gli obiettivi → crea alternative eque → identifica i break-even → misura l'incertezza → verifica la robustezza → aggiorna il piano con la realtà.**

Se un risultato è difficile da spiegare, non aumentare subito la complessità: torna alla baseline, riduci le variabili e ricostruisci il meccanismo economico. Una decisione comprensibile e robusta è più utile di un numero molto preciso ottenuto da ipotesi fragili.
