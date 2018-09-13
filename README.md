# netlify-redirect-bug

## 0. Deploy

Things are reinitialized on deploy so you need to deploy first.

```shell
$ HOST='https://netlify-redirect-bug.netlify.com/'
```

## 1. Accept-language: fr-FR

```shell
$ curl $HOST -H 'accept-language: fr-FR,fr'
Redirecting to /fr/
```

-> OK

## 2. No accept-language

```shell
$ curl $HOST
Redirecting to /en/
```

-> OK

## 3. (Again) Accept-language: fr-FR

```shell
$ curl $HOST -H 'accept-language: fr-FR,fr'
Redirecting to /en/
```

-> NOT OK

## 4. Accept-language: fr

```shell
$ curl $HOST -H 'accept-language: fr'
Redirecting to /fr/
```

-> OK
