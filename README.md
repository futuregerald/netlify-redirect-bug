# netlify-redirect-bug

## 0. Deploy

## 1. With my chrome browser

Go to https://netlify-redirect-bug.netlify.com/
Redirecting to /fr/

-> OK

## 2. With the `accept-language` header sent by my browser

```shell
$ curl 'https://netlify-redirect-bug.netlify.com/' -H 'accept-language: fr-FR,fr;q=0.9,en-US;q=0.8,en;q=0.7,la;q=0.6'
Redirecting to /fr/
```

-> NOT OK

## 3. With basic curl command

```shell
$ curl https://netlify-redirect-bug.netlify.com/
Redirecting to /en/
```

-> OK

## 4. (Again) With the `accept-language` header sent by my browser

```shell
$ curl 'https://netlify-redirect-bug.netlify.com/' -H 'accept-language: fr-FR,fr;q=0.9,en-US;q=0.8,en;q=0.7,la;q=0.6'
Redirecting to /en/
```

-> NOT OK

## 4. With a custom `accept-language` header: fr-FR,fr

```shell
$ curl 'https://netlify-redirect-bug.netlify.com/' -H 'accept-language: fr-FR,fr'
Redirecting to /en/
```

-> NOT OK

## 5. With a custom `accept-language` header: fr-FR

```shell
$ curl 'https://netlify-redirect-bug.netlify.com/' -H 'accept-language: fr-FR'
Redirecting to /en/
```

-> NOT OK

## 6. With a custom `accept-language` header: fr

```shell
$ curl 'https://netlify-redirect-bug.netlify.com/' -H 'accept-language: fr'
Redirecting to /en/
```

-> OK

##
