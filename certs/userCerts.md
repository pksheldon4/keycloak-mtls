openssl req -new -newkey rsa:4096 -nodes -keyout cwest.key -out cwest.csr
openssl x509 -req -CA rootCA.crt -CAkey rootCA.key -in cwest.csr -out cwest.crt -days 365 -CAcreateserial
openssl pkcs12 -export -out cwest.p12 -name "cwest" -inkey cwest.key -in cwest.crt -legacy

