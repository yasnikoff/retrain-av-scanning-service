# Malware Scanner Service

This repository contains the code to build a pipeline that scans objects
uploaded to GCS for malware.

![Architecture diagram](architecture.svg)

## Local development

To run the server locally, you need a GCloud project with setup depicted in `architecture.svg`.

### Add env variables to the `.env` file

DEAD_LETTER_TOPIC={dead letter pub/sub topic name}
PROJECT_ID={gcloud project id}
QUARANTINED_BUCKET=gs://{quarantined-bucket-name}
CVD_MIRROR_BUCKET=gs://{cvd-mirror-bucket-name}

### Set up Application Default Credentials (ADC)

Check your current project and account set in GCloud config:

```bash
gcloud config get project
gcloud config get account

```

Generate ADC file:

```bash
gcloud auth application-default login
```

For more info about ADC see [docs](https://cloud.google.com/docs/authentication/provide-credentials-adc#how-to)

Account that you use for ADC will need permissions on the project you run the server against.
The list of permissions may change as new functionality is added or removed.
Consult with the GCloud project admin.

### Run

Run `npm start` from the root dir (not from 'cloudrun-malware-scanner').

This will run node.js application without ClamAV. Full functionality requires local ClamAV deployment (TODO).

## License

Copyright 2022 Google LLC

Licensed under the Apache License, Version 2.0 (the "License"); you may not use
this file except in compliance with the License. You may obtain a copy of the
License at

```
https://www.apache.org/licenses/LICENSE-2.0
```

Unless required by applicable law or agreed to in writing, software distributed
under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR
CONDITIONS OF ANY KIND, either express or implied. See the License for the
specific language governing permissions and limitations under the License.
