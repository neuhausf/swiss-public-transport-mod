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

## Privacy 

This integration uses :

- the changes made in the pull request by @agners: https://github.com/home-assistant/core/pull/30715
- and some own code to make it work with never home assistant versions