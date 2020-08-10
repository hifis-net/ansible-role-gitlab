.. SPDX-FileCopyrightText: 2020 Helmholtz Centre for Environmental Research (UFZ)
.. SPDX-FileCopyrightText: 2020 Helmholtz-Zentrum Dresden-Rossendorf (HZDR)

.. SPDX-License-Identifier: Apache-2.0

*******
Docker driver installation guide
*******

Requirements
============

* Docker Engine

Install
=======

Please refer to the `Virtual environment`_ documentation for installation best
practices. If not using a virtual environment, please consider passing the
widely recommended `'--user' flag`_ when invoking ``pip``.

.. _Virtual environment: https://virtualenv.pypa.io/en/latest/
.. _'--user' flag: https://packaging.python.org/tutorials/installing-packages/#installing-to-the-user-site

.. code-block:: bash

    $ python3 -m pip install 'molecule[docker]'
