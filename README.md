# dbt-metadata

## Why?

As you build out your data assets, it becomes clear that sharing that data between agencies, departments or any other public interface knowing the metadata about what they're interacting with is their first question.

 - how many tables exist in your database?
 - what columns can I expect to see in your table?
 - What's changed between deployments?

It's also possible within larger organisations that a business analyst will spend months studying existing data and documenting it within an excel spreadsheet somewhere online. Skip the spreadsheet and go straight to `dbt`

> Let's expose that great metadata.

Sidenote: It also is interesting that the main function of `dbt` is to interact with your database, yet it stores all metadata about your models in a flat file.

## How do we answer these questions?

By making the metadata availabile to be queried. Both internally within your database, and externally via an API.

## Tasks

 - use `dbt docs generate` to establish the catalog and manifest json files
 - parse the json to retrieve
   - table names
   - column names
 - generate valid SQL to insert that data
 - use `dbt seed` to inject that data into a target database for querying
 - stand up api-gateway in front of database
   - if you use postgres, you could probably just use debezium
 - implement endpoints that returns json data for
   - GET /tables
   - GET /{table_name}/columns 

## TODO
 - [ ] why can't i do this with amundsen.io
 - [ ] something else