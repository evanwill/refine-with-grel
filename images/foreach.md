https://github.com/mermaid-js/mermaid
[![](https://mermaid.ink/img/pako:eNqNksFugzAMhl_F8iWg0T4ASJPWQnfaaTuN9BBBKExAUBpaTaXvPocULe2pEQrYzvfbxrlgoUqJMVatOhe10Aa-Ut4Dre8851gpnYmiDk6iHeX6OLSNCVjCwghO9MALMBiUEUaxcP2jmn4OctzvncYbSaheJuasElNrKSkEq9XrxPFRkeMEm4BjzghgETBi5pfF2J5j6CQ3lgcr4Ge39DaYk91cTwApAZTleSCzgK3nEdnOyG4pf2FcF77lwV5PqcPBWdmdtVuq8f_vBO-532zynyaB-wpvk3A7RthJ3YmmpJFfrM82JDuaS0yfpazE2BqOvL_SUTEa9fnbFxgbPcoIx6EURqaNOGjRYVyJ9kheWTZG6Q93jebbdP0D7uCzkg?type=png)](https://mermaid.live/edit#pako:eNqNksFugzAMhl_F8iWg0T4ASJPWQnfaaTuN9BBBKExAUBpaTaXvPocULe2pEQrYzvfbxrlgoUqJMVatOhe10Aa-Ut4Dre8851gpnYmiDk6iHeX6OLSNCVjCwghO9MALMBiUEUaxcP2jmn4OctzvncYbSaheJuasElNrKSkEq9XrxPFRkeMEm4BjzghgETBi5pfF2J5j6CQ3lgcr4Ge39DaYk91cTwApAZTleSCzgK3nEdnOyG4pf2FcF77lwV5PqcPBWdmdtVuq8f_vBO-532zynyaB-wpvk3A7RthJ3YmmpJFfrM82JDuaS0yfpazE2BqOvL_SUTEa9fnbFxgbPcoIx6EURqaNOGjRYVyJ9kheWTZG6Q93jebbdP0D7uCzkg)

flowchart TD
    Z[["forEach(value.split(';'), v, v + ' potato').join(';')"]]
    A["one;two;three"] -->|"value.split(';')"| B("['one', 'two', 'three']")
    B --> |"v + ' potato'"| C("one potato")
    B --> |"v + ' potato'"| D("two potato")
    B --> |"v + ' potato'"| E("three potato")
    C --> F("['one potato', 'two potato', 'three potato']")
    D --> F 
    E --> F 
    F --> |".join(';')"| G["one potato;two potato; three potato"]
    