[![hacs_badge](https://img.shields.io/badge/HACS-Default-orange.svg)](https://github.com/custom-components/hacs)

# swiss-public-transport-mod
Based on [@agners lovelace card](https://github.com/agners/swiss-public-transport-card "@agners lovelace card"):

Extends the [swiss_public_transport](https://www.home-assistant.io/integrations/swiss_public_transport/ "swiss_public_transport") sensor by a few features required to visualize a proper [stationboard](https://github.com/neuhausf/lovelace-swiss-stationboard "stationboard"):
- `stationboard` property
- `limit` property

@agners implementation depends upon a [pull-request](https://github.com/home-assistant/home-assistant/pull/30715 "pull-request") which was never merged. To simplify the installation of this sensor, I created two HACS repositories (this one and one for the [lovelace-card](https://github.com/neuhausf/lovelace-swiss-stationboard "lovelace-card")).

## Information

**Note:** You can use the data of this sensor on its own or use the custom lovelace-card to visualize a stationboard.

## Configuration

- Got to HACS
- Add a custom repo: https://github.com/neuhausf/swiss-public-transport-mod
- Install it

Add a new sensor to your `configuration.yaml`:

```YAML
sensor:
  - platform: swiss_public_transport_mod
    name: Schüpfen
    limit: 4
    stationboard:
    - Schüpfen
```

Note that you can aggregate multiple starting stations into the same sensor. For example, if multiple, surrounding bus/tram stations are to be included. For each station a `limit` maximum number of connections is fetched:

```YAML
sensor:
  - platform: swiss_public_transport_mod
    name: Bern
    limit: 4
    stationboard:
    - Bern
    - Bern, Hirschengraben
```

In this example, `limit` equals 4, so 4 connections are fetched starting from Bern and 4 connections starting from Bern, Hirschengraben (total 8):

<img src="https://user-images.githubusercontent.com/7963239/218667500-dddbdf45-9b1a-40a6-9c04-83a018d25e26.png" width="300" >
(note that you need the [lovelace-card](https://github.com/neuhausf/lovelace-swiss-stationboard "lovelace-card") to visualize the sensor)


Multiple sensors with completely different output locations are also possible. To do this, simply duplicate the configuration:

```YAML
sensor:
  - platform: swiss_public_transport_mod
    name: Schüpfen
    limit: 4
    stationboard:
    - Schüpfen
  - platform: swiss_public_transport_mod
    name: Langenthal
    limit: 4
    stationboard:
    - Langenthal
```
... this will lead to:

<img src="https://user-images.githubusercontent.com/7963239/218668664-5f6b70ad-6e0a-410b-83a3-c90f174da738.png" width="300" >

## Privacy 

This integration uses :

- the changes made in the pull request by @agners: https://github.com/home-assistant/core/pull/30715
- and some own code to make it work with never home assistant versions
