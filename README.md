<p align="center"><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/logo.svg"/></a><br/><a href="https://xxai.art"><img src="https://cdn.jsdelivr.net/gh/xxai-art/doc/xxai.svg"/></a></p><p align="center"><a href="https://github.com/xxai-art/doc#readme"><img alt="I18N" src="https://cdn.jsdelivr.net/gh/wactax/img/t.svg"/></a>　<a href="https://groups.google.com/u/0/g/xxai-art"><img alt="Google Groups" src="https://cdn.jsdelivr.net/gh/wactax/img/g-groups.svg"/></a></p>

Javasoljuk, hogy először telepítse a nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , majd `direnv allow` a könyvtárba való belépés után ( [az .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) automatikusan lefut a könyvtárba való belépés után).

Jelentése: kínai fordítás japánra, koreaira, angolra, angol fordítás az összes többi nyelvre. Ha csak a kínait és az angolt szeretnéd támogatni, írd be `zh: en` .

## front-end kód

* [front-end kód](https://github.com/xxai-art/web)
* [Nyelvi csomagok a webhely egészéhez](https://github.com/xxai-art/web/tree/main/i18n)
* [Nyelvi csomagok a bejelentkezési modulokhoz](https://github.com/wacpkg/user/tree/main/ui.i18n)
* [Weboldal többnyelvű dokumentációja](https://github.com/xxai-doc)

A front-end programozási nyelv a [@w5/coffee_plus](http://npmjs.com/@w5/coffee_plus) , amely a coffeescript szintaxisa alapján ad hozzá néhány szolgáltatást, lásd [: ./coffee_plus.md](./coffee_plus.md) .

## Weboldalak és dokumentumok nemzetközivé tétele

Építsen a következő 3 projektre

* [@w5/mdt](https://www.npmjs.com/package/@w5/mdt)

  Az utótag `.mdt` , a `<+ ./coffee_plus/import.js>` hasonló szintaxist használhatja külső fájlok hivatkozására, és leértékelést generálhat az `.md` utótaggal.

* [@w5/trmd](https://www.npmjs.com/package/@w5/trmd)

  A Markdown fordítás nem fordítja le a kódokat és a hivatkozásokat, és a lefordított mondatokat gyorsítótárba helyezi. Ha a fordítást módosítják, de az eredeti szöveget nem módosítják, az újbóli végrehajtás nem írja felül a fordítás módosítását.

* [@w5/i18n](https://www.npmjs.com/package/@w5/i18n)

  Nyelvi fájlok `yaml` által generált webhelyek fordításához.

### Dokumentumfordítási automatizálási utasítások

Lásd [az xxai-art/doc](https://github.com/xxai-art/doc) kódtárat

Javasoljuk, hogy először telepítse a nodejs, [direnv](https://direnv.net) , [bun](https://github.com/oven-sh/bun) , majd `direnv allow` a könyvtárba való belépés után ( [az .envrc](https://github.com/xxai-art/doc/blob/main/.envrc) automatikusan lefut a könyvtárba való belépés után).

A több száz nyelvre lefordított nagy kódbázis elkerülése érdekében minden nyelvhez külön kódbázist készítettem, és létrehoztam egy szervezetet a kódbázis tárolására.

A `GITHUB_ACCESS_TOKEN` környezeti változó beállítása, majd [a create.github.coffee](https://github.com/xxai-art/doc/blob/main/create.github.coffee) futtatása automatikusan létrehozza a kódtárat.

Természetesen kódbázisba is beteheted.

Fordítási szkript hivatkozás [run.sh](https://github.com/xxai-art/doc/blob/main/run.sh)

A script kód értelmezése a következő:

[A bunx](https://bun.sh/docs/cli/bunx) az npx helyettesítője, ami gyorsabb. Természetesen, ha nincs telepítve bun, használhatod helyette `npx` .

`bunx mdt zh` `.md` `.mdt` a zh könyvtárban, lásd a 2 linkelt fájlt alább

* [coffee_plus.mdt](https://github.com/xxai-doc/zh/blob/main/coffee_plus.mdt)
* [coffee_plus.md](https://github.com/xxai-doc/zh/blob/main/coffee_plus.md)

`bunx i18n` a fordítás alapkódja (ha csak `nodejs` van telepítve, de `bun` és `direnv` nincs telepítve, akkor `npx i18n` is futtathatja a fordításhoz).

Ez elemzi [az i18n.yml fájlt](https://github.com/xxai-art/doc/blob/main/i18n.yml) , az `i18n.yml` konfigurációja ebben a dokumentumban a következő:

```
en:
zh: ja ko en
```

Jelentése: kínai fordítás japánra, koreaira, angolra, angol fordítás az összes többi nyelvre. Ha csak a kínait és az angolt szeretnéd támogatni, írd be `zh: en` .

Az utolsó [a gen.README.coffee](https://github.com/xxai-art/doc/blob/main/gen.README.coffee) , amely kivonja a tartalmat az egyes nyelvek `README.md` fájljának főcíme és első alcíme között, és létrehoz egy `README.md` bejegyzést. A kód nagyon egyszerű, meg tudod nézni magad.

A Google API-t ingyenes fordításhoz használják. Ha nem tud hozzáférni a Google-hoz, konfiguráljon és állítson be egy proxyt, például:

```
export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890
```

A fordítási szkript lefordított gyorsítótárat hoz létre `.i18n` könyvtárban. Kérjük, ellenőrizze `git status` , és adja hozzá a kódtárhoz az ismételt fordítások elkerülése érdekében.

Kérjük, futtassa `bunx i18n` minden alkalommal, amikor módosítja a fordítást a gyorsítótár frissítéséhez.

Ha az eredeti szöveget és a fordítást egyszerre módosítjuk, a gyorsítótár összezavarodik, így ha módosítani szeretnénk, csak egyet módosíthatunk, majd futtassuk `bunx i18n` a gyorsítótár frissítéséhez.
