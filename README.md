# Steam Mobile Guard Activator

App for mass activation Steam Mobile Guard, written with BAS

# How it works

This app logs into your account, attaches a virtual phone number and activates mobile security. Once completed, you will receive data for generating temporary access codes to your account.

## Ditailed pipeline

1. Steam login
2. Attach phone
3. Confirmation phone attachment by link from email
   4 Activating guard with sms and totp codes
4. Parsing data (ex. tradelink; optional)
5. Exporting

# Features

## Multithreading

For example, instead of one account, 10 do the same job at the same time. You can limit the number of script runs by the number of successes or failures.

![tab.threading](./src-docs/tab.threading.png)

## Import accounts from file

CSV format, example: `username:password:email:emailpassword`

![tab.accounts](./src-docs/tab.accounts.png)

## Requests proxification

Supported protocols: http, https, socks5.
The ip change link is supported (for proxy rotation by link), a GET request will be sent. If there is no response from the server or if the server returns a status other than 200, the current execution of the script will fail with an IP address change error.

Examples:

-   `http://127.0.0.1:1235`
-   `socks://1.2.3.5:1235|https://changeip.com`
-   `https://user1:pass1@1.2.3.5:1235|changeip.com`

![tab.proxies](./src-docs/tab.proxies.png)

## Auto-confirmation email to attach a phone

The email client works via imap or pop3 protocols. It also supports proxification.
In addition, the application can check email availability before logging into the account.

![tab.email](./src-docs/tab.email.png)

## Auto-confirmation SMS to activate the guard

This works through virtual numbers.

Available services:

-   sms-activate.ru
-   smshub.org
-   5sim.net
-   onlinesim.ru
-   sms-acktiwator.ru
-   sms-reg.com
-   vak-sms.com
-   give-sms.com
-   getsms.online
-   sms-man.ru
-   activation.pw
-   cheapsms.ru
-   smsvk.net
-   365sms.ru
-   smspva.com
-   simsms.org

You can also easily add another service by emulating the API of an existing service and replacing the url in the advanced settings.

![tab.sms](./src-docs/tab.sms.png)

## Parsing account info

You can parse some account info after main process will be done. Parsing categories are now available:

-   trade link

![tab.other](./src-docs/tab.other.png)

## Export with templates

You can set the export format by yourself.

JSON "`payload`" with many useful fields is available.

Write any text on any file and place `${payload['key']}` whare you want to use data from json path.

Available paths:

-   `payload['account']`
-   `payload['account']['email']`
-   `payload['account']['email']['password']`
-   `payload['account']['email']['username']`
-   `payload['account']['hasPhone']`
-   `payload['account']['password']`
-   `payload['account']['raw']`
-   `payload['account']['username']`
-   `payload['auth']`
-   `payload['auth']['account_name']`
-   `payload['auth']['loginSecure']`
-   `payload['auth']['oauth_token']`
-   `payload['auth']['sessionid']`
-   `payload['auth']['steamid']`
-   `payload['auth']['wgtoken']`
-   `payload['auth']['wgtoken_secure']`
-   `payload['guard']`
-   `payload['guard']['account_name']`
-   `payload['guard']['deviceid']`
-   `payload['guard']['identity_secret']`
-   `payload['guard']['phone_number_hint']`
-   `payload['guard']['revocation_code']`
-   `payload['guard']['secret_1']`
-   `payload['guard']['serial_number']`
-   `payload['guard']['server_time']`
-   `payload['guard']['shared_secret']`
-   `payload['guard']['token_gid']`
-   `payload['guard']['uri']`
-   `payload['parsed']`
-   `payload['parsed']['tradelink']`
-   `payload['phone']`
-   `payload['phone']['active']`
-   `payload['phone']['convertedNumber']`
-   `payload['phone']['messageReceived']`
-   `payload['phone']['number']`
-   `payload['phone']['valid']`
-   `payload['proxy']`
-   `payload['proxy']['linkChangeIP']`
-   `payload['proxy']['raw']`
-   `payload['proxy']['type']`
-   `payload['proxy']['value']`
-   `payload['success']`

Example for [mafile](https://hashb.in/#MILgOgqgzgpgTlMBBAJgWwJYDsNQC5wCGeA9nGACIxQDWpADmDAB71l4wpIDG3iAJAG96hAJ4AbEoRQA6QrxIBXLHhmLYcLITQwAvjLSEAYhnEwAUIPMBIAERQAFoTicA+rG4u8tkAAJbQiISUrIA5orOso7Obh5eurYANDb28BiE4q5YimgARvA+/oFiktIy4ZEyGumZ2XnwCcl2LgBuJNzEGCRYrtwkKDCFAcIlIeURcLKt7Z3dvf16SSmKcBhDxcFlFZNqq40pGi3wrngYOusjm2ETUfBHcCdni0228n3KeFnag37DQaXXSpvJQqL46fZ2Ug0GA9UIYFAXf5jbayKEw1xwlAQ2zwmGnPCidwwTwwby/DYA8aVXEqDAEokkvDYuKk1wARkRoy2NyqxK87OxAxaGG4MFc8M5VypOyFIpg8OxADNFOJxISYXASKrOIUCIoYC8AMrUKBdLCFKzWOzGqCm7oASQoksphEUeAcvNtZoVSyttkNHG0ABkSHDzeTLi6FB81BotODfdbA2gQ2HjdwVj8ipGxq73TJJGniZmIXYAOowXLAEgkGgYLPZVVNJMwbSO525t0e/CtzBYxO2ADySC7ABVazCO2U8x6pF2ThOsAkbLpzLogA=).

The first line of the template always specifies where to save it.

You can export as many templates as you want.

![tab.export](./src-docs/tab.export.png)

# How to start

Download latest release and run `bas-steam-guard-mobile-activator.exe`

# Requirements

-   Windows x64 (7+)
-   1 CPU, 512 MB RAM
-   Internet speed 5MB/s +
