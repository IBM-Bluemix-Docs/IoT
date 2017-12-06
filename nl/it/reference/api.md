---

copyright:

years: 2017
lastupdated: "2017-07-20"

---

{:new_window: target="\_blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}


# API
{: #api_overview}

Sono disponibili molte API per lo sviluppo del codice per i dispositivi, i gateway e le applicazioni collegate a {{site.data.keyword.iot_full}}.

Le API HTTP sono protette con l'autenticazione di base HTTP. Quando generi una chiave API utilizzando il dashboard, ti vengono presentati un token di autenticazione e una chiave. Per ulteriori informazioni sui token e sulle chiavi API, consulta [Connessione chiave API](../platform_authorization.html#api-key).


## Informazioni sulle API HTTP
{: #api_about}

Dopo la registrazione alla tua propria organizzazione, ti viene fornito un ID dell'organizzazione di 6 caratteri che è necessario nel nome host di ogni chiamata API HTTP. È possibile accedere all'URL di base della tua organizzazione al seguente indirizzo:

https://<**orgId**>.internetofthings.ibmcloud.com/api/v0002

Per autenticare le richieste nell'API dell'applicazione, imposta in nome utente sulla chiave API e la password sul token di autenticazione.

Per le API di messaggistica, utilizza il seguente indirizzo:

https://<**orgId**>.messaging.internetofthings.ibmcloud.com/api/v0002

## API HTTP
{: #api_http}

API                     | Utilizzata per ...       
------------- | -------------
[Organization Administration ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/orgAdmin.html){: new_window} | Configura un'organizzazione (incluse la creazione e l'eliminazione dei dispositivi), controlla l'utilizzo, lo stato del servizio ed esegue la diagnostica dei problemi di connessione del dispositivo.
[Security ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/security.html){: new_window} | Gestisce l'autenticazione egli inviti utente e l'autorizzazione degli utenti, delle chiavi API e dei dispositivi.
[Information Management ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/info-mgmt.html){: new_window} |  Accede ai dati evento del dispositivo, così come all'ubicazione del dispositivo e ottiene le informazioni sul meteo per tale ubicazione. 
[Data Management  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/state-mgmt.html){: new_window}   |   Organizza e integra i dati in entrata e in uscita di {{site.data.keyword.iot_short_notm}}.
[Device Management ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/deviceMgmt.html){: new_window} | Interagisce con i dispositivi gestiti utilizzando il protocollo di gestione del dispositivo.
[Messaging ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/http-messaging.html){: new_window}   | Pubblica gli eventi e invia i comandi utilizzando HTTP.
[Risk Management ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/riskmgmt.html){: new_window}   | Gestisce le politiche e i report Risk Management.

## Estensione API HTTP
{: #api_extension}

API                     | Utilizzata per ...       
------------- | -------------
[AT&T Extension ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-atnt.html){: new_window} | Gestisce i dispositivi AT&T.
[Jasper Extension  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-jasper.html){: new_window} | Gestisce i dispositivi Jasper.
[Orange Extension  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002/ext-orange.html){: new_window} | Visualizza i dati della SIM card dai dispositivi collegati ala tua organizzazione {{site.data.keyword.iot_short_notm}} e ha una SIM card Orange installata.

## API HTTP beta
{: #api_beta}

API                     | Utilizzata per ...       
------------- | -------------
[Gateway Security  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/security-gateway-beta.html){: new_window}   | Controlla e assegna i ruoli ai dispositivi gateway.
[Device Security  ![Icona link esterno](../../../icons/launch-glyph.svg)](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/security-devices-beta.html){: new_window} | Controlla e assegna i ruoli ai dispositivi.
[Access Control ![Icona link esterno](../../../icons/launch-glyph.svg "Icona link esterno")](https://docs.internetofthings.ibmcloud.com/apis/swagger/v0002-beta/security-subjects-beta.html){: new_window} | Limita l'accesso utente. 
