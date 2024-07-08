
To squash migrations in django, you should run the command

`python manage.py squashmigrations <appname> 0004`

This command will squash all migrations that come before 0004 into a single migration file. This migration file has one difference to a normal migration file. This migration file contains a property called `replaces`  that stores names of all the existing migration files that this squashed migration file replaces.

![[Pasted image 20240708104641.png]]

Now, you can run `python manage.py migrate` command. The output of this command will tell you that there are no migrations to run. This is true since this squashed migration doesnot really do any operations in database. However, in `django_migrations` table, this squashed migration will be added. Also, there is no field in `django_migrations` table to mark this migration as a squashed migration. The `replaces` field is the only one that is marking this as a squashed migration.

Now, 
- remove all the migrations files from code that this replaces array contains. 
- Then remove the replaces field from this squashed migration. This marks the migration as a normal migration and not a squashed migration.

Now run `python manage.py migrate` command. he output of this command will tell you that there are no migrations to run. This is true since we just deleted existing migration from code and updated the squashed migration file to be a normal migration file.  