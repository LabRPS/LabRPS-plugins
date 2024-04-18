# LabRPS-plugins

A repository of peer-reviewed LabRPS plugins.

This repository hosts LabRPS plugins that volunteers have vetted and added for use to the whole community in general available through the [LabRPS Addon Manager](https://www.wiki.labrps.com/AddonManager).

## How to submit a plugin

- The best way to submit a plugin is to post it to the [LabRPS Python Scripting and Plugins subforum](https://labrps/forum) for review. After a green light is given then:

- Fork this repository
- Clone your fork locally `git clone https://github.com/your-gh-username/LabRPS-plugins`
- Go to the newly-created local repository `cd LabRPS-plugins`
- Setup the upstream `git remote add upstream https://github.com/LabRPS/LabRPS-plugins`
- Create a branch to work in `git checkout -b your_branch`
- Follow our [guidelines](https://github.com/LabRPS/LabRPS-plugins#guidelines-for-submitting-a-plugin) below on how to add a plugin
- When you're ready to push your changes: `git push -u origin your_branch`
- Create a PR (pull request) against upstream
- Achieve global fame once PR is merged

## Guidelines for submitting a plugin

### Plugin description
Please add a complete description how to use the plugin near the top of your plugin as normal Python comments.
Ideally write a Wiki page explaining what your plugin does and how to use it by following the instructions on the [Wiki](https://wiki.labrps.com/Plugin_documentation). It's a good habit to write a changelog, especially when bringing API breaking changes, from latest to oldest.

### CamelCase plugin name
Please follow the `CamelCase.RPSPlugin` convention for the plugin name (other associated files except the plugin icon don't need to follow this convention). Please don't start your plugin name with `Plugin` or `FC` or similar (we already know it's a plugin for LabRPS).

### Plugin name specifics
Also, if possible, start the plugin name with the type of object it's working on, e.g. use `ViewRotation` instead of `RotateView`, so that all plugins related to `View` will be together when sorting alphabetically.

### Plugin metadata
Please add the following metadata in your plugin after the Plugin description (mentioned above). 

#### Plugin metadata

```python
    __Name__ = ''
    __Comment__ = ''
    __Author__ = ''
    __Date__ = ''
    __Version__ = ''
    __License__ = ''
    __Web__ = ''
    __Wiki__ = ''
    __Icon__ = ''
    __Xpm__ = ''
    __Help__ = ''
    __Status__ = ''
    __Requires__ = ''
    __Communication__ = ''
    __Files__ = ''
```

#### Explanation of metadata

NOTE: All metadata elements are simple strings, and *may not contain code to evaluate*. The LabRPS Addon Manager parses these strings by searching for an equals sign followed by something inside quotes (single or double), all on a single line. Lines may not wrap. For example:
```
# Good, valid
__Comment__ = "When run, this plugin reads your mind and creates the thing your are imagining."

# Bad, contains code:
__Author__ = ",".join(author_list)

# Bad, not a single string:
__Comment__ = "Some descriptive text" + " and more text"

# Bad, multiple lines:
__Files__ = "MyFirstFile.RPSPlugin \
MySecondFile.RPSPlugin"

# EXCEPTION: __Version__ may be set to __Date__ as long as __Date is defined first
__Date__ = 2022.05.19
__Version__ = __Date__

# EXCEPTION: XPM data must be a triple-quoted multi-line string
__Xpm__ = """
/* XPM */
static char * XFACE[] = {
"48 4 2 1",
"a c #ffffff",
"b c #000000",
"abaabaababaaabaabababaabaabaababaabaaababaabaaab",
"abaabaababaaabaabababaabaabaababaabaaababaabaaab",
"abaabaababaaabaabababaabaabaababaabaaababaabaaab",
"abaabaababaaabaabababaabaabaababaabaaababaabaaab"
};
"""
```

* `__Name__` - The name of the plugin, for display by the Addon Manager. Generally the filename of the plugin without extension, and with spaces between words. For example, the plugin file "DxfToSketchLayers.RPSPlugin" becomes "DXF to Sketch Layers"
* `__Comment__` - A description of what the plugin does. Displayed and searched by the Addon Manager.
* `__Author__` -  Comma-separated list of authors (as a single string, e.g. "Jane Doe, John Smith, Bobbi Jones")
* `__Version__` - Use semantic versioning (1.2.3-beta), or CalVer (2022.05.19)
* `__Date__` - The date of the last update, YYYY-MM-DD
* `__License__` - 'License identifier from https://spdx.org/licenses/, e.g. LGPL-2.0-or-later as LabRPS, MIT, CC0-1.0'
* `__Web__` - A URL to fetch the plugin from
* `__Wiki__` - The wiki page (generally at https://wiki.labrps.com) describing the plugin, and displayed as the "Details" page in the Addon Manager.
* `__Icon__` - Either a relative path to an icon file included in the LabRPS plugins repository, or a URL where the icon may be downloaded from. Must be a direct download of an image file.
* `__Xpm__` - (OPTIONAL) Instead of specifying an `__Icon__`, icon data may be set directly as a triple-quoted string containing XPM data.
* `__Help__` - A short explanation how to use the plugin, e.g. what to select before launching
* `__Status__` - Stable|Alpha|Beta
* `__Requires__` - e.g. LabRPS >= v0.17, there is no programmatic use of this for now
* `__Communication__` - e.g. https://github.com/LabRPS/LabRPS-plugins/issues/ if on the github
* `__Files__` - comma-separated list of files that should be installed together with this file, use paths relative to this file, do not include this file, and do not wrap the line, all files must be listed in the same single-line quoted string.
