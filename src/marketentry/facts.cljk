(ns marketentry.facts "Singapore market-entry catalog.")
(def catalog
  {"SGP" {:name "Singapore"
          :owner-authority "Ministry of Finance / GeBIZ"
          :legal-basis "Government Instruction Manual / GeBIZ terms"
          :national-spec "GeBIZ supplier registration + UEN"
          :provenance "https://www.gebiz.gov.sg/"
          :required-evidence ["UEN record"
                              "GeBIZ registration record"
                              "GST registration record"
                              "Authorized-representative record"]
          :rep-owner-authority "GeBIZ / contracting authorities"
          :rep-legal-basis "Singapore UEN entity typically required for GeBIZ supplier participation"
          :rep-provenance "https://www.gebiz.gov.sg/"
          :corporate-number-owner-authority "ACRA / IRAS"
          :corporate-number-legal-basis "Unique Entity Number (UEN)"
          :corporate-number-provenance "https://www.acra.gov.sg/"}})

(defn spec-basis [iso3] (get catalog iso3))
(defn coverage
  ([] (coverage (keys catalog)))
  ([iso3s]
   (let [have (filter catalog iso3s) missing (remove catalog iso3s)]
     {:requested (count iso3s) :covered (count have)
      :covered-jurisdictions (vec (sort have))
      :missing-jurisdictions (vec (sort missing))
      :note "R0 catalog seed"})))
(defn required-evidence-satisfied? [iso3 submitted]
  (when-let [{:keys [required-evidence]} (spec-basis iso3)]
    (= (count required-evidence) (count (filter (set submitted) required-evidence)))))
(defn evidence-checklist [iso3] (:required-evidence (spec-basis iso3) []))
(defn rep-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:rep-owner-authority sb)
      (select-keys sb [:rep-owner-authority :rep-legal-basis :rep-provenance]))))
(defn corporate-number-spec-basis [iso3]
  (when-let [sb (spec-basis iso3)]
    (when (:corporate-number-owner-authority sb)
      (select-keys sb [:corporate-number-owner-authority :corporate-number-legal-basis :corporate-number-provenance]))))
