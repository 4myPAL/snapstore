SnapStore
========
|snapcraft| |fossa| |landscape| |codacy|

Overview
========

snapstore is a minimalist for snaps, based on the public API specs (https://search.apps.ubuntu.com/docs/). It allows anyone to host their own collection of snaps for installation on supported platforms.

See http://snapcraft.io for more information on creating and using snap packages.

Server setup (with snappy)
----------------------------

::

    snap install snapstore


It will be run as a daemon on the default port 5000.


Server setup (manual)
---------------------

Install python-virtualenv.

E.g. on Ubuntu 16.04::

    sudo apt install python3


Clone this repo::

    git clone https://github.com/kamil1b/snapstore.git
    cd snapstore


Setup virtualenv and install dependencies::

    python -m venv env
    . env/bin/activate
    python setup.py


Run it::

    python snapstore



File management
---------------

Put snaps (named as name.snap) and metadata (named as name.meta) in ./files/ (/var/snap/snapstore/current/files/ for snap version).


Client setup
============

On any distribution supporting snaps (see http://snapcraft.io), install snapd (requires snapd >=2.0.6).

E.g. on Ubuntu 16.04::

    sudo apt install snapd


Edit /etc/environment, add your store URL, e.g.::

    SNAPPY_FORCE_CPI_URL=http://localhost:5000/api/v1/


Then bounce snapd::

    sudo service snapd restart


Usage
=====

Supports snap find <name>, snap install <name>::

    $ snap find
    Name      Version  Developer  Notes  Summary
    bar       0.2      testuser   -      This is a bar snap
    baz       0.4      testuser   -      This is a baz snap
    foobar25  2.5      testuser   -      This is a test snap

    $ snap find ba
    Name  Version  Developer  Notes  Summary
    bar   0.2      testuser   -      This is a bar snap
    baz   0.4      testuser   -      This is a baz snap

    $ snap install bar
    Name  Version  Rev  Developer  Notes
    bar   2.5      1    testuser   -

    $ snap refresh bar
    Name  Version  Rev  Developer  Notes
    bar   2.5      2    testuser   -

Known issues
============

- Alfa version, probably lots!
- snap refresh (bulk) not supported  

.. |snapcraft| image:: https://build.snapcraft.io/badge/kamil1b/snapstore.svg :target: https://build.snapcraft.io/user/kamil1b/snapstore
.. |fossa| image:: https://app.fossa.io/api/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fkamil1b%2Fsnapstore.svg?type=shield :target: https://app.fossa.io/projects/git%2Bhttps%3A%2F%2Fgithub.com%2Fkamil1b%2Fsnapstore?ref=badge_shield
.. |green| image:: https://img.shields.io/badge/docs-latest-brightgreen.svg?style=flat
.. |landscape| image:: https://landscape.io/github/kamil1b/snapstore/master/landscape.svg?style=flat :target: https://landscape.io/github/kamil1b/snapstore
.. |codacy| image:: https://api.codacy.com/project/badge/Grade/5d5581923fcb43a1bfed27f9ba25a3c6 :target: https://www.codacy.com/app/kamil1b/snapstore?utm_source=github.com&amp;utm_medium=referral&amp;utm_content=kamil1b/snapstore&amp;utm_campaign=Badge_Grade


.. image:: https://api.codacy.com/project/badge/Grade/5d5581923fcb43a1bfed27f9ba25a3c6
   :alt: Codacy Badge
   :target: https://www.codacy.com/app/kamil1b/snapstore?utm_source=github.com&utm_medium=referral&utm_content=kamil1b/snapstore&utm_campaign=badger