# Introduction

The Nexcess API allows users, with proper authentication, to manage most aspects of their account and services directly from the API. Nexcess also provides a [PHP SDK](https://github.com/nexcess/nexcess-php-sdk) for those who do not want to script the calls manually, as well as a [command line tool](https://github.com/nexcess/nexcess-cli) that makes these calls for you.

This documentation is for those who wish to make the calls directly to the REST API.

Example calls in this document all use `curl`. It is assumed that the user not only has `curl` installed on their computer but understands how it is used.

# First Things First

Before you begin making calls to the API, you will need to get an API key. You also need to review the possible types of errors we return.

- [Authorization](Authorization.md)
- [Errors](Errors.md)

# Conventions

## JSON

Throughout this documentation, payloads shown in JSON format. JSON is the payload format used in all the Nexcess API calls. In almost all situations, you will need to specify via a header that your application is expecting a JSON payload.

__Example Header__
```
  -H 'Accept: application/json'
```

## \_\_URL\_\_

In all examples, the base URL has been replaced with \_\_URL\_\_.

- If you are a Nexcess.net customer, the URL is https://portal.nexcess.net
- If you are a Thermo.io customer, the URL is https://core.thermo.io


## API Key

In all the examples given in this documentation **YOUR_VERY_LONG_API_KEY_GOES_HERE** is place of your API key. Once you get your API key, you can replace these with your actual API key.


# Endpoints

This document describes the different API endpoints available and how to call them.

- [Cloud Account](CloudAccount.md)
- [Packages](Packages.md)
- [Applications](Applications.md)
- [Clouds](Clouds.md)
