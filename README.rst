===============================
GIT Hook(s) for Web Development 
===============================
(NOTE: Primarily for PHP or Drupal unless others contribute to Rails, Django, or other specific hooks for the collection, I'll be happy to include them directory or as a submodule maintained separetely)

* git pre-commit hook checking PHP syntax errors. ( Uses php version installed local, not whats on the server, please be aware of this if there is diffrences in your versions. )

How to install
--------------
To install hook, copy pre-commit file to your project .git/hooks/pre-commit:

    $ cp pre-commit .git/hooks/pre-commit; 
    $ chmod +x .git/hooks/pre-commit;

Now, when you will make modifications to the code and try to commit, git will invoke `php -l` a.k.a php-lint and will stop the commit if there are errors with location info to fix the problem.

Feedback
--------
If you have found any bugs, have a patch, or a feature request open an issue in the issue queue.