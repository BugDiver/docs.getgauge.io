HOWTO: Integrating Gauge with TeamCity
======================================

-  `Download <http://getgauge.io/get-started/index.html>`__ and Install
   Gauge on the agents. Read more on installing Gauge
   `here <http://getgauge.io/documentation/user/current/installations/operating_system/>`__.
-  Install the required Gauge :ref:`language plugins <plugins-installation>` on
   the agents as: ``gauge --install <language>``

Tips on Installation
--------------------

-  Gauge is installed system wide by default and not user wide. However,
   plugins are installed per user. So plugins should be installed via
   user account with which the TeamCity agent executes. Refer default
   install location of Gauge and its plugins
   `here <http://getgauge.io/documentation/user/current/troubleshooting/installation.html>`__.

-  Alternately, you can set `custom location for
   plugins <http://getgauge.io/documentation/user/current/troubleshooting/installation.html#custom-plugin-install-location>`__
   so that its accessible to TeamCity agent running as a different user.

Create execution task
---------------------

-  Create a new project in TeamCity pointing to Gauge project repository
   URL.
-  Add a build step which will run ``gauge specs``. 
    image:: images/TeamCity_buildStep.png

-  If you want to run only a subset of specs, you can use :ref:`tagged_execution`. 
    Eg. ``gauge --tags "tag1 & tag2" specs``
-  Adding a flag ``-p`` runs them using :ref:`parallel_execution`.
-  Run against specific :ref:`environments` using the ``--env`` flag.
-  See the :ref:`cli_flags` for list of all flags that can be used.

Reports
-------

-  Gauge generates **html-reports** after execution which can be
   configured in TeamCity by adding a new artifact in Artifacts tab.
   These artifacts can be viewed/downloaded from the artifacts tab.

   .. figure:: images/TeamCity_Artifact.png
      :alt: artifact

      artifact

-  You can also add a `custom
   tab <https://confluence.jetbrains.com/display/TCD9/Including+Third-Party+Reports+in+the+Build+Results>`__
   to view your html reports generated.

   To add custom tab, go to Project Settings -> Report tabs -> Add a new
   build report tab.

   .. figure:: images/TeamCity_ReportTab.png
      :alt: report tab

      reportsTab

-  **Console output** can be seen while execution of steps and reports
   can be seen after execution.