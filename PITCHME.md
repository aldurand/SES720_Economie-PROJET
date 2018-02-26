## Projet SES 720: Power Ledger

### Presentation du 27/02/2018
#### Xavier Charef, Mehdi Regina, Alexandre Durand

---
## Contexte

---?image=assets/image/contexte.png&size=auto 90%

---
- La demande métier est souvent par nature floue et evolutive

- Le metier veut brancher sa dataviz, croiser les données avec d'autres applications existantes, offrir une interface web
- Tout en ayant une architecture souple, perenne qui minimise les coûts de développement, d'évolution et d'intégration à l'existant

---
## Marché & Analyse de la concurrence
---
#### Présenter une vue macroscopique <br> des événements sur un mois donné:
- Goldstein Scale
- Tonalité
- CAMEO Root Code
- Nombre de sources
- Géolocalisation

---

## Business Model

---
### Value Proposition
---?image=assets/image/powerledger_reagulated_deregulated_market.png&size=auto 75%

---
### Value Creation
---?image=assets/image/power_ledger_plateform_schema.png&size=auto 75%

---
 - Les Sparkz sont convertibles en la monnaie locale de l’utilisateur
 - Les POWR échangés en Sparkz au cours de Smart Bond.
---
### Value Communication
 - "Democratize and green the enegy space" / "Co-create the future of energy"
---?image=assets/image/canaux_communication.png&size=auto 75%
 

---
### Value Delivery
---
---?image=assets/image/distribution_channel.png&size=auto 75%
---?image=assets/image/retraite_video_power.png&size=auto 75%


---
### Value Capture
---
- GDELT: tables avec des liens relationnels
- Transformation en une seule collection "events" de documents contenant l'event et ses mentions

##### (scrolldown to see the entire sample)
```json
{
	"globalEventId" : 653358758,
	"day" : 20170507,
	"monthyear" : 201705,
	"year" : 2017,
	"fractionDate" : 2017.347900390625,
	"isRootEvent" : 1,
	"eventCode" : "057",
	"eventBaseCode" : "057",
	"eventRootCode" : "05",
	"quadClass" : 1,
	"goldsteinScale" : 8,
	"numMentions" : 2,
	"numSources" : 1,
	"numArticles" : 2,
	"avgTone" : -3.200000047683716,
	"dateadded" : NumberLong("20170507000000"),
	"sourceurl" : "http://www.informationclearinghouse.info/47003.htm",
	"actor1" : {
		"code" : "IRN",
		"name" : "IRAN",
		"countryCode" : "IRN",
		"knownGroupCode" : "",
		"ethnicCode" : "",
		"geography" : {
			"type" : 4,
			"fullname" : "Moscow, Moskva, Russia",
			"countryCode" : "RS",
			"ADM1Code" : "RS48",
			"ADM2Code" : "25106",
			"coordinates" : [
				55.752201080322266,
				37.6156005859375
			]
		}
	},
	"actor2" : {
		"code" : "TUR",
		"name" : "TURKEY",
		"countryCode" : "TUR",
		"knownGroupCode" : "",
		"geography" : {
			"type" : 4,
			"fullname" : "Tehran, Tehran, Iran",
			"countryCode" : "IR",
			"ADM1Code" : "IR26",
			"ADM2Code" : "41130",
			"coordinates" : [
				35.75,
				51.514801025390625
			]
		}
	},
	"actionGeo" : {
		"type" : 4,
		"fullname" : "Moscow, Moskva, Russia",
		"countryCode" : "RS",
		"ADM1Code" : "RS48",
		"ADM2Code" : "25106",
		"coordinates" : [
			55.752201080322266,
			37.6156005859375
		]
	},
	"mentions" : [
		{
			"doctone" : -3.2,
			"id" : "http://www.informationclearinghouse.info/47003.htm",
			"sourceName" : "informationclearinghouse.info",
			"type" : 1,
			"timeDate" : "20170507000000"
		}
	]
}
```

---
## Architecture

[comment]: <> (---?image=assets/image/_ARCHI.png&size=auto 58%)

---?image=assets/image/_ARCHI_white.png&size=auto 57%

---
- **Import des données: MongoSpark**  
  - Processing et transformation des fichiers GDELT par traitement Spark/Scala  
  - Sauvegarde des données directement dans notre cluster MongoDB

- **Stockage: MongoDB**  
Un ReplicaSet de 3 machines

- **Visualisation**  
API REST + Notebook Python

---

## Passage du PoC <br> à la Production :

- Charger toute l'année
  - Sharding (sharding-Key = un des champs 'date')
    (si volume données > 100 Go, d'après préco. MongoDB)

- Inclure les GKG à nos données
  - De nouvelles requêtes possibles

---

### Merci de votre attention

### Des questions?
