#  OTC LVCTR API DOCS

### ID TYPE

* Individual

| Name                             | Retail Platform ID | Description |
|----------------------------------|--------------------|-------------|
| PASSPORT                         | 2                  |             |
| DRIVING_LICENSE                  | 4                  |             |
| ID_CARD                          | 5                  |             |
| CREDIT_FILE                      | 34                 |             |
| UTILITY_STATEMENT                | 40                 |             |
| OTHER                            | 3                  |             |
| GOVERNMENT_ISSUED_IDENTIFICATION | 35                 |             |
| PROVINCIAL_OR_TERRITORIAL        | 37                 |             |
| ----                             | ----               | --------    | 
| NATIONAL_ID                      | 101                |             |
| CONSULAR_ID                      | 102                |             |
| ELECTORAL_ID                     | 103                |             |
| RESIDENT_PERMIT_ID               | 104                |             |
| TAX_ID                           | 105                |             |
| STUDENT_ID                       | 106                |             |
| PASSPORT_CARD_ID                 | 107                |             |
| MILITARY_ID                      | 108                |             |
| PUBLIC_SAFETY_ID                 | 109                |             |
| HEALTH_ID                        | 110                |             |
| OTHER_ID                         | 111                |             |
| VISA                             | 112                |             |
| UNKNOWN                          | 0                  |             |
| REGULAR_DRIVING_LICENSE          | 201                |             |
| LEARNING_DRIVING_LICENSE         | 202                |             |
| E_PASSPORT                       | 301                |             |

* Entity:

| Name                            | Retail Platform ID | Description |
|---------------------------------|--------------------|-------------|
| ANNUAL_REPORT                   | 400                |             |
| ARTICLES_OF_ASSOCIATION         | 401                |             |
| CERTIFICATE_OF_CORPORATE_STATUS | 402                |             |
| CERTIFICATE_OF_INCORPORATION    | 403                |             |
| LETTER_OR_NOTICE_OF_ASSESSMENT  | 404                |             |
| PARTNERSHIP_AGREEMENT           | 405                |             |
| CORPORATE_OTHER                 | 406                |             |

------
### DepositionTypeCode List
| Name                                     | Value | Description |
|------------------------------------------|-------|-------------|
| Deposit to an account                    | 1     |             |
| Conducted currency exchange              | 3     |             |
| Purchase of casino chips                 | 4     |             |
| Purchase of bank draft                   | 5     |             |
| Purchase of money order                  | 6     |             |
| Life insurance policy purchase/deposit   | 7     |             |
| Securities purchase/deposit              | 8     |             |
| Real estate purchase/deposit             | 9     |             |
| Cash out                                 | 10    |             |
| Purchase jewellery                       | 14    |             |
| Purchase precious metals                 | 15    |             |
| Added to virtual currency wallet         | 17    |             |
| Exchange to virtual currency             | 18    |             |
| Outgoing virtual currency transfer       | 19    |             |
| Outgoing email money transfer            | 20    |             |
| Holding funds                            | 21    |             |
| Purchase of precious stones              | 22    |             |
| Issued cheque                            | 23    |             |
| Outgoing domestic funds transfer         | 24    |             |
| Outgoing international funds transfer    | 25    |             |
| Purchase of prepaid payment product/card | 26    |             |
| Other                                    | 11    |             |
------
### 1. CREATE Corporate Member Info

<br>

#### URL:
> wordpress.virgocx.org/otcInfo/saveMemberInfo/corporate  

#### METHOD:
> POST 

<br>

#### DATA:

