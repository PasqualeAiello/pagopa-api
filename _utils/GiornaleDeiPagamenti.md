<img width="150px"  src="https://www.cittametropolitana.genova.it/sites/default/files/siti-tematici/Logo%20PagoPA.jpg" title="pagoPa" alt="pagoPa"></a>
# Giornale dei Pagamenti

Durante il workflow dei pagamenti, gli stati di un pagamento ( identificato da IUV e CCP ) sono riassunti dalla risposta alla primitiva nodoChiediStatoRPT, ovvero


RPT_PARCHEGGIATA_NODO	RPT parcheggiata sul nodo in attesa di essere sbloccata per il pagamento con WISP 2.0
RPT_RICEVUTA_NODO	RPT ricevuta dal Nodo e in attesa di essere processata
RPT_RIFIUTATA_NODO	RPT rifiutata dal Nodo per sintassi o semantica errata
RPT_ACCETTATA_NODO	RPT accettata dal Nodo come valida
RPT_RIFIUTATA_PSP	RPT rifiutata dall’Intermediario PSP per sintassi o semantica errata
RPT_ERRORE_INVIO_A_PSP	RPT inviata all’Intermediario PSP - indisponibilità del ricevente
RPT_INVIATA_A_PSP	RPT inviata all’Intermediario PSP - azione in attesa di risposta
RPT_ACCETTATA_PSP	RPT ricevuta ed accettata dall’Intermediario PSP come valida
RPT_DECORSI_TERMINI	RPT ha superato il periodo di decorrenza termini nel Nodo
RT_RICEVUTA_NODO	RT ricevuta dal Nodo
RT_RIFIUTATA_NODO	RT rifiutata dal Nodo per sintassi o semantica errata
RT_ACCETTATA_NODO	RT accettata dal Nodo come valida ed in corso di invio all’Intermediario dell’Ente Creditore
RT_ACCETTATA_PA	RT ricevuta dall’Intermediario dell’Ente Creditore ed accettata
RT_RIFIUTATA_PA	RT ricevuta dall’Intermediario dell’Ente Creditore e rifiutata
RT_ESITO_SCONOSCIUTO_PA	Esito dell’accettazione RT dell’Intermediario dell’Ente Creditore non interpretabile


Si definiscono i seguenti nuovi stati al fine di tracciare l'inizializzazione di un workflow presso il PSP
RPT_ATTIVAZIONE_ACCETTATA_NODO Ricevuta richiesta di attivazione da parte di un PSP


Inoltre, si definiscono gli stati presso l'EC ed il PSP.

Per l'EC
RPT_ATTIVATA_PA	L'EC ha ricevuto una richiesta di attivazione di pagamento
RPT_INVIATA_PA	L'EC ha inviato una RPT al nodo
RPT_ACCETATA_NODO	L'EC ha riscontro positivo dell'invio della RPT verso il NODO
RPT_RIFIUTATA_NODO	L'EC ha riscontro negativo dell'invio della RPT verso il Nodo
RT_RICEVUTA_PA	L'EC ha ricevuto una RT
RT_ACCETATA_PA	L'EC ha accettatato la RT
RT_RIFIUTATA_PA	L'EC ha rifiutato la RT

Per il PSP
RPT_ERRORE_ATTIVAZIONE	Il PSP ha ricevuto esito KO sulla richiesta di attivazione
RPT_ATTIVATA_PSP	il PSP ha ricevuto esito OK sulla richiesta di attivazione
RPT_RICHIESTA_ATTIVAZIONE	il PSP ha inviato una richiesta di attivazione
RPT_ACCETTATA_PSP	
RPT_INVIATA_A_PSP	
PAGATO	
ANNULLATO	
FLUSSO	

 
