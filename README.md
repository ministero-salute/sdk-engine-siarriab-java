# sdk-engine-siarriab-java

## Sistema Informativo Assistenza Riabilitativa Attività Riabilitazione

### Descrizione repository:

Il microservizio ha come scopo  l'acquisizione dei dati inviati dalle Regioni in merito ai trattamenti riabilitativi erogati, nell'ambito dell'assistenza semiresidenziale e residenziale, a carattere intensivo, estensivo e di mantenimento di cui all'articolo 34 del decreto del Presidente del Consiglio dei ministri del 12 gennaio 2017.

I dati richiesti sono relativi al set di informazioni legate ai trattamenti riabilitativi di cui all'art. 1, previa valutazione multidimensionale dell'assistito, presa in carico e progetto riabilitativo individuale (PRI) ovvero piano individuale di assistenza e riabilitazione. Il tracciato 2 (SIAR_RIAB) comprende le informazioni relative alle prestazioni erogate individualmente ad un assistito.

Il Sistema SIAR viene alimentato con le informazioni relative ai trattamenti riabilitativi erogati a partire dal quarto trimestre 2023

L'invio dei file viene effettuato mediante un tracciato XML.
Per ogni tracciato XML, è fornito il relativo schema XSD di convalida a cui far riferimento

#### Struttura XML:


Campi del nodo di riferimento Trasmissione
-Tipo

Eventi:
- Presa in carico
- Rivalutazione
- Erogazione
- Sospensione 
- Conclusione

Nodi di riferimento Presa in carico:
- Erogatore
- Presa In Carico


Campi Erogatore:
- Regione di erogazione (campo chiave)
- Azienda sanitaria di erogazione (campo chiave)
- Struttura erogatrice (campo chiave)

Campi Presa In Carico: 
- Data apertura PIC (campo chiave)
- ID record (campo chiave)

Nodi di riferimento Rivalutazione:
- Valutazione
- Disturbi

Campi Valutazione:
- Autonomia
- Grado Mobilita
- Comunicazione
- Area sensoriale
- Bisogni internistico- assistenziali
- Stabilità clinica
- Presenza di un caregiver
- Supporto sociale
- Utilizzo di dispositivi/protesi/ortes

Campi Disturbi
- Disturbi cognitivi
- Disturbi comportamentali

Nodi di riferimento Erogazione:
- Trattamento 

Campi Trattamento:
- Data inizio trattamento (campo chiave)
- Data fine trattamento (campo chiave)
- Durata complessiva del trattamento
- Durata media giornaliera del trattament

Nodi di riferimento Sospensione:
- Sospensione

Campi Sospensione:
- Data di inizio sospensione (campo chiave)
- Data di fine sospensione
- Motivazione della sospensione
 
 Nodi di riferimento Conclusione:
- Conclusione

Campi Conclusione:
- Data riunione finale di equipe
- Data di conclusione 
- Modalità di conclusione (campo chiave)
- Esito rilevazione della disabilità in uscita  1
- Esito rilevazione della disabilità in uscita  2
- Esito rilevazione della disabilità in uscita  3
- Esito rilevazione della disabilità in uscita  4
- Esito rilevazione della disabilità in uscita  5
- Esito rilevazione della disabilità in uscita  6

