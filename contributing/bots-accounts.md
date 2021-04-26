---
description: Build dogehouse bots
---

# Bots Accounts

1. Auth with your regular account
2. Send ws message to create bot account with the username you want \(you can create up to 100\):

```text
{ op: "user:create_bot", p: { username: "mybotname" }, ref: "[uuid]", v: "0.2.0" }

// or with Kebab

wrapper.mutation.userCreateBot("username").then((response) => console.log(response));
```

1. You will receive back a message with an api key or error:

```text
{ op: "user:create_bot:reply", p: { apiKey: "asdoifjo1jioj1f1f2" }, ref: "[uuid]", v: "0.2.0" }
```

1. Save that api key somewhere safe \(I will be adding a UI for this but it doesn't exist atm\)
2. Send a POST request to `https://api.dogehouse.tv/bot/auth` with a JSON body `{ apiKey: "asdoifjoqefjo" }` and it will return an `accessToken` and `refreshToken` for that bot account.

