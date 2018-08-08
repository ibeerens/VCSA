# VCSA
Automated deployment of the vCenter Server Appliance deployment

Mount the VCSA 6.7 ISO and navigate to:
win32/vcsa-deploy.exe

Getting help:
Help            |   vcsa-deploy.exe install --help
Template help   |   vcsa-deploy install --template-help

Templates can be found:

templates/
         install/
                Use these templates to install a vCSA/PSC instance.

                embedded_vCSA_on_*.json: Platform Services Controller (PSC) and vCSA
                                         together on one system
                PSC_on_*.json:           Only a PSC
                vCSA_on_*.json:          Only a vCSA
                *_on_ESXi.json:          Install onto the ESXi host specified in the JSON
                                         file
                *_on_VC.json:            Install onto a host managed by the vCenter
                                         instance specified in the JSON file


Deployment

Perform a template verification without installing:
vcsa-deploy install --accept-eula --verify-template-only <JSON file path>

Deploy a VCSA using a template:
vcsa-deploy.exe install --accept-eula --acknowledge-ceip --terse --no-ssl-certificate-verification <JSON file path>


Options:

Information about deployment sizes:
vcsa-cli-installer\win32>vcsa-deploy.exe --supported-deployment-sizes


|Options                     |vCPUs |Memory(GB)|Storage(GB)| Hosts(up to)|VMs(up to)|
|----------------------------|------|----------|-----------|-------------|-----------|
|tiny                        |   2  |   10     |    300     |    10       | 100 |
|tiny-lstorage               |   2  |   10     |    825     |    10       | 100    |
|tiny-xlstorage              |   2  |   10     |    1700    |    10       | 100    |
|small                       |   4  |   16     |    340     |    100      |    1000   |
|small-lstorage              |   4  |   16     |    870     |    100      |    1000   |
|small-xlstorage             |   4  |   16     |    1750    |    100      |    1000   |
|medium                      |   8  |   24     |    525     |    400      |    4000   |
|medium-lstorage             |   8  |   24     |    1025    |    400      |    4000   |
|medium-xlstorage            |   8  |   24     |    1905    |    400      |    4000   |
|large                       |   16 |   32     |    740     |    1000     |    10000  |
|large-lstorage              |   16 |   32     |    1090    |    1000     |    10000  |
|large-xlstorage             |   16 |   32     |    1970    |    1000     |    10000  |
|xlarge                      |   24 |   48     |    1180    |    2000     |    35000  |
|xlarge-lstorage             |   24 |   48     |    1230    |    2000     |    35000  |
|xlarge-xlstorage            |   24 |   48     |    2110    |    2000     |    35000  |
|management-tiny             |   2  |   10     |    300     |    10       |    100    |
|management-tiny-lstorage    |   2  |   10     |    825     |    10       |    100    |
|management-tiny-xlstorage   |   2  |   10     |    1700    |    10       |    100    |
|management-small            |   4  |   16     |    340     |    100      |    1000   |
|management-small-lstorage   |   4  |   16     |    870     |    100      |    1000   |
|management-small-xlstorage  |  4   |   16     |    1750    |    100      |    1000   |
|management-medium           | 8    |   24     |    525     |    400      |    4000   |
|management-medium-lstorage  |  8   |   24     |    1025    |    400      |    4000   |
|management-medium-xlstorage | 8    |   24     |    1905    |    400      |    4000   |
|management-large            |16    |   32     |    740     |    1000     |    10000  |
|management-large-lstorage   |16    |   32     |    1090    |    1000     |    10000  |
|management-large-xlstorage  |16    |   32     |    1970    |    1000     |    10000  |
|management-xlarge           |24    |   48     |    1180    |    2000     |    35000  |
|management-xlarge-lstorage  |24    |   48     |    1230    |    2000     |    35000  |
|management-xlarge-xlstorage |24    |   48     |    2110    |    2000     |    35000  |
|infrastructure              |2     |   4      |    60      |    None     |    None   |
