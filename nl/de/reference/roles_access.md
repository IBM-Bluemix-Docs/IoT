---

copyright:
  years: 2016, 2018
lastupdated: "2018-02-21"

---

{:new_window: target="blank"}
{:shortdesc: .shortdesc}
{:screen: .screen}
{:codeblock: .codeblock}
{:pre: .pre}

# Zugriffsebenen für Benutzerrollen

Die folgenden Tabellen zeigen die Zugriffsebenen der einzelnen Standardbenutzerrollen:

Die Tabellen zeigen Zugriffsebenen für:
- [Geräteoperationen](#user-device-ops)
- [Protokolloperationen](#user-log-ops)
- [Cacheoperationen](#user-cache-ops)
<!-- [Historian Operations](#user-historian) -->
- [Organisationsoperationen](#user-org-ops)
- [Zugriffssteuerungsoperationen](#user-access-ops)
<!-- - [Analytics Operations](#user-analytics-ops)-->
- [Operationen von Drittanbietern](#user-third-party)  
<!-- - [Risk Management Operations](#user-risk-mgt) -->

## Benutzerrollenberechtigungen {: #user-roles}

### Geräteoperationen {: #user-device-ops}

Geräteoperationen ||| Benutzerrollen|||
:--------: | -------------|-------------|---------------|-----|---
           | **Administrator** | **Operator** | **Entwickler** | **Analyst** | **Leser**
Geräte erstellen, aktualisieren oder löschen | X | X | X | - | -
Geräte anzeigen | X | X | X | X | X
Gerät aktivieren | X | X | X | - | -
Ereignis publizieren | - | - | - | - | -
Ereignis subskribieren | X | X | X | X | X
Befehl publizieren | X | X | X | - | -
Befehl subskribieren | - | - | - | - | -
Gerätemanagementaktion initiieren | X | X | X | - | -
Gerätemanagementaktionen anzeigen | X | X | X | X | X
Gerätemanagementaktionen löschen | X | X | X | - | -
DM-Aktionsbundles verwalten | X | X | X | - | -
Gerätetypen erstellen, aktualisieren oder löschen | X | X | X | - | -
Gerätetypen anzeigen | X | X | X | X | X
Diagnoseprotokolle verwalten | X | X | X | - | -
Diagnoseprotokolle anzeigen | X | X | X | - | -

### Protokolloperationen {: #user-log-ops}

Protokolloperationen ||| Benutzerrollen|||
:--------: | -------------|-------------|---------------|-----|---
           | **Administrator** | **Operator** | **Entwickler** | **Analyst** | **Leser**
Serverprotokolle anzeigen | X | X | X | X | X

### Cacheoperationen {: #user-cache-ops}

Cacheoperationen ||| Benutzerrollen|||
:--------: | -------------|-------------|---------------|-----|---
           | **Administrator** | **Operator** | **Entwickler** | **Analyst** | **Leser**
Livedaten anzeigen (Ereigniscache) | X | X | X | X | X
Livedaten verwalten (Ereigniscache) | X	| X | X |	X	| -

### Organisationsoperationen {: #user-org-ops}

Organisationsoperationen ||| Benutzerrollen|||
:--------: | -------------|-------------|---------------|-----|---
           | **Administrator** | **Operator** | **Entwickler** | **Analyst** | **Leser**
Konfigurieren von Speicherparametern|	X| - |-|-|-				
Authentifizierungsprovider konfigurieren|	X|-|-|-|-				
Mailkonfiguration erstellen, anzeigen, aktualisieren, löschen	|X|-|-|-|-				
Verfügbare IoTP-Mailprovider anzeigen	|X|	X|-|-|-			
Mailvorlagen erstellen, anzeigen, aktualisieren, löschen	|X	|X	|-|-|-		
Benutzer erstellen, aktualisieren, löschen	|X|	X|-|-|-			
Benutzer anzeigen	|X|	X|	X|	X|-
Benutzereinladungen erstellen, aktualisieren, löschen|	X	|X	| -|-|-		
Benutzereinladungen anzeigen	|X	|X	|- |- |-		
Einladung abschließen	|X|	X|	X|	X|	X
API-Schlüssel erstellen, aktualisieren, löschen	|X	|X	| -|-|-		
API-Schlüssel anzeigen	|X	|X	|- |- |-		
ORG-Nutzungsinformationen anzeigen	|X	|X	| -|-|-		

### Zugriffssteuerungsoperationen {: #user-access-ops}

Zugriffssteuerungsoperationen ||| Benutzerrollen|||
:--------: | -------------|-------------|---------------|-----|---
           | **Administrator** | **Operator** | **Entwickler** | **Analyst** | **Leser**
Benutzereigenschaften einschließlich Zugriffsrechte anzeigen	|X|	X|	X|	X| -
Eigene Eigenschaften des Benutzers einschließlich Zugriffsrechte anzeigen	|X|	X|	X|	X|	X
Benutzer einschließlich Zugriffsrechte verwalten	|X	|X	|-|-|-		
Eigenschaften des API-Schlüssels einschließlich Zugriffsrechte anzeigen|	X|	X|	X|	X|-
Eigene Eigenschaften des API-Schlüssels einschließlich Zugriffsrechte anzeigen	|-|	-|	-| -| -		
API-Schlüssel einschließlich Zugriffsrechte erstellen, aktualisieren, löschen	|X	|X	|-|-|-		
Geräteeigenschaften einschließlich Zugriffsrechte anzeigen	|X|	X|	X|	X|	X
Eigene Eigenschaften des Geräts einschließlich Zugriffsrechte anzeigen	|-	|- |- |- |-
Geräte einschließlich Zugriffsrechte erstellen, aktualisieren, löschen	|X|	X|	X|	-| -
Rollen anzeigen	|X	|X	|X	|X	|X
Angepasste Rollen erstellen, aktualisieren, löschen	|X	|X |- |- |-
Operationen anzeigen*	|X	|X	|X	|X	|X

### Serviceoperationen von Drittanbietern {: #user-third-party}

Serviceoperationen von Drittanbietern ||| Benutzerrollen|||
:--------: | -------------|-------------|---------------|-----|---
           | **Administrator** | **Operator** | **Entwickler** | **Analyst** | **Leser**
Stapelbenachrichtigungen von einer externen Plattform verarbeiten	|X|	X	|X |-|-
Stapelbenachrichtigungen verarbeiten und an eine externe Plattform senden	|X|	X	|X| -| -		
Ereignis für ein Gerät publizieren	|X|	X	|X|	- |-
Ereignisse eines Geräts subskribieren	|X	|X	|X |-| -		
Callback-URL für die externe Plattform festlegen	|X	|X	|X|	-| -
Subskriptionsebene der externen Plattform festlegen|	X|	X|	X |- |-		
Allgemeinzustand vom Connector abrufen	|X|	X	|X	|- |-
Prüfen, ob ein externes System aktiv ist, und Berechtigungsnachweise validieren	|X	|X|	X	|- |-
