# DBT CERT

Repository created to keep a track of all courses done to get dbt Analytics Engineering  Certification

The guide to follow is [this](https://www.getdbt.com/assets/uploads/dbt_certificate_study_guide.pdf).

## PRE-REQUISITES

Regardless, technical knowledge, you must install:

- Docker (we will use a postgres image)
- Python (in our case Python 3.9.7)

## FIRST STEPS

You can see changes [here](https://github.com/davidmunoz4185/dbt_cert/pull/1/files).

### DATABASE SETUP

Start a Postgres Database using docker:

```bash
docker compose up -d
```

It will create the directory _postgres-data-db-volume_ where postgres stores data and metadata database.

You can check everything is ok connecting with following config:

- __host__: localhost
- __port__: 6432
- __user__: postgres
- __pass__: postgres
- __db__: dbt

### PYTHON INSTALL REQUIREMENTS

Verify your python version

```BASH
python --version
Python 3.9.7
```

Create a virtual env

```BASH
python -m venv .env
```

Activate virtual env

```BASH
source .env/Scripts/activate
```

Upgrade pip

```BASH
pip install --upgrade pip
```

Install requirements

```BASH
pip install -r requirements.txt
```

### INIT DBT PROJECT

```BASH
dbt init
08:36:03  Running with dbt=1.7.7
Enter a name for your project (letters, digits, underscore): dbt_get_certification
08:36:52  
Your new dbt project "dbt_get_certification" was created!

For more information on how to configure the profiles.yml file,
please consult the dbt documentation here:

  https://docs.getdbt.com/docs/configure-your-profile

One more thing:

Need help? Don't hesitate to reach out to us via GitHub issues or on Slack:

  https://community.getdbt.com/

Happy modeling!

08:36:52  Setting up your profile.
Which database would you like to use?
[1] postgres

(Don't see the one you want? https://docs.getdbt.com/docs/available-adapters)

Enter a number: 1
host (hostname for the instance): localhost
port [5432]: 6432
user (dev username): postgres
pass (dev password): 
dbname (default database that dbt will build objects in): dbt
schema (default schema that dbt will build objects in): public
threads (1 or more) [1]: 1
08:37:38  Profile dbt_get_certification written to C:\Users\Bluetab\.dbt\profiles.yml using target's profile_template.yml and your supplied values. Run 'dbt debug' to validate the connection.
```

#### Things to consider

__profiles.yml__ File: File where connection config is stored 4 your dbt project.

__dbt_get_certification/dbt_project.yml__ File: File where project config is stored.

### DEBUG PROJECT

Validate connection

```BASH
cd dbt_get_certification
dbt debug
```

You must see something similar to

```BASH
Connection test: [OK connection ok]

All checks passed!
```

Now you can start with the certication

## PREPARE PROJECT

You can see changes [here](https://github.com/davidmunoz4185/dbt_cert/pull/2/files).

Before starting with coding, lets prepare our dbt project to follow the different courses:

- Remove _models/example_ folder
- Delete any example ref in _dbt_project.yml_
- Add seed files

### ADD RAW DATA

Load seed files in postgres

```BASH
dbt seed
```
