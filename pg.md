Installation
Ubuntu's default repositories contain Postgres packages, so we can install these easily using the apt packaging system.

Since this is our first time using apt in this session, we need to refresh our local package index. We can then install the Postgres package and a -contrib package that adds some additional utilities and functionality:

sudo apt-get update
sudo apt-get install postgresql postgresql-contrib
Now that our software is installed, we can go over how it works and how it may be different from similar database management systems you may have used.

Using PostgreSQL Roles and Databases
By default, Postgres uses a concept called "roles" to handle in authentication and authorization. These are, in some ways, similar to regular Unix-style accounts, but Postgres does not distinguish between users and groups and instead prefers the more flexible term "role".

Upon installation Postgres is set up to use ident authentication, which means that it associates Postgres roles with a matching Unix/Linux system account. If a role exists within Postgres, a Unix/Linux username with the same name will be able to sign in as that role.

There are a few ways to utilize this account to access Postgres.

Switching Over to the postgres Account

The installation procedure created a user account called postgres that is associated with the default Postgres role. In order to use Postgres, we can log into that account.

Switch over to the postgres account on your server by typing:

sudo -i -u postgres
You can now access a Postgres prompt immediately by typing:

psql
You will be logged in and able to interact with the database management system right away.

Exit out of the PostgreSQL prompt by typing:

\q
You should now be back in the postgres Linux command prompt.

