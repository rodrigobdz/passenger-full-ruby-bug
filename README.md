# passenger-full-ruby-bug
[MCVE](https://stackoverflow.com/help/mcve) (Minimal, Complete, and Verifiable example) to reproduce Ruby bug in [phusion/passenger-full:1.0.1](https://github.com/phusion/passenger-docker/releases/tag/rel-1.0.1).

## Description

Expected behavior: Ruby 2.5.3 is configured as default as described in phusion/passenger-docker's [README](https://github.com/phusion/passenger-docker/tree/5c9c074cb9c6e3ea26e0bb4c9271d952d3538a3e#whats_included).

Actual behavior: jruby 9.2.0.0 is the default instead.

## Steps to reproduce

1. Build Docker image

    ```sh
    docker build -t passenger-full-mvce .
    ```

1. Run container

    ```sh
    docker run --rm -t -i passenger-full-mvce:latest  bash -l
    ```

1. Check default Ruby version

    ```sh
     ruby --version
     # jruby 9.2.0.0 (2.5.0) 2018-05-24 81156a8 OpenJDK 64-Bit Server VM 25.191-b12 on 1.8.0_191-8u191-b12-0ubuntu0.18.04.1-b12 +jit [linux-x86_64]
     rvm list
     # =* jruby-9.2.0.0 [ x86_64 ]
     #    ruby-2.3.8 [ x86_64 ]
     #    ruby-2.4.5 [ x86_64 ]
     #    ruby-2.5.3 [ x86_64 ]
     #
     # # => - current
     # # =* - current && default
     # #  * - default
    ```

## License

[MIT](./LICENSE) © 2018 Rodrigo Bermúdez Schettino
