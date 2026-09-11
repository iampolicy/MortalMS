## Client & Data

This repo contains the server-side nonsense, but the client and the raw \*.nx
data are another story.

* Client: JourneyClient
* NX data: TODO

## Development Status

Probably not active (who knows).

## Disclaimers

This server source is **not intended to be stable** as-is. Security audits/pen
testing/stress testing, proper deadlock review, and other maintenance checks
are needed in order to make it suitable for production use.

> THERE IS NO WARRANTY FOR THE PROGRAM, TO THE EXTENT PERMITTED BY APPLICABLE
> LAW. EXCEPT WHEN OTHERWISE STATED IN WRITING THE COPYRIGHT HOLDERS AND/OR
> OTHER PARTIES PROVIDE THE PROGRAM "AS IS" WITHOUT WARRANTY OF ANY KIND,
> EITHER EXPRESSED OR IMPLIED, INCLUDING, BUT NOT LIMITED TO, THE IMPLIED
> WARRANTIES OF MERCHANTABILITY AND FITNESS FOR A PARTICULAR PURPOSE. THE
> ENTIRE RISK AS TO THE QUALITY AND PERFORMANCE OF THE PROGRAM IS WITH YOU.
> SHOULD THE PROGRAM PROVE DEFECTIVE, YOU ASSUME THE COST OF ALL NECESSARY
> SERVICING, REPAIR OR CORRECTION.

## Setup

The "posix-compile.sh" and "posix-launch.sh" files assume that the programs
named "java" and "javac" in your path refer to the OpenJDK implementations of
the Java virtual machine version 10+, and the Java compiler version 10+,
respectively.

Run `./posix-compile.sh` to compile the server code.

Start up MariaDB and execute the provided "db_database.sql" and "db_drops.sql"
scripts, **in that order**. (Hint: in the MariaDB/MySQL command line, that
looks something like: `source /the/full/path/to/your/db_database.sql;`)
Optionally, you can also then execute "db_shopupdate.sql", although this script
is only provided as-is from the original HeavenMS and is not expected to be
useful.

At the end of the execution of the SQL scripts, you should have installed a
database schema called "heavenms". Register your first account to be used
in-game by **manually creating** an entry in the table "accounts", with a name
and a password.

Create your own blank configuration template by copying
"configuration.ini.template" to "configuration.ini". Configure the IP you want
to use for your MapleStory server in your own "configuration.ini" file, or set
it as "localhost" if you want to run it only on your machine. Also make sure
that the username and password for your MariaDB login are correct.

You should now be able to start the server by executing `./posix-launch.sh`.
