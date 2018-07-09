# RecruitisAPI
Dokumentace k API pro službu Recruitis.io vytvořená společností Český Trh Práce.
API je popsáno v adobe APIARY službě.

# Odkazy
[Dokumentace v APIARY](https://jsapi.apiary.io/previews/ceskytrhpracesro/reference)

# Changelog

 * **9.7.2018: branch v1 `1.1`**
    * Zprovozněno volání nad realnými daty na url adrese: `https://app.recrutis.io/api2/`
    * `GET /Jobs` odstraněn parametr `regions`
    * `GET /Jobs` parametr `workfields` přejmenován na `workfield_id` (zpětná kompatibilita je zachována.)
    * `GET /Jobs` přidán parametr `office_id`
    * volání `GET /enum/*` přejmenováno na `GET /enums/*`. (zpětná kompatibilita je zachována: stále se dá volat `enums`)
    * Plánuje se v nejbližší době: zprovozněno volání na `https://api.recrutis.io/` (volání na https://app.recrutis.io/api2/ bude zachováno)

 * **18.6.2018: branch v1 `1.0.1`**
    * `POST /Answers` nyní přijíma parametr `attachment` `base64`. V této návaznosti je nyní povinný atribut `attachment` `filename`.

 * **4.5.2018: branch v1 `1.0.0`**
    * Ustálená verze API volání `jobs` , `answers` a `login`
    * Počáteční verze
