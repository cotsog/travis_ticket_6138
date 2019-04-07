Travis Ticket #6138 2019-04-07
==============================

|Build Status|

environment Variables not expanded properly - see the travis.yml for test code


ISSUE1 - Variables not expanded in - name:
------------------------------------------

what I got : see : https://travis-ci.org/bitranox/travis_ticket_6138

what I would expect : Variables should be expended in - name

----

ISSUE2 - Variables not expanded in script:
------------------------------------------

what I got : see : https://travis-ci.org/bitranox/travis_ticket_6138/jobs/516798427
Line 203, Line208

what I would expect : Variable ${env_variable_within_matrix} should be expended correctly.

----

ISSUE3 - poor Error Messages
----------------------------

in order to debug the travis yml, better error messages would be helpful:

what I got : see : https://travis-ci.org/bitranox/travis_ticket_6138/jobs/516798427
Line 199:

.. code-block:: bash

    $ ${matrix_test} call_a_function_that_fails
    matrix_variable_TEST1: command not found
    The command "${matrix_test} call_a_function_that_fails" exited with 127.

what I would expect:

.. code-block:: bash

    $ ${matrix_test} call_a_function_that_fails
    matrix_variable_TEST1: command not found
    The command "${matrix_test} call_a_function_that_fails" exited with 127.
    TRACEBACK:
        travis.yml, Line Number 45
        ENV Variables Global Scope:
            Name, Value ...
            Name, Value ...
        ENV Variables Matrix Scope:
            Name, Value ...
            Name, Value ...
    RAISED 127(The command "${matrix_test} call_a_function_that_fails")







.. code-block:: bash

    # code
    test

test


.. |Build Status| image:: https://travis-ci.org/bitranox/travis_ticket_6138.svg?branch=master
   :target: https://travis-ci.org/bitranox/travis_ticket_6138

