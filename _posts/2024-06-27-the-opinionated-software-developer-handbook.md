---
layout: post
title: "The Opinionated Software Developer Handbook: Code for Your Future Self"
---

https://www.reddit.com/r/programming/
Do you hate making decisions that you shouldn't have to make?
This is hopefully a great resource for saving you and your team time and energy.

Table of Contents

- Do not remove this line (it will not be displayed)
  {:toc}

Let's get started.

## Why Opinionated?

Why is it helpful to have an opinionated software developer handbook?
As Software Developers, we have so many decisions to make every day.
It takes time to make decisions.
It takes energy.
In many cases, we need to consult members of our team for their input.
If the decision is around the core of your product or service, the time you spend discussing it and forming consensus can be worthwhile.
If it is not, the team's valuable time and energy is consumed.
This is even more important in the context of a startup, where limited resources are the rule.
But ideally, we should always respect not only our time but also the time and opportunity cost of our teammates.
If you do not consult members of your team to collect input before making the decision, that does not mean that they don't have input.
They have their own opinions based on their own experience, these may be strongly-held, and they may differ from yours.
This can lead to discussions and rework down the road, and it might be even more costly than the upfront discussions that you thought you had been able to avoid.

To the extent that we can delegate the decisions that are not at the core of our business, we can be more efficient and we can create codebases that are more internally consistent.
As an industry, we might even be able to find a small set of rules that we can agree on across organizations and codebases.
The aim of this work is to push in that direction.

## Linters

Use linters.
Especially on larger projects that will have a long life span, using linters is one of the primary ways to ensure consistency within the codebase (and you might even find some bugs).
Start with the most popular linters for whatever programming language or framework you are using.
This might be RuboCop for Ruby or ESlint for Javascript.
Configure the linter to stop enforcing rules that you and your teammates find detestable, and ideally learn how to add your own linting rules to codify the conventions your team uses that go above and beyond the built-in rules for the linter.
There might be other linters that are less popular that can also add value.
Don’t necessarily stop at just one.
The nice thing about most linters is that they can analyze your entire codebase in a fraction of the time it takes to run your unit tests.
Run these linters all the time–on developer machines and in CI–such that new code is not approved unless it passes all agreed-upon linting rules.
Use line length 119 because 80 and 88 force so many lines to wrap that it is visually distracting.

## Autoformatters

This goes hand in hand with linters, and some linters are also autoformatters.
Golang has the built-in gofmt.
It’s documentation says:

> Gofmt is a tool that automatically formats Go source code.
>
> Gofmt’d code is:
>
> - _easier to write_: never worry about minor formatting concerns while hacking away,
> - _easier to read_: when all code looks the same you need not mentally convert others’ formatting style into something you can understand.
> - _easier to maintain_: mechanical changes to the source don’t cause unrelated changes to the file’s formatting; diffs show only the real changes.
> - _uncontroversial_: never have a debate about spacing or brace position ever again!

This is pretty much the pitch of this entire document.
Formatters are the most opinionated tools around.
They don’t ask questions.
They just change all the code to make it the way they want.
This can be unpleasant, especially at first, when you are not used to the style.
Hopefully the emotions this evokes will change over time, from boiling anger to simmering anger to minor annoyance to acceptance to appreciation.
But in the meantime, it's a lot better to be angry at formatters than at your teammates.

## Tests

