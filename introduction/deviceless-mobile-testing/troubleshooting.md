# Troubleshooting

Q: My application utilize ssl-pinning, as a result I don't see encrypted traffic.\
A: In that case you must build a development version of your application with one of the options:\
&#x20; (a) disabling ssl-pinning \
&#x20; (b) whitelisting loadmill-mitm-proxy certificate as part of ssl-pinning\
\
Q: After configuring everything, my application is not responding anymore, neither I see traffic.\
A: Make sure the following:\
&#x20; (a) The proxy is started\
&#x20; (b) The proxy port is whitelisted in machine's firewall\
&#x20; (c) Your device and proxy host machine are connected to the same network and the port is allowed by the network.\
&#x20; (d) The application does not utilize ssl-pinning or loadmill-ssl-certificate is whitelisted.
