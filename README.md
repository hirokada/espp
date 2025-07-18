# Espressif++ (ESPP)

This is the repository for some c++ components developed for the
[ESP-IDF](https://github.com/espressif/esp-idf) framework. Specifically we are
targeting `ESP-IDF 5.4` currently.

> NOTE: This repo attempts to stay up to date with ESP-IDF. This means that the
> code within may not be supported on older ESP-IDF targets.

Each component has an `example` folder which contains c++ code showing how to
use the component and which has a README including instructions for how to run
the example

If you have questions or would like to chat, feel free to hop over to our discord!

[<img src="https://discord.com/api/guilds/1345508990716743741/widget.png?style=banner2" alt="Discord Banner 2"/>](https://discord.gg/dvcQw37xAY)

<!-- markdown-toc start - Don't edit this section. Run M-x markdown-toc-refresh-toc -->
**Table of Contents**

- [Espressif++ (ESPP)](#espressif-espp)
    - [Getting Started](#getting-started)
    - [Additional Information and Links](#additional-information-and-links)
    - [Developing](#developing)

<!-- markdown-toc end -->

## Getting Started

The components in this repository are targeted towards ESP-IDF >=5.0, though
they are mainly tested against 5.4 right now.

To use the components in this repository, you have a few options:

1. You can use the [esp-cppp/template](https://github.com/esp-cpp/template)
   repository as a starting point, which is very similar to the esp-idf
   template, but is geared towards c++ development and already has `espp` as a
   submodule, along with the appropriate configuration in the top-level
   CMakeLists.txt.

1. You can add dependencies on the components you want using the `idf component
   manager`. All `espp` components are published to the [ESP Component
   Registry](https://components.espressif.com/components?q=namespace:espp) under the namespace `espp`.
   
   For example, if you want to use the `task` component and the
   `ble_gatt_server` components, you could run:

     ```console
     idf.py add-dependency "espp/task^1.0"
     idf.py add-dependency "espp/ble_gatt_server^1.0"
     ```
   
   Alternatively, you could add the following dependencies to your
   `main/idf_component.yml`:
   
     ```yaml
     dependencies:
        esp-cpp/ble_gatt_server: '>=1.0'
        esp-cpp/task: '>=1.0'
        # other dependencies here...
     ```

1. If you have an existing project with a `components` directory, then you can
   clone `espp` as a submodule within that directory e.g. `git submodule add
   https://github.com/esp-cpp/espp components/espp`, then make sure to run `git
   submodule update --init --recursive`. Afterwards, simply update your
   `CMakeLists.txt` to add

    ```cmake
    # add the component directories that we want to use
    set(EXTRA_COMPONENT_DIRS
      "components/espp/components"
    )
    ```

1. You can clone espp somewhere on your computer and then point your project to
   its `components` directory to use any of the components it contains, similar
   to the step above.

## Additional Information and Links

 * [Documentation](https://esp-cpp.github.io/espp/) - github hosted version of
   the documentation found in [./docs](./docs). This documentation is
   automatically built as part of the CI, but can be locally built for
   validation by running [./build_docs.sh](./build_docs.sh). NOTE: to ensure
   proper build environments, the local documentation build relies on docker, so
   you'll need to run `docker build -t esp-docs doc` once before running
   `build_docs.sh`. This is only required if you want to build the documentation
   locally.

Many components in this repo contain example code (referenced in the
documentation above) that shows some basic usage. This example code can be found
in that component's `example` directory. NOTE: many component examples also make
use of other components (esp. some of the foundational components such as
`format`, `logger`, and `task`.

The [esp-cpp github organization](https://github.com/esp-cpp) contains other
repositories that build specific demonstrations with these (and other)
components.

One such example is the [esp-box-emu](http://github.com/esp-cpp/esp-box-emu)
repository, which builds upon these components to create a multiplatform
emulation system using the ESP32-S3-BOX hardware.

## Developing

If you plan to develop espp components, then it is recommended to configure your
development environment:

### Code style

1. Ensure `clang-format` is installed
2. Ensure [pre-commit](https://pre-commit.com) is installed
3. Set up `pre-commit` for this repository:

  ``` console
  pre-commit install
  ```

This helps ensure that consistent code formatting is applied.

### Building and viewing documentation locally

If you wish to build the documentation, you should have docker installed, then
you can run

``` console
docker build -t esp-docs doc
```

To build the docker container which you will use to build the documentation
locally (for testing).

Thereafter, you can use the included build script to build the documentation
locally.

``` console
./build_docs.sh
```
