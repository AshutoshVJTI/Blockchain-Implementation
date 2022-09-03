# Blockchain Supply Chain POC: COVID-19 Vaccine Passports

1. Goal
Design and implement a system that solves a known problem of trust in the COVID-19 vaccine supply chain.

2. Requirements Gathering

2.1. Vaccine Cold Chain

![image](https://user-images.githubusercontent.com/81223173/188287314-3571eeef-b574-49c3-9a1b-2d4c8df9fc51.png)

Source: Vaccine cold chain Q&A

2.2. System Actors
Manufacturer
process raw materials into vaccines
Distributor
transports vaccines between locations
Inspector
performs quality checks on vaccines
performs quality checks on manufacturing plants
Storage Facility
store vaccines in cold temperatures
Immunizer (the doctors, nurses
vaccinates people
provides vaccine passport/certificates
Traveller (the patient):
receives vaccine
receives vaccine certificate
presents vaccine certificate at the border of the destination country
Border Agent
verifies the vaccine certificates/passports

2.3. Problem-Solution Map

No.
Problems
Affected Actors
Proposed Solutions
1
Vaccine passports can be falsified
Border Agent
Cryptographically verify using on-chain data
2
Key facilities may not meet quality standards
All
Publish inspection results to blockchain
Verify presented inspection results
3
Vaccine passports may not be recognized by destination countries
Distributor
Traveller
Immunizer
Verify signatures in presented certificates


2.4. Why Blockchain?
Tamper-Proof Provenance
does the label on the vaccine’s vial accurately represent its contents?
did the vaccine come from an inspected batch?
Credential Issuance & Verification
cryptographic signatures that are easily verified with on-chain identities
Data Redundancy
the data can’t be lost even if a Traveller “misplaces” their device
the data can’t be lost even if the vials are damaged

3. System Design

3.1. Flow
Inspector issues certificate for batch to Manufacturer
<batch status updated to MANUFACTURED>
Manufacturer presents certificate to Distributor
Distributor verifies each certificate
<batch status updated to DELIVERING_INTERNATIONAL>
Distributor presents updated certificate to Storage Facility
Storage Facility verifies each batch certificate
<batch status updated to STORED>
Storage Facility presents certificates to Distributor
Distributor verifies each certificate
<batch status updated to DELIVERING_LOCAL>
Distributor presents updated certificate to Immunizer
Immunizer verifies certificates
<batch status updated to DELIVERED>
Immunizer vaccinates Traveller and issues vaccine passport
<certificate issued with status VACCINATED>
Traveller presents vaccine passport to Border Agent
Border Agent verifies vaccine passport

3.2. User Classifications
![image](https://user-images.githubusercontent.com/81223173/188287460-0ccba217-7438-41b1-95e1-dea78d98f222.png)


3.3. Use Cases
As an Issuer, I can issue a signature representing a digital certificate for a manufacturer’s plant or storage facility
As a Prover, I can present a certificate/signature issued to me
As a Verifier, I can validate the signature on the blockchain for a vaccine
3.3.1. Out of Scope
Payments between system agents;
Dishonest doctors/immunizers;
Suppliers of raw materials to the manufacturers;
Image capture & QR code scanning;
Scalability;
Distribution to areas without internet access;
IoT;
Machine learning;
Regulatory compliance (e.g. GDPR, HIPAA, etc.); and
Anything not addressed in this video.

3.4. High-level Diagram

3.4.1. 3-Tiered Architecture
![image](https://user-images.githubusercontent.com/81223173/188287464-dc171d22-f3af-4f7a-8209-2ef1353a6af3.png)

3.4.2. 2-Tiered “dApp” Architecture
![image](https://user-images.githubusercontent.com/81223173/188287481-f33c87b4-6da4-4278-9868-9ce9b08b9f21.png)

## References
https://www.bbc.com/news/uk-northern-ireland-58054973
https://www.vanguardngr.com/2021/10/fg-shocked-as-nigeria-loses-out-of-uk-recognised-covid-19-vaccine-certificates/
https://healthpolicy-watch.news/russia-pushes-ahead-with-open-license-approach-to-sputnik-v-despite-who-concerns-over-manufacturing-practices/
