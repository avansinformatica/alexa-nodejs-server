# alexa-nodejs-server
Dit is een server waarin Alexa skills kunnen draaien. Deze server is een standalone Git repo; de skills worden als Git submodules (aparte Git repo's) included.

Dit voorbeeld is afkomstig van [dit uitgewerkte voorbeeld](https://iwritecrappycode.wordpress.com/2016/04/01/create-an-alexa-skill-in-node-js-and-hosting-it-on-heroku/).

## Skills
Skills zijn de feitelijke apps die jouw tekst uitspreken. De server kan meerdere skills hosten.
Skills voeg je toe in de apps folder. Kijk in [de apps folder](https://github.com/avansinformatica/alexa-nodejs-server/tree/master/apps) om te zien welke skills er worden gehost. Skills kun je als aparte gescheiden repo beheren en als Git submodule aan de server toevoegen. Om dat te doen maak je een repo, je kopiëert de code uit de testskill en past deze aan. Om een submodule toe te voegen:
```
git submodule add url-van-jouw-repo apps/naam-van-jouw-submodule
git commit -am "Submodule toegevoegd"
```
De submodule blijft wel een gescheiden repo; je moet deze dus apart committen!

## Gebruik
Clone deze repo naar een directory op je eigen laptop. Vanaf de command line:
```
git clone --recursive https://github.com/avansinformatica/alexa-nodejs-server.git
```
Hiermee clone je meteen de submodules.

Om alle dependencies - ook van de submodules, zie scripts in `package.json` - op te halen type je:
```
npm install
```
Je kunt de server lokaal starten:
```
node server.js
```

## Kijken of het werkt
Test in je browser of je server werkt. Vervang test-skill eventueel voor de naam van jouw skill.
- [http://localhost:3000/alexa/test-skill](http://localhost:3000/alexa/test-skill).

## Heroku
De server en submodules zijn ook beschikbaar op Heroku. 
- [https://avans-alexa-server.herokuapp.com/alexa/test-skill](https://avans-alexa-server.herokuapp.com/alexa/test-skill)

> Om problemen te voorkomen bij het installeren van submodules moet je niet via de webbased interface deployen, maar je code direct naar je Heroku Git repo pushen. Submodules worden dan automatisch geinstalleerd, en het `postinstall` script haalt de dependencies op.
```
heroku apps --all
heroku git:remote -a yourappname
git remote -v
git push heroku
```


  
