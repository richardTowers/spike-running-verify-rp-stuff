.PHONY: all
all: signing-private-key.pk8 signing-certificate.crt encryption-private-key.pk8 encryption-certificate.crt

.PHONY: clean
clean:
	rm -f *.*

%.pk8: %.pem
	openssl pkcs8 -topk8 -inform PEM -outform DER -in $< -nocrypt -out $@

%.crt: %.pem
	openssl req -batch -new -subj "/CN=$$RANDOM" -key $< | openssl x509 -req -sha256 -signkey $< -out $@

%.pem:
	openssl genrsa -des3 -passout pass:x 2048 | openssl rsa -passin pass:x -out $@
