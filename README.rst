Introduction
============

This package integrates `JSHint`_ with Python's `unittest`_ module. This
package was inspired by `gocept.jslint`_.

`JSHint`_ is a community-driven tool to detect errors and potential problems in
JavaScript code and to enforce your team's coding conventions.

It provides a special JSHintTestCase class that collects JavaScript files (in
a configurable manner) and dynamically generates a test method for each file
that calls jslint on that file.

.. contents::


Usage
=====

To use it, create a test class like this::

    class MyPackageJSLintTest(unittest_jshint.JSHintTestCase):

        include = (
            'my.package.browser:js',
            'my.package.browser:js/lib',
            )

        options = ( 'curly', 'eqeqeq', )


``include`` is a list of "resource paths" of the form ``packagename:path``
(passed to pkg_resources).

``exclude`` can be a list of filenames (without path) that will not be
collected.

``options`` is a list of arguments that are passed to JSHint (see its
`documentation`_ for details). The default value is::

    options = ()


All files ending in ``.js`` contained in each of these paths will be collected,
and the test class will grow a method named ``test_<filename>.js``.

You can ignore JSHint error by setting ``ignore`` on the test class (a list of
substrings that are matched against each JHLint output line)::

    ignore = (
        "Use a named parameter",
        )


Requirements
============

``unittest_jshint`` was tested with:

- Python 2.6 (unittest2 required)
- Python 2.7

Currently I only test with `Python`_ versions that are used by `Plone`_ so it
just might work for other `Python`_ versions.

``unittest_jshint`` requires ``jshint`` to be in the ``PATH`` or providing
customized environmental variable ``UNITTEST_JSHINT_COMMAND``.


Contributors
============

- `Rok Garbas`_, garbas



.. _`JSHint`: http://www.jshint.com
.. _`gocept.jslint`: http://pypi.python.org/pypi/gocept.jslint
.. _`documentation`: http://www.jshint.com/options/
.. _`Python`: http://www.python.org
.. _`Plone`: http://www.plone.org
.. _`Rok Garbas`: 'http://garbas.si
