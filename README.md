# pgi-topics
Kafka topics for pgi (pensjonsgivende inntekt) området. Topics er på Aiven, og ikke onprem Kafka.

Utfør endringer i topics/topicnavn.yaml, og push til main branchen. 
Alle topic resursser vil bli oppdatert i både dev-gcp og prod-gcp.

_*NB!*_ Alle topics vil få \<teamnavn>.\<topicnavn> som topicnavn hos kafka brokerne. 
Så privat-pgi-hendelse vil bli renamet til pensjonopptjening.privat-pgi-hendelse

#### Manuelle endringer på topic config:
Det er sjeldent behov for dette, da topicene blir automatisk oppdatert ved push til main branchen.
Hvis det fortsatt er behov, så gjøres det slik:

1. Utfør endringer i yaml filene under `topics/` 
2. Kjør følgende kommandoer:

```
# Rull ut endringer til dev-gcp
kubectl config use-context dev-gcp
kubectl apply -f topics/dev/<topicnavn.yaml> -n pensjonopptjening

# Rull ut endringer til prod-gcp
kubectl config use-context dev-gcp
kubectl apply -f topics/prod/<topicnavn.yaml> -n pensjonopptjening
```
Det må gjøres for både dev og prod hvis du gjør det manuelt.

Du kan verifisere endringer ved hjelp av følgende kommando:

```
kubectl edit topic <topicnavn> -n pensjonopptjening
```

#### Bruksområde
Applikasjonene som bruker topicene kan du finne her:

- [pgi-les-hendelse-skatt](https://github.com/navikt/pgi-les-hendelse-skatt)
- [pgi-les-inntekt-skatt](https://github.com/navikt/pgi-les-inntekt-skatt)
- [pgi-lagre-inntekt-popp](https://github.com/navikt/pgi-lagre-inntekt-popp)


#### Kontakt
Kontakt Team Samhandling dersom du har noen spørsmål. 
Vi finnes blant annet på Slack, i kanalen [#samhandling_pensjonsområdet](https://nav-it.slack.com/archives/CQ08JC3UG)
