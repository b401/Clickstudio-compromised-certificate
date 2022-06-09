# Compromised clickstudio certificate

__Extracted from__: f3ccf22db2c1060251096fe99464002318baccf598b626f8dbdd5e7fd71fd23f  
__Serial__: 0394517DACDC71187A40001B5CC32DE5  
__Signer Hash__: 79bae9ba9b80cd349ebe9a4165224e816f3b597c


## Certificate information

```
Current PE checksum   : 00014A49
Calculated PE checksum: 00014A49

Signature Index: 0  (Primary Signature)
Message digest algorithm  : SHA1
Current message digest    : 893A44297C46442A76C85D32D3107DAF2F28C096
Calculated message digest : 893A44297C46442A76C85D32D3107DAF2F28C096

Signer's certificate:
	Signer #0:
		Subject: /C=AU/ST=South Australia/L=Adelaide/O=Click Studios (SA) Pty Ltd/CN=Click Studios (SA) Pty Ltd
		Issuer : /C=US/O=DigiCert Inc/OU=www.digicert.com/CN=DigiCert SHA2 Assured ID Code Signing CA
		Serial : 0394517DACDC71187A40001B5CC32DE5
		Certificate expiration date:
			notBefore : Oct 26 00:00:00 2020 GMT
			notAfter : Dec 12 23:59:59 2023 GMT
...
```

## Advanced Hunting query

```
DeviceFileCertificateInfo
| where CertificateSerialNumber == "0394517dacdc71187a40001b5cc32de5"
| join DeviceFileEvents on SHA1
| sort by Timestamp
| project Timestamp, DeviceName, FolderPath, SHA256, InitiatingProcessAccountName
```
