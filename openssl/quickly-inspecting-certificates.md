Using OpenSSL To Quickly Inspect a Certificate File
===================================================

While this isn't too difficult to gather from the openssl man page, I do it
frequently enough to merit a brief snippit.  

        openssl x509 -in <cert.pem> -noout -text

This uses the __x509__ command with a certificate (bundle) file as __in__put.  
The __noout__ argument indicates that this is not an encoding operation, so no
output file is expected.  
The __text__ argument prints full certificate details in human readable text.  

https://www.openssl.org/docs/manmaster/apps/x509.html
