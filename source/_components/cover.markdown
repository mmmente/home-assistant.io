---
layout: page
title: "Covers"
description: "Instructions on how to integrate covers into Home Assistant."
date: 2016-06-28 17:30
sidebar: true
comments: false
sharing: true
footer: true
---

Home Assistant can give you an interface to control covers such as rollershutters, blinds, and garage doors.

The display style of each entity can be modified in the [customize section](/getting-started/customizing-devices/). Besides the basic ones like `friendly_name` or `hidden`, the following attributes are supported for covers:
 
| Attribute | Default | Description |
| --------- | ------- | ----------- |
| `device_class` | | see below
| `assumed_state` | `false` | If set to `true`, cover buttons will always be enabled

### {% linkable_title Device Class %}

The way these sensors are displayed in the frontend can be modified in the [customize section](/docs/configuration/customizing-devices/). The following device classes are supported for covers:

- **None**: Generic cover. This is the default and doesn't need to be set.
- **awning**: Control of an awning, such as an exterior retractable window, door, or patio cover.
- **blind**: Control of blinds, which are linked slats that expand or collapse to cover an opening or may be tilted to partially covering an opening, such as window blinds.
- **curtain**: Control of curtains or drapes, which is often fabric hung above a window or door that can be drawn open.
- **damper**: Control of a mechanical damper that reduces airflow, sound, or light.
- **door**: Control of a door or gate that provides access to an area.
- **garage**: Control of a garage door that provides access to a garage.
- **shade**: Control of shades, which are a continuous plane of material or connected cells that expanded or collapsed over an opening, such as window shades.
- **shutter**: Control of shutters, which are linked slats that swing out/in to covering an opening or may be tilted to partially cover an opening, such as indoor or exterior window shutters.
- **window**: Control of a physical window that opens and closes or may tilt.

## {% linkable_title Services %}

### {% linkable_title Cover control services %}

Available services: `cover.open_cover`, `cover.close_cover`, `cover.stop_cover`, `cover.open_cover_tilt`, `cover.close_cover_tilt`, `cover.stop_cover_tilt`

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | yes | String or list of strings that point at `entity_id`'s of covers. Else targets all.

### {% linkable_title Service `cover.set_cover_position` %}

Set cover position of one or multiple covers.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | yes | String or list of strings that point at `entity_id`'s of covers. Else targets all.
| `position` | no | Integer between 0 and 100.

#### {% linkable_title Automation example  %}

```yaml
automation:
  trigger:
    platform: time
    at: "07:15:00"
  action:
    - service: cover.set_cover_position
      data:
        entity_id: cover.demo
        position: 50
```

### {% linkable_title Service `cover.set_cover_tilt_position` %}

Set cover tilt position of one or multiple covers.

| Service data attribute | Optional | Description |
| ---------------------- | -------- | ----------- |
| `entity_id` | yes | String or list of strings that point at `entity_id`'s of covers. Else targets all.
| `position` | no | Integer between 0 and 100.

#### {% linkable_title Automation example  %}

```yaml
automation:
  trigger:
    platform: time
    at: "07:15:00"
  action:
    - service: cover.set_cover_tilt_position
      data:
        entity_id: cover.demo
        position: 50
```
