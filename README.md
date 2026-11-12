Il progetto è stato sviluppato esclusivamente da me.

Il progetto è stato pensato per crearti un widget che ti faccia vedere i paesi che vuoi visitare e se li hai visti o no.
Il widget lo sviluppato creando una secondo target, i target principali (EsameIOS-SAA per l'app principale e EsameIOS-SAAWidgetExtension per i widget)

All'interno dell'app si trova la schermata principale che ti permette di aggiungere nuovi paesi da visitare e nel back-end grazie al nome del paese Geocoding con MapKit: Converte il nome testuale del paese inserito dall'utente in coordinate geografiche (CLLocationCoordinate2D) tramite MKLocalSearch.

Tutti questi dati dei paesi e le loro posizioni sono stati salvati grazia SwiftData: Utilizzato per salvare in locale i paesi aggiunti dall'utente (CountryItem), memorizzando il nome del paese, lo stato di visita (isVisited), eventuali note personali e le coordinate geografiche.

La navigazione tra le schermate viene gestito dal TabBar dove sono presenti Home e Map con i corrispettivi loghi e si articola nelle seguenti viste:
-ContentView: Gestisce la struttura di navigazione principale dell'app.   
-MapView: Integra MapKit per visualizzare su una mappa interattiva i segnaposto dei paesi salvati dall'utente.   
-TodoView: Mostra la lista dei paesi organizzati come checklist di viaggio, permettendo di segnare quelli già visitati.   
-AddCountryView: Schermata dedicata all'inserimento di un nuovo paese, che avvia la ricerca automatica delle coordinate geografiche.   
-CountryDetailView: Vista di dettaglio di un singolo paese che permette di modificare lo stato "Visitato", leggere le note e consultare in tempo reale capitale, continente, popolazione e bandiera.  

La schermata Map contiene una Map con all'interno vari PlaceMark che stanno ad indicare i paesi da visitare poi il colore e il disegno stanno ad indicare se il paese è stato già visitato oppure no.

Infine i PlaceMark se clickati aprono una sheet meta schermo che visualizza dati di base del paese grazia ad una chiamata API e da la possibilità di cambiare lo stato del paese da non visitato a visitato.
Questi ultimi dettagli vengono recuperati dinamicamente tramite una chiamata HTTP asincrona alle REST Countries API (v5). Poiché la richiesta di rete viene eseguita in background per non bloccare l'app, ho utilizzato @MainActor per riportare l'esecuzione sul Main Thread al termine della chiamata, garantendo così un aggiornamento sicuro e immediato dell'interfaccia utente in SwiftUI.
