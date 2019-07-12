# Authorization

Before you can start using the Nexcess API, you will need to get an API token. The pre-requisite for getting an API token is having a Nexcess Account.

Once you have an account, log in. On the upper right hand side of the screen is a drop down that lists all the things you can do at the account level. (SSH keys, payments, API tokens, etc.) Select API Tokens from that menu.

If this is your first API token then the list will be empty. Otherwise, it will show you a list of the tokens you have already created. On the right of each token description is a hamburger menu that gives you the option to edit the token's description or delete the token completely. NOTE: The token is only displayed to you once. You must copy it and store it at that point as there is no way to ever see it again. If you lose your API token, it is easy to revoke that one (delete) and create a new one.

To generate a new API token, click the "Generate New API Token" button. This will ask you for a description for your new token. Be descriptive enough to remind yourself what this token is used for so that you don't accidentally delete an important token at a later date.

Once you are satisfied with the description, click the "Generate" button to generate the actual token.

The next screen will show you the token. You can click the token to copy it to your computers copy buffer, or select it and use your OS's copy feature. This is the one and only time you will be able to see this token. There is no way to see it again, nor can support help you recover it. If you lose it, your only option is to generate a new one. Store this token somewhere safe until you are ready to use it.

Once you have your token safely stored, click the "Close" button.

Congratulations, you are done, you now have a Nexcess API token. Throughout all our examples, you replace YOUR_VERY_LONG_API_KEY_GOES_HERE with the token you just generated so that it will be passed in to the call.