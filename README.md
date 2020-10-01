# mass-data-generator

Mass data generator for dev pruposes. This module generates csv data with as many records as needed, 
creating people, credit cards, bank accounts and/or bank transactions fake, data to be used in 
developing, data science or any purposes.

Created data are invented and random, but some data (credit cards) are generated using real world 
validation algorithm.

When generating person data, the [namefake.com](https://namefake.com) API is used. Main module 
may request a proportional number of names and birthdays and mix queried data in order to 
increase performance, reducing requests to the external RESTful service.


&nbsp;  
&nbsp;  
## README Map

<!--- Start with [Set-up and install](#set-up-and-install).-->
- To run interactivelly, go to [Run from command line](#run-from-command-line).
- To run from python shell, skip to [Run from python console](#run-from-python-console).
<!--- For automatic tests, skip to [Automatic tests](#automatic-tests).-->
- About logs, please move to the corresponding topic, [Logs](#logs).
- Instructions on advanced/technical documentation, go to [Documentation](#documentation).
- Or click to skip to the [To do](#to-do) list.

<!--
## Set-up and install
_Note: To run automatically via Docker, Docker Compose or run automatic tests using Makefile, skip this chapter._  
_Note: I recommend using [virtualenv](https://realpython.com/python-virtual-environments-a-primer/) to run py manually._

Install the requirements:

    $ python3 -m pip install -r requirements.txt

Please check the [config file](config.py) to personalise variables as needed.

_Note: The [config file](config.py) should not be in a public repo, but once there are no secret keys in this project, the file was published to facilitate the instantiation. Normally, copying and editing [config template](config.py.tpl) would be recommended._
-->

## Run from command line
From the project's root directory, run the following command and follow instructions:

    python -m datagenerator


## Run from python console

    from datagenerator.Person import Person
    p1 = Person()
    p1.create()
    p1.info()
    p1.csv()

    from datagenerator.CreditCard import CreditCard
    cc = CreditCard(person=p1)
    cc.csv()

    from datagenerator.BankAccount import BankAccount
    acc = BankAccount(person=p1); acc.info()

    from datagenerator.BankTransaction import BankTransaction
    t = BankTransaction(account=acc, value=1000.00, description='Opening deposit'); t.info()
    t = BankTransaction(account=acc, value=-100.00, description='Withdrawl'); t.csv()


<!--## Automatic tests
Python tests are available using unittest via Makefile or manually.  

_Note: to run tests manually, please refer to [Set-up and install](#set-up-and-install) first._  
_Note: to run tests using Makefile, virtualenv must be already installed._  
_Note: depending on how the app is started, it may require ` sudo chmod o+w logs/* `._

Python tests are available manually or using Makefile.

- Run ` python3 -m unittest tests/test_* `.
- Or use make as in ` make test ` to setup, run the tests and clean up.
-->


## Logs
Logs are recorded in the 'logs' directory in the project's root.  
Please see [docs/logs](docs/logs) if you wish to access samples of the generated logs.


## Documentation
See [docs](docs) for documentation. Or run:

    python -c "import datagenerator; help(datagenerator)"
    python -c "import datagenerator.Person; help(datagenerator.Person)"
    python -c "import datagenerator.CreditCard; help(datagenerator.CreditCard)"
    python -c "import datagenerator.BankAccount; help(datagenerator.BankAccount)"
    python -c "import datagenerator.BankTransaction; help(datagenerator.BankTransaction)"


## To do

* Automatic rotation of log files.
* Log classes other than Person.
* Document main module.

