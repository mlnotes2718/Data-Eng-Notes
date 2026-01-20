# meltano Cheatsheet (update Dec 2025)

## Setting up meltano Projects
Use the following command:
- `meltano init <project-name>`
- `cd <project-name>`

Example:

- `meltano init meltano-ingestion`
- `cd meltano-ingestion`


## meltano Connection
- meltano is a pipeline that connect between different data resource.
- It can be different database, or between a file and a database. Irregardless, they are called data resource.
- A data resource can be a source or destination.
- In meltano, for source, we use `tap` as the prefix.
- For destination, we use `target` as the prefix.
- The rest is just setting up the configuration.
- meltano can be very difficult or very easy. It depends on your data source and its connectors.
- Some data source requires very complex settings, some are very easy such as duckDB.

## Creating Data Source (tap)
- We use the command `meltano add tap-<SOURCE_NAME>` where the source name can be any data source. Please search the meltano website for all the available connectors.
- All data source are prefix `tap`. A datasource such as postgres can be source and destination.
- Listed are some possible data source: [`tap-github`, `tap-csv`, `tap-duckdb`, `tap-postgres`]
- Next we need to configure the data source using the command shown below:
```zsh
meltano config set tap-<SOURCE_NAME> --interactive
```
- An interactive menu will be shown and you can choose which option to set.
- Alternatively, we can also use command line as shown below
```zsh
meltano config set tap-<SOURCE_NAME> <SETTINGS> [value]
```
- Use the following to list all configuration
```zsh
meltano config list tap-<SOURCE_NAME>
```

- Once the setup has been done, for data source it provide a testing tool. Most extractor got the testing tool. You need to search the web for the respective connector to confirm. The command of the test is usually in the format below:
```zsh
meltano config test tap-<SOURCE_NAME>
```

- In addition, meltano also allows data selection using the command `select`.
- Use the following command to list down all data items that we can pick:
```zsh
meltano select tap-<SOURCE_NAME> --list --all
```

```zsh
meltano select <plugin> <entity> <attribute>
```
- The following example allows the extractor to select only some resource.
```zsh
meltano select tap-github releases tag_name
meltano select tap-github releases body
meltano select tap-github releases published_at
```

- Use the following command to list down all data items that we had selected:
```zsh
meltano select tap-<SOURCE_NAME> --list
```

## Creating Data Destination (target)
- We use the command `meltano add target-<TARGET_NAME>` where the target name can be any data source. Please search the meltano website for all the available connectors.
- All data destination are prefix `target`. A datasource such as postgres can be source and destination.
- Listed are some possible data source: [`target-bigquery`, `target-postgres`, `target-jsonl`]
- Next we need to configure the data destination using the command shown below:
```zsh
meltano config set target-<TARGET_NAME> --interactive
```
- An interactive menu will be shown and you can choose which option to set.
- Alternatively, we can also use command line as shown below
```zsh
meltano config set target-<TARGET_NAME> <SETTINGS> [value]
```
- Use the following to list all configuration
```zsh
meltano config list tap-<TARGET_NAME>
```

## Running Meltano Pipeline
Once the data source and destination are set. We can run the pipeline as:
```zsh
meltano run tap-<SOURCE_NAME> target-<TARGET_NAME>
```
- For any errors please refer to the log file under the folder .meltano
- As mention earlier, most errors are configuration for each data connectors.

Some examples:
- `meltano run tap-github target-jsonl`
- `meltano run tap-github target-bigquery`
- `meltano run tap-postgres target-bigquery`
- `meltano run tap-duckdb target-postgres`
- `meltano run tap-duckdb target-bigquery`

## Common Extractor and Configuration 

### tap-github

Add extractor:
```zsh
meltano add tap-github
```

Set configuration:
```zsh
meltano config set tap-github --interactive
```

Essential settings:
- auth_token=token provided by Github
- repositories=repository


Set individual settings:
```zsh
meltano config set tap-github repositories ["pandas-dev/pandas"]
```

Show all configurations:
```zsh
meltano config list tap-github
```

Test configuration
```zsh
meltano config test tap-github
```

**Data Selection (Only for Data Source)**:

We can list all available data item to be extracted
```zsh
# List all available data item
meltano select tap-github --list --all
```

Select data items:
```zsh
meltano select tap-github <entity> <attribute>
#####
meltano select tap-github releases tag_name
meltano select tap-github releases body
meltano select tap-github releases published_at
```


List selected data
```zsh
# List selected data item
meltano select tap-github --list
```

Reference:
- https://hub.meltano.com/extractors/tap-github/

### tap-duckdb
Add extractor:
```zsh
meltano add tap-duckdb
```

Set configuration:
```zsh
meltano config set tap-duckdb --interactive
```

Essential settings:
- Option 3: path=/Users/USER/location_of_your_duckdb.mydb.db


Show all configurations:
```zsh
meltano config list tap-duckdb
```

Test configuration
```zsh
meltano config test tap-duckdb
```

Reference:
- https://hub.meltano.com/extractors/tap-duckdb


### tap-postgres
Add extractor:
```zsh
meltano add tap-postgres
```

Set configuration:
```zsh
meltano config set tap-postgres --interactive
```

Essential settings:
- Option 5: database=postgres
- Option 10: filter_scheme=['public']
- Option 13: host=aws-0-us-west-1.pooler.supabase.com
- Option 16: password=reducted
- Option 17: port=5432
- Option 35: user=postgres.random_nodes



Show all configurations:
```zsh
meltano config list tap-postgres
```

Test configuration
```zsh
meltano config test tap-postgres
```

Reference:
- https://hub.meltano.com/extractors/tap-postgres



## Common Loader and Configuration

### target-jsonl
Add loader:
```zsh
meltano add target-jsonl
```
Note: There are many variants for jsonl

Set configuration:
```zsh
meltano config set target-jsonl --interactive
```

Essential settings:
- destination_path=/location_of_destination/  (default is /output)

Show all configurations:
```zsh
meltano config list target-jsonl
```

Reference:
- https://hub.meltano.com/loaders/target-jsonl


### target-bigquery
Add loader:
```zsh
meltano add target-bigquery
```
Note: There are many variants for jsonl

Set configuration:
```zsh
meltano config set target-bigquery --interactive
```

Essential settings:
- Option 10: credentials_path=/Users/USER/.dbt/my_service_key.json
- Option 11: dataset=my_dataset_name
- Option 13: denormalized=True
- Option 15: flattening_enabled=True
- Option 16: flattening_max_depth=1
- Option 19: method=batch_job
- Option 26: project=my_bigquery_project

Show all configurations:
```zsh
meltano config list target-bigquery
```

Reference:
- https://hub.meltano.com/loaders/target-bigquery



### Additional Resources:
- https://docs.meltano.com/getting-started/part1
- https://docs.meltano.com/guide/integration/#selecting-entities-and-attributes-for-extraction