## How to start hacking on ctypesgen

Found a bug? Don't like the way the code is generated? Start experimenting with the code.

Pull code down: `git clone https://github.com/davidjamesca/ctypesgen.git`

## Run test suite

Currently the tests are hard coded to use GNU gcc, and gcc needs to be in the path. The test suite also only works if called from the "test" directory. E.g. assuming in root svn checkout directory, you can run the following example on Windows. (Linux/Unix probably has gcc in the path already)

    path %SystemDrive%\MinGW\bin;%PATH%

... then run test(s):

    cd test
    python testsuite.py 

You may be able to run nose or some other test runner but the test suite simply relies on the batteries included unittest module.