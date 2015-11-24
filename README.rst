==========================
plonetrick.csrfworkarounds
==========================

Links:

* `Source code @ GitHub <https://github.com/ale-rt/plonetrick.csrfworkarounds>`_
* `Releases @ PyPI <http://pypi.python.org/pypi/plonetrick.csrfworkarounds>`_
* `Continuous Integration @ Travis-CI <http://travis-ci.org/ale-rt/plonetrick.csrfworkarounds>`_

How it works
============

This package contains workarounds for legacy code that contains bugs
that appear evident after applying the plone4.csrffixes patch.


Usage
=====

Add ``plonetrick.csrfworkarounds`` to the list of eggs in your buildout,
run buildout and restart Plone.

Disable plone CSRF check in page templates
-------------------------------------------

One of the canonical way to disable the CSRF protection
is using this code snippet::

    alsoProvides(
        self.request,
        IDisableCSRFProtection,
    )

This solution is better than the workaround provided by this package.
The workaround consist in customizing the template
adding a call to ``here/disable_csrf_protection/disable``, e.g.:::

    <metal:slot fill-slot="top_slot" tal:define="dummy here/@@disable_csrf_protection/disable" />
