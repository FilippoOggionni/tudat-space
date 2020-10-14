=========================
Creating celestial bodies
=========================


Creating a set of celstial bodies is done by creating a list of settings for all bodies, after which these settings are parsed to create a set of Body objects, which are stored in a SystemOfBodies object. In creating this system of bodies, all interdependencies between them are automatically processed. The typical first step, when defining celestial bodies, is to retrieve their 'default' settings as follows:

    .. tabs::

         .. tab:: Python

          .. toggle-header:: 
             :header: Required **Show/Hide**

             .. literalinclude:: /_src_snippets/simulation/environment_setup/req_create_bodies.py
                :language: python

          .. literalinclude:: /_src_snippets/simulation/environment_setup/default_bodies.py
             :language: python

         .. tab:: C++

          .. literalinclude:: /_src_snippets/simulation/environment_setup/req_setup.cpp
             :language: cpp

where the global frame origin and orientation define the reference frame in which state vectors stored within the Body object are represented. In general, it is recommended to choose this as the most 'intuitive' frame origin for your propagation (e.g. SSB or Sun for solar system scale propagations, Earth for an Earth orbiter, Mars for a Martian mission, etc.). This frame definition is *distinct* from the center of propagation that you can define in your propagation setup TODO

Generating default settings prevents a user from having to manually define a varity of 'typical' models for solar-system bodies. The full list of default body settings, and an alternative set of default settings, which is typically more computationally efficient (at the expense of higher memory usage and some practical limitations) is discussed here TODO. 

Default settings may be overridden as follows:

    .. tabs::

         .. tab:: Python

          .. toggle-header:: 
             :header: Required **Show/Hide**

             .. literalinclude:: /_src_snippets/simulation/environment_setup/req_create_bodies.py
             .. literalinclude:: /_src_snippets/simulation/environment_setup/default_bodies.py
                :language: python

          .. literalinclude:: /_src_snippets/simulation/environment_setup/override_default.py
             :language: python

         .. tab:: C++

          .. literalinclude:: /_src_snippets/simulation/environment_setup/req_setup.cpp
             :language: cpp

Where the above example overrides the default setting for the Sun's gravity field, and sets a point-mass gravity field with a gravitationa parameter of 1.32712440042E20 m^3/s^2. A comprehensive list of *all* environment models, and how their settings can be defined and overridden as above, is given in the list TODO

Once all settings for the bodies are defined as desired, the bodies are created and linked as follows:

    .. tabs::

         .. tab:: Python

          .. toggle-header:: 
             :header: Required **Show/Hide**

             .. literalinclude:: /_src_snippets/simulation/environment_setup/req_create_bodies.py
             .. literalinclude:: /_src_snippets/simulation/environment_setup/default_bodies.py
             .. literalinclude:: /_src_snippets/simulation/environment_setup/override_default.py
                :language: python

          .. literalinclude:: /_src_snippets/simulation/environment_setup/create_system_of_bodies.py
             :language: python

         .. tab:: C++

          .. literalinclude:: /_src_snippets/simulation/environment_setup/req_setup.cpp
             :language: cpp

This ``bodies`` in the above simulation are the heart of many Tudat simulations: they contain all properties of your celestial and manmade bodies, and are used to retieve properties of your accelerations, state derivative models, output variables, etc. 

