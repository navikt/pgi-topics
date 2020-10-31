# pgi-topics
Kafka topics for pgi (pensjonsgivende inntekt) området

#### Endringer på topic config for aiven:
1. Utfør endringer i yaml filene under `topics/` 
2. Kjør følgende kommandoer:

```
# Rull ut endringer til dev-gcp
kubectl config use-context dev-gcp
kubectl apply -f topics/<topicnavn.yaml> -n pensjonsamhandling

# Rull ut endringer til prod-gcp
kubectl config use-context dev-gcp
kubectl apply -f topics/<topicnavn.yaml> -n pensjonsamhandling
```
Det må gjøres for både dev og prod.

Du kan verifisere endringer ved hjelp av følgende kommando:

```
kubectl get topics -n pensjonsamhandling
```

#### Endringer på topic config for onprem kafka:
Json filene som starter med "onprem-" kan copy pastes inn i 
[kafka-adminrest](https://kafka-adminrest.nais.preprod.local/api/v1/apidocs/index.html?url=swagger.json) sitt oneshot endepunkt for endring/oppretting.

Servicebrukere for autentisering (brukes kun av onprem kafka):
- srvpgileshendelse
- srvpgilesinntekt
- srvpgilagreinntekt

Det er meningen å migrere bort fra dette, og kun bruke aiven kafka.

#### Bruksområde
Applikasjonene som bruker topicene kan du finne her:

- [pgi-les-hendelse-skatt](https://github.com/navikt/pgi-les-hendelse-skatt)
- [pgi-les-inntekt-skatt](https://github.com/navikt/pgi-les-inntekt-skatt)
- [pgi-lagre-inntekt-popp](https://github.com/navikt/pgi-lagre-inntekt-popp)

#### Kontakt
Kontakt Team Samhandling dersom du har noen spørsmål. 
Vi finnes blant annet på Slack, i kanalen [#samhandling_pensjonsområdet](https://nav-it.slack.com/archives/CQ08JC3UG)
