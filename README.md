# netlify-redirect-bug

## netlify.toml

```toml
[[redirects]]
  from = "/"
  to = "/fr/"
  status = 302
  force = false
  conditions = { Language = ["fr"] }

[[redirects]]
  from = "/"
  to = "/en/"
  status = 302
  force = false
```

## 0. Deploy

Things are reinitialized on deploy so you need to deploy first.

```shell
$ HOST='https://netlify-redirect-bug.netlify.com/'
```

## 1. accept-language: fr-FR,fr

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

## 3. (Again) A-accept-language: fr-FR,fr

```shell
$ curl $HOST -H 'accept-language: fr-FR,fr'
Redirecting to /en/
```

-> NOT OK

## 4. accept-language: fr

```shell
$ curl $HOST -H 'accept-language: fr'
Redirecting to /fr/
```

-> OK

## 5. (Again) A-accept-language: fr-FR,fr

```shell
$ curl $HOST -H 'accept-language: fr-FR,fr'
Redirecting to /en/
```

-> (STILL) NOT OK
