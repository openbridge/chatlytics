# Chatlytics
This project is meant to use chat as an interface to a simple bot which can be used to run SQL queries on data. These queries ultimately output images of the data charts into the chat window.

## Prerequisites
You will need:
* Database connection parameters. Currently only `PostgreSQL`, `MySQL`, `Amazon Redshift`, `Amazon Aurora (Postgres/MYSQL)` and `AmazON RDS (Postgres/MYSQL)` are supported)
* Slack account for the bot to use. If you do not have one you need to get yourself a Slack account. Go to the Slack webite: https://slack.com/


## How To Interact With Fetch, Your Analytics Bot

### Step 1: Add To Slack

The first step required to set the bot up involves clicking the "Add to Slack" button [here](https://www.chatlytics.co).

Chatlytics is only available for use with Slack at the moment. Other chat clients (Hipchat, Facebook, Skype...) will be added soon!

Once you have connected Chatlytics, you can interact with Fetch by sending commands to the linked Slack account.

### Step 2: Setup Your Database connection
You'll want to start by setting up your database connection. Run the commmand `!dbconfig` and follow the prompts to get started.

### Step 3: Ask Fetch To Run Queries For You

Fetch has built-in set of commands it understand. To see a list of available commands Fetch can recognize, type `!help`.

The following is a list of available predefined commands:
* `!list_tables`: Returns a list of all tables in the database.
* `!table_count <table_name> <number_of_days>`: Returns the number of rows in the table.
* `!count_compare <table_name> <date_column> <time_interval> <style>`: Compare record count to the previous day.
* `!date_compare <table_name> <date_column> <date1> <date2> <style>`: Compare record count of two different days.
* `!chart <table_name> <date_column> <number_of_days> <style>`: Generate a bar chart of record counts from the specified table for the given number of days.

# Teaching Fetch Custom Commands
In addition to the predefined commands Fetch understands, you can teach it new ones. This is done by feeding Fetch YAML files.  

How do you train Fetch to understand new commands. There are three easy steps:

* Define Your Command In YAML
* Your Train Fetch To Understand The Commands
* You Ask Fetch To Run Your Commands


### Step 1: Defining Custom Commands Via YAML File
To teach Fetch a new command, you need to first create a YAML definition. This is what a sample YAML definition looks like:

```
queries:
    -   name: test_query
        query: select testColumn, count(*) from testTable group by testColumn
        chart_type: bar_chart
        chart_description: test
        style: blue
```

Each element serves a purpose in helping Fetch understand what you want to have happen:

* `name`: The name of the query. This ultimately becomes the command you use to call the query once it's defined.
* `query`: The SQL query to run.
* `chart_type`: The type of chart which you wish to generate. Currently, valid inputs are "bar_chart", "line_chart" and "table".
* `chart_description`: This description will be included when your query is run.
* `style`: the name of the style which you want the output to use

When writing custom queries for `bar_chart` or `line_chart` graph types, it is expected that the first column will be the x-axis and the second will be the y-axis.

### Step 2: Train Fetch To Understand Your Command
With your YAML file completed, it is time to teach Fetch the new command. This will require that you import or "feed" the YAML file to Fetch. There are three methods for feeding Fetch new commands:

* Drag-and-Drop
* Attachments
* Remote Import from URL

#### Drag-and-Drop
#### Attachments
#### Remote Import from URL

To import a remote YAML file from someplace like Github, you must specify a URL to that YAML file in the following format:

`!define <link_to_yaml>`

For example, if the link is from GitHub you'll need to click the **Raw** button at the top of the file and use the resulting URL.

`!define https://raw.githubusercontent.com/dtroberts/TestRepo/master/ymls/multidef.yml`


### Step 3: Tell Fetch To Run Your New Commands

Once the query is defined and imported, it will be accessible via `!name`, where name is the value of the `name` field in the YAML file.

we need examples

**IMPORTANT**: Custom commands are removed upon shutting down or restarting servers. In a future release we will add persistence capabilities when training Fetch.

# Notes

### MySQL
MySQL connections cannot be opened in read-only mode. As such, any query defined here can be run on the database. The best solution to ensure the security and integrity of your database is to create a new user for use with Chatlytics with read-only permissions and specify those credentials in `!dbconfig`.

For instructions on how to set up a read-only user, see the [guide](http://www.alphadevx.com/a/388-Adding-a-read-only-MySQL-user).

# Issues

If you have any problems with or questions about this image, please contact us through a GitHub issue.

# Contributing

You are invited to contribute new features, fixes, or updates, large or small; we are always thrilled to receive pull requests, and do our best to process them as fast as we can.

Before you start to code, we recommend discussing your plans through a GitHub issue, especially for more ambitious contributions. This gives other contributors a chance to point you in the right direction, give you feedback on your design, and help you find out if someone else is working on the same thing.
