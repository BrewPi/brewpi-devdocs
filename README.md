# brewpi-docs

Top level documentation for BrewPi, which links docs to other repos.

## The big picture

BrewPi is now split into many components: you need things that run on the controller, some service layer and a user interface.

On the controller (Spark/BrewPi), the framework on top of which the [new BrewPi firmware](https://github.com/BrewPi/firmware/tree/feature/controlbox) is developped is called [ControlBox](https://github.com/m-mcgowan/controlbox-cpp). It is written in C++.

The [service layer](https://github.com/glibersat/brewpiweb/tree/develop), written in Python/Django interacts with controllers using the [controlbox connector](https://github.com/m-mcgowan/controlbox-connect-py/tree/develop). Communication is currently done over TCP (Spark has a WiFi chipset built-in) and devices are discovered using the mDNS protocol (zeroconf/avahi).

On top of that, by using the REST API of the service layer, a Web UI will be built in React (we're looking for more people here, feel free to join!).

### Setting up a developpement environnement

#### BrewPi emulator

First, you need a device running BrewPi/Controlbox. A good choice is to run a virtual device. Follow instructions [here](https://github.com/BrewPi/firmware/tree/feature/controlbox/app/cbox#building-brewpi-as-a-cross-compiled-app). Make sure you have a C++ compiler (GCC) and boost installed. If you're running a Linux system and have installed boost using your package manager, don't forget to set your "BOOST_ROOT" environement variable like this: `export BOOST_ROOT=/usr/lib/`. If you're running Windows or OSX, refer to this [document](https://github.com/BrewPi/firmware/blob/feature/controlbox/platform/spark/firmware/hal/src/gcc/readme.md) to install boost.

#### Service layer

To install the service layer, follow these [instructions](https://github.com/glibersat/brewpiweb/#install). If you want to read more about the service layer and dig into the internals, you can refer to [its documentation](http://brewpi-service.readthedocs.io/en/feature-controllers/).
