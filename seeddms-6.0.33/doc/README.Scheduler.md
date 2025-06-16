Scheduler
==========

The scheduler in SolutionDMS manages frequently run tasks. It is very similar
to regular unix cron jobs. A task in SolutionDMS is an instanciation of a task
class which itself is defined by an extension or SolutionDMS itself.
SolutionDMS has some predefined classes e.g. core::expireddocs.

In order for tasks to be runnalbe, a user `cli_scheduler` must exists in
SolutionDMS.

All tasks are executed by a single cronjob in the directory `utils`

> */5 * * * * /home/www-data/solutiondms/seeddms/utils/seeddms-schedulercli --mode=run

Please keep in mind, that the php interpreter used for the cronjob may be
different from the php interpreter used für the web application. Hence, two
different php.ini files might be used. php and the php extensions may differ as
well. This can cause some extensions to be disabled and consequently some task
classes are not defined.

`utils/seeddms-schedulercli` can also be run on the command line. If you
do that, run it with the same system user used for the web server. On Debian
this is www-data. Hence run it like

sudo -u www-data utils/seeddms-schedulercli --mode=list
