Tests:

1: Successful. Includes all requires Keys

mosquitto_pub -h localhost -p 8883 --cafile pki/root_ca.crt \
  --cert clients/sensor-02.crt --key clients/sensor-02.key \
  -t sensor/sensor-02/data -m '{"temp":21.5}'


2: Fails. No client info for TLS handshake

mosquitto_pub -h localhost -p 8883 --cafile pki/root_ca.crt -t test -m hi


3: Fails. Cert name is "localhost", doesn't match.

mosquitto_pub -h 127.0.0.1 -p 8883 --cafile pki/root_ca.crt \
  --cert clients/sensor-01.crt --key clients/sensor-01.key -t test -m hi
