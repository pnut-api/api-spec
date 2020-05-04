# Users


* [General User Identifiers](#general-user-identifiers)
* [Canonical User Profiles](#canonical-user-profiles)
* [User Fields](#user-fields)
* [General User Parameters](#general-user-parameters)
* [Locales](#locales)
* [Timezones](#timezones)


## General User Identifiers {#general-user-identifiers}

Unless otherwise specified, user identifiers can be any of the following:

* User ID (`1`)
* @username (`@33mhz`)
* "me", when authenticated

User IDs are preferred where convenient, because they take less effort and will never change (unlike usernames).

Referring to usernames is not case-sensitive, but usernames will be returned from the API with the casing specified by the user -- so comparisons should normalize them before comparing.



## Canonical User Profiles {#canonical-user-profiles}

Any user profile can be found at `https://pnut.io/@username`, which will redirect to the user profile.


## User Fields {#user-fields}

<table>
    <tr>
        <th>Field</th>
        <th>Type</th>
        <th>Description</th>
    </tr>

    <tr>
        <td><code>badge</code></td>
        <td>object</td>
        <td>
            Optional. Badges are earned, currently only for supporting pnut.io.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>id</code></td>
                    <td>string</td>
                    <td>Reference ID of the badge.</td>
                </tr>

                <tr>
                    <td><code>name</code></td>
                    <td>string</td>
                    <td>Common name for the badge.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>content</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>avatar_image</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>is_default</code></td>
                                <td>boolean</td>
                                <td>Whether or not the user's avatar is the original identicon generated for their username, or an image they uploaded.</td>
                            </tr>

                            <tr>
                                <td><code>height</code></td>
                                <td>integer</td>
                                <td>Original height of the image.</td>
                            </tr>

                            <tr>
                                <td><code>link</code></td>
                                <td>string</td>
                                <td>URL linking to the current avatar image.</td>
                            </tr>

                            <tr>
                                <td><code>width</code></td>
                                <td>integer</td>
                                <td>Original width of the image.</td>
                            </tr>
                        </table>
                    </td>
                </tr>

                <tr>
                    <td><code>cover_image</code></td>
                    <td>object</td>
                    <td>
                        <table>
                            <tr>
                                <th>Field</th>
                                <th>Type</th>
                                <th>Description</th>
                            </tr>

                            <tr>
                                <td><code>link</code></td>
                                <td>string</td>
                                <td>URL linking to the current cover image.</td>
                            </tr>

                            <tr>
                                <td><code>is_default</code></td>
                                <td>boolean</td>
                                <td>Whether or not the user has uploaded an image for their cover image, or if it is the default plain white background.</td>
                            </tr>

                            <tr>
                                <td><code>width</code></td>
                                <td>integer</td>
                                <td>Original width of the image.</td>
                            </tr>

                            <tr>
                                <td><code>height</code></td>
                                <td>integer</td>
                                <td>Original height of the image.</td>
                            </tr>
                        </table>
                    </td>
                </tr>

                <tr>
                    <td><code>entities</code></td>
                    <td>object</td>
                    <td>Rich text information for this user. See the <a href="../implementation/entities">Entities</a> documentation.</td>
                </tr>

                <tr>
                    <td><code>html</code></td>
                    <td>string</td>
                    <td>Server-generated annotated HTML rendering of user text.</td>
                </tr>
                
                <tr>
                    <td><code>markdown_text</code></td>
                    <td>string</td>
                    <td><code>text</code>, with the original markdown links preserved. Only included when looking up the authenticated user's profile or <code>GET /token</code>.</td>
                </tr>

                <tr>
                    <td><code>text</code></td>
                    <td>string</td>
                    <td>User supplied text of the user. All Unicode characters allowed. Maximum length 256 characters. The maximum length can be retrieved from the Configuration endpoint.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>counts</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>bookmarks</code></td>
                    <td>integer</td>
                    <td>Number of bookmarks this user has saved.</td>
                </tr>

                <tr>
                    <td><code>clients</code></td>
                    <td>integer</td>
                    <td>Number of public clients this user has created.</td>
                </tr>

                <tr>
                    <td><code>followers</code></td>
                    <td>integer</td>
                    <td>Number of users following this user.</td>
                </tr>

                <tr>
                    <td><code>following</code></td>
                    <td>integer</td>
                    <td>Number of users this user is following.</td>
                </tr>

                <tr>
                    <td><code>posts</code></td>
                    <td>integer</td>
                    <td>Number of posts created by this user.</td>
                </tr>

                <tr>
                    <td><code>users</code></td>
                    <td>integer</td>
                    <td>Number of users this user has brought to the network.</td>
                </tr>
            </table>
        </td>
    </tr>

    <tr>
        <td><code>created_at</code></td>
        <td>string</td>
        <td>The time at which the User was created in ISO 8601 format.</td>
    </tr>

    <tr>
        <td><code>follows_you</code></td>
        <td>boolean</td>
        <td>Whether or not this user follows you.</td>
    </tr>

    <tr>
        <td><code>id</code></td>
        <td>string</td>
        <td>Primary identifier for a user. This will be an integer, but it is always expressed as a string to avoid limitations with the way JavaScript integers are expressed. This id space is unique to User objects. There can be a Post and User with the same ID; no relation is implied.</td>
    </tr>

    <tr>
        <td><code>locale</code></td>
        <td>string</td>
        <td>User locale in ISO format.</td>
    </tr>

    <tr>
        <td><code>name</code></td>
        <td>string</td>
        <td>Optional user-supplied name. All Unicode characters allowed. Maximum length 50 characters. <em>Be sure to escape if necessary.</em></td>
    </tr>

    <tr>
        <td><code>timezone</code></td>
        <td>string</td>
        <td>User timezone in tzinfo format.</td>
    </tr>

    <tr>
        <td><code>type</code></td>
        <td>string</td>
        <td>human, feed, or bot. See <a href="https://pnut.io/about/resources/account-types">Account Types</a> to be sure of the implications.</td>
    </tr>

    <tr>
        <td><code>username</code></td>
        <td>string</td>
        <td>Case sensitive. 20 characters, may only contain a-z, 0-9 and underscore.</td>
    </tr>

    <tr>
        <td><code>you_blocked</code></td>
        <td>boolean</td>
        <td>Whether or not you blocked this user.</td>
    </tr>

    <tr>
        <td><code>you_can_follow</code></td>
        <td>boolean</td>
        <td>Whether or not you <em>can</em> follow this user -- not taking into account <code>you_follow</code>.</td>
    </tr>

    <tr>
        <td><code>you_follow</code></td>
        <td>boolean</td>
        <td>Whether or not you follow this user.</td>
    </tr>

    <tr>
        <td><code>you_muted</code></td>
        <td>boolean</td>
        <td>Whether or not you muted this user.</td>
    </tr>

    <tr>
        <td><code>verified</code></td>
        <td>object</td>
        <td>
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>

                <tr>
                    <td><code>domain</code></td>
                    <td>string</td>
                    <td>Optional domain verified to be owned by the user</td>
                </tr>

                <tr>
                    <td><code>link</code></td>
                    <td>string</td>
                    <td>Optional URL verified to be owned by the user</td>
                </tr>
            </table>
        </td>
    </tr>
    <tr>
        <td><code>raw</code></td>
        <td>object</td>
        <td>The raw items attached to this object. Only included if query parameter specified.
            <table>
                <tr>
                    <th>Field</th>
                    <th>Type</th>
                    <th>Description</th>
                </tr>
                <tr>
                    <td><code>type</code></td>
                    <td>string</td>
                    <td>The type of raw item this is.</td>
                </tr>
                <tr>
                    <td><code>value</code></td>
                    <td>object</td>
                    <td>The values and fields you specify for this raw item.</td>
                </tr>
            </table>
        </td>
    </tr>
</table>



## General User Parameters {#general-user-parameters}

Any endpoint that returns user objects (including any that return post objects, message objects, etc.) can be subject to these parameters.

### General Parameters

Name|Type|Description
-|-|-
`include_html`|integer (0 or 1)|Should the post and user `html` field be included alongside the `text` field in the response objects? Defaults to true.
`include_user_html`|integer (0 or 1)|Should the user `html` field be included alongside the `text` field in the response objects? Defaults to true. Note that `include_html` takes priority if present.
`include_counts`|integer (0 or 1)|Include the user's counts. Defaults to true.
`include_user`|integer (0 or 1)|Return the user as their complete object, or only as (string) ID if false. Defaults to true.
`include_presence`|integer (0 or 1)|Include the user's current presence. Defaults to false.
`include_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all objects. Defaults to false.
`include_user_raw`|integer (0 or 1)|Include [raw](../implementation/raw) on all user objects. Defaults to false.



## Locales {#locales}

Below is a list of accepted user locales. To have more supported, make a feature request to [the API GitHub repository](https://github.com/pnut-api/api-spec). We would like to have translations of all of these for pnut.io account management. You make make pull requests to https://github.com/pnut-api/pnutio-localizations.

```
ar_SA, bg_BG, cs_CZ, da_DK, de_DE, en_GB, en_US, es_ES, fi_FI, fr_FR, gl_ES, hu_HU, it_IT, ja_JP, ko_KR, lv_LV, nl_NL, pl_PL, pt_BR, ru_RU, sq_AL, sr_SP, sv_SE, tr_TR, uk_UA, zh_CN, zh_HK, zh_TW
```



## Timezones {#timezones}

Below is a list of accepted user timezones.

```
Africa/Abidjan, Africa/Accra, Africa/Addis_Ababa, Africa/Algiers, Africa/Asmara, Africa/Bamako, Africa/Bangui, Africa/Banjul, Africa/Bissau, Africa/Blantyre, Africa/Brazzaville, Africa/Bujumbura, Africa/Cairo, Africa/Casablanca, Africa/Ceuta, Africa/Conakry, Africa/Dakar, Africa/Dar_es_Salaam, Africa/Djibouti, Africa/Douala, Africa/El_Aaiun, Africa/Freetown, Africa/Gaborone, Africa/Harare, Africa/Johannesburg, Africa/Juba, Africa/Kampala, Africa/Khartoum, Africa/Kigali, Africa/Kinshasa, Africa/Lagos, Africa/Libreville, Africa/Lome, Africa/Luanda, Africa/Lubumbashi, Africa/Lusaka, Africa/Malabo, Africa/Maputo, Africa/Maseru, Africa/Mbabane, Africa/Mogadishu, Africa/Monrovia, Africa/Nairobi, Africa/Ndjamena, Africa/Niamey, Africa/Nouakchott, Africa/Ouagadougou, Africa/Porto-Novo, Africa/Sao_Tome, Africa/Tripoli, Africa/Tunis, Africa/Windhoek, America/Adak, America/Anchorage, America/Anguilla, America/Antigua, America/Araguaina, America/Argentina/Buenos_Aires, America/Argentina/Catamarca, America/Argentina/Cordoba, America/Argentina/Jujuy, America/Argentina/La_Rioja, America/Argentina/Mendoza, America/Argentina/Rio_Gallegos, America/Argentina/Salta, America/Argentina/San_Juan, America/Argentina/San_Luis, America/Argentina/Tucuman, America/Argentina/Ushuaia, America/Aruba, America/Asuncion, America/Atikokan, America/Bahia, America/Bahia_Banderas, America/Barbados, America/Belem, America/Belize, America/Blanc-Sablon, America/Boa_Vista, America/Bogota, America/Boise, America/Cambridge_Bay, America/Campo_Grande, America/Cancun, America/Caracas, America/Cayenne, America/Cayman, America/Chicago, America/Chihuahua, America/Costa_Rica, America/Creston, America/Cuiaba, America/Curacao, America/Danmarkshavn, America/Dawson, America/Dawson_Creek, America/Denver, America/Detroit, America/Dominica, America/Edmonton, America/Eirunepe, America/El_Salvador, America/Fort_Nelson, America/Fortaleza, America/Glace_Bay, America/Godthab, America/Goose_Bay, America/Grand_Turk, America/Grenada, America/Guadeloupe, America/Guatemala, America/Guayaquil, America/Guyana, America/Halifax, America/Havana, America/Hermosillo, America/Indiana/Indianapolis, America/Indiana/Knox, America/Indiana/Marengo, America/Indiana/Petersburg, America/Indiana/Tell_City, America/Indiana/Vevay, America/Indiana/Vincennes, America/Indiana/Winamac, America/Inuvik, America/Iqaluit, America/Jamaica, America/Juneau, America/Kentucky/Louisville, America/Kentucky/Monticello, America/Kralendijk, America/La_Paz, America/Lima, America/Los_Angeles, America/Lower_Princes, America/Maceio, America/Managua, America/Manaus, America/Marigot, America/Martinique, America/Matamoros, America/Mazatlan, America/Menominee, America/Merida, America/Metlakatla, America/Mexico_City, America/Miquelon, America/Moncton, America/Monterrey, America/Montevideo, America/Montserrat, America/Nassau, America/New_York, America/Nipigon, America/Nome, America/Noronha, America/North_Dakota/Beulah, America/North_Dakota/Center, America/North_Dakota/New_Salem, America/Ojinaga, America/Panama, America/Pangnirtung, America/Paramaribo, America/Phoenix, America/Port-au-Prince, America/Port_of_Spain, America/Porto_Velho, America/Puerto_Rico, America/Punta_Arenas, America/Rainy_River, America/Rankin_Inlet, America/Recife, America/Regina, America/Resolute, America/Rio_Branco, America/Santarem, America/Santiago, America/Santo_Domingo, America/Sao_Paulo, America/Scoresbysund, America/Sitka, America/St_Barthelemy, America/St_Johns, America/St_Kitts, America/St_Lucia, America/St_Thomas, America/St_Vincent, America/Swift_Current, America/Tegucigalpa, America/Thule, America/Thunder_Bay, America/Tijuana, America/Toronto, America/Tortola, America/Vancouver, America/Whitehorse, America/Winnipeg, America/Yakutat, America/Yellowknife, Antarctica/Casey, Antarctica/Davis, Antarctica/DumontDUrville, Antarctica/Macquarie, Antarctica/Mawson, Antarctica/McMurdo, Antarctica/Palmer, Antarctica/Rothera, Antarctica/Syowa, Antarctica/Troll, Antarctica/Vostok, Arctic/Longyearbyen, Asia/Aden, Asia/Almaty, Asia/Amman, Asia/Anadyr, Asia/Aqtau, Asia/Aqtobe, Asia/Ashgabat, Asia/Atyrau, Asia/Baghdad, Asia/Bahrain, Asia/Baku, Asia/Bangkok, Asia/Barnaul, Asia/Beirut, Asia/Bishkek, Asia/Brunei, Asia/Chita, Asia/Choibalsan, Asia/Colombo, Asia/Damascus, Asia/Dhaka, Asia/Dili, Asia/Dubai, Asia/Dushanbe, Asia/Famagusta, Asia/Gaza, Asia/Hebron, Asia/Ho_Chi_Minh, Asia/Hong_Kong, Asia/Hovd, Asia/Irkutsk, Asia/Jakarta, Asia/Jayapura, Asia/Jerusalem, Asia/Kabul, Asia/Kamchatka, Asia/Karachi, Asia/Kathmandu, Asia/Khandyga, Asia/Kolkata, Asia/Krasnoyarsk, Asia/Kuala_Lumpur, Asia/Kuching, Asia/Kuwait, Asia/Macau, Asia/Magadan, Asia/Makassar, Asia/Manila, Asia/Muscat, Asia/Nicosia, Asia/Novokuznetsk, Asia/Novosibirsk, Asia/Omsk, Asia/Oral, Asia/Phnom_Penh, Asia/Pontianak, Asia/Pyongyang, Asia/Qatar, Asia/Qyzylorda, Asia/Riyadh, Asia/Sakhalin, Asia/Samarkand, Asia/Seoul, Asia/Shanghai, Asia/Singapore, Asia/Srednekolymsk, Asia/Taipei, Asia/Tashkent, Asia/Tbilisi, Asia/Tehran, Asia/Thimphu, Asia/Tokyo, Asia/Tomsk, Asia/Ulaanbaatar, Asia/Urumqi, Asia/Ust-Nera, Asia/Vientiane, Asia/Vladivostok, Asia/Yakutsk, Asia/Yangon, Asia/Yekaterinburg, Asia/Yerevan, Atlantic/Azores, Atlantic/Bermuda, Atlantic/Canary, Atlantic/Cape_Verde, Atlantic/Faroe, Atlantic/Madeira, Atlantic/Reykjavik, Atlantic/South_Georgia, Atlantic/St_Helena, Atlantic/Stanley, Australia/Adelaide, Australia/Brisbane, Australia/Broken_Hill, Australia/Currie, Australia/Darwin, Australia/Eucla, Australia/Hobart, Australia/Lindeman, Australia/Lord_Howe, Australia/Melbourne, Australia/Perth, Australia/Sydney, Europe/Amsterdam, Europe/Andorra, Europe/Astrakhan, Europe/Athens, Europe/Belgrade, Europe/Berlin, Europe/Bratislava, Europe/Brussels, Europe/Bucharest, Europe/Budapest, Europe/Busingen, Europe/Chisinau, Europe/Copenhagen, Europe/Dublin, Europe/Gibraltar, Europe/Guernsey, Europe/Helsinki, Europe/Isle_of_Man, Europe/Istanbul, Europe/Jersey, Europe/Kaliningrad, Europe/Kiev, Europe/Kirov, Europe/Lisbon, Europe/Ljubljana, Europe/London, Europe/Luxembourg, Europe/Madrid, Europe/Malta, Europe/Mariehamn, Europe/Minsk, Europe/Monaco, Europe/Moscow, Europe/Oslo, Europe/Paris, Europe/Podgorica, Europe/Prague, Europe/Riga, Europe/Rome, Europe/Samara, Europe/San_Marino, Europe/Sarajevo, Europe/Saratov, Europe/Simferopol, Europe/Skopje, Europe/Sofia, Europe/Stockholm, Europe/Tallinn, Europe/Tirane, Europe/Ulyanovsk, Europe/Uzhgorod, Europe/Vaduz, Europe/Vatican, Europe/Vienna, Europe/Vilnius, Europe/Volgograd, Europe/Warsaw, Europe/Zagreb, Europe/Zaporozhye, Europe/Zurich, Indian/Antananarivo, Indian/Chagos, Indian/Christmas, Indian/Cocos, Indian/Comoro, Indian/Kerguelen, Indian/Mahe, Indian/Maldives, Indian/Mauritius, Indian/Mayotte, Indian/Reunion, Pacific/Apia, Pacific/Auckland, Pacific/Bougainville, Pacific/Chatham, Pacific/Chuuk, Pacific/Easter, Pacific/Efate, Pacific/Enderbury, Pacific/Fakaofo, Pacific/Fiji, Pacific/Funafuti, Pacific/Galapagos, Pacific/Gambier, Pacific/Guadalcanal, Pacific/Guam, Pacific/Honolulu, Pacific/Kiritimati, Pacific/Kosrae, Pacific/Kwajalein, Pacific/Majuro, Pacific/Marquesas, Pacific/Midway, Pacific/Nauru, Pacific/Niue, Pacific/Norfolk, Pacific/Noumea, Pacific/Pago_Pago, Pacific/Palau, Pacific/Pitcairn, Pacific/Pohnpei, Pacific/Port_Moresby, Pacific/Rarotonga, Pacific/Saipan, Pacific/Tahiti, Pacific/Tarawa, Pacific/Tongatapu, Pacific/Wake, Pacific/Wallis
```
