# 1 - TOKEN STS
- Decode do token;
- Ver scope;
- Verificar alg `None`;

# 2 - Pollution 
- Versão `v2` → `v1`;
- Verb Tampering;  
```json
POST /api/trips/1 
POST /api/trips/1 
POST /api/trips 
DELETE /api/trips/1
```
- HTTP Parameter Pollution; 
```log
/api/profile?user_id=legit&user_id=victim
/api/profile?user_id=victim&user_id=legit
```
- JSON Parameter Pollution; 
```json
//INJETAR CAMPOS NO JSON,A FIM DE ALTERAR/SOBRESCREVER O DADO
{"dados" :"xyz", id : 2}
//INJETAR KEY/VALUE IGUAIS
{"id":111} 
{"id":[111]} 
{"id":{"id":-111}}
{"data" : 1009-10-10}
{"id":{"id":"''''''$%$%"}}
{"user_id":"legit","user_id":"victim"} {"user_id":"victim","user_id":"legit"}
{"username": "John"}
{"username": true}
{"username": null}
{"username": 1}
{"username": [true]}
{"username": ["John", true]}
{"username": {"$neq": "lalala"}}
```
- Wildcard  no ID;
```json
/api/users/1 → /api/users/* /api/users/% /api/users/_ /api/users/.
```
- Content-Type  `application/xml` ver o parse;
- XML ver XXE;

# 3 - SSRF

- Port Scan
- Endpoint de Cloud  169.254.169.254;
- Chamada Externa/Interna  http://webhook.site;


# 4 - Misc
- Refletir Token, Headers em msg de erro;
- Token na URL `/someAction?apiKey=abcd123456789`;
- Muitos dados sendo retornados;
- Rate limit=999999999999;
- Chamadas sem autenticação;
- SQLi;
- Checar IDOR/BOLA;

###



