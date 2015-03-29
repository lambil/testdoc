
.. code:: robotframework

   *** Settings ***

   Documentation     A test suite with a single test for valid login.
   ...
   ...               This test has a workflow that is created using keywords in
   ...               the imported resource file.


   Resource          resource.txt

   *** Test Cases ***
   Valid Login
       Open Browser To Login Page
       Input Username    demo
       Input Password    mode
       Capture page screenshot  robotframework.png
       Submit Credentials
       Welcome Page Should Be Open
       Capture page screenshot  pageopen.png
       [Teardown]    Close Browser
