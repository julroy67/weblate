Weblate frontend
================

The frontend is currently built using Bootstrap, jQuery and few third party libraries.

Dependency management
---------------------

The yarn package manager is used to update third party libraries. The
configuration lives in :file:`scripts/yarn` and there is a wrapper script
:file:`scripts/yarn-update` to upgrade the libraries, build them and copy to
correct locations in :file:`weblate/static/vendor`, where all third partly
frontend code is located.

Coding style
------------

Weblate relies on `Prettier`_ for the code formatting for both JavaScript and CSS files.

We also use `ESLint`_ to check the JavaScript code.

.. _ESLint: https://eslint.org/
.. _Prettier: https://prettier.io/


Localization
------------

Should you need any user visible text in the frontend code, it should be
localizable. In most cases all you need is to wrap your text inside ``gettext``
function, but there are more complex features available:

.. code-block:: javascript

    document.write(gettext('this is to be translated'));

    var object_count = 1 // or 0, or 2, or 3, ...
    s = ngettext('literal for the singular case',
            'literal for the plural case', object_count);

    fmts = ngettext('There is %s object. Remaining: %s',
            'There are %s objects. Remaining: %s', 11);
    s = interpolate(fmts, [11, 20]);
    // s is 'There are 11 objects. Remaining: 20'

.. seealso::

   :doc:`Translation topic in the Django documentation <django:topics/i18n/translation>`

Icons
-----

Weblate currently uses material design icons, in case you are looking for new
one, check <https://materialdesignicons.com/>.

Additionally, there is :file:`scripts/optimize-svg` to reduce size of the SVG
as most of the icons are embedded inside the HTML to allow styling of the
paths.
