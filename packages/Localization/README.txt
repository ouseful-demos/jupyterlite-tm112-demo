Localization
============

The Localization package provides tools for multilateration and triangulation
in 2D, 3D, and on the Earth's surface. The current Earth model supported by the
package is called 'Earth1', which models the Earth as an ideal sphere with a radius
of 6378.1 kilometers.

Original repo: https://github.com/kamalshadi/Localization

Typical usage of the package:

.. code-block:: python

    import localization as lx

To initialize a new localization Project, use:

.. code-block:: python

    P = lx.Project(mode=<mode>, solver=<solver>)

Currently, three modes are supported:

1. 2D
2. 3D
3. Earth1

And three solvers can be utilized:

1. LSE for least square error
2. LSE_GC for least square error with geometric constraints. Geometric constraints
   force the solutions to be in the intersection areas of all multilateration circles.
3. CCA for the centroid method, i.e., the solution will be the centroid of the
   intersection area. If no common intersection area exists, the area with the
   maximum overlap is used.

To add anchors to the project, use:

.. code-block:: python

    P.add_anchor(<name>, <loc>)

where `name` denotes the user-provided label of the anchor and `<loc>` is the location
of the anchor provided as a tuple, e.g., (120, 60).

To add a target, use:

.. code-block:: python

    t, label = P.add_target()

`T` is the target object, and `label` is the package-provided label for the target.

Distance measurements must be added to the target object like:

.. code-block:: python

    t.add_measure(<anchor_label>, <measured_distance>)

Finally, running `P.solve()` will locate all targets. You can access the estimated
location of the target `t` by `t.loc`. `t.loc` is a point object. Point object `B`
has "x", "y", "z" coordinates available by `B.x`, `B.y`, `B.z` respectively.

Installation
============

Install the package via pip:

.. code-block:: bash

    pip install localization

Contact: kamal.shadi85@gmail.com

An Example
==========

Basic
-----

To be completed:

1. README
2. DOC