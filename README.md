# SFDMU Deployment Packages

This repository contains SFDMU configuration files for deploying static sets of objects from a lower Salesforce org to a higher org.

## Setup

1. Install dependencies:
```bash
npm install
```

2. Create a `.env` file with your Salesforce credentials:
```
SOURCE_USERNAME=your_source_org_username
SOURCE_PASSWORD=your_source_org_password
SOURCE_SECURITY_TOKEN=your_source_org_security_token
TARGET_USERNAME=your_target_org_username
TARGET_PASSWORD=your_target_org_password
TARGET_SECURITY_TOKEN=your_target_org_security_token
```

## Configuration

The `export.json` file contains the configuration for which objects to deploy. You can modify it to include different objects and fields as needed.

Each object configuration includes:
- `query`: The SOQL query to fetch the data
- `operation`: The operation to perform (Upsert, Insert, Update, etc.)
- `externalId`: The field to use as an external ID for matching records

## Running the Deployment

To run the deployment:
```bash
npm run deploy
```

## Creating New Deployment Packages

1. Copy the `export.json` file and rename it (e.g., `accounts-contacts.json`)
2. Modify the queries and configurations as needed
3. Run the specific package:
```bash
sfdmu run --sourcefile accounts-contacts.json
```

## Best Practices

1. Always test deployments in a sandbox environment first
2. Use specific queries to limit the data being deployed
3. Consider using external IDs for better record matching
4. Document any special handling or transformations needed 