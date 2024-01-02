# PetLove
automation for petlove

## Environment Setup

Before running or developing test cases, it is recommended to use a virtual environment.

``` bash
virtualenv venv
source venv/bin/activate
pip install -r requirements.txt
rfbrowser init
```

Initiating the rfbrowser for the first time might take some time due to installing node dependencies. These need to be done only once, after which the venv can be activated with just the command:

``` bash
source venv/bin/activate
```

If VS Code is used, it will also prompt to use the venv automatically so this step won't be necessary later.

### Environment Variables

Environment variables, mostly secrets at this point, will be saved in .env file that must not be pushed to git at any time! To set your environment up, do following:

Rename .env_remove_this to .env

``` bash
mv .envREMOVE .env
```

Fill in missing environment variables to file or export them manually. And run setenv script.

``` bash
./setenv.sh
```

## Python Versions

Let's use Python 3.10 for this project. You can check your version using the following cmd.

```python --version
```

If you have multiple Python's installed, create a virtualenvironment like this:

``` bash
python3.10 -m venv /path/to/new/venv
source /path/to/new/venv
```

Check the version again with:

``` bash
python --version
```

## Folder Structure

[testsuites](/testsuites/) is the main folder for all test suite files ie. anything ending .robot.

[resources](/resources/) is the main folder for libraries, variables, python files, other files, anything that is used in the test cases. For now, resources are divided into [keywords](/resources/keywords/), [libraries](/resources/libraries/) and [variables](/resources/variables/).

Test Suites are divided into [MUI](/testsuites/MUI/), [BUI](/testsuites/BUI/) and [API](/testsuites/API/) and new test cases should be added accordingly.

All of the above are divided into features and regression tests. Feature tests can be named for example with the Jira Ticket number and ordered to subfolders like [OnlineCheckIn](/testsuites/MUI/feature/OnlineCheckIn/). This will be up to you in later phases to see what works best.

## Test Suite and Test Case Naming

Test suites should be named in a brief, yet explanatory manner and they should be consistent within the naming and casing. In Robot Framework, generally snake_case is used for everything, but I would keepi Jira tickets as they are (BUI-556.robot instead of snake case like bui_556.robot).

## Variables

It is generally desirable to use variables instead of strings in Test Cases which should be kept clear from any "code like" syntax. This can be prevented by using keywords and variables.

Regarding casing, I have now started to use camelCase for general variables and UPPERCASE for environment variables and secrets. There is no right or wrong here, just what is preferred. However, I suggest it is kept consistent as well.

## Running Tests

Before running tests, you will need to set some environment variables. That can be done by running tests with.
