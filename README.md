# Dr. Max Assignment - hubmatyas@gmail.com

- [LIVE BUILD HERE](https://hubma-drmax-assignment.web.app) hosted on firebase
- **Time to finish**: 2.5 hrs

## Spuštění

```sh
yarn install
```

```sh
yarn dev
```

## Popis projektu

Výpis top 100 článků z hacker news api. Napsáno ve Vue.js SPA, s pomocí axiosu, naservírováno na firebase přes CLI tool.

## Co bych vylepšil

Úkol byl snadný, každopádně je tu (jako u jakéhokoliv projektu) spousta věcí na vylepšení.

- použil bych dotenv na api endpoint
- caching - porovnání článků dle data, kdyžtak purge 💣
- záleží na endpointu a na množství, pokud bych měl v plánu načítat víc, tak bych to dělal postupně dle scrollu, nebo dle stránkování
- styling - vždy to může být hezčí 🤠
- semantic html
- použít nuxt pro ssr - články se každý den myslím mění, ale je fajn když prohlížeč ví cokoli navíc dopředu, jako je například markup okolo - lépe se stránka renderuje
- lepší layout, takhle to působí trochu chaoticky
- srozumitelně zobrazit datum - dd:mm:yyyy, hh:mm (24hod)
- přidat možnost zobrazit podle datumu
- více mě teď nenapadá, vás ale určitě ano, tak mi to můžete potom povědět :-)
