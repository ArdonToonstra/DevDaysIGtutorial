## Introduction

In some country, there is a need to expose laboratory results through a FHIR interface. This service has to be read only and allow the receiver to view information about the laboratory result, patient, and performer they need.

A care provider wants to be able to retrieve lab results of a certain patient over a specific period of time. Including Patient information, information of the lab that performed the patient and of course all relevant reference ranges for the outcome of the result.

Through a workshop with consumers from different regions, we have established the following user stories.

1. Find Lab Results by patient identifier
2. Find Lab Results by time period
3. Find Lab Results by type of lab observation
4. Find Lab Results by method qualifier

We need to be able to extend the functionality of the interface, as new stories and needs are uncovered.

## Actors

| Transaction group                 | Transaction                          | Actor                       | Role                                    |
|-----------------------------------|--------------------------------------|-----------------------------|-----------------------------------------|
| Retrieve Laboratory Results(PULL) | Retrieve laboratory results request  | Laboratory Results Consumer | Request laboratory results from the XIS |
|                                   | Retrieve laboratory results response | Laboratory Results Responder   | Serves laboratory results to the PHR    |