| Name                                   | Type    | Salesforce Key             | Required | Example                   | Description                                                                                                          |
|----------------------------------------|---------|----------------------------|----------|---------------------------|----------------------------------------------------------------------------------------------------------------------|
| otcAccountNumber                       | String  | OTC Account #              | Required | OC00855                   || 
| retailAccountNumber                    | Integer | Retail Account #           | Optional | 73                        || 
| entityName                             | String  | Name                       | Required | DV Chain,LLC              | Corporation Name                                                                                                     | 
| buildingNumber                         | String  | Building number            | Required | 216                       || 
| streetAddress                          | String  | Street Address             | Required | West Jackson Boulevard    || 
| city                                   | String  | City                       | Required | OC00855                   || 
| countryCode                            | String  | Country Abbr               | Required | CA                        || 
| provinceCode                           | String  | Province Abbr              | Optional | ON                        | Country code is MX/US/CA,must provide this field                                                                     | 
| postalCode                             | String  | Postal Code                | Required | A1E4S2                    | A1E4S2(CA)/60606(US)                                                                                                 | 
| telephoneNumber                        | String  | Phone/Primary Phone        | Required | 3128786784                || 
| registrationNumber                     | String  | Register Number            | Required | ON51222012                ||
| registrationJurisdictionCountryCode    | String  | Registration Country Abbr  | Required | CA                        || 
| registrationJurisdictionProvinceCode   | String  | Registration Province Abbr | Optional | ON                        | Registration Country Abbr is MX/US/CA,must provide this field                                                        | 
| identificationType                     | String  | Identification Type        | Required | ANNUAL_REPORT             | Use the value in the name column of Entity Id type,if choose last one, provide the type name with ALL capital letter | 
| identificationNumber                   | String  | Identification Number      | Required ||| 
| identificationJurisdictionCountryCode  | String  | Jurisdiction Country Abbr  | Required | CA                        ||
| identificationJurisdictionProvinceCode | String  | Jurisdiction Province Abbr | Optional | ON                        | Jurisdiction Province Abbr is MX/US/CA,must provide this field                                                       |
| transactionPurpose                     | String  | Purpose/Other Purpose      | Required | OTC Trading/Market making | If the value of 'Purpose of Account' is other,provide the value of 'Other purposes'                                  |



<br>

```
Sample json here...
{
   "otcAccountNumber":"OC00855",
    "retailAccountNumber":42,
    "entityName":"Virgocx INC.",
    "buildingNumber":"45",
    "streetAddress":"Sheppard Ave",
    "city":"Toronto",
    "countryCode":"CA",
    "provinceCode":"ON",
    "postalCode":"K2E5S2",
    "telephoneNumber":"6135818505",
    "registrationNumber":"LEI 549300E8MLUDXFTONN47",
    "registrationJurisdictionCountryCode":"CA",
    "registrationJurisdictionProvinceCode":"ON",
    "identificationType":"LETTER_OR_NOTICE_OF_ASSESSMENT",
    "identificationNumber":"CA1234560_78",
    "identificationJurisdictionCountryCode":"CA",
    "identificationJurisdictionProvinceCode":"ON",
    "transactionPurpose":"OTC Trading"
}
```

---


### 2. CREATE Entity Person/Individual Info

<br>

#### URL:
> wordpress.virgocx.org/otcInfo/saveEntityInfo/entityPerson  

#### METHOD:
> POST

<br>

#### DATA:

| Name             | Type   | Required | Example      | salesforce key |
|------------------|--------|----------|--------------|----------------|
| otcAccountNumber | String | Required | OC00855      | OTC Account #  |
| entityName       | String | Required | Virgocx LLC. | Name           |
| firstName        | String | Required | Adam         | First Name     |
| middleName       | String | Optional || Middle Name  |
| lastName         | String | Required | Cai          | Last Name      |


<br>

```
Sample json here...
{
    "otcAccountNumber":"OC123456",
    "entityName":"KFC LLC.",
    "firstName":"Johnathan",
    "middleName":"Tome",
    "lastName":"Han"
}
```

---
### 3. CREATE Individual Member Info

<br>

#### URL:
> wordpress.virgocx.org/otcInfo/saveMemberInfo/individual  

#### METHOD:
> POST 

<br>

#### DATA:

