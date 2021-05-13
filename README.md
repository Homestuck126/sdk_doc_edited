# ITM SPO SDK Sample User Guide

- [ITM SPO SDK Sample User Guide Traditional Chinese Version](./README_zh.md)

## Release Note

- [ITM SPO SDK Release Note](./doc/ReleaseNote.md)

## SPO Server System Architecture Diagram(include Dashboard public version)

![SPO Server System Architecture Diagram](./doc/SPO-Server-System-Architecture-Diagram_en.png)

## Architecture Component Description

### SPO Client

1. Offer SPO Client to clearance for Raw Data：generates and sends LedgerInput to SPO Server and stores Receipt from SPO Server.
2. When SPO Server reports chained Clearance Order, it will verify Receipt and Clearance Record from Smart Contract, and generates result afterward.

### SPO Server

1. Receive SPO Client LedgerInput and return Receipt
2. Clearance LedgerInputs and upload them to Blockchain until it reaches the setting amount. SPO Client will verify when the success message is reported.
3. Search based on Index Value Key and time interval, generates VerificationProof for the following verification by public [Verification Server](https://verification.itrustmachines.com/) or self-integrate [Verification Program].

### Dashboard

Public version of Device data provides the following：

1. Display Raw Data offered by SPO Server.
2. Display audit status of Raw Data and Etherscan(Ethereum Blockchain Browser) link.
3. Receive Proof：Users can search based on Index Value Key and time interval on interface. Dashboard will ask SPO Server for VerificationProof.

- If developers like to show clearance records on ITM publish version of Dashboard, CMD must contain `deviceId` and `timestamp` fields.

### Verification Server

- Provide users who are not intergrating [Verification Program] with public online Verification Server, which include Proof Verification, Raw Data Verification, Recovery Key and Address.
- Verification Server URL : https://verification.itrustmachines.com/

- If developers like to use original file verification function in public [Verification Server](https://verification.itrustmachines.com/) provided by ITM, CMD must add `fileName` and `fileHash` fields.

### [Verification Program]

1. Verify VerificationProof and receive Error Report and Raw Data.

## SDK List

To apply the follow list testing development, feel free to [Contact us](https://itrustmachines.com/).

- [itm-mcu-porting-kit](https://github.com/itrustmachines/itm-mcu-porting-kit) (Need GitHub authorization)
  - Provide Linux C or Azure Sphere SPO Client example code
  - master branches environment requirements：above Ubuntu 18.04 or Centos 7
  - azs-spo-c-client & azs-spo-c-client-single-thread branches environment requirements：
    - Azure Sphere SDK
    - Visual Studio or Visual Studio Code develop environment
    - Windows 10 operating system
- [itm-spo-sdk-java](https://github.com/itrustmachines/itm-spo-sdk-java) (Need GitHub authorization)
  - Provide Java environment SPO Client example code
  - Environment requirements：above Java 8, installed Maven
- [itm-spo-sdk-android](https://github.com/itrustmachines/itm-spo-sdk-android) (Need GitHub authorization)
  - Provide Andriod environment SPO Client example code
  - Environment requirements：
    - above Java 8, installed Maven
    - Android Studio develop environment
- [itm-dashboard](https://github.com/itrustmachines/itm-dashboard) (Need GitHub authorization)
  - Provide publish version of Dashboard example code
  - Environment requirements：above Java 11, installed Maven