XSD:
```
<xs:schema attributeFormDefault="unqualified" elementFormDefault="qualified" targetNamespace="http://flussi.mds.it/FlsSiar_2" xmlns:fls="http://flussi.mds.it/FlsSiar_2" xmlns:xs="http://www.w3.org/2001/XMLSchema">
	<xs:simpleType name="tipoTrasmissione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[IVC]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="regioneErogazione">
		<xs:restriction base="xs:string">
			<xs:pattern value="010"/>
			<xs:pattern value="020"/>
			<xs:pattern value="030"/>
			<xs:pattern value="041"/>
			<xs:pattern value="042"/>
			<xs:pattern value="050"/>
			<xs:pattern value="060"/>
			<xs:pattern value="070"/>
			<xs:pattern value="080"/>
			<xs:pattern value="090"/>
			<xs:pattern value="100"/>
			<xs:pattern value="110"/>
			<xs:pattern value="120"/>
			<xs:pattern value="130"/>
			<xs:pattern value="140"/>
			<xs:pattern value="150"/>
			<xs:pattern value="160"/>
			<xs:pattern value="170"/>
			<xs:pattern value="180"/>
			<xs:pattern value="190"/>
			<xs:pattern value="200"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="codASL">
		<xs:restriction base="xs:string">
			<xs:length value="3"/>
			<xs:pattern value="[0-9]{3}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="strutturaErogatrice">
		<xs:restriction base="xs:string">
			<xs:maxLength value="6"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="Id_Rec">
		<xs:restriction base="xs:string">
			<xs:length value="88"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="motivoRivalutazione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="confermaPrecedente">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="patologia">
		<xs:restriction base="xs:string">
			<xs:pattern value="[0-9]{5}|99999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="autonomia">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="gradoMobilita">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-5]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="areaSensoriale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="bisognoAssistenziale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-8]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="stabilitaClinica">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-6]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="esito">
		<xs:restriction base="xs:string">
			<xs:maxLength value="5"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="disturbo">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="bisogno">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="supportoSociale">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="durataComplessiva">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}|[10-99]{2}|[100-999]{3}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="durataMedia">
		<xs:restriction base="xs:decimal">
			<xs:minInclusive value="0.5"/>
			<xs:maxInclusive value="24"/>
			<xs:fractionDigits value="1"/>
			<xs:pattern value="\d+(\.5)?"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="eventualiTrattamenti">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-2]{1}"/>
			<xs:pattern value="9"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="motivazioneSospensione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-3]{1}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="modalitaConclusione">
		<xs:restriction base="xs:string">
			<xs:pattern value="[1-9]{1}"/>
			<xs:pattern value="10"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:simpleType name="DataRiunioneFinale">
		<xs:restriction base="xs:string">
			<xs:pattern value="(19|20)\d\d-(0[1-9]|1[012])-(0[1-9]|[12][0-9]|3[01])"/>
			<xs:pattern value="9999999999"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:element name="Trasmissione">
		<xs:complexType>
			<xs:attribute name="tipo" type="fls:tipoTrasmissione" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Erogatore">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="CodiceRegione" type="fls:regioneErogazione"/>
				<xs:element name="CodiceASL" type="fls:codASL"/>
				<xs:element name="StrutturaErogatrice" type="fls:strutturaErogatrice"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="PresaInCarico">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Id_Rec" type="fls:Id_Rec"/>
			</xs:sequence>
			<xs:attribute name="data" type="xs:date" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Rivalutazione">
		<xs:complexType>
			<xs:sequence>
				<xs:element minOccurs="0" ref="fls:Valutazione"/>
			</xs:sequence>
			<xs:attribute name="Data" type="xs:date" use="required"/>
			<xs:attribute name="MotivoValutazione" type="fls:motivoRivalutazione" use="required"/>
			<xs:attribute name="ConfermaPrecedente" type="fls:confermaPrecedente" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Patologia">
		<xs:complexType>
			<xs:sequence>
				<xs:element minOccurs="0" name="Prevalente" type="fls:patologia"/>
				<xs:element minOccurs="0" name="Concomitante" type="fls:patologia"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Disturbi">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Cognitivi" type="fls:disturbo"/>
				<xs:element name="Comportamentali" type="fls:disturbo"/>
				<xs:element name="Comunicazione" type="fls:disturbo"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Valutazione">
		<xs:complexType>
			<xs:sequence>
				<xs:element minOccurs="0" ref="fls:Patologia"/>
				<xs:element name="EventualiTrattamenti" type="fls:eventualiTrattamenti"/>
				<xs:element name="Autonomia" type="fls:autonomia"/>
				<xs:element name="GradoMobilita" type="fls:gradoMobilita"/>
				<xs:element name="AreaSensoriale" type="fls:areaSensoriale"/>
				<xs:element name="BisognoInternistico" type="fls:bisognoAssistenziale"/>
				<xs:element name="StabilitaClinica" type="fls:stabilitaClinica"/>
				<xs:element minOccurs="0" name="SupportoCareGiver" type="fls:bisogno"/>
				<xs:element name="SupportoSociale" type="fls:supportoSociale"/>
				<xs:element minOccurs="0" name="UtilizzoDispositivi" type="fls:bisogno"/>
				<xs:element ref="fls:Disturbi"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Trattamento">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="DurataCompTrat" type="fls:durataComplessiva"/>
				<xs:element name="DurataMedTrat" type="fls:durataMedia"/>
			</xs:sequence>
			<xs:attribute name="DataInizioTrat" type="xs:date" use="required"/>
			<xs:attribute name="DataFineTrat" type="xs:date" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Sospensione">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Motivazione" type="fls:motivazioneSospensione"/>
			</xs:sequence>
			<xs:attribute name="DataInizio" type="xs:date" use="required"/>
			<xs:attribute name="DataFine" type="xs:date" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Conclusione">
		<xs:complexType>
			<xs:sequence>
				<xs:element name="Motivazione" type="fls:modalitaConclusione"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis1" type="fls:esito"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis2" type="fls:esito"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis3" type="fls:esito"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis4" type="fls:esito"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis5" type="fls:esito"/>
				<xs:element minOccurs="0" name="EsitoRilevazioneDis6" type="fls:esito"/>
			</xs:sequence>
			<xs:attribute name="DataRiunioneFinale" type="fls:DataRiunioneFinale" use="required"/>
			<xs:attribute name="DataConclusione" type="xs:date" use="required"/>
		</xs:complexType>
	</xs:element>
	<xs:element name="Flusso2">
		<xs:complexType>
			<xs:sequence>
				<xs:element maxOccurs="unbounded" ref="fls:Assistenza"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Assistenza">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:Trasmissione"/>
				<xs:element ref="fls:Erogatore"/>
				<xs:element ref="fls:Eventi"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
	<xs:element name="Eventi">
		<xs:complexType>
			<xs:sequence>
				<xs:element ref="fls:PresaInCarico"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="fls:Rivalutazione"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="fls:Trattamento"/>
				<xs:element maxOccurs="unbounded" minOccurs="0" ref="fls:Sospensione"/>
				<xs:element minOccurs="0" ref="fls:Conclusione"/>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
</xs:schema>
```


### Struttura repository

La cartella principale è src/main/java che è organizzata nelle seguenti cartelle:

- it.mds.sdk.engine.config che raccoglie i file di configurazione
- it.mds.sdk.flusso.siar.riab che contiene il file necessario all'avvio dell'applicazione
- it.mds.sdk.flusso.siar.riab.controller che contiene i file che vengono invocati direttamente dal client
- it.mds.sdk.flusso.siar.riab.dto che contiene le classi che rappresentano il modello interno di sdk
- it.mds.sdk.flusso.siar.riab.mapper che contiene le classi di conversione

Nella cartella src/main/resources sono presenti le seguenti cartelle:
- META-INF che contiene file di configurazione
- sicof xhe contiene file .moustache
- template contiene un file di regole e file .csv, .xml e .xsd

sono presenti in resources anche file di configurazione:
- application.yaml
- config-flusso.properties
- csvHeaderMapping.properties
- logback-spring.xml
- tmp.xml

è presente il file pom.xml (Project Object Model), è un file XML che contiene le informazioni sul progetto e dettagli sulle configurazioni utilizzate da Maven per eseguire la build del progetto

### Prerequisiti e dipendenze

Il microservizio può girare su qualsiasi sistema operativo per cui è prevista una JVM (Java Virtual Machine) e utilizza la versione 2.7.17 di Spring Boot.

### Istruzioni per l'installazione

Per poter eseguire la build: 
build system maven,
comando mvn clean package

