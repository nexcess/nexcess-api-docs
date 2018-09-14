# Introduction

The Nexcess API allows users, with proper authentication, to manage most aspects of their account and services directly from the API. Nexcess also provides a PHP SDK for those who do not want to script the calls manually, as well as a command line too that makes these calls for you.

This documentation is for those who wish to make the calls directly to the REST API.

Example calls in this document all use `curl`. It is assumed that the user not only has `curl` installed on their computer but understands how it is used.

Throughout this document, payloads shown in JSON format. JSON is the payload format used in all the Nexcess API calls.

In almost all situations, you will need to specify via a header that your application is expecting a JSON payload.

```
  -H 'Accept: application/json'
```

# First Things First
Before you begin making calls to the API, you will need to get an API key.

# Endpoints

This document describes the different API endpoints available and how to call them.

- [Cloud Account](CloudAccount.md)
- [Check the state of a cloud account](CheckStateOfCloudAccount.md)
- [List Clouds](ListClouds.md)
- List Packages
- List Applications