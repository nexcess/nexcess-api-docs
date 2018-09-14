# Check the status of a Cloud Account

Once you have issued the Create Cloud Account command above, you can query the API periodically to check it's status. In the payload above you will notice a value CLOUD_ACCOUNT_ID. This will be an integer for the cloud account that you have just created. Use this id to check the status of your cloud account.

```shell
curl -v '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOU_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

This will return you a JSON payload that resembles the one above. In this case we are looking for one important field in the payload, `STATE`.


```
  "state": "stable",
```

State can have one of five different states.

- creating
- destroying
- failure
- installing
- stable

While they are all self explanatory, in most cases, the one you are looking for is "stable". In the rare case that something went wrong in either creating your cloud account or installing the application requested, you will see the state of 'failure'. This is a fatal state that cannot be recovered from. If a cloud account fails, support will be in contact with you to discuss what went wrong.

Once your VM has reached the status of "stable", you are ready to begin working with it.