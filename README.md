# RecruitisAPI
Dokumentace k API pro službu Recruitis.io vytvořená společností Český Trh Práce s.r.o.
API je napsána v Oracle Apiary, kde se nachází i mock server na jednotlivá volání.

# Odkazy
[Dokumentace v APIARY](https://jsapi.apiary.io/previews/ceskytrhpracesro/reference)


## Changelog

* **14.1.2020: branch v1 `1.4.2`**
     * U volání `GET jobs/` je možné volat parametr `status` a filtrovat s ním i draft inzeráty.
     * Přidáno volání `POST jobs/` které umí vytvořit draft inzerát. (následně je ho možné dokončit v Recruitisu)

 * **15.7.2019: branch v1 `1.4.1`**
     * U volání `GET files/` je možné volat parametr `hash` jako pole. Součet všech příloh musí být menší, než 30MB.
     * Do dokumentace byl přidán popis s meta.code `api.error.response.too_big`.
     * Do seznamu odpovědí přibyly parametry odpovědi `job_contact_name`,`job_contact_email`,`job_contact_phone`

 * **11.7.2019: branch v1 `1.4`**
     * Přibyla dokumentace na zobrazování seznamu odpovědí (`GET answers/`).
     * Přibyla dokumentace na stahování příloh (`GET files/`).

 * **8.2.2019: branch v1 `1.3.5`**
     * Do volání `GET /jobs` přibyl nový parametr `only_deleted`.

 * **3.12.2018: branch v1 `1.3.4`**
     * V dokumentaci přibyl popis stavu při nedostupnosti API. 
     * přibyly nové kódy chyb: `api.error.system.unavailable`, `api.error.request.property.wrong_text_length`,`api.error.request.property.maximum_array_items` 

  * **22.10.2018: branch v1 `1.3.3`**
      * Byla přidána nová sekce `referrals`, ve které je volání na přidání a výpis referralů. 
 
  * **16.10.2018: branch v1 `1.3.2`**
      * Do odpovědi u volání `GET /jobs` přibyl nový prvek `employment` a `education` 
 
 * **Pozor: 18.9.2018 přijde změna ve volání konkrétního inzerátu (`GET /jobs/id`): Nebude se nadále vracet pole s jedním inzerátem, ale bude vracet přímo objekt s daným inzerátem. Připravte na to prosím svoje aplikace.**

 * **17.9.2018: branch v1 `1.3.1`**
     * Bylo přidáno volání `DELETE /candidates`
     * Přibyl popis kvót
     * Přibyla kvóta `quota_candidates_delete`
 
 * **11.9.2018: branch v1 `1.3`**
     * Bylo přidáno volání `POST /candidates`
     * Do dokumentace byla přidán popis tagů
     * Validace telefonního kontaktu v requestu `POST /answers` nyní akceptuje správné české formáty.
     * Validace emailu v requestu `POST /answers` nyní akceptuje znak "+"
 
 * **6.9.2018: branch v1 `1.2.3`**
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
