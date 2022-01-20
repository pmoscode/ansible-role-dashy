Dashy
=========

This role installs Dashy (https://github.com/Lissy93/dashy) on your server. 

From Dashy's GitHub Readme: "Dashy helps you organize your self-hosted services by making them accessible from a single place"

Role Variables
--------------

| Parameter                     | Default                        | Description                                                                                                             |
|-------------------------------|--------------------------------|-------------------------------------------------------------------------------------------------------------------------|
| dashy_version                 | 1.9.7                          | Version to install (Git tag)                                                                                            |
| dashy_install_dir             | /opt/dashy                     | Path where installation should go                                                                                       |
| dashy_server_port             | 8080                           | Port to listen on                                                                                                       |
| dashy_app_language            | de-de                          | Your language (https://en.wikipedia.org/wiki/List_of_ISO_639-1_codes)                                                   |
| dashy_app_startingView        | default                        | Which page to load by default                                                                                           |
| dashy_app_statusCheck         | false                          | Check status of your services                                                                                           |
| dashy_app_allowConfigEdit     | true                           | Allow editing of config from the UI                                                                                     |
| dashy_app_showSplashScreen    | false                          | Show splash screen                                                                                                      |
| dashy_app_disableUpdateChecks | false                          | Disable check for new Dashy versions                                                                                    |
| dashy_app_theme               | one-dark                       | Theme to use (https://github.com/Lissy93/dashy/blob/987ee2d2f3fae5ecd46abe8bf44a982b78710c5d/src/utils/defaults.js#L49) |
| dashy_page_title              | Dashy                          | Title of the Dashboard                                                                                                  |
| dashy_page_footerText         |                                | Custom footer text                                                                                                      |
| dashy_page_logo               |                                | Custom logo (local or remote)                                                                                           |
| dashy_page_description        | Welcome to your new dashboard! | Describe your Dashboard                                                                                                 |
| dashy_page_nav_links          | []                             | See:  https://github.com/Lissy93/dashy/blob/master/docs/configuring.md#pageinfonavlinks-optional                        |
| dashy_page_sections           | []                             | See:  https://github.com/Lissy93/dashy/blob/master/docs/configuring.md#section                                          |

Dependencies
------------

This role depends on:

- nodejs > 14 (ex.: oefenweb.nodejs)
- yarn (ex.: oefenweb.yarn)
- git (ex.: geerlingguy.git)

Example Playbook
----------------

```yaml
- name: "Install Dashy"
  hosts: dashy

  roles:
    - role: oefenweb.nodejs
      vars:
        nodejs_version: nodejs-v14x
    - role: oefenweb.yarn
    - role: geerlingguy.git
    - role: pmoscode.dashy
      vars:
        dashy_page_title: Your Dashboard name
        dashy_page_description: Good stuff here
        dashy_page_nav_links:
          - title: GitHub
            path: https://github.com/Lissy93/dashy
          - title: Documentation
            path: https://dashy.to/docs
        dashy_page_sections:
          - name: Apps
            icon: fas fa-shapes
            items:
              - title: Dashy Live
                description: Development a project management links for Dashy
                icon: https://i.ibb.co/qWWpD0v/astro-dab-128.png
                url: https://live.dashy.to/
                target: newtab
              - title: Showcase
                description: See how others are using Dashy
                url: https://github.com/Lissy93/dashy/blob/master/docs/showcase.md
                icon: far fa-grin-hearts
``` 

License
-------

MIT
