#  OTC LVCTR API DOCS

### ID TYPE

* Individual

| Name                             | Retail Platform ID | Description |
|----------------------------------|--------------------|-------------|
| PASSPORT                         | 2                  |             |
| DRIVING_LICENSE                  | 4                  |             |
| ID_CARD                          | 5                  |             |
| CREDIT_FILE                      | 34                 |             |
| PERMANENT_RESIDENT_CARD          | 32                 |             |
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

### Authentication Rule

Request Param:

> timestamp: the unix timestamp of the time when the request happens.

> sign: lowercase of md5(timestamp+APIKEY)

For example:   
Request time: Mar 23 2022 12:55:54 EST, APIKEY:ABCDE   
Sign is md5(1648054554ABCDE) -> cb333877936e25aeb33e61a946d24155   
URL:  
> otcwordpress.virgocx.org/v2/otcInfo/saveMemberInfo/corporate?timestamp=1648054554&sign=cb333877936e25aeb33e61a946d24155

### 1. CREATE Corporate Member Info

<br>

#### URL:
> otcwordpress.virgocx.org/v2/otcInfo/saveMemberInfo/corporate?timestamp={}&sign={}  

#### METHOD:
> POST 

<br>

#### DATA:

| Name                                   | Type    | Salesforce Key             | Required | Example                   | Description                                                                                                          |
|----------------------------------------|---------|----------------------------|----------|---------------------------|----------------------------------------------------------------------------------------------------------------------|
| otcAccountNumber                       | String  | OTC Account #              | Required | OC00855                   || 
| retailAccountNumber                    | Integer | Retail Account #           | Optional | 73                        || 
| entityName                             | String  | Name                       | Required | DV Chain,LLC              | Corporation Name                                                                                                     | 
| userName(new)                          | String  |                            | Optional | patrickwang               | userName                                                                                                             | 
| email(new)                             | String  |                            | Optional | patrick.wang@virgocx.ca   | email                                                                                                                |
| buildingNumber                         | String  | Building number            | Required | 216                       || 
| streetAddress                          | String  | Street Address             | Required | West Jackson Boulevard    || 
| city                                   | String  | City                       | Required | OC00855                   || 
| countryCode                            | String  | Country Abbr               | Required | CA                        || 
| provinceCode                           | String  | Province Abbr              | Required | ON                        | If don't have specific value, use "Unknown"                                                                          | 
| postalCode                             | String  | Postal Code                | Required | A1E4S2                    | A1E4S2(CA)/60606(US)                                                                                                 | 
| telephoneNumber                        | String  | Phone                      | Required | 3128786784                || 
| telephoneExtension(new)                | String  |                            | Optional |                           ||
| businessNature(new)                    | String  |                            | Required |                           ||
| registrationNumber                     | String  | Register Number            | Required | ON51222012                ||
| registrationJurisdictionCountryCode    | String  | Registration Country Abbr  | Required | CA                        || 
| registrationJurisdictionProvinceCode   | String  | Registration Province Abbr | Required | ON                        | If don't have specific value, use "Unknown"                                                                          | 
| identificationType                     | String  | Identification Type        | Required | ANNUAL_REPORT             | Use the value in the name column of Entity Id type,if choose last one, provide the type name with ALL capital letter | 
| identificationNumber                   | String  | Registration Number        | Required ||| 
| identificationJurisdictionCountryCode  | String  | Jurisdiction Country Abbr  | Required | CA                        ||
| identificationJurisdictionProvinceCode | String  | Jurisdiction Province Abbr | Required | ON                        | If don't have specific value, use "Unknown"                                                                          |
| transactionPurpose                     | String  | Transaction Purpose        | Required | OTC Trading/Market making | If the value of 'Purpose of Account' is other,provide the value of 'Other purposes'                                  |



<br>

