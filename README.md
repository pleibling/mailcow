## Passen Sie das Mailcow UI ihren wünschen an.

Standardanpassungen anpassen:
Einstellungen wie das Logo und die Beschriftungen können sie im Webinterface anpassen - loggen sie sich ein und gehen sie nach dem einloggen nach *System > Konfiuration > Einstellungen > UI Anpassungen*.

## Mailcow WebUI Favicon ändern:
Ersetzen sie die folgende Datei, durch ihre eigene Datei (z.B. ein PNG Bild): */opt/mailcow-dockerized/data/web/favicon.ico*
Führen Sie den folgenden Befehl aus:
```
docker compose restart memcached-mailcow sogo-mailcow
```
## SOGo Webmailer Favicon ändern:
Ersetzen sie die folgende Datei, durch ihre eigene Datei (z.B. ein PNG Bild): */opt/mailcow-dockerized/data/conf/sogo/custom-favicon.ico*
Führen Sie den folgenden Befehl aus:
```
docker compose restart memcached-mailcow sogo-mailcow
```
## SOGo Webmailer Logo ändern:
Erstellen Sie ein Logo als SVG Datei und kopieren sie diese nach */opt/mailcow-dockerized/conf/sogo/sogo-full.svg*
Führen Sie den folgenden Befehl aus:
```
docker compose restart memcached-mailcow sogo-mailcow
```
## SOGo Webmailer Farben ändern:
Ändern sie die Datei */opt/mailcow-dockerized/conf/sogo/custom-theme.js* mit dem folgenden Inhalt:
```
(function() {
  'use strict';
  angular.module('SOGo.Common')
    .config(configure)

  configure.$inject = ['$mdThemingProvider'];
  function configure($mdThemingProvider) {
    var greyMap = $mdThemingProvider.extendPalette('grey', {
      '200': 'F5F5F5',
      '300': 'E5E5E5',
      '1000': '4C566A'
    });
    var blueCow = $mdThemingProvider.extendPalette('red', {
      '600': 'E5E5E5'
    });
    $mdThemingProvider.definePalette('frost-grey', greyMap);
    $mdThemingProvider.definePalette('blue-cow', blueCow);
    $mdThemingProvider.theme('default')
      .primaryPalette('red', {
        'default': '400',
        'hue-1': '400',
        'hue-2': '600',
        'hue-3': 'A700'
      })
      .accentPalette('red', {
        'default': '700',
        'hue-1': '300',
        'hue-2': '300',
        'hue-3': 'A700'
      })
      .backgroundPalette('frost-grey');
    $mdThemingProvider.generateThemesOnDemand(false);
  }
})();
```
Führen Sie den folgenden Befehl aus:
```
docker compose restart memcached-mailcow sogo-mailcow
```
## SOGo Webmailer Theme ändern:
Die benötigten Dateien finden Sie oben, diese gehören in das Unterverzeichnis */opt/mailcow-dockerized* - ihr könnt diese auch wie folgt übernehmen:
```
cd /opt/mailcow-dockerized/data
git clone https://github.com/pleibling/mailcow.git
docker compose down
docker compose up -d
```
## Adminguide
Denn kompletten Adminguide in Deutsch findet ih hier: https://wiki.leibling.de/books/mailcow-adminguide
## Beispielbilder:

![image](https://github.com/pleibling/mailcow/assets/112875086/e9e15561-399d-45ea-93a0-2fc55354df70)

![image](https://github.com/pleibling/mailcow/assets/112875086/1403ef74-dfb8-48f5-bde6-f09d0d111f52)

![image](https://github.com/pleibling/mailcow/assets/112875086/3cda5b37-87d7-44ec-8bef-f7f9d186bc4f)

![image](https://github.com/pleibling/mailcow/assets/112875086/1179377d-d2df-4e7e-b69d-ebe1364ec197)

