# vCenter Server deployment

## Automated deployment of the vCenter Server Appliance deployment
Use the CLI installer to install, upgrade or migrate the vCenter Server.
In this example we use the CLI installer for installing a new VCSA using a Windows Operating system. The CLI installer use a JSON file for the VCSA install.

# Windows environment PRE check
The CLI installer for Windows requires a Microsoft Visual C++ Redistributable version 14.0. This can be checked with the following command:

      \vcsa-cli-installer\win32\check_windows_vc_redist.bat


#### CLI installer

The first step is to mount the VCSA 6.7 ISO and navigate to:

         \vcsa-cli-installer\win32\vcsa-deploy.exe


#### Help

For more information about the syntax and parameters help can used:

         vcsa-deploy.exe install --help
         vcsa-deploy install --template-help

#### JSON templates

JSON Templates can be found:

        \vcsa-cli-installer\templates\install

The following templates are available:

                embedded_vCSA_on_*.json: Platform Services Controller (PSC) and vCSA
                                         together on one system
                PSC_on_*.json:           Only a PSC
                vCSA_on_*.json:          Only a vCSA
                *_on_ESXi.json:          Install onto the ESXi host specified in the JSON
                                         file
                *_on_VC.json:            Install onto a host managed by the vCenter
                                         instance specified in the JSON file

Use one of these JSON templates as starting point. Or use the embedded_VCSA_on_ESXi.json example. I used this example in my lab environment for a embedded VCSA deployment with the PSC and VCSA together.

#### Deployment
**Note:** *Before deploying make sure a DNS record for the VCSA FQDN is defined.*

Perform a template verification without installing:

         vcsa-deploy install --accept-eula --verify-template-only <JSON file path>

Deploy a VCSA using a template:

         vcsa-deploy.exe install --accept-eula --acknowledge-ceip --terse --no-ssl-certificate-verification <JSON file path>


**Options:**

Information about deployment sizes:

         vcsa-deploy.exe --supported-deployment-sizes


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