| Name                                   | Type    | Salesforce Key                | Required | Example                   | Description                                                                         |
|----------------------------------------|---------|-------------------------------|----------|---------------------------|-------------------------------------------------------------------------------------|
| otcAccountNumber                       | String  | OTC Account #                 | Required | OC00855                   |                                                                                     | 
| retailAccountNumber                    | Integer | Retail Account #              | Optional | 73                        |                                                                                     | 
| firstName                              | String  | First Name                    | Required | Adam                      |                                                                                     | 
| middleName                             | String  | Middle Name                   | Optional |                           |                                                                                     | 
| lastName                               | String  | Last Name                     | Required | Cai                       |                                                                                     | 
| unitNumber                             | String  | Unit Number                   | Optional | 4305                      |                                                                                     | 
| buildingNumber                         | String  | Building Number               | Required | 45                        |                                                                                     | 
| streetAddress                          | String  | Street Address                | Required | Sheppard Ave              |                                                                                     | 
| city                                   | String  | City                          | Required | Toronto                   |                                                                                     | 
| district                               | String  | District                      | Optional |                           |                                                                                     |
| countryCode                            | String  | Country Abbr                  | Required | CA                        |                                                                                     | 
| provinceCode                           | String  | Province Abbr                 | Optional | ON                        | Country Abbr is MX/US/CA,must provide this field                                    | 
| postalCode                             | String  | Postal Code                   | Required | A1E4S2                    | US version:60606,5 numbers is ok                                                    | 
| telephoneNumber                        | String  | Phone/Primary Phone           | Required | 41612345678               |                                                                                     | 
| birthDate                              | String  | Date of birth                 | Required | 1989-02-23                |                                                                                     |
| residenceCountryCode                   | String  | Country of residence Abbr     | Required | CA                        |                                                                                     |
| occupation                             | String  | Title/Role                    | Required | Project manager           |                                                                                     |
| identificationType                     | String  | ID Type                       | Required | PASSPORT                  |                                                                                     |
| identificationNumber                   | String  | ID Number                     | Required | G520123456                |                                                                                     |
| identificationJurisdictionCountryCode  | String  | ID Jurisdiction Country Abbr  | Required | CA                        |                                                                                     |
| identificationJurisdictionProvinceCode | String  | ID Jurisdiction Province Abbr | Optional | ON                        | If ID Jurisdiction Country Abbr is MX/US/CA,must provide this field                 |
| transactionPurpose                     | String  | Purpose/Other Purpose         | Required | OTC Trading/Market making | If the value of 'Purpose of Account' is other,provide the value of 'Other purposes' |


<br>

```
Sample json here...
{
    "otcAccountNumber":"OC12345",
    "retailAccountNumber":"1476",
    "firstName":"Xiaofei",
    "middleName":"patrick",
    "lastName":"Wang",
    "unitNumber":"105",
    "buildingNumber":"46",
    "streetAddress":"Mango Drive",
    "city":"Toronto",
    "countryCode":"CA",
    "provinceCode":"ON",
    "postalCode":"A1E4S2",
    "telephoneNumber":"6135818505",
    "birthDate":"1989-02-23",
    "residenceCountryCode":"CA",
    "occupation":"Developer",
    "identificationType":"PASSPORT",
    "identificationNumber":"G52077336",
    "identificationJurisdictionCountryCode":"CA",
    "identificationJurisdictionProvinceCode":"NL",
    "transactionPurpose":"Investing in Cryptocurrencies"
}
```

---
### 4. CREATE/UPDATE Recharge Info

<br>

#### URL:
> wordpress.virgocx.org/saveRechargeInfo/cryptoToCrypto  

> wordpress.virgocx.org/saveRechargeInfo/cryptoToFiat  

#### METHOD:
> POST 

<br>

#### DATA:

| Name                             | Type      | Salesforce Key                     | Required | Example                                                              | Description                               |
|----------------------------------|-----------|------------------------------------|----------|----------------------------------------------------------------------|-------------------------------------------|
| otcAccountNumber                 | String    | OTC Account #                      | Required | "C1234"                                                              |                                           |
| transactionId                    | String    | TransactionID                      | Required | "C1433"                                                              |                                           |
| transactionTypeCode              | Integer   | Method of Transaction Abbr         | Required | 8                                                                    |                                           |
| clientToPlatformHash             | String    | Client to virgocx transaction hash | Required | "0x678011e2833e24628dcc58213fa176a2069607853a74d627a24ca05351d1a818" |                                           |
| clientToPlatformSendingWallet    | String    | Client to virgocx Sending Wallet   | Required | "0xeadc0397ceded9abfbd70ba7625db03067e9cb0c"                         |                                           |
| clientToPlatformReceivingWallet  | String    | Client to virgocx Receiving Wallet | Required | "0x780Bb33836f0DeC4138c39348979EEC739757D6"                          |                                           |
| conductorIndicator               | Integer   | conductorIndicator                 | Required | 0                                                                    | 0 false, 1 true                           |
| onBehalfIndicator                | Integer   | onBehalfIndicator                  | Required | 0                                                                    | 0 false, 1 true                           |
| baseCurrency                     | String    | Base Currency                      | Required | "USDT"                                                               |                                           |
| qty                              | String    | Base Currency Amount               | Required | "61215.320000"                                                       |                                           |
| baseCurrencyCanadianExchangeRate | String    | Current Crypto Price               | Required | "1.3236000000"                                                       |                                           |
| totalValueInCad                  | String    | Value in CAD                       | Required | "81024.600000"                                                       |                                           |
| otcRechargeCompleteActionsList   | JsonArray |                                    | Required | [{}]                                                                 | See CompleteAction table below            |
| otcOriginatorInfo                | JsonArray |                                    | Optional | [{}],if conductorIndicator value is 1, must provide this arrayList   | See otcOriginatorInfo table below         |
| otcOriginatorBehalfInfo          | JsonArray |                                    | Optional | [{}],if onBehalfIndicator value is 1, must provide this arrayList    | See otcOriginatorBehalfInfo table below   |


