https://github.com/mermaid-js/mermaid
[![](https://mermaid.ink/img/pako:eNpdkDFPwzAQhf-KdUsSKUVlzVCJtGUqC2Wi1-EUO4kl20HGAaE0_52zjTrgxdbT99473wLdJBU00JvpuxvJB3F6RSf4vF8uCLovv8jM6sEoN4SxrMROPG5rUbR6KPg6WzKmqBCu1-x6YlNysCQ2m51oyz_hHoFQZbZNwH5BiKEIa5b3Sb4hvPkYcxMHzkyFnPkPeSbzmZhjZPI0dwod1GCVt6Qlf3GJKkIYlWVLw0-peppNQEC3MkpzmM4_roMmcHMN84ekoA6aBk8Wmj521aCkDpN_yWtL21t_AZyKYdM?type=png)](https://mermaid.live/edit#pako:eNpdkDFPwzAQhf-KdUsSKUVlzVCJtGUqC2Wi1-EUO4kl20HGAaE0_52zjTrgxdbT99473wLdJBU00JvpuxvJB3F6RSf4vF8uCLovv8jM6sEoN4SxrMROPG5rUbR6KPg6WzKmqBCu1-x6YlNysCQ2m51oyz_hHoFQZbZNwH5BiKEIa5b3Sb4hvPkYcxMHzkyFnPkPeSbzmZhjZPI0dwod1GCVt6Qlf3GJKkIYlWVLw0-peppNQEC3MkpzmM4_roMmcHMN84ekoA6aBk8Wmj521aCkDpN_yWtL21t_AZyKYdM)

flowchart LR
    Z[["if(value.length() > 10, 'Big', 'Small')"]]
    A["value"] --> B("value.length()")
    B --> C{"> 10"}
    C --> |"True"| D["'Big'"]
    C --> |"False"| E["'Small'"]
    
