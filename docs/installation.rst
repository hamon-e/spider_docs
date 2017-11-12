============
Installation
============

.. highlight:: console

-------------------
Server installation
-------------------

^^^^^^^^^^^^^
Generate Keys
^^^^^^^^^^^^^

Caution:
You can use the embedded keys and certificate for testing only.

""""""""
RSA Keys
""""""""

Use this command to generate the server public and private keys.::

    $ ssh-keygen -t RSA

You must name it serverPrivkey.key and serverPubKey.key

""""""""""""""""""""""
Certificate Generation
""""""""""""""""""""""

For testing you can use those command to generate a self-generate certificate
Otherwise use a service like Let's Encrypt.::

    $ openssl genrsa -des3 -out server.key 1024
    $ openssl req -new -key server.key -out server.csr
    $ mv server.key server.key.org
    $ openssl rsa -in server.key.org -out server.key
    $ openssl x509 -req -days 365 -in server.csr -signkey server.key -out server.crt

^^^^^^^^
Building
^^^^^^^^

""""""""
Manually
""""""""



"""""""""""
With Docker
"""""""""""
