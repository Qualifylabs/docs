.. _fileupload:

Test Data File Upload
=====================

Qualify reporting site allow users to upload their test data files as in zip format. 
These .zip files are extracted and used by Parser in order to be used by executor devices.


Basic Principle
---------------

Test data file parser look for ``variables.py`` and ``arguments.txt``

  - ``variables.py`` is used as `variablefile <http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#variable-file>`_ of Robot Framework.
  - ``arguments.txt`` is used as `argumentfile <http://robotframework.org/robotframework/latest/RobotFrameworkUserGuide.html#argument-files>`_ of Robot Framework.

Argument file shall indicate which suites/tests to run. It is suggested that name of test data file
is given correspondingly.


Appium Tests
------------

Robotframework `AppiumLibrary <http://jollychang.github.io/robotframework-appiumlibrary/doc/AppiumLibrary.html>`_ sessions should start with ``Open Application`` keyword. 

Qualify has predefined **VARIABLES** for ``Open Application`` desiredCapabilities. It is 
mandatory that ``Open Application`` has these argumenents regardless of their values.

.. Note::

  For more information on Appium desiredCapabilities, please visit `Appium documentation <http://appium.io/slate/en/master/?java#appium-server-capabilities>`_.


======================  ==============================  ===============================================
Appium Server Argument  Mandatory Variable of Qualify   Description
======================  ==============================  ===============================================
app                     APP                             | Appication upload url, this will be 
                                                        | automatically given by uploaded application.
---                     REMOTE_URL                      Automatically given by Parser, but should be present
browserName             BROWSER                         
automationName          AUTOMATION_NAME                 
deviceName              DEVICE_NAME                     
platformName            PLATFORM_VERSION                
======================  ==============================  ===============================================

Example Usage:

.. code-block:: robotframework
  
  *** Test Cases ***
  Open Application  ${REMOTE_URL}  automationName=${AUTOMATION_NAME}
  ...  platformName=${PLATFORM_NAME}  platformVersion=${PLATFORM_VERSION}
  ...  browser=${BROWSER}  deviceName=${DEVICE_NAME}  app=${APP}



