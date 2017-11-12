===
API
===

^^^^^^
SignUp
^^^^^^

EndPoint : ``/signup``

Parameters:

.. code-block:: json

    {
      "user": "",
      "password": "",
      "cookie": "Optional if no user in database",
    }

Return:

.. code-block:: json

    {
      "status": "ok / ko",
      "message": "New user created / User not logged in"
    }

^^^^^
Login
^^^^^

EndPoint : ``/login``

Parameters:

.. code-block:: json

    {
      "user": "",
      "password": "",
    }

Return:

.. code-block:: json

    {
      "status": "ok / ko",
      "cookie": "",
      "message": "User Connected / Bad credidentials"
    }



^^^^^^^^^^^^
List Clients
^^^^^^^^^^^^

EndPoint : ``/client_list``

Parameters:

.. code-block:: json

    {
      "cookie": "",
    }

Return:

.. code-block:: json

    {
      "status": "ok / ko",
      "list": [
        {}
      ]
    }


^^^^^^^^^^^^^^
Send To Client
^^^^^^^^^^^^^^

EndPoint : ``/send``

Parameters:

.. code-block:: json

    {
      "cookie": "",
      "data": {

      }
    }

Return:

.. code-block:: json

    {
      "status": "ok / ko",
    }