Write automated tests for your code.
Make sure they run very fast.
Some people shoot for [running the entire suite in under a second](https://www.artima.com/weblogs/viewpost.jsp?thread=126923).
Whether this is realistic, or whether you should try to avoid hitting resources like the database or the filesystem during unit test execution is a common debate, but if your suite takes minutes to run, understand that there are probably lots of people with tests that are similarly thorough and much faster.
Investments to improve the execution time of your test suite will likely pay off as many developers run the suite over time.

## Naming

For variables and functions, prefer longer, more descriptive names over shorter names and abbreviations.
Avoid one-character variable and function names.
These are hard to search for and hurt code readability.
Even for loop variables, prefer `ii` and `jj` over `i` and `j`.
At least the two-character forms are more searchable.
Put units in variable names ([reference](https://ruudvanasseldonk.com/2022/03/20/please-put-units-in-names)).
Classes and objects should be nouns.
Functions should be verbs or verb-noun pairs (Clean Code, Robert C. Martin).
If you are doing something zero-indexed, use the word index (userIndexWithinArray).
If you are doing something one-indexed, use the word number (file_number_within_array).
Note that camelCase vs snake_case should be decided by the conventions of your programming language and enforced by a linter.
If you are using Javascript, eslint is going to request that you use camelCase.
If you are using Python, ruff will enforce snake_case.

## Enumerations

Enumeration classes should be singular nouns.
This is because each value of the enumeration is a single thing.
If the enumeration describes the days of the week, you would want `DayOfWeek` (and `DayOfWeek.Monday`) rather than `DaysOfWeek`.
This recommendation is documented in [Microsoft's .NET Guidelines](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/names-of-classes-structs-and-interfaces#naming-enumerations).

## Functions

Functions should be small, ideally doing the one thing their name indicates.
The more smaller functions you have, the more you have to think about naming, and this improves the readability of your code overall.
Limit the number of function parameters.
Prefer named parameters over position parameters in most cases if your language supports them.
This gives you more context when reading code where functions are called, since you can see the meaning of each parameter without switching context to the function definition.
For an excellent summary of when you might want to break this rule and instead prefer positional parameters, see [Python's PEP-0570 discussion of the Benefits of Positional-Only Parameters](https://peps.python.org/pep-0570/#benefits-of-positional-only-parameters).
Refactor long if/else blocks by extracting the body into its own function.
Function parameters should express the most important arguments first; if the function accepts a country and a province, the country should come first, since provinces are inside of countries / countries are more fundamental.

## Errors

All programming languages should display the stack trace in the same order when there is an uncaught exception.
I don't care if the failing line is at the top or the bottom, but we have some work to do as an industry to fix this mess.

If you have an unused parameter, user, in a method signature, prefix it with an underscore, like `_user` (obviously remove the parameter from the method signature if you can).

## Database

### Transactions

Where should transactions be started and stopped?
In general, an entire API action should be wrapped in a transaction.
Therefore, a commit should often be the last statement in a controller function.

### Schema / DDL

Use singular forms for table names.
That is, `picture` instead of `pictures`.
This one pains me, since rails decided on plural, but it feels like more people use singular.
When you have a table with a compound unique key, name the key like `[table_name]_unique`, so if the table name is user, it would be `user_unique`.
If you have a column named `[something]_id`, like `car_id`, it should be referencing a database primary key, so if your database primary keys are integers, it should be an integer.
If you need to refer to another type of identifier that is not a database primary key, use the suffix `_identifier`, like `car_identifier` for your license plate numbers or whatever.
Name foreign key constraints like this: `[current_table]_[referencedtable]_[referencetablecolumn]_fk`, so if you have a parent table with an id, and a child table referencing it, it should be called child_parent_id_fk

### Sorting

Always include `ORDER BY` clauses in your queries.
Your database engine may have a default sort order, but it is not guaranteed, especially if you later switch to a different engine.

## REST

### Naming

Use pluralized entity names in paths.
To fetch all users, use path `/users`.
To fetch one user, use path `/users/14`.
You are filtering down the list of user resources to fetch just the one you want by ID.

Should we use human readable identifiers or primary key identifiers in resource paths?

- /users/bob OR
- /users/317 OR
- /usesr/f1fbed83-2c21-4cb1-bbe2-1e8c0b1e66f4

If it is a unique identifier that the application user came up with themself, use their human-readable identifier.
if there is no such identifier, use a database primary key ID or guid.
Be careful with database primary key auto increment IDs, as these can give away the scale of your system and give users more of a chance to exploit the system from a security perspective by guessing urls.

### Resources / controllers / routes / APIs

Make them plural.
For example:

- users_controller.rb
- groups_resource.py
- cars_routes.go

Try to have multiple "actions" (distinct endpoints) in each controller.
If you don’t, consider combining two controllers into one.
Consider using noun_verb when naming actions.
For example:

- car_create
- user_show
- friend_list
- paper_update
- group_delete

### HTTP header casing

If you have code that checks HTTP headers, you could use `content-type` or `Content-type` or `Content-Type.` Use `Content-Type` if you are using a library, because that’s the version [the RFC](https://www.w3.org/Protocols/rfc1341/4_Content-Type.html) uses. If you are writing a library, allow the user to use any case, because the values are technically case insensitive.

### HTTP header prefixes

For a time, it was in vogue to prefix custom HTTP headers with `X-` as in `X-Coffee-Intensity`.
The Internet Engineering Task Force [suggested that this practice was not helpful](https://datatracker.ietf.org/doc/html/rfc6648).
Instead, prefix your HTTP headers with the name of your application in order to provide a useful namespace: `MyCoolApp-Awesome-Header`.

### HTTP Response bodies

Never return an empty response body.
If you typically return JSON, always return json.
If there is nothing better to return (when you delete an entity, for example), return:

    {"ok": true}

Returning the same structure in all cases makes things easier for users of your API.

### Partial updates

[Apparently](https://stackoverflow.com/q/2443324/6090676), partial updates should be one of these:

- a POST to /users/1
- a PATCH to /users/1

We are using PUT to /users/1 for partial updates to process models at the moment, which doesn't obviously meet REST muster, but is more familiar to those of us coming from a rails background.

### Health endpoints

Your app should implement the following endpoints.

- /health/liveness - if this returns non-200, the app is down and needs to be restarted
- /health/readiness - if this returns non-200, the app is not ready to receive requests

Readiness should generally include more thorough checks than liveness.

## Sort alphabetically, all else being equal

If there is no other more natural sorting strategy, sort constructs in your code alphabetically.
This includes but is not limited to import statements, items in lists, and function parameters if they only use named parameters ([reference](https://medium.com/flutter-senior/sort-alphabetically-everything-you-can-1e9d7299c4ae)).

## Avoid re-inventing the wheel

Where there is existing guidance that does not conflict with other rules in this document, use it.
For example, for commit messages, use [conventional commits](https://www.conventionalcommits.org/en/v1.0.0/#summary).

## Language-specific guidance

### Python

#### Never use @staticmethod.

Even if the function doesn't depend on anything else in the class right now, using this means you can never call a helper method without repeating the name of the class.
Just use @classmethod.
Guido himself regrets adding @staticmethod to the language: https://mail.python.org/pipermail/python-ideas/2016-July/041189.html

#### Avoid overusing instance methods

If you’re doing stuff like this:

UserService().create_user

Convert create_user to a class method. There’s an empty initializer, so that implies there’s no need for this method (or possibly any method in this class) to be an instance method. There’s no need to create an instance in this case, since there is no relevant instance state being used by create_user.

### Prose

Consider converting documentation/prose/normal written text to [ventilated prose](https://writetheasciidocs.netlify.app/ventilated-prose).
This sed script may or may not help:

    sed -E "s/([\.\?]) +/\1\n/g"

There's also a slightly more robust [python script](https://github.com/no-term-limits/no-term-limits/blob/main/bin/markdown_to_ventilated_prose.py).

### Sort by filename

When you call glob to get a list of files, always sort the result.

For example, in python, this is bad:

```python
files = glob.glob(file_glob)
```

And this is good:

```python
files = sorted(glob.glob(file_glob))
```

If you don't, you will have obscure bugs that are hard to track down years later because the sorting behavior is undefined / system-dependent.

## User Experience

### Dates and Times

Use relative times if the user will be scanning for information, 9 minutes ago or 3 hours ago or 2 days ago, rather than Sep 3, 2024 at 9:30am or 2024-12-01 15:23 UTC.
If you are presenting information in a non-relative format, use the user's timezone if possible.
If you have a list of things, the most recent things should come first, all else being equal.

### Apps

If your mobile app is basically a web app, let people use your site in a browser.

## DevOps

### Environment names

Use three letter environment names. dev is obvious, and stg is maybe not so unintuitive, and just use tst for test and prd for prod.

### make

make is a build tool that has existed for a long time.
The thing that makes it potentially better than a bash script is discoverability of tasks.
The power is really in the conventions.
You could just as easily build a bash script that could accomplish the same thing, but there is no standard way for people to interact with the bash script and discover what it can do.
With a make script, and with some common conventions, you can allow for something like the following (thank you to Sam DeLuca of DCTech slack for pointing this out):

```
make help
help		Print this help message
test		Run the unit tests
server-linux	Build a linux server
server-mac	Build a MacOS server
```

If you have a really good build tool in your technology of choice (cargo in Rust comes to mind), you might consider using that instead, but make is a good least common denominator that many people are familiar with across technologies.

## Conclusion

Thanks for reading.
I've been doing software development for a while now, and for the last serveral years, whenever something important came up, I've been trying to remember to record it here.
I've been using LLMs quite a bit for various purposes, but this article does not contain LLM-generated content.
Hopefully it can be helpful to you and your colleagues.
If you have any feedback, please drop a note on hacker news.

## References

- [A Set of Unit Testing Rules - Michael Feathers](https://www.artima.com/weblogs/viewpost.jsp?thread=126923)
- [Sort alphabetically everything you can - Alexey Inkin](https://medium.com/flutter-senior/sort-alphabetically-everything-you-can-1e9d7299c4ae)
- [Best practices for engine contributors - Godot](https://docs.godotengine.org/en/stable/contributing/development/best_practices_for_engine_contributors.html)
- [JSON API Standard](https://jsonapi.org/)
