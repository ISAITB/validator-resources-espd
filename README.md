# ESPD Validator  
ESPD documents validator based on UBL and ESPD specific business rules.

[![EUPL Licence](https://img.shields.io/badge/Licence-EUPL%20v1.2-blue.svg)](https://eupl.eu/1.2/en)

**Audience** 

This is a technical repository and is intended to be used as a tool that gets as input:  
- ESPD Request and ESPD Response, and 
- UBL, ESPD specific business rules, and Code Lists

and validates the ESPD XML files that are uploaded via the web interface [ISAITB testbed site](https://www.itb.ec.europa.eu/espd/upload).

## Usage

Navigate to [ISAITB testbed site](https://www.itb.ec.europa.eu/espd/upload). Select the _File_ for **File to validate**. Browse and select the ESPD file that you want to validate, it will be either an ESPD Request or na ESPD Response XML file. Select the corresponding ESPD file type and content (e.g. _Requests v3.3.0_) for **Validate as**. Click on **Validate** button.  
If the ESPD file is well formed then a **Success** mesage is displayed. In case of _error_ a list with all errors will be displayed and you can inspect each error.


The files you may edit to adapt the validation are specific to each version:
* Folder `resources\vX.X.X` contains the validation files for ESPD version X.X.X. Those files are produced and maintained in: [espd-validation-schematron](https://github.com/OP-TED/espd-validation-schematron) and [ESPD-EDM](https://github.com/OP-TED/ESPD-EDM/tree/master) repositories.
* File `resources\application-espd.properties` contains configuration that you must adapt. Please read the comments and instructions inside the file.

To create a new version entry in `resources\application-espd.properties`:  
- add 2 new entries for `validator.type`: request_X_X_x and response_X_X_X
- add the corresponding label for each entry:
  - `validator.typeLabel.request_X_X_X = Request (version X.X.X)`
  - `validator.typeLabel.response_X_X_X = Response (version X.X.X)`
- point to the corresponding resource folder for ESPD file validation:
  - `validator.schematronFile.request_X_X_X = vX.X.X/ESPDRequest`
  - `validator.schematronFile.response_X_X_X = vX.X.X/ESPDResponse`  
- point to the XSD files associated to the corresponding UBL version:
  - `validator.schemaFile.request_X_X_X = vX.X.X/xsdrt/maindoc/UBL-QualificationApplicationRequest-2.3.xsd`
  - `validator.schemaFile.response_X_X_X = vX.X.X/xsdrt/maindoc/UBL-QualificationApplicationResponse-2.3.xsd` 

To publish changes commit and push your updates. In 1-2 minutes the online service will be updated.

The online service is accessible at https://www.itb.ec.europa.eu/espd/upload and the web service API at https://www.itb.ec.europa.eu/espd/api.

## Licence

This software is shared using the [European Union Public Licence (EUPL) version 1.2](https://joinup.ec.europa.eu/collection/eupl/eupl-text-eupl-12).