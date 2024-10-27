
Address API
===========

.. _address-staking-info:

Address Staking Info / History
------------------------------

.. http:get:: /v2/address/staking_info/(address)

   :query height: (optional) retrieve data at a specific block height. Mutually exclusive with ``time``.
   :query time: (optional) retrieve data at a specific time. Accepts a number as unix epoch, or a string in ISO 8601 format. Mutually exclusive with ``height``.
   :>json int height: block height of the data.
   :>json int timestamp: block timestamp.
   :>json str amount: bonded amount of the address in microcredits.
   :>json str validator: validator the address is / was bonded to.

   Get the staking info of an address, now or at specific time in the past.
   Returns ``null`` if the address is not bonded.

   **Example request**:

   .. sourcecode:: http

      GET /v2/address/staking_info/aleo1sdjqhlcm9qltpu74ek0vxewt52zsdmn6swmpjn6m0tp9xf57dvpq740r8j HTTP/1.1
      Host: api.aleoscan.io

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      {
          "height": 1230000,
          "timestamp": 1712200000,
          "amount": 10000000000,
          "validator": "aleo1n6c5ugxk6tp09vkrjegcpcprssdfcf7283agcdtt8gu9qex2c5xs9c28ay"
      }

   :statuscode 200: no error
   :statuscode 400: invalid parameter or combination
   :statuscode 404: time or height is before the genesis block

.. _address-delegated:

Address Delegated Credits / History
-----------------------------------

.. http:get:: /v2/address/delegated/(address)

   :query height: (optional) retrieve data at a specific block height. Mutually exclusive with ``time``.
   :query time: (optional) retrieve data at a specific time. Accepts a number as unix epoch, or a string in ISO 8601 format. Mutually exclusive with ``height``.
   :>json int height: block height of the data.
   :>json int timestamp: block timestamp.
   :>json str amount: delegated amount of the address in microcredits.

   Get the amount of tokens delegated to the address, now or at specific time in the past.
   Returns ``null`` if no tokens are delegated to the address.

   **Example request**:

   .. sourcecode:: http

      GET /v2/address/delegated/aleo1sdjqhlcm9qltpu74ek0vxewt52zsdmn6swmpjn6m0tp9xf57dvpq740r8j HTTP/1.1
      Host: api.aleoscan.io

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      {
          "height": 1230000,
          "timestamp": 1712200000,
          "amount": 10000000000000
      }

   :statuscode 200: no error
   :statuscode 400: invalid parameter or combination
   :statuscode 404: time or height is before the genesis block

.. _address-program_id:

Address Program ID
------------------

.. http:get:: /v2/address/program_id/(address)

   Get the program ID of an address, if it is a program address.
   Returns ``null`` if the address is not a program address.

   **Example request**:

   .. sourcecode:: http

      GET /v2/address/program_id/aleo12x4rzm2j56e9uknpy0dcglt32vfk9ujx9e0pl8x7sy77jjyx4cps5sp8hm HTTP/1.1
      Host: api.aleoscan.io

   **Example response**:

   .. sourcecode:: http

      HTTP/1.1 200 OK
      Content-Type: application/json

      "vlink_quest_v1.aleo"

   :statuscode 200: no error
   :statuscode 400: invalid parameter