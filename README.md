# AGEFI WEB SERVICE 
The document describes the AGEFI API to manage ressources on the AGEFI platform. It includes the description of the ressources as well as the allowed operations. 

## Getting started

All actions in the API are secured with the OAUTH2 protocol. Developpers must be familiar with the protocol in order to use the API. The API is provided as a RESTFull Web service, it is also required that developers understand how REST Web services work. 

* Web service type : REST
* Exchange format : JSON 

### Authentification

All operations in the API, require an access token. The access token can be otained with the following request usinge the secretkey. If you don't have a secret key, please contact us.  
* URL : http://agefi-emploi.fr/auth
* Parameters : grant_type = client_credentials
* Header -u username:secretKey

#### Exemple
```
curl -u username:secretKey "http://agefi-emploi.fr/auth" -d
'grant_type=client_credentials'
```
Please adapt the query according to your programming language. 

* Response
```
{"access_token":"xxxxxxxxxxxxxxxxxx",
"expires_in":3600,
"token_type":"Bearer",
"scope":null}
```

* access_token : contains the access token to use to access the web service, it should be securely saved locally
* expires_in : validity of the access key in seconds

### For all the operations in the API 
* Required Parameters : access_token


### JOB resssources
* URI: http://agefi-emploi.fr/jobs
* Parameters : access_token
* Supported Operations : GET, POST, PUT, DELETE 
* Fields : 
```
[
  "jobNom" : String,
  "jobActivite" : integer,
  "jobLocalisation" : integer,
  "jobTypePoste" : integer,
  "jobExperience":integer,
  "jobSalaire":integer,
  "jobDuree" : integer,
  "jobDateStart" : date,
  "jobMission" : String,
  "jobProfil" : String,
  "jobSteId" : integer //enterprise ID,
  "jobCandatureLien" : String,
  "jobCandatureTexte" : String,
  "jobCandidatureEmail" : email 
  "jobTypeCandidature" : integer (
  "jobMetierId" : integer,
  "enAvant" : String,
  "dateModification" : date,
  "jobDatePublication" : date,
  "jobStatut" : integer,
  "contact" : email
]
```

* Required Fields 

```
[
  "jobNom",
  "jobActivite",
  "jobLocalisation",
  "jobTypePoste",
  "jobExperience",
  "jobMission",
  "jobProfil",
  "jobSteId",
  "contact"
]
```

* Extra Actions : Filter jobs 
* Parameters : filter - possible values (jobActivite, jobLocalisation,
* jobTypePoste, jobExperience,jobSteId)
* Example: 

```
$curl "http://agefi-emploi.fr/jobs?
access_token=758b5034c743e2351c96451decb4d93db656417e&jobActivite=24
```

## jobTypePoste Ressources 
* URI : http://agefi-emploi.fr/jobActivites
* Parameter : access_token
* VERBS : GET
* RESPONSE: JSON 

## jobLocalisations Ressources 
* URI : http://agefi-emploi.fr/jobLocalisations
* Parameter : access_token
* VERBS : GET
* RESPONSE: JSON

## jobTypePostes Ressources 
* URI : http://agefi-emploi.fr/jobTypePostes
* Parameter : access_token
* VERBS : GET
* RESPONSE: JSON

## entreprises Ressources 
* URI : http://agefi-emploi.fr/entreprises
* Parameter : access_token
* VERBS : GET
* RESPONSE: JSON

## jobExperiences Ressources 
* URI : http://agefi-emploi.fr/jobExperiences
* Parameter : access_token
* VERBS : GET
* RESPONSE: JSON

