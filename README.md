# itemszop

[![Discord](https://img.shields.io/badge/discord-%237289DA.svg?style=for-the-badge&logo=discord&logoColor=white)](https://discord.com/invite/Nx28v3yAER)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https://github.com/michaljaz/itemszop)
[![Deploy with Netlify](https://www.netlify.com/img/deploy/button.svg)](https://app.netlify.com/start/deploy?repository=https://github.com/michaljaz/itemszop)

**ItemSzop to sklep twojego serwera minecraftowego za darmo!** Działa dzięki złożeniu serverless'owych funkcji z hostowaniem statycznych plików. Nie wymaga żadnej instalacji - model SaaS. Serwis jest zrobiony we frameworku [Nuxt.js](https://nuxtjs.org/). Uwierzytelnianie użytkowników i zapisywanie konfiguracji sklepów odbywa się za pośrednictwem bazy danych [Firebase](https://firebase.google.com/). Dodatkowo użyty jest framework [Vuetify](https://vuetifyjs.com/) do ładnych stylów strony.



## Spis treści
- [Wersja produkcyjna](#wersja-produkcyjna)
- [Plugin do serwera minecraftowego](#plugin-do-serwera-minecraftowego)
- [Wspierani operatorzy płatności](#wspierani-operatorzy-płatności)
- [Konfiguracja budowania](#konfiguracja-budowania)
- [Własne hostowanie](#własne-hostowanie)
	- [Konfiguracja bazy firebase](#1-konfiguracja-bazy-firebase)
	- [Przygotowanie sklepu](#2-przygotowanie-sklepu)
- [Dodatkowe informacje](#dodatkowe-informacje)
- [Limity na darmowych hostingach](#limity-na-darmowych-hostingach)
- [Dla deweloperów](#dla-deweloperów)
- [Forum discordowe](#forum-discordowe)

## Wersja produkcyjna

Wersja produkcyjna znajduje się pod adresem: https://itemszop.tk.

Nie jest wymagane hostowanie własnego sklepu - model Software as a Service. Na tej stronie może się każdy zarejestrować i założyć swój sklep. Wówczas sklep dostanie adres https://itemszop.tk/shop/id_sklepu. Jest również możliwość przekierowania własnej domeny, lecz wtedy trzeba poprosić na forum discordowym.

## Plugin do serwera minecraftowego

Adres do repozytorium z pluginem: https://github.com/michaljaz/itemszop-plugin

Aby itemszop działał prawidłowo niezbędne jest zainstalowanie pluginu na serwerze minecraftowym. Gdy serwer jest offline komendy odkładają się na stos i wywołają się gdy będzie online.

## Wspierani operatorzy płatności

- [x] microsms.pl - [api przelew](https://microsms.pl/documents/przelewy_online.pdf), [api sms](https://microsms.pl/kernel/Mails/files/dokumentacja_techniczna_mirosms.pdf)
- [X] paypal.com - [api p24](https://developer.paypal.com/docs/checkout/apm/przelewy24/)
- [x] lvlup.pro - [api](https://api.lvlup.pro/v4/redoc)
- [ ] hotpay.pl - [api](https://hotpay.pl/dokumentacja-api/)
- [ ] cashbill.pl - [api](https://www.cashbill.pl/pobierz/api/)


## Własne hostowanie

> **_Ważne:_**  Pamiętaj, że nie potrzebujesz stawiać własnego sklepu. Możesz po prostu skorzystać z modelu SaaS.


### 1. Konfiguracja bazy firebase

- Utwórz konto serwisowe w bazie
	- Kliknij `ikonkę koła zębatego > Project Settings > Service accounts > Create service account > Generate new private key`
	- Zapisz plik `serviceAccountKey.json` na swoim komputerze
	- Zawartość pliku będzie wyglądać tak:
```json
{
	"type": "XXXXXXXXX",
	"project_id": "XXXXXXXXX",
	"private_key_id": "XXXXXXXXX",
	"private_key": "XXXXXXXXX",
	"auth_uri": "XXXXXXXXX",
	"token_uri": "XXXXXXXXX",
	"auth_provider_x509_cert_url": "XXXXXXXXX",
	"client_x509_cert_url": "XXXXXXXXX",
	"client_email": "XXXXXXXXX"
}
```

- Zapisz zawartość pliku serviceAccountKey.json w jednej linijce jako FIREBASE_CONFIG

### 2. Przygotowanie sklepu

> **_Wskazówka:_**  Cloudflare jest najlepsze do hostowania itemszopu.

#### Użycie serwisów takich jak Cloudflare, Vercel, Netlify

- Zrób forka głównego repozytorium.

- Połącz swoje repozytorium z panelem na danym serwisie.

- Podczas konfiguracji, zapisz wartość punktu 2 w zmiennej środowiskowej (Environment variable) projektu `FIREBASE_CONFIG`.

- Gotowe!

## Dodatkowe informacje
- Nowo powstały projekt działa tak samo jak strona główna Itemszopu, ale już łączy się do Twojej własnej bazy i ma swoich własnych użytkowników.

- Jeśli chcesz, żeby twój sklep był tylko hostowany w 'roocie' projektu, to wystarczy dodać zmienną środowiskową ```SINGLE_SHOP``` o wartości id sklepu.

- Istnieje również możliwość zablokowania możliwości tworzenia sklepów wszystkim użytkownikom, oprócz jednego. Wówczas trzeba zapisać zmienną środowiskową ```OWNER_ID``` o wartości id użytkownika (wziętym z bazy firebase).

## Limity na darmowych hostingach

### statyczna strona + serverlessowe funkcje

| Limit wysyłanych requestów | Cloudflare | Vercel | Netlify |
| --- | --- | --- | --- |
| Serverlessowe funkcje | 100k / dzień | 100k / dzień | 125k / miesiąc |
| Statyczna strona | bez limitu | bez limitu | bez limitu |

## Dla deweloperów

```bash
# Instalowanie bibliotek
$ npm install

############ KONFIGURACJA DEWELOPERA ############
# używając nuxta
$ npm run dev

# używając netlify
$ netlify dev

############ KONFIGURACJA PRODUKCYJNA ############
# Budowanie aplikacji
$ npm run build

# Hostowanie na porcie 8080
$ npm start

```
Aby uzyskać szczegółowe wyjaśnienie, jak to działa, sprawdź [dokumentację](https://nuxtjs.org).

## Forum discordowe

Pod tym linkiem: https://discord.com/invite/Nx28v3yAER znajduje się serwer discordowy, na którym można zadawać pytania, składać propozycje lub zgłaszać problemy techniczne.
