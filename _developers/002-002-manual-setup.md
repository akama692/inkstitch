---
title: "Manual Setup"
permalink: /developers/inkstitch/manual-setup/
last_modified_at: 2018-07-21
toc: true
---
1. Clone the extension source

   ```
   git clone https://github.com/inkstitch/inkstitch
   ```
2. Python Dependencies

    A few python modules are needed. In some cases this extension uses features that aren’t available in the versions of the modules pre-packaged in distributions, so I recommend installing them directly with pip:
    ```
    pip install -r requirements.txt
    ```

    **Info:** You might need to remove wxPython and [install](https://wiki.wxpython.org/How%20to%20install%20wxPython) a platform specific package (e.g. Debian uses `python-wxgtk3.0`).
    {: .notice--info }
3. Symbolically link into the Inkscape extensions directory

    ```
    cd ~/.config/inkscape/extensions
    ln -s /path/to/inkstitch
    for i in inkstitch/inx/inkstitch_*.inx; do ln -s $i; done
    ln -s inkstitch/inkstitch.py
    ```

4. This step will be no longer necessary with one of the next releases of Ink/Stitch: [#234](https://github.com/inkstitch/inkstitch/pull/234), but for now:

    in the Embroidermodder-master/experimental directory execute:
    ```
    qmake swigpython.pro && make
    ```
    Copy `python/bindings/*libembroidery*` to the Ink/Stitch directory.

4. Run Inkscape.


**Info:** Changes to the Python code take effect the next time the extension is run. Changes to the extension description files (*.inx) take effect the next time Inkscape is restarted.
{: .notice--info }