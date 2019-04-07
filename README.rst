Travis Ticket #6138 2019-04-07
==============================

|Build Status|

environment Variables not expanded properly - see the travis.yml for test code


ISSUE1 - Variables not expanded in - name:
------------------------------------------

what I got : see : https://travis-ci.org/bitranox/travis_ticket_6138/builds/516957359

Matrix1 - Config:${matrix_config}

Matrix2 - Config:${matrix_config}

what I would expect :


Matrix1 - Config:config_1

Matrix2 - Config:config_2


----

ISSUE2 - Variables not expanded in script:
------------------------------------------

what I got : see : https://travis-ci.org/bitranox/travis_ticket_6138/jobs/516957362

Line 127

what I would expect : Variable ${matrix_config} should be expended correctly.

Line 271

what I would expect : Variable ${matrix_config} should be expended correctly.

----

ISSUE3 - poor Error Messages
----------------------------

in order to debug the travis yml, better error messages would be helpful:

what I got : see : https://travis-ci.org/bitranox/travis_ticket_6138/jobs/516957362

Line 263:

.. code-block:: bash

    $ ${global_1} call_a_function_that_fails
    No command 'global1' found, did you mean:
     Command 'global' from package 'global' (universe)
    global1: command not found
    The command "${global_1} call_a_function_that_fails" exited with 127.

what I would expect:

.. code-block:: bash

    $ global1 call_a_function_that_fails
    No command 'global1' found, did you mean:
     Command 'global' from package 'global' (universe)
    global1: command not found
    TRACEBACK:
        travis.yml, Line Number 47
        "${global_1} call_a_function_that_fails" exited with 127 (Command not found)
        Matrix Scope:
            matrix_config="config_1"
            ...
    END TRACEBACK


.. |Build Status| image:: https://travis-ci.org/bitranox/travis_ticket_6138.svg?branch=master
   :target: https://travis-ci.org/bitranox/travis_ticket_6138

