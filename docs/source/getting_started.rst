Getting started
===============

Authentication
^^^^^^^^^^^^^^
This section is subject to changes made by SimFin and may not be up-to-date. 

To use the API you need a `SimFin API key <https://simfin.com/data/access/api>`_. 

To authenticate with you create a client responsible for making the requests by writing::

	import SAW

	client = SAW.Client("<your API key>")


Rate limit
^^^^^^^^^^
For free accounts the rate is limited to 2000 api calls per day, resetting at 00:00 GMT, while for SimFin+ account you have unlimited calls (`read more <https://medium.com/@SimFin_official/introduction-of-api-and-simfin-accounts-dfdd9368aa02>`_). Rate limiting is by standard made by SAW, but specifying that it is a SimFin+ account by writing::

	client = SAW.Client("<your API key>", True)

.. note::

	The rate limiting is not carried over between sessions. You can check how many calls you have used and how long it is until the calls are reseted `here <https://simfin.com/data/access/api>`_. You can also get the amount of calls left by the SAW rate limiter by writing ``client.get_rate_limit()``.


Basic usage
^^^^^^^^^^^

Firstly, the wrapper needs to be imported::

	import saw

The wrapper is built around a ``Client`` which can be initialized by writing::
	
	client = SAW.Client("<your API key")

To get a company by its ticker you can write::

	company = client.get_company_by_ticker("AAPL")

This returns a ``Company`` which can be used to get more information about that company::

	company.get_info()
	>> { "ticker": "AAPL", "sectorCode": 101001, "simId": 111052, "fyearEnd": 9, "name": "Apple Inc", "sectorName": "Computer Hardware", "employees": 120301 }