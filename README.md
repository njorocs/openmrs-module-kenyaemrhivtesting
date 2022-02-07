#HIV Testing services repository
#Description:
This is a repository for HIV Testing Services (hivtestingservices), which is an Openmrs addon module that runs within Kenyaemr.
The module provides partner notification service (PNS) features.
Partner notification is an extension of the broader HIV testing services, where the index (a HIV positive client) is required to elicit contacts, who are at risk of contracting HIV from him/her.
This helps the provider to further reach out/trace the contacts and provide them with hiv testing services.
The goal is to net those who may be exposed to the virus through the index so that they can be tested and put under treatment (if found to be HIV positive).

#Implementation:
The module is primarily implemented by 2 models:
 1. PatientContact which captures nd manipulates details about a Patient Contact. This model has relationships with Patient and Obs models in Openmrs core.
 2. ContactTrace which captures and manipulates contact trace information. The Modela has relationship with PatientContact. 

The module supports the following reports:

1. Family Testing register - A register of contacts who received HTS services and are family members of the index.
2. HTS report - Those clients who received HTS services
3. PNS register - A  register of clients who received HTS services and have a sexual relationship with the index.

It is also possible to view Index-contact taxonomy through a patient contact tree.

#Building from Source:
You will need to have Java 1.6+ and Maven 2.x+ installed. Use the command 'mvn package' to compile and package the module. The .omod file will be in the omod/target folder.

Alternatively you can add the snippet provided in the Creating Modules page to your omod/pom.xml and use the mvn command:

mvn package -P deploy-web -D deploy.path="../../openmrs-1.8.x/webapp/src/main/webapp"
It will allow you to deploy any changes to your web resources such as jsp or js files without re-installing the module. The deploy path says where OpenMRS is deployed.

#Installation:
1. Build the module to produce the .omod file.
2. Use the OpenMRS Administration -> Manage Modules screen to upload and install the .omod file

-If uploads are not allowed from the web (changeable via a runtime property), you can drop the .omod
into the ~/.OpenMRS/modules folder (where ~/.OpenMRS is assumed to be the Application 
data directory that KenyaEMR is currently using).
-Restart OpenMRS/tomcat and the module will be loaded and started.