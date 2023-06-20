
openssl req -new -newkey rsa:4096  -passin pass:changeit -keyout localhost.key -out localhost.csr -nodes

openssl x509 -req  -passin pass:changeit -CA rootCA.crt -CAkey rootCA.key -in localhost.csr -out localhost.crt -days 365 -CAcreateserial -extfile localhost.ext
openssl pkcs12 -export -in localhost.crt -inkey localhost.key -out keystore.p12 -name "server certificate" -chain -CAfile rootCA.crt -caname "self signed ca certificate" -passin pass:changeit -passout pass:changeit
