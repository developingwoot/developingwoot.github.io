---
layout: post
title:  "EntityFramework (ef) Commands Overview"
date:   2016-12-13 07:00:00 -0400
comments: true
categories: entityframework tutorial
---

# Entity Framework Commands Overview
---
Code First development using Entity Framework is really helpful.  It allows you to keep your database schema in code.  When you code is controlled by a good VCS like git you have a powerful configuration for development.

However code first development using EF is not without it's pitfalls, and if you are learning it in the school of hard knocks well those pitfalls can be rather painful.  

This post will prevent you from making some of the same mistakes I made.

## Scenario
---
We are developing a point of sale application for a local restaurant that specializes in tacos.

## Goals
- Create a Taco entity 
- Update the database with our taco entity (this will create our Taco table)
- Modify the entity by adding a column
- Update the database
- Revert the changes removing the new column (Why? This will become more clear soon)

## How
### First - Create our Taco Entity
The first step is for us to create our new Taco entity.  This will be created as a table in our database.  As an example it might look something like this:
```c#
public class Taco
{
  public int Id { get; set; }
  public string Name { get; set; }
}
```

### Second - Update the database with our new entity
After we add this entity to our DbContext we are ready to create our migration.  If you are using Visual Studio 2015 you can do this in the Package Manager Console.  Alternately you can do this in PowerShell.

Note: when naming your migrations be sure to name them clearly as this will help immensely down the road.

```c#
c:\>add-migration -name AddTacoEntity
```
To update the database we will need to run the update-database command also in the Package Manager Console

```c#
c:\>update-database
```
Running the command like we did above will run all pending migrations.  When using EF your database will have a table named MigrationHistory.  This table stores all the migrations that have been applied to your database.

If you have more than one migration that needs to be applied the update-database command will run the sequentially until all have been applied.

### Third - Let's add a column to our Taco table
Adding a column to our Taco table is easy.  We just add a property to our Taco entity, create a migration, and update the database.  

#### Add a property to Taco
```c#
public class Taco
{
  public int Id { get; set; }
  public string Name { get; set; }

  // New property
  public string Price { get; set; }
}
```
#### Add migration
```c#
c:\>add-migration -name AddTacoPriceColumn
```
#### Update database
```c#
c:\>update-database
```

Now in your database you will see an additional column for Price in your Taco table.  That covers the basics of how to use ef commands, but it's not all you need to know.  Keep Reading...

### Fourth - Reverting changes
At this point you might be thinking I have already updated my database why would I want to undo the changes.

As an example let's say you are using a VCS and you need to switch from the branch where you have created the new Price column because your customer has asked you to fix a major bug.  

You don't want to lose the work you did, but you're not ready to commit them to master.  If you commit them to a new branch called AddTacoPrice and switch back to master your database will no longer match the entities in your code.  Remember your database still has the Price column, but your code does not.

After you commit your changes to the AddTacoPrice.  Take a look again at the migration that was created to add the Price column.  It might look something like this.

```c#

    namespace Restaurant.Data.Migrations
    {
        using System;
        using System.Data.Entity.Migrations;
        
        public partial class AddTacoPriceColumn : DbMigration
        {
            public override void Up()
            {
                AddColumn("dbo.Tacos", "Price", c => c.String());
            }
            
            public override void Down()
            {
                DropColumn("dbo.Tacos", "Price");
            }
        }
    }

```

Take note of the Up() and Down() methods.  The Up() method will add the column to the database.  When you run the update-database command that is what gets executed.

Since we have committed our changes to our feature branch AddTacoPrice we now need to switch back to master to fix that bug.  Before we do that we need to revert our changes so our database and code will match.  We do this by targeting a migration.

We know that our master branch is on database migration AddTacoEntity, so we need to revert our database to that point in history.

```c#
c:\>update-database -targetmigration AddTacoEntity
```

When you run this command what happens?  Ef will start at the most recent migration and run the Down() method.  Then it goes to the migration just before that, if that migration is not our target migration it will again run down.  If that migration is our target migration the process is halted and our database now matches our master branch.  We are free to fix that bug our customer requested.
