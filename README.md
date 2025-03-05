This is a very simple setup for frigate nvr and homeassistant for notifications.
It was cobbled together for a temporary setup and is in no way suited for a permanenet deployment.
Also, it is not really secure!
However, it should provide a decent starting point if you need something relatively quickly.
Additional benefit of this setup is, that you can zip everything up and mvoe it to another system since the runtime config of the apps is put in this folder structure.

Frigate is exposed over https://127.0.0.1:8971/ and homeassistant over http://127.0.0.1:8123/.
A MQTT broker to connect the two is available automatically.
An NTP server is also included, so you can point your security cameras here if they are in their own ip range and need an NTP server.

This repo contains no configuration, just the docker stuff.

This might not be a ready to use soution, since also the docker config is dependent on what you have.
E.g. the devices access is hardcoded to the coral usb device and renderD128 for the gpu acceleration for ffmpeg.

To allow notifications over the internet, connect your phone and HA with Tailscale.
That is a very simple solution.

## Configuring homeassistant

Follow the standard setup over at https://docs.frigate.video/integrations/home-assistant/ (if I remember correctly).

To configure MQTT in HA, use `localhost` as broker and `1883` as port.
For the frigate integration use `http://localhost:5000`.

Friate stuff should then show up in HA.

For notifications, you can follow this: https://community.home-assistant.io/t/frigate-mobile-app-notifications-2-0/559732

## Maybe helpful commands

Start (temporarily) with `docker compose up`.

Start "permanently" with `docker compose up -d`.

Stop with `docker compose down`.

List interfaces and addresses with `ip a`.

Add a new address range to an interface with `ip addr add 10.0.0.100/24 dev enp9s0` temporarily.
Use something like `nmtui` if you have network manager for your networking. (If not, good luck!)

