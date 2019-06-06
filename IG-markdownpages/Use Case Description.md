# Use Case 
In some country, there is a need to expose Laboratory Results through a FHIR interface. The receiver of this Information can be either a care provider or the patient using a patient portal. This service has to be read only and allow the receiver to view information about the laboratory result, specimen, patient, and performer they need.

## Lab Results retrieved by a care provider 
A care provider wants to be able to retrieve lab results of a certain patient over a specific period of time. Including Patient information, information about the specimen, information of the lab that performed the patient and of course all relevant reference ranges for the outcome of the result.

## Lab Results retrieved by a patient 
Patients wants to be able to see their own results of a certain type of result (e.g. blood sugar levels) over a specific period of time including the for them relevant reference ranges.

## Userstories 
Through a workshop with consumers from different regions, we have established the following user stories.

1. Find Lab Results by patient identifier
2. Find Lab Results by time period
3. Find Lab Results by type
4. Find Lab Results by status

We need to be able to extend the functionality of the interface, as new stories and needs are uncovered.