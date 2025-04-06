# Definition of URIs

Project resources that are not imported from external repositories are identified by project URIs.

They will be in the form:
```
<https://github.com/Sciences-historiques-numeriques/astronomers/resource/39395bddd7475cffd92e00efcd4905b5>
```
and are produced using this method:
```
URI(CONCAT('https://github.com/Sciences-historiques-numeriques/astronomers/resource/',MD5(str(now())))) as ?pUri)
```

If suitable mechanismes are provided, they could be dereferenced to corresponding pages.




### Some tests on Allegrograph below

```
select (now() as ?now) (encode_for_uri(BNODE()) as ?bnode) 
(URI(CONCAT('https://github.com/Sciences-historiques-numeriques/astronomers/resource/',
STR(?bnode))) as ?bNodeUri)
(URI(CONCAT('https://github.com/Sciences-historiques-numeriques/astronomers/resource/',MD5(str(now())))) as ?pUri) (uuid() as ?person)
where {}
```