Per eseguire l'installazione è necessario prendere il jar generato dal build system e copiarlo in una cartella, successivamente all'interno della root folder ( / su Linux mentre C:\ su Windows) creare la cartella sdk e tutte le sottocartelle e i file necessari:
```
 /
 +- sdk
   +- db - la directory in cui viene genrato il db sqllite per la storicizzazione dele anagrafiche
   +- dir - la directory in cui inserire i csv da validare e inviare
   +- esiti - la directory in cui verranno depositati i file con gli esiti delle esecuzioni dell'sdk
   +- log - la directory in cui verranno scritti i log delll'applicativo
   +- progressivo - la directory in cui l'applicativo mantiene un file dat per la generazione degli id di esecuzione
   +- properties - la directory contenente i file di configurazione dell'sdk
      +- config-flusso.properties - file di configurazione principale (da referenziare in fase di avvio)  
      \- configurazioni-anagrafiche.properties - file per la configurazione del recupero delle anagrafiche 
   +- regole - la directory contenente le regole da applicare ai csv
   +- run - la cartella contenente i file di run per ogni singola esecuzione
   +- xmloutput - la directory contenente gli xml di output
   \- sent - la directory in cui vengono spostati gli xml inviati al ministero
``` 
- #### config-flusso.properties
```
nome.flusso=<nome del flusso lato ministero>
flusso.categoria=<categoria del flusso lato ministero>
flusso.codifica=<codice identificativo del flusso lato ministero>
regole.percorso=<path completo al file xml delle regole: /sdk/regole/regole.xml>

xmloutput.percorso=<path completo della folder in cui scrivere l'output>/SDK_{{periodoRiferimento}}_{{idRun}}.xml (/sdk/xmloutput/SDK_{{periodoRiferimento}}_{{idRun}}.xml)

sent.percorso=<path completo della directory in cui spostare gli xml inviati al ministero: /sdk/sent/>
flusso.percorso=<path completo della directory in cui verranno depositati i file csv: /sdk/dir/>
soglia.invio.mds=<numero intero indicante quanti la soglia di record validi per file affinché possa essere inviato l'xml di output: 100>
separatore=<carattere di separazione dei valori nel csv: ~>

run.percorso=<path completo della directory in storicizzare i file di run: /sdk/run>
esito.percorso=<path completo della directory in cui depositare i file di esito: /sdk/esiti>
progressivo.percorso=<path completo della directory in cui generare il file dat dei progressivi: /sdk/progressivo>

url.rest.gaf=<url per l'invio degli xml: https://api.salute.gov.it/api/gaf/upldfunc>
gaf.sender.authorizer.token-issuer.url=<url per l'autenticazione dell'invio: https://nsis-ids.sanita.it/nidp/oauth/nam/token>
gaf.sender.authorizer.token-issuer.grant_type=<flow di autenticazione: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.username=<username: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.password=<password: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.client_id=<client id: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.client_secret=<client secret: verrà fornita dal ministero>
gaf.sender.authorizer.token-issuer.scope=<scopes a cui deve appartenere l'utente: verranno forniti dal ministero>
gaf.sender.authorizer.type=<tipo di token di autenticazione: JWT>
gaf.sender.type=REST
gaf.sender.fileType=<categoria del flusso: valorizzare come flusso.categoria>
```

- #### configurazioni-anagrafiche.properties
```
sqlite.database.file.path=<path completo in cui creare il db sqllite: /sdk/db/anagrafica.db>
resilienza.ore=<time to live delle anagrafiche nel DB in ore: 2>

client.rest.headers.x-pplication-id: APP_ID_REGISTRYDOWNLOADER_CLIENT
client.type=REST
client.host=<url del gestore anagrafi: https://api.salute.gov.it/api/gestanag/v1>

rest.authorizer.type=<tipo del token di autorizzazione/autenticazione: JWT>
rest.authorizer.token-issuer.url=<url per la generazione di un token di autenticazione: https://nsis-ids.sanita.it/nidp/oauth/nam/token>
rest.authorizer.token-issuer.grant_type=<tipo di flow da utilizzare per l'autenticazione: client_credentials>
rest.authorizer.token-issuer.username=<username: verrà fornita dal ministero>
rest.authorizer.token-issuer.password=<password: verrà fornita dal ministero>
rest.authorizer.token-issuer.client_id=<client id: verrà fornita dal ministero>
rest.authorizer.token-issuer.client_secret=<client secret: verrà fornita dal ministero>
rest.authorizer.token-issuer.scope=<scopes a cui deve appartenere l'utenza: verrà fornita dal ministero>
```

### Istruzioni di avvio

Per avviare l'applicativo eseguire il seguente comando
```
java -jar <path completo del jar> --config=<path completo al file di configurazione principale>
```
Il comando farà partire il software che rimarrà in attesa di richieste sulla porta 8080

#### Avvio validazione di un csv
```
curl --location --request POST 'http://localhost:8080/v1/flusso/SIAR_RIAB' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--data-raw '{
    "nomeFile": "test.csv",
    "idClient": "1663" ,
    "modalitaOperativa":"P",
    "annoRiferimento": "2022",
    "periodoRiferimento": "13",
    "codiceRegione": "120"
}'
```

#### Recupero dell'esito di un'elaborazione
```
curl --location --request GET 'http://localhost:8080/v1/flusso/SIAR_RIAB/info?idRun=34' --header 'Accept: */*'
```

### Detentori di copyright

### Incaricati del mantenimento del progetto open source

### Contatti per segnalazioni

## mantainer:
Accenture SpA until January 2026
