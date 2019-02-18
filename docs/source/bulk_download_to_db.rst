Bulk download to database
=========================

SAW is included with a command line tool to generate a SQLite database from the `bulk download tool <https://simfin.com/data/access/download>`_. The tool is used by writing::

	saw dataset.csv database.db

The dataset is a csv file in wide format with semicolon as delimiter. The database file is a already existing or not yet created SQLite file. 

The database consists of three tables:

**Company:**

+-------------+---------------------------+
| Column name | Column type               |
+=============+===========================+
| ``id``      | ``integer`` - primary key |
+-------------+---------------------------+
| ``ticker``  | ``varchar``               |
+-------------+---------------------------+
| ``name``    | ``varchar``               |
+-------------+---------------------------+

**Indicator:**

+-------------+---------------------------+
| Column name | Column type               |
+=============+===========================+
| ``id``      | ``integer`` - primary key |
+-------------+---------------------------+
| ``name``    | ``varchar``               |
+-------------+---------------------------+

**IndicatorValue:**

+---------------+---------------------------+
| Column name   | Column type               |
+===============+===========================+
| ``id``        | ``integer`` - primary key |
+---------------+---------------------------+
| ``company``   | ``integer`` - foreign key |
+---------------+---------------------------+
| ``indicator`` | ``integer`` - foreign key |
+---------------+---------------------------+
| ``date``      | ``date``                  |
+---------------+---------------------------+
| ``value``     | ``real``                  |
+---------------+---------------------------+
