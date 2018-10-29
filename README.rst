jive
----

**author**: `Iain Carmichael`_

Additional documentation, examples and code revisions are coming soon.
For questions, issues or feature requests please reach out to Iain:
iain@unc.edu.

Overview
========

Angle based Joint and Individual Variation Explained (AJIVE) is a
dimensionality reduction algorithm for the multi-block setting i.e. K
different data matrices, with the same set of observations and
(possibly) different numbers of variables. **AJIVE finds joint modes
of variation which are common to all K data blocks as well as modes of
*individual* variation which are specific to each block.** For a
detailed discussion of AJIVE see `Angle-Based Joint and Individual
Variation Explained`_.

An R version of this package can be found `here`_.

Installation
============
To install use pip:

::

    pip install jive


Or clone the repo:

::

    git clone https://github.com/idc9/py_jive.git
    python setup.py install

Example
=======

.. code:: python

    from jive.AJIVE import AJIVE
    from jive.PCA import PCA
    from jive.ajive_fig2 import generate_data_ajive_fig2
    from jive.viz.block_visualization import jive_full_estimate_heatmaps
    # %matplotlib inline

    X, Y = generate_data_ajive_fig2()

    # determine initial signal ranks by inspecting scree plots
    PCA().fit(X).plot_scree()
    PCA().fit(Y).plot_scree()

    ajive = AJIVE(init_signal_ranks={'x': 2, 'y': 3})
    ajive.fit(blocks={'x': X, 'y': Y})

    plt.figure(figsize=[10, 20])
    jive_full_esimate_heatmaps(ajive.get_full_block_estimates(),
                               blocks={'x':X, 'y': Y})


For some more example code see `this notebook`_.

Help and Support
================

Additional documentation, examples and code revisions are coming soon.
For questions, issues or feature requests please reach out to Iain:
iain@unc.edu.

Documentation
^^^^^^^^^^^^^

The source code is located on github:
`https://github.com/idc9/py\_jive`_. Currently the best math reference
is the `AJIVE paper`_.

Testing
^^^^^^^

Testing is done using `nose`_.

Contributing
^^^^^^^^^^^^

We welcome contributions to make this a stronger package: data examples,
bug fixes, spelling errors, new features, etc.

Citation
^^^^^^^^

A `Journal of Statistical Software`_ paper is hopefully coming soon…

.. _Iain Carmichael: https://idc9.github.io/
.. _Angle-Based Joint and Individual Variation Explained: https://arxiv.org/pdf/1704.02060.pdf
.. _here: https://github.com/idc9/r_jive
.. _this notebook: doc/jive_demo.ipynb
.. _`https://github.com/idc9/py\_jive`: https://github.com/idc9/r_jive
.. _AJIVE paper: https://arxiv.org/pdf/1704.02060.pdf
.. _nose: http://nose.readthedocs.io/en/latest/
.. _Journal of Statistical Software: https://www.jstatsoft.org/index
