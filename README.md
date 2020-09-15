# RecruitisAPI
Dokumentace k API pro službu Recruitis.io vytvořená společností Český Trh Práce s.r.o.
API je napsána v Oracle Apiary, kde se nachází i mock server na jednotlivá volání.

# Odkazy
[Dokumentace v APIARY](https://jsapi.apiary.io/previews/ceskytrhpracesro/reference)


## Changelog

* **15.9.2020: branch v1 `1.7.1`**
    * U výsledku volání `GET jobs/` je nyní lepé popsán atribut `active`, viz přehled parametrů https://ceskytrhpracesro.docs.apiary.io/#reference/jobs/job-lists/get-all-jobs .

* **5.9.2020: branch v1 `1.7.0`**
    * U výsledku volání `GET jobs/` byly přidány tyto atributy: `date_stopped`,`access_state`,`stop_duration`,`activity_state`.
    * U volání `GET jobs/` byly přidány tyto request parametry: `activity_state`,`access_state`
        * `activity_state` Je synonymum pro nynější parametr `status` obsahující aktivní a neaktivní inzeráty. Smazané inzráty jsou nyni označené jako archivované a přesunuty pod parametr `access_state` s hodnotou 3.
        * `access_state` Je request parametr filtrující otevřené, uzavřené, archivované pozice, drafty a šablony. 
        * Podrobnější popis naleznete v přehledu parametrů https://ceskytrhpracesro.docs.apiary.io/#reference/jobs/job-lists/get-all-jobs .
     
     * U volání `GET jobs/` jsou tyto parametry označeny jako obsolete a v budoucnu dojde k jejim vymazání: 
        * `source_site`: Prvek byl zavádějící.
        * `date_end`: Bude nahrazen argumentem `date_stopped`. Důvodem je přesnější pojmenování parametru, které značí datum uzavření pozice.
        * `only_deleted`: Vrátit smazané (resp. archivované pozice) bude možné přes parametr `access_state` s hodnotou 3.
        * `include_inactive`: Neaktivní pozice (tj. pozice, které nejsou aktivní na žádném pulikačním kanálu)  se dají vrátit přes parametr `activity_state` s hodnotou 2, popř. 3 (bitmapa).
        * `status` s hodnotou 4 (drafty) se nyní má volat přes parametr `access_state` s hodnotou 4.
        * `status` s hodnotou 8 (smazané) se nyní má volat přes parametr `access_state` s hodnotou 3.
        
     * **Toerie:** Jedná se o zjednodušení filtračních možností pozic se zachováním všech možných stávajících variant. Zároveň bylo potřeba zakomponovat novou logiku otevřených a uzavřených pozic.
     
    * U volání `POST answers/` nelze přidat odpověď v případě, že směruje na archivovanou pozici. Tento požadavek vrací `code` `api.error.job.wrong_acess_type`.
    * Přidán chybový kód `api.error.job.disallowed_acess_type`.
    * Přidáno API volání `PUT jobs/(id)/access_state/(state)` pro vytvoření změnu uzavírání / otevírání a archivaci pozic.

     * **Pozor: 11.11.2020 Dojde k těmto změnám:**
        * Ve výpisu inzerátů (`GET jobs/` a `GET jobs/id`) dojde k přejmenování parametru `date_end` na `date_stopped` (Původní parametr `date_end` již nebude dostupný.), taktéž se odstraní request parametr `only_deleted` a `include_inactive`.
        * Ve výpisu inzerátů (`GET jobs/` a `GET jobs/id`) dojde k odstranění filtrovacích request parametrů  `only_deleted` a `include_inactive`. 
        * Ve výpisu inzerátů (`GET jobs/` a `GET jobs/id`) dojde k přejmenování filtrovací položky `status` na `activity_state` s bitmap hodnotami 1 a 2, viz přehled parametrů https://ceskytrhpracesro.docs.apiary.io/#reference/jobs/job-lists/get-all-jobs .
        * pozn.: Do tohoto datumu bude dostupný veškerý starý i nový obsah.
 
* **19.8.2020: branch v1 `1.6.1`**
     * U volání `GET jobs/` A `GET jobs/id` jsou v odpovědi navíc tyto parametry: `public_id`,`salary`,`education`,`last_update`,`draft`. Byl rozšíren parametr `details` o `facebook_picture_path` a `opening_reason`

* **1.6.2020: branch v1 `1.6.0`**
     * Přidáno API pro vytvoření reportů ze systému. 
     * Přibyla dokumentace na zobrazování konkrétní odpovědi (`GET answers/id`).
     * U dotazu na seznam odpovědí nyní vracíme parametr `hash` v konkrétní příloze.
     * U volání `GET answers/id` je možné volat parametr `im_author`.
     
* **19.2.2020: branch v1 `1.5.0`**
     * Přidáno API pro vytváření komunikace s uchazečem. 
     * U API s komunikací s uchazečem se nyní vypisují detailněji validační chyby (`meta`.`errors`). Postupně bude hlášení o chybách ve validaci ve všech volání.

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
 
 * **3.12.2018: branch v1 `1.3.4`**
     * V dokumentaci přibyl popis stavu při nedostupnosti API. 
     * Přibyly nové kódy chyb: `api.error.system.unavailable`, `api.error.request.property.wrong_text_length`,`api.error.request.property.maximum_array_items` 
 
 * **22.10.2018: branch v1 `1.3.3`**
     * Byla přidána nová sekce `referrals`, ve které je volání na přidání a výpis referralů. 
     
 * **16.10.2018: branch v1 `1.3.2`**
     * Do odpovědi u volání `GET /jobs` přibyl nový prvek `employment` a `education`.
 
 * **Pozor: 18.9.2018 přijde změna ve volání konkrétního inzerátu (`GET /jobs/id`): Nebude se nadále vracet pole s jedním inzerátem, ale bude vracet přímo objekt s daným inzerátem. Připravte na to prosím svoje aplikace.**

 * **17.9.2018: branch v1 `1.3.1`**
     * Bylo přidáno volání `DELETE /candidates`.
     * Přibyl popis kvót.
     * Přibyla kvóta `quota_candidates_delete`.
 
 * **11.9.2018: branch v1 `1.3`**
     * Bylo přidáno volání `POST /candidates`.
     * Do dokumentace byl přidán popis tagů.
     * Validace telefonního kontaktu v requestu `POST /answers` nyní akceptuje správné české formáty.
     * Validace emailu v requestu `POST /answers` nyní akceptuje znak "+".
 
 * **6.9.2018: branch v1 `1.2.3`**
     * Do volání `GET /jobs` přibyl parametr `include_inactive`.
     * Do volání `GET /jobs` přibyl parametr `include_inactive`.
     * Volání u neexistujícího inzerátu (`GET /jobs/id`) končí s http_statusem `404` namísto prázdné `200` odpovědi.
     * Aktualizace dokumentace o některé důležité informace (popis jednotlivých atributů u inzerátu).

 * **5.9.2018: branch v1 `1.2.2`**
     * Do odpovědi u volání `POST /Answers` přibyl parametr `source`.
     * Do odpovědi u volání `GET /jobs` přibyl parametr `details`.
     * Server nyní vrací přesnější informace u volání `GET /jobs`, dle specifikace dokumentace.
     * Aktualizace dokumentace o některé důležité informace.

 * **28.8.2018: branch v1 `1.2.1`**
    * Do odpovědi u volání `POST /Answers` přibyly nové možnosti (přidání odkazů na sociální sítě uchazeče).
    * Do odpovědi volání `POST /Answers` přibyl parametr `date_created` v objektu `gdpr_agreement`.
 
 * **6.8.2018: branch v1 `1.2`**
    * Přidána sekce **Filters**
    * Zprovozněn parametr filter_id u volání `GET /jobs`.
    * U volání `POST /answer`  přibyl parametr `referral_id`, `channel_id` a `extra`, který dovoluje přidat k odpovědi poznámku nebo tag..
    * U volání `POST /answer`  byl zprovozněn parametr `channel_id`.
    * U volání `POST /answer`  byl upraven parametr `gppr_agreements` - nyní je rozšířen o další atributy.
    * Volání `GET /enums/filters` je označeno jako deprecated. Namísto toho se doporučuje volat `GET /filters`.
 
 * **19.7.2018: branch v1 `1.1.1`**
    * Zprovozněn parametr channel_id u volání `GET /jobs`.
    * Do odpovědi `GET /jobs` přibyly tyto položky: `description` a `workfields`.
    * Opraven parametr channel_assignation u volání `GET /enums/workfields`.
    * Přidáno vynucení správných typů tokenů u volání `GET /enums/workfields` a `GET /jobs`.
    * Standardizovány některé kódové označení chyb + jsou zveřejněny a popsány v dokumentaci.
    * V dokumentaci jsou připsány další dodatečné informace o API.
 
 * **9.7.2018: branch v1 `1.1`**
    * Zprovozněno volání nad reálnými daty na url adrese: `https://app.recruitis.io/api2/`.
    * `GET /jobs` odstraněn parametr `regions`. Namísto něho se bude využívat parametr `office_id`. Filtrace podle lokality není v nejbližším plánu vývoje.
    * `GET /jobs` parametr `workfields` přejmenován na `workfield_id` (zpětná kompatibilita je zachována).
    * `GET /jobs` přidán parametr `office_id`.
    * Přidáno volání `GET /enums/offices`.
    * Volání `GET /enum/*` přejmenováno na `GET /enums/*`(zpětná kompatibilita je zachována: stále se dá volat `enums`).
    * Zprovozněno volání na `https://api.recruitis.io/`(volání na https://app.recruitis.io/api2/ bude zachováno).

 * **18.6.2018: branch v1 `1.0.1`**
    * `POST /Answers` nyní přijímá parametr `attachment` `base64`. V této návaznosti je nyní povinný atribut `attachment` `filename`.

 * **4.5.2018: branch v1 `1.0.0`**
    * Ustálená verze API volání `jobs` , `answers` a `login`.
    * Počáteční verze.

