<h1>Mule MUnit Roman Emperors API</h1>

## Description

## GitHub Repo Setup
- Two Environments:
    - Production
    - Development
- Variables
  
|Variable|Scope|Description|
|--------|-----|-----------|
|ENVIRONMENT|Environment|Anypoint Environment name|
|APP_ENV|Environment|Sufix for the env property to identify environement in the mule app|
|API_ID|Environment|API Manager Instance|
|REPLICAS|Environment|Number of Replicas to be deployed in Cloudhub 2.0 for the app in the specified environment|
|CORES|Environment|Quantity of cores for each replica in Cloudhub 2.0|
|TARGET|Repository|Private Space in Cloudhub 2.0|
|API_LAYER|Repository|Tag for the API led connectivity layer of the app (Experience/Process/System)|

- Secrets

|Secret|Scope|Description|
|--------|-----|-----------|
|ANYPOINT_PLATFORM_CLIENT_ID|Environment|Client ID of Anypoint Environment for API Manager |
|ANYPOINT_PLATFORM_CLIENT_SECRET|Environment|Client Secret of Anypoint Environement for API Manager|
|SECURE_KEY|Environment|Key for encryption of properties|
|MULE_ORG_ID|Repository|Anypoint Master Org ID|
|MULE_BG_ID|Repository|Anypoint Business Group ID where the app is deployed|
|MULE_CLIENT_ID|Repository|Connected APP client ID to Deploy to Cloudhub|
|MULE_CLIENT_SECRET|Repository|Connected APP client SECRET to Deploy to Cloudhub|
|NEXUS_USERNAME|Repository|Username for Mule Enterprise Nexus Repository - Needed to Run MUnit Coverage|
|NEXUS_PASSWORD|Repository|Password for Mule Enterprise Nexus Repository - Needed to Run MUnit Coverage|
