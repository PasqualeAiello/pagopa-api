
<img width="150px"  src="https://www.cittametropolitana.genova.it/sites/default/files/siti-tematici/Logo%20PagoPA.jpg" title="pagoPa" alt="pagoPa"></a>
# Giornale dei Pagamenti
Il Giornale dei pagamenti raccoglie gli eventi registrati, da un soggetto aderente (EC/PSP), che determinano un cambiamento di stato del pagamento.

Ogni evento riportato è caratterizzato dai seguenti elementi :
- data ed ora dell'evento registrato (dateTime)
- identificativo del pagamento (IUV,CCP)
- codice dell'evento rilevato (eventCode)
- descrizione dell'evento (eventDescription)
- (opzionale) descrittore dell'errore riscontrato


## Stato della posizione debitoria
Il diagramma riporta il ciclo di vita di un pagamento 

![pagoPA posizione debitoria](https://www.plantuml.com/plantuml/svg/ZP3F2i8m38VlUOgUXRs01rceHNkmAslOGP4niKXXMsMh5v_U_SDjuC4Sy_k-X2HkGz64LrK211TAoxHltTlvshAzlRdW6rUmP_7m6W4kcokBeXr38fdXMIPAR5cgAKybFqfX2FD5zCNdLEC1Jq9HmaPFgapYq8U5-B_q2-fbgJWQaumySYw81iDecA9fHoPICmzViTszGwsWtkhEWjZMz-vf7m00)



## Trasmissione del dato
Il Giornale dei Pagamenti viene scambiato come file format .zip identificato con il seguente formato
```
GDP_<tipoMittente>_<identificativoMittente>_<data>_<progressivo> 
```
ove:
- tipoMittente, identifica la tipologia del soggetto aderente che invia il dato (EC o PSP )
- identifivativoMittente, identifica in maniera univoca il mittente attraverso il prorpio idDominio ( nel caso EC ) ed identificativoPSP ( nel caso PSP)
- data, specifica la data della giornata operativa a cui il documento di riferisce
- progressivo, numero intero progressivo che permette di inviare più volte il giornale dei pagamenti


## eventCode List
il campo eventCode può assumere uno dei segenti valori ( i campi in corsivo sono nuovi valori rispetto a quanto pubblicato nelle SANP 2.2)

|Event Code   			| Description	| 
|---					|---			|
|RPT_PARCHEGGIATA_NODO	|	RPT parcheggiata sul nodo in attesa di essere sbloccata per il pagamento con WISP 2.0|
|RPT_RICEVUTA_NODO		|RPT ricevuta dal Nodo e in attesa di essere processata|
|RPT_RIFIUTATA_NODO		|RPT rifiutata dal Nodo per sintassi o semantica errata|
|RPT_ACCETTATA_NODO		|RPT accettata dal Nodo come valida|
|RPT_RIFIUTATA_PSP		|RPT rifiutata dall’Intermediario PSP per sintassi o semantica errata|
|RPT_ERRORE_INVIO_A_PSP	|RPT inviata all’Intermediario PSP - indisponibilità del ricevente|
|RPT_INVIATA_A_PSP		|RPT inviata all’Intermediario PSP - azione in attesa di risposta|
|RPT_ACCETTATA_PSP		|RPT ricevuta ed accettata dall’Intermediario PSP come valida|
|RPT_DECORSI_TERMINI	|RPT ha superato il periodo di decorrenza termini nel Nodo|
|RT_RICEVUTA_NODO		|RT ricevuta dal Nodo|
|RT_RIFIUTATA_NODO		|RT rifiutata dal Nodo per sintassi o semantica errata|
|RT_ACCETTATA_NODO		|RT accettata dal Nodo come valida ed in corso di invio all’Intermediario dell’Ente Creditore|
|RT_ACCETTATA_PA		|RT ricevuta dall’Intermediario dell’Ente Creditore ed accettata|
|RT_RIFIUTATA_PA		|RT ricevuta dall’Intermediario dell’Ente Creditore e rifiutata|
|RT_ESITO_SCONOSCIUTO_PA|sito dell’accettazione RT dell’Intermediario dell’Ente Creditore non interpretabile|
|*RPT_RICHIESTA_ATTIVAZIONE*| Viene richiesta attivazione del pagamento|
|*RPT_ATTIVAZIONE_ACCETTATA_NODO*| Richiesta di Attivazione accettata dal Nodo
|*RPT_ATTIVATA_PA*| Richiesta di attivazione accettata dall'EC 
|*RPT_ATTIVATA_ERRORE*| Errore durante la richiesta di attivazione
|*RPT_PAGATA*| RPT incassata
|*RPT_ANNULLATA*| RPT non incassata|
|*RPT_FLUSSO*| lo IUV inseriro all'interno del flusso di rendicontazione


### eventCode PSP
Specificatamente per il PSP, vengono definite le condizioni che generano lo stato ( trigger)

|Event Code   			| Trigger	| 
|---					|---			|
|RPT_RIFIUTATA_PSP| generato a seguito di un errore alla primitiva pspInviaRPT / pspInviaCarrelloRPT / pspInviaCarrelloCarteRPT
|RPT_ACCETATA_PSP| generato a seguito della response posivitiva alla primitiva pspInviaRPT / pspInviaCarrelloRPT / pspInviaCarrelloCarteRPT
|RT_ACCETTATA_NODO| generato a seguito dell'OK alla primitiva pspCHiediRT 
|RT_ACCETATA_PA| generato a seguito dell'OK nodoInviaRT / pspInviaAckRT
|RT_RIFIUTATA_PA| errore ricevuto sulla primitiva nodoInviaRT / pspInviaAckRT
|*RPT_RICHIESTA_ATTIVAZIONE*| a seguito dell'invio della primitiva nodoAttivaRPT 
|*RPT_ATTIVATA_PA*| a seguito della response positiva alla primitivia nodoAttivaRPT 
|*RPT_ATTIVATA_ERRORE*| a seguito della response negativa alla primitivia nodoAttivaRPT 
|*RPT_PAGATA*| a seguito dell'avvenuto incasso da parte del PSP
|*RPT_ANNULLATA*| a seguito di un incasso mancato da parte del PSP ( dopo un attivazione)
|*RPT_FLUSSO*| lo IUV è stato iscritto all'interno del processo di generazione del flusso di rendicontazione.

### eventCode EC

Specificatamente per l'EC, vengono definite le condizioni che generano lo stato ( trigger)

|Event Code   			| Trigger	| 
|---					|---			|	
|RPT_ATTIVATA_PA	| generato a seguito di una risposta positiva alla primitiva paaAttivaRPT
|RPT_ACCETTATA_NODO | generato a seguito di una risposta positiva alla primitiva nodoInviaRPT / nodoInviaCarrelloRPT
|RPT_RIFIUTATA_NODO| generato a seguito di una risposta negativa alla primitiva nodoInviaRPT / nodoInviaCarrelloRPT	
|RT_ACCETTATA_PA		|generato a seguito di una risposta positiva alla primitiva paaInviaRT 
|RT_RIFIUTATA_PA		|generato a seguito di una risposta negativa alla primitiva paaInviaRT 
|*RPT_ATTIVATA_PA*| generato a seguito di una risposta positiva alla primitiva paaAttivaRPT
|*RPT_ATTIVATA_ERRORE*| generato a seguito di una risposta negativa alla primitiva paaAttivaRPT
 

 
## Analisi di un pagamento
Tramite la collezione di tutti i giornali dei pagamenti, in unione con lo stato del pagamento tracciato all'interno di pagoPA è possibile analizzare lo stato delle posizione debitorie legate ai pagamenti avvenuti.

La macchina a stati è generata utilizzando la libreria  Xstate il cui progetto è disponibile al seguente link [XState-Project](https://xstate.js.org/viz/?gist=74a1dfd4a9ef709863d4c3deb4f353e6)
