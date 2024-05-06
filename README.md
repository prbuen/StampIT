# StampIT
An app to cryptographically timestamp computer files such as assessment items.

The aim of this app is to make assessment submission reliable independently of:
- learning management system server outages and server bottlenecks at universal submission times
- internet dropping out during submission (e.g. large files)
- student error (e.g. uploading the wrong assignment)

This app was initially developed at the Queensland University of Technology (QUT), Brisbane, Australia.

## How it works
1. Get a certificate from a time stamping authority (TSA) (=public key)
2. Hash the student submission data (one or several files) and send the hash to the TSA
3. TSA returns a receipt for the hash, encrypted with their public key
4. Verification of student submission timestamps (e.g. by the unit coordinator) unencrypts the receipt using the TSA public key

## Usage
### Stamp
1. Select files by browsing or drag and drop, then click "StampIT":
   ![stamp1](https://github.com/prbuen/StampIT/assets/54585460/2f771b88-ea76-4a8e-b8ea-cbe815234c58)
2. The .zip returned contains all the files stamped and the TSA receipt (incl. metadata such as TSA name)
   ![stamp2](https://github.com/prbuen/StampIT/assets/54585460/6ea29488-c3d9-4878-891b-f73bccfd959c)

### Verify stamp
Bulk verification of timestamps is possible. Select timestamp .zip files and click "Verify":
![verifystamp1](https://github.com/prbuen/StampIT/assets/54585460/c45525cf-627b-4b1c-b8c9-8e0c865e6437)

Valid and invalid timestamps examples (Stamped2.zip was updated after the timestamp was created):
![verifystamp2](https://github.com/prbuen/StampIT/assets/54585460/a109dd68-717b-433a-b725-c9afaf1b9474)

## Current limitations
- Implementation is based on Sha1 and the RFC3161 protocol, which has limitations. *Future:* implement RFC5816 for using other hashes such as Sha256.
- Does not account for how lon the TSA certificate is valid for (=> only short term use)
- TSA used for world clock is http://freetsa.org. *Future:* make customisable.
- The look and feel of the app is based on QUT. *Future:* make customisable.

## Authors
Liam Ferrante and Pascal R Buenzli

## Acknowledgments
QUT Mathematical Sciences Fund for Teaching and Research 2022
