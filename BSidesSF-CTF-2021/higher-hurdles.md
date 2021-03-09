
```
https://higher-hurdles-74a23189.challenges.bsidessf.net/
```
```
$ curl -i -XPUT https://higher-hurdles-74a23189.challenges.bsidessf.net/
HTTP/2 200
date: Tue, 09 Mar 2021 23:31:29 GMT
content-length: 69
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

You'll be rewarded with a flag if you can make it over some /hurdles.
```

```
$ curl -i -XPUT https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/
HTTP/2 401
x-hurdles-remaining: 15
date: Tue, 09 Mar 2021 23:32:05 GMT
content-length: 62
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, Your path would be more exciting if it ended in !!
```

```
$ curl -i -XPUT https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21
HTTP/2 401
x-hurdles-remaining: 14
date: Tue, 09 Mar 2021 23:33:44 GMT
content-length: 78
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, Your URL did not ask to `retrieve` the `flag` in its query string.
```

```
$ curl -i -XPUT https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag
HTTP/2 401
x-hurdles-remaining: 13
date: Tue, 09 Mar 2021 23:34:02 GMT
content-length: 53
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was looking for a parameter named &=&=&
```

```
$ curl -i -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=TEST"
HTTP/2 401
x-hurdles-remaining: 13
date: Tue, 09 Mar 2021 23:34:48 GMT
content-length: 46
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I expected '&=&=&' to equal '%00
'
```

```
$ curl -i -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 12
date: Tue, 09 Mar 2021 23:39:38 GMT
content-length: 61
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, Basically, I was expecting the username username.
```

```
$ curl -i --basic -u username -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
Enter host password for user 'username':
HTTP/2 401
x-hurdles-remaining: 12
date: Tue, 09 Mar 2021 23:40:13 GMT
content-length: 129
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, Basically, I was expecting the password to be the hex representation of the sha3-224 of the author of this challenge.
```

https://sha256calc.com/hash/sha3-224/matir
4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62
```

```
$ curl -i --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 11
date: Tue, 09 Mar 2021 23:41:15 GMT
content-length: 59
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting you to be using a 1337 Browser.
```
```

```
$ curl -i -A "1337 Browser" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 11
date: Tue, 09 Mar 2021 23:41:42 GMT
content-length: 74
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting your browser version (v.XXXX) to be over 9000!
```

```
$ curl -i -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 10
date: Tue, 09 Mar 2021 23:41:57 GMT
content-length: 66
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting this to be forwarded through 127.1.1.1
```

```
$ curl -i -H "X-Forwarded-For: 127.1.1.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 10
date: Tue, 09 Mar 2021 23:42:36 GMT
content-length: 66
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting this to be forwarded through 127.1.1.1
```

```
$ curl -i -H "X-Forwarded-For: 127.1.1.1,127.1.1.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 10
date: Tue, 09 Mar 2021 23:42:52 GMT
content-length: 65
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting this to be forwarded through 10.5.4.3
```

```
$ curl -i -H "X-Forwarded-For: 127.1.1.1,127.1.1.1,10.5.4.3" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 10
date: Tue, 09 Mar 2021 23:43:21 GMT
content-length: 66
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting this to be forwarded through 19.18.0.1
```

```
$ curl -i -H "X-Forwarded-For: 127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 10
date: Tue, 09 Mar 2021 23:43:45 GMT
content-length: 67
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting the forwarding client to be 13.37.37.13
```

```
$ curl -i -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 9
date: Tue, 09 Mar 2021 23:44:00 GMT
content-length: 44
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting a Fortune Cookie
```

```
$ curl -i -b "Fortune=TEST" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 9
date: Tue, 09 Mar 2021 23:44:38 GMT
content-length: 123
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting the cookie to contain the number of the HTTP Cookie (State Management Mechanism) RFC from 2011.
```

https://tools.ietf.org/html/rfc6265

```
$ curl -i -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 8
date: Tue, 09 Mar 2021 23:45:48 GMT
content-length: 69
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I expect you to accept only plain text media (MIME) type.
```

```
$ curl -i -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 7
date: Tue, 09 Mar 2021 23:47:42 GMT
content-length: 61
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, Ich hatte erwartet, dass Sie Deutsch akzeptieren.
```

https://translate.google.com/?sl=auto&tl=en&text=Ich%20hatte%20erwartet%2C%20dass%20Sie%20Deutsch%20akzeptieren.&op=translate

```
$ curl -i -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 6
date: Tue, 09 Mar 2021 23:49:47 GMT
content-length: 87
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting to share resources with the origin https://ctf.bsidessf.net
```

```
$ curl -i -H "Origin: https://ctf.bsidessf.net" -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 5
date: Tue, 09 Mar 2021 23:51:06 GMT
content-length: 88
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I was expecting you would be refered by: https://ctf.bsidessf.net/challenges
```

```
$ curl -i -e "https://ctf.bsidessf.net/challenges" -H "Origin: https://ctf.bsidessf.net" -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 4
date: Tue, 09 Mar 2021 23:51:45 GMT
content-length: 89
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, Surely you'd like to express your opinion on tracking on the web as a header?
```

```
$ curl -i -H "DNT: 0" -e "https://ctf.bsidessf.net/challenges" -H "Origin: https://ctf.bsidessf.net" -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 3
date: Tue, 09 Mar 2021 23:53:34 GMT
content-length: 67
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I expected fetch metadata from the same site or origin.
```

```
$ curl -i -H "Sec-Fetch-Site: same-origin" -H "DNT: 0" -e "https://ctf.bsidessf.net/challenges" -H "Origin: https://ctf.bsidessf.net" -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 2
date: Tue, 09 Mar 2021 23:54:14 GMT
content-length: 63
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I expected the mode of this fetch to be a navigate.
```

```
$ curl -i -H "Sec-Fetch-Mode: navigate" -H "Sec-Fetch-Site: same-origin" -H "DNT: 0" -e "https://ctf.bsidessf.net/challenges" -H "Origin: https://ctf.bsidessf.net" -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 401
x-hurdles-remaining: 1
date: Tue, 09 Mar 2021 23:54:34 GMT
content-length: 55
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

I'm sorry, I expected this fetch to be user activated.
```

```
$ curl -i -H "Sec-Fetch-User: ?1" -H "Sec-Fetch-Mode: navigate" -H "Sec-Fetch-Site: same-origin" -H "DNT: 0" -e "https://ctf.bsidessf.net/challenges" -H "Origin: https://ctf.bsidessf.net" -H 'Accept-Language: de' -H "Accept: text/plain"  -b "Fortune=6265" -H "X-Forwarded-For: 13.37.37.13,127.1.1.1,127.1.1.1,10.5.4.3,19.18.0.1" -A "1337 Browser v.9001" --basic -u username:4ef03423738a4aa7956528feebbc65474c053f5937032dfb9219af62 -XPUT "https://higher-hurdles-74a23189.challenges.bsidessf.net/hurdles/%21%21?retrieve=flag&%26%3D%26%3D%26=%2500%0a"
HTTP/2 200
x-ctf-flag: CTF{good_work_on_hurdling_past_2020}
date: Tue, 09 Mar 2021 23:54:51 GMT
content-length: 16
content-type: text/plain; charset=utf-8
via: 1.1 google
alt-svc: clear

Congratulations!

```

flag in HTTP header:
