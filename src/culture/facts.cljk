(ns culture.facts
  "Country-level regional-culture catalog for Singapore (SGP) -- national
  dishes, protected products, beverages, crafts, festivals and heritage
  sites, per ADR-2607171400 addendum 2 (cloud-itonami-municipality-
  culture-catalog Wave 1, in com-junkawasaki/root). Sibling namespace to
  `marketentry.facts` / `statute.facts` (ADR-2607141700); city-level
  counterparts live in the cloud-itonami-municipality-* repos.

  Catalog is keyed by UPPERCASE ISO3 (mirrors `statute.facts`); entries
  carry no :culture/municipality (that attribute is city-level only).

  Every entry cites a source URL that was actually fetched and read on
  :culture/retrieved-at -- never fabricated. Summaries state only what the
  cited source confirms. An item not in this table has NO spec-basis, full
  stop; extend `catalog`, do not invent an id/url.")

(def catalog
  "iso3 -> vector of culture entries."
  {"SGP"
   [{:culture/id "sgp.dish.chilli-crab"
     :culture/name "Chilli crab"
     :culture/country "SGP"
     :culture/kind :dish
     :culture/summary "Mud crab stir-fried in a semi-thick, sweet and savoury tomato-and-chilli sauce; created in Singapore in 1956 by Cher Yam Tian, whose family opened Palm Beach Seafood restaurant, and popular in both Singapore and Malaysia."
     :culture/url "https://en.wikipedia.org/wiki/Chilli_crab"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "sgp.dish.hainanese-chicken-rice"
     :culture/name "Hainanese chicken rice"
     :culture/country "SGP"
     :culture/kind :dish
     :culture/summary "Poached or roasted chicken with seasoned rice and chilli sauce; widely considered one of the national dishes of Singapore, popularised there in the 1940s-50s by Hainanese immigrants, and eaten daily across the country's hawker centres."
     :culture/url "https://en.wikipedia.org/wiki/Hainanese_chicken_rice"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "sgp.dish.laksa"
     :culture/name "Laksa"
     :culture/country "SGP"
     :culture/kind :dish
     :culture/summary "Spicy coconut-curry or tamarind-soured noodle soup popular across Southeast Asia; the Singaporean-style version and Katong laksa (spoon-only, from a Singapore neighbourhood) are recognized variants, believed to have arisen from Peranakan Chinese interaction with local Singaporean Malays, though the dish is also common in Malaysia and Indonesia."
     :culture/url "https://en.wikipedia.org/wiki/Laksa"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "sgp.beverage.singapore-sling"
     :culture/name "Singapore Sling"
     :culture/country "SGP"
     :culture/kind :beverage
     :culture/summary "Gin-based sling cocktail reputed to have been developed between 1899 and 1915 by bartender Ngiam Tong Boon at the Long Bar of Raffles Hotel, Singapore, originally colored to resemble fruit juice so women could drink it in public."
     :culture/url "https://en.wikipedia.org/wiki/Singapore_sling"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "sgp.festival.chingay-parade"
     :culture/name "Chingay Parade"
     :culture/country "SGP"
     :culture/kind :festival
     :culture/summary "Annual street parade held as part of Chinese New Year festivities; Singapore's first Chingay parade took place on 4 February 1973 after Prime Minister Lee Kuan Yew authorized it following a fireworks ban, and it has since grown into a multi-ethnic celebration."
     :culture/url "https://en.wikipedia.org/wiki/Chingay_parade"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "sgp.heritage.botanic-gardens"
     :culture/name "Singapore Botanic Gardens"
     :culture/country "SGP"
     :culture/kind :heritage
     :culture/summary "Tropical garden founded in 1859, inscribed as a UNESCO World Heritage Site on 4 July 2015 -- Singapore's first such site and the first tropical botanic garden, and only third botanic garden overall, on the World Heritage list."
     :culture/url "https://en.wikipedia.org/wiki/Singapore_Botanic_Gardens"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}
    {:culture/id "sgp.heritage.hawker-culture"
     :culture/name "Hawker culture in Singapore"
     :culture/country "SGP"
     :culture/kind :heritage
     :culture/summary "Community dining and culinary practices centred on hawker centres, which function as 'community dining rooms' bridging Singapore's multicultural communities; inscribed on the UNESCO Representative List of the Intangible Cultural Heritage of Humanity on 16 December 2020."
     :culture/url "https://en.wikipedia.org/wiki/Hawker_centre"
     :culture/url-provenance :wikipedia-en
     :culture/retrieved-at "2026-07-17"}]})

(defn spec-basis [iso3] (get catalog iso3))

(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s)
         missing (remove catalog iso3s)]
     {:requested (count iso3s)
      :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note (str "cloud-itonami-iso3166-sgp culture catalog "
                 "(ADR-2607171400 addendum 2, Wave 1): " (count (get catalog "SGP"))
                 " SGP entries, each with a fetched-and-read citation. "
                 "Extend `culture.facts/catalog`, never fabricate an id/url.")})))

(defn by-kind [iso3 kind]
  (filterv #(= (:culture/kind %) kind) (spec-basis iso3)))