#### CompleteAction

| Name                                | Type    | Salesforce Key                     | Crypto   | Fiat     | Example                                                              | Description                                           |
|-------------------------------------|---------|------------------------------------|----------|----------|----------------------------------------------------------------------|-------------------------------------------------------|
| dispositionTypeCode                 | Integer |                                    | Required | Required | 17                                                                   | See table provide above                               |
| dispositionTypeOther                | String  |                                    | Optional | Optional | "Test Case"                                                          | If dispositionTypeCode is 11, must provide this value |
| platformToClientHash                | String  | Virgocx to Client Transaction Hash | Required | NO       | "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d2468c" |                                                       |
| platformToClientSendingWallet       | String  | Virgocx to Client Sending Wallet   | Required | NO       | "0x780bb33836f0bdec4138c39348979eec739757d6"                         |                                                       |
| platformToClientReceivingWallet     | String  | Virgocx to Client Receiving Wallet | Required | NO       | "0xedac0397ceded9abfbd70ba7625db03067e9cb0c"                         |                                                       |
| counterCurrency                     | String  | Counter Currency                   | Required | NO       | "USDC"                                                               |                                                       |
| counterCurrencyAmount               | String  | Counter Currency Amount            | Required | NO       | "61215.320000",                                                      |                                                       |
| counterCurrencyCanadianExchangeRate | String  | Price per token                    | Required | NO       | "1.0000000000"                                                       |                                                       |
| financialInstitutionNumber          | String  | Institution Number                 | NO       | Required | "004"                                                                |                                                       |
| branchNumber                        | String  | Transit Number                     | NO       | Required | "13282"                                                              |                                                       |
| accountNumber                       | String  | Account Number                     | NO       | Required | "6119164"                                                            |                                                       |
| accountCurrencyTypeCode             | String  | accountCurrencyTypeCode            | NO       | Required | "CAD"/"USD"/"EUR"                                                    |                                                       |
| accountTypeCode                     | Integer |                                    | NO       | Required | 1                                                                    | 1 Personal 2 Business 3 Trust 5 Casino 4 Other        |
| accountTypeOther                    | String  |                                    | NO       | Optional | "Corporate"                                                          | If type code is 4, must provide this value            |  
| fiatCurrency                        | String  | Fiat Currency                      | NO       | Required | "CAD"                                                                |                                                       |


#### otcOriginatorInfo


