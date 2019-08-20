Portal: Clients
---------------

**work in progress**

client:register
===============

Registers a new client User and account.

Note minimum strength/complexity requirements apply to user passwords. Guidelines:
- Choose a password that is long enough, and complex enough, to be difficult to guess. Remember, attackers use specialized software to make millions of guesses per second — it's not just one person typing guesses by hand!
- Use:
  - Long passwords! 16 characters or longer is highly recommended.
  - A password generator tool, such as LastPass
  - Several random words, preferably combined with punctuation, numbers, or other symbols
  - A long keyboard pattern
- Do Not Use:
  - A short password
  - A short password repeated several times to make it "longer"
  - The same/a similar password to one you use ANYWHERE else
  - A common phrase, movie quotes, song lyrics, your birthday, email, address, children's/pet's names, school, or anything that can be easily found on social media (e.g., your Facebook page)
  - "easy" keyboard patterns (e.g., "abcdefg...", a single row of keys like "zxcvbnm,.?", or repeats like "asdfasdfasdf")

After registering, an email will be sent to the provided email address, and the new client must verify that they own the address by providing the verification code (@see client:verify-email).
Before using the Api, the client will need to authenticate using the emaill address and password they signed up with (@see auth:login) and create an Api token (@see api-token:add).

**Endpoint**: POST /v1/register

**Access**: anyone

**Parameters**:
- string `email` (required): new user's email address (will recieve a verification email)
- string `password` (required): new user's desired password. @see auth:password-strength
- bool `agree_to_tos` (required): agreement to Terms of Service and Privacy Policies. @see terms:tos, terms:pp

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/register" \
  -H "Accept: application/json" \
  -H "Content-type: application/json"
  -d '{ "email": "new-user@example.com", "password": "correct horse battery staple", "agree_to_terms": true }'
```

**Success Response**: 201 Created
```

```

**Failure Response** (invalid email / weak password / no agreement to ToS): 422 Unprocessable Entity
