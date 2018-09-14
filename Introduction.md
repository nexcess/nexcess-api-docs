# Introduction

The Nexcess API allows users, with proper authentication, to manage most aspects of their account and services directly from the API. Nexcess also provides a PHP SDK for those who do not want to script the calls manually, as well as a command line too that makes these calls for you.

This documentation is for those who wish to make the calls directly to the REST API.

Example calls in this document all use `curl`. It is assumed that the user not only has `curl` installed on their computer but understands how it is used.

Throughout this document, payloads shown in JSON format. JSON is the payload format used in all the Nexcess API calls.

# First Things First
Before you begin making calls to the API, you will need to get an API key.

# Endpoints

This document describes the different API endpoints available and how to call them.

- Creating a Cloud Account
- Get a Cloud Account details
- List Clouds
- List Packages
- List Applications