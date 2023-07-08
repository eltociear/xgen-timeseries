##################
Installation guide
##################

This section provides detailed information about installing XGenTS. Most XGenTS
functionality is available with the basic requirements, but XGenTS also has optional
dependencies to further enhance the library. This guide will cover both basic and fully-fledged XGenTS installs and several installation methods.


******
Stable
******

XGenTS can be installed either using pip or conda-forge.

Using pip
=========

.. code:: bash

    pip install XGenTS

Use the below pip command to install XGenTS with all of its :ref:`Optional-dependencies`.

.. code:: bash

    pip install "XGenTS[all]"

Using conda-forge
=================

.. code:: bash

    conda install -c conda-forge XGenTS

.. _dev-version:

***********
Development
***********

If you want to install the latest development version of XGenTS, use the following command:

.. code:: bash

    pip install git+https://github.com/XGenTS-devs/XGenTS

**Note**: It can take sometime to execute depending upon your internet connection.

.. _XGenTS-dependencies:

************
Dependencies
************

Required dependencies
=====================

The required dependencies for installing XGenTS are:

.. literalinclude:: ../../../requirements.txt

and

.. code::

    python>=3.8

XGenTS follows `NEP 29 <https://numpy.org/neps/nep-0029-deprecation_policy.html>`_
and `SPEC 0 <https://scientific-python.org/specs/spec-0000/>`_ to choose the minimum
supported versions.

.. _Optional-dependencies:

Optional dependencies
=====================

The list of optional dependencies to further enhance XGenTS is given below.

.. literalinclude:: ../../../requirements-optional.txt


- Numba

  Necessary to speed up the code computation. The installation details can be found
  `here <https://numba.pydata.org/numba-docs/latest/user/installing.html>`_. Further details on enhanced functionality provided in XGenTS by Numba can be
  :ref:`found here <numba_for_XGenTS>`.

- Bokeh

  Necessary for creating advanced interactive visualisations. The Bokeh installation guide can be found `over here <http://docs.bokeh.org/en/dev/docs/first_steps/installation.html>`_.

- UltraJSON

  If available, XGenTS makes use of faster ujson when :func:`XGenTS.from_json` is
  invoked. UltraJSON can be either installed via `pip <https://pypi.org/project/ujson/>`_ or `conda <https://anaconda.org/anaconda/ujson>`_.

- Dask

  Necessary to scale the packages and the surrounding ecosystem. The installation details can be found `at this link <https://docs.dask.org/en/latest/install.html>`_.


.. toctree::

  Installation
  Introduction
  XarrayforXGenTS
  CreatingInferenceData
  WorkingWithInferenceData

