---
sidebar: home_sidebar
title: Craft Rom contributors
permalink: contributors.html
---

{% assign devices = "" | split: " " %}
{% for device in site.data.devices %}
{% assign devices = devices | push: device[1] %}
{% endfor %}
{% assign sorted = devices | sort: 'name' | sort: 'vendor' %}

## Maintainers

### Head Developers (Craft Rom Directors)

These people have responsibility over the direction of the project and are committed to improving it.

| Name | Nickname |
|------|----------|
| Dmytro Galytskyi | melles1991 |
{: .table }

### ExodusOS maintainers

{%- include snippets/branches.md %}
{%- assign versions = "" | split: " " %}
{%- assign versions = versions | push: current_branch %}

{% for version in versions %}

#### ExodusOS (powered by LineageOS) {{ version }}

<table class="table">
<thead>
<tr><th>Device</th><th>Maintainer(s)</th></tr>
</thead>
<tbody>
{%- for device in sorted %}
{%- assign numExMaintainers = device.exodus_maintainers | size %}
{%- if device.current_branch != version or numExMaintainers == 0 %}
{%- continue %}
{%- endif %}
<tr><td><b><a href="{{ "/devices/" | append: device.codename | relative_url }}">{{ device.vendor }} {{ device.name }} ({{ device.codename }})</a></b></td><td>{{ device.exodus_maintainers | join: ', ' }}</td></tr>
{%- endfor %}
</tbody>
</table>
{%- endfor %}

### Chidori Kernel maintainers

<table class="table">
<thead>
<tr><th>Device</th><th>Maintainer(s)</th></tr>
</thead>
<tbody>
{%- for device in sorted %}
{%- assign numMaintainers = device.maintainers | size %}
{%- if numMaintainers == 0 %}
{%- continue %}
{%- endif %}
<tr><td><b><a href="{{ "/devices/" | append: device.codename | relative_url }}">{{ device.vendor }} {{ device.name }} ({{ device.codename }})</a></b></td><td>{{ device.maintainers | join: ', ' }}</td></tr>
{%- endfor %}
</tbody>
</table>

## Telegram

### Chat Administrators and Moderators

Telegram chat administrators have certain administrator rights and can manage users.

| Name | Nickname | Situation |
|------|----------|------|
| Maxim | luckyakalucka | Co-founder |
| Dmitry K | username_DK | Admin |
| Igor | DfP_DEV | Admin |
| Zhenya Landsberg | somersbyscam | Admin |
| --- | forestgun78 | Admin |
| --- | xqwift | Moderator |
{: .table }

### Helpers

The most active users who help other chat users in solving their questions.
In addition, they notify the administration about violations of the chat rules.

| Name | Nickname |
|------|----------|
| --- | guidix_m |
| --- | Ghj8484 |
{: .table }

## Other projects

### Website

These people are responsible for the content of [our website](https://www.craft-rom.pp.ua/):

| Name | Nickname |
|------|----------|
| Dmytro Galytskyi | melles1991 |
{: .table }

### Official app (CraftRom-Manager)

These people are responsible for developing [our app](https://github.com/CraftRom/CraftRom-Manager):

| Name | Nickname |
|------|----------|
| Dmytro Galytskyi | melles1991 |
{: .table }
