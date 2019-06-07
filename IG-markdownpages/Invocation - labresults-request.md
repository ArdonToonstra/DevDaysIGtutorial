## Request - Laboratory Results Consumer

### Trigger Events
When the Laboratory Results Consumer wants to obtain laboratory results, it issues a retrieve laboratory results request message.

### Message Semantics
The Laboratory Results Consumer executes an HTTP GET conform to the FHIR [http://hl7.org/fhir/http.html RESTfull] and [http://hl7.org/fhir/search.html search] specification against the XIS's Observation endpoint. This search query URL is configurable by the Laboratory Results Consumer and has the following format.
 
<pre>
GET [base]/Observation?[parameters]{&_format=[mime-type]}
</pre>

### Search Parameters
The Laboratory Results Consumer may supply, and the Laboratory Results Responder shall be capable of processing, all query parameters listed below. These search parameters are a selection of the defined search parameters by the HL7 FHIR specification search parameters of [http://hl7.org/fhir/STU3/observation.html#search Observation].

| Name             | Type      | Description                                                                               |
|------------------|-----------|-------------------------------------------------------------------------------------------|
| patient          | reference | The subject that the observation is about (if patient)                                    |
| date             | date      | Obtained date/time. If the obtained element is a period, a date that falls in the period. |
| code             | token     | The code of the observation type                                                          |
| method-qualifier | token     | To filter on Observation.method qualifier                                                 |

### Including other resources in search results 
The Laboratory Results Consumer may request that the Laboratory Results Responder return resources related to the search results, in order to reduce the overall network delay of repeated retrievals of related resources. This is useful when the Laboratory Results Consumer is searching on a clinical resource, but for every such resource returned, the client will also need for example the subject (Patient resource) or performer (Organization / Practitioner resource) or Specimen resource that the clinical resource refers to. The client can use the _include parameter to indicate that the subject resources be included in the results. An example is shown below.

### Example search URLs

<pre>
GET [base]/Observation
</pre>

Retrieves all Observation resources.

<pre>
GET [base]/Observation?patient=1123123&code=http://loinc.org|718-7
</pre>

Retrieves all '' Hemoglobin [Mass/volume] in Blood'' Observation resources of Patient with ID 1123123

<pre>
GET [base]/Observation?code=http://loinc.org|718-7&date=ge2010-01-01
</pre>

Retrieves all '' Hemoglobin [Mass/volume] in Blood'' Observation resources that have an effective date greater than 01-01-2010.

<pre>
GET [base]Observation?code=http://loinc.org|718-7&_include=Observation:performerdate=ge2010-01-01&date=le2011-12-31</pre>
</pre>

Retrieves all '' Hemoglobin [Mass/volume] in Blood'' Observation resources that have an effective date within a 2 year period and includes the perfomer information in the search results.

<pre>GET [base]/Observation?code=http://loinc.org|718-7&method-qualifier=http://example-Tx.org|QualifierCode01</pre>

Retrieves all '' Hemoglobin [Mass/volume] in Blood'' Observation resources that have a method-qualifier code 'QualifierCode01'.



### Expected Actions
The Laboratory Results Responder shall process the query to discover Observation resources that match the search parameters given.