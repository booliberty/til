Re-encoding Certificates
========================

While this isn't too difficult to gather from the openssl man page, I do it
frequently enough to merit a brief snippit.  

My understanding of the two most basic forms of X509 certificate encoding are
PEM and DER.  
  
__PEM__ is typically described as an application of base64 encoding to ASCII
certificate files.  PEM certificate file extensions are not strictly observed,
and are conventional, with the most common being .pem, .cer, and .crt.  These
expect each cert blob to be surround by "BEGIN CERTIFICATE/END CERTIFICATE"
headers/footers.  Basic text concatenation is an acceptable form of bundling.  
  
__DER__ is the certificate data represented as binary.  .der is the most common
extension for these, but I've seen plenty of DER-encoded cert files named .cer
or .crt.  There are no human-readable headers/footers, and I'm not sure how
bundling works

        openssl x509 -in <cert.pem> -inform PEM -out <cert.der> -outform DER

This uses the __x509__ command with a certificate (bundle) file as __in__put,
and generates a cert file as __out__put.  
__inform__ and __outform_ describe incoming and outgoing encoding.  
The __text__ argument prints full certificate details in human readable text.  
  
There are also more complex formats like P7B (PKCS7), PKCS8, PFX, and PKCS12.
These are primariliy meant for bundling complete keypairs and chains, and they
support (and in many contexts, require) passwords on private keys and bundles.  
__P7B__ does not support bundling private keys.  It's base64, and is readable
by Tomcat.  Expected file extensions are .p7b and .p7c.
__PKCS8__ is described a way of bundling PEM-encoded keypairs with or without
encryption.
__PKCS12__ and __PFX__ are often described as interchangeable because openssl
and some related tools will treat them as such.  The encoding is not identical,
though.  Expected extensions are .p12 and .pfx.  PFX is a very common standard
on Microsoft systems.  openssl treats them the same way.  Most versions of
keytool I've encountered support p12 bundles with near-parity to the native
java __keystore__ format, but don't necessarily offer the same support for PFX.
I don't really understand the specific differences between these two.  These
are frequently used for bundling an entire certificate chain and private key
with encryption.  
  
        openssl crl2pkcs7 -nocrl -certfile certificatename.pem -out certificatename.p7b -certfile CACert.cer  
        openssl pkcs7 -print_certs -in certificatename.p7b -out certificatename.pem  
        openssl pkcs12 -in certificatename.pfx -out certificatename.pem  
        openssl pkcs12 -in certificatename.pfx -nocerts -nodes -out certificatename.pem  
        openSSL pkcs8 -in certificatename.pem -topk8 -nocrypt -out certificatename.pk8  
        openssl pkcs7 -print_certs -in certificatename.p7b -out certificatename.cer  
        openssl pkcs12 -export -in certificatename.cer -inkey privateKey.key -out certificatename.pfx -certfile  cacert.cer  
  
https://www.openssl.org/docs/manmaster/apps/x509.html
