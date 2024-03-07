# Simple TicTacToe using socket programming in python

## To play the game :

- Clone the repo
- Make sure you have openssl installed
- Genrate the self-signed certificates needed

### To generate the certificates :

- Generating a self-signed certificate for server
  - use your IP in the field 
    ```
    openssl req -x509 -newkey rsa:4096 -keyout server-key.pem -out server-signed-cert1.pem -days 365 -nodes -subj "/CN=example.com" -addext "subjectAltName = IP:127.0.0.1"
    ```

- Generating Client certificate :
  - Generate the client private key:

    ```bash
    openssl genpkey -algorithm RSA -out client-key.pem
    ```

  - Generate a CSR   the client:

    ```bash
    openssl req -new -key client-key.pem -out client-csr.pem
    ```

  - Sign the client certificate with the CA:

    ```bash
    openssl x509 -req -in client-csr.pem -CA ca-cert.pem -CAkey ca-key.pem -out client-cert.pem
    ```

  - Generating the ca-file.pem:

    ```
    cat server-signed-cert.pem server-key.pem > ca-file.pem
    ```
    


