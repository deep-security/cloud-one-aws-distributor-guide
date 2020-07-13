# Trend Micro Cloud One Workload Security AWS Systems Manager Distributor package implementation guide

[Cloud One Workload Security] helps to detect and protect against malware, exploitation of vulnerabilities, and unauthorized 
changes to your Windows and Linux systems as well as containers. 

[Cloud One Workload Security]: https://cloudone.trendmicro.com

[AWS Systems Manager Distributor] is a feature integrated with Systems Manager that you can use to securely store and 
distribute software packages in your accounts.

[AWS Systems Manager Distributor]: https://docs.aws.amazon.com/systems-manager/latest/userguide/distributor.html

## Overview

This guide describes the prerequisites for configuring the Cloud One Workload Security distributor 
package to scale management of Cloud One Workload Security Agents across your enterprise. This package 
enables delivery and manage of agents across Linux and Windows systems managed by SSM in EC2 and on other platforms. 
Use of the package requires a [Cloud One Workload Security Account] or a [Customer Managed Deep Security Manager] both 
of which can be delivered via subscription from the AWS Marketplace.

[Cloud One Workload Security Account]: https://aws.amazon.com/marketplace/pp/Trend-Micro-Trend-Micro-Cloud-One-Workload-Securit/B01LXMNGHB
[Customer Managed Deep Security Manager]: https://aws.amazon.com/marketplace/pp/B01AVYHVHO?qid=1594681648985&sr=0-1&ref_=srh_res_product_title

### Usage
The package retrieves necessary details to activate the agent from Systems Manager Parameter Store. The four required 
parameters and examples are listed here.

dsActivationUrl: dsm://agents.deepsecurity.trendmicro.com:443/

dsManagerUrl: https://app.deepsecurity.trendmicro.com:443

dsTenantId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

dsToken: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

The values for dsActivationUrl and dsManagerUrl should be entered as they appear here for Cloud One Workload Security. 
Give care to the trailing slash for ActivationUrl but lack thereof for ManagerUrl. To find the appropriate values for 
tenant ID and token, in the Cloud One Workload Security console, go to Support > Deployment Scripts, scroll to the end 
of the script that is generated, and copy the tenantID and token values.

#### Customer Managed Deep Security
The same four parameters are required for agents to be provisioned with Deep Security Manager. The ActivationUrl and 
ManagerUrl will be pointed to the activation and console port of the DSM respectively, while the tenantId will be empty 
and token optional for single tenant implementations which will be the majority of deployments.

 dsActivationUrl: dsm://dsm.company.com:4120/
 
 dsManagerUrl: https://dsm.company.com:443
 
 dsTenantId: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx or empty for single tenant
 
 dsToken: xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx or empty (optional) for single tenant