```
Sample json here...
{
   "otcAccountNumber":"OC00855",
    "retailAccountNumber":42,
    "entityName":"Virgocx INC.",
    "userName":"patrickwang",
    "email":"patrick.wang@virgocx.ca"
    "buildingNumber":"45",
    "streetAddress":"Sheppard Ave",
    "city":"Toronto",
    "countryCode":"CA",
    "provinceCode":"ON",
    "postalCode":"K2E5S2",
    "telephoneNumber":"6135818505",
    "telephoneExtension":"008",
    "businessNature":"Trading platform",
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
> otcwordpress.virgocx.org/v2/otcInfo/saveEntityInfo/entityPerson?timestamp={}&sign={}    

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
> otcwordpress.virgocx.org/v2/otcInfo/saveMemberInfo/individual?timestamp={}&sign={}    

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
| userName(new)                          | String  |                               | Optional | patrickwang               | userName                                                                            | 
| email(new)                             | String  |                               | Required | patrick.wang@virgocx.ca   | email                                                                               |
| unitNumber                             | String  | Unit Number                   | Optional | 4305                      |                                                                                     | 
| buildingNumber                         | String  | Building Number               | Required | 45                        |                                                                                     | 
| streetAddress                          | String  | Street Address                | Required | Sheppard Ave              |                                                                                     | 
| city                                   | String  | City                          | Required | Toronto                   |                                                                                     | 
| district                               | String  | District                      | Optional |                           |                                                                                     |
| countryCode                            | String  | Country Abbr                  | Required | CA                        |                                                                                     | 
| provinceCode                           | String  | Province Abbr                 | Required | ON                        | If don't have specific value, use "Unknown"                                         | 
| postalCode                             | String  | Postal Code                   | Required | A1E4S2                    | US version:60606,5 numbers is ok                                                    | 
| telephoneNumber                        | String  | Phone                         | Required | 41612345678               |                                                                                     | 
| telephoneExtension(new)                | String  |                               | Optional |                           |                                                                                     |
| birthDate                              | String  | Date of birth                 | Required | 1989-02-23                |                                                                                     |
| residenceCountryCode                   | String  | Country of residence Abbr     | Required | CA                        |                                                                                     |
| occupation                             | String  | Title/Role                    | Required | Project manager           |                                                                                     |
| employerName(new)                      | String  |                               | Optional | Virgocx                   | employer name                                                                       |
| identificationType                     | String  | ID Type                       | Required | PASSPORT                  |                                                                                     |
| identificationNumber                   | String  | ID Number                     | Required | G520123456                |                                                                                     |
| identificationJurisdictionCountryCode  | String  | ID Jurisdiction Country Abbr  | Required | CA                        |                                                                                     |
| identificationJurisdictionProvinceCode | String  | ID Jurisdiction Province Abbr | Required | ON                        | If don't have specific value, use "Unknown"                                         |
| transactionPurpose                     | String  | Transaction Purpose           | Required | OTC Trading/Market making | If the value of 'Purpose of Account' is other,provide the value of 'Other purposes' |


<br>

```
Sample json here...
{
    "otcAccountNumber":"OC33333",
    "retailAccountNumber":"1475",
    "firstName":"Xiaofei",
    "middleName":"patrick",
    "lastName":"Wang",
    "userName"："patrickwang"，
    "email":"patrick.wang@virgocx.ca"
    "unitNumber":"105",
    "buildingNumber":"46",
    "streetAddress":"Mango Drive",
    "city":"Toronto",
    "countryCode":"CA",
    "provinceCode":"ON",
    "postalCode":"A1E4S2",
    "telephoneNumber":"6135818505",
    "telephoneExtension":"008",
    "birthDate":"1989-02-23",
    "residenceCountryCode":"CA",
    "occupation":"Developer",
    "employerName":"Virgocx",
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
> otcwordpress.virgocx.org/v2/otcInfo/saveRechargeInfo/cryptoToCrypto?timestamp={}&sign={}    

> otcwordpress.virgocx.org/v2/otcInfo/saveRechargeInfo/cryptoToFiat?timestamp={}&sign={}    

#### METHOD:
> POST 

<br>

#### DATA:

| Name                                       | Type      | Salesforce Key             | Required | Example                                                            | Description                                                                    |
|--------------------------------------------|-----------|----------------------------|----------|--------------------------------------------------------------------|--------------------------------------------------------------------------------|
| otcAccountNumber                           | String    | OTC Account #              | Required | "C1234"                                                            |                                                                                |
| transactionId                              | String    | TransactionID              | Required | "C1433"                                                            |                                                                                |
| transactionMethodTypeCode(update key name) | Integer   | Method of Transaction Abbr | Required | 8                                                                  | 1:In person 7:Other 8:Online 9:Virtual currency ATM  was "transactionTypeCode" |
| transactionMethodTypeOther(new)            | String    |                            | Optional | "Whatsapp"                                                         | If transactionMethodTypeCode is 7 must provide this value                      |
| conductorIndicator                         | Integer   | conductorIndicator         | Required | 0                                                                  | 0 false, 1 true                                                                |
| onBehalfIndicator                          | Integer   | onBehalfIndicator          | Required | 0                                                                  | 0 false, 1 true                                                                |
| qty                                        | String    | Total Crypto Amount        | Required | "61215.320000"                                                     |                                                                                |
| totalValueInCad                            | String    | Value in CAD               | Required | "81024.600000"                                                     |                                                                                |
| deviceTypeCode(new)                        | Integer   |                            | Optional | 3                                                                  | 1 Computer/Laptop,2 Mobile phone,3 Tablet,4 Other                              |
| deviceTypeOther(new)                       | String    |                            | Optional |                                                                    | if deviceTypeCode is 4, must provide this value                                |
| deviceIdentificationNumber(new)            | String    |                            | Optional | "03e73331cd0f94093a4bb22dfdb3baee"                                 |                                                                                |
| deviceIpAddress(new)                       | String    |                            | Optional | "24.16.223.12"                                                     |                                                                                |
| transactionTime                            | timestamp |                            | Required | "1646191191000"                                                    | Transaction time for this record, pass the value to api with 13 digits         |
| institutionCode(new)                       | Integer   |                            | Required | 1                                                                  | virgocx 1,direct Inc 2                                                         |
| otcRechargeStartActionsList(new)           | JsonArray |                            | Required | [{}]                                                               | See StartAction table below                                                    |
| otcRechargeCompleteActionsList             | JsonArray |                            | Required | [{}]                                                               | See CompleteAction table below                                                 |
| otcOriginatorInfo                          | JsonArray |                            | Optional | [{}],if conductorIndicator value is 1, must provide this arrayList | See otcOriginatorInfo table below                                              |
| otcOriginatorBehalfInfo                    | JsonArray |                            | Optional | [{}],if onBehalfIndicator value is 1, must provide this arrayList  | See otcOriginatorBehalfInfo table below                                        |
#### CompleteAction

| Name                                | Type      | Salesforce Key          | Crypto   | Fiat     | Example                                                                                   | Description                                           |
|-------------------------------------|-----------|-------------------------|----------|----------|-------------------------------------------------------------------------------------------|-------------------------------------------------------|
| dispositionTypeCode                 | Integer   |                         | Required | Required | 17                                                                                        | See table provide above                               |
| dispositionTypeOther                | String    |                         | Optional | Optional | "Test Case"                                                                               | If dispositionTypeCode is 11, must provide this value |
| benefitingUsername(new)             | String    |                         | Optional | Optional | "patrick"                                                                                 |                                                       |
| platformToClientHash                | String    | Transaction Hash        | Required | NO       | "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d2468c"                      |                                                       |
| platformToClientSendingWalletList   | JsonArray | Address                 | Required | NO       | "0x780bb33836f0bdec4138c39348979eec739757d6"                                              |                                                       |
| platformToClientReceivingWalletList | JsonArray | Address                 | Required | NO       | ["0xedac0397ceded9abfbd70ba7625db03067e9cb0c",0xedac0397ceded9abfbd70ba7625db03067e9cb0a] |                                                       |
| counterCurrency                     | String    | Counter Currency        | Required | NO       | "USDC"                                                                                    |                                                       |
| counterCurrencyAmount               | String    | Counter Currency Amount | Required | NO       | "61215.320000",                                                                           |                                                       |
| counterCurrencyCanadianExchangeRate | String    | Current crypto price    | Required | NO       | "1.0000000000"                                                                            |                                                       |
| financialInstitutionNumber          | String    | Institution Number      | NO       | Required | "004"                                                                                     |                                                       |
| branchNumber                        | String    | Transit Number          | NO       | Required | "13282"                                                                                   |                                                       |
| accountHolderUsername(new)          | String    | Transit Number          | NO       | Optional | "patrick"                                                                                 |                                                       |
| accountNumber                       | String    | Account Number          | NO       | Required | "6119164"                                                                                 |                                                       |
| accountCurrencyTypeCode             | String    | Fiat Currency           | NO       | Required | "CAD"/"USD"/"EUR"                                                                         |                                                       |
| accountTypeCode                     | Integer   |                         | NO       | Required | 1                                                                                         | 1 Personal 2 Business 3 Trust 5 Casino 4 Other        |
| accountTypeOther                    | String    |                         | NO       | Optional | "Corporate"                                                                               | If type code is 4, must provide this value            |  
| fiatCurrency                        | String    | Fiat Currency           | NO       | Required | "CAD"                                                                                     |                                                       |
| referenceNumber(new)                | String    |                         | NO       | Optional | "123456789"                                                                               |                                                       |
| otherRelatedNumber(new)             | String    |                         | NO       | Optional | "WF123456789"                                                                             | If dispositionTypeCode is 25, must provide this value |

#### StartAction

| Name                                     | Type      | Salesforce Key   | Required | Example                                                                                     | Description        |
|------------------------------------------|-----------|------------------|----------|---------------------------------------------------------------------------------------------|--------------------|
| clientToPlatformHash                     | String    | Transaction Hash | Required | "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d2468c"                        |                    |
| clientToPlatformSendingWalletList(new)   | JsonArray | Address          | Required | "0x780bb33836f0bdec4138c39348979eec739757d6"                                                |                    |
| clientToPlatformReceivingWalletList(new) | JsonArray | Address          | Required | ["0xedac0397ceded9abfbd70ba7625db03067e9cb0c","0xedac0397ceded9abfbd70ba7625db03067e9cb0c"] |                    |
| baseCurrency                             | String    |                  | Required | "USDT"                                                                                      |                    |
| subTransactionTime(new)                  | String    |                  | Optional | "1646191191000"                                                                             | 13 digital numbers |
| baseCurrencyCanadianExchangeRate         | String    |                  | Required | "1.235680"                                                                                  |                    |
| subAmount                                | String    |                  | Required | "61325.000000"                                                                              |                    |



#### otcOriginatorInfo


| Name                                   | Type    | Salesforce Key                | Individual | Corporate | Example                              | Description                                             |
|----------------------------------------|---------|-------------------------------|------------|-----------|--------------------------------------|---------------------------------------------------------|
| perOrEntity                            | Integer |                               | Required   | Required  | 1 or 2                               | 1. Individual 2. entity                                 |
| entityName                             | String  | Name                          | NO         | Required  | "Virgocx"                            |                                                         |
| firstName                              | String  | First Name                    | Required   | NO        | "Adam"                               |                                                         |
| middleName                             | String  | Middle Name                   | Optional   | NO        |                                      |                                                         |
| lastName                               | String  | Last Name                     | Required   | NO        | "Cai"                                |                                                         |
| unitNum                                | String  | Unit Number                   | Optional   | Optional  |                                      |                                                         |
| buildingNum                            | String  | Building Number               | Required   | Required  | "45"                                 |                                                         |
| streetAddress                          | String  | Street Address                | Required   | Required  | "Sheppard Ave"                       |                                                         |
| city                                   | String  | City                          | Required   | Required  | "Toronto"                            |                                                         |
| district                               | String  | District                      | Optional   | Optional  | "North York"                         |                                                         |
| countryCode                            | String  | Country Abbr                  | Required   | Required  | "CA"                                 |                                                         |
| province                               | String  | Province Abbr                 | Required   | Required  | "ON"                                 | If don't have specific value, use "Unknown"             |
| postalCode                             | String  | Postal Code                   | Required   | Required  | "A1E4S2"                             | US version:60606,5 numbers is ok                        |
| telephoneNumber                        | String  | Phone                         | Required   | Required  | "41612345678"                        |                                                         |
| telephoneExtension(new)                | String  |                               | Optional   | Optional  |                                      |                                                         |
| birthday                               | String  | Date of birth                 | Required   | NO        | "1989-02-23"                         |                                                         |
| residenceCountryCode                   | String  | Country of residence Abbr     | Required   | NO        | "CA"                                 |                                                         |
| occupation                             | String  | Title/Role                    | Required   | NO        | "Project manager"                    |                                                         |
| employerName(new)                      | String  |                               | Optional   | NO        | "Virgocx.INC"                        |                                                         |
| idType                                 | String  | ID Type                       | Required   | Required  | "PASSPORT"/"ARTICLES_OF_ASSOCIATION" | Please provide value depend on ID type table list above |
| idNum                                  | String  | ID Number                     | Required   | Required  | "G520123456"                         |                                                         |
| identificationJurisdictionCountryCode  | String  | ID Jurisdiction Country Abbr  | Required   | Required  | "CA"                                 |                                                         |
| identificationJurisdictionProvinceCode | String  | ID Jurisdiction Province Abbr | Required   | Required  | "ON"                                 | If don't have specific value, use "Unknown"             |
| businessNature(new)                    | String  |                               | NO         | Optional  | "Trading platform"                   |                                                         |
| registrationNumber                     | String  | Register Number               | NO         | Required  | "ON51222012"                         |                                                         |
| registrationJurisdictionCountryCode    | String  | Registration Country Abbr     | NO         | Required  | "CA"                                 |                                                         | 
| registrationJurisdictionProvinceCode   | String  | Registration Province Abbr    | NO         | Required  | "ON"                                 | If don't have specific value, use "Unknown"             | 


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
| province                               | String  | Province Abbr                 | Required   | Required  | "ON"                                 | If don't have specific value, use "Unknown"                                                                                                                                        |
| postalCode                             | String  | Postal Code                   | Required   | Required  | "A1E4S2"                             | US version:60606,5 numbers is ok                                                                                                                                                   |
| telephoneNumber                        | String  | Phone                         | Required   | Required  | "41612345678"                        |                                                                                                                                                                                    |
| birthday                               | String  | Date of birth                 | Required   | NO        | "1989-02-23"                         |                                                                                                                                                                                    |
| residenceCountryCode                   | String  | Country of residence Abbr     | Required   | NO        | "CA"                                 |                                                                                                                                                                                    |
| occupation                             | String  | Title/Role                    | Required   | NO        | "Project manager"                    |                                                                                                                                                                                    |
| idType                                 | String  | ID Type                       | Required   | Required  | "PASSPORT"/"ARTICLES_OF_ASSOCIATION" | Please provide value depend on ID type table list above                                                                                                                            |
| idNum                                  | String  | ID Number                     | Required   | Required  | "G520123456"                         |                                                                                                                                                                                    |
| identificationJurisdictionCountryCode  | String  | ID Jurisdiction Country Abbr  | Required   | Required  | "CA"                                 |                                                                                                                                                                                    |
| identificationJurisdictionProvinceCode | String  | ID Jurisdiction Province Abbr | Required   | Required  | "ON"                                 | If don't have specific value, use "Unknown"                                                                                                                                        |
| registrationNumber                     | String  | Register Number               | NO         | Required  | "ON51222012"                         |                                                                                                                                                                                    |
| registrationJurisdictionCountryCode    | String  | Registration Country Abbr     | NO         | Required  | "CA"                                 |                                                                                                                                                                                    |
| registrationJurisdictionProvinceCode   | String  | Registration Province Abbr    | NO         | Required  | "ON"                                 | If don't have specific value, use "Unknown"                                                                                                                                        |
| relationshipTypeCode                   | Integer |                               | Required   | Required  | 4                                    | 1. Accountant 2. Agent 10. Legal counsel 3. Borrower 4. Broker 11. Employer 5. Customer 6. Employee 7. Friend 8. Relative 12. Joint/Secondary owner 13. Power of attorney 9. Other |
| relationshipTypeOther                  | String  |                               | Optional   | Optional  | "Unknown" OR "Couple" OR "Wife"      | If relationShipTypeCode is 4, must provide this value                                                                                                                              |
```
Sample json here, crypto-crypto example 1,conductorIndicator is 1 and onbehalfIndictor is 1 and both of them are individual type
{
    "otcAccountNumber":"C1234",
    "transactionId":"C1488",
    "transactionMethodTypeCode":7,
    "transactionMethodTypeOther":"WhatsApp",
    "conductorIndicator":1,
    "onBehalfIndicator":0,
    "qty":"888888.320000",
    "totalValueInCad":"81024.600000",
    "deviceTypeCode": 3,
    "deviceTypeOther": "",
    "deviceIdentificationNumber": "03e73331cd0f94093a4bb22dfdb3baee",
    "deviceIpAddress": "24.16.223.12",
    "transactionTime":"1646191191000",
    "institutionCode":1,
    "otcRechargeStartActionsList":[
       {
             "clientToPlatformHash":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "clientToPlatformSendingWalletList":["0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673"],
             "clientToPlatformReceivingWalletList":["0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d241111"],
             "baseCurrency":"USDT",
             "subTransactionTime":"1646191191000",
             "baseCurrencyCanadianExchangeRate":"1.23450000",
             "subAmount":"61215.320000"
       }
    ],
    "otcRechargeCompleteActionsList":[
       {
             "dispositionTypeCode":17,
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d24987",
             "platformToClientSendingWalletList":["0x780bb33836f0bdec4138c39348979eec739757d6"],
             "platformToClientReceivingWalletList":["0xedac0397ceded9abfbd70ba7625db03067e9cb0c"],
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"31215.320000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000",
             "benefitingUsername":"patrick"
       },
       {
             "dispositionTypeCode":17,
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d24987",
             "platformToClientSendingWalletList":["0x780bb33836f0bdec4138c39348979eec739757d6"],
             "platformToClientReceivingWalletList":["0xedac0397ceded9abfbd70ba7625db03067e9cb0c"],
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"30000.000000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000",
             "benefitingUsername":"patrick"
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
            "telephoneExtension":"008",
            "birthday":"1989-02-23",
            "residenceCountryCode":"CA",
            "occupation":"Developer",
            "employerName":"Virgocx",
            "idType":"PASSPORT",
            "idNum":"G51213456",
            "identificationJurisdictionCountryCode":"CA",
            "identificationJurisdictionProvinceCode":"ON"        
        }
    ],
    "otcOriginatorBehalfInfo":[]
}

Sample json here, crypto-crypto example 2,conductorIndicator is 1 and onbehalfIndictor is 1 and both of them are corporate type
{
    "otcAccountNumber":"C1234",
    "transactionId":"C1469",
    "transactionMethodTypeCode":8,
    "conductorIndicator":1,
    "onBehalfIndicator":1,
    "qty":"61215.320000",
    "totalValueInCad":"81024.600000",
    "deviceTypeCode": 3,
    "deviceTypeOther": "",
    "deviceIdentificationNumber": "03e73331cd0f94093a4bb22dfdb3baee",
    "deviceIpAddress": "24.16.223.12",
    "transactionTime":"1646191191000",
    "institutionCode":1,
    "otcRechargeStartActionsList":[
       {
             "clientToPlatformHash":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "clientToPlatformSendingWalletList":["0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673"],
             "clientToPlatformReceivingWalletList":["0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d241111"],
             "baseCurrency":"USDT",
             "subTransactionTime":"1646191191000",
             "baseCurrencyCanadianExchangeRate":"1.23450000",
             "subAmount":"61215.320000"
       },
       {
             "clientToPlatformHash":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "clientToPlatformSendingWalletList":["0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673"],
             "clientToPlatformReceivingWalletList":["0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d241111"],
             "baseCurrency":"USDT",
             "realTimeStamp":"1646191191000",
             "baseCurrencyCanadianExchangeRate":"1.23450000",
             "subAmount":"31215.320000"
       },
    ],
    "otcRechargeCompleteActionsList":[
       {
             "dispositionTypeCode":11,
             "dispositionTypeOther":"Test case",
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673",
             "platformToClientSendingWalletList":["0x780bb33836f0bdec4138c39348979eec739757d6"],
             "platformToClientReceivingWalletList":["0xedac0397ceded9abfbd70ba7625db03067e9cb0c"],
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"61215.320000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000",
             "benefitingUsername":"patrick"
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
            "businessNature":"Trading platform",
            "registrationNumber":"ON12345678",
            "registrationJurisdictionCountryCode":"CA",
            "registrationJurisdictionProvinceCode":"ON",
            "telephoneNumber":"4165818505",
            "telephoneExtension":"008",
            "idType":"ARTICLES_OF_ASSOCIATION",
            "idNum":"G51213456",
            "identificationJurisdictionCountryCode":"CN",
            "identificationJurisdictionProvinceCode":"Unknown"
            
        }
    ],
    "otcOriginatorBehalfInfo":[]
}

Sample json here, crypto-fiat example 3,conductorIndicator is 0 and onbehalfIndictor is 0
{
    "otcAccountNumber":"C1234",
    "transactionId":"C1470",
    "transactionMethodTypeCode":8,
    "conductorIndicator":0,
    "onBehalfIndicator":0,
    "qty":"61215.320000",
    "totalValueInCad":"81024.600000",
    "deviceTypeCode": 3,
    "deviceTypeOther": "",
    "deviceIdentificationNumber": "03e73331cd0f94093a4bb22dfdb3baee",
    "deviceIpAddress": "24.16.223.12",
    "transactionTime":"1646191191000",
    "institutionCode":"2",
    "otcRechargeStartActionsList":[
       {
             "clientToPlatformHash":"0x780bb33836f0bdec4138c39348979eec739757d6",
             "clientToPlatformSendingWalletList":[
                  "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673",
                  "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246674"
             ],
             "clientToPlatformReceivingWalletList":[
                  "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d241111",
                  "0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d241112"
             ]
             "baseCurrency":"USDT",
             "subTransactionTime":"1646191191000",
             "baseCurrencyCanadianExchangeRate":"1.23450000",
             "subAmount":"61215.320000"
       }
    ],
    "otcRechargeCompleteActionsList":[
       {
             "dispositionTypeCode":17,
             "platformToClientHash":"0xcefd143db7a1c20e49cebf7bfa75ac7f1d4779e38ed3e011da38379b89d246673",
             "platformToClientSendingWalletList":[
                  "0x780bb33836f0bdec4138c39348979eec739757d6",
                  "0x780bb33836f0bdec4138c39348979eec739757d7"
             ]
             "platformToClientReceivingWalletList":[
                  "0xedac0397ceded9abfbd70ba7625db03067e9cb0c",
                  "0xedac0397ceded9abfbd70ba7625db03067e9cb01"
             ]
             "counterCurrency":"USDC",
             "counterCurrencyAmount":"61215.320000",
             "counterCurrencyCanadianExchangeRate":"1.0000000000",
             "benefitingUsername":"patrick"
       },
       {
             "dispositionTypeCode":25,
             "financialInstitutionNumber":"004",
             "branchNumber":"13282",
             "accountHolderUsername":"patrick",
             "accountNumber":"6119164",
             "accountCurrencyTypeCode":"CAD",
             "accountTypeCode":1,
             "fiatCurrency":"CAD",
             "benefitingUsername":"patrick",
             "referenceNumber":"123455",
             "otherRelatedNumber":"WF1234455612"
       }
    ],
    "otcOriginatorInfo":[],
    "otcOriginatorBehalfInfo":[]
}
```

---
