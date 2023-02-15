---
sidebar: home_sidebar
title: Google apps
permalink: gapps.html
---
Google apps are the proprietary Google-branded applications that come pre-installed with most Android devices, such as the Play Store, Gmail, Maps, etc.
Due to licensing restrictions, these apps cannot come pre-installed with some ROM's and must be installed separately. The Google apps are not required to
boot or run ROM's, however many users find them beneficial to take full advantage of the Android ecosystem.


## Installation

Google apps should be installed via recovery **immediately** after installing AndroidOS. Exact steps vary, and as such, you should see your device's installation guide [here]({{ "devices/" | relative_url }}) for specific instructions.

{% include alerts/important.html content="If you reboot into AndroidOS before installing Google apps, you must factory reset and then install them, otherwise expect crashes.<br/>
This also applies when you experience issues and want to try an older or other package of these apps." %}

### Note regarding Open GApps

{% include alerts/important.html content="This only applies if Open GApps is listed as the GApps package for your Android version in Link column of the tables below in 'Downloads' paragraph. If Open GApps is not listed for your Android version, it is not recommended." %}

If you use Open GApps, they offer a variety of sizes of packages that include and overwrite different apps.

Since you can install any non included apps later, we only recommend the following package sizes (or smaller):
 - For mobile devices: `nano`, as described in [Open GApps Package Comparison](https://github.com/opengapps/opengapps/wiki/Package-Comparison).
 
 If your device states that there is not enough space on any specific partition during install, you will need to use an even smaller package instead.
 
 
## Downloads

These packages are only dependent on your OS version and architecture, which can be found on each device specific info page in ([Device overview]({{ "devices/" | relative_url }})).

{% include alerts/note.html content="Filenames on MindTheGapps are of the format `MindTheGapps-<AndroidVersion>-<architecture>-<date>_<time>.zip` (with Android 12L being 12.1), choose carefully!" %}

{% include alerts/warning.html content="Users often experience issues when deviating from the packages listed below. Be warned!" %}
|Version                   |Link                                                   |
|--------------------------|-------------------------------------------------------|
|Android 13|[MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps))|
|Android 12L|[MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps))|
|Android 11|[MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps)), [NikGapps](https://sourceforge.net/projects/nikgapps/files/Releases/NikGapps-R/), [Open GApps](http://opengapps.org/?api=11&variant=nano)|
|Android 10|[MindTheGapps](https://androidfilehost.com/?w=files&flid=322935) ([mirror](http://downloads.codefi.re/jdcteam/javelinanddart/gapps)), [Open GApps](http://opengapps.org/?api=10&variant=nano)|
|Android 9.0|[MindTheGapps](http://downloads.codefi.re/jdcteam/javelinanddart/gapps) ([mirror](https://androidfilehost.com/?w=files&flid=170282)), [Open GApps](http://opengapps.org/?api=9.0&variant=nano)|
|Android 8.1|[MindTheGapps](http://downloads.codefi.re/jdcteam/javelinanddart/gapps) ([mirror](https://androidfilehost.com/?w=files&flid=170282)), [Open GApps](http://opengapps.org/?api=8.1&variant=nano)|
|Android 7.1|[Open GApps](http://opengapps.org/?api=7.1&variant=nano)|
|Android 6.0|[Open GApps](http://opengapps.org/?api=6.0&variant=nano)|
{: .table }