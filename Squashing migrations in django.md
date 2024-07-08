
To squash migrations in django, you should run the command

`python manage.py squashmigrations <appname> 0004`

This command will squash all migrations that come before 0004 into a single migration file. This migration file has one difference to a normal migration file. This migration file contains a property called `replaces`  that stores names of all the existing migration files that this squashed migration file replaces.

![[Pasted image 20240708104641.png]]

Now, you can run `python manage.py migrate` command. The output of this command will tell you that there are no migrations to run. This is true since this squashed migration doesnot really do any operations in database. However, in `django_migrations` table, this squashed migration will be added. Also, there is no field in `django_migrations` table to mark this migration as a squashed migration. The `replaces` field is the only one that is marking this as a squashed migration.

Now, 
- remove all the migrations files from code that this replaces array contains. 
- Then remove the replaces field from this squashed migration. This marks the migration as a normal migration and not a squashed migration.

Now run `python manage.py migrate` command. the output of this command will tell you that there are no migrations to run. This is true since all we did was to delete existing migration from code and updated the squashed migration file to be a normal migration file.  

When you run `python manage.py migrate` command, 
- Django will get all the applied migrations information  from `django_migrations` table.
- Django will then get all the migration files from the code. 
- Django will compare if the records in `django_migrations` are exactly same as migration files in code including dependencies. 
- If `django_migrations` has record that is not present in the code, 
- available in the latest django will compare the last applied migration from `django_migrations` table to see the new migrations added to your code. Then, django will apply only the updated migrations to the database and also update the `django_migrations` table to update the recent migration files.

So, when you remove the existing migration files from your database and apply python manage.py migrate, you will see no changes made. 