| Name                                   | Type    | Salesforce Key                | Individual | Corporate | Example                              | Description                                                         |
|----------------------------------------|---------|-------------------------------|------------|-----------|--------------------------------------|---------------------------------------------------------------------|
| perOrEntity                            | Integer |                               | Required   | Required  | 1 or 2                               | 1. Individual 2. entity                                             |
| entityName                             | String  | Name                          | NO         | Required  | "Virgocx"                            |                                                                     |
| firstName                              | String  | First Name                    | Required   | NO        | "Adam"                               |                                                                     |
| middleName                             | String  | Middle Name                   | Optional   | NO        |                                      |                                                                     |
| lastName                               | String  | Last Name                     | Required   | NO        | "Cai"                                |                                                                     |
| unitNum                                | String  | Unit Number                   | Optional   | Optional  |                                      |                                                                     |
| buildingNum                            | String  | Building Number               | Required   | Required  | "45"                                 |                                                                     |
| streetAddress                          | String  | Street Address                | Required   | Required  | "Sheppard Ave"                       |                                                                     |
| city                                   | String  | City                          | Required   | Required  | "Toronto"                            |                                                                     |
| district                               | String  | District                      | Optional   | Optional  | "North York"                         |                                                                     |
| countryCode                            | String  | Country Abbr                  | Required   | Required  | "CA"                                 |                                                                     |
| province                               | String  | Province Abbr                 | Optional   | Optional  | "ON"                                 | Country Abbr is MX/US/CA,must provide this field                    |
| postalCode                             | String  | Postal Code                   | Required   | Required  | "A1E4S2"                             | US version:60606,5 numbers is ok                                    |
| telephoneNumber                        | String  | Phone/Primary Phone           | Required   | Required  | "41612345678"                        |                                                                     |
| birthday                               | String  | Date of birth                 | Required   | NO        | "1989-02-23"                         |                                                                     |
| residenceCountryCode                   | String  | Country of residence Abbr     | Required   | NO        | "CA"                                 |                                                                     |
| occupation                             | String  | Title/Role                    | Required   | NO        | "Project manager"                    |                                                                     |
| idType                                 | String  | ID Type                       | Required   | Required  | "PASSPORT"/"ARTICLES_OF_ASSOCIATION" | Please provide value depend on ID type table list above             |
| idNum                                  | String  | ID Number                     | Required   | Required  | "G520123456"                         |                                                                     |
| identificationJurisdictionCountryCode  | String  | ID Jurisdiction Country Abbr  | Required   | Required  | "CA"                                 |                                                                     |
| identificationJurisdictionProvinceCode | String  | ID Jurisdiction Province Abbr | Optional   | Optional  | "ON"                                 | If ID Jurisdiction Country Abbr is MX/US/CA,must provide this field |
| registrationNumber                     | String  | Register Number               | NO         | Required  | "ON51222012"                         |                                                                     |
| registrationJurisdictionCountryCode    | String  | Registration Country Abbr     | NO         | Required  | "CA"                                 |                                                                     | 
| registrationJurisdictionProvinceCode   | String  | Registration Province Abbr    | NO         | Optional  | "ON"                                 | Registration Country Abbr is MX/US/CA,must provide this field       | 


#### otcOriginatorBehalfInfo

