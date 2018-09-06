# RecruitisAPI
Dokumentace k API pro službu Recruitis.io vytvořená společností Český Trh Práce s.r.o.
API je napsána v Oracle Apiary, kde se nachází i mock server na jednotlivá volání.

# Odkazy
[Dokumentace v APIARY](https://jsapi.apiary.io/previews/ceskytrhpracesro/reference)

## Changelog

 * **6.9.2018: branch v1 `1.2.3`**
     * **Pozor: 11.9.2018 přijde změna ve volání konrétního inzerátu (`GET /jobs/id`): Nebude nadále vracet pole s jedním inzerátem, ale bude vracet přímo objekt s daným inzerátem. Připravte na to prosím svoje aplikace.**
     * Do volání `GET /jobs` přibyl parametr `include_inactive`
     * Volání u neexistujícího inzerátu (`GET /jobs/id`) končí s http_statusem `404` na místo prázdné `200` odpovědi
     * Aktualizace dokumentace o některé důležité informace (popis jednotlivých atributů u inzerátu).

 * **5.9.2018: branch v1 `1.2.2`**
     * Do odpovědi u volání `POST /Answers` Přibyl parametr `source`.
     * Do odpovědi u volání `GET /jobs` přibyl parametr `details`
     * Server nyní vrací přesnější informace u volání `GET /jobs`, dle specifikace dokumentace
     * Aktualizace dokumentace o některé důležité informace.

 * **28.8.2018: branch v1 `1.2.1`**
    * Do odpovědi u volání `POST /Answers` přibyly nové možnosti (přidání odkazů na sociální sítě uchazeče)
    * Do odpovědi volání `POST /Answers` přibyl parametr `date_created` v objektu `gdpr_agreement`
 
 * **6.8.2018: branch v1 `1.2`**
    * Přidána sekce **Filters**
    * Zprovozněn parametr filter_id u volání `GET /jobs`
    * U volání `POST /answer`  přibyl parametr `referral_id`, `channel_id` a `extra`, který dovoluje přidat k odpovědi poznámku nebo tag.
    * U volání `POST /answer`  byl zprovozněn parametr `channel_id` 
    * U volání `POST /answer`  byl upraven parametr `gppr_agreements` - Nyní je rozšířen o další atributy 
    * Volání `GET /enums/filters` je označeno jako deprecated. Namísto toho se doporučuje volat `GET /filters`
 
 * **19.7.2018: branch v1 `1.1.1`**
    * Zprovozněn parametr channel_id u volání `GET /jobs`
    * Do odpovědi `GET /jobs` přibyly tyto položky: `description` a `workfields`
    * Opraven parametr channel_assignation u volání `GET /enums/workfields`
    * Přidáno vynucení správných typů tokenů u volání `GET /enums/workfields` a `GET /jobs`
    * Standartizovány některé kódové označení chyb + jsou zveřejněny a popsány v dokumentaci
    * V dokumentaci jsou připsány další dodatečné informace o API
 
 * **9.7.2018: branch v1 `1.1`**
    * Zprovozněno volání nad realnými daty na url adrese: `https://app.recrutis.io/api2/`
    * `GET /jobs` odstraněn parametr `regions`. Na místo něho se bude využívat parametr `office_id`. Filtrace podle lokality není v nejblížším plánu vývoje.
    * `GET /jobs` parametr `workfields` přejmenován na `workfield_id` (zpětná kompatibilita je zachována.)
    * `GET /jobs` přidán parametr `office_id`
    * Přidáno volání `GET /enums/offices`
    * volání `GET /enum/*` přejmenováno na `GET /enums/*`. (zpětná kompatibilita je zachována: stále se dá volat `enums`)
    * Plánuje se v nejbližší době: zprovozněno volání na `https://api.recrutis.io/` (volání na https://app.recrutis.io/api2/ bude zachováno)

 * **18.6.2018: branch v1 `1.0.1`**
    * `POST /Answers` nyní přijíma parametr `attachment` `base64`. V této návaznosti je nyní povinný atribut `attachment` `filename`.

 * **4.5.2018: branch v1 `1.0.0`**
    * Ustálená verze API volání `jobs` , `answers` a `login`
    * Počáteční verze
