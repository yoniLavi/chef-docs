.. The contents of this file are included in multiple topics.
.. This file describes a command or a sub-command for Knife.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.


|knife| includes a set of subcommands that are built around common verbs: ``create``, ``delete``, ``download``, ``list``, ``show``, and ``upload``. These subcommands allow |knife| to issue commands that interact with any object stored in the |chef repo| or stored on the |chef server|. Some important principles behind this group of subcommands includes:

* A command that works with each object in the |chef| repository. The subcommands specify the desired action (the "verb"), and then directory in which that object resides (``cookbooks/``, ``data_bags/``, ``environments/``, and ``roles/``). For example: ``download cookbooks/``
* Uses the |chef server| as if it were a file system, allowing the |chef repo| on the |chef server| to behave like a mirror of the |chef repo| on the workstation. The |chef server| will have the same objects as the local |chef repo|. To make changes to the files on the |chef server|, just download files from the |chef server| or upload files from the |chef repo|
* The context from which a command is run matters. For example, when working in the ``roles/`` directory, |knife| will know what is being worked with. Enter ``knife show base.json`` and |knife| will return the base role from the |chef server|. From the |chef repo| root, enter ``knife show roles/base.json`` to get the same result

