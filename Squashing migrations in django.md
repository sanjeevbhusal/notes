
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
- Django will then compare if the migration files in code are present in `django_migration` table or not. 
- If a migration file is present in code but not `django_migrations`, django will then apply that migration and also update the `django_migrations` table.
- If  `django_migrations` has record that is not present in the code, nothing happens. Django just checks if all migration files are present in `django_migrations` table and not vice-versa. 

Lets see the same scenario with squashed migrations.

- You run `python manage.py squashmigrations <appname> 0004`. This will create a migration file that has all the operations of all the migration files that are squashed. Lets call the migration file as `0001_squashed_file`
- You run `python manage.py migrate` command. Like described above, this will compare all the migration files in code with `django_migrations` table. Since the new squashed migration file is not present in `django_migrations` table, it should be applied to database and also added to `django_migrations` table. However, if you apply the migration file, you will get a error since all the operations had already been applied by the files that were squashed. Hence, django won't apply the changes to database and only add the file to `django_migrations`. As discussed above, django knows that this is a squashed migration file due to the presence of `replaces` field.
- Now, we delete all the normal migration files that are referenced by the squashed migration file and remove the replaces field of the squashed migration file. 
- Now, we run `python manage.py migrate` command. Like described above, this will compare all the migration files in code with `django_migrations` table. Since we removed all the squashed migration files