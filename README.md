rails_best_practices
====================

[![Build Status](https://secure.travis-ci.org/flyerhzm/rails_best_practices.png)](http://travis-ci.org/flyerhzm/rails_best_practices)

[![Click here to lend your support to: rails-bestpractices.com and make a donation at www.pledgie.com !](https://www.pledgie.com/campaigns/12057.png?skin_name=chrome)](http://www.pledgie.com/campaigns/12057)

rails_best_practices is a code metric tool to check the quality of rails codes. It supports both activerecord and mongoid from version 1.5.0.

Usage
-----

At the root directory of rails app

    rails_best_practices .

or html output

    rails_best_practices -f html .

By default rails_best_practices will do parse codes in vendor, spec, test and features directories. If you need, see the command options:

    $ rails_best_practices -h
    Usage: rails_best_practices [options]
        -d, --debug                      debug mode
            --silent                     silent mode
        -f, --format FORMAT              output format
            --without-color              only output plain text without color
            --with-textmate              open file by textmate in html format
            --with-mvim                  open file by mvim in html format
            --with-git                   display git commit and git username in html format
            --with-hg                    display hg commit and hg username in html format
            --vendor                     include vendor files
            --spec                       include spec files
            --test                       include test files
            --features                   include features files
        -x, --exclude PATTERNS           don't analyze files matching a pattern
                                         (comma-separated regexp list)
        -g, --generate                   generate configuration yaml
        -v, --version                    show this version
        -h, --help                       show this message

Resources
---------

Homepage: <http://rails-bestpractices.com>

Github: <http://github.com/flyerhzm/rails_best_practices>

RDoc: <http://rdoc.rails-bestpractices.com>

Team Blog <http://rails-bestpractices.com/blog/posts>

Google Group: <https://groups.google.com/group/rails_best_practices>

Wiki: <http://github.com/flyerhzm/rails_best_practices/wiki>

Issue Tracker: <http://github.com/flyerhzm/rails_best_practices/issues>

Donating
--------

<a href='http://www.pledgie.com/campaigns/12057'>Support rails_best_practices at Pledgie</a>

Install
-------

rails_best_practices gem is rewritten based on ripper instead of ruby_parser to support ruby 1.9 new syntax.

Ruby 1.9

    gem install rails_best_practices

or add in Gemfile

    gem "rails_best_practices"

Issue
-----

If you install the rails_best_practices with bundler-installed github-sourced gem, please use the following command instead.

    bundle exec rails_best_practices .

If you got NoMethodError or any syntax error, you should use debug mode to detect which file rails_best_practices is parsing and getting the error.

    rails_best_practices -d .

Then give me the error stack and the source code of the file that rails_best_practices is parsing error.

Customize Configuration
-----------------------

First run

    rails_best_practices -g

to generate `rails_best_practices.yml` file.

Now you can customize this configuration file, the default configuration is as follows:

    MoveFinderToNamedScopeCheck: { }
    UseModelAssociationCheck: { }
    UseScopeAccessCheck: { }
    AddModelVirtualAttributeCheck: { }
    ReplaceComplexCreationWithFactoryMethodCheck: { attribute_assignment_count: 2 }
    MoveModelLogicIntoModelCheck: { use_count: 4 }
    OveruseRouteCustomizationsCheck: { customize_count: 3 }
    NeedlessDeepNestingCheck: { nested_count: 2 }
    NotUseDefaultRouteCheck: {  }
    KeepFindersOnTheirOwnModelCheck: { }
    LawOfDemeterCheck: { }
    UseObserverCheck: { }
    IsolateSeedDataCheck: { }
    AlwaysAddDbIndexCheck: { }
    UseBeforeFilterCheck: { customize_count: 2 }
    MoveCodeIntoControllerCheck: { }
    MoveCodeIntoModelCheck: { use_count: 2 }
    MoveCodeIntoHelperCheck: { array_count: 3 }
    ReplaceInstanceVariableWithLocalVariableCheck: { }
    DryBundlerInCapistranoCheck: { }
    UseSayWithTimeInMigrationsCheck: { }
    UseQueryAttributeCheck: { }
    RemoveTrailingWhitespaceCheck: { }
    UseMultipartAlternativeAsContentTypeOfEmailCheck: {}
    SimplifyRenderInViewsCheck: {}
    SimplifyRenderInControllersCheck: {}
    RemoveEmptyHelpersCheck: {}
    RemoveTabCheck: {}
    RestrictAutoGeneratedRoutesCheck: { }
    RemoveUnusedMethodsInModelsCheck: { except_methods: [] }
    RemoveUnusedMethodsInControllersCheck: { except_methods: [] }

You can remove or comment one review to disable it, and you can change the options.

Implementation
--------------

Move code from Controller to Model

1. Move finder to named_scope (rails2 only)
2. Use model association
3. Use scope access
4. Add model virtual attribute
5. Replace complex creation with factory method
6. Move model logic into the Model

RESTful Conventions

1. Overuse route customizations
2. Needless deep nesting
3. Not use default route
4. Restrict auto-generated routes

Model

1. Keep finders on their own model (rails2 only)
2. the law of demeter
3. Use observer
4. Use query attribute
5. Remove unused methods in models

Mailer

1. Use multipart/alternative as content_type of email

Migration

1. Isolating seed data
2. Always add db`index
3. Use say with time in migrations

Controller

1. Use before_filter
2. Simplify render in controllers
3. Remove unused methods In controllers

Helper

1. Remove empty helpers

View

1. Move code into controller
2. Move code into model
3. Move code into helper
4. Replace instance variable with local variable
5. Simplify render in views

Deployment

1. Dry bundler in capistrano

Other

1. Remove trailing whitespace
2. Remove tab

Write Your Own Check List
-------------------------

If you want to write your own check list (some check list only for your rails projects), please read this first, [How to write your own check list?][1]

Contribute
----------

If you want to add your rails best practices into the gem, please post your best practices on <http://rails-bestpractices.com>

Contact Us
----------

We provide rails consulting services, you can contact us by twitter or email.

Follow us on twitter: <http://twitter.com/railsbp>

Send us email: <team@rails-bestpractices.com>


Copyright © 2009 - 2011 Richard Huang (flyerhzm@gmail.com), released under the MIT license


[1]:https://github.com/flyerhzm/rails_best_practices/wiki/How-to-write-your-own-check-list