| Name                                   | Type    | Salesforce Key                | Individual | Corporate | Example                              | Description                                                                                                                                                                        |
|----------------------------------------|---------|-------------------------------|------------|-----------|--------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| perOrEntity                            | Integer |                               | Required   | Required  | 1 or 2                               | 1. Individual 2. entity                                                                                                                                                            |
| entityName                             | String  | Name                          | NO         | Required  | "Virgocx"                            |                                                                                                                                                                                    |
| firstName                              | String  | First Name                    | Required   | NO        | "Adam"                               |                                                                                                                                                                                    |
| middleName                             | String  | Middle Name                   | Optional   | NO        |                                      |                                                                                                                                                                                    |
| lastName                               | String  | Last Name                     | Required   | NO        | "Cai"                                |                                                                                                                                                                                    |
| unitNum                                | String  | Unit Number                   | Optional   | Optional  |                                      |                                                                                                                                                                                    |
| buildingNum                            | String  | Building Number               | Required   | Required  | "45"                                 |                                                                                                                                                                                    |
| streetAddress                          | String  | Street Address                | Required   | Required  | "Sheppard Ave"                       |                                                                                                                                                                                    |
| city                                   | String  | City                          | Required   | Required  | "Toronto"                            |                                                                                                                                                                                    |
| district                               | String  | District                      | Optional   | Optional  | "North York"                         |                                                                                                                                                                                    |
| countryCode                            | String  | Country Abbr                  | Required   | Required  | "CA"                                 |                                                                                                                                                                                    |
| province                               | String  | Province Abbr                 | Optional   | Optional  | "ON"                                 | Country Abbr is MX/US/CA,must provide this field                                                                                                                                   |
| postalCode                             | String  | Postal Code                   | Required   | Required  | "A1E4S2"                             | US version:60606,5 numbers is ok                                                                                                                                                   |
| telephoneNumber                        | String  | Phone/Primary Phone           | Required   | Required  | "41612345678"                        |                                                                                                                                                                                    |
| birthday                               | String  | Date of birth                 | Required   | NO        | "1989-02-23"                         |                                                                                                                                                                                    |
| residenceCountryCode                   | String  | Country of residence Abbr     | Required   | NO        | "CA"                                 |                                                                                                                                                                                    |
| occupation                             | String  | Title/Role                    | Required   | NO        | "Project manager"                    |                                                                                                                                                                                    |
| idType                                 | String  | ID Type                       | Required   | Required  | "PASSPORT"/"ARTICLES_OF_ASSOCIATION" | Please provide value depend on ID type table list above                                                                                                                            |
| idNum                                  | String  | ID Number                     | Required   | Required  | "G520123456"                         |                                                                                                                                                                                    |
| identificationJurisdictionCountryCode  | String  | ID Jurisdiction Country Abbr  | Required   | Required  | "CA"                                 |                                                                                                                                                                                    |
| identificationJurisdictionProvinceCode | String  | ID Jurisdiction Province Abbr | Optional   | Optional  | "ON"                                 | If ID Jurisdiction Country Abbr is MX/US/CA,must provide this field                                                                                                                |
| registrationNumber                     | String  | Register Number               | NO         | Required  | "ON51222012"                         |                                                                                                                                                                                    |
| registrationJurisdictionCountryCode    | String  | Registration Country Abbr     | NO         | Required  | "CA"                                 |                                                                                                                                                                                    |
| registrationJurisdictionProvinceCode   | String  | Registration Province Abbr    | NO         | Optional  | "ON"                                 | Registration Country Abbr is MX/US/CA,must provide this field                                                                                                                      |
| relationshipTypeCode                   | Integer |                               | Required   | Required  | 4                                    | 1. Accountant 2. Agent 10. Legal counsel 3. Borrower 4. Broker 11. Employer 5. Customer 6. Employee 7. Friend 8. Relative 12. Joint/Secondary owner 13. Power of attorney 9. Other |
| relationshipTypeOther                  | String  |                               | Optional   | Optional  | "Unknown" OR "Couple" OR "Wife"      | If relationShipTypeCode is 4, must provide this value                                                                                                                              |
```
Sample json here, crypto-crypto example 1,conductorIndicator is 1 and onbehalfIndictor is 1 and both of them are individual type
{
    "otcAccountNumber":"C1234",
    "transactionId":"C1488",
    "transactionTypeCode":8,
    "clientToPlatformHash":"0x678011e2833e24628dcc58213fa176a2069607853a74d627a24ca05351d1a999",
    "clientToPlatformSendingWallet":"0xeadc0397ceded9abfbd70ba7625db03067e9cb0c",
    "clientToPlatformReceivingWallet":"0x780Bb33836f0DeC4138c39348979EEC739757D6",
    "conductorIndicator":1,
    "onBehalfIndicator":1,
    "baseCurrency":"USDT",
    "qty":"888888.320000",
    "baseCurrencyCanadianExchangeRate":"1.3236000000",
    "totalValueInCad":"81024.600000",
    "transactionTime":"1646191191000",
    "otcRechargeCompleteActionsList":[
       {
             "dispositionTypeCode":17,
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d24987",
             "platformToClientSendingWallet":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "platformToClientReceivingWallet":"0xedac0397ceded9abfbd70ba7625db03067e9cb0c",
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"31215.320000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000"
       },
       {
             "dispositionTypeCode":17,
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d24987",
             "platformToClientSendingWallet":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "platformToClientReceivingWallet":"0xedac0397ceded9abfbd70ba7625db03067e9cb0c",
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"30000.000000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000"
       }
    ],
    "otcOriginatorInfo":[
        {
            "perOrEntity":1,
            "firstName":"Patrick",
            "lastName":"Wang",
            "buildingNum":"45",
            "streetAddress":"Sheppard Ave",
            "city":"Toronto",
            "countryCode":"CA",
            "province":"ON",
            "postalCode":"A1E4S2",
            "telephoneNumber":"4165818505",
            "birthday":"1989-02-23",
            "residenceCountryCode":"CA",
            "occupation":"Developer",
            "idType":"PASSPORT",
            "idNum":"G51213456",
            "identificationJurisdictionCountryCode":"CA",
            "identificationJurisdictionProvinceCode":"ON"        
        }
    ],
    "otcOriginatorBehalfInfo":[
        {
            "perOrEntity":1,
            "firstName":"Xiaofei",
            "lastName":"Wang",
            "buildingNum":"45",
            "streetAddress":"Sheppard Ave",
            "city":"Toronto",
            "countryCode":"CA",
            "province":"ON",
            "postalCode":"A1E4S2",
            "telephoneNumber":"4165818505",
            "birthday":"1989-01-23",
            "residenceCountryCode":"CA",
            "occupation":"Developer",
            "idType":"PASSPORT",
            "idNum":"G51213456",
            "identificationJurisdictionCountryCode":"CA",
            "identificationJurisdictionProvinceCode":"BC",
            "relationshipTypeCode":9,
            "relationshipTypeOther":"Unknown"
        }
    ]
}

Sample json here, crypto-crypto example 2,conductorIndicator is 1 and onbehalfIndictor is 1 and both of them are corporate type
{
    "otcAccountNumber":"C1234",
    "transactionId":"C1469",
    "transactionTypeCode":8,
    "clientToPlatformHash":"0x678011e2833e24628dcc58213fa176a2069607853a74d627a24ca05351d1a308",
    "clientToPlatformSendingWallet":"0xeadc0397ceded9abfbd70ba7625db03067e9cb0c",
    "clientToPlatformReceivingWallet":"0x780Bb33836f0DeC4138c39348979EEC739757D6",
    "conductorIndicator":1,
    "onBehalfIndicator":1,
    "baseCurrency":"USDT",
    "qty":"61215.320000",
    "baseCurrencyCanadianExchangeRate":"1.3236000000",
    "totalValueInCad":"81024.600000",
    "transactionTime":"1646191191000",
    "otcRechargeCompleteActionsList":[
       {
             "dispositionTypeCode":11,
             "dispositionTypeOther":"Test case",
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673",
             "platformToClientSendingWallet":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "platformToClientReceivingWallet":"0xedac0397ceded9abfbd70ba7625db03067e9cb0c",
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"61215.320000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000"
       }
    ],
    "otcOriginatorInfo":[
        {
            "perOrEntity":2,
            "entityName":"VirgocxCx LLC.",
            "buildingNum":"45",
            "streetAddress":"Sheppard Ave",
            "city":"Toronto",
            "countryCode":"CA",
            "province":"ON",
            "postalCode":"A1E4S2",
            "registrationNumber":"ON12345678",
            "registrationJurisdictionCountryCode":"CA",
            "registrationJurisdictionProvinceCode":"ON",
            "telephoneNumber":"4165818505",
            "idType":"ARTICLES_OF_ASSOCIATION",
            "idNum":"G51213456",
            "identificationJurisdictionCountryCode":"CN"
        }
    ],
    "otcOriginatorBehalfInfo":[
        {
            "perOrEntity":2,
            "entityName":"VirgocxCx LLC.",
            "buildingNum":"45",
            "streetAddress":"Sheppard Ave",
            "city":"Toronto",
            "countryCode":"CA",
            "province":"ON",
            "postalCode":"A1E4S2",
            "registrationNumber":"ON12345678",
            "registrationJurisdictionCountryCode":"CA",
            "registrationJurisdictionProvinceCode":"ON",
            "telephoneNumber":"4165818505",
            "idType":"ARTICLES_OF_ASSOCIATION",
            "idNum":"G51213456",
            "identificationJurisdictionCountryCode":"CA",
            "identificationJurisdictionProvinceCode":"ON",
            "relationshipTypeCode":10
        }
    ]
}

Sample json here, crypto-fiat example 3,conductorIndicator is 0 and onbehalfIndictor is 0
{
    "otcAccountNumber":"C1234",
    "transactionId":"C1470",
    "transactionTypeCode":8,
    "clientToPlatformHash":"0x678011e2833e24628dcc58213fa176a2069607853a74d627a24ca05351d1a308",
    "clientToPlatformSendingWallet":"0xeadc0397ceded9abfbd70ba7625db03067e9cb0c",
    "clientToPlatformReceivingWallet":"0x780Bb33836f0DeC4138c39348979EEC739757D6",
    "conductorIndicator":0,
    "onBehalfIndicator":0,
    "baseCurrency":"USDT",
    "qty":"61215.320000",
    "baseCurrencyCanadianExchangeRate":"1.3236000000",
    "totalValueInCad":"81024.600000",
    "transactionTime":"1646191191000",
    "otcRechargeCompleteActionsList":[
       {
             "depositionTypeCode":17,
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673",
             "platformToClientSendingWallet":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "platformToClientReceivingWallet":"0xedac0397ceded9abfbd70ba7625db03067e9cb0c",
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"61215.320000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000"
       },
       {
             "depositionTypeCode":24,
             "financialInstitutionNumber":"004",
             "branchNumber":"13282",
             "accountNumber":"6119164",
             "accountCurrencyTypeCode":"CAD",
             "accountTypeCode":1,
             "fiatCurrency":"CAD"
       }
    ],
    "otcOriginatorInfo":[],
    "otcOriginatorBehalfInfo":[]
}
```

---
