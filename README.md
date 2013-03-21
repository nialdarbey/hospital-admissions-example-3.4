Hospital Admissions Example
===========================
This is an example of Webservice orchestration in Mule using simple xml only processing of messages. Routing of messages is determined
using the xpath() function to retrieve the name of the element (Document Literal Wrapped pattern). 
The webservice is exposed as a SOAP based service and orchestrates two other services used to electively admit a patient to hospital:
* the PatientService responsible for Patient Demographics administration
* the EHRService responsible for the administration of Episodes in the Electronic Health Record.

The above services have been mocked for the purpose of this example.

Proxy Service
=============
Webservices are exposed using the Proxy service operation on the SOAP Message Processor. This accepts a Soap Envelope and permits the extraction
of the contents of the body or passing the whole Envelope as is. Validation against the schema defined in the wsdl is allowed.

Proxy Client
============
The consumption of other services is realised by the Proxy client operation on the Soap Message Processor. This will automatically wrap the xml message in
a Soap Envelope suitable to send to a SOAP based web service.

Canonical Model
===============
The use of a standard business domain model is a recommended best practice in the Service Oriented Architecture. This example also standardises on the Messaging format 
for all three services: PatientService, EHRService and AdmissionService each of which exploit the commonality offered in the canonical model.

Testing
=======
This webservice can be tested using SoapUI by pointing it at the url: http://localhost:8081/AdmissionService

Further Information
===================
A more complete version of this example and the principles behind service orhestration are explained at http://blogs.mulesoft.org/soa-school-service-orchestration-2/
