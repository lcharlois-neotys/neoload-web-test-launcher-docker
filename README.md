# Start a NeoLoad Web test using a Container

## Overview

Docker container allowing to launch a test with [NeoLoad](https://www.neotys.com/neoload/overview).
It allows you to interact with the NeoLoad [Runtime API](https://neoload-api.saas.neotys.com/explore/) to launch a load test and wait for the test result.

| Property | Value |
| ----------------    | ----------------   |
| Maturity | Experimental |
| Author | Neotys |
| License           | [BSD 2-Clause "Simplified"](https://github.com/Neotys-Labs/Worksoft-Certify/blob/master/LICENSE) |
| NeoLoad Licensing | License FREE edition, or Enterprise edition, or Professional with Integration & Advanced Usage|
| Supported versions | Tested with NeoLoad from version [6.10.0](https://www.neotys.com/support/download-neoload)
| Download Binaries | See [docker hub](https://https://hub.docker.com/r/neotys/neoload-web-test-launcher)|

##Usage

### Using a volume mapping
    docker run -d --rm \
            -v /localpath/myProject:/neoload-project
            -e NEOLOADWEB_API_URL={nlweb-onpremise-apiurl:port} \
            -e NEOLOADWEB_FILES_API_URL= {nlweb-onpremise-file-apiurl:port}\
            -e NEOLOADWEB_TOKEN={nlweb-token} \
            -e TEST_NAME={test-name} \
            -e SCENARIO_NAME={scenario-name} \
            -e CONTROLLER_ZONE_ID={controller-zone} \
            -e LG_ZONE_IDS={lg-zones:lg-number} \
            neotys/neoload-web-test-launcher
            
### Using project URL
    docker run -d --rm \
            -e NEOLOAD_PROJECT_URL={url-to-project-zip}
            -e NEOLOADWEB_API_URL={nlweb-onpremise-apiurl:port} \
            -e NEOLOADWEB_FILES_API_URL= {nlweb-onpremise-file-apiurl:port}\
            -e NEOLOADWEB_TOKEN={nlweb-token} \
            -e TEST_NAME={test-name} \
            -e SCENARIO_NAME={scenario-name} \
            -e CONTROLLER_ZONE_ID={controller-zone} \
            -e LG_ZONE_IDS={lg-zones:lg-number} \
            neotys/neoload-web-test-launcher

### Parameters
| Env | Comment | Example |
| ------------------------ | --------------------------------------------- | ---------------- |
| NEOLOAD_PROJECT_URL (Optional) | A zipped version of he NeoLoad project to launch. Optional, a volume containing the project can also be mapped. | https://github.com/me/myProject/raw/master/neoload-project/Archive/smokeTest.zip
| NEOLOADWEB_API_URL (Optional) |  The NeoLoad Web API URL. Optional, is only required for NeoLoad Web OnPremise deployment. If not present, the Controller will use NeoLoad Web SAAS. | https://neoload.mycompany.com:8080 |
| NEOLOADWEB_FILES_API_URL (Optional) |  The NeoLoad Web Files API URL. Optional, is only required for NeoLoad Web OnPremise deployment. If not present, the Controller will use NeoLoad Web SAAS. | https://neoload.mycompany.com:8080 |
| NEOLOADWEB_TOKEN | The NeoLoad Web API token. | 9be32780c6ec86d92jk0d1d25c |
| NEOLOADWEB_PROXY (Optional) | The proxy URL to access NeoLoad Web | http://login:password@myproxy |
| TEST_NAME | The name of the test result. | MyProject non regression test |
| SCENARIO_NAME (Optional) | The scenario name to launch as it appear in the NeoLoad project. This parameter is optional if only one scenario exist in the project. | MyLargeScenario |
| CONTROLLER_ZONE_ID | The controller zone Id. | ZoneId |
| LG_ZONE_IDS | The LG zones with the number of the LGs. | ZoneId1:10,ZoneId2:5 |

## ChangeLog
* Version 1.0.0 (September, 2019): Initial release.