[comment]: # "Auto-generated SOAR connector documentation"
# Digital Shadows

Publisher: Digital Shadows Ltd\.  
Connector Version: 2\.0\.2  
Product Vendor: Digital Shadows  
Product Name: Digital Shadows SearchLight  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 5\.2\.0  

The Digital Shadows SearchLight App allows users to create flexible and dynamic playbooks that fully harness the capabilities provided by the Digital Shadows SearchLight API

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Digital Shadows SearchLight asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**ds\_api\_key** |  required  | string | The account key of the Digital Shadows portal that is used to configure this app
**ds\_api\_secret\_key** |  required  | password | A secured key that is linked with the API key used to configure this app
**private\_incident** |  optional  | boolean | A private incident is an event that could lead to loss of, or disruption to, an organization's operations, services, or functions
**global\_incident** |  optional  | boolean | A global incident is a type of event that can remotely lead to the loss of an organization's resources
**history\_days\_interval** |  required  | string | Historical days for which data needs to be polled by the application\. Example input\: 10 \(for last 10 days data\)
**inc\_typ\_data\_leakage** |  optional  | boolean | The severity of Data Leakage incident is based on the observation that sensitive client systems information, with credentials, is publicly available
**inc\_typ\_brand\_protection** |  optional  | boolean | Brand Protection is a type of incident in which attackers impersonate domains, social accounts, people, and mobile applications
**inc\_typ\_infrastructure** |  optional  | boolean | Infrastructure incident occurs when an internal network protocol is exposed to the internet
**inc\_typ\_physical\_security** |  optional  | boolean | Physical Security incident occurs when the certificate of a domain has security issues
**inc\_typ\_social\_media\_compliance** |  optional  | boolean | Social Media Compliance incident consists of exploiting secured information such as passwords on social media
**inc\_typ\_cyber\_threat** |  optional  | boolean | Cyber Threat incident usually consists of a company's account information to be sold and accessed by unauthorized personnel

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate connection to the Digital Shadows API  
[on poll](#action-on-poll) - Callback action for the 'on\_poll' ingest functionality  
[search all records](#action-search-all-records) - Search across all Digital Shadow's entities including incidents, threat profiles, and our closed data stores  
[get incident](#action-get-incident) - Retrieve a single incident and its details, identified by its unique integer identifier  
[search incidents](#action-search-incidents) - Search incidents based on filters\. The On Poll action also uses this endpoint to collect incidents for a given time range/interval  
[get incident review](#action-get-incident-review) - Retrieve the history of all review submissions for a given incident, ordered by submission time with the most recent submission first  
[post incident review](#action-post-incident-review) - Post a status update to the incident along with a note  
[search intelligence incidents](#action-search-intelligence-incidents) - Meant to be a simple way to search Intelligence Incidents based on time range and incident types if needed  
[get intelligence incident](#action-get-intelligence-incident) - Retrieve a single intelligence incident and its details, identified by its unique integer identifier  
[get intelligenceincident ioc](#action-get-intelligenceincident-ioc) - Retrieve the indicators of compromise associated with an intelligence incident  
[search data breaches](#action-search-data-breaches) - Search across all data breaches that are relevant to your organization  
[get data breach](#action-get-data-breach) - Retrieve a single data breach and its details, identified by its unique integer identifier\. The records associated with the breach must be retrieved using a separate operation  
[search databreach records](#action-search-databreach-records) - Search data breach records across all data breaches\. This operation also includes basic information about the data breach the record occurred within  
[get databreach records](#action-get-databreach-records) - Retrieve breach records \(credentials\) for a specific breach  
[get breachrecord byuser](#action-get-breachrecord-byuser) - This action allows you to search breach records based on the domain, review status, or full/partial strings from the username  
[get breachrecord review](#action-get-breachrecord-review) - Retrieve the list of review status updates for a given data breach record  
[post breachrecord review](#action-post-breachrecord-review) - Update an individual breach record's notes or status using this action  

## action: 'test connectivity'
Validate connection to the Digital Shadows API

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'on poll'
Callback action for the 'on\_poll' ingest functionality

Type: **ingest**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**start\_time** |  optional  | Start of the polling time range for which the app will fetch all the events after this time\. It should be in epoch time \(milliseconds\)\. Example \- 1611587778000 | numeric | 
**end\_time** |  optional  | End of the polling time range for which the app will fetch all the events before this time\. It should be in epoch time \(milliseconds\)\. Example \- 1611587778000 | numeric | 

#### Action Output
No Output  

## action: 'search all records'
Search across all Digital Shadow's entities including incidents, threat profiles, and our closed data stores

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**date\_range** |  required  | Date Range\. Example input\: P30D\(for Past 30 Days\) | string |  `digital shadows date range` 
**query** |  required  | Search string | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.date\_range | string |  `digital shadows date range` 
action\_result\.parameter\.query | string | 
action\_result\.data | string | 
action\_result\.summary\.entity\_count | string | 
action\_result\.summary\.entity\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get incident'
Retrieve a single incident and its details, identified by its unique integer identifier

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**incident\_id** |  required  | Digital Shadows Incident ID | numeric |  `digital shadows incident id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.incident\_id | numeric |  `digital shadows incident id` 
action\_result\.data | string | 
action\_result\.summary\.incident\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'search incidents'
Search incidents based on filters\. The On Poll action also uses this endpoint to collect incidents for a given time range/interval

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**date\_range** |  required  | Incident Date Range\. Example input\: P30D\(for Past 30 Days\) | string |  `digital shadows date range` 
**incident\_types** |  optional  | Incident Types | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.date\_range | string |  `digital shadows date range` 
action\_result\.parameter\.incident\_types | string | 
action\_result\.data | string | 
action\_result\.summary\.incident\_count | string | 
action\_result\.summary\.incident\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get incident review'
Retrieve the history of all review submissions for a given incident, ordered by submission time with the most recent submission first

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**incident\_id** |  required  | Digital Shadows Incident ID | numeric |  `digital shadows incident id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.incident\_id | numeric |  `digital shadows incident id` 
action\_result\.data | string | 
action\_result\.summary\.incident\_reviews\_count | numeric | 
action\_result\.summary\.incident\_reviews\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'post incident review'
Post a status update to the incident along with a note

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**incident\_id** |  required  | Incident ID | numeric |  `digital shadows incident id` 
**review\_note** |  required  | Incident Review Note | string | 
**review\_status** |  required  | Incident Review Status | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.incident\_id | numeric |  `digital shadows incident id` 
action\_result\.parameter\.review\_note | string | 
action\_result\.parameter\.review\_status | string | 
action\_result\.data | string | 
action\_result\.summary\.incident\_reviews\_message | boolean | 
action\_result\.summary\.incident\_reviews\_status\_code | string | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'search intelligence incidents'
Meant to be a simple way to search Intelligence Incidents based on time range and incident types if needed

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**date\_range** |  required  | Intelligence Incident Date Range\. Example input\: P30D\(for Past 30 Days\) | string |  `digital shadows date range` 
**incident\_types** |  optional  | Incident Types | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.date\_range | string |  `digital shadows date range` 
action\_result\.parameter\.incident\_types | string | 
action\_result\.data | string | 
action\_result\.summary\.intelligence\_incident\_count | string | 
action\_result\.summary\.intelligence\_incident\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get intelligence incident'
Retrieve a single intelligence incident and its details, identified by its unique integer identifier

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**intel\_incident\_id** |  required  | Digital Shadows Intelligence Incident ID | numeric |  `digital shadows intelligence incident id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.intel\_incident\_id | numeric |  `digital shadows intelligence incident id` 
action\_result\.data | string | 
action\_result\.summary\.intelligence\_incident\_count | string | 
action\_result\.summary\.intelligence\_incident\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get intelligenceincident ioc'
Retrieve the indicators of compromise associated with an intelligence incident

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**intel\_incident\_id** |  required  | Digital Shadows Intelligence Incident IoCs ID | numeric |  `digital shadows intelligence incident id` 
**types** |  optional  | Types | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.intel\_incident\_id | numeric |  `digital shadows intelligence incident id` 
action\_result\.parameter\.types | string | 
action\_result\.data | string | 
action\_result\.summary\.intelligence\_incident\_ioc\_count | string | 
action\_result\.summary\.intelligence\_incident\_ioc\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'search data breaches'
Search across all data breaches that are relevant to your organization

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**date\_range** |  required  | Data Breach Date Range\. Example input\: P30D\(for Past 30 Days\) | string |  `digital shadows date range` 
**reposted\_credentials** |  optional  | Data Breach reposted Credentials | string | 
**severities** |  optional  | Severities | string | 
**statuses** |  optional  | Statuses | string | 
**user\_name** |  optional  | Username \(use '\*' for wildcard matching\) | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.date\_range | string |  `digital shadows date range` 
action\_result\.parameter\.reposted\_credentials | string | 
action\_result\.parameter\.severities | string | 
action\_result\.parameter\.statuses | string | 
action\_result\.parameter\.user\_name | string | 
action\_result\.data | string | 
action\_result\.summary\.data\_breach\_count | string | 
action\_result\.summary\.data\_breach\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get data breach'
Retrieve a single data breach and its details, identified by its unique integer identifier\. The records associated with the breach must be retrieved using a separate operation

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**breach\_id** |  required  | Data Breach ID | numeric |  `digital shadows breach id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.breach\_id | numeric |  `digital shadows breach id` 
action\_result\.data | string | 
action\_result\.summary\.data\_breach\_count | string | 
action\_result\.summary\.data\_breach\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'search databreach records'
Search data breach records across all data breaches\. This operation also includes basic information about the data breach the record occurred within

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**date\_range** |  required  | Data Breach record Date Range\. Example input\: P30D\(for Past 30 Days\) | string |  `digital shadows date range` 
**domain\_names** |  optional  | Data Breach record domain names \(comma separated\)\. Example input\: 'xyz\.com, abc\.org'  | string | 
**review\_statuses** |  optional  | Review Statuses | string | 
**distinction** |  optional  | Distinction | string | 
**user\_name** |  optional  | Username \(use '\*' for wildcard matching\) | string | 
**password** |  optional  | Password \(use '\*' for wildcard matching\) | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.date\_range | string |  `digital shadows date range` 
action\_result\.parameter\.distinction | string | 
action\_result\.parameter\.domain\_names | string | 
action\_result\.parameter\.password | string | 
action\_result\.parameter\.review\_statuses | string | 
action\_result\.parameter\.user\_name | string | 
action\_result\.data | string | 
action\_result\.summary\.data\_breach\_record\_count | string | 
action\_result\.summary\.data\_breach\_record\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get databreach records'
Retrieve breach records \(credentials\) for a specific breach

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**breach\_id** |  required  | Data Breach ID | numeric |  `digital shadows breach id` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.breach\_id | numeric |  `digital shadows breach id` 
action\_result\.data | string | 
action\_result\.summary\.data\_breach\_record\_count | string | 
action\_result\.summary\.data\_breach\_record\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get breachrecord byuser'
This action allows you to search breach records based on the domain, review status, or full/partial strings from the username

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**user\_name** |  required  | Username \(use '\*' for wildcard matching\) | string | 
**domain\_names** |  optional  | Domain Names \(comma separated\) | string | 
**published\_date\_range** |  optional  | Published Date Range\. Example input\: P30D\(for Past 30 Days\) | string | 
**review\_statuses** |  optional  | Review Statuses \(comma separated\)\. Example\: open, read, closed | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.domain\_names | string | 
action\_result\.parameter\.published\_date\_range | string | 
action\_result\.parameter\.review\_statuses | string | 
action\_result\.parameter\.user\_name | string | 
action\_result\.data | string | 
action\_result\.summary\.data\_breach\_record\_count | string | 
action\_result\.summary\.data\_breach\_record\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get breachrecord review'
Retrieve the list of review status updates for a given data breach record

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**breach\_record\_id** |  required  | Digital Shadows Breach Record ID | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.breach\_record\_id | numeric | 
action\_result\.data | string | 
action\_result\.summary\.breach\_record\_reviews\_count | numeric | 
action\_result\.summary\.breach\_record\_reviews\_found | boolean | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'post breachrecord review'
Update an individual breach record's notes or status using this action

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**breach\_record\_id** |  required  | Data Breach Record ID | numeric | 
**review\_note** |  required  | Update an individual breach record's notes using this action | string | 
**review\_status** |  required  | Update an individual breach record's status using this action | string | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.parameter\.breach\_record\_id | numeric | 
action\_result\.parameter\.review\_note | string | 
action\_result\.parameter\.review\_status | string | 
action\_result\.data | string | 
action\_result\.summary\.breach\_record\_reviews\_message | boolean | 
action\_result\.summary\.breach\_record\_reviews\_status\_code | string | 
action\_result\.status | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 