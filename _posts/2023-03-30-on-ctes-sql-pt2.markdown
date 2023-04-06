---
layout: post
title: "Part 2: No Love for SQL"
date: 2023-03-30
categories: sql
---

Why do folks not like SQL? Regardless of domain developers appear allergic to the  idea of writing SQL - there’s zero enthusiasm.

This lack of excitement can be topped - simply ask someone to maintain SQL that a current/former colleague/lover wrote. The only similar reponse I’ve seen is when asking to maintain some Perl code that the psycho down the hall wrote! Horror. Revulsion. Tears and tantrums. Why me? Have I done something to hurt you?

> fwiw I wrote Perl and SQL for a chunk of my life. I regret nothing, but I do resent you Dave

I get why SQL isn’t loved, or I think I can appreciate why it triggers an upchuck reflex. SQL isn’t new, it’s been around forever (50ish years), it’s tried and tested. It’s boring.

There are a few things that jump to mind when looking at SQL Pain Points:

* __harsh learning curve__: Despite the work done by Chamberlain and Boyce, you have to understand the underlying data model, structures and relationships. It’s not uncommon for schemas to be somewhat sprawling, it’s often time-consuming to build a mental model, which is a big cognitive load.

* __Code is often repetitive and deeply nested__: A couple hundred lines of Python/Scala/Java and you’re fine. 100+ of SQL? No, no thanks - you’re unlikely to have test support and those SQL errors … I would rather fight the borrow checker.

* __Multiple syntax and dialects__: Not all SQL is equal, sometimes the changes between dialects is minimal, other times not. Hopping between databases can be frustrating - it’s yet another thing to deal with when __I JUST WANT THE F*CKING DATA, PLEASE DATABASE GODS.__

* __It’s declarative__: You write what you want the database to do, not how to do it. It can feel hard.

* __Evolving databases__: There’s a chance you’ll change the database, perhaps it’s best to throw in an abstraction like an Object-relational mapping like SQLAlchemy, Hibernate or Diesel? Coupled applications and databases make long-running structure/data changes harder to handle and test. I really don’t like ORMs.

* __Testing__: Love or hate TDD, in the long run, testing makes the development cycle smoother. Testing in SQL isn’t as mature as it is in Python or Scala … or Perl.


### The pain can’t be disappeared, it can be reduced.

I was late to the Common Table Expressions _(CTEs)_ party. I don’t remember when I found them but I’ve found them to be a wonderful addition to the toolbox. CTEs provide a big improvement to quality of life when SQL-ing.

* They enable code to be broken down into smaller more manageable pieces, improving readability and reducing maintenance burden

* They enable recursive queries. This is where a query refers to its own output. If you have some logic that needs to traverse a tree or
graph then CTEs will make your code much easier to understand.

* They’re similar to derived tables, but can be referenced multiple times within themselves.  This grants greater flexibility and reduces repetition.

That said, CTEs aren’t a silver bullet.  They’re still just queries, as such, they can be inefficient and have a negative impact on a database and end-user experiences.

> To understand the performance of queries you can use EXPLAIN, I will cover improving queries and database management in another post.

__BUT__ the biggest win for me is that they paved the way for [dbt](https://docs.getdbt.com/docs/introduction), and if you aren’t using dbt for your database transformations you are missing out. I am going to do a series of posts and intro videos on using dbt, from simple models, removing duplications with macros and testing.

With this said, and despite the availability of great tools like [duckdb](https://duckdb.org/) and [Litestream](https://litestream.io/), it's unlikely that SQL will suddenly become everyone's favourite language. However, with these powerful tools at your disposal, you should definitely consider diving into SQL and pushing through any difficulties. Who knows, you might even end up loving it!
