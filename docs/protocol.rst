========
Protocol
========

The communication between the server and the client is based on JSON formatted UDP request.

The packet is divided in 2 sections:

* the header
* the data

If the data is larger than a configurable value, it's splitted between several packet.

------
Header
------

The header is composed on the following value:

* ``id``: Used to identify different packet
* ``crypt``: Used to know the encryption algorythm in used (None,RSA,AES)
* ``cookie``: Used to authentificate clients
* ``checksum``: Used to check data corruption
* ``timestamp``
* ``part``: Used reconstitute packet in the good order
* ``totalpart``: Used to know when all part of packet is received
* ``data``


-----------------
Packet Reception
-----------------

In order to confirm the good reception of a packet, a confirm packet must be send
Format the data like this (dont forget to snet the good ID and PART in the header)

.. code-block:: json

    {
      "type": "success",
    }

----------
Encryption
----------

""""""""""""""
Initialization
""""""""""""""

The client must first generate an RSA key pair.

Next send it to the server (it can be encrypted with the server public key)
Format the data like this

.. code-block:: json

    {
      "type": "PublicKey",
      "key": "CLIENT_PUBLIC_KEY",
    }

The communication can now be encrypted in both way.

""""""""""""
SetUp
""""""""""""

RSA algorythm can only encrypt small data.
In order to send bigger packet a symetric encryption must be setup like this.

The server generate an AES keys and a cookie.
Send it to the client like this

.. code-block:: json

    {
      "type": "AesKey",
      "key": {
        "AES_KEY": "AES_KEY",
        "AES_IV": "AES_IV",
        "cookie": "COOKIE"
      }
    }

-------
Modules
-------

""""""
Deploy
""""""

The server can deploy modules into the client like this

.. code-block:: json

    {
      "type": "Upload",
      "lib": "MODULE_CONTENT"
    }

""""""
Orders
""""""

The server can send orders to client like this

.. code-block:: json

    {
      "type": "Order",
      "order": {
        "key": "ORDER_KEY",
        "value": "ORDER_VALUE",
      }
    }
