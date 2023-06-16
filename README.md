<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

# xxAI.art

A webhely kódjának egy része nyílt forráskódú, szívesen segítünk a fordítás optimalizálásában.

## front-end kód

* [front-end kód](https://github.com/xxai-art/web)
* [Nyelvi csomagok a webhely egészéhez](https://github.com/xxai-art/web/tree/main/i18n)
* [Nyelvi csomagok a bejelentkezési modulokhoz](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Weboldal többnyelvű dokumentációja](https://github.com/xxai-doc)

A front-end programozási nyelv a [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , amely a coffeescript szintaxisa alapján ad hozzá néhány szolgáltatást, lásd [a ./coffee_plus.md fájlt](./coffee_plus.md) .

## Weboldalak és dokumentumok nemzetközivé tétele

Építsen a következő 3 projektre

### [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

Az `.mdt` utótaggal rendelkező leírósablon `<+ ./coffee_plus/import.js>` hasonló szintaxisú külső fájlokra hivatkozhat.

[@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

A Markdown fordítás nem fordítja le a kódokat és a hivatkozásokat, és a lefordított mondatokat gyorsítótárba helyezi. Ha a fordítást módosítják, de az eredeti szöveget nem módosítják, az újbóli végrehajtás nem írja felül a fordítás módosítását.

[@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

Nyelvi fájlok `yaml` által generált webhelyek fordításához.
