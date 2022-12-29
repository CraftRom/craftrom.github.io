---
sidebar: home_sidebar
title: How to add a new device 
folder: internal
permalink: addingdevice-howto.html
search: exclude
tags:
 - internal
---

## Adding your device

### Prepare the required files

There are a few files which need to be there to have a device on the wiki.
In order to get them, navigate to `CraftRom/craftrom.github.io` and run:

```
./scripts/generate_device.sh your_device
```

Obviously replace `your_device` with the codename of your device

### Populating the YAML

The sample template has been copied to `$LINEAGE_SRC/lineage/wiki/_data/devices/your_device.yml`.
Update the values to match your device. An explanation of some of the options is below.

Some of the properties allow specifying different values for multiple models being covered in the same file.
In that case the format stays the same as for a single device, but is used in a Key-Value style like this:

```
property:
- Model1: Value
- Model2: Value
```

An example using the `battery` property:
Just one device:

```
battery: {removable: False, capacity: 1000, tech: 'Li-Ion'}
```

vs. two different models:

```
battery:
- Model1: {removable: False, capacity: 1000, tech: 'Li-Ion'}
- Model2: {removable: True, capacity: 2000, tech: 'Li-Po'}
```

The following list will mention Model-Value pairs where applicable.

#### List of properties

{% assign definitions = site.data.schema.definitions %}
{% assign properties = site.data.schema.properties %}

* `architecture`: The CPU architecture of the device, can be one of

  ```
  {{ definitions.valid_architectures.enum | join: ', ' }}
  ```

  If your device has a 64 bit architecture but Android runs on 32 bit, you can use a different format: `{cpu: 'arm64', userspace: 'arm'}`

* `battery`: Use the format `{removable: False, capacity: <number in mAh>, tech: '<tech>'}`. If your battery is removable, use `True` instead.
  For `tech` you can use:

  ```
  {{ definitions.battery_data.properties.tech.enum | join: ', ' }}
  ```

  This property supports Model-Value pairs.

* `bluetooth`: The proper format is either `{spec: '<version>'}` with `version` being the version of the BT protocol supported, or `{spec: '<version>', profiles: '<profiles>'}` when your device
  supports additional profiles. These are the possible values:

  ```
  For the specification:
  {{ properties.bluetooth.properties.spec.enum | join: ', ' }}

  For the optional profiles:
  {{ properties.bluetooth.properties.profiles.items.enum | join: ', ' }}
  ```

* `camera`: One entry for each camera in the format

   ```
   - {flash: '<flash>', info: 'x MP'}
   ```

  with `flash` being one of
  ```
  {{ definitions.camera_data.properties.flash.enum | join: ', ' }}
  ```
  and `info` in the format `x MP` or `x MP (wide)` (wide, ultrawide, depth, etc. can be used), or `x MP (Model1) or x MP (Model2)` if necessary

* `cpu`: The CPU type of the device, can be one of the following list:

  ```
  {{ properties.cpu.enum | join: ", " }}
  ```

* `dimensions`: Use the format `{width: '', height: '', depth: ''}` with `123 mm (12.3 in)` being the proper format for each of them (including the exact whitespaces!).

  This property supports Model-Value pairs.

* `download_boot`: Instructions for booting the device into the mode used to install recovery. On most devices, this is fastboot mode.
* `image`: The image located under `images/devices/` to use for this device. Instructions on adding an image <a href="#adding-the-devices-image">can be found below</a>.
* `install_method`: Used to determine the recovery install template to use. Templates can be found in *_includes/templates/recovery_install_*`install_method`*.md* and must be one of:

  ```
  {{ properties.install_method.enum | join: ", " }}
  ```

* `kernel`: The repo name of the kernel - for example, `android_kernel_oneplus_msm8974`.
* `network`: The frequencies and channels for the various network technologies. You can look them up [here](https://www.frequencycheck.com/models/). Keep the non-available technologies empty.
* `peripherals`: A list of peripherals available on the device, can be any of the following list:

  ```
  {{ definitions.valid_peripherals.items.enum | join: ", " }}
  ```

* `release`: Allowed formats are `yyyy`, `yyyy-mm` and `yyyy-mm-dd`. This property supports Model-Value pairs.

* `screen`: Use `{size: '<screen size>', density: <number>, resolution: '<1234x567>', technology: ''}` with `123 mm (12.3 in)` as the proper format for `size`,
  a number for `density`, `1234x567` for `resolution` and a string for `technology`.
  Please look at other devices in order to use the same names for same technologies across all devices!

  This property supports Model-Value pairs.

* `tree`: The repo name of the device tree - for example, `android_device_oneplus_bacon`.
* `vendor_short`: The vendor name used for the device tree - for example, `oneplus`.

### Adding the device's image

Find a reasonably high-quality image of your device, and add it to `images/devices/<image>.png`. The filename must match the
entry in your YAML file. Also make sure the background of the image is transparent.

## Testing it works

Start the wiki on your local Jekyll server, and navigate to [the devices list](http://localhost:4000/devices.html). Your device should be there.
Click on it, and check that the info/install/build pages all seem correct.

Now run the validation:

```
bundle install
ruby ./test/validate.rb
```

If the script doesn't give you an output, all the validated fields have a proper format. Otherwise, read the messages carefully to see which fields have to be corrected.