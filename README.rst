rumps
=====

**R**\ idiculously **U**\ ncomplicated **m**\ acOS **P**\ ython **S**\ tatusbar apps.

.. image:: https://raw.github.com/jaredks/rumps/master/examples/rumps_example.png

.. code-block:: python

    import rumps

    class AwesomeStatusBarApp(rumps.App):
        @rumps.clicked("Preferences")
        def prefs(self, _):
            rumps.alert("jk! no preferences available!")

        @rumps.clicked("Silly button")
        def onoff(self, sender):
            sender.state = not sender.state

        @rumps.clicked("Say hi")
        def sayhi(self, _):
            rumps.notification("Awesome title", "amazing subtitle", "hi!!1")

    if __name__ == "__main__":
        AwesomeStatusBarApp("Awesome App").run()

How fun!?

``rumps`` can greatly shorten the code required to generate a working app. No ``PyObjC`` underscore syntax required!


Use case
--------

``rumps`` is for any console-based program that would benefit from a simple configuration toolbar or launch menu.

Good for:

* Notification-center-based app
* Controlling daemons / launching separate programs
* Updating simple info from web APIs on a timer

Not good for:

* Any app that is first and foremost a GUI application


Required
--------

* PyObjC
* Python 2.6+

Mac OS X 10.6 was shipped with Python 2.6 as the default version and PyObjC has been included in the default Python
since Mac OS X 10.5. If you're using Mac OS X 10.6+ and the default Python that came with it, then ``rumps`` should be
good to go!


Recommended
-----------

* py2app

For creating standalone apps, just make sure to include ``rumps`` in the ``packages`` list. Most simple statusbar-based
apps are just "background" apps (no icon in the dock; inability to tab to the application) so it is likely that you
would want to set ``'LSUIElement'`` to ``True``. A basic ``setup.py`` would look like,

.. code-block:: python

    from setuptools import setup

    APP = ['example_class.py']
    DATA_FILES = []
    OPTIONS = {
        'argv_emulation': True,
        'plist': {
            'LSUIElement': True,
        },
        'packages': ['rumps'],
    }

    setup(
        app=APP,
        data_files=DATA_FILES,
        options={'py2app': OPTIONS},
        setup_requires=['py2app'],
    )

With this you can then create a standalone,

.. code-block:: bash

    python setup.py py2app


Installation
------------

Using pip,

.. code-block:: bash

    pip install rumps

Or from source,

.. code-block:: bash

    python setup.py install

Both of which will require ``sudo`` if installing in a system-wide location.


Documentation
-------------

Documentation is available at http://rumps.readthedocs.org


License
-------

"Modified BSD License". See LICENSE for details. Copyright Jared Suttles, 2017.

Works Made With rumps
---------------------

`allofthelights
<https://github.com/kenkeiter/allofthelights/>`_

`attendee-tool-mlh
<https://github.com/Bucknalla/attendee-tool-mlh/>`_

`bundle-checker
<https://github.com/jeffgodwyll/bundle-checker/>`_

`c1t1
<https://github.com/e9t/c1t1/>`_

`commitwatch
<https://github.com/chrisfosterelli/commitwatch/>`_

`cryptocoin-quotes
<https://github.com/Sayan98/cryptocoin-quotes/>`_

`dns.app
<https://github.com/damln/dns.app/>`_

`HalfCaff
<https://github.com/dougn/HalfCaff/>`_

`harmenubar
<https://github.com/vekkt0r/harmenubar/>`_

`HipStatus
<https://github.com/jamfit/HipStatus/>`_

`idiot
<https://github.com/snare/idiot/>`_

`LifxController
<https://github.com/mitchmcdee/LifxController/>`_

`mac-shrew
<https://github.com/mejmo/mac-shrew/>`_

`narcissist
<https://github.com/helmholtz/narcissist/>`_

`osx-bamboo-plan-status
<https://github.com/spalter/osx-bamboo-plan-status/>`_

`py-Timey
<https://github.com/asakasinsky/py-Timey/>`_

`pySplash
<https://github.com/Egregors/pySplash/>`_

`rideindegochecker
<https://github.com/josepvalls/rideindegochecker/>`_

`slack-status-bar
<https://github.com/ericwb/slack-status-bar/>`_

`sonostus
<https://github.com/sarkkine/sonostus/>`_

`SpotifyLyrics
<https://github.com/yask123/SpotifyLyrics/>`_

`umma
<https://github.com/mankoff/umma/>`_

`WallpDesk
<https://github.com/L3rchal/WallpDesk/>`_

`WhyFi
<https://github.com/OzTamir/WhyFi/>`_

`WordTime
<https://github.com/Demonstrandum/WordTime/>`_

Submit a pull request to add your own!
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
